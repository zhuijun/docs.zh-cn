---
title: 消息编码
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 8e5a71095ba62e0e2e6592c8b7b83b67602ef7e7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69931599"
---
# <a name="message-encoding"></a><span data-ttu-id="9875c-102">消息编码</span><span class="sxs-lookup"><span data-stu-id="9875c-102">Message Encoding</span></span>
<span data-ttu-id="9875c-103">编码是将一组 Unicode 字符转换为一个字节序列的过程。</span><span class="sxs-lookup"><span data-stu-id="9875c-103">Encoding is the process of transforming a set of Unicode characters into a sequence of bytes.</span></span> <span data-ttu-id="9875c-104">解码是反向过程。</span><span class="sxs-lookup"><span data-stu-id="9875c-104">Decoding is the reverse process.</span></span> <span data-ttu-id="9875c-105">Windows Communication Foundation (WCF) 包含三种类型的 SOAP 消息编码：文本、二进制和消息传输优化机制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="9875c-105">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="9875c-106">`binaryMessageEncoding` 配置节指定基于二进制的 XML 消息所使用的字符编码和消息版本管理。</span><span class="sxs-lookup"><span data-stu-id="9875c-106">The `binaryMessageEncoding` configuration section specifies the character encoding and message versioning used for binary-based XML messages.</span></span> <span data-ttu-id="9875c-107">二进制消息编码器在网络上以二进制形式对 Windows Communication Foundation (WCF) 消息进行编码。</span><span class="sxs-lookup"><span data-stu-id="9875c-107">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="9875c-108">虽然这种编码有助于非常快速地传输消息，但是丢失了基于 WS-\* 标准的互操作性。</span><span class="sxs-lookup"><span data-stu-id="9875c-108">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
 <span data-ttu-id="9875c-109">`mtomMessageEncoding` 配置节指定用于使用消息传输优化机制 (MTOM) 编码的消息的字符编码和消息版本管理。</span><span class="sxs-lookup"><span data-stu-id="9875c-109">The `mtomMessageEncoding` configuration section specifies the character encoding and message versioning used for a message using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="9875c-110">(MTOM) 是一种用于传输 Windows Communication Foundation (WCF) 消息中二进制数据的有效技术。</span><span class="sxs-lookup"><span data-stu-id="9875c-110">(MTOM) is an efficient technology for transmitting binary data in Windows Communication Foundation (WCF) messages.</span></span> <span data-ttu-id="9875c-111">MTOM 编码器试图在效率和互操作性之间取得平衡。</span><span class="sxs-lookup"><span data-stu-id="9875c-111">The MTOM encoder attempts to strike a balance between efficiency and interoperability.</span></span> <span data-ttu-id="9875c-112">MTOM 编码以文本形式传输大多数 XML，但是会通过按原样（即不转换为文本）的方式传输来优化大型二进制数据块。</span><span class="sxs-lookup"><span data-stu-id="9875c-112">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to text.</span></span>  
  
 <span data-ttu-id="9875c-113">`textMessageEncoding` 配置节指定用于在网络上创建基于文本的消息的文本编码器。</span><span class="sxs-lookup"><span data-stu-id="9875c-113">The `textMessageEncoding` configuration section specifies a text encoder used to create text-based messages on the wire.</span></span> <span data-ttu-id="9875c-114">此编码器产生的消息适合于基于 WS-\* 的互操作性。</span><span class="sxs-lookup"><span data-stu-id="9875c-114">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="9875c-115">Web 服务或 Web 服务客户端通常可以理解文本 XML。</span><span class="sxs-lookup"><span data-stu-id="9875c-115">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="9875c-116">但是，对于 XML 消息编码来说，以文本形式传输较大的二进制数据块是最低效的方法。</span><span class="sxs-lookup"><span data-stu-id="9875c-116">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9875c-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9875c-117">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [<span data-ttu-id="9875c-118">绑定</span><span class="sxs-lookup"><span data-stu-id="9875c-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9875c-119">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="9875c-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9875c-120">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="9875c-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="9875c-121">选择消息编码器</span><span class="sxs-lookup"><span data-stu-id="9875c-121">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
