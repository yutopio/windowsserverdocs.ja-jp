---
title: cscript
description: Cscript コマンドのリファレンス記事。コマンドライン環境で実行されるようにスクリプトを開始します。
ms.topic: reference
ms.assetid: fba3cbca-594e-4663-bb22-4ee0f63a1ac6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2e35efeccc219a7e678e2eccab74de5d0c4d6837
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628990"
---
# <a name="cscript"></a>cscript

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

コマンドライン環境で実行するスクリプトを開始します。

>[!IMPORTANT]
> このタスクを実行するときは、管理資格情報は必要ありません。 そのため、セキュリティ対策として、このタスクは管理資格情報のないユーザーとして実行することを検討してください。

## <a name="syntax"></a>構文

```
cscript <scriptname.extension> [/b] [/d] [/e:<engine>] [{/h:cscript | /h:wscript}] [/i] [/job:<identifier>] [{/logo | /nologo}] [/s] [/t:<seconds>] [x] [/u] [/?] [<scriptarguments>]
```

#### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| scriptname | オプションのファイル名拡張子を持つスクリプトファイルのパスとファイル名を指定します。 |
| /b | アラート、スクリプトエラー、入力プロンプトを表示しないバッチモードを指定します。 |
| /d | デバッガーを起動します。 |
| /e:`<engine>` | スクリプトの実行に使用するエンジンを指定します。 |
| /h: cscript | スクリプトを実行するための既定のスクリプトホストとして cscript.exe を登録します。 |
| /h: wscript | スクリプトを実行するための既定のスクリプトホストとして wscript.exe を登録します。 これは既定です。 |
| /i | アラート、スクリプトエラー、および入力プロンプトを表示する対話モードを指定します。 これは既定値であり、の逆 `/b` です。 |
| /ジョブ (<identifier> | Wsf スクリプトファイル内の *識別子* によって識別されるジョブを実行します。 |
| /ロゴ | スクリプトを実行する前に、Windows スクリプトホストバナーをコンソールに表示することを指定します。 これは既定値であり、の逆 `/nologo` です。 |
| /nologo | スクリプトを実行する前に、Windows スクリプトホストバナーを表示しないように指定します。 |
| /s | 現在のユーザーの現在のコマンドプロンプトオプションを保存します。 |
| /t: <seconds> | スクリプトを実行できる最長時間を秒単位で指定します。 最大32767秒を指定できます。 既定では、時間制限はありません。 |
| /U | コンソールからリダイレクトされる入力と出力の Unicode を指定します。 |
| /x | デバッガーでスクリプトを開始します。 |
| /? | 使用可能なコマンドパラメーターを表示し、それらを使用するためのヘルプを提供します。 これは、パラメーターを指定せずに **cscript.exe** を入力する場合と同じですが、スクリプトはありません。 |
| scriptarguments | スクリプトに渡される引数を指定します。 各スクリプト引数の前にはスラッシュ () を付ける必要があり **/** ます。 |

#### <a name="remarks"></a>注釈

- 各パラメーターは省略可能です。ただし、スクリプトを指定せずにスクリプトの引数を指定することはできません。 スクリプトまたはスクリプトの引数を指定しない場合は、cscript.exe の構文と有効なホストオプションが cscript.exe 表示されます。

- **/T**パラメーターを指定すると、タイマーを設定することによって、スクリプトの過剰な実行を防ぐことができます。 実行時間が指定された値を超えると、cscript はスクリプトエンジンを中断し、プロセスを終了します。

- Windows スクリプトファイルは、通常、次のファイル名拡張子のいずれかになります。 wsf、.vbs、.js。 Windows スクリプトホストでは、wsf スクリプトファイルを使用できます。 各 wsf ファイルは、複数のスクリプトエンジンを使用して複数のジョブを実行できます。

- 拡張子が関連付けられていないスクリプトファイルをダブルクリックすると、[ **ファイルを開くアプリケーション** の選択] ダイアログボックスが表示されます。 [Wscript] または [cscript] を選択し、[この **ファイルの種類を開くには常にこのプログラムを使用する**] を選択します。 これにより、このファイルの種類のファイルの既定のスクリプトホストとして wscript.exe または cscript が登録されます。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
