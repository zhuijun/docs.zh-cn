---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: c5cd8e9e2002f44fd9feebdc6bb7ede023de459a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556442"
---
# \<textMessageEncoding>
<span data-ttu-id="7e4ad-101">指定用于基于文本的 XML 消息的字符编码和消息版本控制。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-101">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="7e4ad-102">语法</span><span class="sxs-lookup"><span data-stu-id="7e4ad-102">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e4ad-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7e4ad-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7e4ad-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e4ad-105">特性</span><span class="sxs-lookup"><span data-stu-id="7e4ad-105">Attributes</span></span>  
  
|<span data-ttu-id="7e4ad-106">属性</span><span class="sxs-lookup"><span data-stu-id="7e4ad-106">Attribute</span></span>|<span data-ttu-id="7e4ad-107">说明</span><span class="sxs-lookup"><span data-stu-id="7e4ad-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e4ad-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="7e4ad-108">maxReadPoolSize</span></span>|<span data-ttu-id="7e4ad-109">一个整数，指定在无需分配新读取器的情况下可以同时读取的消息数。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-109">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="7e4ad-110">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="7e4ad-111">默认值为 64。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-111">The default is 64.</span></span>|  
|<span data-ttu-id="7e4ad-112">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="7e4ad-112">maxWritePoolSize</span></span>|<span data-ttu-id="7e4ad-113">一个整数，指定在无需分配新编写器的情况下可以同时发送的消息数。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-113">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="7e4ad-114">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="7e4ad-115">默认值为 16。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-115">The default is 16.</span></span>|  
|<span data-ttu-id="7e4ad-116">messageVersion</span><span class="sxs-lookup"><span data-stu-id="7e4ad-116">messageVersion</span></span>|<span data-ttu-id="7e4ad-117">指定使用此绑定发送的消息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-117">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="7e4ad-118">有效值为</span><span class="sxs-lookup"><span data-stu-id="7e4ad-118">Valid values are</span></span><br /><br /> <span data-ttu-id="7e4ad-119">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="7e4ad-119">-   Soap11Addressing10</span></span><br /><span data-ttu-id="7e4ad-120">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="7e4ad-120">-   Soap12Addressing10</span></span><br /><span data-ttu-id="7e4ad-121">- Soap11</span><span class="sxs-lookup"><span data-stu-id="7e4ad-121">-   Soap11</span></span><br /><span data-ttu-id="7e4ad-122">- Soap12</span><span class="sxs-lookup"><span data-stu-id="7e4ad-122">-  Soap12</span></span><br /><br /><span data-ttu-id="7e4ad-123">默认值为 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="7e4ad-124">此属性的类型为 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="7e4ad-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="7e4ad-125">writeEncoding</span></span>|<span data-ttu-id="7e4ad-126">指定要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="7e4ad-127">有效值为</span><span class="sxs-lookup"><span data-stu-id="7e4ad-127">Valid values are</span></span><br /><br /> <span data-ttu-id="7e4ad-128">-UnicodeFffeTextEncoding： Unicode BigEndian 编码</span><span class="sxs-lookup"><span data-stu-id="7e4ad-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="7e4ad-129">-Utf16TextEncoding： Unicode 编码</span><span class="sxs-lookup"><span data-stu-id="7e4ad-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="7e4ad-130">-Utf8TextEncoding：8位编码</span><span class="sxs-lookup"><span data-stu-id="7e4ad-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="7e4ad-131">默认值为 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="7e4ad-132">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e4ad-133">子元素</span><span class="sxs-lookup"><span data-stu-id="7e4ad-133">Child Elements</span></span>  
  
|<span data-ttu-id="7e4ad-134">元素</span><span class="sxs-lookup"><span data-stu-id="7e4ad-134">Element</span></span>|<span data-ttu-id="7e4ad-135">说明</span><span class="sxs-lookup"><span data-stu-id="7e4ad-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="7e4ad-136">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7e4ad-137">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e4ad-138">父元素</span><span class="sxs-lookup"><span data-stu-id="7e4ad-138">Parent Elements</span></span>  
  
|<span data-ttu-id="7e4ad-139">元素</span><span class="sxs-lookup"><span data-stu-id="7e4ad-139">Element</span></span>|<span data-ttu-id="7e4ad-140">说明</span><span class="sxs-lookup"><span data-stu-id="7e4ad-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="7e4ad-141">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e4ad-142">备注</span><span class="sxs-lookup"><span data-stu-id="7e4ad-142">Remarks</span></span>  
 <span data-ttu-id="7e4ad-143">编码是将消息转换为一个字节序列的过程。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="7e4ad-144">解码是反向过程。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-144">Decoding is the reverse process.</span></span> <span data-ttu-id="7e4ad-145">Windows Communication Foundation (WCF) 包含三种类型的 SOAP 消息编码：文本、二进制和消息传输优化机制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="7e4ad-146">由 `textMessageEncoding` 元素表示的文本编码互操作性最强，但却是效率最低的 XML 消息编码器。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-146">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="7e4ad-147">文本编码器在网络上创建基于文本的消息。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-147">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="7e4ad-148">此编码器产生的消息适合于基于 WS-\* 的互操作性。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-148">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="7e4ad-149">Web 服务或 Web 服务客户端通常可以理解文本 XML。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-149">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="7e4ad-150">但是，对于 XML 消息编码来说，以文本形式传输较大的二进制数据块是最低效的方法。</span><span class="sxs-lookup"><span data-stu-id="7e4ad-150">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e4ad-151">示例</span><span class="sxs-lookup"><span data-stu-id="7e4ad-151">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="7e4ad-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="7e4ad-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="7e4ad-153">选择消息编码器</span><span class="sxs-lookup"><span data-stu-id="7e4ad-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="7e4ad-154">消息编码</span><span class="sxs-lookup"><span data-stu-id="7e4ad-154">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="7e4ad-155">绑定</span><span class="sxs-lookup"><span data-stu-id="7e4ad-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7e4ad-156">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="7e4ad-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7e4ad-157">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="7e4ad-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
