---
title: tpmtool
description: トラステッドプラットフォームモジュールに関する情報を取得する tpmtool コマンドの参照記事です。
ms.topic: reference
author: ashleytqy
ms.author: asteoh
manager: raigner
ms.date: 05/07/2019
ms.openlocfilehash: bc0aaa4bc4bd9c23e0cf22b0315335287867d8cd
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156434"
---
# <a name="tpmtool"></a>tpmtool

このユーティリティは、 [トラステッドプラットフォームモジュール (TPM)](/windows/security/information-protection/tpm/trusted-platform-module-overview)に関する情報を取得するために使用できます。

>[!IMPORTANT]
>一部の情報はプレリリース版の製品に関連している場合があります。これは、販売を開始する前に大幅に変更されている可能性があります。 本書に記載された情報について、Microsoft は明示または黙示を問わずいかなる保証をするものでもありません。

## <a name="syntax"></a>構文

```
tpmtool /parameter [<arguments>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| getdeviceinformation | TPM の基本情報が表示されます。 情報フラグの値の詳細については、 [Win32_Tpm:: IsReadyInformation メソッドのパラメーター](/windows/win32/secprov/win32-tpm-isreadyinformation#parameters) に関する記事を参照してください。 |
| gatherlogs [出力ディレクトリのパス] | TPM ログを収集し、指定したディレクトリに格納します。 このディレクトリが存在しない場合は作成されます。 既定では、ログファイルは現在のディレクトリに配置されます。 生成される可能性があるファイルは次のとおりです。<ul><li>TpmEvents</li><li>TpmInformation.txt</li><li>SRTMBoot dat</li><li>SRTMResume. dat</li><li>DRTMBoot dat</li><li>DRTMResume</li></ul> |
| drivertracing `[start | stop]` | TPM ドライバーのトレースの収集を開始または停止します。 トレースログ *TPMTRACE*が作成され、現在のディレクトリに配置されます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>使用例

TPM の基本情報を表示するには、次のように入力します。

```
tpmtool getdeviceinformation
```

TPM ログを収集して現在のディレクトリに配置するには、次のように入力します。

```
tpmtool gatherlogs
```

TPM ログを収集してに配置するには、次のように `C:\Users\Public` 入力します。

```
tpmtool gatherlogs C:\Users\Public
```

TPM ドライバーのトレースを収集するには、次のように入力します。

```
tpmtool drivertracing start
# Run scenario
tpmtool drivertracing stop
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [COM エラーコード (TPM、PLA、FVE)](/windows/win32/com/com-error-codes-6)
