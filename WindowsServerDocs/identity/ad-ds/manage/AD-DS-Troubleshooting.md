---
ms.assetid: fd3bc84a-48eb-4f00-9dc2-846bf2c2668b
title: AD FS のトラブルシューティング
description: AD DS のトラブルシューティングセクションの概要
ms.author: daveba
author: iainfoulds
manager: dcscontentpm
ms.date: 11/22/2019
ms.topic: article
ms.openlocfilehash: 923b2442d68590821dfdfccee15f732c47829f3a
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93068114"
---
# <a name="ad-ds-troubleshooting"></a>AD FS のトラブルシューティング

>適用対象: windows Server 2019、Windows Server 2016、Windows Server 2012 R2

ここでは、Active Directory レプリケーション中に発生する可能性のある問題を診断および修正するためのトラブルシューティングの推奨事項と手順について説明します。 この記事では、ディレクトリサービスのイベントログエントリに応答する方法と、Repadmin.exe や Dcdiag.exe などのツールによって報告される可能性があるメッセージの解釈方法について説明します。

Repadmin.exe と Dcdiag.exe は、Windows Server 2012 R2 以降のバージョンを実行しているすべてのドメインコントローラーで使用できます。 これらのツールを使用して問題のトラブルシューティングを行う方法の詳細については、次の記事を参照してください。

- [トラブルシューティングのためにコンピューターを構成する Active Directory](../manage/troubleshoot/Configuring-a-Computer-for-Troubleshooting.md)
- [Active Directory レプリケーションの問題のトラブルシューティングに関するページ](../manage/troubleshoot/Troubleshooting-Active-Directory-Replication-Problems.md)

もう1つの便利なテクノロジは、Windows イベントトレーシング (ETW) です。 ETW を使用して、ドメインコントローラー間の LDAP 通信のトラブルシューティングを行うことができます。 詳細については、「 [ETW を使用した LDAP 接続のトラブルシューティング](../manage/troubleshoot/troubleshoot-ldap-using-etw.md)」を参照してください。

また、Windows 10 を実行しているメンバーサーバーにリモートサーバー管理ツール (RSAT) をインストールすることもできます。 RSAT のインストール方法の詳細については、「 [リモートサーバー管理ツール](../../../remote/remote-server-administration-tools.md)」を参照してください。
