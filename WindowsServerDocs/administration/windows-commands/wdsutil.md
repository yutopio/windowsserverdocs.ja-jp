---
title: wdsutil
description: Windows 展開サービスサーバーの管理に使用されるコマンドラインユーティリティである wdsutil のリファレンス記事です。
ms.topic: reference
ms.assetid: 3a1965a0-8677-40cc-9495-30ae806808d1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7516eea3d6edd013b3f507671e6b219da7dfd632
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718369"
---
# <a name="wdsutil"></a>wdsutil

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

wdsutil は、Windows 展開サービスサーバーの管理に使用するコマンドラインユーティリティです。 これらのコマンドを実行するには、[ **スタート**] ボタンをクリックし、[ **コマンドプロンプト**] を右クリックして、[ **管理者として実行**] をクリックします。

## <a name="commands"></a>コマンド

|コマンド|説明|
|------|--------|
|[wdsutil コマンドの追加](wdsutil-add.md)|オブジェクトまたはプレステージコンピューターを追加します。|
|[wdsutil 承認-autoadddevices コマンド](wdsutil-approve-autoadddevices.md)|管理者の承認待ちのコンピューターを承認します。|
|[wdsutil riprepimage コマンド](wdsutil-convert-riprepimage.md)|既存のリモートインストール準備 (RIPrep) イメージを Windows イメージ (.wim) ファイルに変換します。|
|[wdsutil copy コマンド](wdsutil-copy.md)|イメージ、ドライバー グループをコピーします。|
|[wdsutil delete-autoadddevices コマンド](wdsutil-delete-autoadddevices.md)|自動追加データベースにあるコンピューターのうち、サーバー上のコンピューターに関する情報を格納するコンピューターを削除します。|
|[wdsutil disable コマンド](wdsutil-disable.md)|Windows 展開サービスのすべてのサービスを無効にします。|
|[wdsutil disconnect-クライアントコマンド](wdsutil-disconnect-client.md)|マルチキャスト転送または名前空間を使用して、クライアントを切断します。|
|[wdsutil enable コマンド](wdsutil-enable.md)|Windows 展開サービスのすべてのサービスを有効にします。|
|[wdsutil export-イメージコマンド](wdsutil-export-image.md)|イメージストアから .wim ファイルにイメージをエクスポートします。|
|[wdsutil get コマンド](wdsutil-get.md)|指定したオブジェクトに関するプロパティと属性を取得します。|
|[wdsutil initialize-サーバーコマンド](wdsutil-initialize-server.md)|初期使用のために Windows 展開サービスサーバーを構成します。|
|[wdsutil new コマンド](wdsutil-new.md)|新しいキャプチャと検出イメージだけでなく、マルチキャスト転送と名前空間を作成します。|
|[wdsutil progress コマンド](wdsutil-progress.md)|コマンドの実行中に進行状況の状態を表示します。|
|[wdsutil 拒否-autoadddevices コマンド](wdsutil-reject-autoadddevices.md)|管理者の承認待ちのコンピューターを拒否します。|
|[wdsutil コマンドの削除](wdsutil-remove.md)|オブジェクトを削除します。|
|[wdsutil replace-イメージコマンド](wdsutil-replace-image.md)|ブートイメージまたはインストールイメージを、そのイメージの新しいバージョンに置き換えます。|
|[wdsutil set コマンド](wdsutil-set.md)|指定したオブジェクトのプロパティと属性を設定します。|
|[wdsutil start server コマンド](wdsutil-start-server.md)|マルチキャスト転送、名前空間、トランスポートサーバーなど、Windows 展開サービスサーバー上のすべてのサービスを開始します。|
|[wdsutil サーバーの停止コマンド](wdsutil-stop-server.md)|Windows 展開サービスサーバー上のすべてのサービスを停止します。|
|[wdsutil 初期化解除-サーバーコマンド](wdsutil-uninitialize-server.md)|サーバーの初期化中に行われた変更を元に戻します。|
|[wdsutil update-serverfiles コマンド](wdsutil-update-serverfiles.md)|RemoteInstall 共有上のサーバーファイルを更新します。|
|[wdsutil verbose コマンド](wdsutil-verbose.md)|指定したコマンドの詳細出力を表示します。|
