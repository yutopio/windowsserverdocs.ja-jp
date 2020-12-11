---
description: 詳細については、障害ドメインの認識
ms.assetid: 56fc7f80-9558-467e-a6e9-a04c9abbee33
title: フォールト ドメインの認識
ms.author: cosdar
manager: eldenc
ms.topic: article
author: cosmosdarwin
ms.date: 09/16/2016
ms.openlocfilehash: 5f0c3df62ec7385a3402a8b71b8f50d4a7b359a2
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97048660"
---
# <a name="fault-domain-awareness"></a>フォールト ドメインの認識

> 適用対象: Windows Server 2019 および Windows Server 2016

フェールオーバー クラスタリングでは、複数のサーバーが連携して高可用性 (言い換えれば、ノードのフォールト トレランス) を実現できます。 しかし、今日のビジネスではインフラストラクチャからの可用性が高まっています。 クラウドのようなアップタイムを達成するには、シャーシの障害、ラックの停止、自然災害など、発生する可能性が極めて低い事態であっても対策を講じる必要があります。 そのため、Windows Server 2016 のフェールオーバークラスタリングでは、シャーシ、ラック、およびサイトフォールトトレランスも導入されました。

## <a name="fault-domain-awareness"></a>フォールト ドメインの認識

障害ドメインとフォールト トレランスは、密接に関連する概念です。 障害ドメインとは、単一障害点を共有するハードウェア コンポーネントのセットです。 特定のレベルのフォールト トレランスを実現するには、そのレベルに複数の障害ドメインが必要です。 たとえば、ラックのフォールト トレランスを実現するには、サーバーとデータが複数のラックに分散されている必要があります。

