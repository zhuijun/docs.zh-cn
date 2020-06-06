---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855292"
---
# \<endToEndTracing>
<span data-ttu-id="a90e3-101">一个配置元素，用于启用和禁用服务应用程序运行过程中端对端跟踪的不同方面。</span><span class="sxs-lookup"><span data-stu-id="a90e3-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="a90e3-102">语法</span><span class="sxs-lookup"><span data-stu-id="a90e3-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a90e3-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a90e3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a90e3-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a90e3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a90e3-105">特性</span><span class="sxs-lookup"><span data-stu-id="a90e3-105">Attributes</span></span>  
  
|<span data-ttu-id="a90e3-106">属性</span><span class="sxs-lookup"><span data-stu-id="a90e3-106">Attribute</span></span>|<span data-ttu-id="a90e3-107">说明</span><span class="sxs-lookup"><span data-stu-id="a90e3-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="a90e3-108">一个布尔值，指定是否启用活动跟踪。</span><span class="sxs-lookup"><span data-stu-id="a90e3-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="a90e3-109">一个布尔值，指定是否启用消息流跟踪。</span><span class="sxs-lookup"><span data-stu-id="a90e3-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="a90e3-110">一个布尔值，指定是否将传播特性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="a90e3-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a90e3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a90e3-111">Child Elements</span></span>  
 <span data-ttu-id="a90e3-112">无。</span><span class="sxs-lookup"><span data-stu-id="a90e3-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a90e3-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a90e3-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a90e3-114">元素</span><span class="sxs-lookup"><span data-stu-id="a90e3-114">Element</span></span>|<span data-ttu-id="a90e3-115">描述</span><span class="sxs-lookup"><span data-stu-id="a90e3-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="a90e3-116">定义管理员运行时检查和控制的 WCF 设置。</span><span class="sxs-lookup"><span data-stu-id="a90e3-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a90e3-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a90e3-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="a90e3-118">端到端跟踪</span><span class="sxs-lookup"><span data-stu-id="a90e3-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
