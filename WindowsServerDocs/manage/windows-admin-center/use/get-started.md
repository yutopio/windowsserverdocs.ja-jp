---
title: Windows 管理センターを使ってみる
description: Windows 管理センターを使ってみる
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.date: 02/15/2019
ms.openlocfilehash: 11cfe250bd08a04f1577a5537389885718a755a3
ms.sourcegitcommit: 2365a7b23e2eccd13be350306c622d2ad9d36bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2020
ms.locfileid: "96787901"
---
# <a name="get-started-with-windows-admin-center"></a>Windows 管理センターを使ってみる

>適用先:Windows Admin Center、Windows Admin Center Preview

> [!Tip]
> Windows Admin Center を初めて使用する場合
> [Windows Admin Center についての詳細を確認する](../overview.md)か、[今すぐダウンロード](../overview.md)してください。

## <a name="windows-admin-center-installed-on-windows-10"></a>Windows 10 にインストールされた windows 管理センター

> [!IMPORTANT]
> Windows 10 で Windows 管理センターを使用するには、ローカル管理者のグループのメンバーである必要があります。

### <a name="selecting-a-client-certificate"></a>クライアント証明書の選択

Windows 10 で windows 管理センターを初めて開くときは、必ず *Windows 管理センタークライアント* 証明書を選択してください (そうしないと、"このページにアクセスできません" という HTTP 403 エラーが表示されます)。

Microsoft Edge で、このダイアログボックスが表示されたら、次のように入力します。

1. **その他の選択肢** をクリック

    ![その他の選択肢が強調表示されている証明書ボックスを選択します](../media/launch-cert-1.png)

2. **Windows 管理センタークライアント** という名前の証明書を選択し、[ **OK]** をクリックします。

    ![使用可能な証明書が表示されている証明書ボックスを選択します](../media/launch-cert-2.png)

3. **常にアクセスを許可する** ことを確認し、[**許可**] をクリックします。

    ![[資格情報が必要です] ダイアログボックス](../media/launch-cert-3.png)

## <a name="connecting-to-managed-nodes-and-clusters"></a>管理対象ノードとクラスターへの接続

Windows 管理センターのインストールが完了したら、メインの [概要] ページから、管理するサーバーまたはクラスターを追加できます。

 **単一のサーバーまたはクラスターを管理ノードとして追加する**

1. **[すべての接続]** の下にある **[+ 追加]** をクリックします。

   ![Windows Admin Center - すべての接続のページ](../media/launch/addserver0.png)

2. サーバー、クラスター、Windows PC、または Azure VM を追加することを選択します。

   ![Windows 管理センター-[リソースの追加] ページ](../media/launch/ChooseConnectionType.png)

3. 管理するサーバーまたはクラスターの名前を入力し、[ **送信**] をクリックします。 サーバーまたはクラスターが [概要] ページの接続リストに追加されます。

   ![Windows 管理センター-[サーバー] ページ](../media/launch/addserver2.png)

   **--または--**

**複数のサーバーの一括インポート**

 1. [ **サーバー接続の追加** ] ページで、[ **サーバーのインポート** ] タブを選択します。

    ![Windows 管理センター-[サーバーのインポート] タブ](../media/launch/import-servers.png)

 2. [ **参照** ] をクリックし、追加するサーバーの fqdn のコンマまたは改行を含むテキストファイルを選択します。

