---
title: Azure File Sync を使用してファイル サーバーとクラウドを同期する
description: Azure File Sync を使用すると、オンプレミスのファイルサーバーの柔軟性、パフォーマンス、および互換性を維持しながら、Azure で組織のファイル共有を一元化できます。 Azure File Sync は、Windows Server を、オプションのクラウドの階層化機能を使用して、Azure ファイル共有の高速キャッシュに変換します。
ms.topic: article
author: fauhse
ms.author: fauhse
ms.date: 04/12/2019
ms.localizationpriority: medium
ms.openlocfilehash: 56937ad0351a1421ab64b93351d7fa5f6d9f4fe8
ms.sourcegitcommit: 5344adcf9c0462561a4f9d47d80afc1d095a5b13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2020
ms.locfileid: "90766685"
---
# <a name="sync-your-file-server-with-the-cloud-by-using-azure-file-sync"></a>Azure File Sync を使用してファイル サーバーとクラウドを同期する

>適用先:Windows Admin Center、Windows Admin Center Preview

Azure File Sync を使用すると、オンプレミスのファイルサーバーの柔軟性、パフォーマンス、および互換性を維持しながら、Azure で組織のファイル共有を一元化できます。 Azure File Sync は、Windows Server を、オプションのクラウドの階層化機能を使用して、Azure ファイル共有の高速キャッシュに変換します。 SMB、NFS、FTPS など、Windows Server 上で利用できるあらゆるプロトコルを使用して、データにローカルにアクセスできます。

ファイルがクラウドに同期されたら、同じ Azure ファイル共有に複数のサーバーを接続して、コンテンツをローカルに同期してキャッシュすることができます。アクセス許可 (Acl) も常に転送されます。 Azure Files には、Azure ファイル共有の差分スナップショットを生成できるスナップショット機能が用意されています。 これらのスナップショットは、参照と復元を容易にするために、SMB 経由で読み取り専用ネットワークドライブとしてマウントすることもできます。 クラウドの階層化と組み合わせることで、オンプレミスのファイルサーバーを簡単に実行できるようになりました。

詳細については、「 [Planning for a Azure File Sync deployment](/azure/storage/files/storage-sync-files-planning)」を参照してください。