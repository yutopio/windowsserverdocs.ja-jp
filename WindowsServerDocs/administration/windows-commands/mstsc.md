---
title: mstsc
description: Mstsc コマンドのリファレンス記事。リモートデスクトップセッションホストサーバーまたはその他のリモートコンピューターへの接続を作成し、既存のリモートデスクトップ接続 (.rdp) 構成ファイルを編集して、クライアント接続マネージャーで作成された従来の接続ファイルを新しい .rdp 接続ファイルに移行します。
ms.topic: reference
ms.assetid: 59801227-1e7e-4dbd-96e6-f54102a3ce92
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0a9c1eb46e2d6802c50dfc89e4a3085e6a6afca2
ms.sourcegitcommit: fe356f95188b7ce8e719765f44c0789c065832fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2020
ms.locfileid: "89057564"
---
# <a name="mstsc"></a>mstsc

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートデスクトップセッションホストサーバーまたはその他のリモートコンピューターへの接続を作成し、既存のリモートデスクトップ接続 (.rdp) 構成ファイルを編集して、クライアント接続マネージャーで作成された従来の接続ファイルを新しい .rdp 接続ファイルに移行します。

## <a name="syntax"></a>構文

```
mstsc.exe [<connectionfile>] [/v:<server>[:<port>]] [/admin] [/f] [/w:<width> /h:<height>] [/public] [/span]
mstsc.exe /edit <connectionfile>
mstsc.exe /migrate
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ------------|
| `<connectionfile>` | 接続の .rdp ファイルの名前を指定します。 |
| /v:`<server>[:<port>]` | リモートコンピューターと、必要に応じて接続するポート番号を指定します。 |
| /admin | サーバーを管理するためのセッションに接続します。 |
| /f | 全画面表示モードでリモート デスクトップ接続を起動します。 |
| /w`<width>` | リモートデスクトップウィンドウの幅を指定します。 |
| /h`<height>` | リモート デスクトップ ウィンドウの高さを指定します。 |
| /public | リモートデスクトップをパブリックモードで実行します。 パブリックモードでは、パスワードとビットマップはキャッシュされません。 |
| /span | リモートデスクトップの幅と高さをローカル仮想デスクトップと照合し、必要に応じて複数のモニターにまたがっています。 |
| /edit `<connectionfile>` | 指定した .rdp ファイルを編集用に開きます。 |
| /migrate | クライアント接続マネージャーで作成された従来の接続ファイルを新しい .rdp 接続ファイルに移行します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- 既定の .rdp は、ユーザーごとに隠しファイルとしてユーザーの **Documents** フォルダーに格納されます。

- ユーザーが作成した .rdp ファイルは、既定ではユーザーの **Documents** フォルダーに保存されますが、どこにでも保存できます。

- 複数のモニターにまたがる場合、モニターは同じ解像度を使用する必要があり、水平方向 (つまりサイドバイサイド) に調整する必要があります。 現在、クライアントシステム上で複数のモニターを垂直方向にまたがることはサポートされていません。

### <a name="examples"></a>例

全画面表示モードでセッションに接続するには、次のように入力します。

```
mstsc /f
```
または
```
mstsc /v:computer1 /f
```
幅/高さを割り当てるには、次のように入力します。

```
mstsc /v:computer1 /w:1920 /h:1080
```
編集するためにファイル *名 .rdp* という名前のファイルを開くには、次のように入力します。

```
mstsc /edit filename.rdp
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
