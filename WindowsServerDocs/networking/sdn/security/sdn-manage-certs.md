---
title: ソフトウェア定義ネットワークの証明書の管理
description: このトピックでは、Windows Server 2016 Datacenter でソフトウェアによるネットワーク制御 (SDN) を展開するときに、Network Controller Northbound と Southbound 通信の証明書を管理する方法について説明します。
manager: grcusanz
ms.topic: article
ms.assetid: c4e2f6c7-0364-4bf8-bb66-9af59c0bbd74
ms.author: anpaul
author: AnirbanPaul
ms.date: 08/22/2018
ms.openlocfilehash: 2bd72ec096d7c1301601848602a1d55e44ca5086
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96866511"
---
# <a name="manage-certificates-for-software-defined-networking"></a>ソフトウェア定義ネットワークの証明書の管理

>適用先:Windows Server (半期チャネル)、Windows Server 2016

このトピックでは、Windows Server 2016 Datacenter でソフトウェア定義のネットワーク SDN を展開するときに \( \) 、System Center Virtual Machine Manager \( SCVMM を SDN 管理クライアントとして使用している場合に、Network Controller Northbound と Southbound 通信の証明書を管理する方法について説明し \) ます。

>[!NOTE]
>ネットワークコントローラーの概要については、「 [ネットワークコントローラー](../technologies/network-controller/Network-Controller.md)」を参照してください。

ネットワークコントローラーの通信をセキュリティで保護するために Kerberos を使用していない場合は、x.509 証明書を使用して認証、承認、および暗号化を行うことができます。

Windows Server 2016 Datacenter の SDN では \- 、自己署名証明書と証明機関 \( CA で署名された x.509 証明書の両方がサポートされてい \) ます。 このトピックでは、これらの証明書を作成し、それらをセキュリティで保護されたネットワークコントローラーの Northbound 通信チャネルに適用して、管理クライアントと、ソフトウェア Load Balancer SLB などのネットワークデバイスとの通信を Southbound する手順について説明し \( \) ます。
.
証明書ベースの認証を使用する場合は、 \- 次の方法で使用されるネットワークコントローラーノードに証明書を1つ登録する必要があります。

1. \( \) ネットワークコントローラーノードと管理クライアント (System Center Virtual Machine Manager など) との間で Secure Sockets Layer SSL を使用して Northbound 通信を暗号化します。
2. ネットワークコントローラーノードと Southbound デバイスとサービス (Hyper-v ホストやソフトウェアロードバランサー slbs など) 間の認証 \( \) 。

## <a name="creating-and-enrolling-an-x509-certificate"></a>X.509 証明書の作成と登録

自己 \- 署名証明書または CA によって発行された証明書を作成して登録することができます。

>[!NOTE]
>SCVMM を使用してネットワークコントローラーを展開する場合は、ネットワークコントローラーのサービステンプレートを構成するときに、Northbound 通信の暗号化に使用される x.509 証明書を指定する必要があります。

証明書の構成には、次の値を含める必要があります。

- **RestEndPoint** テキストボックスの値は、ネットワークコントローラーの完全修飾ドメイン名の \( FQDN または IP アドレスである必要があり \) ます。
- **RestEndPoint** 値は、 \( \) x.509 証明書のサブジェクト名の共通名 (CN) と一致している必要があります。

### <a name="creating-a-self-signed-x509-certificate"></a>自己 \- 署名 X.509 証明書の作成

自己署名された x.509 証明書を作成し、パスワードで保護された秘密キーでエクスポートするには、次 \( \) の手順に従って、 \- ネットワークコントローラーの単一ノードおよび複数ノードの展開を行い \- ます。

自己 \- 署名証明書を作成する場合は、次のガイドラインを参考にしてください。

- DnsName パラメーターにはネットワークコントローラー REST エンドポイントの IP アドレスを使用できますが、これは推奨されません。これは、1つのラックにある1つの管理サブネット内にネットワークコントローラーノードがすべて存在する必要があるためです \( 。\)
- 複数のノード NC 展開では、指定した DNS 名がネットワークコントローラークラスター DNS ホストの FQDN になり \( ます。 A レコードは自動的に作成されます。\)
- 単一ノードのネットワークコントローラーの展開では、DNS 名は、ネットワークコントローラーのホスト名の後に完全なドメイン名を付けたものにすることができます。

#### <a name="multiple-node"></a>複数ノード

[新しい-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) Windows PowerShell コマンドを使用して、自己 \- 署名証明書を作成できます。

**構文**

```powershell
New-SelfSignedCertificate -KeyUsageProperty All -Provider "Microsoft Strong Cryptographic Provider" -FriendlyName "<YourNCComputerName>" -DnsName @("<NCRESTName>")
```

