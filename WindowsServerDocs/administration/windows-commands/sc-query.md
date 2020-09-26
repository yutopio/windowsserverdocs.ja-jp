---
title: Sc.exe クエリ
description: 指定されたサービス、ドライバー、サービスの種類、またはドライバーの種類に関する情報を取得して表示する、sc.exe クエリコマンドの参照記事。
ms.topic: reference
ms.assetid: ac365f89-4b20-4de6-a582-b204c5e7d0eb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7d5994c54914165cb79ba0f505f1a44b2d7f019a
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388215"
---
# <a name="scexe-query"></a>Sc.exe クエリ

取得し、指定されたサービス、ドライバー、サービスの種類またはドライバーの種類に関する情報を表示します。

## <a name="syntax"></a>構文

```
sc.exe [<servername>] query [<servicename>] [type= {driver | service | all}] [type= {own | share | interact | kernel | filesys | rec | adapt}] [state= {active | inactive | all}] [bufsize= <Buffersize>] [ri= <Resumeindex>] [group= <groupname>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| `<servername>` | サービスが配置されているリモート サーバーの名前を指定します。 名前には、汎用名前付け規則 (UNC) 形式 (myserver など) を使用する必要があり \\ ます。 SC.exe をローカルで実行するには、このパラメーターを使用しないでください。 |
| `<servicename>` | によって返されるサービスの名前を指定、 **られて** 操作します。 この **クエリ** パラメーターは、他の **クエリ** パラメーター ( *servername*以外) と共に使用されることはありません。 |
| `type= {driver | service | all}` | 列挙の対象を指定します。 選択肢は次のようになっています。<ul><li>**ドライバー** -ドライバーのみが列挙されることを指定します。</li><li>**サービス** -列挙されるサービスのみを指定します。 これが既定値です。</li><li>**all** -ドライバーとサービスの両方が列挙されることを指定します。</li></ul> |
| `type= {own | share | interact | kernel | filesys | rec | adapt}` | サービスの型または列挙するドライバーの種類を指定します。 選択肢は次のようになっています。<ul><li>**独自** -独自のプロセスで実行されているサービスを指定します。 実行可能ファイルは他のサービスと共有されません。 これが既定値です。</li><li>**共有** -共有プロセスとして実行されるサービスを指定します。 その他のサービス実行可能ファイルを共有します。</li><li>**カーネル** のドライバーを指定します。</li><li>**filesys** -ファイル システム ドライバーを指定します。</li><li>**推奨値** -ファイル システムで認められたコンピューターで使用されるファイル システムを識別するドライバーを指定します。</li><li>**対話** -ユーザーからの入力を受け取って、デスクトップと対話可能なサービスを指定します。 対話型サービスは、LocalSystem アカウントで実行する必要があります。 この型は、 **type = 独自**または**type = shared**と組み合わせて使用する必要があります (たとえば、 **type = 相互作用****型 = 独自**)。 使用して **型 = 対話** 自体でエラーが生成されます。</li></ul> |
| `state= {active | inactive | all}` | 列挙するサービスの開始状態を指定します。 選択肢は次のようになっています。<ul><li>**アクティブ** -すべてのアクティブなサービスを指定します。 これが既定値です。</li><li>**inactive** -一時停止または停止されたすべてのサービスを指定します。</li><li>**all** -すべてのサービスを指定します。</li></ul> |
| `bufsize= <Buffersize>` | 列挙バッファーのサイズをバイト単位で指定します。 既定のバッファー サイズは、1,024 バイトです。 クエリの結果の表示が1024バイトを超える場合は、バッファーのサイズを大きくする必要があります。 |
| `ri= <Resumeindex>` | 列挙を開始または再開するにはインデックス番号を指定します。 既定値は 0 (ゼロ) です。 既定のバッファーに表示される値よりも詳細な情報が返される場合は、パラメーターを指定してこのパラメーターを使用し `bufsize=` ます。 |
| `group= <Groupname>` | 列挙するサービス グループを指定します。 既定では、すべてのグループが列挙されます。 既定では、すべてのグループが列挙されます (* * グループ = * *)。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- 各コマンドラインオプション (パラメーター) には、オプション名の一部として等号を含める必要があります。

- スペースは、オプションとその値の間で必要な (たとえば、 **型 = 独自**します。 スペースを省略した場合、操作は失敗します。

- **クエリ** 操作には、サービスに関する次の情報が表示されます: WIN32_EXIT_B、SERVICE_EXIT_B、チェックポイント、および WAIT_HINT (状態は使用できない) と同様に状態 (サービスのレジストリ サブキーの名前)、サービス名を入力します。

- **型 =** 場合によってはで 2 回パラメーターを使用することができます。 最初の外観、 **型 =** パラメーターでは、サービス、ドライバー、またはその両方のクエリを実行するかどうかを指定します (**すべて**)。 2 つ目の外観、 **型 =** パラメーターから型を指定、 **作成** さらに、クエリの範囲を絞り込むに操作します。

- **クエリ**コマンドからの表示結果が列挙バッファーのサイズを超えると、次のようなメッセージが表示されます。

  ```
  Enum: more data, need 1822 bytes start resume at index 79

  To display the remaining **query** information, rerun **query**, setting **bufsize=** to be the number of bytes and setting **ri=** to the specified index. For example, the remaining output would be displayed by typing the following at the command prompt:

  sc.exe query bufsize= 1822 ri= 79
  ```

## <a name="examples"></a>例

アクティブなサービスのみの情報を表示するには、次のコマンドのいずれかを入力します。

```
sc.exe query
sc.exe query type= service
```

アクティブなサービスの情報を表示し、2,000 バイトのバッファー サイズを指定するには、次のように入力します。

```
sc.exe query type= all bufsize= 2000
```

*Wuauserv*サービスの情報を表示するには、次のように入力します。

```
sc.exe query wuauserv
```

すべてのサービス (アクティブおよび非アクティブ) の情報を表示するには、次のように入力します。

```
sc.exe query state= all
```

すべてのサービス (アクティブおよび非アクティブ)、56 行目から始まる情報を表示するには、次のように入力します。

```
sc.exe query state= all ri= 56
```

対話型サービスの情報を表示するには、次のように入力します。

```
sc.exe query type= service type= interact
```

ドライバーのみの情報を表示するには、次のように入力します。

```
sc.exe query type= driver
```

ドライバーに関する情報を *Network Driver Interface Specification (NDIS) グループ*に表示するには、次のように入力します。

```
sc.exe query type= driver group= NDIS
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
