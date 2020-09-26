---
title: sfc
description: Sfc コマンドの参照記事。保護されたすべてのシステムファイルの整合性をスキャンおよび検証し、不適切なバージョンを正しいバージョンに置き換えます。
ms.topic: reference
ms.assetid: c58c25da-e028-42a6-9e10-973484a4b953
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 829c6e328ad0ea993e11cb5eb5d96d99f0d52476
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388942"
---
# <a name="sfc"></a>sfc

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

スキャンし、保護されているすべてのシステムの整合性がファイルし、正しいバージョンと正しくないバージョンが置き換えられますことを確認します。 このコマンドによって、保護されたファイルが上書きされたことが検出されると、 **systemroot\system32\dllcache** フォルダーから正しいバージョンのファイルが取得され、正しくないファイルが置き換えられます。

> [!IMPORTANT]
> このコマンドを実行するには、Administrators グループのメンバーとしてログオンする必要があります。

## <a name="syntax"></a>構文

```
sfc [/scannow] [/verifyonly] [/scanfile=<file>] [/verifyfile=<file>] [/offwindir=<offline windows directory> /offbootdir=<offline boot directory>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /scannow | すべての保護されたシステム ファイルの整合性をスキャンし、可能であれば、問題のあるファイルを修復します。 |
| /verifyonly | 修復を実行せずに、保護されたすべてのシステムファイルの整合性をスキャンします。 |
| /scanfile `<file>` | 指定されたファイル (完全パスとファイル名) の整合性をスキャンし、問題が検出された場合は修復を試みます。 |
| /verifyfile `<file>` | 修復を実行せずに、指定されたファイル (完全パスとファイル名) の整合性を確認します。 |
| /offwindir `<offline windows directory>` | オフライン修復用のオフラインの windows ディレクトリの場所を指定します。 |
| /offbootdir `<offline boot directory>` | オフライン修復用のオフラインブートディレクトリの場所を指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

確認する、 *kernel32.dll ファイル*, 、種類。

```
sfc /verifyfile=c:\windows\system32\kernel32.dll
```

オフラインのブートディレクトリを * D: に設定し、オフラインの windows ディレクトリを D:\windows に設定して、 *kernel32.dll*ファイルのオフライン修復をセットアップするには \* 、次のように入力します。 *D:\windows*

```
sfc /scanfile=D:\windows\system32\kernel32.dll /offbootdir=D:\ /offwindir=d:\windows
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
