---
title: pwlauncher
description: Pwlauncher コマンドの参照記事。 Windows To 進むスタートアップオプション (pwlauncher) を有効または無効にします。
ms.topic: reference
ms.assetid: 0917bb7b-408a-40f7-a1c5-20e94c10d38b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8bdc4f7b3b5c91cb804f6760a60ec421652d1642
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639926"
---
# <a name="pwlauncher"></a>pwlauncher

Windows To 進むスタートアップオプション (pwlauncher) を有効または無効にします。 **Pwlauncher**コマンドラインツールを使用すると、コンピューターを Windows to 移動ワークスペースで自動的に起動するように構成することができます (1 つが存在する場合)。ただし、ファームウェアを入力したり、スタートアップオプションを変更したりする必要はありません。

Windows To 進むスタートアップオプションを使用すると、ファームウェアが USB からの起動をサポートしている限り、Windows 内から USB から起動するようにコンピューターを構成することができます。 システムが常に USB から起動できるようにするには、まず考慮する必要があることに注意してください。 たとえば、マルウェアを含む USB デバイスが誤ってシステムを危険にさらす可能性がある場合や、複数の USB ドライブが接続され、ブートの競合が発生する場合があります。 このため、既定の構成では、Windows To 進むスタートアップオプションが既定で無効になっています。 また、Windows To ゴースタートアップオプションを構成するには、管理者特権が必要です。 Pwlauncher コマンドラインツールまたは **Windows To ゴースタートアップオプションを変更** するアプリを使用して Windows to 進むスタートアップオプションを有効にすると、コンピューターは起動前にコンピューターに挿入されている任意の USB デバイスから起動しようとします。

## <a name="syntax"></a>構文

```
pwlauncher {/enable | /disable}
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /enable | Windows To ゴースタートアップオプションを有効にします。これにより、コンピューターは、USB デバイスが存在する場合に自動的に起動します。 |
| /disable | Windows To ゴースタートアップオプションを無効にします。これにより、ファームウェアで手動で構成しない限り、コンピューターを USB デバイスからブートできなくなります。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

USB からのブートを有効にするには:

```
pwlauncher /enable
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
