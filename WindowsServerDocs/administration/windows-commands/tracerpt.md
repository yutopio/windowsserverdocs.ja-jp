---
title: tracerpt
description: Tracerpt コマンドのリファレンス記事。イベントトレースログ、パフォーマンスモニターによって生成されたログファイル、およびリアルタイムのイベントトレースプロバイダーを解析します。
ms.topic: reference
ms.assetid: cb9eaf86-0ef6-4197-b6c8-9cca8a1d723c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1e468dab3c99219560047668f9f1bd001e8e451e
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156713"
---
# <a name="tracerpt"></a>tracerpt

**Tracerpt**コマンドは、イベントトレースログ、パフォーマンスモニターによって生成されるログファイル、およびリアルタイムのイベントトレースプロバイダーを解析します。 また、ダンプファイル、レポートファイル、およびレポートスキーマも生成します。

## <a name="syntax"></a>構文

```
tracerpt <[-l] <value [value [...]]>|-rt <session_name [session_name [...]]>> [options]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -config `<filename>` | コマンドオプションを含む、読み込む設定ファイルを指定します。 |
| -y | プロンプトを表示せずにすべての質問に対して **[はい]** を回答するように指定します。 |
| -f `<XML | HTML>` | レポートファイルの形式を指定します。 |
| -/ `<CSV | EVTX | XML>` | ダンプファイルの形式を指定します。 既定値は **XML*です。 |
| -df `<filename>` | Microsoft 固有のカウント/レポートスキーマファイルを作成することを指定します。 |
| -int `<filename>` | 解釈されたイベント構造を指定したファイルにダンプするように指定します。 |
| -rts | イベントトレースヘッダーにレポートの生のタイムスタンプを追加するように指定します。 は **、-o**と共にのみ使用できます。 **-Report**または **-summary**ではサポートされていません。 |
| -tmf `<filename>` | 使用するトレースメッセージ形式定義ファイルを指定します。 |
| -tp `<value>` | TMF ファイルの検索パスを指定します。 セミコロン (;) で区切られた複数のパスを使用できます。 |
| -i `<value>` | プロバイダーイメージのパスを指定します。 一致する PDB は、シンボルサーバーに配置されます。 複数のパスを使用して、セミコロン (;) で区切ることができます。 |
| -pdb `<value>` | シンボルサーバーパスを指定します。 複数のパスを使用して、セミコロン (;) で区切ることができます。 |
| -gmt | WPP ペイロードのタイムスタンプをグリニッジ標準時に変換することを指定します。 |
| -rl `<value>` | システムレポートレベルを 1 ~ 5 のレベルで指定します。 既定値は *1*です。 |
| -summary [ファイル名] | 概要レポートのテキストファイルを作成することを指定します。 ファイル名が指定されていない場合は、 *summary.txt*ます。 |
| -o [ファイル名] | テキスト出力ファイルを作成することを指定します。 ファイル名が指定されていない場合は、 *dumpfile.xml*ます。 |
| -レポート [ファイル名] | テキスト出力レポートファイルを作成することを指定します。 ファイル名が指定されていない場合は、 *workload.xml*ます。 |
| -lr | 制限を低くすることを指定します。 これは、events スキーマに一致しないイベントに対して最適な作業を行います。 |
| -export [ファイル名] | イベントスキーマエクスポートファイルを作成することを指定します。 ファイル名が指定されていない場合は、 *schema. man*となります。 |
| [-l] `<value [value […]]>` | 処理するイベントトレースログファイルを指定します。 |
| -rt `<session_name [session_name […]]>` | リアルタイムイベントトレースセッションのデータソースを指定します。 |
| -? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>使用例

2つのイベントログ*logfile1*と*logfile2*に基づいてレポートを作成し、ダンプファイルを*XML*形式で作成*logdump.xml*には、次のように入力します。

```
tracerpt logfile1.etl logfile2.etl -o logdump.xml -of XML
```

イベントログの *ログ* *logdmp.xml* ファイルに基づいてレポートを作成するには、XML 形式でダンプファイルを作成するために、スキーマに含まれていないイベントを特定するために最適な方法を使用し、概要レポートファイル *logdump.txt* とレポートファイル *logrpt.xml*を生成するために、次のように入力します。

```
tracerpt logfile.etl -o logdmp.xml -of XML -lr -summary logdmp.txt -report logrpt.xml
```

2つのイベントログ *logfile1* と *logfile2* を使用してダンプファイルを生成し、既定のファイル名を含むレポートファイルを作成するには、次のように入力します。

```
tracerpt logfile1.etl logfile2.etl -o -report
```

イベント *ログのログファイル* と、パフォーマンスログのファイル *.blg* を使用してレポートファイルを生成するには、次のように入力します。 *logrpt.xml* 、Microsoft 固有の XML スキーマファイル *schema.xml*です。

```
tracerpt logfile.etl counterfile.blg -report logrpt.xml -df schema.xml
```

リアルタイムイベントトレースセッション NT カーネルロガーを読み取り、 *CSV*形式の*logfile.csv*ダンプファイルを生成するには、次のように入力します。

```
tracerpt -rt NT Kernel Logger -o logfile.csv -of CSV
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
