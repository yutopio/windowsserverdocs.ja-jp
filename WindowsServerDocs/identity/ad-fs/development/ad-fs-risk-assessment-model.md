---
title: AD FS 2019 リスク評価モデルでプラグインを構築する
description: 詳細については、「AD FS 2019 のリスク評価モデルを使用したプラグインのビルド」を参照してください。
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 05/05/2020
ms.topic: article
ms.openlocfilehash: 2c1d05450869d558d1991da2f95b72bcaeca7462
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97047820"
---
# <a name="build-plug-ins-with-ad-fs-2019-risk-assessment-model"></a>AD FS 2019 リスク評価モデルでプラグインを構築する

独自のプラグインを構築して、さまざまな段階 (要求の受信、事前認証、事後認証) で、認証要求に対するリスクスコアをブロックまたは割り当てることができるようになりました。 これは、AD FS 2019 で導入された新しいリスク評価モデルを使用して実現できます。

## <a name="what-is-the-risk-assessment-model"></a>リスク評価モデルとは何ですか。

リスク評価モデルは、開発者が認証要求ヘッダーを読み取り、独自のリスク評価ロジックを実装できるようにするためのインターフェイスとクラスのセットです。 実装されたコード (プラグイン) は、AD FS 認証プロセスを使用してラインで実行されます。 たとえば、モデルに含まれているインターフェイスとクラスを使用して、要求ヘッダーに含まれるクライアント IP アドレスに基づいて認証要求をブロックまたは許可するコードを実装できます。 AD FS は、各認証要求のコードを実行し、実装されているロジックに従って適切なアクションを実行します。

このモデルでは、次に示すように、AD FS 認証パイプラインの3つの段階のいずれかでプラグインコードを使用できます。

![対象となるのは、モデル](media/ad-fs-risk-assessment-model/risk1.png)

1.    **要求の受信ステージ** -ユーザーが資格情報を入力する前に、AD FS が認証要求を受信するときに、要求を許可またはブロックするプラグインを作成できるようにします。 この段階で利用可能な要求コンテキスト (クライアント IP、Http メソッド、プロキシサーバー DNS など) を使用して、リスク評価を実行できます。 たとえば、要求コンテキストから IP を読み取るためのプラグインを作成し、その IP が危険な ip の事前定義リストにある場合は認証要求をブロックすることができます。

2.    **事前認証段階** –プラグインを使用して、ユーザーが資格情報を入力した時点で要求を許可またはブロックすることができますが、AD FS によって評価されます。 この段階では、要求コンテキストに加えて、リスク評価ロジックで使用するセキュリティコンテキスト (ユーザートークン、ユーザー id など) とプロトコルコンテキスト (認証プロトコル、clientid、resourceid など) に関する情報も用意されています。 たとえば、ユーザートークンからユーザーのパスワードを読み取り、パスワードが危険なパスワードの事前定義リストにある場合は認証要求をブロックすることで、パスワードスプレー攻撃を防ぐためのプラグインを構築できます。

3.    **認証後** -ユーザーが資格情報を入力し、AD FS によって認証が実行された後に、プラグインを構築してリスクを評価できるようにします。 この段階では、要求コンテキスト、セキュリティコンテキスト、およびプロトコルコンテキストに加え、認証結果 (成功または失敗) に関する情報も表示されます。 このプラグインでは、利用可能な情報に基づいてリスクスコアを評価し、さらに評価するためにリスクスコアを要求およびポリシーの規則に渡すことができます。

リスク評価プラグインを構築して AD FS プロセスで実行する方法について理解を深めるために、危険と特定された特定の **エクストラネット** ip からの要求をブロックするサンプルプラグインを作成し、AD FS にプラグインを登録し、最後に機能をテストします。

