---
title: WCF 中的安全行为
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 1f15a5aec2f5da89e4069deec946cc20b54f414e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554060"
---
# <a name="security-behaviors-in-wcf"></a><span data-ttu-id="a140e-102">WCF 中的安全行为</span><span class="sxs-lookup"><span data-stu-id="a140e-102">Security Behaviors in WCF</span></span>
<span data-ttu-id="a140e-103">在 Windows Communication Foundation (WCF) ，行为在服务级别或终结点级别修改运行时行为。</span><span class="sxs-lookup"><span data-stu-id="a140e-103">In Windows Communication Foundation (WCF), behaviors modify run-time behavior at the service level or at the endpoint level.</span></span> <span data-ttu-id="a140e-104"> (有关一般行为的详细信息，请参阅 [指定服务运行时行为](../specifying-service-run-time-behavior.md)。 ) *安全行为* 允许对凭据、身份验证、授权和审核日志进行控制。</span><span class="sxs-lookup"><span data-stu-id="a140e-104">(For more information about behaviors in general, see [Specifying Service Run-Time Behavior](../specifying-service-run-time-behavior.md).) *Security behaviors* allow control over credentials, authentication, authorization, and auditing logs.</span></span> <span data-ttu-id="a140e-105">可以通过编程或通过配置来使用行为。</span><span class="sxs-lookup"><span data-stu-id="a140e-105">You can use behaviors either by programming or through configuration.</span></span> <span data-ttu-id="a140e-106">本主题重点讨论如何配置下列与安全功能相关的行为：</span><span class="sxs-lookup"><span data-stu-id="a140e-106">This topic focuses on configuring the following behaviors related to security functions:</span></span>  
  
- <span data-ttu-id="a140e-107">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="a140e-107">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
- <span data-ttu-id="a140e-108">[\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="a140e-108">[\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).</span></span>  
  
- <span data-ttu-id="a140e-109">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).</span><span class="sxs-lookup"><span data-stu-id="a140e-109">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).</span></span>  
  
- <span data-ttu-id="a140e-110">[\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).</span><span class="sxs-lookup"><span data-stu-id="a140e-110">[\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).</span></span>  
  
- <span data-ttu-id="a140e-111">[\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md)，它还使你可以指定客户端可以访问的元数据的安全终结点。</span><span class="sxs-lookup"><span data-stu-id="a140e-111">[\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md), which also enables you to specify a secure endpoint that clients can access for metadata.</span></span>  
  
