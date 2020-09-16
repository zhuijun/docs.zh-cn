---
title: SAML 令牌提供程序
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 4e371d518d7ef25152aba83fa00d79893397b07f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554418"
---
# <a name="saml-token-provider"></a><span data-ttu-id="81121-102">SAML 令牌提供程序</span><span class="sxs-lookup"><span data-stu-id="81121-102">SAML Token Provider</span></span>
<span data-ttu-id="81121-103">本示例演示如何实现一个自定义客户端 SAML 令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="81121-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="81121-104">Windows Communication Foundation 中的令牌提供程序 (WCF) 用于向安全基础结构提供凭据。</span><span class="sxs-lookup"><span data-stu-id="81121-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="81121-105">令牌提供程序一般检查目标并颁发相应的凭据，以使安全基础结构能够确保消息的安全。</span><span class="sxs-lookup"><span data-stu-id="81121-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="81121-106">WCF 附带了默认的凭据管理器令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="81121-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="81121-107">WCF 还附带了一个 CardSpace 令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="81121-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="81121-108">自定义令牌提供程序在下列情况下有用：</span><span class="sxs-lookup"><span data-stu-id="81121-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="81121-109">存在不能由这些令牌提供程序操作的凭据存储。</span><span class="sxs-lookup"><span data-stu-id="81121-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="81121-110">如果希望提供自己的自定义机制，以便在 WCF 客户端框架使用凭据时，从用户提供详细信息时开始转换凭据。</span><span class="sxs-lookup"><span data-stu-id="81121-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="81121-111">要生成一个自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="81121-111">If you are building a custom token.</span></span>

 <span data-ttu-id="81121-112">此示例演示如何生成一个自定义令牌提供程序，该提供程序允许使用从 WCF 客户端框架之外获取的 SAML 令牌。</span><span class="sxs-lookup"><span data-stu-id="81121-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="81121-113">总之，此示例将演示如下内容：</span><span class="sxs-lookup"><span data-stu-id="81121-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="81121-114">如何使用自定义令牌提供程序对客户端进行配置。</span><span class="sxs-lookup"><span data-stu-id="81121-114">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="81121-115">如何将 SAML 令牌传递给自定义客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="81121-115">How a SAML token can be passed to the custom client credentials.</span></span>

- <span data-ttu-id="81121-116">如何将 SAML 令牌提供给 WCF 客户端框架。</span><span class="sxs-lookup"><span data-stu-id="81121-116">How the SAML token is provided to the WCF client framework.</span></span>

