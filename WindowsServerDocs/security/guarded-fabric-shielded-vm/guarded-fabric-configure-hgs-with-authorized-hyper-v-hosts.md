---
description: '詳細情報: 保護されたホストの展開'
title: 保護されたホストの展開
ms.topic: article
ms.assetid: 2379ca26-b32d-4055-8b4b-99d1f2df37e1
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: fb3d189ce0817d52a536af8f25fd9b78fda719e5
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049880"
---
# <a name="deploy-guarded-hosts"></a>保護されたホストの展開

>適用対象: windows server 2019、Windows Server (半期チャネル)、Windows Server 2016

このセクションのトピックでは、ファブリック管理者がホストガーディアンサービス (HGS) を使用するように Hyper-v ホストを構成するために実行する手順について説明します。 これらの手順を開始する前に、HGS クラスター内の少なくとも1つのノードがセットアップされて [いる必要があり](guarded-fabric-setting-up-the-host-guardian-service-hgs.md)ます。

**TPM で信頼された構成証明の場合**:
1. [ファブリック dns を構成](guarded-fabric-configuring-fabric-dns.md)する: ファブリックドメインから HGS ドメインに DNS フォワーダーを設定する方法について説明します。
2. [HGS に必要なキャプチャ情報](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md): tpm 識別子 (プラットフォーム id とも呼ばれます) をキャプチャする方法、コード整合性ポリシーを作成する方法、tpm ベースラインを作成する方法について説明します。 次に、この情報を HGS 管理者に提供して、構成証明を構成します。
3. [保護されたホストが証明できることを確認する](guarded-fabric-confirm-hosts-can-attest-successfully.md)

**ホストキーの構成証明の場合**:
1. [ホストキーを作成](guarded-fabric-create-host-key.md#create-a-host-key)する: ファブリックドメインから HGS ドメインに DNS フォワーダーを設定する方法について説明します。
2. [構成証明サービスにホストキーを追加](guarded-fabric-create-host-key.md#add-the-host-key-to-the-attestation-service)する: ファブリックドメインで Active Directory セキュリティグループを設定し、保護されたホストをそのグループのメンバーとして追加し、そのグループ識別子を HGS 管理者に提供する方法を指示します。
3. [保護されたホストが証明できることを確認する](guarded-fabric-confirm-hosts-can-attest-successfully.md)


**管理者によって信頼された構成証明の場合**:
1. [ファブリック dns を構成](guarded-fabric-configuring-fabric-dns.md)する: ファブリックドメインから HGS ドメインに DNS フォワーダーを設定する方法について説明します。
2. [セキュリティグループの作成](guarded-fabric-admin-trusted-attestation-creating-a-security-group.md): ファブリックドメインで Active Directory セキュリティグループを設定し、保護されたホストをそのグループのメンバーとして追加し、そのグループ ID を HGS 管理者に提供する方法を示します。
3. [保護されたホストが証明できることを確認する](guarded-fabric-confirm-hosts-can-attest-successfully.md)


## <a name="additional-references"></a>その他の参照情報

- [保護されたファブリックとシールドされた Vm の展開タスク](guarded-fabric-deploying-hgs-overview.md#deployment-tasks-for-guarded-fabrics-and-shielded-vms)
