---
title: AD フォレストの回復-権限のない復元
ms.author: daveba
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: e4ce1d18-d346-492a-8bca-f85513aa3ac1
ms.openlocfilehash: 9924b7498bde45f07df9c0078ff45fce84807680
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93071274"
---
# <a name="performing-a-nonauthoritative-restore-of-active-directory-domain-services"></a>Active Directory Domain Services の権限のない復元を実行する

>適用対象: Windows Server 2016、Windows Server 2012、および 2012 R2、Windows Server 2008 および 2008 R2

権限のない復元を実行するには、次の手順を実行します。

次の手順では、Wbadmin.exe を使用して、Active Directory または Active Directory Domain Services (AD DS) の authoritative restore を実行します。 別のバックアップソリューションを使用している場合、または後でフォレストの回復プロセスで SYSVOL の authoritative restore を実行する場合は、次の代替方法を使用して SYSVOL の authoritative restore を実行できます。

- ファイルレプリケーションサービス (FRS) を使用して SYSVOL をレプリケートする場合は、Microsoft サポート技術情報の [記事 290762](https://go.microsoft.com/fwlink/?LinkId=148443) の手順に従って、 **BurFlags** レジストリキーを使用して、FRS レプリカセットを再初期化します。または、必要に応じて、315457 [315457](https://support.microsoft.com/kb/315457)を使用して sysvol ツリーを再構築します。 SYSVOL が FRS によってレプリケートされているかどうかを判断するには、「 [ドメインコントローラーの Sysvol フォルダーが DFSR または frs によってレプリケートされているかどうか](/windows/win32/vss/backing-up-and-restoring-an-frs-replicated-sysvol-folder#determining_whether_a_domain_controller_s_sysvol_folder_is_replicated_by_dfsr_or_frs)を判断する
- 分散ファイルシステム (DFS) レプリケーションを使用して SYSVOL をレプリケートする場合は、「DFSR によってレプリケートされた [sysvol の権限のある同期を実行](AD-Forest-Recovery-Authoritative-Recovery-SYSVOL.md)する」を参照してください。

## <a name="performing-a-nonauthoritative-restore"></a>権限のない復元を実行する

次の手順を使用して、Windows Server 2012、Windows Server 2008 R2、または Windows Server 2008 を実行する DC で wbadmin.exe を使用して、AD DS と SYSVOL の authoritative restore を同時に実行します。 バックアップには、システム状態データを明示的に含める必要があります。完全なサーバーの回復に使用される完全なサーバーバックアップは機能しません。 システム状態のバックアップを作成する方法の詳細については、「 [システム状態データの](AD-Forest-Recovery-Backing-up-System-State.md)バックアップ」を参照してください。

### <a name="to-perform-a-nonauthoritative-restore-of-ad-ds-and-authoritative-restore-of-sysvol-using-wbadminexe"></a>wbadmin.exe を使用して SYSVOL の AD DS と authoritative restore の権限のない復元を実行するには

- 次の例に示すように、回復コマンドに **-authsysvol** スイッチを含めます。

   ```
   wbadmin start systemstaterecovery <otheroptions> -authsysvol
   ```

   次に例を示します。

   ```
   wbadmin start systemstaterecovery -version:11/20/2012-13:00 -authsysvol
   ```

![復元](media/AD-Forest-Recovery-Nonauthoritative-Restore/nonauth.png)

## <a name="next-steps"></a>次の手順

- [AD フォレストの回復ガイド](AD-Forest-Recovery-Guide.md)
- [AD フォレストの回復 - 手順](AD-Forest-Recovery-Procedures.md)
