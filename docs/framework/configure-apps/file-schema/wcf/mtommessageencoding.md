---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: cffde19c8fd06836eaaedb5c4fc8687b97ae0afe
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556175"
---
# \<mtomMessageEncoding>
<span data-ttu-id="ce7ee-101">指定用于基于 SOAP 消息传输优化机制 (MTOM) 的消息的编码和消息版本控制。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="ce7ee-102">语法</span><span class="sxs-lookup"><span data-stu-id="ce7ee-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce7ee-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ce7ee-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ce7ee-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce7ee-105">特性</span><span class="sxs-lookup"><span data-stu-id="ce7ee-105">Attributes</span></span>  
  
|<span data-ttu-id="ce7ee-106">属性</span><span class="sxs-lookup"><span data-stu-id="ce7ee-106">Attribute</span></span>|<span data-ttu-id="ce7ee-107">说明</span><span class="sxs-lookup"><span data-stu-id="ce7ee-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce7ee-108">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="ce7ee-108">maxBufferSize</span></span>|<span data-ttu-id="ce7ee-109">一个指定可以使用的缓冲区最大大小的整数。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="ce7ee-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="ce7ee-110">maxReadPoolSize</span></span>|<span data-ttu-id="ce7ee-111">一个整数，指定在无需分配新读取器的情况下可以同时读取的消息数。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="ce7ee-112">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ce7ee-113">默认值为 64。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-113">The default is 64.</span></span>|  
|<span data-ttu-id="ce7ee-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="ce7ee-114">maxWritePoolSize</span></span>|<span data-ttu-id="ce7ee-115">一个整数，指定在无需分配新编写器的情况下可以同时发送的消息数。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="ce7ee-116">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="ce7ee-117">默认值为 16。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-117">The default is 16.</span></span>|  
|<span data-ttu-id="ce7ee-118">messageVersion</span><span class="sxs-lookup"><span data-stu-id="ce7ee-118">messageVersion</span></span>|<span data-ttu-id="ce7ee-119">指定使用此绑定发送的消息的 SOAP 版本。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="ce7ee-120">有效值为</span><span class="sxs-lookup"><span data-stu-id="ce7ee-120">Valid values are</span></span><br /><br /> <span data-ttu-id="ce7ee-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="ce7ee-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="ce7ee-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="ce7ee-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="ce7ee-123">默认值为 Soap12Addressing10。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="ce7ee-124">此属性的类型为 <xref:System.ServiceModel.Channels.MessageVersion>。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="ce7ee-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="ce7ee-125">writeEncoding</span></span>|<span data-ttu-id="ce7ee-126">指定要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="ce7ee-127">有效值为</span><span class="sxs-lookup"><span data-stu-id="ce7ee-127">Valid values are</span></span><br /><br /> <span data-ttu-id="ce7ee-128">-UnicodeFffeTextEncoding： Unicode BigEndian 编码</span><span class="sxs-lookup"><span data-stu-id="ce7ee-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="ce7ee-129">-Utf16TextEncoding： Unicode 编码</span><span class="sxs-lookup"><span data-stu-id="ce7ee-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="ce7ee-130">-Utf8TextEncoding：8位编码</span><span class="sxs-lookup"><span data-stu-id="ce7ee-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="ce7ee-131">默认值为 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="ce7ee-132">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce7ee-133">子元素</span><span class="sxs-lookup"><span data-stu-id="ce7ee-133">Child Elements</span></span>  
  
|<span data-ttu-id="ce7ee-134">元素</span><span class="sxs-lookup"><span data-stu-id="ce7ee-134">Element</span></span>|<span data-ttu-id="ce7ee-135">说明</span><span class="sxs-lookup"><span data-stu-id="ce7ee-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="ce7ee-136">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="ce7ee-137">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ce7ee-138">父元素</span><span class="sxs-lookup"><span data-stu-id="ce7ee-138">Parent Elements</span></span>  
  
|<span data-ttu-id="ce7ee-139">元素</span><span class="sxs-lookup"><span data-stu-id="ce7ee-139">Element</span></span>|<span data-ttu-id="ce7ee-140">说明</span><span class="sxs-lookup"><span data-stu-id="ce7ee-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="ce7ee-141">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce7ee-142">备注</span><span class="sxs-lookup"><span data-stu-id="ce7ee-142">Remarks</span></span>  
 <span data-ttu-id="ce7ee-143">编码是将消息转换为一个字节序列的过程。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="ce7ee-144">解码是反向过程。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-144">Decoding is the reverse process.</span></span> <span data-ttu-id="ce7ee-145">Windows Communication Foundation (WCF) 包含三种类型的 SOAP 消息编码：文本、二进制和消息传输优化机制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="ce7ee-146">`MtomMessageEncoding` 元素指定使用消息传输优化机制 (MTOM) 编码的消息所用的字符编码和消息版本管理以及其他设置。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="ce7ee-147">MTOM 是一种用于在 WCF 消息中传输二进制数据的有效技术。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="ce7ee-148">MTOM 编码器会尝试在效率和互操作性之间建立平衡。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="ce7ee-149">MTOM 编码以文本形式传输大多数 XML，但通过按原样传输来优化大型二进制数据块的传输，无需将其转换为 base64 编码格式。</span><span class="sxs-lookup"><span data-stu-id="ce7ee-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce7ee-150">示例</span><span class="sxs-lookup"><span data-stu-id="ce7ee-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="ce7ee-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="ce7ee-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="ce7ee-152">消息编码</span><span class="sxs-lookup"><span data-stu-id="ce7ee-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="ce7ee-153">选择消息编码器</span><span class="sxs-lookup"><span data-stu-id="ce7ee-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="ce7ee-154">绑定</span><span class="sxs-lookup"><span data-stu-id="ce7ee-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ce7ee-155">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="ce7ee-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ce7ee-156">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="ce7ee-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
