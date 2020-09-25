---
title: <add> 的 <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: c1de0605bc8afc502a85d9b2917b975ee45a3d26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201650"
---
# <a name="add-of-filters"></a><span data-ttu-id="caa65-102">\<add> 的 \<filters></span><span class="sxs-lookup"><span data-stu-id="caa65-102">\<add> of \<filters></span></span>

<span data-ttu-id="caa65-103">一个 XPath 筛选器，用于指定要记录的消息的种类。</span><span class="sxs-lookup"><span data-stu-id="caa65-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<messageLogging>**](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="caa65-104">语法</span><span class="sxs-lookup"><span data-stu-id="caa65-104">Syntax</span></span>  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="caa65-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="caa65-105">Attributes and Elements</span></span>  

 <span data-ttu-id="caa65-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="caa65-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="caa65-107">特性</span><span class="sxs-lookup"><span data-stu-id="caa65-107">Attributes</span></span>  
  
|<span data-ttu-id="caa65-108">属性</span><span class="sxs-lookup"><span data-stu-id="caa65-108">Attribute</span></span>|<span data-ttu-id="caa65-109">描述</span><span class="sxs-lookup"><span data-stu-id="caa65-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="caa65-110">filter</span><span class="sxs-lookup"><span data-stu-id="caa65-110">filter</span></span>|<span data-ttu-id="caa65-111">一个字符串，用于指定由 XPath 1.0 表达式定义的 XML 文档的查询。</span><span class="sxs-lookup"><span data-stu-id="caa65-111">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="caa65-112">有关详细信息，请参阅 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>。</span><span class="sxs-lookup"><span data-stu-id="caa65-112">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="caa65-113">子元素</span><span class="sxs-lookup"><span data-stu-id="caa65-113">Child Elements</span></span>  

 <span data-ttu-id="caa65-114">无。</span><span class="sxs-lookup"><span data-stu-id="caa65-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="caa65-115">父元素</span><span class="sxs-lookup"><span data-stu-id="caa65-115">Parent Elements</span></span>  
  
|<span data-ttu-id="caa65-116">元素</span><span class="sxs-lookup"><span data-stu-id="caa65-116">Element</span></span>|<span data-ttu-id="caa65-117">描述</span><span class="sxs-lookup"><span data-stu-id="caa65-117">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters.md)|<span data-ttu-id="caa65-118">包含用于控制所记录的消息类型的 XPath 筛选器集合。</span><span class="sxs-lookup"><span data-stu-id="caa65-118">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caa65-119">备注</span><span class="sxs-lookup"><span data-stu-id="caa65-119">Remarks</span></span>  

 <span data-ttu-id="caa65-120">如果将 `logMessagesAtTransportLevel` 指定为 `true`，筛选器将只应用于传输层。</span><span class="sxs-lookup"><span data-stu-id="caa65-120">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="caa65-121">筛选器不影响服务级别和格式不正确的消息日志记录。</span><span class="sxs-lookup"><span data-stu-id="caa65-121">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="caa65-122">若要向集合添加筛选器，请使用 `add` 关键字。</span><span class="sxs-lookup"><span data-stu-id="caa65-122">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="caa65-123">如果定义一个或多个筛选器，则仅记录与其中至少一个筛选器相匹配的消息。</span><span class="sxs-lookup"><span data-stu-id="caa65-123">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="caa65-124">如果未定义任何筛选器，则所有消息都可通过。</span><span class="sxs-lookup"><span data-stu-id="caa65-124">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="caa65-125">筛选器支持完整的 XPath 语法，并按照其在配置文件中出现的顺序进行应用。</span><span class="sxs-lookup"><span data-stu-id="caa65-125">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="caa65-126">存在语法错误的筛选器会导致配置异常。</span><span class="sxs-lookup"><span data-stu-id="caa65-126">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="caa65-127">下面的示例演示如何配置一个筛选器，它仅记录具有 SOAP 标头部分的消息。</span><span class="sxs-lookup"><span data-stu-id="caa65-127">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caa65-128">示例</span><span class="sxs-lookup"><span data-stu-id="caa65-128">Example</span></span>  

 <span data-ttu-id="caa65-129">下面的示例演示如何配置一个筛选器，它仅记录具有 SOAP 标头部分的消息。</span><span class="sxs-lookup"><span data-stu-id="caa65-129">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="caa65-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="caa65-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="caa65-131">配置消息日志记录</span><span class="sxs-lookup"><span data-stu-id="caa65-131">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
