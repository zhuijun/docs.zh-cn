---
title: 消息协议
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 69a92bfb406e2e1af3bdcbb0316711dbf531204b
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812050"
---
# <a name="messaging-protocols"></a><span data-ttu-id="379f5-102">消息协议</span><span class="sxs-lookup"><span data-stu-id="379f5-102">Messaging Protocols</span></span>

<span data-ttu-id="379f5-103">Windows Communication Foundation (WCF) 通道堆栈采用编码和传输通道，将内部消息表示形式转换为其网络格式，并使用特定传输来发送。</span><span class="sxs-lookup"><span data-stu-id="379f5-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="379f5-104">用于 Web 服务互操作性的最常见传输是 HTTP，Web 服务使用的最常见编码是基于 XML 的 SOAP 1.1、SOAP 1.2 和消息传输优化机制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="379f5-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="379f5-105">本主题介绍了使用的以下协议的 WCF 实现细节 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 。</span><span class="sxs-lookup"><span data-stu-id="379f5-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="379f5-106">规范/文档：</span><span class="sxs-lookup"><span data-stu-id="379f5-106">Specification/document:</span></span>

- [<span data-ttu-id="379f5-107">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="379f5-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="379f5-108">[SOAP 1.1 HTTP 绑定](https://www.w3.org/TR/2000/NOTE-SOAP-20000508)，第7部分</span><span class="sxs-lookup"><span data-stu-id="379f5-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="379f5-109">[SOAP 1.2 HTTP 绑定](https://www.w3.org/TR/soap12-part2) 第7部分</span><span class="sxs-lookup"><span data-stu-id="379f5-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="379f5-110">本主题介绍了和使用的以下协议的 WCF 实现细节 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> 。</span><span class="sxs-lookup"><span data-stu-id="379f5-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="379f5-111">规范/文档：</span><span class="sxs-lookup"><span data-stu-id="379f5-111">Specification/Document:</span></span>

- [<span data-ttu-id="379f5-112">XML</span><span class="sxs-lookup"><span data-stu-id="379f5-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="379f5-113">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="379f5-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="379f5-114">SOAP 1.2 核心</span><span class="sxs-lookup"><span data-stu-id="379f5-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="379f5-115">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="379f5-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="379f5-116">W3C Web 服务寻址 1.0 - 核心</span><span class="sxs-lookup"><span data-stu-id="379f5-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="379f5-117">W3C Web 服务寻址 1.0 - SOAP 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="379f5-118">W3C Web 服务寻址 1.0-WSDL 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="379f5-119">W3C Web 服务寻址 1.0 - 元数据</span><span class="sxs-lookup"><span data-stu-id="379f5-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="379f5-120">WSDL SOAP1.1 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="379f5-121">WSDL SOAP1.2 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="379f5-122">本主题介绍适用于的以下协议的 WCF 实现细节 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> 。</span><span class="sxs-lookup"><span data-stu-id="379f5-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="379f5-123">规范/文档：</span><span class="sxs-lookup"><span data-stu-id="379f5-123">Specification/document:</span></span>

- [<span data-ttu-id="379f5-124">XOP</span><span class="sxs-lookup"><span data-stu-id="379f5-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="379f5-125">MTOM + SOAP 1.2 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="379f5-126">MTOM SOAP 1.1 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="379f5-127">MTOM WS-Policy 断言</span><span class="sxs-lookup"><span data-stu-id="379f5-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="379f5-128">本主题中使用以下 XML 命名空间和关联的前缀：</span><span class="sxs-lookup"><span data-stu-id="379f5-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

| <span data-ttu-id="379f5-129">前缀</span><span class="sxs-lookup"><span data-stu-id="379f5-129">Prefix</span></span> | <span data-ttu-id="379f5-130">命名空间统一资源标识符 (URI)</span><span class="sxs-lookup"><span data-stu-id="379f5-130">Namespace Uniform Resource Identifier (URI)</span></span> |
|------------|---------------------------------------------------|
| <span data-ttu-id="379f5-131">s11</span><span class="sxs-lookup"><span data-stu-id="379f5-131">s11</span></span> | `http://schemas.xmlsoap.org/soap/envelope` |
| <span data-ttu-id="379f5-132">s12</span><span class="sxs-lookup"><span data-stu-id="379f5-132">s12</span></span> |`http://www.w3.org/2003/05/soap-envelope` |
| <span data-ttu-id="379f5-133">wsa</span><span class="sxs-lookup"><span data-stu-id="379f5-133">wsa</span></span> |`http://www.w3.org/2004/08/addressing` |
| <span data-ttu-id="379f5-134">wsam</span><span class="sxs-lookup"><span data-stu-id="379f5-134">wsam</span></span> |`http://www.w3.org/2007/05/addressing/metadata` |
| <span data-ttu-id="379f5-135">wsap</span><span class="sxs-lookup"><span data-stu-id="379f5-135">wsap</span></span> |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| <span data-ttu-id="379f5-136">wsa10</span><span class="sxs-lookup"><span data-stu-id="379f5-136">wsa10</span></span> |`http://www.w3.org/2005/08/addressing` |
| <span data-ttu-id="379f5-137">wsaw10</span><span class="sxs-lookup"><span data-stu-id="379f5-137">wsaw10</span></span> |`http://www.w3.org/2006/05/addressing/wsdl` |
| <span data-ttu-id="379f5-138">xop</span><span class="sxs-lookup"><span data-stu-id="379f5-138">xop</span></span> |`http://www.w3.org/2004/08/xop/include` |
| <span data-ttu-id="379f5-139">xmime</span><span class="sxs-lookup"><span data-stu-id="379f5-139">xmime</span></span> |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| <span data-ttu-id="379f5-140">dp</span><span class="sxs-lookup"><span data-stu-id="379f5-140">dp</span></span> |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="379f5-141">SOAP 1.1 和 SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="379f5-141">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="379f5-142">信封和处理模型</span><span class="sxs-lookup"><span data-stu-id="379f5-142">Envelope and Processing Model</span></span>
<span data-ttu-id="379f5-143">WCF 实现 SOAP 1.1 信封处理基本配置文件 1.1 (BP11) 和基本配置文件 1.0 (SSBP10) 。</span><span class="sxs-lookup"><span data-stu-id="379f5-143">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="379f5-144">SOAP 1.2 信封处理是遵循 SOAP12-Part1 实现的。</span><span class="sxs-lookup"><span data-stu-id="379f5-144">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="379f5-145">本部分介绍 WCF 与 BP11 和 SOAP12-Part1 有关的某些实现选择。</span><span class="sxs-lookup"><span data-stu-id="379f5-145">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="379f5-146">强制标头处理</span><span class="sxs-lookup"><span data-stu-id="379f5-146">Mandatory Header Processing</span></span>
<span data-ttu-id="379f5-147">WCF 遵循用于处理 `mustUnderstand` soap 1.1 和 soap 1.2 规范中所述标头的规则，具有以下变化形式。</span><span class="sxs-lookup"><span data-stu-id="379f5-147">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="379f5-148">通过关联的绑定元素配置的单个通道（例如，文本消息编码、安全性、可靠消息传递和事务）处理进入 WCF 信道堆栈的消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-148">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="379f5-149">每个通道都识别来自关联命名空间的标头，并将其标记为已理解。</span><span class="sxs-lookup"><span data-stu-id="379f5-149">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="379f5-150">消息进入调度程序后，操作格式化程序读取相应消息/操作协定所期望的标头，并将其标记为已理解。</span><span class="sxs-lookup"><span data-stu-id="379f5-150">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="379f5-151">然后，调度程序验证是否还有任何标头未被理解，但仍标记为 `mustUnderstand`，如果是这样，则引发异常。</span><span class="sxs-lookup"><span data-stu-id="379f5-151">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="379f5-152">包含 `mustUnderstand` 标头并且目标为接收方的消息不会由接收方应用程序代码进行处理。</span><span class="sxs-lookup"><span data-stu-id="379f5-152">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="379f5-153">这样的分层处理实现了 SOAP 节点的基础结构层和应用层之间的分离。</span><span class="sxs-lookup"><span data-stu-id="379f5-153">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="379f5-154">B1111：在 WCF 基础结构通道堆栈处理消息之后但在应用程序处理之前，检测不到的标头</span><span class="sxs-lookup"><span data-stu-id="379f5-154">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="379f5-155">在 SOAP 1.1 和 SOAP 1.2 中，`mustUnderstand` 标头值不相同。</span><span class="sxs-lookup"><span data-stu-id="379f5-155">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="379f5-156">Basic Profile 1.1 要求，在 SOAP 1.1 消息中，`mustUnderstand` 值为 0 或 1。</span><span class="sxs-lookup"><span data-stu-id="379f5-156">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="379f5-157">SOAP 1.2 可以使用 0、1、`false` 和 `true` 作为值，但建议使用 `xs:boolean` 值的规范表示形式（`false` 和 `true`）。</span><span class="sxs-lookup"><span data-stu-id="379f5-157">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="379f5-158">B1112：对于 soap `mustUnderstand` 1.1 和 soap 1.2 版本的 soap 信封，WCF 将发出值0和1。</span><span class="sxs-lookup"><span data-stu-id="379f5-158">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="379f5-159">WCF 将接受标头的整个值空间 `xs:boolean` `mustUnderstand` (0、1、 `false` `true`) </span><span class="sxs-lookup"><span data-stu-id="379f5-159">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="379f5-160">SOAP 错误</span><span class="sxs-lookup"><span data-stu-id="379f5-160">SOAP Faults</span></span>
<span data-ttu-id="379f5-161">下面是特定于 WCF 的 SOAP 错误实现的列表。</span><span class="sxs-lookup"><span data-stu-id="379f5-161">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="379f5-162">B2121： WCF 返回以下 SOAP 1.1 错误代码： `s11:mustUnderstand` 、 `s11:Client` 和 `s11:Server` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-162">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="379f5-163">B2122： WCF 返回以下 SOAP 1.2 错误代码： `s12:MustUnderstand` 、 `s12:Sender` 和 `s12:Receiver` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-163">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="379f5-164">HTTP 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-164">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="379f5-165">SOAP 1.1 HTTP 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-165">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="379f5-166">WCF 在基本配置文件1.1 规范第3.4 节后实现 SOAP 1.1 HTTP 绑定，并提供以下说明：</span><span class="sxs-lookup"><span data-stu-id="379f5-166">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="379f5-167">B2211： WCF 服务不实现 HTTP POST 请求的重定向。</span><span class="sxs-lookup"><span data-stu-id="379f5-167">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="379f5-168">B2212： WCF 客户端根据3.4.8 支持 HTTP Cookie。</span><span class="sxs-lookup"><span data-stu-id="379f5-168">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="379f5-169">SOAP 1.2 HTTP 绑定</span><span class="sxs-lookup"><span data-stu-id="379f5-169">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="379f5-170">WCF 实现 SOAP 1.2 HTTP 绑定，如 SOAP 1.2-第2部分 (SOAP12Part2) 规范中所述，其中包含以下说明。</span><span class="sxs-lookup"><span data-stu-id="379f5-170">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="379f5-171">SOAP 1.2 为 `application/soap+xml` 媒体类型提供了一个可选的操作参数。</span><span class="sxs-lookup"><span data-stu-id="379f5-171">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="379f5-172">在未使用 WS-Addressing 时，采用此参数优化消息调度很有用，这种情况下，不需要分析 SOAP 消息的正文。</span><span class="sxs-lookup"><span data-stu-id="379f5-172">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="379f5-173">R2221：`application/soap+xml` 操作参数出现在 SOAP 1.2 请求中时，必须与相应 WSDL 绑定内的 `soapAction` 元素的 `wsoap12:operation` 属性匹配。</span><span class="sxs-lookup"><span data-stu-id="379f5-173">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="379f5-174">R2222：如果使用 WS-Addressing 2004/08 或 WS-Addressing 1.0，`application/soap+xml` 操作参数出现在 SOAP 1.2 消息中时，必须与 `wsa:Action` 匹配。</span><span class="sxs-lookup"><span data-stu-id="379f5-174">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="379f5-175">如果 WS-Addressing 禁用，并且传入的请求不包含操作参数，则视为未指定消息 `Action`。</span><span class="sxs-lookup"><span data-stu-id="379f5-175">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="379f5-176">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="379f5-176">WS-Addressing</span></span>
<span data-ttu-id="379f5-177">WCF 实现了 WS-ADDRESSING 的3个版本：</span><span class="sxs-lookup"><span data-stu-id="379f5-177">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="379f5-178">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="379f5-178">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="379f5-179">W3C Web 服务寻址 1.0 核心 (ADDR10-CORE) 和 SOAP 绑定 (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="379f5-179">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="379f5-180">WS-Addressing 1.0 - 元数据</span><span class="sxs-lookup"><span data-stu-id="379f5-180">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="379f5-181">终结点引用</span><span class="sxs-lookup"><span data-stu-id="379f5-181">Endpoint References</span></span>
<span data-ttu-id="379f5-182">WCF 实现的所有 WS-ADDRESSING 版本都使用终结点引用来描述终结点。</span><span class="sxs-lookup"><span data-stu-id="379f5-182">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="379f5-183">终结点引用和 WS-Addressing 版本</span><span class="sxs-lookup"><span data-stu-id="379f5-183">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="379f5-184">WCF 实现了许多基础结构协议，它们使用 WS-ADDRESSING，尤其是 `EndpointReference` 元素和 `W3C.WsAddressing.EndpointReferenceType` 类 (例如，Ws-reliablemessaging、WS-SECURECONVERSATION 和 ws-trust) 。</span><span class="sxs-lookup"><span data-stu-id="379f5-184">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="379f5-185">WCF 支持将 WS-ADDRESSING 的任一版本与其他基础结构协议一起使用。</span><span class="sxs-lookup"><span data-stu-id="379f5-185">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="379f5-186">WCF 端点支持每个端点有一个 WS-ADDRESSING 版本。</span><span class="sxs-lookup"><span data-stu-id="379f5-186">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="379f5-187">对于 R3111， `EndpointReference` 与 WCF 终结点交换的消息中所使用的元素或类型的命名空间必须与此终结点实现的 ws-addressing 的版本匹配。</span><span class="sxs-lookup"><span data-stu-id="379f5-187">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="379f5-188">例如，如果 WCF 终结点实现了 WS-RELIABLEMESSAGING，则中的 `AcksTo` 此类终结点返回的标头将 `CreateSequenceResponse` 使用 `EncodingBinding` 元素为此终结点指定的 ws-addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="379f5-188">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="379f5-189">终结点引用和元数据</span><span class="sxs-lookup"><span data-stu-id="379f5-189">Endpoint References and Metadata</span></span>
<span data-ttu-id="379f5-190">很多情况下，需要对给定终结点进行元数据或元数据引用通信。</span><span class="sxs-lookup"><span data-stu-id="379f5-190">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="379f5-191">B3121： WCF 使用 Ws-metadataexchange (MEX 中描述的机制) 规范第6部分，按值或按引用包含终结点引用的元数据。</span><span class="sxs-lookup"><span data-stu-id="379f5-191">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="379f5-192">请考虑这样一种情况： WCF 服务需要使用安全断言标记语言进行身份验证， (SAML) 令牌颁发者颁发的令牌颁发者 `http://sts.fabrikam123.com` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-192">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="379f5-193">WCF 终结点通过 `sp:IssuedToken` 将断言与 `sp:Issuer` 指向令牌颁发者的嵌套断言结合使用来描述此身份验证要求。</span><span class="sxs-lookup"><span data-stu-id="379f5-193">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="379f5-194">访问该 `sp:Issuer` 断言的客户端应用程序需要知道如何与令牌颁发机构终结点进行通信。</span><span class="sxs-lookup"><span data-stu-id="379f5-194">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="379f5-195">客户端需要知道令牌颁发机构的有关元数据。</span><span class="sxs-lookup"><span data-stu-id="379f5-195">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="379f5-196">使用在 MEX 中定义的终结点引用元数据扩展，WCF 提供对令牌颁发者元数据的引用。</span><span class="sxs-lookup"><span data-stu-id="379f5-196">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a><span data-ttu-id="379f5-197">消息寻址标头</span><span class="sxs-lookup"><span data-stu-id="379f5-197">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="379f5-198">消息头</span><span class="sxs-lookup"><span data-stu-id="379f5-198">Message Headers</span></span>
<span data-ttu-id="379f5-199">对于这两个 ws-addressing 版本，WCF 使用规范、、、和规定的以下消息标头 `wsa:To` `wsa:ReplyTo` `wsa:Action` `wsa:MessageID` `wsa:RelatesTo` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-199">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="379f5-200">B3211：对于所有 WS-ADDRESSING 版本，WCF 将接受，但不会生成现成的 WS-ADDRESSING 消息头 `wsa:FaultTo` 和 `wsa:From` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-200">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="379f5-201">与 WCF 应用程序交互的应用程序可以添加这些消息标头，WCF 将相应地对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="379f5-201">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="379f5-202">引用参数和属性</span><span class="sxs-lookup"><span data-stu-id="379f5-202">Reference Parameters and Properties</span></span>

<span data-ttu-id="379f5-203">WCF 根据相应规范实现终结点引用参数和引用属性的处理。</span><span class="sxs-lookup"><span data-stu-id="379f5-203">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="379f5-204">B3221：配置为使用 WS-ADDRESSING 2004/08 时，WCF 终结点不区分处理引用属性和引用参数。</span><span class="sxs-lookup"><span data-stu-id="379f5-204">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="379f5-205">消息交换模式</span><span class="sxs-lookup"><span data-stu-id="379f5-205">Message Exchange Patterns</span></span>
<span data-ttu-id="379f5-206">Web 服务操作调用所涉及的消息序列称为 " *消息交换模式*"。</span><span class="sxs-lookup"><span data-stu-id="379f5-206">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="379f5-207">WCF 支持单向、请求-答复和双工消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="379f5-207">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="379f5-208">本节根据所用的消息交换模式说明 WS-Addressing 对消息处理的需求。</span><span class="sxs-lookup"><span data-stu-id="379f5-208">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="379f5-209">本节通篇都是由请求方发送第一条消息，响应方接收第一条消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-209">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="379f5-210">单向消息</span><span class="sxs-lookup"><span data-stu-id="379f5-210">One-Way Message</span></span>
<span data-ttu-id="379f5-211">当 WCF 终结点配置为支持具有给定的消息 `Action` 遵循单向模式时，wcf 终结点将遵循以下行为和要求。</span><span class="sxs-lookup"><span data-stu-id="379f5-211">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="379f5-212">除非另行指定，否则行为和规则适用于 WCF 中支持的两个版本的 WS-ADDRESSING：</span><span class="sxs-lookup"><span data-stu-id="379f5-212">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="379f5-213">R3311：请求方必须包含 `wsa:To`、`wsa:Action` 以及表示终结点引用所指定的所有引用参数的标头。</span><span class="sxs-lookup"><span data-stu-id="379f5-213">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="379f5-214">如果使用 WS-Addressing 2004/08 并且终结点引用指定了 [reference properties]，则对应的标头必须也添加到消息中。</span><span class="sxs-lookup"><span data-stu-id="379f5-214">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="379f5-215">B3312：请求方可以包含 `MessageID`、`ReplyTo` 和 `FaultTo` 标头。</span><span class="sxs-lookup"><span data-stu-id="379f5-215">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="379f5-216">接收方基础结构将忽略这些标头，并且这些标头将传给应用程序。</span><span class="sxs-lookup"><span data-stu-id="379f5-216">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="379f5-217">R3313：在使用 HTTP 并且没有通过 HTTP 响应发送任何消息时，响应方必须发送一个正文为空且 HTTP 状态码为 202 的 HTTP 响应。</span><span class="sxs-lookup"><span data-stu-id="379f5-217">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="379f5-218">如果使用的是 HTTP 传输，并且操作协定声明消息是单向的，则 HTTP 响应仍可用于发送基础结构消息 — 例如，可靠消息传递可通过 HTTP 响应发送 `SequenceAcknowledgement` 消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-218">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="379f5-219">B3314： WCF 响应方不会发送错误消息来响应单向消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-219">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="379f5-220">请求-答复</span><span class="sxs-lookup"><span data-stu-id="379f5-220">Request-Reply</span></span>
<span data-ttu-id="379f5-221">如果为具有给定的消息配置了 WCF 终结点 `Action` 以遵循请求-答复模式，则 wcf 终结点将遵循下面的行为和要求。</span><span class="sxs-lookup"><span data-stu-id="379f5-221">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="379f5-222">除非另外指定，否则行为和规则适用于 WCF 中支持的两个版本的 WS-ADDRESSING：</span><span class="sxs-lookup"><span data-stu-id="379f5-222">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="379f5-223">R3321：请求者必须在请求中包含 `wsa:To` `wsa:Action` `wsa:MessageID` 所有引用参数或引用属性的请求、、和标头，或由终结点引用所指定的)  (。</span><span class="sxs-lookup"><span data-stu-id="379f5-223">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="379f5-224">R3322：使用 WS-Addressing 2004/08 时，还必须在请求中包含 `ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="379f5-224">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="379f5-225">R3323：使用 WS-ADDRESSING 1.0 时 `ReplyTo` ，如果请求中不存在该地址，则使用具有等于的 [address] 属性的默认终结点引用 `http://www.w3.org/2005/08/addressing/anonymous` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-225">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="379f5-226">R3324：请求 `wsa:To` `wsa:Action` 者必须 `wsa:RelatesTo` 在答复消息中包含、和标头，以及所有引用参数或引用属性的标头 (或 `ReplyTo` 请求中的终结点引用所指定的) 。</span><span class="sxs-lookup"><span data-stu-id="379f5-226">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="379f5-227">Web 服务寻址错误</span><span class="sxs-lookup"><span data-stu-id="379f5-227">Web Services Addressing Faults</span></span>
<span data-ttu-id="379f5-228">R3411： WCF 生成由 WS-ADDRESSING 2004/08 定义的以下错误。</span><span class="sxs-lookup"><span data-stu-id="379f5-228">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

| <span data-ttu-id="379f5-229">代码</span><span class="sxs-lookup"><span data-stu-id="379f5-229">Code</span></span> | <span data-ttu-id="379f5-230">原因</span><span class="sxs-lookup"><span data-stu-id="379f5-230">Cause</span></span> |
|----------|-----------|
| `wsa:DestinationUnreachable` | <span data-ttu-id="379f5-231">到达的消息所带有的 `ReplyTo` 不同于为此通道建立的答复地址；在 To 标头中指定的地址上，没有终结点在进行侦听。</span><span class="sxs-lookup"><span data-stu-id="379f5-231">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa:ActionNotSupported` | <span data-ttu-id="379f5-232">与终结点关联的基础结构通道或调度程序不能识别在 `Action` 标头中指定的操作。</span><span class="sxs-lookup"><span data-stu-id="379f5-232">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span> |

<span data-ttu-id="379f5-233">R3412： WCF 生成由 WS-ADDRESSING 1.0 定义的以下错误。</span><span class="sxs-lookup"><span data-stu-id="379f5-233">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

| <span data-ttu-id="379f5-234">代码</span><span class="sxs-lookup"><span data-stu-id="379f5-234">Code</span></span> | <span data-ttu-id="379f5-235">原因</span><span class="sxs-lookup"><span data-stu-id="379f5-235">Cause</span></span> |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | <span data-ttu-id="379f5-236">重复 `wsa:To` 的 `wsa:ReplyTo` 、 `wsa:From` 或 `wsa:MessageID` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-236">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="379f5-237">`wsa:RelatesTo`用相同的重复 `RelationshipType` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-237">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span> |
| `wsa10:MessageAddressingHeaderRequired` | <span data-ttu-id="379f5-238">缺少必需的 Addressing 标头。</span><span class="sxs-lookup"><span data-stu-id="379f5-238">The required Addressing header is missing.</span></span> |
| `wsa10:DestinationUnreachable` | <span data-ttu-id="379f5-239">到达的消息所带有的 `ReplyTo` 不同于为此通道建立的答复地址。</span><span class="sxs-lookup"><span data-stu-id="379f5-239">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="379f5-240">在 To 标头中指定的地址上没有终结点在进行侦听。</span><span class="sxs-lookup"><span data-stu-id="379f5-240">There is no endpoint listening at the address specified in the To header.</span></span> |
| `wsa10:ActionNotSupported` | <span data-ttu-id="379f5-241">与终结点关联的基础结构通道或调度程序不能识别在 `Action` 标头中指定的操作。</span><span class="sxs-lookup"><span data-stu-id="379f5-241">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span> |
| `wsa10:EndpointUnavailable` | <span data-ttu-id="379f5-242">RM 通道发送回此错误，指示终结点将不会根据对 `CreateSequence` 消息的寻址标头的检查结果来处理序列。</span><span class="sxs-lookup"><span data-stu-id="379f5-242">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span> |

<span data-ttu-id="379f5-243">上表中的代码对应于 SOAP 1.1 中的 `FaultCode` 和 SOAP 1.2 中的 `SubCode` (Code=Sender)。</span><span class="sxs-lookup"><span data-stu-id="379f5-243">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="379f5-244">WSDL 1.1 绑定和 WS-Policy 断言</span><span class="sxs-lookup"><span data-stu-id="379f5-244">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="379f5-245">指示使用 WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="379f5-245">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="379f5-246">WCF 使用策略断言来指示终结点对特定 WS-ADDRESSING 版本的支持。</span><span class="sxs-lookup"><span data-stu-id="379f5-246">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="379f5-247">下面的策略断言具有终结点策略主题 [WS-PA]，并指示从终结点收发的消息必须使用 WS-Addressing 2004/08。</span><span class="sxs-lookup"><span data-stu-id="379f5-247">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="379f5-248">此策略断言扩充了 WS-Addressing 2004/08 规范。</span><span class="sxs-lookup"><span data-stu-id="379f5-248">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="379f5-249">下面的策略断言指示发送/接收的消息必须使用 WS-Addressing 1.0。</span><span class="sxs-lookup"><span data-stu-id="379f5-249">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="379f5-250">下面的策略断言具有终结点策略主题 [WS-PA]，并指示从终结点收发的消息必须使用 WS-Addressing 2004/08。</span><span class="sxs-lookup"><span data-stu-id="379f5-250">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="379f5-251">`wsaw10:UsingAddressing` 元素借自于 [WS-Addressing-WSDL]，并在符合该规范第 3.1.2 节的 WS-Policy 的上下文中使用。</span><span class="sxs-lookup"><span data-stu-id="379f5-251">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="379f5-252">使用 Addressing 不会更改 WSDL 1.1、SOAP 1.1 和 SOAP 1.2 HTTP 绑定的语义。</span><span class="sxs-lookup"><span data-stu-id="379f5-252">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="379f5-253">例如，如果某个请求发送到使用 Addressing 和 WSDL SOAP 1.x HTTP 绑定的终结点，并且该请求期望得到一个答复，则该答复必须用 HTTP 响应发送。</span><span class="sxs-lookup"><span data-stu-id="379f5-253">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="379f5-254">对于通过 http 响应发送的答复，WS-AM 断言是：</span><span class="sxs-lookup"><span data-stu-id="379f5-254">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="379f5-255">完整的策略断言可能类似于：</span><span class="sxs-lookup"><span data-stu-id="379f5-255">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="379f5-256">但是，有些消息交换模式可以从在请求方和响应方之间建立两个独立的反向 HTTP 连接中获益，例如，由响应方发送的主动单向消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-256">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="379f5-257">WCF 提供一项功能，通过该功能，两个基础传输通道可构成一个复合双工通道，其中一个通道用于输入消息，另一个用于输出消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-257">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="379f5-258">对于 HTTP 传输，复合双工提供了两个反向 HTTP 连接。</span><span class="sxs-lookup"><span data-stu-id="379f5-258">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="379f5-259">请求方使用一个连接将消息发送到响应方，而响应方使用另一个连接将消息发送回请求方。</span><span class="sxs-lookup"><span data-stu-id="379f5-259">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="379f5-260">对于通过单独的 http 请求发送的答复，ws-am 断言是：</span><span class="sxs-lookup"><span data-stu-id="379f5-260">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="379f5-261">完整的策略断言可能类似于：</span><span class="sxs-lookup"><span data-stu-id="379f5-261">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="379f5-262">在使用 WSDL 1.1 SOAP 1.x HTTP 绑定的终结点上，如果要使用以下具有终结点策略主题 [WS-PA] 的断言，要求将两个单独的反向 HTTP 连接分别用于从请求方到响应方以及从响应方到请求方传送消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-262">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="379f5-263">上面的陈述对于请求消息的 `wsa:ReplyTo` 标头提出了以下要求：</span><span class="sxs-lookup"><span data-stu-id="379f5-263">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="379f5-264">R3514： `ReplyTo` `[address]` `http://www.w3.org/2005/08/addressing/anonymous` 如果终结点使用 WSDL 1.1 SOAP 1.x HTTP 绑定，并且具有与 `wsap10:UsingAddressing` 附加的 or 断言耦合的策略替代 `wsap:UsingAddressing` `cdp:CompositeDuplex` 项，则发送到终结点的请求消息必须有一个标头，其属性不等于。</span><span class="sxs-lookup"><span data-stu-id="379f5-264">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="379f5-265">R3515：发送到终结点的请求消息必须有一个 `ReplyTo` 标头 `[address]` ，其属性等于 `http://www.w3.org/2005/08/addressing/anonymous` ，或者根本没有 `ReplyTo` 标头，前提是该终结点使用 WSDL 1.1 SOAP 1.x HTTP 绑定，并且具有具有断言的策略替代项 `wsap10:UsingAddressing` 并且未 `cdp:CompositeDuplex` 附加断言。</span><span class="sxs-lookup"><span data-stu-id="379f5-265">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="379f5-266">R3516：发送到终结点的请求消息必须有一个 `ReplyTo` 标头，其 `[address]` 属性等于， `http://www.w3.org/2005/08/addressing/anonymous` 如果终结点使用 WSDL 1.1 SOAP 1.x HTTP 绑定，并且有一个带有断言的策略替代项 `wsap:UsingAddressing` ，且未 `cdp:CompositeDuplex` 附加断言。</span><span class="sxs-lookup"><span data-stu-id="379f5-266">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="379f5-267">WS-addressing WSDL 规范力图描述类似协议绑定，它引入了一个带有 3 个文本值（required、optional 和 prohibited）的 `<wsaw:Anonymous/>` 元素来指示对 `wsa:ReplyTo` 标头的需求（第 3.2 节）。</span><span class="sxs-lookup"><span data-stu-id="379f5-267">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="379f5-268">遗憾的是，在 WS-Policy 的上下文中，这样的元素定义不特别适合用作断言，因为它要求使用特定于域的扩展来支持将此类元素用作断言的备选项的交集。</span><span class="sxs-lookup"><span data-stu-id="379f5-268">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="379f5-269">这样的元素定义还指示 `ReplyTo` 标头的值在传输时与终结点行为相反，这使它只能特定于 HTTP 传输。</span><span class="sxs-lookup"><span data-stu-id="379f5-269">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="379f5-270">操作定义</span><span class="sxs-lookup"><span data-stu-id="379f5-270">Action Definition</span></span>
<span data-ttu-id="379f5-271">WS-Addressing 2004/08 为 `wsa:Action` 元素定义了一个 `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` 属性。</span><span class="sxs-lookup"><span data-stu-id="379f5-271">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="379f5-272">WS-Addressing 1.0 WSDL 绑定 (WS-ADDR10-WSDL) 定义了一个类似属性 `wsaw10:Action`。</span><span class="sxs-lookup"><span data-stu-id="379f5-272">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="379f5-273">两者之间唯一的区别在于默认 Action 模式语义（分别在 WS-ADDR 第 3.3.2 节和 WS-ADDR10-WSDL 第 4.4.4 节描述）。</span><span class="sxs-lookup"><span data-stu-id="379f5-273">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="379f5-274">`portType`在 WCF 术语) 但使用不同版本的 ws-addressing 时，有两个终结点共享相同的 (或协定是合理的。</span><span class="sxs-lookup"><span data-stu-id="379f5-274">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="379f5-275">但是，如果 Action 是由 `portType` 定义的，并且在实现该 `portType` 的终结点之间不应更改，则不可能同时支持这两种默认操作模式。</span><span class="sxs-lookup"><span data-stu-id="379f5-275">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="379f5-276">为了解决此矛盾，WCF 支持单一版本的 `Action` 属性。</span><span class="sxs-lookup"><span data-stu-id="379f5-276">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="379f5-277">B3521： WCF 使用 `wsaw10:Action` `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` WS-ADDR10-WSDL-WSDL 中定义的元素上的属性来确定相应消息的 URI，而不 `Action` 考虑终结点使用的 ws-addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="379f5-277">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="379f5-278">在 WSDL 端口内使用终结点引用</span><span class="sxs-lookup"><span data-stu-id="379f5-278">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="379f5-279">WS-ADDR10-WSDL 4.1 节扩展了 `wsdl:port` 元素以包含 `<wsa10:EndpointReference…/>` 子元素，从而以 WS-Addressing 方式描述终结点。</span><span class="sxs-lookup"><span data-stu-id="379f5-279">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="379f5-280">WCF 将此实用程序扩展到 WS-ADDRESSING 2004/08，允许 `<wsa:EndpointReference…/>` 显示为的子元素 `wsdl:port` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-280">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="379f5-281">R3531：如果终结点有一个带有 `<wsaw10:UsingAddressing/>``wsdl:port`。</span><span class="sxs-lookup"><span data-stu-id="379f5-281">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="379f5-282">R3532：如果 `wsdl:port` 包含一个子元素 `<wsa10:EndpointReference …/>` ，则 `wsa10:EndpointReference/wsa10:Address` 子元素的值必须与同级元素的属性的值匹配 `@address` `wsdl:port` / `wsdl:location` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-282">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="379f5-283">R3533：如果终结点有一个带有 `<wsap:UsingAddressing/>``wsdl:port`。</span><span class="sxs-lookup"><span data-stu-id="379f5-283">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="379f5-284">R3534：如果 `wsdl:port` 包含一个子元素 `<wsa:EndpointReference …/>` ，则 `wsa:EndpointReference/wsa:Address` 子元素的值必须与同级元素的属性的值匹配 `@address` `wsdl:port` / `wsdl:location` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-284">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="379f5-285">与 WS-Security 的结合</span><span class="sxs-lookup"><span data-stu-id="379f5-285">Composition with WS-Security</span></span>
<span data-ttu-id="379f5-286">根据 WS-ADDR 和 WS-ADDR10 中的安全注意事项章节，建议将所有寻址消息头和消息正文一起签名，以便将它们绑定在一起。</span><span class="sxs-lookup"><span data-stu-id="379f5-286">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="379f5-287">当 WS-Security 用于消息完整性保护时，WS-Addressing 消息头和从引用参数或/和属性产生的标头必须与消息正文一起签名。</span><span class="sxs-lookup"><span data-stu-id="379f5-287">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="379f5-288">示例</span><span class="sxs-lookup"><span data-stu-id="379f5-288">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="379f5-289">单向消息</span><span class="sxs-lookup"><span data-stu-id="379f5-289">One-Way Message</span></span>
<span data-ttu-id="379f5-290">在此方案中，发送方向接收方发出单向消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-290">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="379f5-291">使用 SOAP 1.2、HTTP 1.1 和 W3C WS-Addressing 1.0。</span><span class="sxs-lookup"><span data-stu-id="379f5-291">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="379f5-292">请求消息结构：消息头包含 `wsa10:To` 和 `wsa10:Action` 元素。</span><span class="sxs-lookup"><span data-stu-id="379f5-292">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="379f5-293">消息正文包含来自应用程序命名空间的一个特定 `<app:Ping>` 元素。</span><span class="sxs-lookup"><span data-stu-id="379f5-293">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="379f5-294">HTTP 标头： POST 中的目标与元素中的 URI 匹配 `wsa10:To` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-294">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="379f5-295">按照 SOAP 1.2 的要求，Content-Type 标头的值为 `application/soap+xml`。</span><span class="sxs-lookup"><span data-stu-id="379f5-295">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="379f5-296">此外，还包含参数 `charset` 和 `action`。</span><span class="sxs-lookup"><span data-stu-id="379f5-296">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="379f5-297">Content-Type 标头的 `action` 参数与 `wsa10:Action` 消息头的值匹配。</span><span class="sxs-lookup"><span data-stu-id="379f5-297">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

```http
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

<span data-ttu-id="379f5-298">接收方以一个状态为 202 的空 HTTP 响应进行回应。</span><span class="sxs-lookup"><span data-stu-id="379f5-298">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="379f5-299">HTTP 响应的一个示例为：</span><span class="sxs-lookup"><span data-stu-id="379f5-299">An example of the HTTP response:</span></span>

```http
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="379f5-300">SOAP Message Transmission Optimization Mechanism（SOAP 消息传输优化机制）</span><span class="sxs-lookup"><span data-stu-id="379f5-300">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="379f5-301">本部分介绍 HTTP SOAP MTOM 的 WCF 实现细节。</span><span class="sxs-lookup"><span data-stu-id="379f5-301">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="379f5-302">MTOM 技术是与传统文本/XML 编码或 WCF 二进制编码相同的类的 SOAP 消息编码机制。</span><span class="sxs-lookup"><span data-stu-id="379f5-302">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="379f5-303">MTOM 包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="379f5-303">MTOM includes the following:</span></span>

- <span data-ttu-id="379f5-304">[XOP] 描述的 XML 编码和打包机制，用于将包含 base64 编码的二进制数据的 XML 信息项优化为多个独立的二进制部分。</span><span class="sxs-lookup"><span data-stu-id="379f5-304">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="379f5-305">XOP 包的 MIME 封装，用于将 XML Infoset 和 XOP 包的每一个二进制部分序列化为单独的 MIME 部分。</span><span class="sxs-lookup"><span data-stu-id="379f5-305">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="379f5-306">应用于 SOAP 1.x 信封的 MIME XOP 编码。</span><span class="sxs-lookup"><span data-stu-id="379f5-306">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="379f5-307">HTTP 传输绑定。</span><span class="sxs-lookup"><span data-stu-id="379f5-307">An HTTP transport binding.</span></span>

<span data-ttu-id="379f5-308">可以通过 WCF 将 MTOM 与非 HTTP 传输一起使用。</span><span class="sxs-lookup"><span data-stu-id="379f5-308">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="379f5-309">不过，在本主题中，我们将着重讨论 HTTP 上的应用。</span><span class="sxs-lookup"><span data-stu-id="379f5-309">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="379f5-310">MTOM 格式利用了包含 MTOM 本身、XOP 以及 MIME 在内的大型规范集。</span><span class="sxs-lookup"><span data-stu-id="379f5-310">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="379f5-311">在某种程度上，此规范集的模块性使得重新构造格式和处理语义的确切需求变得有点困难。</span><span class="sxs-lookup"><span data-stu-id="379f5-311">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="379f5-312">本节介绍 MTOM HTTP 绑定的格式和处理需求。</span><span class="sxs-lookup"><span data-stu-id="379f5-312">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="379f5-313">MTOM 消息编码</span><span class="sxs-lookup"><span data-stu-id="379f5-313">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="379f5-314">生成 MTOM 消息</span><span class="sxs-lookup"><span data-stu-id="379f5-314">Generating MTOM messages</span></span>
<span data-ttu-id="379f5-315">[XOP] 第 3.1 节描述了将具有元素信息项（包含 base64 值）的 XML 编码为抽象定义的 XOP 包的过程。</span><span class="sxs-lookup"><span data-stu-id="379f5-315">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="379f5-316">下面的一系列步骤描述了特定于 MTOM 的编码过程：</span><span class="sxs-lookup"><span data-stu-id="379f5-316">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="379f5-317">确保要编码的 SOAP 信封不包含具有的和的元素信息项 `[namespace name]` `http://www.w3.org/2004/08/xop/include` `[local name]` `Include` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-317">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="379f5-318">创建一个空 MIME 包。</span><span class="sxs-lookup"><span data-stu-id="379f5-318">Create an empty MIME package.</span></span>

3. <span data-ttu-id="379f5-319">在原始 XML Infoset 中标识要优化的元素信息项。</span><span class="sxs-lookup"><span data-stu-id="379f5-319">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="379f5-320">对于要优化的项，组成 `[children]` 元素信息项的字符必须采用规范形式 `xs:base64Binary` (请参阅 3.2.16 base64Binary) ，并不能包含前面、以内联的任何空白字符，或遵循非空白的内容。）</span><span class="sxs-lookup"><span data-stu-id="379f5-320">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="379f5-321">创建一个是原始 SOAP 信封副本的 XOP SOAP 信封，但是，在上一步中标识的每个元素信息项的 children 都替换为如下构造的 `xop:Include` 元素信息项：</span><span class="sxs-lookup"><span data-stu-id="379f5-321">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="379f5-322">通过将被替换字符处理为 base64 编码的数据，将其转换为二进制数据。</span><span class="sxs-lookup"><span data-stu-id="379f5-322">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="379f5-323">生成一个符合 R3133 和 R3134 需求的唯一 Content-ID 标头值。</span><span class="sxs-lookup"><span data-stu-id="379f5-323">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="379f5-324">生成一个具有二进制值的 Content-Transfer-Encoding MIME 标头。</span><span class="sxs-lookup"><span data-stu-id="379f5-324">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="379f5-325">如果要优化的元素信息项（新插入的 `xop:Include` 元素信息项的 [parent]）有一个 `xmime:contentType` 属性信息项，则生成一个带有 `xmime:contentType` 属性的值的 Content-Type MIME 标头。</span><span class="sxs-lookup"><span data-stu-id="379f5-325">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="379f5-326">生成一个新的二进制 MIME 部分，其内容由以下几项组成：从处理为 base64 的被替换数据解码的二进制数据、4b 中的 Content-ID、4c 中的 Content- Transfer-Encoding 标头，以及 Content-Type 标头（如果在步骤 4d 中生成）。</span><span class="sxs-lookup"><span data-stu-id="379f5-326">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="379f5-327">将一个 `href` 属性添加到 `xop:Include` 元素，其值为从 Content-ID 标头值（在步骤 4b 中生成）派生的 cid: uri。</span><span class="sxs-lookup"><span data-stu-id="379f5-327">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="379f5-328">删除包含 " \<" and "> " 字符，对剩余的字符串进行 URL 转义，然后添加前缀 `cid:` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-328">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="379f5-329">以下最小字符集需要根据 RFC1738 和 RFC2396 进行转义。</span><span class="sxs-lookup"><span data-stu-id="379f5-329">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="379f5-330">其他字符也可转义。</span><span class="sxs-lookup"><span data-stu-id="379f5-330">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="379f5-331">用步骤 4 中的 XOP SOAP 信封创建一个根 MIME 部分。</span><span class="sxs-lookup"><span data-stu-id="379f5-331">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="379f5-332">写入 HTTP 标头，包括 HTTP Content-Type 标头。</span><span class="sxs-lookup"><span data-stu-id="379f5-332">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="379f5-333">写入 MIME 包。</span><span class="sxs-lookup"><span data-stu-id="379f5-333">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="379f5-334">处理 MTOM 消息</span><span class="sxs-lookup"><span data-stu-id="379f5-334">Processing MTOM messages</span></span>
<span data-ttu-id="379f5-335">处理 MTOM 消息的过程与前面“生成 MTOM 消息”一节中所述的过程完全相反：</span><span class="sxs-lookup"><span data-stu-id="379f5-335">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="379f5-336">确保根 MIME 部分有 Content-Type `application/xop+xml`。</span><span class="sxs-lookup"><span data-stu-id="379f5-336">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="379f5-337">通过将包的根 MIME 部分作为 XML 文档进行分析，构造一个 SOAP 信封。</span><span class="sxs-lookup"><span data-stu-id="379f5-337">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="379f5-338">字符编码由根 MIME 部分的 Content-Type 的 `charset` 参数确定。</span><span class="sxs-lookup"><span data-stu-id="379f5-338">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="379f5-339">对于构造的 SOAP 信封中的每个元素信息项（有一个 `xop:Include` 元素信息项作为其 [children] 属性的唯一成员）：</span><span class="sxs-lookup"><span data-stu-id="379f5-339">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="379f5-340">移除 `cid:` 前缀，取消转义 `@href` 元素的 `xop:Include` 属性的值中所有 URI 转义序列 (RFC 2396)。</span><span class="sxs-lookup"><span data-stu-id="379f5-340">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="379f5-341">将结果字符串括在 " \<", "> " 中。</span><span class="sxs-lookup"><span data-stu-id="379f5-341">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="379f5-342">找到 Content-ID 标头值与步骤 3a 中派生的字符串匹配的 MIME 部分。</span><span class="sxs-lookup"><span data-stu-id="379f5-342">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="379f5-343">将出现在每一项的 `xop:Include` 属性中的 `children` 元素信息项替换为字符信息项，这些字符信息项表示的是 MIME 部分（在步骤 3b 中标识）全部正文的规范 base64 编码（请参见 XSD-2，3.2.16 base64Binary）（实际是将 `xop:Include` 元素信息项替换为从包部分重新构造的数据）。</span><span class="sxs-lookup"><span data-stu-id="379f5-343">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="379f5-344">HTTP Content-Type 标头</span><span class="sxs-lookup"><span data-stu-id="379f5-344">HTTP Content-Type Header</span></span>
<span data-ttu-id="379f5-345">下面是一个 WCF 说明，其中列出了从 MTOM 规范本身所述的要求派生的 SOAP 1. x MTOM 编码消息的 HTTP Content-type 标头格式，并派生自 MTOM 和 RFC 2387。</span><span class="sxs-lookup"><span data-stu-id="379f5-345">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="379f5-346">R4131：HTTP Content-Type 标头必须具有值 multipart/related（不区分大小写）及其参数。</span><span class="sxs-lookup"><span data-stu-id="379f5-346">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="379f5-347">参数名不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="379f5-347">Parameter names are case-insensitive.</span></span> <span data-ttu-id="379f5-348">参数顺序并不重要。</span><span class="sxs-lookup"><span data-stu-id="379f5-348">Parameter order is not significant.</span></span>

- <span data-ttu-id="379f5-349">RFC 2045 第 5.1 节中列出了 MIME 消息 Content-Type 标头的完全 Backus-Naur 形式 (BNF)。</span><span class="sxs-lookup"><span data-stu-id="379f5-349">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="379f5-350">R4132：HTTP Content-Type 标头必须具有一个类型参数，并且值 `application/xop+xml` 括在双引号中。</span><span class="sxs-lookup"><span data-stu-id="379f5-350">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="379f5-351">虽然 RFC 2387 中不明确要求使用双引号，但文本观察到所有多部分/相关的媒体类型参数最有可能包含 " \@ " 或 "/" 之类的保留字符，因此需要双引号。</span><span class="sxs-lookup"><span data-stu-id="379f5-351">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="379f5-352">R4133：HTTP Content-Type 标头应该有一个 start 参数，其值为包含 SOAP 1.x 信封的 MIME 部分的 Content-ID 标头，并且括在双引号中。</span><span class="sxs-lookup"><span data-stu-id="379f5-352">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="379f5-353">如果省略 start 参数，则第一个 MIME 部分必须包含 SOAP 1.x 信封。</span><span class="sxs-lookup"><span data-stu-id="379f5-353">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="379f5-354">R4134：SOAP 1.1 MTOM 编码消息的 HTTP Content-Type 标头必须包含值为 text/xml（括在双引号中）的 start-info 参数。</span><span class="sxs-lookup"><span data-stu-id="379f5-354">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="379f5-355">R4135：SOAP 1.2 MTOM 编码消息的 HTTP Content-Type 标头必须包含值为 `application/soap+xml`（括在双引号中）的 start-info 参数。</span><span class="sxs-lookup"><span data-stu-id="379f5-355">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="379f5-356">R4136：SOAP 1.x MTOM 编码消息的 HTTP Content-Type 标头必须具有边界参数，其值（括在双引号中）与 RFC 2046 第 5.1.1 节中定义的 MIME 边界 BNF 匹配。</span><span class="sxs-lookup"><span data-stu-id="379f5-356">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="379f5-357">示例：</span><span class="sxs-lookup"><span data-stu-id="379f5-357">Examples:</span></span>

     <span data-ttu-id="379f5-358">正确</span><span class="sxs-lookup"><span data-stu-id="379f5-358">CORRECT</span></span>

    ```http
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="379f5-359">正确</span><span class="sxs-lookup"><span data-stu-id="379f5-359">CORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="379f5-360">不正确</span><span class="sxs-lookup"><span data-stu-id="379f5-360">INCORRECT</span></span>

    ```http
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="379f5-361">Infoset MIME 部分</span><span class="sxs-lookup"><span data-stu-id="379f5-361">Infoset MIME Part</span></span>
<span data-ttu-id="379f5-362">SOAP 1.x 信封封装为 XOP MIME 包的根部分，通常称为 `infoset` 部分。</span><span class="sxs-lookup"><span data-stu-id="379f5-362">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="379f5-363">R4141：SOAP 1.x 信封必须封装为 XOP MIME 包的根部分，称为 `infoset` 部分，并从 HTTP Content-Type 引用。</span><span class="sxs-lookup"><span data-stu-id="379f5-363">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="379f5-364">R4142：SOAP `Infoset` 部分必须包含以下 MIME 标头：`Content-ID`、`Content-Transfer-Encoding` 和 `Content-Type`。</span><span class="sxs-lookup"><span data-stu-id="379f5-364">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="379f5-365">Content-ID 标头的格式根据 RFC 2045 定义为</span><span class="sxs-lookup"><span data-stu-id="379f5-365">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="379f5-366">其中 `msg-id` 在 RFC 2822（取代 RFC 822，在 RFC 2045 中引用）定义：</span><span class="sxs-lookup"><span data-stu-id="379f5-366">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="379f5-367">和实际上是包含在 "" 中的电子邮件地址 \<" and  "> 。</span><span class="sxs-lookup"><span data-stu-id="379f5-367">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="379f5-368">RFC 2822 中增加了 `[CFWS]` 前缀和后缀，用于携带注释，不应用于保持互操作性。</span><span class="sxs-lookup"><span data-stu-id="379f5-368">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="379f5-369">R4143：Infoset MIME 部分的 Content-ID 标头的值必须遵循 RFC 2822 中的 `msg-id` 结果，并省略 `[CFWS]` 前缀和后缀部分。</span><span class="sxs-lookup"><span data-stu-id="379f5-369">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="379f5-370">许多 MIME 实现会将 "" 中包含的值的要求宽松 \<" and "> 为电子邮件地址，并 `absoluteURI` \<" , "> 在电子邮件地址之外使用。</span><span class="sxs-lookup"><span data-stu-id="379f5-370">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="379f5-371">此版本的 WCF 使用以下形式的内容 ID MIME 标头值：</span><span class="sxs-lookup"><span data-stu-id="379f5-371">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0>
```

<span data-ttu-id="379f5-372">R4144：MTOM 处理程序应接受符合以下宽松 `msg-id` 的 Content-ID 标头值。</span><span class="sxs-lookup"><span data-stu-id="379f5-372">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="379f5-373">MIME (RFC 2045) 提供 Content-Transfer-Encoding 标头来传递 MIME 部分内容的编码。</span><span class="sxs-lookup"><span data-stu-id="379f5-373">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="379f5-374">为 Content-Transfer-Encoding 定义的默认值为 7-bit，它不适合于大多数 SOAP 消息，因此，需要使用 Content-Transfer-Encoding 标头以获得更好的互操作性：</span><span class="sxs-lookup"><span data-stu-id="379f5-374">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="379f5-375">R4145：SOAP Infoset 部分必须包含 Content-Transfer-Encoding 标头。</span><span class="sxs-lookup"><span data-stu-id="379f5-375">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="379f5-376">R4146：如果 SOAP 信封字符编码为 UTF-8，则 Content-Transfer-Encoding 标头的值必须为 8-bit。</span><span class="sxs-lookup"><span data-stu-id="379f5-376">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="379f5-377">R4147：如果 SOAP 信封字符编码为 UTF-16，则 Content-Transfer-Encoding 标头的值必须为 binary。</span><span class="sxs-lookup"><span data-stu-id="379f5-377">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="379f5-378">根据 [XOP] 第 5 节，</span><span class="sxs-lookup"><span data-stu-id="379f5-378">According to [XOP] section 5,</span></span>

- <span data-ttu-id="379f5-379">R4148： SOAP 1.1 信息集部分必须包含媒体类型为 application/xop + xml 且参数类型 = "text/xml" 和字符集的 Content-type 标头</span><span class="sxs-lookup"><span data-stu-id="379f5-379">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="379f5-380">R4149： SOAP 1.2 信息集部分必须包含 media type `application/xop+xml` 和 parameters 类型为 "" 和的 content-type 标头 `application/soap+xml` `charset` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-380">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="379f5-381">虽然 XOP 定义 `charset` 参数对于 `application/xop+xml` 是可选的，但是对于类似于 BP 1.1 对 `charset` 媒体类型要求有 `text/xml` 参数的互操作性，该参数仍然是需要的。</span><span class="sxs-lookup"><span data-stu-id="379f5-381">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="379f5-382">R41410：`type` 和 `charset` 参数必须出现在 SOAP 1.x Infoset 部分的 Content-Type 标头中。</span><span class="sxs-lookup"><span data-stu-id="379f5-382">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="379f5-383">WCF 对 MTOM 的终结点支持</span><span class="sxs-lookup"><span data-stu-id="379f5-383">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="379f5-384">MTOM 的用途是对 SOAP 消息进行编码，以优化 base64 编码数据。</span><span class="sxs-lookup"><span data-stu-id="379f5-384">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="379f5-385">下面列出了相关约束：</span><span class="sxs-lookup"><span data-stu-id="379f5-385">The following is a list of constraints:</span></span>

- <span data-ttu-id="379f5-386">R4151：任何包含 base64 编码数据的元素信息项都可以优化。</span><span class="sxs-lookup"><span data-stu-id="379f5-386">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="379f5-387">B4152： WCF 优化包含 base64 编码数据的元素信息项，长度超过1024个字节。</span><span class="sxs-lookup"><span data-stu-id="379f5-387">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="379f5-388">配置为使用 MTOM 的 WCF 终结点将始终发送 MTOM 编码的消息。</span><span class="sxs-lookup"><span data-stu-id="379f5-388">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="379f5-389">即使没有一个部分符合必需的标准，消息仍然是 MTOM 编码消息（序列化为一个 MIME 包，具有包含 SOAP 信封的单个 MIME 部分）。</span><span class="sxs-lookup"><span data-stu-id="379f5-389">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="379f5-390">MTOM 的 WS-Policy 断言</span><span class="sxs-lookup"><span data-stu-id="379f5-390">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="379f5-391">WCF 使用以下策略断言来指示终结点的 MTOM 使用：</span><span class="sxs-lookup"><span data-stu-id="379f5-391">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization />
```

- <span data-ttu-id="379f5-392">R4211：上面的策略断言有一个终结点策略主题，并指定终结点收发的所有消息都必须使用 MTOM 进行优化。</span><span class="sxs-lookup"><span data-stu-id="379f5-392">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="379f5-393">B4212：配置为使用 MTOM 优化时，WCF 终结点会向附加到相应的策略添加 MTOM 策略断言 `wsdl:binding` 。</span><span class="sxs-lookup"><span data-stu-id="379f5-393">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="379f5-394">与 WS-Security 的结合</span><span class="sxs-lookup"><span data-stu-id="379f5-394">Composition with WS-Security</span></span>
<span data-ttu-id="379f5-395">MTOM 是一种类似于 `text/xml` 和 WCF 二进制 XML 的编码机制。</span><span class="sxs-lookup"><span data-stu-id="379f5-395">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="379f5-396">MTOM 可以与 WS-Security 及其他 WS-\* 协议自然结合：使用 WS-Security 进行保护的消息可使用 MTOM 优化。</span><span class="sxs-lookup"><span data-stu-id="379f5-396">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="379f5-397">示例</span><span class="sxs-lookup"><span data-stu-id="379f5-397">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="379f5-398">使用 MTOM 编码的 WCF SOAP 1.1 消息</span><span class="sxs-lookup"><span data-stu-id="379f5-398">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

```http
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="379f5-399">使用 MTOM 编码的 WCF 安全 SOAP 1.2 消息</span><span class="sxs-lookup"><span data-stu-id="379f5-399">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="379f5-400">此示例中，消息是使用 MTOM 以及采用 WS-Security 进行保护的 SOAP 1.2 编码的。</span><span class="sxs-lookup"><span data-stu-id="379f5-400">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="379f5-401">标识来进行编码的二进制部分为 `BinarySecurityToken` 的内容、对应于加密签名的 `CipherValue` 的 `EncryptedData`，以及经过加密的正文。</span><span class="sxs-lookup"><span data-stu-id="379f5-401">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="379f5-402">请注意， `CipherValue` WCF 的 `EncryptedKey` 无法进行优化标识，因为其长度小于1024个字节。</span><span class="sxs-lookup"><span data-stu-id="379f5-402">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

```http
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml";
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```
