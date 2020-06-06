---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738590"
---
# \<sslStreamSecurity>
<span data-ttu-id="91a09-101">表示一个自定义绑定元素，它支持使用 SSL 流的通道安全。</span><span class="sxs-lookup"><span data-stu-id="91a09-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="91a09-102">语法</span><span class="sxs-lookup"><span data-stu-id="91a09-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91a09-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="91a09-103">Attributes and Elements</span></span>  
 <span data-ttu-id="91a09-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="91a09-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91a09-105">特性</span><span class="sxs-lookup"><span data-stu-id="91a09-105">Attributes</span></span>  
  
|<span data-ttu-id="91a09-106">属性</span><span class="sxs-lookup"><span data-stu-id="91a09-106">Attribute</span></span>|<span data-ttu-id="91a09-107">说明</span><span class="sxs-lookup"><span data-stu-id="91a09-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91a09-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="91a09-108">requireClientCertificate</span></span>|<span data-ttu-id="91a09-109">一个布尔值，指定此绑定是否需要客户端证书。</span><span class="sxs-lookup"><span data-stu-id="91a09-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="91a09-110">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="91a09-110">The default is `false`.</span></span>|  
|<span data-ttu-id="91a09-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="91a09-111">sslProtocols</span></span>|<span data-ttu-id="91a09-112">指定支持哪些 SslProtocols 的 SslProtocols 枚举标志值。</span><span class="sxs-lookup"><span data-stu-id="91a09-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="91a09-113">默认值为 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="91a09-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91a09-114">子元素</span><span class="sxs-lookup"><span data-stu-id="91a09-114">Child Elements</span></span>  
 <span data-ttu-id="91a09-115">无。</span><span class="sxs-lookup"><span data-stu-id="91a09-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91a09-116">父元素</span><span class="sxs-lookup"><span data-stu-id="91a09-116">Parent Elements</span></span>  
  
|<span data-ttu-id="91a09-117">元素</span><span class="sxs-lookup"><span data-stu-id="91a09-117">Element</span></span>|<span data-ttu-id="91a09-118">描述</span><span class="sxs-lookup"><span data-stu-id="91a09-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="91a09-119">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="91a09-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91a09-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91a09-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="91a09-121">绑定</span><span class="sxs-lookup"><span data-stu-id="91a09-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="91a09-122">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="91a09-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="91a09-123">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="91a09-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
