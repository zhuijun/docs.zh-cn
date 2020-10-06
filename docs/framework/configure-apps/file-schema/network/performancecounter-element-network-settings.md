---
title: <performanceCounters> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 584bdafbbd60303401cbc6ad96b8654fe11c7077
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756255"
---
# <a name="performancecounters-element-network-settings"></a><span data-ttu-id="f1bda-102">\<performanceCounters> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="f1bda-102">\<performanceCounters> Element (Network Settings)</span></span>

<span data-ttu-id="f1bda-103">启用或禁用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="f1bda-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="f1bda-104">语法</span><span class="sxs-lookup"><span data-stu-id="f1bda-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1bda-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f1bda-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f1bda-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f1bda-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1bda-107">特性</span><span class="sxs-lookup"><span data-stu-id="f1bda-107">Attributes</span></span>  
  
|<span data-ttu-id="f1bda-108">属性</span><span class="sxs-lookup"><span data-stu-id="f1bda-108">Attribute</span></span>|<span data-ttu-id="f1bda-109">说明</span><span class="sxs-lookup"><span data-stu-id="f1bda-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f1bda-110">指定是否启用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="f1bda-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="f1bda-111">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="f1bda-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1bda-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f1bda-112">Child Elements</span></span>  

 <span data-ttu-id="f1bda-113">无。</span><span class="sxs-lookup"><span data-stu-id="f1bda-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1bda-114">父元素</span><span class="sxs-lookup"><span data-stu-id="f1bda-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f1bda-115">元素</span><span class="sxs-lookup"><span data-stu-id="f1bda-115">Element</span></span>|<span data-ttu-id="f1bda-116">说明</span><span class="sxs-lookup"><span data-stu-id="f1bda-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1bda-117">设置</span><span class="sxs-lookup"><span data-stu-id="f1bda-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="f1bda-118">配置 <xref:System.Net> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="f1bda-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1bda-119">注解</span><span class="sxs-lookup"><span data-stu-id="f1bda-119">Remarks</span></span>  

 <span data-ttu-id="f1bda-120">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="f1bda-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="f1bda-121">需要在要使用的配置文件中启用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="f1bda-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="f1bda-122">通过配置文件中的单个设置即可启用或禁用所有网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="f1bda-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="f1bda-123">不能启用或禁用单个网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="f1bda-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="f1bda-124">有关特定的网络性能计数器的详细信息，请参阅 [联网性能计数器](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)。</span><span class="sxs-lookup"><span data-stu-id="f1bda-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="f1bda-125">默认值是禁用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="f1bda-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="f1bda-126"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>属性可用于从适用的配置文件中获取**已启用**属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="f1bda-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1bda-127">示例</span><span class="sxs-lookup"><span data-stu-id="f1bda-127">Example</span></span>  

 <span data-ttu-id="f1bda-128">下面的示例演示如何配置 <xref:System.Net> 和相关命名空间，以启用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="f1bda-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1bda-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="f1bda-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f1bda-130">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="f1bda-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f1bda-131">网络性能计数器</span><span class="sxs-lookup"><span data-stu-id="f1bda-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
