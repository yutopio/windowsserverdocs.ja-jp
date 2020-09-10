---
title: pnpunattend
description: Pnpunattend コマンドの参照記事。コンピューター上のデバイスドライバーを監査するだけでなく、サイレントドライバインストールも実行します。
ms.topic: reference
ms.assetid: 4fa88932-cff0-4dfc-936c-98c0e3dfbeb8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 6e3e0f0dfd1b689a62bf59956d3934e5ea74d177
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633671"
---
# <a name="pnpunattend"></a>pnpunattend

デバイス ドライバー用にコンピューターを監査およびドライバーの無人インストールを実行またはドライバーをインストールしなくても検索され、必要に応じて、コマンドラインに結果を報告します。 このコマンドを使用して、特定のハードウェア デバイスの特定のドライバーのインストールを指定します。

## <a name="prerequisites"></a>前提条件

以前のバージョンの Windows オペレーティングシステムでは、事前準備が必要です。 このコマンドを使用する前に、次のタスクを完了する必要があります。

1. インストールするドライバー用のディレクトリを作成します。 たとえばでフォルダーを作成 **C:\Drivers\Video** のビデオ アダプターのドライバーです。

2. ダウンロードして、デバイスのドライバー パッケージを抽出します。 オペレーティング システムのバージョンの INF ファイルを含むサブフォルダーおよびサブフォルダーの内容を作成したビデオ フォルダーにコピーします。 たとえば、ビデオドライバーファイルを **C:\Drivers\Video**にコピーします。

3. たとえば、手順 1. で作成したフォルダーにシステム環境のパス変数を追加 **C:\Drivers\Video**します。

4. 次のレジストリ キーを作成し、 **DriverPaths** キーセットを作成する、 **値のデータ** に **1**します。

5. Windows®7の場合は、レジストリパス**HKEY_LOCAL_Machine \Software\microsoft\windows NT\CurrentVersion \\ **に移動し、キー **UnattendSettings\PnPUnattend\DriverPaths \\ **を作成します。

## <a name="syntax"></a>構文

```
PnPUnattend.exe auditsystem [/help] [/?] [/h] [/s] [/l]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| auditsystem | オンラインでのドライバーのインストールを指定します。<p>必須。ただし、 **/help** または/? でこのコマンドを実行する場合を除き **ます。** %2!d! です。 |
| /s | 省略可能。 インストールしなくてもドライバーの検索を指定します。 |
| /l | 省略可能。 コマンド プロンプトで、このコマンドのログ情報を指定します。 |
| `/? | /help` | 省略可能。 コマンド プロンプトで次のコマンドのヘルプを表示します。 |

### <a name="examples"></a>例

次のコマンドは、 **PNPUnattend.exe** を使用してコンピューターを監査し、ドライバーが更新される可能性があるかどうかを確認し、結果をコマンドプロンプトに報告する方法を示しています。

```
pnpunattend auditsystem /s /l
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
