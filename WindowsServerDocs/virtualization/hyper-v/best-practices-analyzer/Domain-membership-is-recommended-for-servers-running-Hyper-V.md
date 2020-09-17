---
title: ドメインメンバーシップは、Hyper-v を実行するサーバーに推奨されます。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 2f4578e5-0848-46b4-a50b-7dbd480b80bf
ms.date: 8/16/2016
ms.openlocfilehash: 6a813af7d5064f91870652e6b0073c5c73c62604
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745667"
---
# <a name="domain-membership-is-recommended-for-servers-running-hyper-v"></a>ドメインメンバーシップは、Hyper-v を実行するサーバーに推奨されます。

>適用先:Windows Server 2016



*ベストプラクティスとスキャンの詳細については、「ベストプラクティスアナライザー」を参照してください* [Best Practices Analyzer](https://go.microsoft.com/fwlink/?LinkId=122786)。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*このサーバーは、ワークグループのメンバーです。*

## <a name="impact"></a>影響

*このサーバーの一元管理はありません。*

このコンピューターをドメインに参加させることで、id、セキュリティ、および監査に関するポリシーを使用して一元管理を行うことができます。

## <a name="resolution"></a>解決策

*使用可能なドメイン環境がある場合は、このサーバーをそのドメインに参加させます。*

> [!IMPORTANT]
> このコンピューターの仮想マシンで実行されているワークロードを確認し、このコンピューターをドメインに参加させることによるセキュリティへの影響があるかどうかを判断することをお勧めします。 仮想マシンのいずれかが仮想化ドメインコントローラーである場合は、「 [仮想化ドメインコントローラーの計画に関する考慮事項](https://go.microsoft.com/fwlink/?LinkId=190192) 」 (を参照してください https://go.microsoft.com/fwlink/?LinkId=190192) 。

コンピューターをドメインに参加させるには、コンピューターとドメインに対するアクセス許可が必要です。
- コンピューターには、Administrators グループのメンバーであるユーザーアカウントが必要です。 この種類のアカウントでログオンするか、メッセージが表示されたらアカウントのユーザー名とパスワードを入力します。
- ドメインでは、ドメインにコンピューターを参加させる権限を持つユーザーアカウントが必要になります。 ユーザー名とパスワードの入力を求められます。

手順については、「 [コンピューターをドメインに参加](https://go.microsoft.com/fwlink/?LinkId=190193) させる」 (「」を参照してください https://go.microsoft.com/fwlink/?LinkId=190193) 。