>[!NOTE]
>または、リスクの高い [ユーザープラグイン](https://github.com/microsoft/adfs-sample-block-user-on-adfs-marked-risky-by-AzureAD-IdentityProtection)をビルドすることもできます。このプラグインは、認証をブロックしたり、multi-factor AUTHENTICATION (MFA) を適用したりするために Azure AD Identity Protection によって決定されるユーザーリスクレベルを活用するサンプルプラグインです。 危険なユーザープラグインを作成する手順については、こちらを参照して[ください](https://github.com/microsoft/adfs-sample-block-user-on-adfs-marked-risky-by-AzureAD-IdentityProtection)。

## <a name="building-a-sample-plug-in"></a>サンプルプラグインのビルド

>[!NOTE]
>このチュートリアルでは、サンプルプラグインを作成する方法についてのみ説明します。 このソリューションは、エンタープライズ対応のソリューションを作成することを意味します。

### <a name="pre-requisites"></a>前提条件
このサンプルプラグインをビルドするために必要な前提条件の一覧を次に示します。

- AD FS 2019 がインストールおよび構成されている
- 4.7 以降の .NET Framework
- Visual Studio

### <a name="build-plug-in-dll"></a>ビルドプラグイン dll
次の手順では、サンプルプラグイン dll を構築する方法について説明します。

1. サンプルプラグインをダウンロードし、Git Bash を使用して次のように入力します。

   ```
   git clone https://github.com/Microsoft/adfs-sample-RiskAssessmentModel-RiskyIPBlock
   ```

2. AD FS サーバー上の任意の場所に .csv ファイルを作成し **ます** (ここでは、 **authconfigdb.csv** ファイルを **c:\ 拡張機能** に作成し、このファイルにブロックする ip を追加します)。

   このサンプルプラグインは、このファイルに記載されている **エクストラネット ip** からの認証要求をすべてブロックします。

   >{!注: AD FS ファームがある場合は、任意またはすべての AD FS サーバー上にファイルを作成できます。 すべてのファイルを使用して、危険な Ip を AD FS にインポートできます。 インポートプロセスの詳細については、後述の「 [プラグイン dll を AD FS に登録](#register-the-plug-in-dll-with-ad-fs) する」を参照してください。

3. `ThreatDetectionModule.sln`Visual Studio を使用してプロジェクトを開く

4. `Microsoft.IdentityServer.dll`次に示すように、ソリューションエクスプローラーからを削除します。</br>
   ![model](media/ad-fs-risk-assessment-model/risk2.png)

5. `Microsoft.IdentityServer.dll`次に示すように、AD FS のへの参照を追加します。

   a.    **ソリューションエクスプローラー** で [**参照**] を右クリックし、[**参照の追加**] を選択します。</br>
   ![model](media/ad-fs-risk-assessment-model/risk3.png)

   b.    [ **参照マネージャー** ] ウィンドウで、[ **参照**] を選択します。 [ **参照するファイルの選択...]** ダイアログボックスで、 `Microsoft.IdentityServer.dll` AD FS のインストールフォルダー (ここでは **C:\Windows\ADFS**) から選択し、[ **追加**] をクリックします。

   >[!NOTE]
   >ここでは、AD FS サーバー自体にプラグインを構築しています。 開発環境が別のサーバーにある場合は、 `Microsoft.IdentityServer.dll` AD FS サーバーの AD FS インストールフォルダーから開発用のボックスにをコピーします。</br>

   ![対象となるのは、モデル](media/ad-fs-risk-assessment-model/risk4.png)

   c.    チェックボックスをオンにした後、[**参照マネージャー** ] ウィンドウで [ **OK]** をクリックします。 `Microsoft.IdentityServer.dll`</br>
   ![model](media/ad-fs-risk-assessment-model/risk5.png)

6. すべてのクラスと参照が、ビルドを実行するために配置されました。   ただし、このプロジェクトの出力は dll であるため、AD FS サーバーの **グローバルアセンブリキャッシュ**(GAC) にインストールする必要があり、dll を先に署名する必要があります。 そのためには、次の手順に従います。

   a.    プロジェクトの名前 ThreatDetectionModule を **右クリック** します。 メニューの [ **プロパティ**] をクリックします。</br>
   ![model](media/ad-fs-risk-assessment-model/risk6.png)

   b.    [ **プロパティ** ] ページで、左側の [ **署名**] をクリックし、[ **アセンブリの署名**] チェックボックスをオンにします。 [**厳密な名前のキーファイルを選択** してください] プルダウンメニューから、[ **<新規作成... >** ] を選択します。</br>
   ![model](media/ad-fs-risk-assessment-model/risk7.png)

   c.    [ **厳密な名前キーの作成] ダイアログ** ボックスで、キーの名前 (任意の名前を選択できます) を入力し、 **[キーファイルをパスワードで保護** する] チェックボックスをオフにします。 次に、 **[OK]** をクリックします</br>
   ![model](media/ad-fs-risk-assessment-model/risk8.png)

   d.    次のようにプロジェクトを保存します。</br>
   ![model](media/ad-fs-risk-assessment-model/risk9.png)

7. 次に示すように、[ **ビルド** ]、[ **ソリューションのリビルド** ] の順にクリックして、プロジェクトをビルドします。</br>
   ![model](media/ad-fs-risk-assessment-model/risk10.png)

   画面の下部にある [ **出力] ウィンドウ** で、エラーが発生していないかどうかを確認します。</br>
   ![model](media/ad-fs-risk-assessment-model/risk11.png)


これでプラグイン (dll) が使用できるようになりました。プロジェクトフォルダーの **\bin\debug** フォルダー (ここでは **C:\extensions\ThreatDetectionModule\bin\Debug\ThreatDetectionModule.dll**) にあります。

次の手順では、この dll を AD FS に登録して、AD FS 認証プロセスで実行します。

### <a name="register-the-plug-in-dll-with-ad-fs"></a>AD FS にプラグイン dll を登録する

AD FS サーバーで PowerShell コマンドを使用して AD FS に dll を登録する必要があり `Register-AdfsThreatDetectionModule` ます。ただし、登録する前に、公開キートークンを取得する必要があります。 この公開キートークンは、キーを作成し、そのキーを使用して dll に署名したときに作成されたものです。 Dll の公開キートークンの詳細については、次のように **SN.exe** を使用できます。

1. **\Bin\debug** フォルダーから別の場所に dll ファイルをコピーします (ここでは、 **c:\ 拡張子** にコピーします)。

2. Visual Studio の **開発者コマンドプロンプト** を開始し、 **sn.exe** が格納されているディレクトリにアクセスします (ここでは、ディレクトリは **C:\Program files (X86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.7.2 Tools**) モデルです。 ![](media/ad-fs-risk-assessment-model/risk12.png)

3. **-T** パラメーターとファイルの場所 (私のケースでは) を指定して、 **SN** コマンドを実行します `SN -T "C:\extensions\ThreatDetectionModule.dll"` 。 ![](media/ad-fs-risk-assessment-model/risk13.png)</br>
   このコマンドにより、公開キートークンが提供されます ( **公開キートークンは 714697626ef96b35**)

4. AD FS サーバーの **グローバルアセンブリキャッシュ** に dll を追加するベストプラクティスとして、プロジェクトに適したインストーラーを作成し、インストーラーを使用してファイルを GAC に追加することをお勧めします。 もう1つの解決策は、開発用コンピューターで **Gacutil.exe** ([こちら](/dotnet/framework/tools/gacutil-exe-gac-tool)で入手できる **Gacutil.exe** に関する詳細情報) を使用することです。  AD FS と同じサーバーに visual studio をインストールしているため、次のように **Gacutil.exe** を使用します。

   a.    開発者コマンドプロンプト Visual Studio の場合、 **Gacutil.exe** が格納されているディレクトリにアクセスします (ここでは、ディレクトリは **C:\Program files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.7.2 Tools**)

   b.    **Gacutil** コマンド (my case) モデルを実行します `Gacutil /IF C:\extensions\ThreatDetectionModule.dll` 。 ![](media/ad-fs-risk-assessment-model/risk14.png)

   >[!NOTE]
   >AD FS ファームがある場合は、ファーム内の各 AD FS サーバーで上記の手順を実行する必要があります。

5. **Windows PowerShell** を開き、次のコマンドを実行して dll を登録します。
   ```
   Register-AdfsThreatDetectionModule -Name "<Add a name>" -TypeName "<class name that implements interface>, <dll name>, Version=10.0.0.0, Culture=neutral, PublicKeyToken=< Add the Public Key Token from Step 2. above>" -ConfigurationFilePath "<path of the .csv file>"
   ```
   この場合、コマンドは次のようになります。
   ```
   Register-AdfsThreatDetectionModule -Name "IPBlockPlugin" -TypeName "ThreatDetectionModule.UserRiskAnalyzer, ThreatDetectionModule, Version=10.0.0.0, Culture=neutral, PublicKeyToken=714697626ef96b35" -ConfigurationFilePath "C:\extensions\authconfigdb.csv"
   ```

   >[!NOTE]
   >AD FS ファームがある場合でも、dll を登録する必要があるのは1回だけです。

6. Dll の登録後に AD FS サービスを再起動する

これで、dll が AD FS に登録され、使用できるようになりました。

 >[!NOTE]
 > プラグインに変更が加えられ、プロジェクトが再構築された場合は、更新された dll を再度登録する必要があります。 登録する前に、次のコマンドを使用して現在の dll の登録を解除する必要があります。</br></br>
 >`
  UnRegister-AdfsThreatDetectionModule -Name "<name used while registering the dll in 5. above>"
 >`</br></br>
 >この場合、コマンドは次のようになります。
 >```
 >UnRegister-AdfsThreatDetectionModule -Name "IPBlockPlugin"
 >```

### <a name="testing-the-plug-in"></a>プラグインのテスト

1. 前の手順で作成した **authconfig.csv** ファイル (ここでは、" **c:\ 拡張子**") を開き、ブロックする **エクストラネット ip** を追加します。 すべての IP は個別の行に配置する必要があり、末尾にスペースを入れないでください。</br>
   ![model](media/ad-fs-risk-assessment-model/risk18.png)

2. ファイルを保存して閉じます

3. 次の PowerShell コマンドを実行して、更新されたファイルを AD FS にインポートします。

   ```
   Import-AdfsThreatDetectionModuleConfiguration -name "<name given while registering the dll>" -ConfigurationFilePath "<path of the .csv file>"
   ```

   この場合、コマンドは次のようになります。
   ```
   Import-AdfsThreatDetectionModuleConfiguration -name "IPBlockPlugin" -ConfigurationFilePath "C:\extensions\authconfigdb.csv")
   ```

4. **authconfig.csv** で追加したものと同じ IP アドレスを使用して、サーバーから認証要求を開始します。

   このデモでは、要求を開始するために AD FS を使用して、 [X レイ](https://adfshelp.microsoft.com/ClaimsXray/TokenRequest) の要求を使用します。 X レイツールを使用する場合は、次の手順に従ってください。

   フェデレーションサーバーインスタンスを入力し、[ **認証のテスト** ] ボタンをクリックします。</br>
   ![model](media/ad-fs-risk-assessment-model/risk15.png)

5. 次に示すように、認証はブロックされます。</br>
   ![model](media/ad-fs-risk-assessment-model/risk16.png)

これで、プラグインをビルドして登録する方法がわかりました。次は、モデルで導入された新しいインターフェイスとクラスを使用して実装を理解するためのプラグインコードについて説明します。

## <a name="plug-in-code-walkthrough"></a>プラグインコードのチュートリアル

`ThreatDetectionModule.sln`Visual Studio を使用してプロジェクトを開き、画面の右側にある **ソリューションエクスプローラー** からメインファイル **UserRiskAnalyzer.cs** を開きます。</br>
![model](media/ad-fs-risk-assessment-model/risk17.png)

このファイルには、抽象クラス [ThreatDetectionModule](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule) とインターフェイス [IRequestReceivedThreatDetectionModule](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule) を実装する main クラス UserRiskAnalyzer が含まれています。このクラスは、要求コンテキストから ip を読み取り、取得した ip と AD FS DB から読み込まれた ip を比較し、IP 一致がある場合は要求をブロックします。 これらの型についてさらに詳しく説明します。

### <a name="threatdetectionmodule-abstract-class"></a>ThreatDetectionModule 抽象クラス

この抽象クラスは、プラグインを AD FS パイプラインに読み込み、AD FS プロセスを使用してプラグインコードをインラインで実行できるようにします。

```
public abstract class ThreatDetectionModule
{
    protected ThreatDetectionModule();

    public abstract string VendorName { get; }
    public abstract string ModuleIdentifier { get; }

 public abstract void OnAuthenticationPipelineLoad(ThreatDetectionLogger logger, ThreatDetectionModuleConfiguration configData);
 public abstract void OnAuthenticationPipelineUnload(ThreatDetectionLogger logger);
  public abstract void OnConfigurationUpdate(ThreatDetectionLogger logger, ThreatDetectionModuleConfiguration configData);
 }
```
クラスには、次のメソッドとプロパティが含まれています。

|Method |Type|定義|
|-----|-----|-----|
|[OnAuthenticationPipelineLoad](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload) |Void|プラグインがパイプラインに読み込まれるときに AD FS によって呼び出されます|
|[OnAuthenticationPipelineUnload](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineunload) |Void|プラグインがそのパイプラインからアンロードされるときに AD FS によって呼び出されます|
|[OnConfigurationUpdate](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate)| Void|構成の更新時に AD FS によって呼び出されます |
|**Property** |**Type** |**定義**|
|[VendorName](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.vendorname)|String |プラグインを所有しているベンダーの名前を取得します。|
|[ModuleIdentifier](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.moduleidentifier)|String |プラグインの識別子を取得します。|

このサンプルプラグインでは、 [Onauthenticationpipelineload](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload) メソッドと [onconfigurationupdate](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate) メソッドを使用して、AD FS DB から事前に定義された ip を読み取ります。 [Onauthenticationpipelineload](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload) は、プラグインが AD FS に登録されているときに呼び出されます。また、コマンドレットを使用して .csv をインポートするときに [onconfigurationupdate](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate) が呼び出され `Import-AdfsThreatDetectionModuleConfiguration` ます。

#### <a name="irequestreceivedthreatdetectionmodule-interface"></a>IRequestReceivedThreatDetectionModule インターフェイス

この [インターフェイス](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule) を使用すると、AD FS が認証要求を受信する前に、ユーザーが認証プロセスの受信要求ステージで資格情報を入力する前に、リスク評価を実装できます。

```
public interface IRequestReceivedThreatDetectionModule
{
Task<ThrottleStatus> EvaluateRequest (
ThreatDetectionLogger logger,
RequestContext requestContext );
}
```

インターフェイスには、 [EvaluateRequest](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule.evaluaterequest) メソッドが含まれています。これにより、requestContext 入力パラメーターで渡される認証要求のコンテキストを使用して、リスク評価ロジックを記述できます。 RequestContext パラメーターの型は [requestcontext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext)です。

渡されたもう1つの入力パラメーターは、 [ThreatDetectionLogger](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger)型の logger です。 パラメーターを使用すると、エラー、監査、およびデバッグメッセージを AD FS ログに書き込むことができます。

このメソッドは、ThrottleStatus を返します。これは、 [](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.throttlestatus) (注として、1からブロック、および 2) AD FS が返されます。その後、要求をブロックするか許可します。

このサンプルプラグインでは、 [EvaluateRequest](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule.evaluaterequest)メソッドの実装は、 [RequestContext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext)パラメーターから[clientIpAddress](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext.clientipaddresses#Microsoft_IdentityServer_Public_ThreatDetectionFramework_RequestContext_ClientIpAddresses)を解析し、AD FS DB から読み込まれたすべての ip と比較します。 一致が見つかった場合、メソッドは **Block** に2を返します。それ以外の場合は、 **Allow** に1を返します。 返された値に基づいて、AD FS がブロックされるか、または要求が許可されます。

>[!NOTE]
>上記で説明したサンプルプラグインは、IRequestReceivedThreatDetectionModule インターフェイスのみを実装します。 ただし、リスク評価モデルには、IPreAuthenticationThreatDetectionModule (事前認証段階) と IPostAuthenticationThreatDetectionModule (認証後の段階でリスク評価ロジックを実装するため) という2つの追加のインターフェイスが用意されています。 2つのインターフェイスの詳細については、以下を参照してください。

#### <a name="ipreauthenticationthreatdetectionmodule-interface"></a>IPreAuthenticationThreatDetectionModule インターフェイス

この [インターフェイス](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipreauthenticationthreatdetectionmodule) を使用すると、ユーザーが資格情報を入力した時点でリスク評価ロジックを実装することができます。ただし、AD FS は事前認証段階です。

```
public interface IPreAuthenticationThreatDetectionModule
{
Task<ThrottleStatus> EvaluatePreAuthentication (
ThreatDetectionLogger logger,
RequestContext requestContext,
SecurityContext securityContext,
ProtocolContext protocolContext,
IList<Claim> additionalClams
);
}
```
インターフェイスには、 [Evaluatepreauthentication](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipreauthenticationthreatdetectionmodule.evaluatepreauthentication) 認証メソッドが含まれています。これにより、 [requestcontext Requestcontext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext)、 [SecurityContext SecurityContext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext)、 [protocolcontext protocolcontext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext)、および [IList <Claim> additionalclams](/dotnet/api/system.collections.generic.ilist-1?view=netframework-4.7.2) 入力パラメーターで渡された情報を使用して、事前認証のリスク評価ロジックを作成できます。

>[!NOTE]
>各コンテキストの種類で渡されるプロパティの一覧については、「 [RequestContext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext)、 [SecurityContext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext)、および [protocolcontext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext) クラスの定義」を参照してください。

渡されたもう1つの入力パラメーターは、 [ThreatDetectionLogger](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger)型の logger です。 パラメーターを使用すると、エラー、監査、およびデバッグメッセージを AD FS ログに書き込むことができます。

このメソッドは、ThrottleStatus を返します。これは、 [](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.throttlestatus) (注として、1からブロック、および 2) AD FS が返されます。その後、要求をブロックするか許可します。

#### <a name="ipostauthenticationthreatdetectionmodule-interface"></a>IPostAuthenticationThreatDetectionModule インターフェイス

この [インターフェイス](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipostauthenticationthreatdetectionmodule) を使用すると、ユーザーが資格情報を提供し、AD FS が認証後の段階で認証を実行した後に、リスク評価ロジックを実装できます。

```
public interface IPostAuthenticationThreatDetectionModule
{
Task<RiskScore> EvaluatePostAuthentication (
ThreatDetectionLogger logger,
RequestContext requestContext,
SecurityContext securityContext,
ProtocolContext protocolContext,
AuthenticationResult authenticationResult,
IList<Claim> additionalClams
);
}
```

このインターフェイスには、評価後のリスク評価ロジックを記述するために、 [requestContext requestcontext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext)、 [SecurityContext SecurityContext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext)、 [protocolcontext protocolcontext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext)、および[IList <Claim> additionalclams](/dotnet/api/system.collections.generic.ilist-1?view=netframework-4.7.2)入力パラメーターで渡される情報を使用できる[evaluatepostauthentication](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipostauthenticationthreatdetectionmodule.evaluatepostauthentication)メソッドが含まれています。

>[!NOTE]
> 各コンテキスト型で渡されるプロパティの完全な一覧については、「 [RequestContext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext)、 [SecurityContext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext)、および [protocolcontext](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext) クラスの定義」を参照してください。

渡されたもう1つの入力パラメーターは、 [ThreatDetectionLogger](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger)型の logger です。 パラメーターを使用すると、エラー、監査、およびデバッグメッセージを AD FS ログに書き込むことができます。

メソッドは、AD FS ポリシーと要求規則で使用できる [リスクスコア](/dotnet/api/microsoft.identityserver.authentication.riskscoreconstants) を返します。

>[!NOTE]
>プラグインを機能させるには、メインクラス (この場合は UserRiskAnalyzer) が [ThreatDetectionModule](/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule) 抽象クラスを派生する必要があり、上記の3つのインターフェイスのうち少なくとも1つを実装する必要があります。 Dll が登録されると、AD FS 実装されているインターフェイスを確認し、パイプラインの適切なステージでそれらを呼び出します。

### <a name="faqs"></a>FAQ

**これらのプラグインを作成する必要があるのはなぜですか。**</br>
**A:** これらのプラグインは、パスワードスプレー攻撃などの攻撃から環境を保護するための追加機能を提供するだけでなく、お客様の要件に基づいて独自のリスク評価ロジックを構築するための柔軟性も提供します。

**ログはどこでキャプチャされますか。**</br>
**A:** WriteAdminLogErrorMessage メソッドを使用して "AD FS/Admin" イベントログにエラーログを書き込むことができます。また、WriteAuditMessage メソッドを使用して "監査ログ" を "AD FS 監査" し、ログを "AD FS トレース" を使用して、WriteDebugMessage メソッドを使用してデバッグログに記録します。

**これらのプラグインを追加すると、認証プロセスの待機時間 AD FS 増加しますか。**</br>
**A:** 待機時間の影響は、実装するリスク評価ロジックの実行にかかった時間によって決まります。 運用環境にプラグインを展開する前に、待機時間の影響を評価することをお勧めします。

**危険な Ip やユーザーなどの一覧を AD FS 提案できないのはなぜですか。**</br>
**A:** 現在は利用できませんが、プラグ可能なリスク評価モデルでは、危険な Ip やユーザーなどを提案するインテリジェンスの構築に取り組んでいます。 近日中に発表日を共有します。

**その他のサンプルプラグインを利用できますか。**</br>
**A:** 次のサンプルプラグインを利用できます。

|名前|説明|
|-----|-----|
|[危険なユーザープラグイン](https://github.com/microsoft/adfs-sample-block-user-on-adfs-marked-risky-by-AzureAD-IdentityProtection)|Azure AD Identity Protection によって決定されたユーザーリスクレベルに基づいて、認証をブロックするか、MFA を強制するサンプルプラグイン。|
