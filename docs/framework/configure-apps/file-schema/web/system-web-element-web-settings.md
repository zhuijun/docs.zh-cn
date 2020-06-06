---
title: <system.web> 元素（网络设置）
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: b37b05bdf90630251cbfcf86751243a3a8b77663
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152836"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="4917c-102">\<system.web> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4917c-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="4917c-103">包含有关 ASP.NET 承载层如何管理进程范围的行为的信息。</span><span class="sxs-lookup"><span data-stu-id="4917c-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="4917c-104">语法</span><span class="sxs-lookup"><span data-stu-id="4917c-104">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4917c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4917c-105">Attributes and Elements</span></span>  

<span data-ttu-id="4917c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4917c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4917c-107">特性</span><span class="sxs-lookup"><span data-stu-id="4917c-107">Attributes</span></span>  

<span data-ttu-id="4917c-108">无。</span><span class="sxs-lookup"><span data-stu-id="4917c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4917c-109">子元素</span><span class="sxs-lookup"><span data-stu-id="4917c-109">Child Elements</span></span>  
  
|<span data-ttu-id="4917c-110">元素</span><span class="sxs-lookup"><span data-stu-id="4917c-110">Element</span></span>|<span data-ttu-id="4917c-111">说明</span><span class="sxs-lookup"><span data-stu-id="4917c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="4917c-112">为 aspnet 文件中的 IIS 应用程序池指定配置设置。</span><span class="sxs-lookup"><span data-stu-id="4917c-112">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4917c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4917c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4917c-114">元素</span><span class="sxs-lookup"><span data-stu-id="4917c-114">Element</span></span>|<span data-ttu-id="4917c-115">说明</span><span class="sxs-lookup"><span data-stu-id="4917c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="4917c-116">指定公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="4917c-116">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4917c-117">注解</span><span class="sxs-lookup"><span data-stu-id="4917c-117">Remarks</span></span>  

<span data-ttu-id="4917c-118">`system.web`元素及其子 `applicationPool` 元素已添加到 .NET FRAMEWORK 3.5 SP1 中的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="4917c-118">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="4917c-119">在集成模式下运行 IIS 7.0 或更高版本时，此元素组合可让你配置 ASP.NET 管理线程的方式，以及在 ASP.NET 托管在 IIS 应用程序池中时，如何将请求排队。</span><span class="sxs-lookup"><span data-stu-id="4917c-119">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="4917c-120">如果在经典或 ISAPI 模式下运行 IIS 7.0 或更高版本，则将忽略这些设置。</span><span class="sxs-lookup"><span data-stu-id="4917c-120">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4917c-121">示例</span><span class="sxs-lookup"><span data-stu-id="4917c-121">Example</span></span>  

<span data-ttu-id="4917c-122">下面的示例演示当 ASP.NET 托管在 IIS 应用程序池中时，如何在 ASP.NET 文件中配置进程范围行为。</span><span class="sxs-lookup"><span data-stu-id="4917c-122">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="4917c-123">该示例假设 IIS 在集成模式下运行，并且该应用程序正在使用 .NET Framework 3.5 SP1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="4917c-123">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="4917c-124">此行为不会在早于 .NET Framework 3.5 SP1 的 .NET Framework 版本中发生。</span><span class="sxs-lookup"><span data-stu-id="4917c-124">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="4917c-125">示例中的值为默认值。</span><span class="sxs-lookup"><span data-stu-id="4917c-125">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="4917c-126">元素信息</span><span class="sxs-lookup"><span data-stu-id="4917c-126">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4917c-127">命名空间</span><span class="sxs-lookup"><span data-stu-id="4917c-127">Namespace</span></span>||  
|<span data-ttu-id="4917c-128">架构名称</span><span class="sxs-lookup"><span data-stu-id="4917c-128">Schema Name</span></span>||  
|<span data-ttu-id="4917c-129">验证文件</span><span class="sxs-lookup"><span data-stu-id="4917c-129">Validation File</span></span>||  
|<span data-ttu-id="4917c-130">可以为空</span><span class="sxs-lookup"><span data-stu-id="4917c-130">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="4917c-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4917c-131">See also</span></span>

- [<span data-ttu-id="4917c-132">\<applicationPool>元素（Web 设置）</span><span class="sxs-lookup"><span data-stu-id="4917c-132">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
