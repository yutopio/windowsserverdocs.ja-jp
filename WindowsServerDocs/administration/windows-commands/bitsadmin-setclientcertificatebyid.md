---
title: bitsadmin setclientcertificatebyid
description: Bitsadmin setclientcertificatebyid コマンドの参照記事。 HTTPS (SSL) 要求でクライアント認証に使用するクライアント証明書の識別子を指定します。
ms.topic: reference
ms.assetid: 8585a7a1-7472-437b-b04a-a11925782a3a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: aa49c0fc93972ce447c114ec20722afe67ca5dda
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631035"
---
# <a name="bitsadmin-setclientcertificatebyid"></a>bitsadmin setclientcertificatebyid

HTTPS (SSL) 要求でクライアント認証に使用するクライアント証明書の識別子を指定します。

## <a name="syntax"></a>構文

```
bitsadmin /setclientcertificatebyid <job> <store_location> <store_name> <hexadecimal_cert_id>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| store_location | 次のような、証明書の検索に使用するシステムストアの場所を指定します。<ul><li>CURRENT_USER</li><li>LOCAL_MACHINE</li><li>CURRENT_SERVICE</li><li>サービス</li><li>ユーザー</li><li>CURRENT_USER_GROUP_POLICY</li><li>LOCAL_MACHINE_GROUP_POLICY</li><li>LOCAL_MACHINE_ENTERPRISE。</li></ul> |
| store_name | 証明書ストアの名前 (以下を含む)。<ul><li>CA (証明機関の証明書)</li><li>MY (個人用証明書)</li><li>ルート (ルート証明書)</li><li>SPC (ソフトウェア発行元証明書)。</li></ul> |
| hexadecimal_cert_id | 証明書のハッシュを表す16進数。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの HTTPS (SSL) 要求でクライアント認証に使用するクライアント証明書の識別子を指定するには、次のようにします。

```
bitsadmin /setclientcertificatebyid myDownloadJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
