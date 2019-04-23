---
title: 手順 3 OTP 証明書の展開の計画
description: このトピックでは、ガイド Windows Server 2016 での OTP 認証を使用したリモート アクセスの展開の一部です。
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eca02eeb-d92d-463e-aae0-1f7038ba26fe
ms.author: pashort
author: shortpatti
ms.openlocfilehash: bb6be03ed5319a56f9507859e753c88e020ceea9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813873"
---
# <a name="step-3-plan-otp-certificate-deployment"></a>手順 3 OTP 証明書の展開の計画

>適用先:Windows Server 2016 の Windows Server (半期チャネル)

RADIUS サーバーを計画するには後、は、ワンタイム パスワード (OTP) 証明書、OTP 証明書テンプレート、およびリモートで使用される登録機関の証明書を発行する CA をなど、証明機関 (CA) の要件を計画する必要があります。すべての DirectAccess クライアント OTP 証明書要求の署名にアクセス サーバー。 これらの証明書は、次のように使用されます。  
  
1.  DirectAccess クライアントは、OTP 証明書を要求し、リモート アクセス サーバーが要求を受信します。  
  
2.  リモート アクセス サーバーは、OTP 資格情報を確認し、有効な場合は、サーバーは登録機関として機能し、署名の有効期間が短い証明書を使用して、OTP 証明書の登録要求に署名します。  
  
3.  リモート アクセス サーバーが DirectAccess クライアントに署名証明書の登録要求を送信します  
  
4.  クライアントは、サーバーによって署名された証明書の登録要求を使用して、CA からの OTP 証明書を登録します。  
  
5.  CA は、資格情報と、要求を検証します。  
  
|タスク|説明|  
|----|--------|  
|[3.1 OTP CA を計画します。](#bkmk_3_1_CA)|使用して DirectAccess クライアント OTP 認証用に証明書を発行する証明機関 (CA) を計画します。|  
|[3.2 OTP 証明書テンプレートを計画します。](#bkmk_3_2_OTP_Cert)|OTP 証明書テンプレートを計画します。|
|[3.3 登録機関の証明書を計画します。](#bkmk_33RACert)|OTP 認証証明書のすべての要求の署名に登録機関の証明書を計画します。|

## <a name="bkmk_3_1_CA"></a>3.1 OTP CA を計画します。  
ワンタイム パスワード認証 (OTP) を使用して DirectAccess を展開するには、DirectAccess クライアント コンピューターに、OTP 認証の証明書を発行する、内部 CA が必要です。 このため、標準の IPsec コンピューター認証に使用される証明書の発行に使用する同じ内部 CA を使用できます。  
  
## <a name="bkmk_3_2_OTP_Cert"></a>3.2 OTP 証明書テンプレートを計画します。  
各 DirectAccess クライアントには、内部ネットワークにアクセスするには、OTP 認証の証明書が必要です。 OTP 証明書の内部 CA でテンプレートを構成する必要があります。 OTP 証明書テンプレートを構成するときに、次に注意してください。  
  
-   OTP 認証を実行する必要があるすべてのユーザーがいる必要があります読み取りし、このテンプレートに対するアクセス許可を登録します。  
  
-   サブジェクト名は、OTP ユーザー名、および証明書の要求を実行するリモート アクセス サーバーの名前ではなく、サブジェクト名が一致することを確認して、Active Directory の情報から構築する必要があります。 サブジェクト名は、完全な識別名の形式である必要があり、サブジェクトの別名を UPN 形式である必要があります。 これにより、登録済みの OTP 証明書がスマート カード Kerberos 認証で有効にします。  
  
-   証明書の目的は、スマート カード ログオンをする必要があります。  
  
-   発行には、1 つの承認済み署名が必要とする必要があります。 署名は、登録機関の署名証明書テンプレートで設定定義済みの DirectAccess OTP アプリケーション ポリシーで構成する必要があります。  
  
-   有効期間は、1 時間に設定する必要があります。  
  
    > [!NOTE]  
    > 場合、CA サーバーが Windows Server 2003 コンピューターを別のコンピューターで、テンプレートを構成する必要があります。 これは、設定にするため、**有効期間**時間ことができない 2008/Vista より前の Windows バージョンを実行している場合。 テンプレートを構成するために使用するコンピューターには、証明サービス役割をインストールするはありません。 または、クライアント コンピューターは、証明書テンプレート スナップインをインストールする必要があります。 このトピックの詳細については次のようにクリックします。[ここ](https://technet.microsoft.com/library/cc732445.aspx)します。  
  
-   更新期間は 0 に設定する必要があります。  
  
-   (省略可能)証明書と要求を CA データベースに保存しない必要があります。  
  
-   正しく、次のように、証明書の拡張キー使用法のパラメーターを設定する必要があります。  
  
    -   DirectAccess は、署名証明書テンプレートの登録は、1.3.6.1.4.1.311.81.1.1 キーを使用します。  
  
    -   OTP 認証の証明書テンプレートには、キー 1.3.6.1.4.1.311.20.2.2 キーを使用します。  
  
## <a name="bkmk_33RACert"></a>3.3 登録機関の証明書を計画します。  
OTP 証明書を要求すると、DirectAccess クライアント、リモート アクセス サーバーがクライアントから要求を受信します。 リモート アクセス サーバーは、すべての登録機関の証明書を使用するクライアントからの OTP 証明書の要求に署名します。 リモート アクセス サーバーの登録機関の証明書を要求に署名する場合にのみ、CA は証明書を発行します。 内部 CA によって証明書を発行する必要があります、証明書が自己署名することはできません。 OTP 証明書を発行した CA によって発行されることはありませんが、OTP 証明書を発行した CA は、登録機関の署名証明書を発行する CA を信頼する必要があります。  
  
## <a name="BKMK_Links"></a>参照してください。  
  
-   [手順 4:OTP をリモート アクセス サーバーを計画します。](Step-4-Plan-for-OTP-on-the-Remote-Access-Server.md)  
  

