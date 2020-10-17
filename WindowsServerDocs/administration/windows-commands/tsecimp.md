---
title: tsecimp
description: Tsecimp コマンドの参照記事。これは、拡張マークアップ言語 (XML) ファイルからの割り当て情報を TAPI サーバーセキュリティファイル (Tsec.ini) にインポートします。
ms.topic: reference
ms.assetid: d7488ec6-0eff-45ff-89ee-9cbe752416bf
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0db7c7c191b4ca4cdd1d266892b68aa717c142da
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156704"
---
# <a name="tsecimp"></a>tsecimp

拡張マークアップ言語 (XML) ファイルからの割り当て情報を TAPI サーバーセキュリティファイル (Tsec.ini) にインポートします。 また、このコマンドを使用して、TAPI プロバイダーと、それぞれに関連付けられている回線デバイスの一覧を表示したり、コンテンツをインポートせずに XML ファイルの構造を検証したり、ドメインのメンバーシップを確認したりすることもできます。

## <a name="syntax"></a>構文

```
tsecimp /f <filename> [{/v | /u}]
tsecimp /d
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /f `<filename>` | 必須です。 インポートする割り当て情報を含んだ XML ファイルの名前を指定します。 |
| /v | Tsec.ini ファイルに情報をインポートせず、XML ファイルの構造を検証します。 |
| /U | 各ユーザーについて、XML ファイルで指定されたドメインのメンバーかどうかをチェックします。 このパラメーターは、ネットワークに接続されているコンピューター上で使用する必要があります。 大量のユーザー割り当て情報を処理する場合、このパラメーターを指定するとパフォーマンスが大幅に低下することがあります。 |
| /d | インストールされているテレフォニー プロバイダーの一覧を表示します。 テレフォニー プロバイダーごとに、関連付けられた回線デバイスと、各回線デバイスに関連付けられたアドレスおよびユーザーが表示されます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

割り当て情報のインポート元となる XML ファイルは、以下で説明する構造に従う必要があります。

```xml
<UserList>
  <User>
    <LineList>
      <Line>
```

- `<Userlist element>` -XML ファイルの最上位要素。

- `<User element>` -ドメインのメンバーであるユーザーに関する情報が含まれています。 各ユーザーには 1 つ以上の回線デバイスが割り当てられることがあります。 さらに、各 **ユーザー** 要素には、 **nomerge**という名前の属性が含まれている場合があります。 この属性が指定されている場合、ユーザーに対する回線デバイスの現在の割り当ては、新しい割り当てが作成される前にすべて削除されます。 この属性を使用すると、無用なユーザー割り当てを簡単に削除できます。 既定では、この属性は指定されません。 **User**要素には、ユーザーのドメインとユーザー名を指定する単一の**domainusername**要素が含まれている必要があります。 **User**要素には、ユーザーのフレンドリ名を指定する**FriendlyName**要素が1つ含まれている場合もあります。 **User**要素には、 **linelist**要素が1つ含まれている場合があります。 **Linelist**要素が存在しない場合、このユーザーのすべてのラインデバイスが削除されます。

- `<LineList element>` -ユーザーに割り当てられている可能性のある各回線またはデバイスに関する情報が含まれています。 各 **Linelist** 要素には、複数の **Line** 要素を含めることができます。

- `<Line element>` -ラインデバイスを指定します。 **Line 要素の下**に**Address**要素または**PermanentID**要素を追加することによって、各ラインデバイスを識別する必要があります。 各 **Line** 要素に対して、 **Remove** 属性を設定できます。 この属性を設定した場合、当該ユーザーはその回線デバイスに割り当てられなくなります。 設定しない場合、当該ユーザーはその回線デバイスにアクセスできます。 ユーザーが回線デバイスを使用できない場合、エラーは表示されません。

##### <a name="sample-output-for-d-parameter"></a>/D パラメーターの出力例

このサンプル出力は、 **/d** パラメーターを実行して現在の TAPI 構成を表示した後に表示されます。 テレフォニー プロバイダーごとに、関連付けられた回線デバイスと、各回線デバイスに関連付けられたアドレスおよびユーザーが表示されます。

```
NDIS Proxy TAPI Service Provider
  Line: WAN Miniport (L2TP)
    Permanent ID: 12345678910

NDIS Proxy TAPI Service Provider
  Line: LPT1DOMAIN1\User1
    Permanent ID: 12345678910

Microsoft H.323 Telephony Service Provider
  Line: H323 Line
    Permanent ID: 123456
    Addresses:
      BLDG1-TAPI32
```

## <a name="examples"></a>使用例

*User1*に割り当てられているすべての回線デバイスを削除するには、次のように入力します。

```xml
<UserList>
  <User NoMerge=1>
    <DomainUser>domain1\user1</DomainUser>
  </User>
</UserList>
```

*User1*に割り当てられているすべての回線デバイスを削除するには、アドレス*99999*を使用して1行を割り当てる前に、次のように入力します。

```xml
<UserList>
  <User NoMerge=1>
  <DomainUser>domain1\user1</DomainUser>
  <FriendlyName>User1</FriendlyName>
  <LineList>
    <Line>
      <Address>99999</Address>
    </Line>
  </LineList>
  </User>
</UserList>
```

この例では、既に回線デバイスが割り当てられているかどうかに関係なく、 *User1* には他のラインデバイスが割り当てられていません。

*User1*に1つのラインデバイスを追加するには、以前に割り当てられた回線デバイスを削除せずに、次のように入力します。

```xml
<UserList>
  <User>
  <DomainUser>domain1\user1</DomainUser>
  <FriendlyName>User1</FriendlyName>
  <LineList>
    <Line>
      <Address>99999</Address>
    </Line>
  </LineList>
  </User>
</UserList>
```

行アドレス*99999*を追加し、 *user1*アクセスから行アドレス*88888*を削除するには、次のように入力します。

```xml
<UserList>
  <User>
  <DomainUser>domain1\user1</DomainUser>
  <FriendlyName>User1</FriendlyName>
  <LineList>
    <Line>
      <Address>99999</Address>
    </Line>
    <Line Remove=1>
      <Address>88888</Address>
    </Line>
  </LineList>
  </User>
</UserList>
```

永続的なデバイス*1000*を追加し、 *user1*アクセスから行*88888*を削除するには、次のように入力します。

```xml
<UserList>
  <User>
  <DomainUser>domain1\user1</DomainUser>
  <FriendlyName>User1</FriendlyName>
  <LineList>
    <Line>
    <PermanentID>1000</PermanentID>
    </Line>
    <Line Remove=1>
    <Address>88888</Address>
    </Line>
  </LineList>
  </User>
</UserList>
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コマンド シェルの概要](/previous-versions/windows/it-pro/windows-server-2003/cc737438(v=ws.10))
