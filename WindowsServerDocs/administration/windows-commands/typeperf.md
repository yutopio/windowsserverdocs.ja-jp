---
title: typeperf
description: コマンドウィンドウまたはログファイルにパフォーマンスデータを書き込む typeperf コマンドの参照記事。
ms.topic: reference
ms.assetid: 0c7ca89a-03b3-4626-afcf-ef8565e90043
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6a06d422db5f681c3e1775facc4f8d0eee422244
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156350"
---
# <a name="typeperf"></a>typeperf

**Typeperf**コマンドは、パフォーマンスデータをコマンドウィンドウまたはログファイルに書き込みます。 **Typeperf**を停止するには、Ctrl + C キーを押します。

## <a name="syntax"></a>構文

```
typeperf <counter [counter ...]> [options]
typeperf -cf <filename> [options]
typeperf -q [object] [options]
typeperf -qx [object] [options]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<counter [counter […]]>` | 監視するパフォーマンスカウンターを指定します。 パラメーターは、のよう `<counter>` に、 \\ Computer\Object (インスタンス) カウンター形式のパフォーマンスカウンターの完全な名前です `\\Server1\Processor(0)\% User Time` 。  |

#### <a name="options"></a>オプション

| オプション | 説明 |
|--|--|
| -f `<CSV | TSV | BIN | SQL>` | 出力ファイルの形式を指定します。 既定値は CSV です。 |
| -cf `<filename>` | 監視するパフォーマンスカウンターの一覧を含むファイルを指定します。1行につき1つのカウンターがあります。 |
| -si `<[[hh:]mm:]ss>` | サンプル間隔を指定します。 既定値は1秒です。 |
| -o `<filename>` | 出力ファイルまたは SQL データベースのパスを指定します。 既定値は STDOUT (コマンドウィンドウに書き込まれます) です。 |
| -q `[object]` | インストールされているカウンターの一覧を表示します (インスタンスなし)。 1つのオブジェクトのカウンターを一覧表示するには、オブジェクト名を含めます。 よう |
| -qx `[object]` | インストールされているカウンターの一覧をインスタンスと共に表示します。 1つのオブジェクトのカウンターを一覧表示するには、オブジェクト名を含めます。 |
| -sc `<samples>` | 収集するサンプルの数を指定します。 既定では、CTRL + C キーが押されるまでデータが収集されます。 |
| -config `<filename>` | コマンドオプションを含む設定ファイルを指定します。 |
| -s `<computer_name>` | カウンターパスにコンピューターが指定されていない場合に、監視するリモートコンピューターを指定します。 |
| -y | 確認を求めずにすべての質問に対して *[はい]* を回答します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>使用例

ローカルコンピューターのパフォーマンスカウンターの値を `\Processor(_Total)\% Processor Time` コマンドウィンドウに書き込むには、CTRL + C キーを押してから、次のように入力します。

```
typeperf \Processor(_Total)\% Processor Time
```

ファイル内のカウンターの一覧の値を書き込むには、50のサンプルが収集されるまでの5秒のサンプル間隔で、タブ区切りのファイル*domain2*に*counters.txt* 、次のように入力します。

```
typeperf -cf counters.txt -si 5 -sc 50 -f TSV -o domain2.tsv
```

カウンターオブジェクト *PhysicalDisk* のインスタンスを使用してインストールされたカウンターを照会し、結果の一覧をファイル *counters.txt*に書き込むには、次のように入力します。

```
typeperf -qx PhysicalDisk -o counters.txt
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
