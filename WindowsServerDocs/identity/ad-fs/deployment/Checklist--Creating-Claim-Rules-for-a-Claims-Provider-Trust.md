---
description: '詳細については、「チェックリスト: 要求プロバイダー信頼の要求規則を作成する」を参照してください。'
ms.assetid: 503733f8-be0c-429c-81f0-cd4205e8b118
title: チェックリスト-要求プロバイダー信頼の要求規則を作成する
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 40e79c394ad413b60dadb0ba19385ceabd881b3f
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97050370"
---
# <a name="checklist-creating-claim-rules-for-a-claims-provider-trust"></a>チェックリスト: 要求プロバイダー信頼の要求規則の作成


このチェックリストには、Active Directory フェデレーションサービス (AD FS) AD FS の要求プロバイダー信頼に関連付けられている要求規則を計画、設計、および展開するためのタスクが含まれてい \( \) ます。

> [!NOTE]
> このチェックリストのタスクは順番に実行してください。 参照リンクによって手順に移動した場合は、このチェックリストの残りのタスクを進めることができるように、その手順の作業が完了したらこのトピックに戻ります。

![要求規則の作成](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**チェックリスト: 要求プロバイダー信頼の要求規則セットの作成**

|タスク|リファレンス|
|--------|-------------|
|要求、要求規則、要求規則セット、要求規則テンプレート、およびそれらがフェデレーション信頼にどのように関連付けられているかに関する概念を確認します。|![要求規則の作成要求](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[の役割](../../ad-fs/technical-reference/The-Role-of-Claims.md)<p>![要求規則](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[の作成要求規則の役割](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md)|
|要求発行パイプラインのすべてのステージを通じて要求がどのように流れ、要求発行エンジンによってルールがどのように処理されるかについての概念を確認します。|![要求規則の作成要求](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[パイプラインの役割](../../ad-fs/technical-reference/The-Role-of-the-Claims-Pipeline.md)<p>![要求規則の作成要求](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[エンジンの役割](../../ad-fs/technical-reference/The-Role-of-the-Claims-Engine.md)|
|この要求プロバイダー信頼に対して発行される出力要求を効果的に計画および実装するには、1つまたは複数の要求規則が必要かどうか、およびこの要求プロバイダー信頼で使用する必要がある要求規則を確認します。|![要求規則を作成する](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[と、使用する要求規則テンプレートの種類が決まります](../../ad-fs/technical-reference/Determine-the-Type-of-Claim-Rule-Template-to-Use.md)。|
|別の要求規則を作成するタイミングと、要求規則言語を使用して標準規則より複雑なロジックを提供する方法についての概念を確認して、理想的な出力要求セットに必要な結果を提供します。|![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[パススルーまたはフィルター要求規則を使用する場合の](../../ad-fs/technical-reference/When-to-Use-a-Pass-Through-or-Filter-Claim-Rule.md)要求規則の作成<p>![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[変換要求規則を使用する場合の](../../ad-fs/technical-reference/When-to-Use-a-Transform-Claim-Rule.md)要求規則の作成<p>!["](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[LDAP 属性を要求として送信" 規則を使用する場合の](../../ad-fs/technical-reference/When-to-Use-a-Send-LDAP-Attributes-as-Claims-Rule.md)要求規則の作成<p>![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[グループメンバーシップを要求として送信するルールを使用する場合の](../../ad-fs/technical-reference/When-to-Use-a-Send-Group-Membership-as-a-Claim-Rule.md)要求規則の作成<p>![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[カスタム要求規則を使用する場合の](../../ad-fs/technical-reference/When-to-Use-a-Custom-Claim-Rule.md)要求規則の作成<p>![要求規則を作成する](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[要求規則言語の役割](../../ad-fs/technical-reference/The-Role-of-the-Claim-Rule-Language.md)|
|要求の説明は、組織のニーズを満たすものが存在しない場合に作成する必要があります。 AD FS には、AD FS 管理スナップインで公開される要求説明の既定のセットが付属してい \- ます。|![要求規則](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[の作成要求の説明を追加](../../ad-fs/operations/Add-a-Claim-Description.md)する|
|組織のニーズに応じて、要求が適切に発行されるように、この要求プロバイダー信頼に関連付けられている受け入れ変換規則セットに対して1つまたは複数の要求規則を作成します。|![要求規則を作成すると、](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[入力方向の要求をパススルーまたはフィルター処理するルールが作成](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)されます。<p>![要求規則](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[を作成する規則を作成して、LDAP 属性を要求として送信する](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)<p>![要求規則を作成](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[する規則を作成して、グループメンバーシップを要求として送信する](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)<p>![要求規則](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[を作成する規則を作成して、入力方向の要求を変換し](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)ます。<p>![要求規則](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[を作成する認証方法の要求を送信する規則を作成する](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)<p>![要求規則](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[を作成すると、AD FS 1.x と互換性のある要求を送信する規則が作成されます。](../../ad-fs/operations/Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)<p>![要求規則を作成する](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[カスタム規則を使用して要求を送信する規則を作成する](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)|


