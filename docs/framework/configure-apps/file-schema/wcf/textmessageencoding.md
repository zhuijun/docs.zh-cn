---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 159c581955336575af87a66a796cb78dd35d09c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158651"
---
# \<textMessageEncoding>

<span data-ttu-id="9d886-101">指定用于基于文本的 XML 消息的字符编码和消息版本控制。</span><span class="sxs-lookup"><span data-stu-id="9d886-101">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="9d886-102">语法</span><span class="sxs-lookup"><span data-stu-id="9d886-102">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d886-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9d886-103">Attributes and Elements</span></span>  

 <span data-ttu-id="9d886-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9d886-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d886-105">特性</span><span class="sxs-lookup"><span data-stu-id="9d886-105">Attributes</span></span>  
  
|<span data-ttu-id="9d886-106">属性</span><span class="sxs-lookup"><span data-stu-id="9d886-106">Attribute</span></span>|<span data-ttu-id="9d886-107">描述</span><span class="sxs-lookup"><span data-stu-id="9d886-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d886-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="9d886-108">maxReadPoolSize</span></span>|<span data-ttu-id="9d886-109">一个整数，指定在无需分配新读取器的情况下可以同时读取的消息数。</span><span class="sxs-lookup"><span data-stu-id="9d886-109">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="9d886-110">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="9d886-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="9d886-111">默认值为 64。</span><span class="sxs-lookup"><span data-stu-id="9d886-111">The default is 64.</span></span>|  
|<span data-ttu-id="9d886-112">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="9d886-112">maxWritePoolSize</span></span>|<span data-ttu-id="9d886-113">一个整数，指定在无需分配新编写器的情况下可以同时发送的消息数。</span><span class="sxs-lookup"><span data-stu-id="9d886-113">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="9d886-114">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="9d886-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="9d886-115">默认值为 16。</span><span class="sxs-lookup"><span data-stu-id="9d886-115">The default is 16.</span></span>|  
|<span data-ttu-id="9d886-116">messageVersion</span><span class="sxs-lookup"><span data-stu-id="9d886-116">messageVersion</span></span>|<span data-ttu-id="9d886-117">指定使用此绑定发送的消息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="9d886-117">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="9d886-118">有效值为</span><span class="sxs-lookup"><span data-stu-id="9d886-118">Valid values are</span></span><br /><br /> <span data-ttu-id="9d886-119">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="9d886-119">-   Soap11Addressing10</span></span><br /><span data-ttu-id="9d886-120">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="9d886-120">-   Soap12Addressing10</span></span><br /><span data-ttu-id="9d886-121">- Soap11</span><span class="sxs-lookup"><span data-stu-id="9d886-121">-   Soap11</span></span><br /><span data-ttu-id="9d886-122">- Soap12</span><span class="sxs-lookup"><span data-stu-id="9d886-122">-  Soap12</span></span><br /><br /><span data-ttu-id="9d886-123">默认值为 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="9d886-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="9d886-124">此属性的类型为 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="9d886-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="9d886-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="9d886-125">writeEncoding</span></span>|<span data-ttu-id="9d886-126">指定要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="9d886-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9d886-127">有效值为</span><span class="sxs-lookup"><span data-stu-id="9d886-127">Valid values are</span></span><br /><br /> <span data-ttu-id="9d886-128">-UnicodeFffeTextEncoding： Unicode BigEndian 编码</span><span class="sxs-lookup"><span data-stu-id="9d886-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="9d886-129">-Utf16TextEncoding： Unicode 编码</span><span class="sxs-lookup"><span data-stu-id="9d886-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="9d886-130">-Utf8TextEncoding：8位编码</span><span class="sxs-lookup"><span data-stu-id="9d886-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9d886-131">默认值为 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="9d886-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="9d886-132">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="9d886-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d886-133">子元素</span><span class="sxs-lookup"><span data-stu-id="9d886-133">Child Elements</span></span>  
  
|<span data-ttu-id="9d886-134">元素</span><span class="sxs-lookup"><span data-stu-id="9d886-134">Element</span></span>|<span data-ttu-id="9d886-135">描述</span><span class="sxs-lookup"><span data-stu-id="9d886-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="9d886-136">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="9d886-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9d886-137">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="9d886-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d886-138">父元素</span><span class="sxs-lookup"><span data-stu-id="9d886-138">Parent Elements</span></span>  
  
|<span data-ttu-id="9d886-139">元素</span><span class="sxs-lookup"><span data-stu-id="9d886-139">Element</span></span>|<span data-ttu-id="9d886-140">描述</span><span class="sxs-lookup"><span data-stu-id="9d886-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="9d886-141">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="9d886-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d886-142">备注</span><span class="sxs-lookup"><span data-stu-id="9d886-142">Remarks</span></span>  

 <span data-ttu-id="9d886-143">编码是将消息转换为一个字节序列的过程。</span><span class="sxs-lookup"><span data-stu-id="9d886-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="9d886-144">解码是反向过程。</span><span class="sxs-lookup"><span data-stu-id="9d886-144">Decoding is the reverse process.</span></span> <span data-ttu-id="9d886-145">Windows Communication Foundation (WCF) 包含三种类型的 SOAP 消息编码：文本、二进制和消息传输优化机制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="9d886-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="9d886-146">由 `textMessageEncoding` 元素表示的文本编码互操作性最强，但却是效率最低的 XML 消息编码器。</span><span class="sxs-lookup"><span data-stu-id="9d886-146">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="9d886-147">文本编码器在网络上创建基于文本的消息。</span><span class="sxs-lookup"><span data-stu-id="9d886-147">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="9d886-148">此编码器产生的消息适合于基于 WS-\* 的互操作性。</span><span class="sxs-lookup"><span data-stu-id="9d886-148">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="9d886-149">Web 服务或 Web 服务客户端通常可以理解文本 XML。</span><span class="sxs-lookup"><span data-stu-id="9d886-149">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="9d886-150">但是，对于 XML 消息编码来说，以文本形式传输较大的二进制数据块是最低效的方法。</span><span class="sxs-lookup"><span data-stu-id="9d886-150">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d886-151">示例</span><span class="sxs-lookup"><span data-stu-id="9d886-151">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="9d886-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="9d886-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="9d886-153">选择消息编码器</span><span class="sxs-lookup"><span data-stu-id="9d886-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="9d886-154">消息编码</span><span class="sxs-lookup"><span data-stu-id="9d886-154">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="9d886-155">绑定</span><span class="sxs-lookup"><span data-stu-id="9d886-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9d886-156">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="9d886-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9d886-157">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="9d886-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
