---
title: secedit generaterollback
description: 指定された構成テンプレートのロールバックテンプレートを生成することができる、secedit generaterollback コマンドの参照記事です。
ms.topic: reference
ms.assetid: 385a6799-51a7-4fe3-bd73-10c7998b6680
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ae2e368ef387ea84095fcbcc51ad1e622225a2cc
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388818"
---
# <a name="secedit-generaterollback"></a>secedit/generaterollback

指定した構成テンプレートのロールバック テンプレートを生成できます。 既存のロールバックテンプレートが存在する場合、このコマンドを再実行すると、既存の情報が上書きされます。

このコマンドを正常に実行すると、指定したセキュリティテンプレートのセキュリティポリシーの構成と scesrv.dll ファイルとの不一致がログに記録されます。

## <a name="syntax"></a>構文

```
secedit /generaterollback /db <database file name> /cfg <configuration file name> /rbk <rollback template file name> [/log <log file name>] [/quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /db | 必須です。 分析の実行対象となる保存された構成を含むデータベースのパスとファイル名を指定します。 ファイル名に、関連付けられている (構成ファイルによって表される) セキュリティテンプレートがないデータベースが指定されている場合は、 `/cfg <configuration file name>` オプションも指定する必要があります。 |
| /cfg | 必須です。 分析用のデータベースにインポートするセキュリティ テンプレートのパスとファイル名を指定します。 このオプションは、パラメーターと共に使用する場合にのみ有効です `/db <database file name>` 。 このパラメーターも指定されていない場合は、データベースに既に格納されている構成に対して分析が実行されます。 |
| /rbk | 必須です。 ロールバック情報が書き込まれるセキュリティ テンプレートを指定します。 セキュリティ テンプレートを作成するには、セキュリティ テンプレート スナップインを使用します。 次のコマンドでは、ロールバック ファイルを作成できます。 |
| /log | プロセスで使用するログ ファイルのパスとファイル名を指定します。 ファイルの場所を指定しない場合は、既定のログファイル `<systemroot>\Documents and Settings\<UserAccount>\My Documents\Security\Logs\<databasename>.log` が使用されます。 |
| スイッチを | 画面とログの出力を抑制します。 できます分析結果を表示する、セキュリティの構成と分析スナップインを Microsoft 管理コンソール (MMC) を使用しています。 |

## <a name="examples"></a>例

以前に作成した *Sectmplcontoso .inf* ファイルのロールバック構成ファイルを作成し、元の設定を保存して、その操作を *SecAnalysisContosoFY11* ログファイルに書き込むには、次のように入力します。

```
secedit /generaterollback /db C:\Security\FY11\SecDbContoso.sdb /cfg sectmplcontoso.inf /rbk sectmplcontosoRBK.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [secedit/analyze](secedit-analyze.md)

- [secedit/configure](secedit-configure.md)

- [secedit/export](secedit-export.md)

- [secedit/import](secedit-import.md)

- [secedit/validate](secedit-validate.md)