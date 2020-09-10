---
title: logman delete
description: 既存のデータコレクターを削除する logman delete コマンドの参照記事です。
ms.topic: reference
ms.assetid: 8f3b2422-3dce-4fb4-adbb-8536b1d7da2b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 57d909a23e65de3c74daff4fe82f42943cb3875d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634375"
---
# <a name="logman-delete"></a>logman delete

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

既存のデータコレクターを削除します。

## <a name="syntax"></a>構文

```
logman delete <[-n] <name>> [options]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| -s `<computer name>` | 指定されたリモートコンピューターでコマンドを実行します。 |
| -config `<value>` | コマンドオプションを含む設定ファイルを指定します。 |
| [-n] `<name>` | 対象オブジェクトの名前。 |
| -/ | イベントトレースセッションに直接コマンドを送信します。保存もスケジュールもされません。 |
| -[-] u `<user [password]>` | として実行するユーザーを指定します。 パスワードのを入力すると、パスワードの入力を \* 求めるメッセージが表示されます。 パスワードは、パスワード用プロンプトで入力した場合は表示されません。 |
| /? | 状況依存のヘルプを表示します。 |

### <a name="examples"></a>例

データコレクター *perf_log*を削除するには、次のように入力します。

```
logman delete perf_log
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [logman コマンド](logman.md)