- <span data-ttu-id="81121-117">客户端如何使用服务器的 X.509 证书对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="81121-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="81121-118">服务公开两个终结点，用于与服务进行通信，并使用配置文件 App.config 定义。每个终结点由地址、绑定和协定组成。</span><span class="sxs-lookup"><span data-stu-id="81121-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="81121-119">绑定由使用消息安全的标准 `wsFederationHttpBinding` 进行配置。</span><span class="sxs-lookup"><span data-stu-id="81121-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="81121-120">一个终结点需要客户端用使用对称校验密钥的 SAML 令牌进行身份验证，而另一个终结点需要客户端用使用不对称校验密钥的 SAML 令牌进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="81121-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="81121-121">服务还使用 `serviceCredentials` 行为来配置服务证书。</span><span class="sxs-lookup"><span data-stu-id="81121-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="81121-122">使用 `serviceCredentials` 行为可以配置服务证书。</span><span class="sxs-lookup"><span data-stu-id="81121-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="81121-123">客户端使用服务证书对服务进行身份验证并提供消息保护。</span><span class="sxs-lookup"><span data-stu-id="81121-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="81121-124">以下配置引用了在示例安装过程中安装的“localhost”证书，如本主题最后的安装说明所述。</span><span class="sxs-lookup"><span data-stu-id="81121-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="81121-125">使用 `serviceCredentials` 行为还可以配置受信任的证书以对 SAML 令牌进行签名。</span><span class="sxs-lookup"><span data-stu-id="81121-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="81121-126">下面的配置引用了在示例过程中安装的“Alice”证书。</span><span class="sxs-lookup"><span data-stu-id="81121-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="81121-127">以下步骤演示如何开发自定义 SAML 令牌提供程序并将其与 WCF： security framework 集成：</span><span class="sxs-lookup"><span data-stu-id="81121-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1. <span data-ttu-id="81121-128">编写一个自定义 SAML 令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="81121-128">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="81121-129">示例实现一个自定义 SAML 令牌提供程序，该提供程序根据在构造时提供的 SAML 断言返回一个安全令牌。</span><span class="sxs-lookup"><span data-stu-id="81121-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="81121-130">为了执行此任务，从 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 类派生了自定义令牌提供程序并重写了 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="81121-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="81121-131">此方法创建并返回一个新的 `SecurityToken`。</span><span class="sxs-lookup"><span data-stu-id="81121-131">This method creates and returns a new `SecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. <span data-ttu-id="81121-132">编写自定义安全令牌管理器。</span><span class="sxs-lookup"><span data-stu-id="81121-132">Write custom security token manager.</span></span>

     <span data-ttu-id="81121-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager> 类用于为在 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法中传入的特定 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 创建 `CreateSecurityTokenProvider`。</span><span class="sxs-lookup"><span data-stu-id="81121-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="81121-134">安全令牌管理器还用于创建令牌身份验证器和令牌序列化程序，但它们不包括在本示例中。</span><span class="sxs-lookup"><span data-stu-id="81121-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="81121-135">在本示例中，自定义安全令牌管理器继承自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 类并重写 `CreateSecurityTokenProvider` 方法，以便当传递的令牌需求指示请求 SAML 令牌时返回自定义 SAML 令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="81121-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="81121-136">如果客户端凭据类（请参见步骤 3）未指定一个断言，则安全令牌管理器将创建一个相应的实例。</span><span class="sxs-lookup"><span data-stu-id="81121-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```csharp
    public class SamlSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. <span data-ttu-id="81121-137">编写自定义客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="81121-137">Write a custom client credential.</span></span>

     <span data-ttu-id="81121-138">客户端凭据类用于表示为客户端代理配置的凭据并创建一个安全令牌管理器，该管理器用于获取令牌身份验证器、令牌提供程序和令牌序列化程序。</span><span class="sxs-lookup"><span data-stu-id="81121-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```csharp
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. <span data-ttu-id="81121-139">配置客户端以使用自定义客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="81121-139">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="81121-140">示例删除默认的客户端凭据类，并提供新的客户端凭据类，以便客户端可以使用自定义客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="81121-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```csharp
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 <span data-ttu-id="81121-141">在服务上，将显示与调用方关联的声明。</span><span class="sxs-lookup"><span data-stu-id="81121-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="81121-142">运行示例时，操作请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="81121-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="81121-143">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="81121-143">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="81121-144">设置批处理文件</span><span class="sxs-lookup"><span data-stu-id="81121-144">Setup Batch File</span></span>
 <span data-ttu-id="81121-145">通过运行此示例随附的 Setup.bat 批处理文件，可以用相关的证书将服务器配置为运行需要基于服务器证书的安全性的自承载应用程序。</span><span class="sxs-lookup"><span data-stu-id="81121-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="81121-146">必须修改此批处理文件，以便跨计算机或在非承载情况下工作。</span><span class="sxs-lookup"><span data-stu-id="81121-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="81121-147">下面提供了批处理文件不同节的简要概述，以便可以修改批处理文件从而在相应的配置中运行。</span><span class="sxs-lookup"><span data-stu-id="81121-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="81121-148">创建服务器证书：</span><span class="sxs-lookup"><span data-stu-id="81121-148">Creating the server certificate:</span></span>

     <span data-ttu-id="81121-149">Setup.bat 批处理文件中的以下行创建将要使用的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="81121-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="81121-150">`%SERVER_NAME%`变量指定服务器名称。</span><span class="sxs-lookup"><span data-stu-id="81121-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="81121-151">更改此变量可以指定您自己的服务器名称。</span><span class="sxs-lookup"><span data-stu-id="81121-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="81121-152">此批处理文件中的默认值为 localhost。</span><span class="sxs-lookup"><span data-stu-id="81121-152">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="81121-153">证书存储在 LocalMachine 存储位置下的 My（个人）存储区中。</span><span class="sxs-lookup"><span data-stu-id="81121-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="81121-154">将服务器证书安装到客户端的受信任证书存储区中：</span><span class="sxs-lookup"><span data-stu-id="81121-154">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="81121-155">Setup.bat 批处理文件中的以下行将服务器证书复制到客户端的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="81121-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="81121-156">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="81121-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="81121-157">如果已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用服务器证书填充客户端证书存储区这一步骤。</span><span class="sxs-lookup"><span data-stu-id="81121-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="81121-158">创建颁发者证书。</span><span class="sxs-lookup"><span data-stu-id="81121-158">Creating the issuer certificate.</span></span>

     <span data-ttu-id="81121-159">Setup.bat 批处理文件中的以下行创建将要使用的颁发者证书。</span><span class="sxs-lookup"><span data-stu-id="81121-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="81121-160">`%USER_NAME%` 变量指定颁发者名称。</span><span class="sxs-lookup"><span data-stu-id="81121-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="81121-161">更改此变量可以指定您自己的颁发者名称。</span><span class="sxs-lookup"><span data-stu-id="81121-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="81121-162">此批处理文件中的默认值为 Alice。</span><span class="sxs-lookup"><span data-stu-id="81121-162">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="81121-163">证书存储在 CurrentUser 存储位置下的 My（个人）存储区中。</span><span class="sxs-lookup"><span data-stu-id="81121-163">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="81121-164">将颁发者证书安装到服务器的受信任证书存储区中。</span><span class="sxs-lookup"><span data-stu-id="81121-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="81121-165">Setup.bat 批处理文件中的以下行将服务器证书复制到客户端的受信任的人的存储区中。</span><span class="sxs-lookup"><span data-stu-id="81121-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="81121-166">因为客户端系统不隐式信任 Makecert.exe 生成的证书，所以需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="81121-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="81121-167">如果您已经拥有一个证书，该证书来源于客户端的受信任根证书（例如由 Microsoft 颁发的证书），则不需要执行使用颁发者证书填充服务器证书存储这一步骤。</span><span class="sxs-lookup"><span data-stu-id="81121-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="81121-168">设置和生成示例</span><span class="sxs-lookup"><span data-stu-id="81121-168">To set up and build the sample</span></span>

