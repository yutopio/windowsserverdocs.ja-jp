---
title: 管理者のための Windows デスクトップ クライアント
description: Windows デスクトップ クライアントの情報は、主に管理者に役立ちます。
ms.topic: article
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 12/02/2020
ms.localizationpriority: medium
ms.openlocfilehash: fe553c03e85f3cb68f76b1a8d27e1da93bf9d9a3
ms.sourcegitcommit: dce404a0a4500a693e294e0431c93f0ae90f8b13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2020
ms.locfileid: "96563782"
---
# <a name="windows-desktop-client-for-admins"></a>管理者のための Windows デスクトップ クライアント

>適用先:Windows 10 および Windows 7

このトピックでは、管理者にとって役に立つ Windows デスクトップ クライアントに関する追加情報を示します。 基本的な使用方法については、「[Windows デスクトップ クライアントの概要](windowsdesktop.md)」を参照してください。

## <a name="installation-options"></a>インストール オプション

ユーザーはダウンロード後にクライアントを直接インストールできますが、管理者が複数のデバイスに展開する場合は、他の方法でデバイスにクライアントを展開することもできます。 グループ ポリシーまたは Microsoft Endpoint Configuration Manager を使用して展開すると、コマンド ラインを使用してインストーラーをサイレント モードで実行できます。 デバイスごとまたはユーザーごとにクライアントを展開するには、次のコマンドを実行します。

### <a name="per-device-installation"></a>デバイスごとのインストール

```
msiexec.exe /I <path to the MSI> /qn ALLUSERS=1
```

### <a name="per-user-installation"></a>ユーザーごとのインストール

```
msiexec.exe /i `<path to the MSI>` /qn ALLUSERS=2 MSIINSTALLPERUSER=1
```

## <a name="configuration-options"></a>構成オプション

このセクションでは、このクライアントの新しい構成オプションについて説明します。

### <a name="configure-update-notifications"></a>更新プログラム通知を構成する

既定では、更新プログラムがあるたびにクライアントから通知され、クライアントが閉じていて、アクティブな接続がないときに、クライアントは自動的に更新されます。 アクティブな接続がない場合でも、msrdc.exe プロセスはバックグラウンドで実行されるので、クライアントを再度開いたときにすぐに再接続することができます。 msrdc.exe を停止するには、システム トレイ領域の Windows Virtual Desktop アイコンを右クリックし、ドロップダウン メニューの **[セッションをすべて切断]** を選択します。

通知をオフにするには、次のレジストリ情報を設定します。

- **キー:** HKLM\Software\Microsoft\MSRDC\Policies
- **型:** REG_DWORD
- **名前:** AutomaticUpdates
- **データ:** 0 = 通知を無効にする。 1 = 通知を表示する。 2 = 通知を表示し、クローズ時に自動更新する。

### <a name="configure-user-groups"></a>ユーザー グループを構成する

次のいずれかの種類のユーザー グループ用にクライアントを構成できます。これにより、クライアントがいつ更新プログラムを受け取るかが決まります。

#### <a name="insider-group"></a>Insider グループ

Insider グループは早期検証用であり、管理者と管理者によって選択されたユーザーで構成されます。 Insider グループは、テスト実行を行って、Public グループにリリースされる前に、パフォーマンスに影響する可能性がある更新プログラムの問題を検出します。

> [!NOTE]
> 更新プログラムをテストして問題を早期に発見するには、各組織のユーザーを Insider グループに含めることをお勧めします。

Insider グループでは、早期検証のために、毎月第 2 火曜日に新しいバージョンのクライアントがユーザーにリリースされます。 更新プログラムに問題がない場合は、2 週間後に Public グループにリリースされます。 Insider グループのユーザーは、更新プログラムの準備が整うたびに、更新プログラム通知を自動的に受け取ります。 クライアントに対する変更の詳細は、「[Windows デスクトップ クライアントの新機能](windowsdesktop-whatsnew.md)」で確認できます。

Insider グループのクライアントを構成するには、次のレジストリ情報を設定します。

- **キー:** HKLM\Software\Microsoft\MSRDC\Policies
- **型:** REG_SZ
- **名前:** ReleaseRing
- **データ:** insider

#### <a name="public-group"></a>Public グループ

このグループはすべてのユーザーが対象であり、最も安定したバージョンです。 このグループを構成するために何もする必要はありません。

Public グループは、毎月第 4 火曜日に、Insider グループによってテストされたバージョンのクライアントを受け取ります。 設定が有効になっている場合、Public グループのすべてのユーザーが更新プログラム通知を受け取ります。
