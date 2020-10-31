---
title: AD フォレストの回復-GC の追加
ms.author: daveba
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 5a291f65-794e-4fc3-996e-094c5845a383
ms.openlocfilehash: 91f638c5a73b334c63a1ce765aaf0fb776806d5d
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93067994"
---
# <a name="ad-forest-recovery---adding-the-gc"></a>AD フォレストの回復-GC の追加

>適用対象: Windows Server 2016、Windows Server 2012、および 2012 R2、Windows Server 2008 および 2008 R2

グローバルカタログを DC に追加するには、次の手順に従います。

## <a name="to-add-the-global-catalog"></a>グローバルカタログを追加するには

1. [ **スタート** ] をクリックし、[ **すべてのプログラム** ]、[ **管理ツール** ] の順にポイントして、[ **Active Directory サイトとサービス** ] をクリックします。
2. コンソールツリーで、[ **サイト** ] コンテナを展開し、対象サーバーが含まれている適切なサイトを選択します。
3. [ **サーバー** ] コンテナーを展開し、グローバルカタログを追加する DC のサーバーオブジェクトを展開します。
4. [ **NTDS 設定** ] を右クリックし、[ **プロパティ** ] をクリックします。
5. [ **グローバルカタログ** ] チェックボックスをオンにします。
![GC の追加](media/AD-Forest-Recovery-Add-GC/addgc1.png)

## <a name="to-add-the-global-catalog-using-repadmin"></a>Repadmin を使用してグローバルカタログを追加するには

- 管理者特権でのコマンドプロンプトを開き、次のコマンドを入力して、enter キーを押します。

   ```
   repadmin.exe /options DC_NAME +IS_GC
   ```

次に、グローバルカタログをルートドメインの DC に追加するプロセスを高速化する方法を示します。

- ルートドメインの DC は、ルート以外のドメインの復元された Dc のレプリケーションパートナーであることが理想的です。 その場合は、知識整合性チェッカー (KCC) によって、ルート DC 内のソース DC およびパーティションに対応する **repsFrom** オブジェクトが作成されていることを確認します。 これを確認するには、 **repadmin/showreps/v** コマンドを実行します。

- **RepsFrom** オブジェクトが作成されていない場合は、構成パーティション用にこのオブジェクトを作成します。 これにより、ルートドメインの DC は、ルート以外のドメイン内のどの Dc が削除されたかを判断できます。 これを行うには、次のコマンドを使用します。

   ```
   repadmin /add ConfigurationNamingContext DestinationDomainController SourceDomainControllerCNAME
   ```

   ```
   repadmin /options DSA -Disable_NTDSCONN_XLATE
   ```

   *Sourcedomainコントローラー cname* の形式は次のとおりです。

   ```

   sourceDCGuid._msdcs.root domain
   ```

   たとえば、contoso.com ドメインの構成パーティションの repadmin/add コマンドは次のようになります。

   ```
   repadmin /add cn=configuration,DC=contoso,DC=com DC01 937ef930-7356-43c8-88dc-8baaaa781cf6._msdcs.dDSP17A22.contoso.com
   ```

- **RepsFrom** オブジェクトが存在する場合は、ルートドメインの dc と非ルートドメインの dc を次のように同期します。

   ```
   Repadmin /sync DomainNamingContext DestinationDomainController SourceDomainControllerGUID
   ```

   ここで、 *DestinationDomainController* はルートドメインの Dc、 *SourceDomainController* はルート以外のドメインの復元された dc です。

- ルートドメインの DNS サーバーには、ソース DC のエイリアス (CNAME) リソースレコードが必要です。 親 DNS ゾーンに、子ゾーンの正しい Dc (バックアップから復元された Dc) の委任リソースレコード (ネームサーバー (NS) とホスト (A) リソースレコード) が含まれていることを確認します。
- ルートドメインの DC が、ルート以外のドメインの正しいキー配布センター (KDC) に接続していることを確認します。 これをテストするには、コマンドプロンプトで次のコマンドを入力し、enter キーを押します。

   ```
   nltest /dsgetdc:nonroot domain name /KDC /Force
   ```

## <a name="next-steps"></a>次の手順

- [AD フォレストの回復ガイド](AD-Forest-Recovery-Guide.md)
- [AD フォレストの回復 - 手順](AD-Forest-Recovery-Procedures.md)
