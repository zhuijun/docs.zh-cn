---
title: <diagnostics>用于激活
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400413"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="c0bbb-102">\<diagnostics>用于激活</span><span class="sxs-lookup"><span data-stu-id="c0bbb-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="c0bbb-103">配置 Windows Communication Foundation （WCF）侦听器的诊断功能。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="c0bbb-104">语法</span><span class="sxs-lookup"><span data-stu-id="c0bbb-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="c0bbb-105">类型</span><span class="sxs-lookup"><span data-stu-id="c0bbb-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0bbb-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c0bbb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c0bbb-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0bbb-108">特性</span><span class="sxs-lookup"><span data-stu-id="c0bbb-108">Attributes</span></span>  
  
|<span data-ttu-id="c0bbb-109">属性</span><span class="sxs-lookup"><span data-stu-id="c0bbb-109">Attribute</span></span>|<span data-ttu-id="c0bbb-110">说明</span><span class="sxs-lookup"><span data-stu-id="c0bbb-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="c0bbb-111">一个布尔值，指示是否启用用于诊断目的的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0bbb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c0bbb-112">Child Elements</span></span>  
 <span data-ttu-id="c0bbb-113">无。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0bbb-114">父元素</span><span class="sxs-lookup"><span data-stu-id="c0bbb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c0bbb-115">元素</span><span class="sxs-lookup"><span data-stu-id="c0bbb-115">Element</span></span>|<span data-ttu-id="c0bbb-116">描述</span><span class="sxs-lookup"><span data-stu-id="c0bbb-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="c0bbb-117">包含侦听器进程 SMSvcHost.exe 的配置设置。</span><span class="sxs-lookup"><span data-stu-id="c0bbb-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0bbb-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0bbb-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
