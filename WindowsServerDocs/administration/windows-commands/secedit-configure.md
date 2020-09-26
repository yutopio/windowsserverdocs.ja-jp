---
title: secedit configure
description: Secedit configure コマンドの参照記事。データベースに格納されているセキュリティ設定を使用して、現在のシステム設定を構成できます。
ms.topic: reference
ms.assetid: a92e68ca-003c-4219-8655-0e7734f5fab3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 39f69651a69a748acf65727ecec0bcbe4b9c911a
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388225"
---
# <a name="secedit-configure"></a>secedit/configure

データベースに格納されているセキュリティ設定を使用して現在のシステム設定を構成できます。

## <a name="syntax"></a>構文

```
secedit /configure /db <database file name> [/cfg <configuration file name>] [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /db | 必須です。 格納されている構成を含むデータベースのパスとファイル名を指定します。 ファイル名に、関連付けられている (構成ファイルによって表される) セキュリティテンプレートがないデータベースが指定されている場合は、 `/cfg <configuration file name>` オプションも指定する必要があります。 |
| /cfg | 分析用のデータベースにインポートするセキュリティ テンプレートのパスとファイル名を指定します。 このオプションは、パラメーターと共に使用する場合にのみ有効です `/db <database file name>` 。 このパラメーターも指定されていない場合は、データベースに既に格納されている構成に対して分析が実行されます。 |
| /overwrite | データを格納されたテンプレートに追加するのではなく、 **/cfg** パラメーターのセキュリティテンプレートで、データベースに格納されているテンプレートまたは複合テンプレートを上書きするかどうかを指定します。 このオプションは、 `/cfg <configuration file name>` パラメーターも使用されている場合にのみ有効です。 このパラメーターも指定されていない場合は、 **/cfg** パラメーターのテンプレートが、格納されているテンプレートに追加されます。 |
| /areas | システムに適用するセキュリティ領域を指定します。 このパラメーターが指定されていない場合は、データベースで定義されているすべてのセキュリティ設定が、システムに適用されます。 複数の領域を構成するには、各領域をスペースで区切ります。 次のセキュリティの領域がサポートされています。<ul><li>**ws-securitypolicy:** アカウントポリシー、監査ポリシー、セキュリティオプションなど、システムのローカルポリシーとドメインポリシー。</li><li>  **group_mgmt:** セキュリティテンプレートで指定したグループの制限されたグループ設定。</li><li>**user_rights:** ユーザーのログオン権限と特権の付与。</li><li>**regkeys:** ローカルレジストリキーのセキュリティ。</li><li>**filestore:** ローカルファイルストレージのセキュリティ。</li><li>**サービス:** 定義されたすべてのサービスのセキュリティ。</li></ul> |
| /log | プロセスで使用するログ ファイルのパスとファイル名を指定します。 ファイルの場所を指定しない場合は、既定のログファイル `<systemroot>\Documents and Settings\<UserAccount>\My Documents\Security\Logs\<databasename>.log` が使用されます。 |
| スイッチを | 画面とログの出力を抑制します。 できます分析結果を表示する、セキュリティの構成と分析スナップインを Microsoft 管理コンソール (MMC) を使用しています。 |

## <a name="examples"></a>例

セキュリティデータベースのセキュリティパラメーターの分析を実行するには、 *Secdbcontoso*を実行し、コマンドが正しく実行されたことを確認するプロンプトなど、出力 *をファイルに*送信します。

```
secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /log C:\Security\FY11\SecAnalysisContosoFY11.log
```

*SecAnalysisContosoFY11*ファイルで分析プロセスに必要な変更を組み込み、プロンプトを表示せずに、既存のファイルに出力を送信するには、次のように入力*します。*

```
secedit /configure /db C:\Security\FY11\SecDbContoso.sdb /cfg SecContoso.inf /overwrite /log C:\Security\FY11\SecAnalysisContosoFY11.xml /quiet
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [secedit/analyze](secedit-analyze.md)

- [secedit/export](secedit-export.md)

- [secedit/generaterollback](secedit-generaterollback.md)

- [secedit/import](secedit-import.md)

- [secedit/validate](secedit-validate.md)