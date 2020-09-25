---
title: <appDomainResourceMonitoring> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 9ecf2e382b5d483377df871835793219b3f74760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170267"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="32f9d-102">\<appDomainResourceMonitoring> 元素</span><span class="sxs-lookup"><span data-stu-id="32f9d-102">\<appDomainResourceMonitoring> Element</span></span>

<span data-ttu-id="32f9d-103">指示运行时在过程的生命周期过程中收集所有应用程序域的统计数据。</span><span class="sxs-lookup"><span data-stu-id="32f9d-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="32f9d-104">语法</span><span class="sxs-lookup"><span data-stu-id="32f9d-104">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32f9d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="32f9d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="32f9d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="32f9d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32f9d-107">特性</span><span class="sxs-lookup"><span data-stu-id="32f9d-107">Attributes</span></span>  
  
|<span data-ttu-id="32f9d-108">属性</span><span class="sxs-lookup"><span data-stu-id="32f9d-108">Attribute</span></span>|<span data-ttu-id="32f9d-109">描述</span><span class="sxs-lookup"><span data-stu-id="32f9d-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="32f9d-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="32f9d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="32f9d-111">指定运行时是否收集应用程序域资源监视的统计信息。</span><span class="sxs-lookup"><span data-stu-id="32f9d-111">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="32f9d-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="32f9d-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="32f9d-113">值</span><span class="sxs-lookup"><span data-stu-id="32f9d-113">Value</span></span>|<span data-ttu-id="32f9d-114">描述</span><span class="sxs-lookup"><span data-stu-id="32f9d-114">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="32f9d-115">收集应用程序域资源监视的统计信息。</span><span class="sxs-lookup"><span data-stu-id="32f9d-115">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="32f9d-116">不收集应用程序域资源监视的统计信息。</span><span class="sxs-lookup"><span data-stu-id="32f9d-116">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32f9d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="32f9d-117">Child Elements</span></span>  

 <span data-ttu-id="32f9d-118">无。</span><span class="sxs-lookup"><span data-stu-id="32f9d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32f9d-119">父元素</span><span class="sxs-lookup"><span data-stu-id="32f9d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="32f9d-120">元素</span><span class="sxs-lookup"><span data-stu-id="32f9d-120">Element</span></span>|<span data-ttu-id="32f9d-121">描述</span><span class="sxs-lookup"><span data-stu-id="32f9d-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="32f9d-122">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="32f9d-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="32f9d-123">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="32f9d-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32f9d-124">备注</span><span class="sxs-lookup"><span data-stu-id="32f9d-124">Remarks</span></span>  

 <span data-ttu-id="32f9d-125">应用程序域资源监视可通过托管应用程序域类、托管 [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) 接口和 WINDOWS (ETW) 的事件跟踪获得。</span><span class="sxs-lookup"><span data-stu-id="32f9d-125">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="32f9d-126">启用监视后，会在进程的生存期内收集进程中所有应用程序域的统计信息。</span><span class="sxs-lookup"><span data-stu-id="32f9d-126">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="32f9d-127">若要从托管代码启用监视，请使用 <xref:System.AppDomain.MonitoringIsEnabled%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="32f9d-127">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="32f9d-128">此配置元素仅在 .NET Framework 4 及更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="32f9d-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32f9d-129">示例</span><span class="sxs-lookup"><span data-stu-id="32f9d-129">Example</span></span>  

 <span data-ttu-id="32f9d-130">下面的示例演示如何启用应用程序域资源监视。</span><span class="sxs-lookup"><span data-stu-id="32f9d-130">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32f9d-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="32f9d-131">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="32f9d-132">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="32f9d-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="32f9d-133">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="32f9d-133">Configuration File Schema</span></span>](../index.md)