## <a name="setting-credentials-with-behaviors"></a><span data-ttu-id="a140e-112">用行为设置凭据</span><span class="sxs-lookup"><span data-stu-id="a140e-112">Setting Credentials with Behaviors</span></span>  
 <span data-ttu-id="a140e-113">使用 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 和 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) 设置服务或客户端的凭据值。</span><span class="sxs-lookup"><span data-stu-id="a140e-113">Use the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) and [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) to set credential values for a service or client.</span></span> <span data-ttu-id="a140e-114">基础绑定配置决定是否必须设置凭据。</span><span class="sxs-lookup"><span data-stu-id="a140e-114">The underlying binding configuration determines whether a credential has to be set.</span></span> <span data-ttu-id="a140e-115">例如，如果安全模式设置为 `None`，则客户端和服务不会相互进行身份验证，并且不需要任何类型的凭据。</span><span class="sxs-lookup"><span data-stu-id="a140e-115">For example, if the security mode is set to `None`, both clients and services do not authenticate each other and require no credentials of any type.</span></span>  
  
 <span data-ttu-id="a140e-116">另一方面，服务绑定可能要求使用客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="a140e-116">On the other hand, the service binding can require a client credential type.</span></span> <span data-ttu-id="a140e-117">在此情况下，您可能必须使用行为来设置凭据值。</span><span class="sxs-lookup"><span data-stu-id="a140e-117">In that case, you may have to set a credential value using a behavior.</span></span> <span data-ttu-id="a140e-118"> (有关可能的凭据类型的详细信息，请参阅 [选择凭据类型](selecting-a-credential-type.md)。 ) 在某些情况下（例如，使用 Windows 凭据进行身份验证时），环境会自动确定实际凭据值，而无需显式设置凭据值 (，除非你想要指定一组不同的) 凭据。</span><span class="sxs-lookup"><span data-stu-id="a140e-118">(For more information about the possible types of credentials, see [Selecting a Credential Type](selecting-a-credential-type.md).) In some cases, such as when Windows credentials are used to authenticate, the environment automatically establishes the actual credential value and you do not need to explicitly set the credential value (unless you want to specify a different set of credentials).</span></span>  
  
 <span data-ttu-id="a140e-119">所有服务凭据都作为的子元素找到 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="a140e-119">All service credentials are found as child elements of the [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md).</span></span> <span data-ttu-id="a140e-120">下面的示例演示一个用作服务凭据的证书。</span><span class="sxs-lookup"><span data-stu-id="a140e-120">The following example shows a certificate used as a service credential.</span></span>  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a><span data-ttu-id="a140e-121">服务凭据</span><span class="sxs-lookup"><span data-stu-id="a140e-121">Service Credentials</span></span>  
 <span data-ttu-id="a140e-122">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md)包含四个子元素。</span><span class="sxs-lookup"><span data-stu-id="a140e-122">The [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) contains four child elements.</span></span> <span data-ttu-id="a140e-123">以下几节将讨论这些元素和它们的用法。</span><span class="sxs-lookup"><span data-stu-id="a140e-123">The elements and their usages are discussed in the following sections.</span></span>  
  
