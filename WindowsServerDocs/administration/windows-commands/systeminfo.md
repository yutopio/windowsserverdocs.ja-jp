---
title: systeminfo
description: Systeminfo コマンドの参照記事。オペレーティングシステムの構成、セキュリティ情報、製品 ID、ハードウェアのプロパティ (RAM、ディスク領域、ネットワークカードなど) を含む、コンピューターとそのオペレーティングシステムに関する詳細な構成情報が表示されます。
ms.topic: reference
ms.assetid: 39954968-3c2e-4d3e-9d89-c9c43347461e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9c104d3114eae6170e3fbbd60ab718fa0013ea85
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718199"
---
# <a name="systeminfo"></a>systeminfo

コンピューターとオペレーティング システムの構成、セキュリティ情報、製品 ID、および (RAM、ディスク領域のネットワーク カードなど) のハードウェア プロパティを含む、オペレーティング システムの構成情報の詳細表示します。

## <a name="syntax"></a>構文

```
systeminfo [/s <computer> [/u <domain>\<username> [/p <password>]]] [/fo {TABLE | LIST | CSV}] [/nh]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /s `<computer>` | 名前またはリモート コンピューターの IP アドレスを指定します (円記号を使用しない)。 既定値はローカル コンピューターです。 |
| /u `<domain>\<username>` | 指定したユーザー アカウントのアカウント権限でコマンドを実行します。 場合 **/u** が指定されていない、このコマンドは、現在のコマンドを発行しているコンピューターにログオンしたユーザーのアクセス許可を使用します。 |
| /p `<password>` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| /fo `<format>` | 次の値のいずれかで出力形式を指定します。<ul><li>**テーブル** -出力をテーブルに表示します。</li><li>**リスト** -出力を一覧に表示します。</li><li>**Csv** -コンマ区切り値 (.csv) 形式で出力を表示します。</li></ul> |
| /nh | 出力に列ヘッダーを抑制します。 有効な場合に、 **/fo** パラメーターがテーブルまたは CSV に設定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

*Srvmain*という名前のコンピューターの構成情報を表示するには、次のように入力します。

```
systeminfo /s srvmain
```

*Maindom*ドメインに配置されている*Srvmain2*という名前のコンピューターの構成情報をリモートで表示するには、次のように入力します。

```
systeminfo /s srvmain2 /u maindom\hiropln
```

*Maindom*ドメインに配置されている*Srvmain2*という名前のコンピューターの構成情報を (一覧形式で) リモートで表示するには、次のように入力します。

```
systeminfo /s srvmain2 /u maindom\hiropln /p p@ssW23 /fo list
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