1. <span data-ttu-id="81121-169">确保已对 [Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="81121-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="81121-170">若要生成解决方案，请按照 [生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="81121-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="81121-171">如果使用 Svcutil.exe 为此示例重新生成配置，请确保在客户端配置中修改终结点名称以与客户端代码匹配。</span><span class="sxs-lookup"><span data-stu-id="81121-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="81121-172">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="81121-172">To run the sample on the same computer</span></span>

1. <span data-ttu-id="81121-173">使用管理员权限运行 Visual Studio 2012 命令提示符下的示例安装文件夹中的 Setup.bat。</span><span class="sxs-lookup"><span data-stu-id="81121-173">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="81121-174">这将安装运行示例所需的所有证书。</span><span class="sxs-lookup"><span data-stu-id="81121-174">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="81121-175">Setup.bat 批处理文件设计为在 Visual Studio 2012 命令提示符下运行。</span><span class="sxs-lookup"><span data-stu-id="81121-175">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="81121-176">在 Visual Studio 2012 命令提示符下设置的 PATH 环境变量指向包含 Setup.bat 脚本所需的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="81121-176">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="81121-177">启动 service\bin 中的 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="81121-177">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="81121-178">启动 \client\bin 中的 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="81121-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="81121-179">客户端活动将显示在客户端控制台应用程序上。</span><span class="sxs-lookup"><span data-stu-id="81121-179">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="81121-180">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="81121-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="81121-181">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="81121-181">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="81121-182">在服务计算机上为服务二进制文件创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="81121-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="81121-183">将服务程序文件复制到服务计算机上的服务目录。</span><span class="sxs-lookup"><span data-stu-id="81121-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="81121-184">另外，将 Setup.bat 和 Cleanup.bat 文件复制到服务计算机上。</span><span class="sxs-lookup"><span data-stu-id="81121-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="81121-185">必须具有一个其主题名称中包含计算机的完全限定域名的服务器证书。</span><span class="sxs-lookup"><span data-stu-id="81121-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="81121-186">必须更新 Service.exe.config 文件以反映此新证书名称。</span><span class="sxs-lookup"><span data-stu-id="81121-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="81121-187">可以通过修改 Setup.bat 批处理文件来创建服务器证书。</span><span class="sxs-lookup"><span data-stu-id="81121-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="81121-188">请注意，setup.bat 文件必须在以管理员特权打开的 Visual Studio 窗口开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="81121-188">Note that the setup.bat file must be run in a Developer Command Prompt for Visual Studio window opened with administrator privileges.</span></span> <span data-ttu-id="81121-189">必须将 `%SERVER_NAME%` 变量设置为用于承载服务的计算机的完全限定的主机名。</span><span class="sxs-lookup"><span data-stu-id="81121-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="81121-190">将服务器证书复制到客户端的 CurrentUser-TrustedPeople 存储中。</span><span class="sxs-lookup"><span data-stu-id="81121-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="81121-191">如果服务器证书是由客户端受信任的颁发者颁发，则不需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="81121-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="81121-192">在服务计算机的 Service.exe.config 文件中，更改基址的值以指定一个完全限定的计算机名称，而不是 localhost。</span><span class="sxs-lookup"><span data-stu-id="81121-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="81121-193">在服务计算机上，在命令提示符下运行 Service.exe。</span><span class="sxs-lookup"><span data-stu-id="81121-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="81121-194">将 \client\bin\ 文件夹（在语言特定文件夹内）中的客户端程序文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="81121-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="81121-195">在客户端计算机上的 Client.exe.config 文件中，更改终结点的地址值，使其与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="81121-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="81121-196">在客户端计算机上，从命令提示窗口中启动 `Client.exe`。</span><span class="sxs-lookup"><span data-stu-id="81121-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="81121-197">如果客户端和服务无法进行通信，请参阅 [WCF 示例的故障排除提示](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="81121-197">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="81121-198">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="81121-198">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="81121-199">运行完示例后运行示例文件夹中的 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="81121-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