### <a name="servicecertificate-element"></a><span data-ttu-id="a140e-124">\<serviceCertificate> 元素</span><span class="sxs-lookup"><span data-stu-id="a140e-124">\<serviceCertificate> Element</span></span>  
 <span data-ttu-id="a140e-125">使用此元素可指定一个 X.509 证书，以供服务用来向使用消息安全模式的客户端证明自己的身份。</span><span class="sxs-lookup"><span data-stu-id="a140e-125">Use this element to specify an X.509 certificate that is used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="a140e-126">如果您使用的是定期续订的证书，则证书的指纹将会变更。</span><span class="sxs-lookup"><span data-stu-id="a140e-126">If you are using a certificate that is periodically renewed, then its thumbprint changes.</span></span> <span data-ttu-id="a140e-127">在此情况下，请使用主题名称作为 `X509FindType`，因为可以使用同一主题名称来重新颁发该证书。</span><span class="sxs-lookup"><span data-stu-id="a140e-127">In that case, use the subject name as the `X509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 <span data-ttu-id="a140e-128">有关使用元素的详细信息，请参阅 [如何：指定客户端凭据值](../how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-128">For more information about using the element, see [How to: Specify Client Credential Values](../how-to-specify-client-credential-values.md).</span></span>  
  
### <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="a140e-129">\<certificate> of \<clientCertificate> 元素</span><span class="sxs-lookup"><span data-stu-id="a140e-129">\<certificate> of \<clientCertificate> Element</span></span>  
 <span data-ttu-id="a140e-130">[\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)如果服务必须事先拥有客户端的证书，以便与客户端进行安全通信，请使用元素。</span><span class="sxs-lookup"><span data-stu-id="a140e-130">Use the [\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) element when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="a140e-131">使用双工通信模式时，会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="a140e-131">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="a140e-132">在更为典型的请求-答复模式中，客户端会将它的证书包含在请求中，服务会使用该证书来确保它的响应安全返回客户端。</span><span class="sxs-lookup"><span data-stu-id="a140e-132">In the more typical request-reply pattern, the client includes its certificate in the request, which the service uses to secure its response back to the client.</span></span> <span data-ttu-id="a140e-133">但是，双工通信模式没有请求和答复。</span><span class="sxs-lookup"><span data-stu-id="a140e-133">The duplex communication pattern, however, has no requests and replies.</span></span> <span data-ttu-id="a140e-134">服务无法从通信中推断出客户端的证书，因此服务需要事先得到客户端的证书来保护发送到客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="a140e-134">The service cannot infer the client's certificate from the communication and therefore the service requires the client's certificate in advance to secure the messages to the client.</span></span> <span data-ttu-id="a140e-135">您必须通过带外方式来获取客户端的证书，并使用此元素指定该证书。</span><span class="sxs-lookup"><span data-stu-id="a140e-135">You must obtain the client's certificate in an out-of-band manner and specify the certificate using this element.</span></span> <span data-ttu-id="a140e-136">有关双工服务的详细信息，请参阅 [如何：创建双工协定](how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-136">For more information about duplex services, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
### <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="a140e-137">\<authentication> of \<clientCertificate> 元素</span><span class="sxs-lookup"><span data-stu-id="a140e-137">\<authentication> of \<clientCertificate> Element</span></span>  
 <span data-ttu-id="a140e-138">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)元素使你可以自定义如何对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="a140e-138">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) element enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="a140e-139">可以将 `CertificateValidationMode` 属性设置为 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="a140e-139">You can set the `CertificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="a140e-140">默认情况下，该级别设置为 `ChainTrust` ，它指定每个证书都必须位于证书层次结构中，以在链顶部以 *根证书颁发机构* 结束。</span><span class="sxs-lookup"><span data-stu-id="a140e-140">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="a140e-141">这是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="a140e-141">This is the most secure mode.</span></span> <span data-ttu-id="a140e-142">您还可以将此值设置为 `PeerOrChainTrust`，该值指定受信任的链中的证书以及自行颁发的证书（对等信任）都被接受。</span><span class="sxs-lookup"><span data-stu-id="a140e-142">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="a140e-143">因为不需要从受信任的证书颁发机构那里购买自行颁发的证书，所以可以在开发和调试客户端和服务时使用此值。</span><span class="sxs-lookup"><span data-stu-id="a140e-143">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="a140e-144">在部署客户端时，请改用 `ChainTrust` 值。</span><span class="sxs-lookup"><span data-stu-id="a140e-144">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="a140e-145">还可以将该值设置为 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="a140e-145">You can also set the value to `Custom`.</span></span> <span data-ttu-id="a140e-146">当该值设置为 `Custom` 值时，您还必须将 `CustomCertificateValidatorType` 属性设置为用于验证证书的程序集和类型。</span><span class="sxs-lookup"><span data-stu-id="a140e-146">When set to the `Custom` value, you must also set the `CustomCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="a140e-147">若要创建您自己的自定义验证程序，必须从 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 抽象类进行继承。</span><span class="sxs-lookup"><span data-stu-id="a140e-147">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
### <a name="issuedtokenauthentication-element"></a><span data-ttu-id="a140e-148">\<issuedTokenAuthentication> 元素</span><span class="sxs-lookup"><span data-stu-id="a140e-148">\<issuedTokenAuthentication> Element</span></span>  
 <span data-ttu-id="a140e-149">颁发的令牌方案包含三个阶段。</span><span class="sxs-lookup"><span data-stu-id="a140e-149">The issued token scenario has three stages.</span></span> <span data-ttu-id="a140e-150">在第一阶段中，尝试访问服务的客户端被称为 (STS) 的 *安全令牌服务* 。</span><span class="sxs-lookup"><span data-stu-id="a140e-150">In the first stage, a client trying to access a service is referred to a *secure token service* (STS).</span></span> <span data-ttu-id="a140e-151">然后，STS 对该客户端进行身份验证，随后向该客户端颁发一个令牌（通常是一个安全断言标记语言 (SAML) 令牌）。</span><span class="sxs-lookup"><span data-stu-id="a140e-151">The STS then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="a140e-152">接下来，客户端携带此令牌返回服务。</span><span class="sxs-lookup"><span data-stu-id="a140e-152">The client then returns to the service with the token.</span></span> <span data-ttu-id="a140e-153">服务检查该令牌，以获取使其可以对该令牌并进而对该客户端进行身份验证的数据。</span><span class="sxs-lookup"><span data-stu-id="a140e-153">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="a140e-154">若要对令牌进行身份验证，安全令牌服务所使用的证书必须为该服务所知。</span><span class="sxs-lookup"><span data-stu-id="a140e-154">To authenticate the token, the certificate that the secure token service uses must be known to the service.</span></span> <span data-ttu-id="a140e-155">[\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)元素是任何此类安全令牌服务证书的储存库。</span><span class="sxs-lookup"><span data-stu-id="a140e-155">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="a140e-156">若要添加证书，请使用 [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="a140e-156">To add certificates, use the [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="a140e-157">为 [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) 每个证书插入一个，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="a140e-157">Insert an [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="a140e-158">默认情况下，必须从安全令牌服务那里获取证书。</span><span class="sxs-lookup"><span data-stu-id="a140e-158">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="a140e-159">这些“已知的”证书可以确保只有合法的客户端才能访问服务。</span><span class="sxs-lookup"><span data-stu-id="a140e-159">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="a140e-160">应 [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) 在使用 *安全令牌服务* (STS) 颁发安全令牌的联合应用程序中使用该集合 `SamlSecurityToken` 。</span><span class="sxs-lookup"><span data-stu-id="a140e-160">You should use the [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) collection in a federated application that utilizes a *secure token service* (STS) that issues `SamlSecurityToken` security tokens.</span></span> <span data-ttu-id="a140e-161">当 STS 颁发安全令牌时，它可以通过将 `SamlAudienceRestrictionCondition` 添加到安全令牌中，来指定安全令牌的目标 Web 服务的 URI。</span><span class="sxs-lookup"><span data-stu-id="a140e-161">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a `SamlAudienceRestrictionCondition` to the security token.</span></span> <span data-ttu-id="a140e-162">这样，通过指定应采用以下方式执行此检查，接收方 Web 服务的 `SamlSecurityTokenAuthenticator` 将能够验证颁发的安全令牌是否针对此 Web 服务：</span><span class="sxs-lookup"><span data-stu-id="a140e-162">That allows the `SamlSecurityTokenAuthenticator` for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="a140e-163">将 `audienceUriMode` 的属性设置 [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 为 `Always` 或 `BearerKeyOnly` 。</span><span class="sxs-lookup"><span data-stu-id="a140e-163">Set the `audienceUriMode` attribute of [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) to `Always` or `BearerKeyOnly`.</span></span>  
  
- <span data-ttu-id="a140e-164">将有效 URI 添加到此集合，以指定有效 URI 集。</span><span class="sxs-lookup"><span data-stu-id="a140e-164">Specify the set of valid URIs, by adding the URIs to this collection.</span></span> <span data-ttu-id="a140e-165">为此，请 [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) 为每个 URI 插入一个</span><span class="sxs-lookup"><span data-stu-id="a140e-165">To do this, insert an [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) for each URI</span></span>  
  
 <span data-ttu-id="a140e-166">有关详细信息，请参阅 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="a140e-166">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="a140e-167">有关使用此配置元素的详细信息，请参阅 [如何：在联合身份验证服务上配置凭据](how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-167">For more information about using this configuration element, see [How to: Configure Credentials on a Federation Service](how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
#### <a name="allowing-anonymous-cardspace-users"></a><span data-ttu-id="a140e-168">允许匿名 CardSpace 用户</span><span class="sxs-lookup"><span data-stu-id="a140e-168">Allowing Anonymous CardSpace Users</span></span>  
 <span data-ttu-id="a140e-169">将 `AllowUntrustedRsaIssuers` 元素的 `<IssuedTokenAuthentication>` 属性设置为 `true`，可以显式允许任何客户端提供已用任意 RSA 密钥对签名的自行颁发的令牌。</span><span class="sxs-lookup"><span data-stu-id="a140e-169">Setting the `AllowUntrustedRsaIssuers` attribute of the `<IssuedTokenAuthentication>` element to `true` explicitly allows any client to present a self-issued token signed with an arbitrary RSA key pair.</span></span> <span data-ttu-id="a140e-170">此颁发者不 *受信任* ，因为该密钥没有关联的颁发者数据。</span><span class="sxs-lookup"><span data-stu-id="a140e-170">The issuer is *untrusted* because the key has no issuer data associated with it.</span></span> <span data-ttu-id="a140e-171">CardSpace 用户可以创建一个自行颁发的卡，其中包含自行提供的标识声明。</span><span class="sxs-lookup"><span data-stu-id="a140e-171">A CardSpace user can create a self-issued card that includes self-provided claims of identity.</span></span> <span data-ttu-id="a140e-172">使用此功能时一定要小心。</span><span class="sxs-lookup"><span data-stu-id="a140e-172">Use this capability with caution.</span></span> <span data-ttu-id="a140e-173">若要使用此功能，请将 RSA 公钥视为更加安全的密码，应将其与用户名一起存储在数据库中。</span><span class="sxs-lookup"><span data-stu-id="a140e-173">To use this feature, think of the RSA public key as a more secure password that should be stored in a database along with a user name.</span></span> <span data-ttu-id="a140e-174">在允许客户端访问服务之前，请将客户端提供的 RSA 公钥与所提供的用户名的已存储公钥进行比较，以便对该公钥进行验证。</span><span class="sxs-lookup"><span data-stu-id="a140e-174">Before allowing a client access to the service, verify the client-presented RSA public key by comparing it with the stored public key for the presented user name.</span></span> <span data-ttu-id="a140e-175">这里假设您已建立了注册过程，用户可以通过此过程来注册他们的用户名并将其用户名与自行颁发的 RSA 公钥相关联。</span><span class="sxs-lookup"><span data-stu-id="a140e-175">This presumes that you have established a registration process whereby users can register their user names and associate them with the self-issued RSA public keys.</span></span>  
  
## <a name="client-credentials"></a><span data-ttu-id="a140e-176">客户端凭据</span><span class="sxs-lookup"><span data-stu-id="a140e-176">Client Credentials</span></span>  
 <span data-ttu-id="a140e-177">在要求相互进行身份验证的情况下，需要使用客户端凭据使客户端通过服务的身份验证。</span><span class="sxs-lookup"><span data-stu-id="a140e-177">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="a140e-178">当客户端必须使用服务的证书来保护发送到服务的消息时，可以使用该节来指定服务证书。</span><span class="sxs-lookup"><span data-stu-id="a140e-178">You can use the section to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
 <span data-ttu-id="a140e-179">您还可以将客户端配置为联合方案的一部分，以便使用来自安全令牌服务或本地令牌颁发机构颁发的令牌。</span><span class="sxs-lookup"><span data-stu-id="a140e-179">You can also configure a client as part of a federation scenario to use issued tokens from a secure token service or a local issuer of tokens.</span></span> <span data-ttu-id="a140e-180">有关联合方案的详细信息，请参阅 [联合和颁发的令牌](federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-180">For more information about federated scenarios, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span> <span data-ttu-id="a140e-181">所有客户端凭据都位于下 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) ，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="a140e-181">All client credentials are found under the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md), as shown in the following code.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
#### <a name="clientcertificate-element"></a><span data-ttu-id="a140e-182">\<clientCertificate> 元素</span><span class="sxs-lookup"><span data-stu-id="a140e-182">\<clientCertificate> Element</span></span>  
 <span data-ttu-id="a140e-183">可以使用此元素设置用于对客户端进行身份验证的证书。</span><span class="sxs-lookup"><span data-stu-id="a140e-183">Set the certificate used to authenticate the client with this element.</span></span> <span data-ttu-id="a140e-184">有关详细信息，请参阅 [如何：指定客户端凭据值](../how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-184">For more information, see [How to: Specify Client Credential Values](../how-to-specify-client-credential-values.md).</span></span>  
  
#### \<httpDigest>  
 <span data-ttu-id="a140e-185">必须使用 Windows 上的 Active Directory 和 Internet 信息服务 (IIS) 启用此功能。</span><span class="sxs-lookup"><span data-stu-id="a140e-185">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="a140e-186">有关详细信息，请参阅 [IIS 6.0 中的摘要式身份验证](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="a140e-186">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
#### <a name="issuedtoken-element"></a><span data-ttu-id="a140e-187">\<issuedToken> 元素</span><span class="sxs-lookup"><span data-stu-id="a140e-187">\<issuedToken> Element</span></span>  
 <span data-ttu-id="a140e-188">[\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md)包含用于配置令牌的本地颁发者的元素，或用于 security token service 的行为。</span><span class="sxs-lookup"><span data-stu-id="a140e-188">The [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="a140e-189">有关将客户端配置为使用本地颁发者的说明，请参阅 [如何：配置本地颁发者](how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-189">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span>  
  
#### \<localIssuerAddress>  
 <span data-ttu-id="a140e-190">指定默认的安全令牌服务地址。</span><span class="sxs-lookup"><span data-stu-id="a140e-190">Specifies a default security token service address.</span></span> <span data-ttu-id="a140e-191">当没有 <xref:System.ServiceModel.WSFederationHttpBinding> 为 security token service 提供 URL 时，或者当联合绑定的颁发者地址为或时，将使用此功能 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` 。</span><span class="sxs-lookup"><span data-stu-id="a140e-191">This is used when the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="a140e-192">在这些情况下，必须使用本地颁发机构的地址和用来与该颁发机构进行通信的绑定来配置 <xref:System.ServiceModel.Description.ClientCredentials>。</span><span class="sxs-lookup"><span data-stu-id="a140e-192">In such cases, the <xref:System.ServiceModel.Description.ClientCredentials> must be configured with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
