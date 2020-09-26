---
title: secedit import
description: セキュリティテンプレートを使用して構成されたデータベースからエクスポートされたセキュリティ設定 (.inf ファイル) をインポートする、secedit import コマンドの参照記事。
ms.topic: reference
ms.assetid: 1dd59d4c-9d48-444a-871b-b957eb682597
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 35705012d32a196934c0834b3de0c67f7210270b
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388235"
---
# <a name="secedit-import"></a>secedit/import

セキュリティテンプレートを使用して構成されたデータベースから以前にエクスポートしたセキュリティ設定 (.inf ファイル) をインポートします。

> [!IMPORTANT]
> .Inf ファイルを別のコンピューターにインポートする前に、 `secedit /generaterollback` インポートが実行されるデータベースでコマンドを実行する必要があります。
>
> また、インポートファイルでコマンドを実行して、整合性を確認する必要があり `secedit /validate` ます。

## <a name="syntax"></a>構文

```
secedit /import /db <database file name> /cfg <configuration file name> [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /db | 必須です。 インポートを実行する保存された構成を含むデータベースのパスとファイル名を指定します。 ファイル名に、関連付けられている (構成ファイルによって表される) セキュリティテンプレートがないデータベースが指定されている場合は、 `/cfg <configuration file name>` オプションも指定する必要があります。 |
| /overwrite | データを格納されたテンプレートに追加するのではなく、 **/cfg** パラメーターのセキュリティテンプレートで、データベースに格納されているテンプレートまたは複合テンプレートを上書きするかどうかを指定します。 このオプションは、 `/cfg <configuration file name>` パラメーターも使用されている場合にのみ有効です。 このパラメーターも指定されていない場合は、 **/cfg** パラメーターのテンプレートが、格納されているテンプレートに追加されます。 |
| /cfg | 必須です。 分析用のデータベースにインポートするセキュリティ テンプレートのパスとファイル名を指定します。 このオプションは、パラメーターと共に使用する場合にのみ有効です `/db <database file name>` 。 このパラメーターも指定されていない場合は、データベースに既に格納されている構成に対して分析が実行されます。 |
| /areas | システムに適用するセキュリティ領域を指定します。 このパラメーターが指定されていない場合は、データベースで定義されているすべてのセキュリティ設定が、システムに適用されます。 複数の領域を構成するには、各領域をスペースで区切ります。 次のセキュリティの領域がサポートされています。<ul><li>**ws-securitypolicy:** アカウントポリシー、監査ポリシー、セキュリティオプションなど、システムのローカルポリシーとドメインポリシー。</li><li>  **group_mgmt:** セキュリティテンプレートで指定したグループの制限されたグループ設定。</li><li>**user_rights:** ユーザーのログオン権限と特権の付与。</li><li>**regkeys:** ローカルレジストリキーのセキュリティ。</li><li>**filestore:** ローカルファイルストレージのセキュリティ。</li><li>**サービス:** 定義されたすべてのサービスのセキュリティ。</li></ul> |
| /log | プロセスで使用するログ ファイルのパスとファイル名を指定します。 ファイルの場所を指定しない場合は、既定のログファイル `<systemroot>\Documents and Settings\<UserAccount>\My Documents\Security\Logs\<databasename>.log` が使用されます。 |
| スイッチを | 画面とログの出力を抑制します。 できます分析結果を表示する、セキュリティの構成と分析スナップインを Microsoft 管理コンソール (MMC) を使用しています。 |

## <a name="examples"></a>例

セキュリティデータベースとドメインセキュリティポリシーを .inf ファイルにエクスポートし、そのファイルを別のデータベースにインポートして別のコンピューターのポリシー設定をレプリケートするには、次のように入力します。

```
secedit /export /db C:\Security\FY11\SecDbContoso.sdb /mergedpolicy /cfg NetworkShare\Policies\SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log /quiet
```

ファイルのセキュリティポリシー部分のみを別のコンピューター上の別のデータベースにインポートするには、次のように入力します。

```
secedit /import /db C:\Security\FY12\SecDbContoso.sdb /cfg NetworkShare\Policies\SecContoso.inf /areas securitypolicy /log C:\Security\FY11\SecAnalysisContosoFY12.log /quiet
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [secedit/analyze](secedit-analyze.md)

- [secedit/configure](secedit-configure.md)

- [secedit/export](secedit-export.md)

- [secedit/generaterollback](secedit-generaterollback.md)

- [secedit/validate](secedit-validate.md)