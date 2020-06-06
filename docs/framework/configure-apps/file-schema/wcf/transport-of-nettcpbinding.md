---
title: <transport> 的 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735931"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="b2d1e-102">\<transport> 的 \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="b2d1e-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="b2d1e-103">为使用配置的终结点定义消息级安全性要求的类型 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="b2d1e-104">语法</span><span class="sxs-lookup"><span data-stu-id="b2d1e-104">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2d1e-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b2d1e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b2d1e-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2d1e-107">特性</span><span class="sxs-lookup"><span data-stu-id="b2d1e-107">Attributes</span></span>  
  
|<span data-ttu-id="b2d1e-108">属性</span><span class="sxs-lookup"><span data-stu-id="b2d1e-108">Attribute</span></span>|<span data-ttu-id="b2d1e-109">说明</span><span class="sxs-lookup"><span data-stu-id="b2d1e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2d1e-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b2d1e-110">clientCredentialType</span></span>|<span data-ttu-id="b2d1e-111">可选。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-111">Optional.</span></span> <span data-ttu-id="b2d1e-112">指定要在使用传输安全性执行客户端身份验证时使用的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="b2d1e-113">-默认值为 `Windows` 。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="b2d1e-114">-此属性的类型为 <xref:System.ServiceModel.TcpClientCredentialType> 。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="b2d1e-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="b2d1e-115">protectionLevel</span></span>|<span data-ttu-id="b2d1e-116">可选。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-116">Optional.</span></span> <span data-ttu-id="b2d1e-117">定义 TCP 传输级别的安全性。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="b2d1e-118">消息签名降低了在消息传输过程中第三方对消息进行篡改的风险。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="b2d1e-119">加密为传输过程提供了数据级保密功能。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="b2d1e-120">默认值为 `EncryptAndSign`。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="b2d1e-121">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="b2d1e-121">sslProtocols</span></span>|<span data-ttu-id="b2d1e-122">指定支持哪些 SslProtocols 的 SslProtocols 枚举标志值。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="b2d1e-123">默认值为 Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="b2d1e-124">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="b2d1e-124">policyEnforcement</span></span>|<span data-ttu-id="b2d1e-125">此枚举指定应何时强制实施 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b2d1e-126">1. 从不–不强制实施策略（禁用扩展保护）。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b2d1e-127">WhenSupported-仅当客户端支持扩展保护时才强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b2d1e-128">3. always –始终强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b2d1e-129">不支持扩展保护的客户端将无法进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b2d1e-130">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="b2d1e-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b2d1e-131">值</span><span class="sxs-lookup"><span data-stu-id="b2d1e-131">Value</span></span>|<span data-ttu-id="b2d1e-132">说明</span><span class="sxs-lookup"><span data-stu-id="b2d1e-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b2d1e-133">无</span><span class="sxs-lookup"><span data-stu-id="b2d1e-133">None</span></span>|<span data-ttu-id="b2d1e-134">客户端为匿名客户端。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-134">The client is anonymous.</span></span> <span data-ttu-id="b2d1e-135">这需要服务证书。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="b2d1e-136">Windows</span><span class="sxs-lookup"><span data-stu-id="b2d1e-136">Windows</span></span>|<span data-ttu-id="b2d1e-137">指定使用 SP 协商（Kerberos 协商）进行客户端 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="b2d1e-138">证书</span><span class="sxs-lookup"><span data-stu-id="b2d1e-138">Certificate</span></span>|<span data-ttu-id="b2d1e-139">使用证书进行对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="b2d1e-140">这使用 SSL 协商并需要服务证书。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="b2d1e-141">protectionLevel 属性</span><span class="sxs-lookup"><span data-stu-id="b2d1e-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="b2d1e-142">值</span><span class="sxs-lookup"><span data-stu-id="b2d1e-142">Value</span></span>|<span data-ttu-id="b2d1e-143">说明</span><span class="sxs-lookup"><span data-stu-id="b2d1e-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b2d1e-144">无</span><span class="sxs-lookup"><span data-stu-id="b2d1e-144">None</span></span>|<span data-ttu-id="b2d1e-145">无保护。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-145">No protection.</span></span>|  
|<span data-ttu-id="b2d1e-146">Sign</span><span class="sxs-lookup"><span data-stu-id="b2d1e-146">Sign</span></span>|<span data-ttu-id="b2d1e-147">对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-147">Messages are signed.</span></span>|  
|<span data-ttu-id="b2d1e-148">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="b2d1e-148">EncryptAndSign</span></span>|<span data-ttu-id="b2d1e-149">-对消息进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2d1e-150">子元素</span><span class="sxs-lookup"><span data-stu-id="b2d1e-150">Child Elements</span></span>  
 <span data-ttu-id="b2d1e-151">无</span><span class="sxs-lookup"><span data-stu-id="b2d1e-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2d1e-152">父元素</span><span class="sxs-lookup"><span data-stu-id="b2d1e-152">Parent Elements</span></span>  
  
|<span data-ttu-id="b2d1e-153">元素</span><span class="sxs-lookup"><span data-stu-id="b2d1e-153">Element</span></span>|<span data-ttu-id="b2d1e-154">描述</span><span class="sxs-lookup"><span data-stu-id="b2d1e-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="b2d1e-155">指定的安全功能 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2d1e-156">注解</span><span class="sxs-lookup"><span data-stu-id="b2d1e-156">Remarks</span></span>  
 <span data-ttu-id="b2d1e-157">使用传输安全性以获得 SOAP 消息的完整性和保密性以及相互身份验证。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="b2d1e-158">如果在绑定上选择此安全模式，则使用安全传输配置信道栈，并且使用传输安全性（如 Windows (Negotiate) 或 SSLL）保护 SOAP 消息安全通过 TCP 传递。</span><span class="sxs-lookup"><span data-stu-id="b2d1e-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d1e-159">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2d1e-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="b2d1e-160">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="b2d1e-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b2d1e-161">绑定</span><span class="sxs-lookup"><span data-stu-id="b2d1e-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b2d1e-162">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="b2d1e-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b2d1e-163">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="b2d1e-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
