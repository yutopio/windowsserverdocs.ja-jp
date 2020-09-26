---
title: secedit analyze
description: Secedit analyze コマンドの参照記事。データベースに格納されているベースライン設定に対して現在のシステム設定を分析できます。
ms.topic: reference
ms.assetid: 3430cf9d-1411-48b1-b5a9-2e47701dc87f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 783f9d1042b860adefc49f58f38f66e0571468e3
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388558"
---
# <a name="secedit-analyze"></a>secedit/analyze

データベースに格納されているベースライン設定に対する現在のシステム設定を分析できます。

## <a name="syntax"></a>構文

```
secedit /analyze /db <database file name> [/cfg <configuration file name>] [/overwrite] [/log <log file name>] [/quiet}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /db | 必須です。 分析の実行対象となる保存された構成を含むデータベースのパスとファイル名を指定します。 ファイル名に、関連付けられている (構成ファイルによって表される) セキュリティテンプレートがないデータベースが指定されている場合は、 `/cfg <configuration file name>` オプションも指定する必要があります。 |
| /cfg | 分析用のデータベースにインポートするセキュリティ テンプレートのパスとファイル名を指定します。 このオプションは、パラメーターと共に使用する場合にのみ有効です `/db <database file name>` 。 このパラメーターも指定されていない場合は、データベースに既に格納されている構成に対して分析が実行されます。 |
| /overwrite | データを格納されたテンプレートに追加するのではなく、 **/cfg** パラメーターのセキュリティテンプレートで、データベースに格納されているテンプレートまたは複合テンプレートを上書きするかどうかを指定します。 このオプションは、 `/cfg <configuration file name>` パラメーターも使用されている場合にのみ有効です。 このパラメーターも指定されていない場合は、 **/cfg** パラメーターのテンプレートが、格納されているテンプレートに追加されます。 |
| /log | プロセスで使用するログ ファイルのパスとファイル名を指定します。 ファイルの場所を指定しない場合は、既定のログファイル `<systemroot>\Documents and Settings\<UserAccount>\My Documents\Security\Logs\<databasename>.log` が使用されます。 |
| スイッチを | 画面出力を抑制します。 できます分析結果を表示する、セキュリティの構成と分析スナップインを Microsoft 管理コンソール (MMC) を使用しています。 |

## <a name="examples"></a>例

セキュリティデータベースのセキュリティパラメーターの分析を実行するには、 *Secdbcontoso*を実行し、コマンドが正しく実行されたことを確認するプロンプトなど、出力 *をファイルに*送信します。

```
secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /log C:\Security\FY11\SecAnalysisContosoFY11.log
```

*SecAnalysisContosoFY11*ファイルで分析プロセスに必要な変更を組み込み、プロンプトを表示せずに、既存のファイルに出力を送信するには、次のように入力*します。*

```
secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /cfg SecContoso.inf /overwrite /log C:\Security\FY11\SecAnalysisContosoFY11.xml /quiet
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [secedit/configure](secedit-configure.md)

- [secedit/export](secedit-export.md)

- [secedit/generaterollback](secedit-generaterollback.md)

- [secedit/import](secedit-import.md)

- [secedit/validate](secedit-validate.md)