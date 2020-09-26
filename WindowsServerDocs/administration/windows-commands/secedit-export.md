---
title: secedit export
description: セキュリティテンプレートを使用して構成されたデータベースに格納されているセキュリティ設定をエクスポートする、secedit エクスポートの参照記事。
ms.topic: reference
ms.assetid: 49a8b241-aa8c-45b7-844d-67a29fab708e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: dfd766674a4e4ac2e9552d36b4cb706117c173bd
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388245"
---
# <a name="secedit-export"></a>secedit/export

セキュリティ テンプレートで構成されるデータベースに格納されているセキュリティ設定をエクスポートします。 このコマンドを使用すると、設定を別のコンピューターにインポートするだけでなく、ローカルコンピューター上のセキュリティポリシーをバックアップすることもできます。

## <a name="syntax"></a>構文

```
secedit /export /db <database file name> [/mergedpolicy] /cfg <configuration file name> [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /db | 必須です。 エクスポートの実行対象となる保存された構成を含むデータベースのパスとファイル名を指定します。 ファイル名に、関連付けられている (構成ファイルによって表される) セキュリティテンプレートがないデータベースが指定されている場合は、 `/cfg <configuration file name>` オプションも指定する必要があります。 |
| /mergedpolicy | マージし、ドメインとローカル ポリシーのセキュリティ設定をエクスポートします。 |
| /cfg | 必須です。 分析用のデータベースにインポートするセキュリティ テンプレートのパスとファイル名を指定します。 このオプションは、パラメーターと共に使用する場合にのみ有効です `/db <database file name>` 。 このパラメーターも指定されていない場合は、データベースに既に格納されている構成に対して分析が実行されます。 |
| /areas | システムに適用するセキュリティ領域を指定します。 このパラメーターが指定されていない場合は、データベースで定義されているすべてのセキュリティ設定が、システムに適用されます。 複数の領域を構成するには、各領域をスペースで区切ります。 次のセキュリティの領域がサポートされています。<ul><li>**ws-securitypolicy:** アカウントポリシー、監査ポリシー、セキュリティオプションなど、システムのローカルポリシーとドメインポリシー。</li><li>  **group_mgmt:** セキュリティテンプレートで指定したグループの制限されたグループ設定。</li><li>**user_rights:** ユーザーのログオン権限と特権の付与。</li><li>**regkeys:** ローカルレジストリキーのセキュリティ。</li><li>**filestore:** ローカルファイルストレージのセキュリティ。</li><li>**サービス:** 定義されたすべてのサービスのセキュリティ。</li></ul> |
| /log | プロセスで使用するログ ファイルのパスとファイル名を指定します。 ファイルの場所を指定しない場合は、既定のログファイル `<systemroot>\Documents and Settings\<UserAccount>\My Documents\Security\Logs\<databasename>.log` が使用されます。 |
| スイッチを | 画面とログの出力を抑制します。 できます分析結果を表示する、セキュリティの構成と分析スナップインを Microsoft 管理コンソール (MMC) を使用しています。 |

## <a name="examples"></a>例

セキュリティデータベースとドメインセキュリティポリシーを inf ファイルにエクスポートし、別のコンピューターのセキュリティポリシー設定をレプリケートするためにそのファイルを別のデータベースにインポートするには、次のように入力します。

```
secedit /export /db C:\Security\FY11\SecDbContoso.sdb /mergedpolicy /cfg SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log /quiet
```

例のファイルを別のコンピューター上の別のデータベースにインポートするには、次のように入力します。

```
secedit /import /db C:\Security\FY12\SecDbContoso.sdb /cfg SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY12.log /quiet
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [secedit/analyze](secedit-analyze.md)

- [secedit/configure](secedit-configure.md)

- [secedit/generaterollback](secedit-generaterollback.md)

- [secedit/import](secedit-import.md)

- [secedit/validate](secedit-validate.md)