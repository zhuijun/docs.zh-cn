---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69918876"
---
# \<filters>

<span data-ttu-id="563f6-101">`filters` 元素包含用于控制所记录的消息类型的 XPath 筛选器集合。</span><span class="sxs-lookup"><span data-stu-id="563f6-101">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="563f6-102">如果将 `logMessagesAtTransportLevel` 指定为 `true`，筛选器将只应用于传输层。</span><span class="sxs-lookup"><span data-stu-id="563f6-102">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="563f6-103">筛选器不影响服务级别和格式不正确的消息日志记录。</span><span class="sxs-lookup"><span data-stu-id="563f6-103">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="563f6-104">若要向集合添加筛选器，请使用 `add` 关键字。</span><span class="sxs-lookup"><span data-stu-id="563f6-104">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="563f6-105">如果定义一个或多个筛选器，则仅记录与其中至少一个筛选器相匹配的消息。</span><span class="sxs-lookup"><span data-stu-id="563f6-105">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="563f6-106">如果未定义任何筛选器，则所有消息都可通过。</span><span class="sxs-lookup"><span data-stu-id="563f6-106">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="563f6-107">筛选器支持完整的 XPath 语法，并按照其在配置文件中出现的顺序进行应用。</span><span class="sxs-lookup"><span data-stu-id="563f6-107">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="563f6-108">存在语法错误的筛选器会导致配置异常。</span><span class="sxs-lookup"><span data-stu-id="563f6-108">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="563f6-109">下面的示例演示如何配置一个筛选器，它仅记录具有 SOAP 标头部分的消息。</span><span class="sxs-lookup"><span data-stu-id="563f6-109">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="563f6-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="563f6-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="563f6-111">配置消息日志记录</span><span class="sxs-lookup"><span data-stu-id="563f6-111">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