#### \<issuerChannelBehaviors>  
 <span data-ttu-id="a140e-193">使用 [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) 可添加与 security token service 通信时使用的 WCF 客户端行为。</span><span class="sxs-lookup"><span data-stu-id="a140e-193">Use the [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) to add WCF client behaviors used when communicating with a security token service.</span></span> <span data-ttu-id="a140e-194">在部分中定义客户端行为 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="a140e-194">Define client behaviors in the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) section.</span></span> <span data-ttu-id="a140e-195">若要使用已定义的行为，请将 <`add`> 元素添加到 `<issuerChannelBehaviors>` 具有两个属性的元素中。</span><span class="sxs-lookup"><span data-stu-id="a140e-195">To use a defined behavior, add an <`add`> element to the `<issuerChannelBehaviors>` element with two attributes.</span></span> <span data-ttu-id="a140e-196">将 `issuerAddress` 设置为安全令牌服务的 URL，将 `behaviorConfiguration` 特性设置为已定义终结点行为的名称，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a140e-196">Set the `issuerAddress` to the URL of the security token service and set the `behaviorConfiguration` attribute to the name of the defined endpoint behavior, as shown in the following example.</span></span>  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
      </issuerChannelBehaviors>  
   </issuedToken>  
</clientCredentials>
```  
  
#### <a name="servicecertificate-element"></a><span data-ttu-id="a140e-197">\<serviceCertificate> 元素</span><span class="sxs-lookup"><span data-stu-id="a140e-197">\<serviceCertificate> Element</span></span>  
 <span data-ttu-id="a140e-198">使用此元素可控制服务证书的身份验证。</span><span class="sxs-lookup"><span data-stu-id="a140e-198">Use this element to control authentication of service certificates.</span></span>  
  
 <span data-ttu-id="a140e-199">[\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md)元素可以存储在服务未指定证书时使用的单个证书。</span><span class="sxs-lookup"><span data-stu-id="a140e-199">The [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) element can store a single certificate used when the service specifies no certificate.</span></span>  
  
 <span data-ttu-id="a140e-200">使用 [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) 和 [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) 设置与特定服务关联的服务证书。</span><span class="sxs-lookup"><span data-stu-id="a140e-200">Use the [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) and [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) to set service certificates that are associated with specific services.</span></span> <span data-ttu-id="a140e-201">`<add>` 元素包含一个 `targetUri` 属性，该属性用于将证书与服务相关联。</span><span class="sxs-lookup"><span data-stu-id="a140e-201">The `<add>` element includes a `targetUri` attribute that is used to associate the certificate with the service.</span></span>  
  
 <span data-ttu-id="a140e-202">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)元素指定用于对证书进行身份验证的信任级别。</span><span class="sxs-lookup"><span data-stu-id="a140e-202">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="a140e-203">默认情况下，该级别设置为“ChainTrust”，它指定每个证书都必须存在于某个证书层次结构中，而该层次结构以位于证书链顶端的受信任的证书颁发机构结束。</span><span class="sxs-lookup"><span data-stu-id="a140e-203">By default, the level is set to "ChainTrust," which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="a140e-204">这是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="a140e-204">This is the most secure mode.</span></span> <span data-ttu-id="a140e-205">还可以将此值设置为“PeerOrChainTrust”，该值指定受信任的链中的证书以及自行颁发的证书（对等信任）都被接受。</span><span class="sxs-lookup"><span data-stu-id="a140e-205">You can also set the value to "PeerOrChainTrust", which specifies that self-issued certificates (peer trust) are accepted, as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="a140e-206">因为不需要从受信任的证书颁发机构那里购买自行颁发的证书，所以可以在开发和调试客户端和服务时使用此值。</span><span class="sxs-lookup"><span data-stu-id="a140e-206">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="a140e-207">在部署客户端时，请改用“ChainTrust”值。</span><span class="sxs-lookup"><span data-stu-id="a140e-207">When deploying a client, use the "ChainTrust" value instead.</span></span> <span data-ttu-id="a140e-208">还可以将此值设置为“Custom”或“None”。</span><span class="sxs-lookup"><span data-stu-id="a140e-208">You can also set the value to "Custom" or "None."</span></span> <span data-ttu-id="a140e-209">若要使用“Custom”值，您还必须将 `CustomCertificateValidatorType` 属性设置为用于验证证书的程序集和类型。</span><span class="sxs-lookup"><span data-stu-id="a140e-209">To use the "Custom" value, you must also set the `CustomCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="a140e-210">若要创建您自己的自定义验证程序，必须从 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 抽象类进行继承。</span><span class="sxs-lookup"><span data-stu-id="a140e-210">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="a140e-211">有关详细信息，请参阅 [如何：创建使用自定义证书验证程序的服务](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-211">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="a140e-212">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)元素包含一个 `RevocationMode` 属性，该属性指定如何检查证书的吊销状态。</span><span class="sxs-lookup"><span data-stu-id="a140e-212">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element includes a `RevocationMode` attribute that specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="a140e-213">默认值为“online”，指示自动检查证书是否已吊销。</span><span class="sxs-lookup"><span data-stu-id="a140e-213">The default is "online", which indicates that certificates are automatically checked for revocation.</span></span> <span data-ttu-id="a140e-214">有关详细信息，请参阅使用 [证书](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-214">For more information, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
## <a name="serviceauthorization"></a><span data-ttu-id="a140e-215">ServiceAuthorization</span><span class="sxs-lookup"><span data-stu-id="a140e-215">ServiceAuthorization</span></span>  
 <span data-ttu-id="a140e-216">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)元素包含影响授权、自定义角色提供程序和模拟的元素。</span><span class="sxs-lookup"><span data-stu-id="a140e-216">The [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) element contains elements that affect authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="a140e-217"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 类被应用于服务方法。</span><span class="sxs-lookup"><span data-stu-id="a140e-217">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> class is applied to a service method.</span></span> <span data-ttu-id="a140e-218">该属性指定在授权使用受保护方法时要使用的用户组。</span><span class="sxs-lookup"><span data-stu-id="a140e-218">The attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="a140e-219">默认值为“UseWindowsGroups”，该值指定在 Windows 组（例如，“Administrators”或“Users”）中搜索试图访问某个资源的标识。</span><span class="sxs-lookup"><span data-stu-id="a140e-219">The default value is "UseWindowsGroups" and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="a140e-220">你还可以指定 "UseAspNetRoles" 以使用在 <> 元素下配置的自定义角色提供程序 `system.web` ，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="a140e-220">You can also specify "UseAspNetRoles" to use a custom role provider that is configured under the <`system.web` > element, as shown in the following code.</span></span>  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add
          name="SqlProvider"
          type="System.Web.Security.SqlMembershipProvider"
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 <span data-ttu-id="a140e-221">下面的代码演示与 `roleProviderName` 特性一起使用的 `principalPermissionMode`。</span><span class="sxs-lookup"><span data-stu-id="a140e-221">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a><span data-ttu-id="a140e-222">配置安全审核</span><span class="sxs-lookup"><span data-stu-id="a140e-222">Configuring Security Audits</span></span>  
 <span data-ttu-id="a140e-223">使用 [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) 指定要写入的日志以及要记录的事件类型。</span><span class="sxs-lookup"><span data-stu-id="a140e-223">Use the [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) to specify the log written to, and what types of events to log.</span></span> <span data-ttu-id="a140e-224">有关详细信息，请参阅 [审核](auditing-security-events.md)。</span><span class="sxs-lookup"><span data-stu-id="a140e-224">For more information, see [Auditing](auditing-security-events.md).</span></span>  
  
