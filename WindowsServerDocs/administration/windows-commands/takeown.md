---
title: takeown
description: Takeown コマンドの参照記事。これにより、管理者は以前に拒否されたファイルへのアクセスを回復できます。
ms.topic: reference
ms.assetid: 0683cd65-a6db-4cab-962b-45a0ff61f43c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 34fce5000a0a8c91123a2ebd4765bf4cbb00a289
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718239"
---
# <a name="takeown"></a>takeown

管理者をファイルの所有者にすることによって、拒否されていたファイルへの管理者のアクセスを回復できます。 通常、このコマンドはバッチファイルで使用されます。

## <a name="syntax"></a>構文

```
takeown [/s <computer> [/u [<domain>\]<username> [/p [<password>]]]] /f <filename> [/a] [/r [/d {Y|N}]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /s `<computer>` | 名前またはリモート コンピューターの IP アドレスを指定します (円記号を使用しない)。 既定値はローカル コンピューターです。 このパラメーターは、すべてのファイルと、コマンドで指定されたフォルダーに適用されます。 |
| /u `[<domain>\]<username>` | 指定したユーザー アカウントのアクセス許可を持つ、スクリプトを実行します。 既定値は、システムのアクセス許可です。 |
| /p `[<[password>]` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| /f `<filename>` | ファイル名またはディレクトリの名前を指定のパターン。 ワイルドカード文字を使用する `*` パターンを指定するとします。 構文を使用することもでき `<sharename>\<filename>` ます。 |
| /a | 現在のユーザーの代わりに、Administrators グループに所有権を示します。 このオプションを指定しない場合、ファイルの所有権は、現在コンピューターにログオンしているユーザーに与えられます。 |
| /r | 指定したディレクトリとサブディレクトリ内のすべてのファイルに対して再帰的な操作を実行します。 |
| d `{Y | N}` | 現在のユーザーが指定されたディレクトリに対する **リストフォルダー** のアクセス許可を持っていない場合に表示される確認プロンプトを表示しません。代わりに、指定された既定値を使用します。 **/D**オプションの有効な値は次のとおりです。<ul><li>**Y** -ディレクトリの所有権を取得します。</li><li>**N** -ディレクトリをスキップします。<p>**注**<br>このオプションは、 **/r** オプションと組み合わせて使用する必要があります。</li></ul> |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="remarks"></a>解説

- 使用した混合のパターン (**でしょうか。** および **&#42;**) は、 **takeown** コマンドではサポートされていません。

- **Takeown**を使用してロックを削除した後は、ファイルとディレクトリを削除する前に、Windows エクスプローラーを使用してファイルとディレクトリに対する完全なアクセス許可を付与する必要がある場合があります。

## <a name="examples"></a>例

*Lostfile*という名前のファイルの所有権を取得するには、次のように入力します。

```
takeown /f lostfile
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
