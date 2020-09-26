---
title: scwcmd register
description: Scwcmd register コマンドの参照記事。ロール、タスク、サービス、またはポートの定義を含むセキュリティ構成データベースファイルを登録して、セキュリティ構成ウィザード (SCW) のセキュリティ構成データベースを拡張またはカスタマイズします。
ms.topic: reference
ms.assetid: fe4d126a-9f27-4076-b7b1-fbefa45f378a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b1e981ef2a428174406fd793d5c959de57a8067c
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388578"
---
# <a name="scwcmd-register"></a>scwcmd register

> 適用対象: Windows Server 2012 R2 および Windows Server 2012

拡張または役割、タスク、サービス、またはポートの定義を含むセキュリティの構成データベース ファイルを登録することによってセキュリティ構成ウィザード (SCW) のセキュリティの構成データベースをカスタマイズします。

## <a name="syntax"></a>構文

```
scwcmd register /kbname:<MyApp> [/kbfile:<kb.xml>] [/kb:<path>] [/d]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /kbname:`<MyApp>` | セキュリティ構成データベースの拡張機能の登録を使用する名前を指定します。 このパラメーターを指定する必要があります。 |
| /kbfile`<kb.xml>` | 基本セキュリティ構成データベースを拡張またはカスタマイズするために使用するセキュリティ構成データベースファイルのパスとファイル名を指定します。 セキュリティ構成データベースファイルが SCW スキーマに準拠しているかどうかを検証するには、 `%windir%\security\KBRegistrationInfo.xsd` スキーマ定義ファイルを使用します。 しない限り、このオプションを指定する必要があります、 **/d** パラメーターを指定します。 |
| /kb`<path>` | 更新するセキュリティの構成データベース ファイルを含むディレクトリへのパスを指定します。 このオプションが指定されていない場合 `%windir%\security\msscw\kbs` は、が使用されます。 |
| /d | セキュリティの構成データベースからセキュリティの構成データベースの拡張機能の登録を解除します。 登録を解除する拡張機能は、 **/kbname** パラメーターによって指定されます。 ( **/Kb ファイル** パラメーターを指定しないでください)。拡張機能の登録を解除するセキュリティ構成データベースは、 **/kb** パラメーターによって指定されます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

場所に*MyApp*という名前の*SCWKBForMyApp.xml*という名前のセキュリティ構成データベースファイルを登録するには `\\kbserver\kb` 、次のように入力します。

```
scwcmd register /kbfile:d:\SCWKBForMyApp.xml /kbname:MyApp /kb:\\kbserver\kb
```

にあるセキュリティ構成データベース *MyApp*の登録を解除するには `\\kbserver\kb` 、次のように入力します。

```
scwcmd register /d /kbname:MyApp /kb:\\kbserver\kb
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [scwcmd analyze コマンド](scwcmd-analyze.md)

- [scwcmd configure コマンド](scwcmd-configure.md)

- [scwcmd rollback コマンド](scwcmd-rollback.md)

- [scwcmd transform コマンド](scwcmd-transform.md)

- [scwcmd view コマンド](scwcmd-view.md)