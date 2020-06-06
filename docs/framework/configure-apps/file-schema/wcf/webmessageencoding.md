---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 4aa87acaf9080959ba8b53e3ec3216314dc745b6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732584"
---
# \<webMessageEncoding>
<span data-ttu-id="dd1d1-101">允许在 Windows Communication Foundation (WCF) 绑定中使用纯文本 XML、JavaScript 对象表示法 (JSON) 消息编码和“原始”二进制内容时对其进行读写。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-101">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="dd1d1-102">语法</span><span class="sxs-lookup"><span data-stu-id="dd1d1-102">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd1d1-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dd1d1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="dd1d1-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd1d1-105">特性</span><span class="sxs-lookup"><span data-stu-id="dd1d1-105">Attributes</span></span>  
  
|<span data-ttu-id="dd1d1-106">属性</span><span class="sxs-lookup"><span data-stu-id="dd1d1-106">Attribute</span></span>|<span data-ttu-id="dd1d1-107">说明</span><span class="sxs-lookup"><span data-stu-id="dd1d1-107">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="dd1d1-108">无需分配新的读取器便可同时读取的消息数。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-108">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="dd1d1-109">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-109">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="dd1d1-110">默认情况下将为每个内部编码器（文本、JSON 和“原始”）分配 64 个读取器。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-110">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="dd1d1-111">增大此数字将会增加内存消耗，但能够让编码器处理传入消息的突现高峰，因为编码器可以使用池中已创建的读取器，而不必创建新的读取器。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-111">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="dd1d1-112">无需分配新的编写器便可同时发送的消息数。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-112">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="dd1d1-113">池越大，系统允许的活动峰值就越大，但工作集也会随之增大。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-113">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="dd1d1-114">默认情况下将为每个内部编码器（文本、JSON 和“原始”）分配 16 个编写器。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-114">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="dd1d1-115">增大此数字将会增加内存消耗，但能够让编码器处理传出消息的突现高峰，因为编码器可以使用池中已创建的编写器，而不必创建新的编写器。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-115">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="dd1d1-116">指定要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-116">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="dd1d1-117">有效值是：</span><span class="sxs-lookup"><span data-stu-id="dd1d1-117">Valid values are:</span></span><br /><br /> <span data-ttu-id="dd1d1-118">-UnicodeFffeTextEncoding： Unicode Big Endian 编码。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-118">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="dd1d1-119">-Utf16TextEncoding： Unicode 编码。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-119">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="dd1d1-120">-Utf8TextEncoding：8位编码。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-120">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="dd1d1-121">默认值为 Utf8TextEncoding。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-121">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="dd1d1-122">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-122">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd1d1-123">子元素</span><span class="sxs-lookup"><span data-stu-id="dd1d1-123">Child Elements</span></span>  
  
|<span data-ttu-id="dd1d1-124">元素</span><span class="sxs-lookup"><span data-stu-id="dd1d1-124">Element</span></span>|<span data-ttu-id="dd1d1-125">描述</span><span class="sxs-lookup"><span data-stu-id="dd1d1-125">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="dd1d1-126">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-126">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="dd1d1-127">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-127">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd1d1-128">父元素</span><span class="sxs-lookup"><span data-stu-id="dd1d1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="dd1d1-129">元素</span><span class="sxs-lookup"><span data-stu-id="dd1d1-129">Element</span></span>|<span data-ttu-id="dd1d1-130">描述</span><span class="sxs-lookup"><span data-stu-id="dd1d1-130">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="dd1d1-131">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd1d1-132">注解</span><span class="sxs-lookup"><span data-stu-id="dd1d1-132">Remarks</span></span>  
 <span data-ttu-id="dd1d1-133">编码是将消息转换为一个字节序列的过程。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-133">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="dd1d1-134">解码是反向过程。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-134">Decoding is the reverse process.</span></span> <span data-ttu-id="dd1d1-135">这些过程都需要字符编码规范。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-135">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="dd1d1-136">`webMessageEncoding` 元素的工作方式是委托一系列内部编码器对纯文本 XML 与 JSON 编码以及“原始”二进制数据进行处理。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-136">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="dd1d1-137">委托由复合消息编码器来完成。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-137">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="dd1d1-138">在不使用 SOAP 消息（由 `webHttpBinding` 元素使用）的方案中，用该绑定元素及其复合编码器控制编码。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-138">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="dd1d1-139">这些方案包括“纯旧式 XML”(POX)、具象状态传输 (REST)、真正简单的整合 (RSS) 与 Atom 整合以及异步 JavaScript 和 XML (AJAX)。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-139">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="dd1d1-140">复合消息编码器不支持 SOAP 或 WS-Addressing。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-140">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="dd1d1-141">可以使用 `writeEncoding` 属性通过写字符编码来配置绑定元素。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-141">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="dd1d1-142">所提供的 <xref:System.Text.Encoding> 值指定 JSON 与文本 XML 情况的编写行为。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-142">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="dd1d1-143">在读取时，将理解任何有效的消息编码与文本编码。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-143">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="dd1d1-144">属性 `maxReadPoolSize` 与 `maxWritePoolSize` 也可以分别用来设置要分配的读取器和编写器最大数目。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-144">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="dd1d1-145">默认情况下，将分配 64 个读取器和 16 个编写器。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-145">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="dd1d1-146">还使用元素设置默认的复杂性约束， [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) 以防范尝试使用消息复杂性来占用终结点处理资源的拒绝服务（DOS）攻击的类。</span><span class="sxs-lookup"><span data-stu-id="dd1d1-146">Default complexity constraints are also set using the [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd1d1-147">示例</span><span class="sxs-lookup"><span data-stu-id="dd1d1-147">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="dd1d1-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd1d1-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="dd1d1-149">消息编码</span><span class="sxs-lookup"><span data-stu-id="dd1d1-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="dd1d1-150">选择消息编码器</span><span class="sxs-lookup"><span data-stu-id="dd1d1-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="dd1d1-151">绑定</span><span class="sxs-lookup"><span data-stu-id="dd1d1-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dd1d1-152">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="dd1d1-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="dd1d1-153">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="dd1d1-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
