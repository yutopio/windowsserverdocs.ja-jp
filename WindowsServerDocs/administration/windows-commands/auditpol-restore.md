---
title: auditpol restore
description: Auditpol 復元コマンドの参照記事。このコマンドは、システム監査ポリシーの設定、すべてのユーザーのユーザーごとの監査ポリシー設定、および/backup オプションで使用されるコンマ区切り値 (CSV) ファイル形式と構文的に一致するファイルからのすべての監査オプションを復元します。
ms.topic: reference
ms.assetid: ad73e520-484f-4cf1-a7f9-ae7488e9edf6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dcf4f85da5955f49e644962de82a66a4dedaea64
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029010"
---
# <a name="auditpol-restore"></a>auditpol restore

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

システム監査ポリシー設定、すべてのユーザーのユーザーごとの監査ポリシー設定、および/backup オプションで使用されるコンマ区切り値 (CSV) ファイル形式と構文的に一致するファイルからのすべての監査オプションを復元します。

*ユーザーごと*のポリシーと*システム*ポリシーに対して*復元*操作を実行するには、セキュリティ記述子でそのオブジェクトセットの**書き込み**または**フルコントロール**のアクセス許可を持っている必要があります。 "**監査とセキュリティログの管理**" (SeSecurityPrivilege) ユーザー権利を持っている場合は、*復元*操作を実行することもできます。これは、エラーや悪意のある攻撃が発生したときにセキュリティ記述子を復元する場合に便利です。

## <a name="syntax"></a>構文

```
auditpol /restore /file:<filename>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| /file | 監査ポリシーの復元元のファイルを指定します。 このファイルは、/backup オプションを使用して作成されているか、/backup オプションで使用される CSV ファイル形式と構文的に一致している必要があります。 |
| /? |コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

システム監査ポリシー設定、すべてのユーザーのユーザーごとの監査ポリシー設定、および/backup コマンドを使用して作成された auditpolicy.csv という名前のファイルからのすべての監査オプションを復元するには、次のように入力します。

```
auditpol /restore /file:c:\auditpolicy.csv
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [auditpol backup](auditpol-backup.md)

- [auditpol コマンド](auditpol.md)
