---
description: '詳細情報: シナリオ: Office ドキュメントの Classification-Based 暗号化'
ms.assetid: 73542e1c-53ef-4ddb-89b1-bc563b2bfb49
title: Office ドキュメントに対する分類ベースの暗号化をシナリオ
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 9f8588b5ff2ef9e895e05c45ba0a5d8607add281
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97044750"
---
# <a name="scenario-classification-based-encryption-for-office-documents"></a>シナリオ:Office ドキュメントに対する分類ベースの暗号化

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

機密情報を保護する主な目的は組織のリスクを低減することです。 医療保険の携行性と責任に関する法律 (HIPAA) や Payment Card Industry Data Security Standard (PCI-DSS) などのさまざまなコンプライアンス規定が情報の暗号化を義務付けており、その他にも数多くのビジネス上の理由で機密情報が暗号化されています。 一方、情報の暗号化は高コストであるだけでなく、ビジネスの生産性を低下させる原因にもなります。 このためさまざまな組織がさまざまなアプローチを採用して、暗号化する情報に優先順位を設定しています。

## <a name="scenario-description"></a><a name="BKMK_OVER"></a>シナリオの説明
 Windows Server 2012 では、機密性の高い Microsoft Office ファイル、分類に基づいて自動で暗号化する機能を提供します。 これはファイル管理タスクを通じて実行されます。ファイル管理タスクは、ファイル サーバー上のファイルを機密性が高いと認識した数秒後に Active Directory Rights Management サーバー (AD RMS) 保護を起動します。 これは、ファイル サーバー上の連続ファイル管理タスクによって容易になります。

AD RMS 暗号化により、ファイル保護のための新しい層が追加されます。 機密性の高いファイルへのアクセス権を持つユーザーがファイルを誤って電子メールで送信した場合も、AD RMS 暗号化によりファイルは保護されます。 ファイルへのアクセスを必要とするユーザーは、最初に AD RMS サーバーでユーザー自身を認証し、暗号化キーを受け取る必要があります。 このプロセスを次の図に示します。

![ソリューション ガイド](media/Scenario--Classification-Based-Encryption-for-Office-Documents/DynamicAccessControl_RevGuide_6.JPG)

**図 6** 分類ベースの RMS 保護

マイクロソフト以外のファイル形式については、マイクロソフト以外のベンダーがサポートしています。 AD RMS 暗号化による保護が適用されたファイルには、検索ベースやコンテンツベースの分類などのデータ管理機能は使用できません。

## <a name="in-this-scenario"></a>このシナリオの内容
次に、このシナリオで使用可能なガイダンスを示します。

-   [Office 文書の暗号化に関する考慮事項の計画](assetId:///14714ba6-d6a2-45e4-aae5-d3318817e52a)

-   [デモンストレーション手順 &#40;の Office ファイルの暗号化を展開する&#41;](Deploy-Encryption-of-Office-Files--Demonstration-Steps-.md)

-   [ダイナミック アクセス制御: シナリオの概要](Dynamic-Access-Control--Scenario-Overview.md)

## <a name="roles-and-features-included-in-this-scenario"></a><a name="BKMK_NEW"></a>このシナリオに含まれている役割と機能
次の表で、このシナリオに含まれている役割と機能を紹介すると共に、それをシナリオに活かす方法について説明します。

|役割/機能|このシナリオのサポート方法|
|-----------------|---------------------------------|
|Active Directory ドメイン サービスの役割 (AD DS)|AD DS では、分散データベースにより、ネットワーク リソース、およびディレクトリ対応アプリケーションに固有のデータが保存、管理されます。 このシナリオでは、Windows Server 2012 で AD DS には、クレーム ベースの承認プラットフォームをユーザーの信頼性情報とデバイスの信頼性情報、複合 id (ユーザーおよびデバイスの信頼性情報)、新しい集約型アクセス ポリシー モデル、および承認の判断でのファイル分類情報の用途の作成が導入されています。|
|ファイル サービスおよび記憶域サービスの役割<p>File Server Resource Manager|ファイル サービスおよび記憶域サービスには、1 台以上のファイル サーバーの設定および管理を支援するテクノロジが備わっています。ファイル サーバーは、ファイルを保存したり、ユーザーと共有したりできる、ネットワーク上の中心的な場所です。 ネットワーク ユーザーが同じファイルおよびアプリケーションにアクセスする必要がある場合、または一元化されたバックアップとファイル管理が組織にとって重要である場合、ファイル サービスおよび記憶域サービスの役割と適切な役割サービスをコンピューターに追加して、1 台以上のコンピューターをファイル サーバーとして設定する必要があります。 このシナリオでは、ファイル サーバー管理者はファイル管理タスクを構成できます。ファイル管理タスク (ファイル サーバー上で継続的に実行) は、ファイル サーバー上のファイルを機密性が高いと認識した数秒後に AD RMS 保護を起動します。|
|Active Directory Rights Management サービス (AD RMS) の役割|AD RMS により、個人ユーザーおよび管理者は、Information Rights Management (IRM) ポリシーを介して、ドキュメント、ブック、およびプレゼンテーションに対するアクセス許可を指定できます。 これにより、不正ユーザーによる機密情報の印刷、転送、コピーを防止できます。 IRM を使用してファイルに対するアクセス許可を制限すると、情報がどこにあるかを問わず、アクセスと使用に関する制限が適用されます。これは、ファイルに対するアクセス許可がドキュメント ファイルそのものに格納されるためです。 このシナリオでは、AD RMS 暗号化により、ファイル保護のための新しい層が追加されます。 機密性の高いファイルへのアクセス権を持つユーザーがファイルを誤って電子メールで送信した場合も、AD RMS 暗号化によりファイルは保護されます。 ファイルへのアクセスを必要とするユーザーは、最初に AD RMS サーバーでユーザー自身を認証し、暗号化キーを受け取る必要があります。|