**使用例**

```powershell
New-SelfSignedCertificate -KeyUsageProperty All -Provider "Microsoft Strong Cryptographic Provider" -FriendlyName "MultiNodeNC" -DnsName @("NCCluster.Contoso.com")
```

#### <a name="single-node"></a>単一ノード

[新しい-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) Windows PowerShell コマンドを使用して、自己 \- 署名証明書を作成できます。

**構文**

```powershell
New-SelfSignedCertificate -KeyUsageProperty All -Provider "Microsoft Strong Cryptographic Provider" -FriendlyName "<YourNCComputerName>" -DnsName @("<NCFQDN>")
```

**使用例**

```powershell
New-SelfSignedCertificate -KeyUsageProperty All -Provider "Microsoft Strong Cryptographic Provider" -FriendlyName "SingleNodeNC" -DnsName @("SingleNodeNC.Contoso.com")
```

### <a name="creating-a-ca-signed-x509-certificate"></a>CA に \- 署名された X.509 証明書の作成

CA を使用して証明書を作成するには、 \( \) Active Directory 証明書サービス AD CS を持つ公開キー基盤 PKI を既に展開している必要があり \( \) ます。

>[!NOTE]
>サードパーティの Ca または openssl などのツールを使用して、ネットワークコントローラーで使用する証明書を作成できます。ただし、このトピックの手順は AD CS に固有のものです。 サードパーティの CA またはツールを使用する方法については、使用しているソフトウェアのドキュメントを参照してください。

CA を使用して証明書を作成するには、次の手順を実行します。

1. ユーザーまたは組織のドメインまたはセキュリティ管理者が証明書テンプレートを構成する
2. ユーザーまたは組織のネットワークコントローラーの管理者または SCVMM 管理者が、CA に新しい証明書を要求します。

#### <a name="certificate-configuration-requirements"></a>証明書の構成要件

次の手順で証明書テンプレートを構成するときに、構成するテンプレートに次の必須要素が含まれていることを確認します。

1. 証明書のサブジェクト名は、Hyper-v ホストの FQDN である必要があります。
2. 証明書はローカルコンピューターの個人用ストアに配置する必要があります (My – cert:\ localmachine\my)
3. 証明書には、サーバー認証 (EKU: 1.3.6.1.5.5.7.3.1) とクライアント認証 (EKU: 1.3.6.1.5.5.7.3.2) の両方のアプリケーションポリシーが必要です。

>[!NOTE]
>\(Hyper-v ホストの Personal My – cert:\ localmachine\my \) 証明書ストアに、 \- ホストの完全修飾ドメイン名 FQDN としてサブジェクト名 (CN) を持つ x.509 証明書が複数ある場合は \( \) 、SDN によって使用される証明書に、OID 1.3.6.1.4.1.311.95.1.1.1 を持つカスタム拡張キー使用法プロパティが追加されていることを確認してください。 そうでない場合、ネットワーク コントローラーとホスト間の通信が機能しない可能性があります。

#### <a name="to-configure-the-certificate-template"></a>証明書テンプレートを構成するには

>[!NOTE]
>この手順を実行する前に、証明書テンプレートコンソールで証明書の要件と利用可能な証明書テンプレートを確認する必要があります。 既存のテンプレートを変更するか、既存のテンプレートの複製を作成してから、テンプレートのコピーを変更することができます。 既存のテンプレートのコピーを作成することをお勧めします。

