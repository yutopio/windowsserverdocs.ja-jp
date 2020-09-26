---
title: scwcmd transform
description: Scwcmd transform コマンドの参照記事。セキュリティ構成ウィザード (SCW) を使用して生成されたセキュリティポリシーファイルを Active Directory Domain Services の新しいグループポリシーオブジェクト (GPO) に変換します。
ms.topic: reference
ms.assetid: 640dd892-0bb9-416d-8318-60a26605bcf4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: bef3d9800d19ac0e3e574b4ef2e1195dcdc3baed
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389255"
---
# <a name="scwcmd-transform"></a>scwcmd transform

> 適用対象: Windows Server 2012 R2 および Windows Server 2012

新しいグループ ポリシー オブジェクト (GPO) で Active Directory ドメイン サービス セキュリティ構成ウィザード (SCW) を使用して、生成されたセキュリティ ポリシー ファイルを変換します。 変換の処理には、実行されるサーバー上のすべての設定は変わりません。 変換の操作が完了した後、管理者は、サーバーにポリシーを展開する目的の Ou に GPO をリンクする必要があります。

> [!IMPORTANT]
> 変換操作を完了するには、ドメイン管理者の資格情報が必要です。
>
> グループポリシーを使用してインターネットインフォメーションサービス (IIS) セキュリティポリシー設定を展開することはできません。
>
> サーバーが最後に起動したときに Windows ファイアウォールサービスが自動的に開始されていない限り、承認済みアプリを一覧表示するファイアウォールポリシーをサーバーに展開することはできません。

## <a name="syntax"></a>構文

```
scwcmd transform /p:<policyfile.xml> /g:<GPOdisplayname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /p`<policyfile.xml>` | 適用される .xml ポリシー ファイルのパスとファイル名を指定します。 このパラメーターを指定する必要があります。 |
| /g`<GPOdisplayname>` | GPO の表示名を指定します。 このパラメーターを指定する必要があります。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

*FileServerPolicy.xml*という名前のファイルから*FileServerSecurity*という名前の GPO を作成するには、次のように入力します。

```
scwcmd transform /p:FileServerPolicy.xml /g:FileServerSecurity
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [scwcmd analyze コマンド](scwcmd-analyze.md)

- [scwcmd configure コマンド](scwcmd-configure.md)

- [scwcmd register コマンド](scwcmd-register.md)

- [scwcmd rollback コマンド](scwcmd-rollback.md)

- [scwcmd view コマンド](scwcmd-view.md)