```xml  
<behaviors>
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"
             messageAuthenticationAuditLevel="Success" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a><span data-ttu-id="a140e-225">安全元数据交换</span><span class="sxs-lookup"><span data-stu-id="a140e-225">Secure Metadata Exchange</span></span>  
 <span data-ttu-id="a140e-226">对于服务和客户端开发人员来讲，向客户端导出元数据是很方便的，因为使用该操作可以下载配置和客户端代码。</span><span class="sxs-lookup"><span data-stu-id="a140e-226">Exporting metadata to clients is convenient for service and client developers, as it enables downloads of configuration and client code.</span></span> <span data-ttu-id="a140e-227">为了降低服务被恶意使用者滥用的可能性，可以使用 SSL over HTTP (HTTPS) 机制来确保传输的安全。</span><span class="sxs-lookup"><span data-stu-id="a140e-227">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="a140e-228">为此，必须首先将一个适合的 X.509 证书绑定到承载该服务的计算机上的特定端口。</span><span class="sxs-lookup"><span data-stu-id="a140e-228">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="a140e-229"> (有关详细信息，请参阅使用 [证书](working-with-certificates.md)。 ) 秒，请将添加 [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) 到服务配置，并将 `HttpsGetEnabled` 特性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a140e-229">(For more information, see [Working with Certificates](working-with-certificates.md).) Second, add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) to the service configuration and set the `HttpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="a140e-230">最后，将 `HttpsGetUrl` 属性设置为服务元数据终结点的 URL，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a140e-230">Finally, set the `HttpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a140e-231">请参阅</span><span class="sxs-lookup"><span data-stu-id="a140e-231">See also</span></span>

- [<span data-ttu-id="a140e-232">审核</span><span class="sxs-lookup"><span data-stu-id="a140e-232">Auditing</span></span>](auditing-security-events.md)
- <span data-ttu-id="a140e-233">[Windows Server App Fabric 的安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a140e-233">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
