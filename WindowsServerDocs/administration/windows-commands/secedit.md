---
title: secedit コマンド
description: Secedit コマンドの参照記事。現在のセキュリティ構成を指定されたセキュリティテンプレートと比較します。
ms.topic: reference
ms.assetid: 58ed57ed-08e3-403d-a363-0620b358637a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ceb1a28376c17ab9d08689c7b0367dd90fdecc4f
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388289"
---
# <a name="secedit-commands"></a>secedit コマンド

現在のセキュリティ構成を指定されたセキュリティテンプレートと比較することによって、システムのセキュリティを構成および分析します。

> [!NOTE]
> Microsoft 管理コンソール (MMC) とセキュリティの構成と分析スナップインでは、Server Core では使用できません。

## <a name="syntax"></a>構文

```
secedit /analyze
secedit /configure
secedit /export
secedit /generaterollback
secedit /import
secedit /validate
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| [secedit/analyze](secedit-analyze.md) | データベースに格納されているベースライン設定に対する現在のシステム設定を分析できます。  分析結果は、データベースの独立した領域には保存され、セキュリティの構成と分析スナップインで表示できます。 |
| [secedit/configure](secedit-configure.md) | 使用すると、システム データベースに格納されているセキュリティ設定を構成できます。 |
| [secedit/export](secedit-export.md) | データベースに格納されているセキュリティ設定をエクスポートできます。 |
| [secedit/generaterollback](secedit-generaterollback.md) | 構成テンプレートに関してロールバック テンプレートを生成できます。 |
| [secedit/import](secedit-import.md) | テンプレートで指定された設定をシステムに適用またはシステムに照らして分析できるように、データベースにセキュリティ テンプレートをインポートできます。 |
| [secedit/validate](secedit-validate.md) | セキュリティ テンプレートの構文を検証できます。 |

#### <a name="remarks"></a>解説

- Filepath が指定されていない場合は、すべてのファイル名が既定で現在のディレクトリに設定されます。

- 分析結果はデータベースの別の領域に格納され、[セキュリティの構成と分析] スナップインで MMC に表示できます。

- セキュリティテンプレートスナップインを使用してセキュリティテンプレートを作成し、それらのテンプレートに対してセキュリティの構成と分析スナップインを実行すると、次のファイルが作成されます。

    | ファイル | 説明 |
    |--|--|
    | scesrv.dll | <ul><li>**場所:**`%windir%\security\logs`</li><li>**作成者:** オペレーティング システム</li><li>**ファイルの種類:** 本文</li><li>**更新頻度:**`secedit analyze`、 `secedit configure` 、または `secedit export` が実行されるときに上書き `secedit import` されます。</li><li>**コンテンツ:** ポリシーの種類ごとにグループ化された分析の結果が含まれます。</li></ul> |
    | *ユーザーが選択した名前*sdb | <ul><li>**場所:**`%windir%\<user account>\Documents\Security\Database`</li><li>**作成者:** セキュリティの構成と分析スナップインの実行</li><li>**ファイルの種類:** 各社</li><li>**更新頻度:** 新しいセキュリティテンプレートが作成されるたびに更新されます。</li><li>**コンテンツ:** ローカルセキュリティポリシーとユーザーが作成したセキュリティテンプレート。</li></ul> |
    | *ユーザーが選択した名前*.log | <ul><li>**場所:** ユーザー定義ですが、既定値は `%windir%\<user account>\Documents\Security\Logs`</li><li>**作成者:**`secedit analyze`コマンドまたは `secedit configure` コマンドを実行するか、セキュリティの構成と分析スナップインを使用します。</li><li>**ファイルの種類:** 本文</li><li>**更新頻度:** または `secedit analyze` の `secedit configure` 実行時、またはセキュリティの構成と分析スナップインを使用して上書きされます。</li><li>**コンテンツ:** ログファイル名、日付と時刻、および分析または調査の結果。</li></ul> |
    | *ユーザーが選択した名前 (.inf)* | <ul><li>**場所:**`%windir%\*<user account>\Documents\Security\Templates`</li><li>**作成者:** セキュリティテンプレートスナップインを実行しています。</li><li>**ファイルの種類:** 本文</li><li>**更新頻度:** セキュリティテンプレートが更新されるたびに上書きされます。</li><li>**コンテンツ:** スナップインを使用して選択した各ポリシーのテンプレートに関する設定情報が含まれます。</li></ul> |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
