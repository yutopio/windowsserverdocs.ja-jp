---
title: scwcmd
description: セキュリティの構成ウィザード (SCW) に含まれる scwcmd.exe コマンドラインツールのリファレンス記事です。
ms.topic: reference
ms.assetid: 188ae881-c7d4-4a7a-b967-8fdc79f5f345
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 87bd2c718bec18810026c5701b955d5ef655b53e
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388922"
---
# <a name="scwcmd"></a>scwcmd

> 適用対象: Windows Server 2012 R2 および Windows Server 2012

セキュリティ構成ウィザード (SCW) に含まれている Scwcmd.exe コマンドラインツールを使用して、次のタスクを実行できます。

- SCW で生成されたポリシーを使用して 1 つまたは複数のサーバーを分析します。

- SCW で生成されたポリシーを使用して 1 つまたは複数のサーバーを構成します。

- SCW でセキュリティの構成データベースの拡張機能を登録します。

- SCW ポリシーをロールバックします。

- グループ ポリシーによってサポートされているネイティブのファイル、SCW で生成されたポリシーに変換します。

- HTML 形式では、分析結果を表示します。

> [!NOTE]
> **Scwcmd**を使用してリモートサーバー上のポリシーを構成、分析、またはロールバックする場合は、リモートサーバーに SCW がインストールされている必要があります。

## <a name="syntax"></a>構文

```
scwcmd analyze
scwcmd configure
scwcmd register
scwcmd rollback
scwcmd transform
scwcmd view
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| [scwcmd analyze](scwcmd-analyze.md) | コンピューターが、ポリシーに準拠しているかどうかを判断します。 |
| [scwcmd configure](scwcmd-configure.md) | SCW で生成されたセキュリティ ポリシーをコンピューターに適用されます。|
| [scwcmd register](scwcmd-register.md) | 拡張または役割、タスク、サービス、またはポートの定義を含むセキュリティの構成データベース ファイルを登録することにより、SCW のセキュリティ構成データベースをカスタマイズします。 |
| [scwcmd rollback](scwcmd-rollback.md) | 使用可能な最新のロールバックのポリシーを適用し、そのロールバックのポリシーを削除します。 |
| [scwcmd transform](scwcmd-transform.md) | Active Directory ドメイン サービスに新しいグループ ポリシー オブジェクト (GPO) に SCW を使用して、生成されたセキュリティ ポリシー ファイルを変換します。 |
| [scwcmd view](scwcmd-view.md) | 指定した .xsl 変換を使用して .xml ファイルを表示します。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
