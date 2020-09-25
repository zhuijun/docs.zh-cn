---
title: <security> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: 48b49bf69f791f90ed5b2eea8e6d412438cd9519
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169838"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="6dffd-102">\<security> 的 \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="6dffd-102">\<security> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="6dffd-103">表示与元素一起使用的安全设置 [\<ws2007HttpBinding>](ws2007httpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="6dffd-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="6dffd-104">语法</span><span class="sxs-lookup"><span data-stu-id="6dffd-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dffd-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6dffd-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6dffd-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6dffd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dffd-107">特性</span><span class="sxs-lookup"><span data-stu-id="6dffd-107">Attributes</span></span>  
  
|<span data-ttu-id="6dffd-108">属性</span><span class="sxs-lookup"><span data-stu-id="6dffd-108">Attribute</span></span>|<span data-ttu-id="6dffd-109">描述</span><span class="sxs-lookup"><span data-stu-id="6dffd-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="6dffd-110">可有可无.</span><span class="sxs-lookup"><span data-stu-id="6dffd-110">-   Optional.</span></span> <span data-ttu-id="6dffd-111">指定所应用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="6dffd-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6dffd-112">默认为 `Message`。</span><span class="sxs-lookup"><span data-stu-id="6dffd-112">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="6dffd-113">此属性的类型为 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="6dffd-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6dffd-114">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="6dffd-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="6dffd-115">值</span><span class="sxs-lookup"><span data-stu-id="6dffd-115">Value</span></span>|<span data-ttu-id="6dffd-116">描述</span><span class="sxs-lookup"><span data-stu-id="6dffd-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6dffd-117">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="6dffd-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="6dffd-118">使用 HTTPS 提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6dffd-118">Security is provided using HTTPS.</span></span> <span data-ttu-id="6dffd-119">此服务必须使用安全套接字层 (SSL) 证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="6dffd-119">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="6dffd-120">消息使用 HTTPS 获得全面保护，而且客户端使用服务的 SSL 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="6dffd-120">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="6dffd-121">客户端身份验证通过元素的 `ClientCredentials` 属性进行控制 [\<transport>](transport-of-ws2007httpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="6dffd-121">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="6dffd-122">使用 SOAP 消息安全提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6dffd-122">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6dffd-123">默认情况下，将对 SOAP 正文进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="6dffd-123">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="6dffd-124">此模式提供了各种各样的功能，例如服务凭据在带外客户端是否可用、要使用的算法套件以及通过 <xref:System.ServiceModel.Security.SecurityMessageProperty> 要应用于消息正文的保护级别。</span><span class="sxs-lookup"><span data-stu-id="6dffd-124">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="6dffd-125">每个会话将执行一次客户端身份验证，身份验证的结果在会话过程中将进行缓存。</span><span class="sxs-lookup"><span data-stu-id="6dffd-125">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="6dffd-126">在此模式下，HTTPS 将提供完整性、保密性和服务器身份验证，SOAP 消息安全将提供客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="6dffd-126">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="6dffd-127">默认情况下，每个会话将执行一次客户端身份验证，身份验证的结果在会话过程中将进行缓存。</span><span class="sxs-lookup"><span data-stu-id="6dffd-127">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6dffd-128">子元素</span><span class="sxs-lookup"><span data-stu-id="6dffd-128">Child Elements</span></span>  
  
|<span data-ttu-id="6dffd-129">元素</span><span class="sxs-lookup"><span data-stu-id="6dffd-129">Element</span></span>|<span data-ttu-id="6dffd-130">描述</span><span class="sxs-lookup"><span data-stu-id="6dffd-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="6dffd-131">定义传输安全设置。</span><span class="sxs-lookup"><span data-stu-id="6dffd-131">Defines the transport security settings.</span></span> <span data-ttu-id="6dffd-132">此元素与 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 类型相对应。</span><span class="sxs-lookup"><span data-stu-id="6dffd-132">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="6dffd-133">仅在将模式设置为“Transport”时才应用这些设置。</span><span class="sxs-lookup"><span data-stu-id="6dffd-133">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="6dffd-134">定义消息的安全设置。</span><span class="sxs-lookup"><span data-stu-id="6dffd-134">Defines the security settings for the message.</span></span> <span data-ttu-id="6dffd-135">此元素与 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 类型相对应。</span><span class="sxs-lookup"><span data-stu-id="6dffd-135">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="6dffd-136">将模式设置为“Transport”时，不应用这些设置。</span><span class="sxs-lookup"><span data-stu-id="6dffd-136">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6dffd-137">父元素</span><span class="sxs-lookup"><span data-stu-id="6dffd-137">Parent Elements</span></span>  
  
|<span data-ttu-id="6dffd-138">元素</span><span class="sxs-lookup"><span data-stu-id="6dffd-138">Element</span></span>|<span data-ttu-id="6dffd-139">描述</span><span class="sxs-lookup"><span data-stu-id="6dffd-139">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="6dffd-140">HTTP 传输应用程序的安全绑定。</span><span class="sxs-lookup"><span data-stu-id="6dffd-140">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dffd-141">备注</span><span class="sxs-lookup"><span data-stu-id="6dffd-141">Remarks</span></span>  

 <span data-ttu-id="6dffd-142">此元素专用于与实现 WS-\* 规范的服务进行互操作。</span><span class="sxs-lookup"><span data-stu-id="6dffd-142">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="6dffd-143">此绑定的传输安全为 HTTP 上的安全套接字层 (SSL)，即 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="6dffd-143">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dffd-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="6dffd-144">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="6dffd-145">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="6dffd-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6dffd-146">绑定</span><span class="sxs-lookup"><span data-stu-id="6dffd-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6dffd-147">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="6dffd-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6dffd-148">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="6dffd-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
