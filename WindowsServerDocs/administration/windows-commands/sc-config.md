---
title: sc.exe 構成
description: sc.exe config コマンドの参照記事。レジストリおよびサービスコントロールマネージャーデータベースでサービスのエントリの値を変更することによって、サービスの構成を変更します。
ms.topic: reference
ms.assetid: ad4d68a6-efe5-452b-8501-7f1f1c552a4a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 06/05/2018
ms.openlocfilehash: 55587314e87f8eca50b94ad9f102aebc72324dd2
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388828"
---
# <a name="scexe-config"></a>sc.exe 構成

レジストリおよびサービス コントロール マネージャー データベースのサービスのエントリの値を変更します。

## <a name="syntax"></a>構文

```
sc.exe [<servername>] config [<servicename>] [type= {own | share | kernel | filesys | rec | adapt | interact type= {own | share}}] [start= {boot | system | auto | demand | disabled | delayed-auto}] [error= {normal | severe | critical | ignore}] [binpath= <binarypathname>] [group= <loadordergroup>] [tag= {yes | no}] [depend= <dependencies>] [obj= {<accountname> | <objectname>}] [displayname= <displayname>] [password= <password>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| `<servername>` | サービスが配置されているリモート サーバーの名前を指定します。 名前には、汎用名前付け規則 (UNC) 形式 (myserver など) を使用する必要があり \\ ます。 SC.exe をローカルで実行するには、このパラメーターを使用しないでください。 |
| `<servicename>` | によって返されるサービスの名前を指定、 **られて** 操作します。 |
| `type= {own | share | kernel | filesys | rec | adapt | interact type= {own | share}}` | サービスの種類を指定します。 選択肢は次のようになっています。<ul><li>**独自** -独自のプロセスで実行されているサービスを指定します。 実行可能ファイルは他のサービスと共有されません。 これが既定値です。</li><li>**共有** -共有プロセスとして実行されるサービスを指定します。 その他のサービス実行可能ファイルを共有します。</li><li>**カーネル** のドライバーを指定します。</li><li>**filesys** -ファイル システム ドライバーを指定します。</li><li>**推奨値** -ファイル システムで認められたコンピューターで使用されるファイル システムを識別するドライバーを指定します。</li><li>**適応** - キーボード、マウスなどのハードウェア デバイスを識別するアダプタのドライバを指定し、ディスク ドライブします。</li><li>**対話** -ユーザーからの入力を受け取って、デスクトップと対話可能なサービスを指定します。 対話型サービスは、LocalSystem アカウントで実行する必要があります。 この型は、 **type = 独自**または**type = shared**と組み合わせて使用する必要があります (たとえば、 **type = 相互作用****型 = 独自**)。 使用して **型 = 対話** 自体でエラーが生成されます。</li></ul> |
| `start= {boot | system | auto | demand | disabled | delayed-auto}` | サービスの開始の種類を指定します。 選択肢は次のようになっています。<ul><li>**ブート** のブート ローダーによって読み込まれるデバイス ドライバーを指定します。</li><li>**システム** のカーネルの初期化中に開始されるデバイス ドライバーを指定します。</li><li>**自動** - サービスが自動的に各開始ときに、コンピューターの再起動を指定し、コンピューターにログオンできない場合でも実行できます。</li><li>**必要に応じて** -を手動で起動するサービスを指定します。 これは既定値の場合 **開始 =** が指定されていません。</li><li>**無効になっている** -サービスを起動できないように指定します。 無効なサービスを開始するには、他のいくつかの値に開始の種類を変更します。</li><li>**遅延自動** -サービスが自動的に開始短い形式の時刻が、その他の自動サービスの開始後を指定します。</li></ul> |
| `error= {normal | severe | critical | ignore}` | コンピューターの起動時にサービスを開始できない場合のエラーの重大度を指定します。 選択肢は次のようになっています。<ul><li>**通常** -サービスの開始に失敗したユーザーに通知エラーをログに記録し、メッセージ ボックスが表示されることを指定します。 起動が続行されます。 これが既定の設定です。</li><li>**重大な** -エラーが (可能な場合) に記録するように指定します。 コンピューターは、前回正常起動時の構成と再起動を試みます。 コンピューターを再起動することが発生する可能性がサービス可能性がありますもことはできませんを実行します。</li><li>**重要な** -エラーが (可能な場合) に記録するように指定します。 コンピューターは、前回正常起動時の構成と再起動を試みます。 前回正常起動時の構成が失敗した場合、スタートアップも失敗し、ブート プロセスが Stop エラーで停止します。</li><li>**無視** -エラーがログに記録し、起動処理は続行するように指定します。 イベント ログにエラーを記録する以外のユーザーに通知は表示されません。</li></ul> |
| `binpath= <binarypathname>` | サービスのバイナリ ファイルへのパスを指定します。 既定値はありません **binpath =**, 、この文字列を提供する必要があります。 |
| `group= <loadordergroup>` | このサービスがメンバーになっているグループの名前を指定します。 グループの一覧が、レジストリに格納されている、 **HKLM\System\CurrentControlSet\Control\ServiceGroupOrder** サブキー。 既定値は、null です。 |
| `tag= {yes | no}` | CreateService 呼び出し、TagID で取得するかどうかを指定します。 タグは、ブート開始またはシステム開始ドライバーに対してだけ使用されます。 |
| `depend= <dependencies>` | サービスまたはこのサービスの前に、まずグループの名前を指定します。 名前は、スラッシュ (/) で区切られます。 |
| `obj= {<accountname> | <objectname>}` | サービスが実行されますが、またはドライバーを実行する Windows ドライバー オブジェクトの名前を指定するアカウントの名を指定します。 既定の設定は **LocalSystem**します。 |
| `displayname= <displayname>` | ユーザー インターフェイスのプログラムでサービスを識別するためのわかりやすい名前を指定します。 たとえば、1 つの特定のサービスのサブキーの名前は **wuauserv**, 、自動更新のわかりやすい表示名を持ちます。 |
| `password= <password>` | パスワードを指定します。 ローカル システム アカウント以外のアカウントを使用する場合に必要です。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- 各コマンドラインオプション (パラメーター) には、オプション名の一部として等号を含める必要があります。

- スペースは、オプションとその値の間で必要な (たとえば、 **型 = 独自**します。 スペースを省略した場合、操作は失敗します。

## <a name="examples"></a>例

*Newservice*サービスのバイナリパスを指定するには、次のように入力します。

```
sc.exe config NewService binpath= ntsd -d c:\windows\system32\NewServ.exe
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
