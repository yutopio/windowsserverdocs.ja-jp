---
title: tpmvscmgr
description: Tpmvscmgr のリファレンス記事。管理者の資格情報を持つユーザーがコンピューターで TPM 仮想スマートカードを作成および削除できるようにするコマンドラインツールです。
ms.topic: reference
ms.assetid: 8b2c8ff4-5c5d-446d-99e7-4daa1b36a163
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1dfa4a51c0ea75092e3abf885476e77d3c35435a
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156420"
---
# <a name="tpmvscmgr"></a>tpmvscmgr

Tpmvscmgr コマンドラインツールを使用すると、管理者の資格情報を持つユーザーは、コンピューター上で TPM 仮想スマートカードを作成および削除できます。

## <a name="syntax"></a>構文

```
tpmvscmgr create [/name] [/adminkey DEFAULT | PROMPT | RANDOM] [/PIN DEFAULT | PROMPT] [/PUK DEFAULT | PROMPT] [/generate] [/machine] [/?]
```

```
tpmvscmgr destroy [/instance <instanceID>] [/?]
```

### <a name="create-parameters"></a>パラメーターを作成する

**Create**コマンドは、ユーザーのシステムに新しい仮想スマートカードを設定します。 また、削除が必要な場合、後で参照するために新しく作成されたカードのインスタンス ID も返されます。 インスタンス ID は、 **ROOT\SMARTCARDREADER\000n** の形式になります。 **n** は0から始まり、新しい仮想スマートカードを作成するたびに1ずつ増加します。

| パラメーター | 説明 |
|--|--|
| /name | 必須です。 新しい仮想スマートカードの名前を示します。 |
| /adminkey | ユーザーが PIN を忘れた場合にカードの PIN をリセットするために使用できる、必要な管理者キーを示します。 次の事柄が関係します。<ul><li>**Default** - *010203040506070801020304050607080102030405060708*の既定値を指定します。</li><li>[**プロンプト**-ユーザーに管理者キーの値を入力するように求めるメッセージを表示します。</li><li>**ランダム** -ユーザーに返されないカードの管理者キーに対してランダムな設定が行われます。 これにより、スマートカード管理ツールを使用して管理できないカードが作成されます。 RANDOM オプションを使用する場合、管理者キーは48の16進数文字で入力する必要があります。</li></ul> |
| /ピン | 必要なユーザー PIN の値を示します。<ul><li>**既定** -12345678 の既定の PIN を指定します。</li><li>**PROMPT** -コマンドラインで PIN を入力するようにユーザーに要求します。 PIN は8文字以上にする必要があり、数字、文字、および特殊文字を含めることができます。</li></ul> |
| /PUK | 必要な PIN のロック解除キー (PUK) の値を示します。 PUK 値は、8文字以上で、数字、文字、および特殊文字を含めることができます。 パラメーターを省略した場合は、PUK を使用せずにカードが作成されます。 選択肢は次のようになっています。<ul><li>**既定** 値: *12345678*の既定の PUK を指定します。</li><li>**プロンプト** -コマンドラインで PUK を入力するようにユーザーに求めます。</li></ul> |
| /生成 | では、仮想スマートカードが機能するために必要なファイルがストレージに生成されます。 **/Generate**パラメーターを使用しない場合は、基になるファイルシステムを使用せずにカードを作成したのと同じです。 ファイルシステムのないカードは、Microsoft Configuration Manager などのスマートカード管理システムでのみ管理できます。 |
| /machine | 仮想スマートカードを作成できるリモートコンピューターの名前を指定できます。 これはドメイン環境でのみ使用でき、DCOM に依存します。 別のコンピューターで仮想スマートカードを作成するコマンドを正常に実行するには、このコマンドを実行するユーザーが、リモートコンピューターのローカル管理者グループのメンバーである必要があります。 |
| /? | このコマンドのヘルプを表示します。 |

### <a name="destroy-parameters"></a>パラメーターの破棄

[ **破棄** ] コマンドを実行すると、ユーザーのコンピューターから仮想スマートカードが安全に削除されます。

> [!WARNING]
> 削除された仮想スマートカードは回復できません。

| パラメーター | 説明 |
|--|--|
| /instance | 削除する仮想スマートカードのインスタンス ID を指定します。 InstanceID は、カードが作成されたときに tpmvscmgr.exe によって出力として生成されました。 **/インスタンス**パラメーターは、 **Destroy**コマンドの必須フィールドです。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- 英数字入力の場合、127文字の完全な ASCII セットが許可されます。

## <a name="examples"></a>使用例

別のコンピューターから起動したスマートカード管理ツールで後で管理できる仮想スマートカードを作成するには、次のように入力します。

```
tpmvscmgr.exe create /name VirtualSmartCardForCorpAccess /AdminKey DEFAULT /PIN PROMPT
```

または、既定の管理者キーを使用する代わりに、コマンドラインで管理者キーを作成することもできます。 次のコマンドは、管理者キーを作成する方法を示しています。

```
tpmvscmgr.exe create /name VirtualSmartCardForCorpAccess /AdminKey PROMPT /PIN PROMPT
```

証明書の登録に使用できる管理されていない仮想スマートカードを作成するには、次のように入力します。

```
tpmvscmgr.exe create /name VirtualSmartCardForCorpAccess /AdminKey RANDOM /PIN PROMPT /generate
```

ランダム化された管理者キーを使用して、仮想スマートカードが作成されます。 キーは、カードが作成された後に自動的に破棄されます。 これは、ユーザーが PIN を忘れた場合、または PIN を変更したい場合、ユーザーはカードを削除して再度作成する必要があることを意味します。

カードを削除するには、次のように入力します。

```
tpmvscmgr.exe destroy /instance <instance ID>
```

ここで、 `<instanceID>` は、ユーザーがカードを作成したときに画面に出力された値です。 具体的には、最初に作成されたカードのインスタンス ID は *ROOT\SMARTCARDREADER\0000*です。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
