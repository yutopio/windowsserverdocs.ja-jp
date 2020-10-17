---
title: tsprof
description: Tsprof コマンドの参照記事。ユーザーの構成情報リモートデスクトップサービスを別のユーザーにコピーします。
ms.topic: reference
ms.assetid: 27047868-b706-4208-b7e0-1437a2325dd3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e18f736a31af3cc649d4921197710f713e7df6af
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156341"
---
# <a name="tsprof"></a>tsprof

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

1 人のユーザーから別のリモート デスクトップ サービス ユーザーの構成情報をコピーします。 リモートデスクトップサービスユーザーの構成情報は、[ローカルユーザーとグループ] と [active directory ユーザーとコンピューター] の [リモートデスクトップサービスの拡張機能] に表示されます。

> [!NOTE]
> [Tsprof コマンド](tsprof.md)を使用して、ユーザーのプロファイルパスを設定することもできます。
>
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
tsprof /update {/domain:<Domainname> | /local} /profile:<path> <username>
tsprof /copy {/domain:<Domainname> | /local} [/profile:<path>] <src_user> <dest_user>
tsprof /q {/domain:<Domainname> | /local} <username>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /update | ドメイン内ののプロファイルパス情報 `<username>` `<domainname>` をに更新 `<profilepath>` します。 |
| /domain`<Domainname>` | 操作が適用されるドメインの名前を指定します。 |
| /local | ローカルユーザーアカウントにのみ操作を適用します。 |
| /profile`<path>` | [ローカルユーザーとグループ]、[active directory ユーザーとコンピューター] のリモートデスクトップサービス拡張機能に表示されるプロファイルパスを指定します。 |
| `<username>` | サーバープロファイルパスを更新または照会するユーザーの名前を指定します。 |
| /copy | からにユーザー構成情報をコピー `<src_user>` `<dest_user>` し、のプロファイルパス情報をに更新し `<dest_user>` `<profilepath>` ます。 とはどちらもローカルであるか、 `<src_user>` `<dest_user>` またはドメイン内に存在する必要があり `<domainname>` ます。 |
| `<src_user>` | ユーザー構成情報をコピーするユーザーの名前を指定します。 ソースユーザーとも呼ばれます。 |
| `<dest_user>` | ユーザー構成情報をコピーするユーザーの名前を指定します。 宛先ユーザーとも呼ばれます。 |
| /q | サーバープロファイルパスに対してクエリを実行するユーザーの現在のプロファイルパスを表示します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>使用例

ユーザー構成情報を *LocalUser1* から *LocalUser2*にコピーするには、次のように入力します。

```
tsprof /copy /local LocalUser1 LocalUser2
```

*LocalUser1*のリモートデスクトップサービスプロファイルパスを*c:\ プロファイル*という名前のディレクトリに設定するには、次のように入力します。

```
tsprof /update /local /profile:c:\profiles LocalUser1
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)