1. AD CS がインストールされているサーバーのサーバーマネージャーで、[ **ツール**] をクリックし、[ **証明機関**] をクリックします。 証明機関 Microsoft 管理コンソール \( MMC \) が開きます。
2. MMC で、CA 名をダブルクリックし、[ **証明書テンプレート**] を右クリックして、[ **管理**] をクリックします。
3. [証明書テンプレートコンソールが開きます。 すべての証明書テンプレートが詳細ウィンドウに表示されます。
4. 詳細ウィンドウで、複製するテンプレートをクリックします。
5.  [ **操作** ] メニューをクリックし、[ **テンプレートの複製**] をクリックします。 [テンプレートの **プロパティ** ] ダイアログボックスが表示されます。
6.  [テンプレートの **プロパティ** ] ダイアログボックスの [ **サブジェクト名** ] タブで、[ **要求に含ま** れる] をクリックします。 \(この設定は、ネットワークコントローラーの SSL 証明書に必要です。\)
7.  [テンプレートの **プロパティ** ] ダイアログボックスの [ **要求処理** ] タブで、[ **秘密キーのエクスポートを許可** する] が選択されていることを確認します。 また、 **署名と暗号化** の目的が選択されていることを確認します。
8.  [テンプレートの **プロパティ** ] ダイアログボックスの [ **拡張機能** ] タブで、[ **キー使用法**] を選択し、[ **編集**] をクリックします。
9.  [ **署名**] で、[ **デジタル署名** ] が選択されていることを確認します。
10.  [テンプレートの **プロパティ** ] ダイアログボックスの [ **拡張機能** ] タブで、[ **アプリケーションポリシー**] を選択し、[ **編集**] をクリックします。
11.  [ **アプリケーションポリシー**] で、[ **クライアント認証** ] と [ **サーバー認証** ] が表示されていることを確認します。
12.  **ネットワークコントローラーテンプレート** などの一意の名前を使用して、証明書テンプレートのコピーを保存します。

#### <a name="to-request-a-certificate-from-the-ca"></a>CA に証明書を要求するには

証明書スナップインを使用して、証明書を要求することができます。 証明書の要求を処理する CA の管理者によって事前に構成され、使用可能になっている任意の種類の証明書を要求できます。

この手順を完了するには、**ユーザー** またはローカルの **管理者** が最低限必要なグループメンバーシップです。

1. コンピューターの証明書スナップインを開きます。
2. コンソールツリーで、[**証明書] [ \( ローカルコンピューター \)**] をクリックします。 **個人** 証明書ストアを選択します。
3. [ **操作** ] メニューの [すべてのタスク] をポイントし、<strong>[新しい証明書の要求</strong> ] をクリックして証明書の登録ウィザードを起動します。 **[次へ]** をクリックします。
4. 管理者証明書の登録ポリシー **によって構成され** たを選択し、[ **次へ**] をクリックします。
5. 前の **Active Directory Enrollment Policy** \( セクションで構成した CA テンプレートに基づいて、Active Directory の登録ポリシーを選択し \) ます。
6. [ **詳細** ] セクションを展開し、次の項目を構成します。
   1. **キー使用法** に <strong>デジタル署名 * * と * * キーの暗号化</strong>の両方が含まれていることを確認します。
   2. **アプリケーションポリシー** に **サーバー認証** \( 1.3.6.1.5.5.7.3.1 \) と **クライアント認証** 1.3.6.1.5.5.7.3.2 の両方が含まれていることを確認し \( \) ます。
7. **[プロパティ]** をクリックします。
8. [ **サブジェクト** ] タブの [ **サブジェクト名**] の [ **種類**] で、[ **共通名**] を選択します。 [値] で、 **ネットワークコントローラー REST エンドポイント** を指定します。
9. [**適用**] をクリックし、[**OK**] をクリックします。
10. **[登録]** をクリックします。

[証明書] MMC で、[個人] ストアをクリックして、CA から登録した証明書を表示します。

## <a name="exporting-and-copying-the-certificate-to-the-scvmm-library"></a>証明書をエクスポートし、SCVMM ライブラリにコピーする

自己 \- 署名証明書または CA 署名証明書を作成した後は、証明書 \- スナップイン \( \) \( から Base-64 形式の \) 秘密キーを使用して、証明書を .pfx 形式でエクスポートする必要があります。

次に、2つのエクスポートされたファイルを、NC サービステンプレートのインポート時に指定した **ServerCertificate.cr** および **NCCertificate.cr** フォルダーにコピーする必要があります。

1. 証明書スナップイン (certlm .msc) を開き、ローカルコンピューターの [個人] 証明書ストアで証明書を探します。
2. \-証明書を右クリックし、[**すべてのタスク**] をクリックして、[**エクスポート**] をクリックします。 証明書のエクスポート ウィザードが開きます。 **[次へ]** をクリックします。
3. [ **はい**、秘密キーをエクスポートします] オプションを選択し、[ **次へ**] をクリックします。
4. [ **Personal Information Exchange-PKCS #12 () を選択します。[PFX])** を受け入れ、既定値をそのまま使用して、可能な場合は証明の **パスにすべての証明書を含め** ます。
5. ユーザー/グループと、エクスポートする証明書のパスワードを割り当てて、**[次へ]** をクリックします。
6. [エクスポートするファイル] ページで、エクスポートしたファイルを配置する場所を参照し、名前を付けます。
7. 同様に、で証明書をエクスポートします。CER 形式。 注: .CER 形式にエクスポートする場合は、[はい、秘密キーをエクスポートします] オプションをオフにします。
8. PFX を ServerCertificate.cr フォルダーにコピーします。
9. .CER ファイルを NCCertificate.cr フォルダーにコピーします。

完了したら、SCVMM ライブラリ内のこれらのフォルダーを更新し、これらの証明書がコピーされていることを確認します。 ネットワークコントローラーのサービステンプレートの構成と展開を続行します。

## <a name="authenticating-southbound-devices-and-services"></a>Southbound のデバイスとサービスの認証

ホストと SLB MUX デバイスとのネットワークコントローラーの通信では、認証に証明書を使用します。 SLB MUX デバイスとの通信は、WCF プロトコル経由でのホストとの通信が終了しています。

### <a name="hyper-v-host-communication-with-network-controller"></a>Hyper-v ホストとネットワークコントローラーとの通信

ホストコンピューターに対して Hyper-v ホストとの通信を行うには、ネットワークコントローラーがホストコンピューターに証明書を提示する必要があります。 既定では、SCVMM はネットワークコントローラーで構成されている SSL 証明書を取得し、ホストとの southbound 通信に使用します。

その理由は、SSL 証明書にクライアント認証 EKU が構成されている必要があるためです。 この証明書は、"サーバー" REST リソースで構成されます (Hyper-v ホストは、サーバーリソースとしてネットワークコントローラーで表されます)。また、Windows PowerShell コマンド **NetworkControllerServer** を実行して表示できます。

サーバー REST リソースの例を次に示します。

```
   "resourceId": "host31.fabrikam.com",
      "properties": {
        "connections": [
          {
            "managementAddresses": [
               "host31.fabrikam.com"
            ],
            "credential": {
              "resourceRef": "/credentials/a738762f-f727-43b5-9c50-cf82a70221fa"
            },
            "credentialType": "X509Certificate"
          }
        ],
```

相互認証の場合、Hyper-v ホストにはネットワークコントローラーと通信するための証明書も必要です。

証明機関の CA から証明書を登録 \( でき \) ます。 CA ベースの証明書がホストコンピューターで見つからない場合、SCVMM は自己署名証明書を作成し、ホストコンピューター上にプロビジョニングします。

ネットワークコントローラーと Hyper-v ホストの証明書は、互いに信頼されている必要があります。 Hyper-v ホスト証明書のルート証明書は、ローカルコンピューターのネットワークコントローラーの信頼されたルート証明機関ストアに存在している必要があります。また、その逆も同様です。

自己署名証明書を使用している場合、SCVMM は、 \- 必要な証明書がローカルコンピューターの信頼されたルート証明機関ストアに存在することを確認します。

Hyper-v ホストに CA ベースの証明書を使用している場合は、ローカルコンピューターのネットワークコントローラーの信頼されたルート証明機関ストアに CA のルート証明書が存在することを確認する必要があります。

### <a name="software-load-balancer-mux-communication-with-network-controller"></a>ネットワークコントローラーとのソフトウェア Load Balancer MUX の通信

マルチプレクサーです MUX とネットワークコントローラーのソフトウェア Load Balancer は、 \( \) 認証に証明書を使用して、WCF プロトコルを介して通信します。

既定では、SCVMM はネットワークコントローラーで構成されている SSL 証明書を取得し、それを使用して Mux デバイスとの southbound 通信に使用します。 この証明書は "NetworkControllerLoadBalancerMux" REST リソースで構成され、Powershell コマンドレット **NetworkControllerLoadBalancerMux** を実行することで表示できます。

MUX REST リソースの一部の例 \( \) :

```
      "resourceId": "slbmux1.fabrikam.com",
      "properties": {
        "connections": [
          {
            "managementAddresses": [
               "slbmux1.fabrikam.com"
            ],
            "credential": {
              "resourceRef": "/credentials/a738762f-f727-43b5-9c50-cf82a70221fa"
            },
            "credentialType": "X509Certificate"
          }
        ],
```

相互認証の場合、SLB MUX デバイスにも証明書が必要です。 この証明書は、scvmm を使用してソフトウェアロードバランサーを展開するときに、SCVMM によって自動的に構成されます。

>[!IMPORTANT]
>ホストと SLB ノードでは、信頼されたルート証明機関の証明書ストアに、"発行先" とは異なる証明書が含まれていないことが重要です。 この問題が発生すると、ネットワークコントローラーと southbound デバイス間の通信が失敗します。

ネットワークコントローラーと SLB MUX 証明書は互いに信頼されている必要があり \( ます。また、SLB mux 証明書のルート証明書は、ネットワークコントローラーコンピューターの信頼されたルート証明機関ストアに存在する必要があり、その逆も同様 \) です。 自己署名証明書を使用している場合、 \- SCVMM は、ローカルコンピューターの信頼されたルート証明機関ストアのに必要な証明書が存在することを確認します。
