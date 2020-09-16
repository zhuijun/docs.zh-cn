---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: e2b92b88c3e2a8abb14f58af90aab6e2e58ce14a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557289"
---
# \<byteStreamMessageEncoding>
<span data-ttu-id="86f62-101">指定消息编码作为字节流，也可以选择指定字符编码。</span><span class="sxs-lookup"><span data-stu-id="86f62-101">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="86f62-102">语法</span><span class="sxs-lookup"><span data-stu-id="86f62-102">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86f62-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="86f62-103">Attributes and Elements</span></span>  
 <span data-ttu-id="86f62-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="86f62-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86f62-105">特性</span><span class="sxs-lookup"><span data-stu-id="86f62-105">Attributes</span></span>  
  
|<span data-ttu-id="86f62-106">属性</span><span class="sxs-lookup"><span data-stu-id="86f62-106">Attribute</span></span>|<span data-ttu-id="86f62-107">说明</span><span class="sxs-lookup"><span data-stu-id="86f62-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86f62-108">messageVersion</span><span class="sxs-lookup"><span data-stu-id="86f62-108">messageVersion</span></span>|<span data-ttu-id="86f62-109">指定使用此绑定发送的消息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="86f62-109">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="86f62-110">此属性只能设置为 <xref:System.ServiceModel.Channels.MessageVersion.None%2A> 的消息版本值。</span><span class="sxs-lookup"><span data-stu-id="86f62-110">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="86f62-111">字节流消息编码器不支持其他任何消息版本。</span><span class="sxs-lookup"><span data-stu-id="86f62-111">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="86f62-112">此属性的类型为 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="86f62-112">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86f62-113">子元素</span><span class="sxs-lookup"><span data-stu-id="86f62-113">Child Elements</span></span>  
  
|<span data-ttu-id="86f62-114">元素</span><span class="sxs-lookup"><span data-stu-id="86f62-114">Element</span></span>|<span data-ttu-id="86f62-115">说明</span><span class="sxs-lookup"><span data-stu-id="86f62-115">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="86f62-116">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="86f62-116">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="86f62-117">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="86f62-117">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86f62-118">父元素</span><span class="sxs-lookup"><span data-stu-id="86f62-118">Parent Elements</span></span>  
  
|<span data-ttu-id="86f62-119">元素</span><span class="sxs-lookup"><span data-stu-id="86f62-119">Element</span></span>|<span data-ttu-id="86f62-120">说明</span><span class="sxs-lookup"><span data-stu-id="86f62-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="86f62-121">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="86f62-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86f62-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="86f62-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="86f62-123">消息编码</span><span class="sxs-lookup"><span data-stu-id="86f62-123">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="86f62-124">选择消息编码器</span><span class="sxs-lookup"><span data-stu-id="86f62-124">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="86f62-125">绑定</span><span class="sxs-lookup"><span data-stu-id="86f62-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="86f62-126">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="86f62-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="86f62-127">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="86f62-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
