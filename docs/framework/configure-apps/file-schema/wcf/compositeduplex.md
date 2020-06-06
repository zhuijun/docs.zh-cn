---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736776"
---
# \<compositeDuplex>
<span data-ttu-id="f3bfe-101">定义绑定元素，客户端在必须公开一个终结点以使服务可以将消息发送回客户端时使用此元素。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="f3bfe-102">语法</span><span class="sxs-lookup"><span data-stu-id="f3bfe-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3bfe-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f3bfe-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f3bfe-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3bfe-105">特性</span><span class="sxs-lookup"><span data-stu-id="f3bfe-105">Attributes</span></span>  
  
|<span data-ttu-id="f3bfe-106">属性</span><span class="sxs-lookup"><span data-stu-id="f3bfe-106">Attribute</span></span>|<span data-ttu-id="f3bfe-107">说明</span><span class="sxs-lookup"><span data-stu-id="f3bfe-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3bfe-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="f3bfe-108">clientBaseAddress</span></span>|<span data-ttu-id="f3bfe-109">一个在双工模式下设置反向通道地址的 URI。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="f3bfe-110">服务使用该地址与客户端进行联系和建立连接。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="f3bfe-111">如果未设置此属性，则生成默认地址 " `full qualified name+default port\TemporaryIndigoAddress\guid` "。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="f3bfe-112">默认为 `null`。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3bfe-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f3bfe-113">Child Elements</span></span>  
 <span data-ttu-id="f3bfe-114">无</span><span class="sxs-lookup"><span data-stu-id="f3bfe-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3bfe-115">父元素</span><span class="sxs-lookup"><span data-stu-id="f3bfe-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f3bfe-116">元素</span><span class="sxs-lookup"><span data-stu-id="f3bfe-116">Element</span></span>|<span data-ttu-id="f3bfe-117">描述</span><span class="sxs-lookup"><span data-stu-id="f3bfe-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f3bfe-118">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3bfe-119">注解</span><span class="sxs-lookup"><span data-stu-id="f3bfe-119">Remarks</span></span>  
 <span data-ttu-id="f3bfe-120">此配置元素与本身不允许进行双工通信的传输（例如，HTTP）一起使用。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="f3bfe-121">与此相反，TCP 本身允许进行双工通信，并且不要求服务在将消息发送回客户端时使用此绑定元素。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="f3bfe-122">客户端必须公开一个地址，以便服务进行联系和建立连接。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="f3bfe-123">此客户端地址由 `clientBaseAddress` 属性提供。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="f3bfe-124">请注意，如果用户未显式设置 ClientBaseAddress，则 Windows Communication Foundation (WCF) 将自动生成一个 ClientBaseAddress。</span><span class="sxs-lookup"><span data-stu-id="f3bfe-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3bfe-125">示例</span><span class="sxs-lookup"><span data-stu-id="f3bfe-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f3bfe-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3bfe-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f3bfe-127">绑定</span><span class="sxs-lookup"><span data-stu-id="f3bfe-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3bfe-128">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="f3bfe-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f3bfe-129">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="f3bfe-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
