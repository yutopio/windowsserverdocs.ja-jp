---
title: waitfor
description: システムでシグナルを送信または待機する waitfor コマンドの参照記事。
ms.topic: reference
ms.assetid: a48ef70d-4d28-4035-b6b0-7d7b46ac2157
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 157861a02abe8fbf851a6ef12460b257a7628803
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156123"
---
# <a name="waitfor"></a>waitfor

送信またはシステムでのシグナルを待機します。 このコマンドは、ネットワーク上のコンピューターを同期するために使用されます。

## <a name="syntax"></a>構文

```
waitfor [/s <computer> [/u [<domain>\]<user> [/p [<password>]]]] /si <signalname>
waitfor [/t <timeout>] <signalname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /s `<computer>` | リモートコンピューターの名前または IP アドレスを指定します (円記号は使用しないでください)。 既定値はローカル コンピューターです。 このパラメーターは、コマンドで指定されたすべてのファイルとフォルダーに適用されます。 このパラメーターを使用しない場合、信号はドメイン内のすべてのシステムにブロードキャストされます。 このパラメーターを使用すると、指定したシステムにのみシグナルが送信されます。 |
| /u `[<domain>]<user>` | 指定したユーザー アカウントの資格情報を使用してスクリプトを実行します。 既定では、 **waitfor** 現在のユーザーの資格情報を使用します。 |
| /p `[\<password>]` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| /si | ネットワーク経由で指定されたシグナルを送信します。 このパラメーターを使用すると、手動でシグナルをアクティブにすることもできます。 |
| /t `<timeout>` | シグナルを待機する秒数を指定します。 既定では、 **waitfor** が無制限に待機します。 |
| `<signalname>` | 信号を指定する **waitfor** まで待機するか、または送信します。 このパラメーターでは大文字と小文字が区別されず、225文字を超えることはできません。 有効な文字には、a ~ z、A ~ Z、0 ~ 9、および拡張文字セット (128 ~ 255) ASCII が含まれます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- 複数のインスタンスを実行する **waitfor** 1 台のコンピューターではの各インスタンスで **waitfor** 異なるシグナルを待機する必要があります。 1 つだけ **waitfor** 、特定のコンピューター上で指定されたシグナルを待機できます。

- のみ、コンピューターは、信号を送信するコンピューターと同じドメイン内にある場合、シグナルを受信します。

- このコマンドは、ソフトウェアビルドをテストするときに使用できます。 コンパイルを行うコンピューターが実行されている複数のコンピューターに信号を送信するなど **waitfor** コンパイルが正常に完了後します。 信号の要求を受信したバッチ ファイルを含む **waitfor** コンピューターがすぐにソフトウェアのインストールやコンパイル済みのビルドでテストを実行するように指定できます。

## <a name="examples"></a>使用例

*Espressobuild007*シグナルが受信されるまで待機するには、次のように入力します。

```
waitfor espresso\build007
```

既定では、 **waitfor** シグナルを無期限に待機します。

*Espresso\compile007*シグナルが受信されるまで*10 秒間*待機するには、次のように入力します。

```
waitfor /t 10 espresso\build007
```

*Espresso\ build007*信号を手動でアクティブ化するには、次のように入力します。

```
waitfor /si espresso\build007
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
