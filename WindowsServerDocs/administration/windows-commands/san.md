---
title: san
description: San コマンドの参照記事。オペレーティングシステムの記憶域ネットワーク (san) ポリシーを表示または設定します。
ms.topic: reference
ms.assetid: d57c2df1-eb82-4b81-b8cd-e30564c6a929
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8881855e77f8df579cb054954d26296edf4c971f
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388371"
---
# <a name="san"></a>san

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

オペレーティングシステムの記憶域ネットワーク (san) ポリシーを表示または設定します。 パラメーターを指定せずに使用した場合は、現在の san ポリシーが表示されます。

## <a name="syntax"></a>構文

```
san [policy={onlineAll | offlineAll | offlineShared}] [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| ポリシー = {全オンライン|offlineAll|オフライン共有}] | 現在ブートされているオペレーティングシステムの san ポリシーを設定します。 San ポリシーは、新しく検出されたディスクをオンラインにするか、オフラインのままにするか、読み取り/書き込み可能または読み取り専用のままにするかを決定します。 ディスクがオフラインのときは、ディスク レイアウトを読み取るがからプラグ アンド プレイ デバイスのボリュームは発生しません。 これは、ディスク上のファイル システムがマウントしないことを意味します。 ディスクがオンラインのとき、ディスクの 1 つまたは複数のボリュームのデバイスがインストールされます。 各パラメーターの説明を次に示します。<ul><li>**全オンライン**。 新しく検出されたすべてのディスクはオンラインで行われた読み取り/書き込みにするかを指定します。 **重要:** ディスクを共有するサーバーで [オンラインにする ( **すべて** ) を指定すると、データが破損する可能性があります。 そのため、サーバーがクラスターの一部でない限り、ディスクがサーバー間で共有されている場合は、このポリシーを設定しないでください。</li><li>**Offlineall**。 スタートアップディスクを除く、新しく検出されたすべてのディスクをオフラインにし、既定で読み取り専用にすることを指定します。</li><li>**オフライン共有**。 共有バス (SCSI、iSCSI など) に常駐していないディスクがオンラインに戻るを検出し、読み取り/書き込みが行われたすべての新しくを指定します。 オフラインのまま、ディスクは、既定では読み取り専用になります。</li></ul>詳細については、「 [VDS_san_POLICY 列挙型](https://docs.microsoft.com/windows/win32/api/vds/ne-vds-vds_san_policy?redirectedfrom=MSDN)」を参照してください。 |
| noerr | スクリプト作成にのみ使用されます。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>例

現在のポリシーを表示するには、次のように入力します。

```
san
```

起動ディスクを除くすべての新しく検出されたディスクをオフラインであり、既定では読み取り専用にするには、次のように入力します。

```
san policy=offlineAll
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
