---
title: <performanceCounter> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 4859f3a9e6de4f1bf8a56212bfe01f94d66f5650
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190236"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="a3eec-102">\<performanceCounter> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="a3eec-102">\<performanceCounter> Element (Network Settings)</span></span>

<span data-ttu-id="a3eec-103">启用或禁用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="a3eec-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="a3eec-104">语法</span><span class="sxs-lookup"><span data-stu-id="a3eec-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3eec-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a3eec-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a3eec-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a3eec-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3eec-107">特性</span><span class="sxs-lookup"><span data-stu-id="a3eec-107">Attributes</span></span>  
  
|<span data-ttu-id="a3eec-108">属性</span><span class="sxs-lookup"><span data-stu-id="a3eec-108">Attribute</span></span>|<span data-ttu-id="a3eec-109">描述</span><span class="sxs-lookup"><span data-stu-id="a3eec-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a3eec-110">指定是否启用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="a3eec-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="a3eec-111">默认值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="a3eec-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3eec-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a3eec-112">Child Elements</span></span>  

 <span data-ttu-id="a3eec-113">无。</span><span class="sxs-lookup"><span data-stu-id="a3eec-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3eec-114">父元素</span><span class="sxs-lookup"><span data-stu-id="a3eec-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a3eec-115">元素</span><span class="sxs-lookup"><span data-stu-id="a3eec-115">Element</span></span>|<span data-ttu-id="a3eec-116">描述</span><span class="sxs-lookup"><span data-stu-id="a3eec-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3eec-117">设置</span><span class="sxs-lookup"><span data-stu-id="a3eec-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a3eec-118">配置 <xref:System.Net> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="a3eec-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3eec-119">备注</span><span class="sxs-lookup"><span data-stu-id="a3eec-119">Remarks</span></span>  

 <span data-ttu-id="a3eec-120">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="a3eec-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="a3eec-121">需要在要使用的配置文件中启用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="a3eec-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="a3eec-122">通过配置文件中的单个设置即可启用或禁用所有网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="a3eec-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="a3eec-123">不能启用或禁用单个网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="a3eec-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="a3eec-124">有关特定的网络性能计数器的详细信息，请参阅 [联网性能计数器](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)。</span><span class="sxs-lookup"><span data-stu-id="a3eec-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="a3eec-125">默认值是禁用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="a3eec-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="a3eec-126"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>属性可用于从适用的配置文件中获取**已启用**属性的当前值。</span><span class="sxs-lookup"><span data-stu-id="a3eec-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3eec-127">示例</span><span class="sxs-lookup"><span data-stu-id="a3eec-127">Example</span></span>  

 <span data-ttu-id="a3eec-128">下面的示例演示如何配置 <xref:System.Net> 和相关命名空间，以启用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="a3eec-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3eec-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="a3eec-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a3eec-130">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="a3eec-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a3eec-131">网络性能计数器</span><span class="sxs-lookup"><span data-stu-id="a3eec-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
