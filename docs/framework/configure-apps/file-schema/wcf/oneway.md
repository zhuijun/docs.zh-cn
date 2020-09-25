---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: 92cd6b280305c223ee125a45724691c5205ce3c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195007"
---
# \<oneWay>

<span data-ttu-id="04484-101">对自定义绑定启用数据包路由并使用单向方法。</span><span class="sxs-lookup"><span data-stu-id="04484-101">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="04484-102">语法</span><span class="sxs-lookup"><span data-stu-id="04484-102">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04484-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="04484-103">Attributes and Elements</span></span>  

 <span data-ttu-id="04484-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="04484-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04484-105">特性</span><span class="sxs-lookup"><span data-stu-id="04484-105">Attributes</span></span>  
  
|<span data-ttu-id="04484-106">属性</span><span class="sxs-lookup"><span data-stu-id="04484-106">Attribute</span></span>|<span data-ttu-id="04484-107">描述</span><span class="sxs-lookup"><span data-stu-id="04484-107">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="04484-108">一个布尔值，指定是否启用数据包路由。</span><span class="sxs-lookup"><span data-stu-id="04484-108">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="04484-109">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="04484-109">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="04484-110">一个整数，指定可接受的最大通道数。</span><span class="sxs-lookup"><span data-stu-id="04484-110">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04484-111">子元素</span><span class="sxs-lookup"><span data-stu-id="04484-111">Child Elements</span></span>  
  
|<span data-ttu-id="04484-112">元素</span><span class="sxs-lookup"><span data-stu-id="04484-112">Element</span></span>|<span data-ttu-id="04484-113">描述</span><span class="sxs-lookup"><span data-stu-id="04484-113">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="04484-114">一个 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> 对象，包含当前通道的通道池的属性。</span><span class="sxs-lookup"><span data-stu-id="04484-114">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="04484-115">父元素</span><span class="sxs-lookup"><span data-stu-id="04484-115">Parent Elements</span></span>  
  
|<span data-ttu-id="04484-116">元素</span><span class="sxs-lookup"><span data-stu-id="04484-116">Element</span></span>|<span data-ttu-id="04484-117">描述</span><span class="sxs-lookup"><span data-stu-id="04484-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="04484-118">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="04484-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04484-119">备注</span><span class="sxs-lookup"><span data-stu-id="04484-119">Remarks</span></span>  

 <span data-ttu-id="04484-120">若要启用数据包路由，必须使用此元素提供的单向转换层。</span><span class="sxs-lookup"><span data-stu-id="04484-120">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="04484-121">用户可以创建一个自定义绑定，将此绑定置于具有会话功能或请求/答复传输的上层，使之可进行数据包路由。</span><span class="sxs-lookup"><span data-stu-id="04484-121">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="04484-122">如果希望以更自然的方式公开单向方法，则此元素也十分有用。</span><span class="sxs-lookup"><span data-stu-id="04484-122">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="04484-123">在这一层上可应用更多的转换，如复合双工和可靠消息。</span><span class="sxs-lookup"><span data-stu-id="04484-123">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04484-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="04484-124">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="04484-125">绑定</span><span class="sxs-lookup"><span data-stu-id="04484-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="04484-126">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="04484-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="04484-127">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="04484-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
