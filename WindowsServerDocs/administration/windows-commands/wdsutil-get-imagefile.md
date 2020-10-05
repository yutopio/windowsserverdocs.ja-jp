---
title: get-help-イメージ
description: Windows イメージ (.wim) ファイルに格納されているイメージに関する情報を取得する、ファイルイメージの参照記事。
ms.topic: reference
ms.assetid: e1e296fb-20cf-4a60-9db4-4cbac7d4dab5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c358c490424406e6eb8d709c879f043ce017164d
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730793"
---
# <a name="get-imagefile"></a>get-help-イメージ

Windows イメージ (.wim) ファイルに含まれるイメージに関する情報を取得します。

## <a name="syntax"></a>構文

```
WDSUTIL [Options] /Get-ImageFile /ImageFile:<wim file path> [/Detailed]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|イメージ\<WIM file path>|.Wim ファイルの完全パスとファイル名を指定します。|
|[/詳細]|各イメージからすべてのイメージのメタデータを返します。 このオプションを使用しない場合、既定の動作は、イメージの名前、説明、およびファイル名のみを返すには。|

## <a name="examples"></a>例

イメージに関する情報を表示するには、次のように入力します。
```
WDSUTIL /Get-ImageFile /ImageFile:C:\temp\install.wim
```
詳細な情報を表示するには、次のように入力します。
```
WDSUTIL /Verbose /Get-ImageFile /ImageFile:\\Server\Share\My Folder \install.wim /Detailed
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)