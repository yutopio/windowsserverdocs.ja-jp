---
title: cscript
description: 'Windows コマンド」のトピック * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fba3cbca-594e-4663-bb22-4ee0f63a1ac6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ffdbd6f67e4e4c32022134191deabd861bf248b9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827673"
---
# <a name="cscript"></a>cscript

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

コマンドライン環境で実行されるように、スクリプトを開始します。
## <a name="syntax"></a>構文
```
cscript <Scriptname.extension> [/B] [/D] [/E:<Engine>] [{/H:cscript|/H:wscript}] [/I] [/Job:<Identifier>] [{/Logo|/NoLogo}] [/S] [/T:<Seconds>] [/X] [/U] [/?] [<ScriptArguments>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|Scriptname.extension|省略可能なファイル名拡張子を持つスクリプト ファイルのパスとファイル名を指定します。|
|/B|アラート、スクリプトのエラー、または入力プロンプトは表示されませんが、バッチ モードを指定します。|
|/D|デバッガーを起動します。|
|/E:<Engine>|スクリプトを実行するために使用するエンジンを指定します。|
|/H:cscript|スクリプトを実行するための既定のスクリプト ホストとして cscript.exe を登録します。|
|/H:wscript|スクリプトを実行するための既定のスクリプト ホストとして wscript.exe を登録します。 これが既定値です。|
|/I|警告、スクリプト エラーは、入力プロンプトを表示する対話型モードを指定します。 これは、既定と反対の **/B**します。|
|/Job:<Identifier>|によって識別されるジョブの実行*識別子*.wsf スクリプト ファイル。|
|/ロゴ|スクリプトを実行する前に、コンソールで、Windows Script Host のバナーが表示されることを指定します。 これは、既定と反対の **/Nologo**します。|
|/Nologo|スクリプトの実行前に、Windows Script Host のバナーが表示されないことを指定します。|
|/S|現在のユーザーの現在のコマンド プロンプト オプションを保存します。|
|/T:<Seconds>|スクリプトは、秒単位で実行できる最長時間を指定します。 最大で 32,767 秒を指定することができます。 既定値には、時間制限はありません。|
|/U|入力と出力をコンソールからがリダイレクトされるは、Unicode を指定します。|
|/X|デバッガーでスクリプトを開始します。|
|/?|使用可能なコマンドのパラメーターを表示し、それらの使用に関するヘルプを提供します。 これは入力と同じ**cscript.exe**パラメーターがないとスクリプトをします。|
|ScriptArguments|スクリプトに渡される引数を指定します。 各スクリプトの引数の前に、スラッシュでする必要があります (**/**)。|
### <a name="remarks"></a>注釈
-   この作業を実行するときは、管理者資格情報は必要ありません。 つまり、セキュリティを考慮するうえで最適な方法として、管理者資格情報のないユーザーとしてこのタスクを実行することを検討してください。
-   コマンド プロンプトを開くには**開始**画面で「 **cmd**、順にクリックします**コマンド プロンプト**します。
-   各パラメーターは省略可能です。ただし、スクリプトを指定せずにスクリプトの引数を指定することはできません。 スクリプトまたは任意のスクリプトの引数を指定しない場合、cscript.exe は、cscript.exe の構文と、有効なホスト オプションを表示します。
-   **/T**パラメーターは、タイマーを設定してスクリプトの過剰な実行を防止します。 実行時では、指定した値を超える、cscript はスクリプト エンジンを中断し、プロセスを終了します。
-   Windows スクリプト ファイルが通常は次のファイル名拡張子のいずれかをある: .wsf、.vbs、.js。
-   個々 のスクリプトのプロパティを設定することができます。 詳細については、関連トピックを参照してください。
-   Windows スクリプト ホストでは、.wsf スクリプト ファイルを使用できます。 各 .wsf ファイルは、複数のスクリプト エンジンを使用し、複数のジョブを実行できます。
-   関連付けを持たない拡張機能を含むスクリプト ファイルをダブルクリックする場合、**プログラムから開く** ダイアログ ボックスが表示されます。 wscript と cscript のどちらを選択し、選択**常にこのプログラムを使用して、この種類のファイルを開く**します。 この種類のファイルの既定のスクリプト ホストとして wscript.exe と cscript のどちらが登録します。
-   個々 のスクリプトのプロパティを設定することができます。 参照してください[その他の参照](#BKMK_references)詳細についてはします。
-   Windows スクリプト ホストでは、.wsf スクリプト ファイルを使用できます。 各 .wsf ファイルは、複数のスクリプト エンジンを使用し、複数のジョブを実行できます。

#### <a name="BKMK_references"></a>その他の参照

[コマンドライン構文キー](command-line-syntax-key.md)