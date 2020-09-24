---
title: <transport> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 60e8758d653848176ca3f287e253bd7990e78470
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162044"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="f3d86-102">\<transport> 的 \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="f3d86-102">\<transport> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="f3d86-103">定义 HTTP 传输的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="f3d86-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="f3d86-104">语法</span><span class="sxs-lookup"><span data-stu-id="f3d86-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="f3d86-105">类型</span><span class="sxs-lookup"><span data-stu-id="f3d86-105">Type</span></span>  

 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3d86-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f3d86-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f3d86-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f3d86-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3d86-108">特性</span><span class="sxs-lookup"><span data-stu-id="f3d86-108">Attributes</span></span>  
  
|<span data-ttu-id="f3d86-109">属性</span><span class="sxs-lookup"><span data-stu-id="f3d86-109">Attribute</span></span>|<span data-ttu-id="f3d86-110">描述</span><span class="sxs-lookup"><span data-stu-id="f3d86-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="f3d86-111">指定用于向服务证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="f3d86-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="f3d86-112">此属性的类型为 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="f3d86-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="f3d86-113">指定用于向域代理证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="f3d86-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="f3d86-114">此属性的类型为 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="f3d86-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="f3d86-115">摘要式或基本身份验证的身份验证领域。</span><span class="sxs-lookup"><span data-stu-id="f3d86-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="f3d86-116">默认值为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="f3d86-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="f3d86-117">身份验证领域至少指定执行身份验证的主机的名称。</span><span class="sxs-lookup"><span data-stu-id="f3d86-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="f3d86-118">它还可以指定具有访问权限的用户集合。</span><span class="sxs-lookup"><span data-stu-id="f3d86-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="f3d86-119">用户可以查询身份验证领域，以确定多个可能的用户名和密码中哪一个可以使用。</span><span class="sxs-lookup"><span data-stu-id="f3d86-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="f3d86-120">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="f3d86-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f3d86-121">值</span><span class="sxs-lookup"><span data-stu-id="f3d86-121">Value</span></span>|<span data-ttu-id="f3d86-122">描述</span><span class="sxs-lookup"><span data-stu-id="f3d86-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3d86-123">无</span><span class="sxs-lookup"><span data-stu-id="f3d86-123">None</span></span>|<span data-ttu-id="f3d86-124">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="f3d86-124">Security is disabled.</span></span>|  
|<span data-ttu-id="f3d86-125">基本</span><span class="sxs-lookup"><span data-stu-id="f3d86-125">Basic</span></span>|<span data-ttu-id="f3d86-126">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3d86-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="f3d86-127">摘要</span><span class="sxs-lookup"><span data-stu-id="f3d86-127">Digest</span></span>|<span data-ttu-id="f3d86-128">使用摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3d86-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="f3d86-129">Ntlm</span><span class="sxs-lookup"><span data-stu-id="f3d86-129">Ntlm</span></span>|<span data-ttu-id="f3d86-130">对 Windows 域使用 NTLM 身份验证作为回退。</span><span class="sxs-lookup"><span data-stu-id="f3d86-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="f3d86-131">Windows</span><span class="sxs-lookup"><span data-stu-id="f3d86-131">Windows</span></span>|<span data-ttu-id="f3d86-132">使用集成 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3d86-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="f3d86-133">证书</span><span class="sxs-lookup"><span data-stu-id="f3d86-133">Certificate</span></span>|<span data-ttu-id="f3d86-134">使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3d86-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="f3d86-135">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="f3d86-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f3d86-136">值</span><span class="sxs-lookup"><span data-stu-id="f3d86-136">Value</span></span>|<span data-ttu-id="f3d86-137">描述</span><span class="sxs-lookup"><span data-stu-id="f3d86-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3d86-138">无</span><span class="sxs-lookup"><span data-stu-id="f3d86-138">None</span></span>|<span data-ttu-id="f3d86-139">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="f3d86-139">Security is disabled.</span></span>|  
|<span data-ttu-id="f3d86-140">基本</span><span class="sxs-lookup"><span data-stu-id="f3d86-140">Basic</span></span>|<span data-ttu-id="f3d86-141">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3d86-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="f3d86-142">摘要</span><span class="sxs-lookup"><span data-stu-id="f3d86-142">Digest</span></span>|<span data-ttu-id="f3d86-143">使用摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3d86-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="f3d86-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="f3d86-144">Ntlm</span></span>|<span data-ttu-id="f3d86-145">对 Windows 域使用 NTLM 作为回退。</span><span class="sxs-lookup"><span data-stu-id="f3d86-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="f3d86-146">Windows</span><span class="sxs-lookup"><span data-stu-id="f3d86-146">Windows</span></span>|<span data-ttu-id="f3d86-147">使用集成 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3d86-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="f3d86-148">证书</span><span class="sxs-lookup"><span data-stu-id="f3d86-148">Certificate</span></span>|<span data-ttu-id="f3d86-149">使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f3d86-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3d86-150">子元素</span><span class="sxs-lookup"><span data-stu-id="f3d86-150">Child Elements</span></span>  

 <span data-ttu-id="f3d86-151">无</span><span class="sxs-lookup"><span data-stu-id="f3d86-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3d86-152">父元素</span><span class="sxs-lookup"><span data-stu-id="f3d86-152">Parent Elements</span></span>  
  
|<span data-ttu-id="f3d86-153">元素</span><span class="sxs-lookup"><span data-stu-id="f3d86-153">Element</span></span>|<span data-ttu-id="f3d86-154">描述</span><span class="sxs-lookup"><span data-stu-id="f3d86-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="f3d86-155">表示元素的安全功能 [\<ws2007HttpBinding>](ws2007httpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="f3d86-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3d86-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3d86-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="f3d86-157">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="f3d86-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f3d86-158">绑定</span><span class="sxs-lookup"><span data-stu-id="f3d86-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3d86-159">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="f3d86-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f3d86-160">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="f3d86-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
