---
title: repair-bde
description: 修復 bde コマンドのリファレンス記事。 BitLocker を使用してドライブが暗号化されている場合は、重大な損傷を受けたドライブの重要な部分を再構築し、回復可能なデータを回復することができます。
ms.topic: reference
ms.assetid: 534dca1a-05f7-4ea8-ac24-4fe5f14f988a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e7ebf0f2923e565e16e546a7804ee42771eec83d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640637"
---
# <a name="repair-bde"></a>repair-bde

重大な損傷を受けたドライブの重要な部分の再構築を試行し、BitLocker を使用してドライブが暗号化されている場合は回復可能なデータを回復します。また、暗号化解除のために有効な回復パスワードまたは回復キーを持っている場合は、

> [!IMPORTANT]
> ドライブ上の BitLocker メタデータデータが破損している場合は、回復パスワードまたは回復キーに加えて、バックアップキーパッケージを指定できる必要があります。 Active Directory Domain Services の [既定のキーのバックアップ] 設定を使用した場合は、キーパッケージがバックアップされます。 Bitlocker [: Bitlocker 回復パスワードビューアー](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-use-bitlocker-recovery-password-viewer) を使用して、AD DS からキーパッケージを取得できます。
>
> キーパッケージと回復パスワードまたは回復キーを使用すると、ディスクが破損している場合でも、BitLocker で保護されたドライブの一部を暗号化解除できます。 各キーパッケージは、対応するドライブ識別子を持つドライブに対してのみ機能します。

## <a name="syntax"></a>構文

```
repair-bde <inputvolume> <outputvolumeorimage> [-rk] [–rp] [-pw] [–kp] [–lf] [-f] [{-?|/?}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<inputvolume>` | 修復する BitLocker で暗号化されたドライブのドライブ文字を指定します。 ドライブ文字にはコロンを含める必要があります。例: **C:**。 キーパッケージへのパスが指定されていない場合、このコマンドはドライブでキーパッケージを検索します。 ハードドライブが破損している場合は、このコマンドでパッケージを見つけることができず、パスを入力するように求められます。 |
| `<outputvolumeorimage>` | 修復されたドライブの内容を保存するドライブを指定します。 出力ドライブのすべての情報が上書きされます。 |
| -rk | ボリュームのロックを解除するために使用する回復キーの場所を指定します。 このコマンドは **、-recoverykey**として指定することもできます。 |
| -rp | ボリュームのロックを解除するために使用する必要がある数値回復パスワードを指定します。 このコマンドは **、-recoverypassword**として指定することもできます。 |
| -pw | ボリュームのロックを解除するために使用するパスワードを指定します。 このコマンドは **、パスワード**として指定することもできます。 |
| -kp | ボリュームのロックを解除するために使用できる回復キーパッケージを識別します。 このコマンドは **、-keypackage**として指定することもできます。 |
| -lf | 修復 bde エラー、警告、および情報メッセージを格納するファイルへのパスを指定します。 このコマンドは **、-logfile**として指定することもできます。 |
| -f | ボリュームをロックできない場合でも、強制的にマウントを解除します。 このコマンドは **、-force**として指定することもできます。 |
| -? または /? | コマンド プロンプトでヘルプを表示します。 |

### <a name="limitations"></a>制限事項

このコマンドには、次の制限があります。

- このコマンドでは、暗号化または暗号化解除のプロセス中に失敗したドライブを修復することはできません。

- このコマンドは、ドライブに暗号化がある場合、ドライブが完全に暗号化されていることを前提としています。

## <a name="examples"></a>例

ドライブ C: の修復を試行するには、ドライブ C: に格納されている回復キーファイル (RecoveryKey. bek) を使用してドライブ D: ドライブに格納されている回復キーファイル (RecoveryKey bek) を使用して、ドライブ Z: のログファイル (log.txt) に次のように入力します。

```
repair-bde C: D: -rk F:\RecoveryKey.bek –lf Z:\log.txt
```

ドライブ C: を修復し、ドライブ C: からドライブ D: にコンテンツを書き込むには、指定された48数字の回復パスワードを使用して、次のように入力します。

```
repair-bde C: D: -rp 111111-222222-333333-444444-555555-666666-777777-888888
```

>[!NOTE]
> 回復パスワードは、各ブロックをハイフンで区切った6桁の8つのブロックで入力する必要があります。

ドライブ C: を強制的にマウント解除するには、ドライブ c: を修復し、ドライブ C: からドライブ c: にコンテンツを書き込みます。ドライブ F: に格納されている回復キーパッケージと回復キーファイル (RecoveryKey. bek) を使用して、次のように入力します。

```
repair-bde C: D: -kp F:\RecoveryKeyPackage -rk F:\RecoveryKey.bek -f
```

ドライブ c: を修復し、ドライブ c: からドライブ D: にコンテンツを書き込むには、パスワードを入力する必要があります。ドライブ C: (メッセージが表示された場合) には、次のように入力します。

```
repair-bde C: D: -pw
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