この短いビデオでは、Windows Server 2016 の障害ドメインの概要について説明します。 [ ![ windows server 2016 の障害ドメインの概要については、このイメージをクリックし](media/Fault-Domains-in-Windows-Server-2016/Part-1-Fault-Domains-Overview.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-1-Overview)てください。

### <a name="fault-domain-awareness-in-windows-server-2019"></a>Windows Server 2019 での障害ドメインの認識

障害ドメインの認識は Windows Server 2019 で利用できますが、既定で無効になっているため、Windows レジストリを使用して有効にする必要があります。

Windows Server 2019 で障害ドメインの認識を有効にするには、Windows レジストリに移動し、(クラスターの取得) を設定します。自動割り当てのレジストリキーを1にします。

```Registry
    (Get-Cluster).AutoAssignNodeSite=1
```

Windows 2019 で障害ドメインの認識を無効にするには、Windows レジストリに移動し、(クラスターの取得) を設定します。レジストリキーが0に自動割り当てされます。

```Registry
    (Get-Cluster).AutoAssignNodeSite=0
```

## <a name="benefits"></a>利点
- **記憶域スペース ダイレクトを含めて、記憶域スペースでは、データの安全性を最大化するために障害ドメインが使用されます。**
    記憶域スペースの回復性は、分散型の、ソフトウェアで定義される RAID と概念的に似ています。 すべてのデータの複数コピーは、同期されて保持されます。ハードウェアで障害が発生して、1 つのコピーが失われると、回復性を復元するために、他のコピーが再びコピーされます。 回復性を最適化するには、別個の障害ドメイン内にコピーが保持される必要があります。

- **[ヘルスサービス](health-service-overview.md)は、障害ドメインを使用して、より有用なアラートを提供します。**
    各障害ドメインを場所のメタデータと関連付けることができます。これは後続のアラートに自動的に含まれるようになります。 これらの記述子は、運用や保守の担当者の役に立ちます。これらの記述子でハードウェアを明確にすることにより、エラーを減らすこともできます。

- **ストレッチクラスタリングでは、ストレージアフィニティにフォールトドメインを使用します。** ストレッチ クラスタリングにより、遠隔地のサーバーを一般的なクラスターに参加させることができます。 最高のパフォーマンスのためには、記憶域を提供するサーバーの近くにあるサーバーでアプリケーションまたは仮想マシンを実行する必要があります。 障害ドメインの認識によって、このストレージアフィニティが有効になります。

## <a name="levels-of-fault-domains"></a>障害ドメインのレベル
障害ドメインには、サイト、ラック、シャーシ、ノードという 4 つの標準的なレベルがあります。 ノードは自動的に検出されます。追加の各レベルはオプションです。 たとえば、展開でブレード サーバーを使用しない場合、シャーシ レベルは合理的でない可能性があります。

![さまざまなレベルの障害ドメインの図](media/Fault-Domains-in-Windows-Server-2016/levels-of-fault-domains.png)

## <a name="usage"></a>使用方法
PowerShell または XML マークアップを使用して、障害ドメインを指定できます。 どちらの方法も同等であり、完全な機能が提供されます。

>[!IMPORTANT]
> 障害ドメインを指定してから、可能であれば、記憶域スペース ダイレクトを有効にします。 これにより、シャーシまたはラックのフォールト トレランスのためにプール、階層、および設定 (回復性や列の数など) を準備する自動構成が可能になります。 プールとボリュームが作成された後に、障害ドメイン トポロジの変化に応じてデータが遡及的に移動することはありません。 記憶域スペース ダイレクトを有効にした後に、シャーシ間やラック間でノードを移動するには、`Remove-ClusterNode -CleanUpDisks` を使用して、最初にノードとそのドライブをプールから削除する必要があります。

### <a name="defining-fault-domains-with-powershell"></a>PowerShell を使用した障害ドメインの定義
Windows Server 2016 では、障害ドメインを操作するために次のコマンドレットが導入されています。
* `Get-ClusterFaultDomain`
* `Set-ClusterFaultDomain`
* `New-ClusterFaultDomain`
* `Remove-ClusterFaultDomain`

このショート ビデオでは、これらのコマンドレットの使用法を説明します。
[![このイメージをクリックすると、クラスター障害ドメインコマンドレットの使用に関する短いビデオが見ていきます。](media/Fault-Domains-in-Windows-Server-2016/Part-2-Using-PowerShell.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-2-Using-PowerShell)

`Get-ClusterFaultDomain`現在の障害ドメインのトポロジを表示するには、を使用します。 これにより、クラスター内のすべてのノードと、作成したシャーシ、ラック、またはサイトが一覧表示されます。 **-Type** や **-Name** といったパラメーターを使用して、フィルター処理できます。ただし、これらのパラメーターは必須ではありません。

```PowerShell
Get-ClusterFaultDomain
Get-ClusterFaultDomain -Type Rack
Get-ClusterFaultDomain -Name "server01.contoso.com"
```

を使用して、 `New-ClusterFaultDomain` 新しいシャーシ、ラック、またはサイトを作成します。 `-Type` パラメーターと `-Name` パラメーターは必須です。 に指定できる値 `-Type` は `Chassis` 、、、 `Rack` および `Site` です。 には `-Name` 任意の文字列を指定できます。 ( `Node` タイプフォールトドメインの場合、名前は、自動的に設定される実際のノード名である必要があります)。

```PowerShell
New-ClusterFaultDomain -Type Chassis -Name "Chassis 007"
New-ClusterFaultDomain -Type Rack -Name "Rack A"
New-ClusterFaultDomain -Type Site -Name "Shanghai"
```

> [!IMPORTANT]
> Windows Server では、作成した障害ドメインが実際の物理的な世界にあるものと対応しているかどうかを確認することはできません。 (これは明らかにわかるかもしれませんが、理解しておくことが重要です)。物理的な世界では、ノードがすべて1つのラックにある場合、ソフトウェアで2つの障害ドメインを作成し `-Type Rack` ても、魔法のようにラックのフォールトトレランスを実現することはできません。 上記のコマンドレットを使用して、ハードウェアの実際の配置と一致するトポロジを作成する必要があります。

`Set-ClusterFaultDomain`障害ドメインを別のドメインに移動するには、を使用します。 "親" と "子" という用語は、この入れ子の関係を説明するのに一般的に使用されます。 `-Name` パラメーターと `-Parent` パラメーターは必須です。 で `-Name` 、移動する障害ドメインの名前を指定します。には、 `-Parent` 変換先の名前を指定します。 複数の障害ドメインを一度に移動するには、それらの名前を列記します。

```PowerShell
Set-ClusterFaultDomain -Name "server01.contoso.com" -Parent "Rack A"
Set-ClusterFaultDomain -Name "Rack A", "Rack B", "Rack C", "Rack D" -Parent "Shanghai"
```

> [!IMPORTANT]
> 障害ドメインが移動するときは、その子も一緒に移動します。 上記の例で、Rack A が server01.contoso.com の親である場合、server01.contoso.com は、現実の世界と同様に、親 (Rack A) の移動先 (Shanghai サイト) にすでに存在するため、別途 Shanghai サイトに移動する必要はありません。

の出力では、 `Get-ClusterFaultDomain` 列と列に親子関係が表示さ `ParentName` れ `ChildrenNames` ます。

また、を使用して、 `Set-ClusterFaultDomain` 障害ドメインの特定の他のプロパティを変更することもできます。 たとえば、 `-Location` `-Description` 任意の障害ドメインに対して省略可能なまたはメタデータを指定できます。 この情報を指定すると、ヘルス サービスからのハードウェアのアラートにこの情報が含まれるようになります。 パラメーターを使用して、障害ドメインの名前を変更することもでき `-NewName` ます。 `Node`タイプフォールトドメインの名前を変更しないでください。

```PowerShell
Set-ClusterFaultDomain -Name "Rack A" -Location "Building 34, Room 4010"
Set-ClusterFaultDomain -Type Node -Description "Contoso XYZ Server"
Set-ClusterFaultDomain -Name "Shanghai" -NewName "China Region"
```

`Remove-ClusterFaultDomain`作成したシャーシ、ラック、またはサイトを削除するには、を使用します。 `-Name` パラメーターは必須です。 子を含む障害ドメインを削除することはできません。最初に、子を削除するか、を使用して外部に移動し `Set-ClusterFaultDomain` ます。 障害ドメインを他の障害ドメインの外部に移動するには、を `-Parent` 空の文字列 ("") に設定します。 タイプフォールトドメインを削除することはできません `Node` 。 複数の障害ドメインを一度に削除するには、それらの名前を列記します。

```PowerShell
Set-ClusterFaultDomain -Name "server01.contoso.com" -Parent ""
Remove-ClusterFaultDomain -Name "Rack A"
```

### <a name="defining-fault-domains-with-xml-markup"></a>XML マークアップによる障害ドメインの定義
XML を基にした構文を使用して、障害ドメインを指定できます。 Visual Studio Code (*[こちら](https://code.visualstudio.com/)* から無料で入手できます) やメモ帳など、使い慣れたテキスト エディターを使用して、保存して再利用できる XML ドキュメントを作成することをお勧めします。

このショート ビデオでは、障害ドメインを指定するための XML マークアップの使用法を説明します。

[![この画像をクリックすると、XML を使用して障害ドメインを指定する方法についての短いビデオを見ることができるようになります。](media/Fault-Domains-in-Windows-Server-2016/Part-3-Using-XML-Markup.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-3-Using-XML)

PowerShell で、次のコマンドレットを実行し `Get-ClusterFaultDomainXML` ます。 これにより、クラスターの現在の障害ドメインの詳細が XML として返されます。 これは、検出されたすべての `<Node>` タグを開始タグと終了タグでラップしたもの `<Topology>` です。

次のコマンドレットを実行して、この出力をファイルに保存します。

```PowerShell
Get-ClusterFaultDomainXML | Out-File <Path>
```

ファイルを開き、、、タグを追加して `<Site>` 、 `<Rack>` これらのノードを `<Chassis>` サイト、ラック、シャーシに分散する方法を指定します。 すべてのタグは、一意の **Name** で識別される必要があります。 ノードについては、既定で設定された名前をそのまま保持する必要があります。

> [!IMPORTANT]
> すべての追加タグはオプションですが、推移的な Site &gt; Rack &gt; Chassis &gt; Node の階層に従って、適切に閉じられる必要があります。
名前に加えて、自由形式 `Location="..."` と `Description="..."` 記述子を任意のタグに追加できます。

#### <a name="example-two-sites-one-rack-each"></a>例: 2 つのサイトのそれぞれに 1 つのラック

```XML
<Topology>
  <Site Name="SEA" Location="Contoso HQ, 123 Example St, Room 4010, Seattle">
    <Rack Name="A01" Location="Aisle A, Rack 01">
      <Node Name="Server01" Location="Rack Unit 33" />
      <Node Name="Server02" Location="Rack Unit 35" />
      <Node Name="Server03" Location="Rack Unit 37" />
    </Rack>
  </Site>
  <Site Name="NYC" Location="Regional Datacenter, 456 Example Ave, New York City">
    <Rack Name="B07" Location="Aisle B, Rack 07">
      <Node Name="Server04" Location="Rack Unit 20" />
      <Node Name="Server05" Location="Rack Unit 22" />
      <Node Name="Server06" Location="Rack Unit 24" />
    </Rack>
  </Site>
</Topology>
```

#### <a name="example-two-chassis-blade-servers"></a>例: 2 つのシャーシ、ブレード サーバー
```XML
<Topology>
  <Rack Name="A01" Location="Contoso HQ, Room 4010, Aisle A, Rack 01">
    <Chassis Name="Chassis01" Location="Rack Unit 2 (Upper)" >
      <Node Name="Server01" Location="Left" />
      <Node Name="Server02" Location="Right" />
    </Chassis>
    <Chassis Name="Chassis02" Location="Rack Unit 6 (Lower)" >
      <Node Name="Server03" Location="Left" />
      <Node Name="Server04" Location="Right" />
    </Chassis>
  </Rack>
</Topology>
```

新しい障害ドメインの仕様を設定するには、XML を保存し、PowerShell で次のように実行します。

```PowerShell
$xml = Get-Content <Path> | Out-String
Set-ClusterFaultDomainXML -XML $xml
```

このガイドでは2つの例を紹介していますが、、、 `<Site>` `<Rack>` 、タグは、 `<Chassis>` `<Node>` デプロイの物理的なトポロジを反映するために、さまざまな方法で組み合わせることができます。 上記の例は、これらのタグの柔軟性と、タグを明確にするための自由形式の Location 記述子の価値を説明しています。

### <a name="optional-location-and-description-metadata"></a>省略可能: 場所と説明のメタデータ

任意の障害ドメインに対して、任意の **場所** または **説明** のメタデータを指定できます。 この情報を指定すると、ヘルス サービスからのハードウェアのアラートにこの情報が含まれるようになります。 この短いビデオでは、このような記述子を追加するための値を示します。

[![障害ドメインに位置記述子を追加することの値を示す短いビデオを表示する場合にクリックします](media/Fault-Domains-in-Windows-Server-2016/part-4-location-description.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-4-Location-Description)

## <a name="see-also"></a>関連項目
- [Windows Server 2019 の概要](../get-started-19/get-started-19.md)
- [Windows Server 2016 を使ってみる](../get-started/server-basics.md)
-   [記憶域スペース ダイレクトの概要](../storage/storage-spaces/storage-spaces-direct-overview.md)