> [!Note]
> [PowerShell を使用した接続のエクスポート](#use-powershell-to-import-or-export-your-connections-with-tags)によって作成される .csv ファイルには、サーバー名以外の追加情報が含まれており、このインポート方法との互換性がありません。

  **--または--**

**Active Directory を検索してサーバーを追加する**

 1. [ **サーバー接続の追加** ] ページで、[ **検索 Active Directory** ] タブを選択します。

    ![Windows 管理センター-検索 Active Directory タブ](../media/launch/search-ad.png)

 2. 検索条件を入力し、[ **検索**] をクリックします。 ワイルドカード (*) がサポートされています。

 3. 検索が完了したら、1つまたは複数の結果を選択し、必要に応じてタグを追加して、[ **追加**] をクリックします。

## <a name="authenticate-with-the-managed-node"></a>管理ノードで認証する ##

Windows 管理センターでは、管理対象ノードで認証を行うためのメカニズムがいくつかサポートされています。 シングルサインオンが既定値です。

**シングルサインオン**

現在の Windows 資格情報を使用して、管理対象ノードで認証を行うことができます。 これは既定の設定であり、Windows 管理センターはサーバーを追加するときにサインオンを試行します。

**Windows Server にサービスとしてデプロイされた場合のシングル サインオン**

Windows Server に Windows 管理センターがインストールされている場合は、シングルサインオンのために追加の構成が必要になります。  [委任のために環境を構成する](../configure/user-access-control.md)

**--または--**

**管理アカウントを使用し *て* 資格情報を指定する**

[ **すべての接続**] で、一覧からサーバーを選択し、[管理に使用する資格情報] を選択し **て** 、管理ノードへの認証に使用する資格情報を指定します。

![すべての接続、オプションとして管理](../media/launch-use-6.png)

Windows 管理センターが Windows Server でサービスモードで実行されているが、Kerberos 委任が構成されていない場合は、Windows 資格情報を再入力する必要があります。

![[資格情報の指定] ページ](../media/launch-use-7.png)

すべての接続に資格情報を適用することができます。これにより、その特定のブラウザーセッションに対して資格情報がキャッシュされます。 ブラウザーを再読み込みする場合は、 **管理** 者の資格情報を再入力する必要があります。

**ローカル管理者パスワードソリューション (LAPS)**

お使いの環境で [LAPS](/previous-versions/mt227395(v=msdn.10))を使用していて、Windows 管理センターが WINDOWS 10 PC にインストールされている場合は、LAPS の資格情報を使用して、管理対象ノードで認証を行うことができます。 **このシナリオを使用する場合は、フィードバックを提供してください** [provide feedback](https://aka.ms/WACFeedback)。

## <a name="using-tags-to-organize-your-connections"></a>タグを使用した接続の整理

タグを使用して、接続リスト内の関連するサーバーを識別し、フィルター処理することができます。  これにより、サーバーのサブセットを接続リストに表示できます。  これは、多数の接続がある場合に特に便利です。

### <a name="edit-tags"></a>タグの編集

* [すべての接続] の一覧で1つまたは複数のサーバーを選択します。
* [**すべての接続**] の [**タグの編集**] をクリックします。

![Windows 管理センター-[タグの編集] オプション](../media/launch/tags-5.png)

[ **接続タグの編集** ] ウィンドウでは、選択した接続のタグを変更、追加、または削除できます。

* 選択した接続に新しいタグを追加するには、[ **タグの追加** ] を選択し、使用するタグ名を入力します。

* 既存のタグ名を使用して選択した接続にタグを付けるには、適用するタグ名の横にあるチェックボックスをオンにします。

* 選択したすべての接続からタグを削除するには、削除するタグの横にあるチェックボックスをオフにします。

* 選択した接続のサブセットにタグが適用されている場合、このチェックボックスは中間状態として表示されます。 チェックボックスをオンにして確認し、選択したすべての接続にタグを適用するか、もう一度クリックして選択を解除し、選択したすべての接続からタグを削除することができます。

![Windows 管理センター-[接続タグの編集] ページ](../media/launch/tags-6.png)

### <a name="filter-connections-by-tag"></a>タグによる接続のフィルター

1つまたは複数のサーバー接続にタグを追加すると、接続リストでタグを表示し、タグで接続リストをフィルター処理できます。

* タグでフィルター処理するには、検索ボックスの横にあるフィルターアイコンを選択します。

   ![Windows 管理センター-検索ボックスを使用してフィルター処理する](../media/launch/tags-7.png)

   * 選択したタグのフィルター動作を変更するには、"or"、"and"、または "not" を選択します。

   ![Windows 管理センター-[接続のフィルター選択] ページ](../media/launch/tags-8.png)

## <a name="use-powershell-to-import-or-export-your-connections-with-tags"></a>PowerShell を使用して (タグを使って) 接続をインポートまたはエクスポートする

[!INCLUDE [ps-connections](../includes/ps-connections.md)]

## <a name="view-powershell-scripts-used-in-windows-admin-center"></a>Windows 管理センターで使用される PowerShell スクリプトを表示する

サーバー、クラスター、または PC に接続したら、Windows 管理センターで使用可能な UI 操作を強化する PowerShell スクリプトを確認できます。 ツール内から、上部のアプリケーションバーにある PowerShell アイコンをクリックします。 ドロップダウンから目的のコマンドを選択して、対応する PowerShell スクリプトに移動します。

![[概要] ページの PowerShell スクリプトの表示](../media/launch/showscript.png)