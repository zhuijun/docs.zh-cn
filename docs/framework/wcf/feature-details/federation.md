---
title: 联合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: c31c2612b595e627b0c4c2d7fbb3a359b19ee704
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595487"
---
# <a name="federation"></a><span data-ttu-id="7f081-102">联合</span><span class="sxs-lookup"><span data-stu-id="7f081-102">Federation</span></span>
<span data-ttu-id="7f081-103">本主题概要介绍联合安全概念。</span><span class="sxs-lookup"><span data-stu-id="7f081-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="7f081-104">它还介绍了用于部署联合安全体系结构的 Windows Communication Foundation （WCF）支持。</span><span class="sxs-lookup"><span data-stu-id="7f081-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="7f081-105">有关演示联合的示例应用程序，请参阅[联合示例](../samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="7f081-105">For a sample application that demonstrates federation, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="7f081-106">联合安全的定义</span><span class="sxs-lookup"><span data-stu-id="7f081-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="7f081-107">联合安全允许客户端访问的服务与关联的身份验证和授权过程完全分离。</span><span class="sxs-lookup"><span data-stu-id="7f081-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="7f081-108">联合安全还允许跨不同信任领域内的多个系统、网络和组织进行协作。</span><span class="sxs-lookup"><span data-stu-id="7f081-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="7f081-109">WCF 支持构建和部署采用联合安全的分布式系统。</span><span class="sxs-lookup"><span data-stu-id="7f081-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="7f081-110">联合安全体系结构的元素</span><span class="sxs-lookup"><span data-stu-id="7f081-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="7f081-111">联合安全体系结构有三个关键元素，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="7f081-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="7f081-112">元素</span><span class="sxs-lookup"><span data-stu-id="7f081-112">Element</span></span>|<span data-ttu-id="7f081-113">描述</span><span class="sxs-lookup"><span data-stu-id="7f081-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f081-114">域/领域</span><span class="sxs-lookup"><span data-stu-id="7f081-114">Domain/realm</span></span>|<span data-ttu-id="7f081-115">安全管理或信任的单个单位。</span><span class="sxs-lookup"><span data-stu-id="7f081-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="7f081-116">典型的域可能包括单个组织。</span><span class="sxs-lookup"><span data-stu-id="7f081-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="7f081-117">联合</span><span class="sxs-lookup"><span data-stu-id="7f081-117">Federation</span></span>|<span data-ttu-id="7f081-118">已建立信任的域的集合。</span><span class="sxs-lookup"><span data-stu-id="7f081-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="7f081-119">信任级别可能有所不同，但通常包括身份验证，几乎始终包括授权。</span><span class="sxs-lookup"><span data-stu-id="7f081-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="7f081-120">典型的联合可能包括为了对一组资源进行共享访问而建立信任的许多组织。</span><span class="sxs-lookup"><span data-stu-id="7f081-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="7f081-121">安全令牌服务 (STS)</span><span class="sxs-lookup"><span data-stu-id="7f081-121">Security Token Service (STS)</span></span>|<span data-ttu-id="7f081-122">颁发安全令牌的 Web 服务；也就是说，该服务基于它所信任的证据向信任服务的人作出断言。</span><span class="sxs-lookup"><span data-stu-id="7f081-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="7f081-123">这为域之间的信任代理奠定了基础。</span><span class="sxs-lookup"><span data-stu-id="7f081-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="7f081-124">示例方案</span><span class="sxs-lookup"><span data-stu-id="7f081-124">Example Scenario</span></span>  
 <span data-ttu-id="7f081-125">下图显示了联合安全的示例：</span><span class="sxs-lookup"><span data-stu-id="7f081-125">The following illustration shows an example of federated security:</span></span>  
  
 ![显示典型联合安全方案的关系图。](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="7f081-127">此方案包括两个组织：A 和 B。组织 B 拥有组织 A 中某些用户认为有价值的 Web 资源（Web 服务）。</span><span class="sxs-lookup"><span data-stu-id="7f081-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f081-128">本部分使用术语 "*资源*"、"*服务*" 和 " *Web 服务*"。</span><span class="sxs-lookup"><span data-stu-id="7f081-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="7f081-129">通常，组织 B 要求组织 A 中的用户在访问服务之前提供某种有效的身份验证形式。</span><span class="sxs-lookup"><span data-stu-id="7f081-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="7f081-130">另外，该组织还可能要求用户获得授权才能访问所说的特定资源。</span><span class="sxs-lookup"><span data-stu-id="7f081-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="7f081-131">可解决此问题并使组织 A 中的用户能够访问组织 B 中的资源的一种方法如下所述：</span><span class="sxs-lookup"><span data-stu-id="7f081-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="7f081-132">组织 A 中的用户向组织 B 注册他们的凭据（用户名和密码）。</span><span class="sxs-lookup"><span data-stu-id="7f081-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="7f081-133">在访问资源的过程中，组织 A 中的用户在访问资源之前，向组织 B 提供其凭据并进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="7f081-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="7f081-134">此方法有三个明显的缺点：</span><span class="sxs-lookup"><span data-stu-id="7f081-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="7f081-135">组织 B 除了管理其本地用户的凭据外，还必须管理组织 A 中用户的凭据。</span><span class="sxs-lookup"><span data-stu-id="7f081-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="7f081-136">组织 A 中的用户除了保留他们通常用于访问组织 A 中资源的凭据外，还需要保留一组附加凭据（即记住附加用户名和密码）。因此通常鼓励在多个服务站点使用相同的用户名和密码，但这不是一种有效的安全措施。</span><span class="sxs-lookup"><span data-stu-id="7f081-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="7f081-137">随着认为组织 B 的资源有价值的组织越来越多，体系结构不会随之进行调整。</span><span class="sxs-lookup"><span data-stu-id="7f081-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="7f081-138">可以解决上述缺点的另一种替代方法是使用联合安全。</span><span class="sxs-lookup"><span data-stu-id="7f081-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="7f081-139">在此方法中，组织 A 和组织 B 建立一种信任关系并使用安全令牌服务 (STS) 启用所建立信任的代理。</span><span class="sxs-lookup"><span data-stu-id="7f081-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="7f081-140">在联合安全体系结构中，组织 A 中的用户知道，如果他们想访问组织 B 中的 Web 服务，就必须提供组织 B 的 STS 颁发的有效安全令牌，此令牌对用户进行身份验证并授权他们访问特定服务。</span><span class="sxs-lookup"><span data-stu-id="7f081-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="7f081-141">在与 STS B 联系时，用户可通过与 STS 关联的策略获得另一级间接寻址。</span><span class="sxs-lookup"><span data-stu-id="7f081-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="7f081-142">用户必须提供 STS A（即客户端信任领域）颁发的有效安全令牌，STS B 才会向他们颁发安全令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="7f081-143">这是两个组织之间建立的信任关系的必然结果，同时暗示着组织 B 不必管理组织 A 中用户的标识。实际上，STS B 通常具有空的 `issuerAddress` 和 `issuerMetadataAddress`。</span><span class="sxs-lookup"><span data-stu-id="7f081-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="7f081-144">有关详细信息，请参阅[如何：配置本地颁发者](how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="7f081-144">For more information, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="7f081-145">在这种情况下，客户端会咨询本地策略以查找 STS A。此配置称为 "*主领域联合*"，由于 sts B 不必保留有关 STS A 的信息，因此可更好地进行缩放。</span><span class="sxs-lookup"><span data-stu-id="7f081-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="7f081-146">然后，用户可与组织 A 的 STS 联系并通过提供他们通常用于访问组织 A 中任何其他资源的身份验证凭据获取安全令牌。这也会缓解用户必须保留多组凭据或在多个服务站点使用同组凭据的问题。</span><span class="sxs-lookup"><span data-stu-id="7f081-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="7f081-147">用户从 STS A 获取安全令牌后，他们可以将该令牌提供给 STS B。组织 B 将继续对用户的请求执行身份验证并从其自己的安全令牌集中向用户颁发安全令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="7f081-148">之后，用户可以将他们的令牌提供给组织 B 的资源并访问服务。</span><span class="sxs-lookup"><span data-stu-id="7f081-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="7f081-149">WCF 中的联合安全支持</span><span class="sxs-lookup"><span data-stu-id="7f081-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="7f081-150">WCF 为通过部署联合安全体系结构提供全包式支持 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="7f081-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="7f081-151">[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)元素提供安全、可靠且可互操作的绑定，该绑定要求使用 HTTP 作为请求-答复通信样式的基础传输机制，采用文本和 XML 作为传输的传输格式。</span><span class="sxs-lookup"><span data-stu-id="7f081-151">The [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="7f081-152">[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)在联合安全方案中使用可以与两个逻辑上独立的阶段分离，如以下各节中所述。</span><span class="sxs-lookup"><span data-stu-id="7f081-152">The use of [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="7f081-153">阶段 1：设计阶段</span><span class="sxs-lookup"><span data-stu-id="7f081-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="7f081-154">在设计阶段，客户端使用工作身份[数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)来读取服务终结点公开的策略，并收集服务的身份验证和授权要求。</span><span class="sxs-lookup"><span data-stu-id="7f081-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="7f081-155">构造相应代理以在客户端创建以下联合安全通信模式：</span><span class="sxs-lookup"><span data-stu-id="7f081-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="7f081-156">从客户端信任领域中的 STS 获取安全令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="7f081-157">将令牌提供给服务信任领域中的 STS。</span><span class="sxs-lookup"><span data-stu-id="7f081-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="7f081-158">从服务信任领域中的 STS 获取安全令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="7f081-159">向服务提供令牌以访问该服务。</span><span class="sxs-lookup"><span data-stu-id="7f081-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="7f081-160">阶段 2：运行时阶段</span><span class="sxs-lookup"><span data-stu-id="7f081-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="7f081-161">在运行时阶段，客户端实例化 WCF 客户端类的对象并使用 WCF 客户端进行调用。</span><span class="sxs-lookup"><span data-stu-id="7f081-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="7f081-162">WCF 的基础框架在联合安全通信模式中处理前面提到的步骤，并使客户端能够无缝地使用服务。</span><span class="sxs-lookup"><span data-stu-id="7f081-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="7f081-163">使用 WCF 的实现示例</span><span class="sxs-lookup"><span data-stu-id="7f081-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="7f081-164">下图显示了使用 WCF 的本机支持的联合安全体系结构的示例实现。</span><span class="sxs-lookup"><span data-stu-id="7f081-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![显示联合身份验证安全实现示例的关系图。](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="7f081-166">MyService 示例</span><span class="sxs-lookup"><span data-stu-id="7f081-166">Example MyService</span></span>  
 <span data-ttu-id="7f081-167">服务 `MyService` 通过 `MyServiceEndpoint` 公开单个终结点。</span><span class="sxs-lookup"><span data-stu-id="7f081-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="7f081-168">下图显示与该终结点关联的地址、绑定和协定。</span><span class="sxs-lookup"><span data-stu-id="7f081-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![显示 MyServiceEndpoint 详细信息的关系图。](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="7f081-170">服务终结点 `MyServiceEndpoint` 使用 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) 并需要有效的安全断言标记语言（SAML）令牌，其中包含 `accessAuthorized` 由 STS B 颁发的声明。这是以声明方式在服务配置中指定的。</span><span class="sxs-lookup"><span data-stu-id="7f081-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="7f081-171">对于 `MyService` 要求的声明，有一细微点应加以注意。</span><span class="sxs-lookup"><span data-stu-id="7f081-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="7f081-172">第二个图指示 `MyService` 需要具有 `accessAuthorized` 声明的 SAML 令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="7f081-173">更确切地说，这指定了 `MyService` 需要的声明类型。</span><span class="sxs-lookup"><span data-stu-id="7f081-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="7f081-174">此声明类型的完全限定名称是 `http://tempuri.org:accessAuthorized` （连同关联的命名空间），在服务配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="7f081-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="7f081-175">此声明的值指示存在此声明并假定 STS B 将此值设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="7f081-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="7f081-176">在运行时，此策略作为 `MyServiceOperationRequirement` 一部分由 `MyService` 类强制实现。</span><span class="sxs-lookup"><span data-stu-id="7f081-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="7f081-177">STS B</span><span class="sxs-lookup"><span data-stu-id="7f081-177">STS B</span></span>  
 <span data-ttu-id="7f081-178">下图显示 STS B。如前所述，安全令牌服务 (STS) 也是一种 Web 服务，并可具有其自己的关联终结点、策略等。</span><span class="sxs-lookup"><span data-stu-id="7f081-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![显示 security token service B 的关系图。](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="7f081-180">STS B 公开名为 `STSEndpoint` 的单个终结点用于请求安全令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="7f081-181">具体地说，STS B 颁发具有 `accessAuthorized` 声明的 SAML 令牌，此令牌可在 `MyService` 服务站点用于访问服务。</span><span class="sxs-lookup"><span data-stu-id="7f081-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="7f081-182">但是，STS B 要求用户提供由 STS A 颁发的包含 `userAuthenticated` 声明的有效 SAML 令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="7f081-183">这是以声明方式在 STS 配置中指定的。</span><span class="sxs-lookup"><span data-stu-id="7f081-183">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="7f081-184">同样， `userAuthenticated` 声明是 STS B 所需的声明类型。此声明类型的完全限定名称是 `http://tempuri.org:userAuthenticated` （连同关联的命名空间），用于 STS 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="7f081-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="7f081-185">此声明的值指示存在此声明并假定 STS A 将此值设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="7f081-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="7f081-186">在运行时，此策略作为 STS B 的一部分由 `STS_B_OperationRequirement` 类强制实现。</span><span class="sxs-lookup"><span data-stu-id="7f081-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="7f081-187">如果通过访问检查，则 STS B 将颁发具有 `accessAuthorized` 声明的 SAML 令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="7f081-188">STS A</span><span class="sxs-lookup"><span data-stu-id="7f081-188">STS A</span></span>  
 <span data-ttu-id="7f081-189">下图显示 STS A。</span><span class="sxs-lookup"><span data-stu-id="7f081-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="7f081-190">![联合](media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="7f081-190">![Federation](media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="7f081-191">与 STS B 类似，STS A 也是一种 Web 服务，该服务颁发安全令牌并为此目的公开单个终结点。</span><span class="sxs-lookup"><span data-stu-id="7f081-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="7f081-192">但是，它使用不同的绑定（ `wsHttpBinding` ），并要求用户提供具有声明的有效 CardSpace `emailAddress` 。</span><span class="sxs-lookup"><span data-stu-id="7f081-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="7f081-193">作为响应，它会颁发具有 `userAuthenticated` 声明的 SAML 令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="7f081-194">这是以声明方式在服务配置中指定的。</span><span class="sxs-lookup"><span data-stu-id="7f081-194">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"
                       storeName="My" />  
       </identity>  
    </endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="7f081-195">在运行时，此策略作为 STS A 的一部分由 `STS_A_OperationRequirement` 类强制实现。</span><span class="sxs-lookup"><span data-stu-id="7f081-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="7f081-196">如果访问为 `true`，则 STS A 颁发具有 `userAuthenticated` 声明的 SAML 令牌。</span><span class="sxs-lookup"><span data-stu-id="7f081-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="7f081-197">组织 A 的客户端</span><span class="sxs-lookup"><span data-stu-id="7f081-197">Client at Organization A</span></span>  
 <span data-ttu-id="7f081-198">下图显示组织 A 的客户端以及进行 `MyService` 服务调用所涉及的步骤。</span><span class="sxs-lookup"><span data-stu-id="7f081-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="7f081-199">为保持完整性，还包括了其他功能组件。</span><span class="sxs-lookup"><span data-stu-id="7f081-199">The other functional components are also included for completeness.</span></span>  
  
 ![显示 MyService 服务调用中的步骤的关系图。](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="7f081-201">摘要</span><span class="sxs-lookup"><span data-stu-id="7f081-201">Summary</span></span>  
 <span data-ttu-id="7f081-202">联合安全可以清晰划分责任范围并有助于生成安全、可伸缩的服务体系结构。</span><span class="sxs-lookup"><span data-stu-id="7f081-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="7f081-203">作为构建和部署分布式应用程序的平台，WCF 为实现联合安全提供本机支持。</span><span class="sxs-lookup"><span data-stu-id="7f081-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f081-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f081-204">See also</span></span>

- [<span data-ttu-id="7f081-205">安全性</span><span class="sxs-lookup"><span data-stu-id="7f081-205">Security</span></span>](security.md)
