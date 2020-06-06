---
title: <transport> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732761"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="b3791-102">\<transport> 的 \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="b3791-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="b3791-103">定义 HTTP 传输的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="b3791-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="b3791-104">语法</span><span class="sxs-lookup"><span data-stu-id="b3791-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="b3791-105">类型</span><span class="sxs-lookup"><span data-stu-id="b3791-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3791-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b3791-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b3791-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b3791-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3791-108">特性</span><span class="sxs-lookup"><span data-stu-id="b3791-108">Attributes</span></span>  
  
|<span data-ttu-id="b3791-109">属性</span><span class="sxs-lookup"><span data-stu-id="b3791-109">Attribute</span></span>|<span data-ttu-id="b3791-110">说明</span><span class="sxs-lookup"><span data-stu-id="b3791-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="b3791-111">指定用于向服务证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="b3791-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="b3791-112">此属性的类型为 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="b3791-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="b3791-113">指定用于向域代理证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="b3791-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="b3791-114">此属性的类型为 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="b3791-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="b3791-115">摘要式或基本身份验证的身份验证领域。</span><span class="sxs-lookup"><span data-stu-id="b3791-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="b3791-116">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="b3791-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="b3791-117">身份验证领域至少指定执行身份验证的主机的名称。</span><span class="sxs-lookup"><span data-stu-id="b3791-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="b3791-118">它还可以指定具有访问权限的用户集合。</span><span class="sxs-lookup"><span data-stu-id="b3791-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="b3791-119">用户可以查询身份验证领域，以确定多个可能的用户名和密码中哪一个可以使用。</span><span class="sxs-lookup"><span data-stu-id="b3791-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b3791-120">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="b3791-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b3791-121">值</span><span class="sxs-lookup"><span data-stu-id="b3791-121">Value</span></span>|<span data-ttu-id="b3791-122">说明</span><span class="sxs-lookup"><span data-stu-id="b3791-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b3791-123">无</span><span class="sxs-lookup"><span data-stu-id="b3791-123">None</span></span>|<span data-ttu-id="b3791-124">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="b3791-124">Security is disabled.</span></span>|  
|<span data-ttu-id="b3791-125">基本</span><span class="sxs-lookup"><span data-stu-id="b3791-125">Basic</span></span>|<span data-ttu-id="b3791-126">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3791-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="b3791-127">摘要</span><span class="sxs-lookup"><span data-stu-id="b3791-127">Digest</span></span>|<span data-ttu-id="b3791-128">使用摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3791-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="b3791-129">Ntlm</span><span class="sxs-lookup"><span data-stu-id="b3791-129">Ntlm</span></span>|<span data-ttu-id="b3791-130">对 Windows 域使用 NTLM 身份验证作为回退。</span><span class="sxs-lookup"><span data-stu-id="b3791-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="b3791-131">Windows</span><span class="sxs-lookup"><span data-stu-id="b3791-131">Windows</span></span>|<span data-ttu-id="b3791-132">使用集成 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3791-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="b3791-133">证书</span><span class="sxs-lookup"><span data-stu-id="b3791-133">Certificate</span></span>|<span data-ttu-id="b3791-134">使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3791-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="b3791-135">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="b3791-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b3791-136">值</span><span class="sxs-lookup"><span data-stu-id="b3791-136">Value</span></span>|<span data-ttu-id="b3791-137">说明</span><span class="sxs-lookup"><span data-stu-id="b3791-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b3791-138">无</span><span class="sxs-lookup"><span data-stu-id="b3791-138">None</span></span>|<span data-ttu-id="b3791-139">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="b3791-139">Security is disabled.</span></span>|  
|<span data-ttu-id="b3791-140">基本</span><span class="sxs-lookup"><span data-stu-id="b3791-140">Basic</span></span>|<span data-ttu-id="b3791-141">使用基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3791-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="b3791-142">摘要</span><span class="sxs-lookup"><span data-stu-id="b3791-142">Digest</span></span>|<span data-ttu-id="b3791-143">使用摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3791-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="b3791-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="b3791-144">Ntlm</span></span>|<span data-ttu-id="b3791-145">对 Windows 域使用 NTLM 作为回退。</span><span class="sxs-lookup"><span data-stu-id="b3791-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="b3791-146">Windows</span><span class="sxs-lookup"><span data-stu-id="b3791-146">Windows</span></span>|<span data-ttu-id="b3791-147">使用集成 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3791-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="b3791-148">证书</span><span class="sxs-lookup"><span data-stu-id="b3791-148">Certificate</span></span>|<span data-ttu-id="b3791-149">使用 X.509 证书对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3791-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3791-150">子元素</span><span class="sxs-lookup"><span data-stu-id="b3791-150">Child Elements</span></span>  
 <span data-ttu-id="b3791-151">无</span><span class="sxs-lookup"><span data-stu-id="b3791-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3791-152">父元素</span><span class="sxs-lookup"><span data-stu-id="b3791-152">Parent Elements</span></span>  
  
|<span data-ttu-id="b3791-153">元素</span><span class="sxs-lookup"><span data-stu-id="b3791-153">Element</span></span>|<span data-ttu-id="b3791-154">描述</span><span class="sxs-lookup"><span data-stu-id="b3791-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="b3791-155">表示元素的安全功能 [\<ws2007HttpBinding>](ws2007httpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="b3791-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3791-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3791-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="b3791-157">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="b3791-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b3791-158">绑定</span><span class="sxs-lookup"><span data-stu-id="b3791-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b3791-159">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="b3791-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b3791-160">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="b3791-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
