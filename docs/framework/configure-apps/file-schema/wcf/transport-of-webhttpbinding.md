---
title: <transport> 的 <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: b9efc732832a8862373b14f657796a59fb52c1a1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162109"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="9714e-102">\<transport> 的 \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9714e-102">\<transport> of \<webHttpBinding></span></span>

<span data-ttu-id="9714e-103">定义配置为接收 HTTP 请求的服务终结点的传输级安全设置。</span><span class="sxs-lookup"><span data-stu-id="9714e-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="9714e-104">语法</span><span class="sxs-lookup"><span data-stu-id="9714e-104">Syntax</span></span>  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="9714e-105">类型</span><span class="sxs-lookup"><span data-stu-id="9714e-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9714e-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9714e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9714e-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9714e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9714e-108">特性</span><span class="sxs-lookup"><span data-stu-id="9714e-108">Attributes</span></span>  
  
|<span data-ttu-id="9714e-109">属性</span><span class="sxs-lookup"><span data-stu-id="9714e-109">Attribute</span></span>|<span data-ttu-id="9714e-110">描述</span><span class="sxs-lookup"><span data-stu-id="9714e-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="9714e-111">指定用于向服务证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="9714e-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="9714e-112">此属性的类型为 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="9714e-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="9714e-113">指定用于向域代理证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="9714e-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="9714e-114">此属性的类型为 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="9714e-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="9714e-115">一个字符串，指定摘要式或基本身份验证的身份验证领域。</span><span class="sxs-lookup"><span data-stu-id="9714e-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="9714e-116">默认值为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="9714e-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="9714e-117">身份验证领域至少指定执行身份验证的主机的名称。</span><span class="sxs-lookup"><span data-stu-id="9714e-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="9714e-118">它还可以指定具有访问权限的用户的集合。</span><span class="sxs-lookup"><span data-stu-id="9714e-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="9714e-119">用户可以查询身份验证领域，以确定多个可能的用户名和密码中哪一个可以使用。</span><span class="sxs-lookup"><span data-stu-id="9714e-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="9714e-120">此枚举指定应何时强制实施 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>。</span><span class="sxs-lookup"><span data-stu-id="9714e-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="9714e-121">1. 从不–不会强制实施策略 (禁用扩展保护) 。</span><span class="sxs-lookup"><span data-stu-id="9714e-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="9714e-122">WhenSupported-仅当客户端支持扩展保护时才强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="9714e-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="9714e-123">3. always –始终强制实施策略。</span><span class="sxs-lookup"><span data-stu-id="9714e-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="9714e-124">不支持扩展保护的客户端将无法进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="9714e-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="9714e-125">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="9714e-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9714e-126">值</span><span class="sxs-lookup"><span data-stu-id="9714e-126">Value</span></span>|<span data-ttu-id="9714e-127">描述</span><span class="sxs-lookup"><span data-stu-id="9714e-127">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="9714e-128">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="9714e-128">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="9714e-129">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="9714e-129">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="9714e-130">使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="9714e-130">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="9714e-131">使用摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="9714e-131">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="9714e-132">对 Windows 域使用 NTLM 身份验证作为回退。</span><span class="sxs-lookup"><span data-stu-id="9714e-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="9714e-133">使用集成 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9714e-133">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="9714e-134">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="9714e-134">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9714e-135">值</span><span class="sxs-lookup"><span data-stu-id="9714e-135">Value</span></span>|<span data-ttu-id="9714e-136">描述</span><span class="sxs-lookup"><span data-stu-id="9714e-136">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="9714e-137">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="9714e-137">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="9714e-138">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="9714e-138">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="9714e-139">使用摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="9714e-139">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="9714e-140">对 Windows 域使用 NTLM 作为回退。</span><span class="sxs-lookup"><span data-stu-id="9714e-140">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="9714e-141">使用集成 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="9714e-141">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9714e-142">子元素</span><span class="sxs-lookup"><span data-stu-id="9714e-142">Child Elements</span></span>  

 <span data-ttu-id="9714e-143">无。</span><span class="sxs-lookup"><span data-stu-id="9714e-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9714e-144">父元素</span><span class="sxs-lookup"><span data-stu-id="9714e-144">Parent Elements</span></span>  
  
|<span data-ttu-id="9714e-145">元素</span><span class="sxs-lookup"><span data-stu-id="9714e-145">Element</span></span>|<span data-ttu-id="9714e-146">描述</span><span class="sxs-lookup"><span data-stu-id="9714e-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="9714e-147">表示元素的安全功能 [\<wsHttpBinding>](wshttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="9714e-147">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9714e-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="9714e-148">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="9714e-149">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="9714e-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9714e-150">绑定</span><span class="sxs-lookup"><span data-stu-id="9714e-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9714e-151">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="9714e-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9714e-152">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="9714e-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="9714e-153">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="9714e-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
