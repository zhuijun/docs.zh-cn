---
title: 持久性已颁发令牌提供程序
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: fed5f44e6cc40cfe2ca963077b6371c14b3b086a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600551"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="c3285-102">持久性已颁发令牌提供程序</span><span class="sxs-lookup"><span data-stu-id="c3285-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="c3285-103">此示例演示如何实现一个自定义客户端已颁发令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="c3285-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c3285-104">讨论区</span><span class="sxs-lookup"><span data-stu-id="c3285-104">Discussion</span></span>  
 <span data-ttu-id="c3285-105">Windows Communication Foundation （WCF）中的令牌提供程序用于向安全基础结构提供凭据。</span><span class="sxs-lookup"><span data-stu-id="c3285-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="c3285-106">令牌提供程序一般检查目标并颁发相应的凭据，以使安全基础结构能够确保消息的安全。</span><span class="sxs-lookup"><span data-stu-id="c3285-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="c3285-107">WCF 附带了一个 CardSpace 令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="c3285-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="c3285-108">自定义令牌提供程序在下列情况下有用：</span><span class="sxs-lookup"><span data-stu-id="c3285-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="c3285-109">存在不能由内置令牌提供程序操作的凭据存储区。</span><span class="sxs-lookup"><span data-stu-id="c3285-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="c3285-110">如果希望提供自己的自定义机制，以便在 WCF 客户端使用凭据时，从用户提供详细信息时开始转换凭据。</span><span class="sxs-lookup"><span data-stu-id="c3285-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="c3285-111">要生成一个自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="c3285-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="c3285-112">此示例演示如何生成一个自定义令牌提供程序，该提供程序可以缓存由安全令牌服务 (STS) 颁发的令牌。</span><span class="sxs-lookup"><span data-stu-id="c3285-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="c3285-113">总之，此示例将演示如下内容：</span><span class="sxs-lookup"><span data-stu-id="c3285-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="c3285-114">如何使用自定义令牌提供程序对客户端进行配置。</span><span class="sxs-lookup"><span data-stu-id="c3285-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="c3285-115">如何缓存颁发的令牌并将其提供给 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="c3285-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="c3285-116">客户端如何使用服务器的 X.509 证书对服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c3285-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="c3285-117">此示例由客户端控制台程序 (Client.exe)、安全令牌服务控制台程序 (Securitytokenservice.exe) 和服务控制台程序 (Service.exe) 组成。</span><span class="sxs-lookup"><span data-stu-id="c3285-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="c3285-118">该服务实现定义“请求-答复”通信模式的协定。</span><span class="sxs-lookup"><span data-stu-id="c3285-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c3285-119">该协定由 `ICalculator` 接口定义，此接口公开数学运算（加、减、乘和除）。</span><span class="sxs-lookup"><span data-stu-id="c3285-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="c3285-120">客户端从安全令牌服务 (STS) 中获取安全令牌，向给定数学运算的服务发出同步请求，服务使用结果进行回复。</span><span class="sxs-lookup"><span data-stu-id="c3285-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="c3285-121">客户端活动显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="c3285-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3285-122">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="c3285-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c3285-123">此示例使用公开 ICalculator 协定 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="c3285-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="c3285-124">下面的代码演示了此绑定在客户端上的配置。</span><span class="sxs-lookup"><span data-stu-id="c3285-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows"
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="c3285-125">在 `security` 的 `wsFederationHttpBinding` 上，`mode` 值配置应该使用的安全模式。</span><span class="sxs-lookup"><span data-stu-id="c3285-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="c3285-126">在此示例中使用了消息安全性，这就是在 `message` 的 `wsFederationHttpBinding` 元素内指定 `security` 的 `wsFederationHttpBinding` 元素的原因。</span><span class="sxs-lookup"><span data-stu-id="c3285-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="c3285-127">`issuer` 的 `wsFederationHttpBinding` 元素（位于 `message` 的 `wsFederationHttpBinding` 元素内）为向客户端颁发安全令牌的安全令牌服务指定地址和绑定，以便客户端能够向计算器服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="c3285-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="c3285-128">下面的代码演示了此绑定在服务上的配置。</span><span class="sxs-lookup"><span data-stu-id="c3285-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType="FindBySubjectDistinguishedName"
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="c3285-129">在 `security` 的 `wsFederationHttpBinding` 上，`mode` 值配置应该使用的安全模式。</span><span class="sxs-lookup"><span data-stu-id="c3285-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="c3285-130">在此示例中使用了消息安全性，这就是在 `message` 的 `wsFederationHttpBinding` 元素内指定 `security` 的 `wsFederationHttpBinding` 元素的原因。</span><span class="sxs-lookup"><span data-stu-id="c3285-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="c3285-131">`issuerMetadata` 的 `wsFederationHttpBinding` 元素（位于 `message` 的 `wsFederationHttpBinding` 元素内）为终结点指定地址和标识，该终结点可用于检索安全令牌服务的元数据。</span><span class="sxs-lookup"><span data-stu-id="c3285-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="c3285-132">下面的代码演示了该服务的行为。</span><span class="sxs-lookup"><span data-stu-id="c3285-132">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine"
              storeName="TrustedPeople"
              x509FindType="FindBySubjectDistinguishedName"
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine"
                        storeName="My"
                        x509FindType="FindBySubjectDistinguishedName"
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 <span data-ttu-id="c3285-133">`issuedTokenAuthentication` 元素内的 `serviceCredentials` 元素允许服务对它在身份验证过程中允许客户端提供的令牌指定约束。</span><span class="sxs-lookup"><span data-stu-id="c3285-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="c3285-134">此配置指定该服务接受由主题名称为 CN=STS 的证书签名的令牌。</span><span class="sxs-lookup"><span data-stu-id="c3285-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="c3285-135">安全令牌服务使用标准 wsHttpBinding 来公开一个终结点。</span><span class="sxs-lookup"><span data-stu-id="c3285-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="c3285-136">安全令牌服务响应客户端对令牌的请求，使用 Windows 帐户提供客户端身份验证，并颁发包含客户端用户名（作为已颁发令牌中的声明）的令牌。</span><span class="sxs-lookup"><span data-stu-id="c3285-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="c3285-137">作为创建令牌的一部分，安全令牌服务使用与 CN=STS 证书关联的私钥对令牌进行签名。</span><span class="sxs-lookup"><span data-stu-id="c3285-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="c3285-138">另外，它还创建对称密钥并使用与 CN=localhost 证书关联的公钥对该密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="c3285-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="c3285-139">在向客户端返回令牌的过程中，安全令牌服务还返回对称密钥。</span><span class="sxs-lookup"><span data-stu-id="c3285-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="c3285-140">客户端向计算器服务出示颁发的令牌，并通过使用该对称密钥对消息进行签名来证明客户端知道该密钥。</span><span class="sxs-lookup"><span data-stu-id="c3285-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="c3285-141">自定义客户端凭据和令牌提供程序</span><span class="sxs-lookup"><span data-stu-id="c3285-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="c3285-142">以下步骤演示如何开发自定义令牌提供程序，以便缓存已颁发的令牌并将其与 WCF： security 集成。</span><span class="sxs-lookup"><span data-stu-id="c3285-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="c3285-143">开发自定义安全令牌提供程序</span><span class="sxs-lookup"><span data-stu-id="c3285-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="c3285-144">编写自定义令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="c3285-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="c3285-145">此示例实现一个自定义令牌提供程序，它返回从缓存中检索的安全令牌。</span><span class="sxs-lookup"><span data-stu-id="c3285-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="c3285-146">为了执行此任务，自定义令牌提供程序派生了 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 类，并重写了 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c3285-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="c3285-147">此方法尝试从缓存中获取令牌，如果在缓存中找不到令牌，则从基础提供程序中检索令牌并缓存该令牌。</span><span class="sxs-lookup"><span data-stu-id="c3285-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="c3285-148">在这两种情况下，该方法都返回 `SecurityToken`。</span><span class="sxs-lookup"><span data-stu-id="c3285-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```csharp  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. <span data-ttu-id="c3285-149">编写自定义安全令牌管理器。</span><span class="sxs-lookup"><span data-stu-id="c3285-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="c3285-150"><xref:System.IdentityModel.Selectors.SecurityTokenManager> 用于为在 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法中传递给它的特定 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 创建 `CreateSecurityTokenProvider`。</span><span class="sxs-lookup"><span data-stu-id="c3285-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="c3285-151">安全令牌管理器还用于创建令牌身份验证器和令牌序列化程序，但本示例不涉及这些内容。</span><span class="sxs-lookup"><span data-stu-id="c3285-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="c3285-152">在此示例中，自定义安全令牌管理器从 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 类集成，并重写 `CreateSecurityTokenProvider` 方法，以便在所传递的令牌需求指示需要一个已颁发的令牌时返回自定义令牌提供程序。</span><span class="sxs-lookup"><span data-stu-id="c3285-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```csharp
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="c3285-153">编写自定义客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="c3285-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="c3285-154">客户端凭据类用于表示为客户端代理配置的凭据并创建一个安全令牌管理器，该管理器用于获取令牌身份验证器、令牌提供程序和令牌序列化程序。</span><span class="sxs-lookup"><span data-stu-id="c3285-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```csharp
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        get  
        {  
          return this.cache;  
        }  
        set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. <span data-ttu-id="c3285-155">实现令牌缓存。</span><span class="sxs-lookup"><span data-stu-id="c3285-155">Implement the token cache.</span></span> <span data-ttu-id="c3285-156">该示例实现使用一个抽象基类，给定令牌缓存的使用方通过该基类与缓存进行交互。</span><span class="sxs-lookup"><span data-stu-id="c3285-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="c3285-157">为了使客户端使用自定义客户端凭据，该示例删除了默认的客户端凭据类，并提供了新的客户端凭据类。</span><span class="sxs-lookup"><span data-stu-id="c3285-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="c3285-158">运行示例</span><span class="sxs-lookup"><span data-stu-id="c3285-158">Running the sample</span></span>  
 <span data-ttu-id="c3285-159">请参见下面的说明来运行该示例。</span><span class="sxs-lookup"><span data-stu-id="c3285-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="c3285-160">运行示例时，对安全令牌的请求显示在安全令牌服务控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="c3285-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="c3285-161">操作请求和响应显示在客户端和服务控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="c3285-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="c3285-162">在任何一个控制台窗口中按 Enter 可以关闭应用程序。</span><span class="sxs-lookup"><span data-stu-id="c3285-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="c3285-163">Setup.cmd 批处理文件</span><span class="sxs-lookup"><span data-stu-id="c3285-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="c3285-164">通过运行此示例随附的 Setup.cmd 批处理文件，可以用相关的证书配置服务器和安全令牌服务以运行自承载的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c3285-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="c3285-165">批处理文件在 CurrentUser/TrustedPeople 证书存储区中创建两个证书。</span><span class="sxs-lookup"><span data-stu-id="c3285-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="c3285-166">第一个证书的主题名称为 CN=STS，并由安全令牌服务用来对颁发给客户端的安全令牌进行签名。</span><span class="sxs-lookup"><span data-stu-id="c3285-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="c3285-167">第二个证书的主题名称为 CN=localhost，并由安全令牌服务用来加密机密，以便服务能够解密该机密。</span><span class="sxs-lookup"><span data-stu-id="c3285-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3285-168">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="c3285-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c3285-169">运行 Setup.cmd 文件以创建所需的证书。</span><span class="sxs-lookup"><span data-stu-id="c3285-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="c3285-170">若要生成解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c3285-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="c3285-171">确保生成解决方案中的所有项目（Shared、RSTRSTR、Service、SecurityTokenService 和 Client）。</span><span class="sxs-lookup"><span data-stu-id="c3285-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="c3285-172">确保 Service.exe 和 SecurityTokenService.exe 都使用管理员权限运行。</span><span class="sxs-lookup"><span data-stu-id="c3285-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="c3285-173">运行 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="c3285-173">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="c3285-174">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="c3285-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="c3285-175">运行完示例后运行示例文件夹中的 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="c3285-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c3285-176">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="c3285-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3285-177">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="c3285-177">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c3285-178">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="c3285-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3285-179">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="c3285-179">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
