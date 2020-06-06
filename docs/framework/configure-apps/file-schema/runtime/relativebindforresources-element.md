---
title: <relativeBindForResources> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153901"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="7dedf-102">\<relativeBindForResources> 元素</span><span class="sxs-lookup"><span data-stu-id="7dedf-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="7dedf-103">优化附属程序集的探测。</span><span class="sxs-lookup"><span data-stu-id="7dedf-103">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="7dedf-104">语法</span><span class="sxs-lookup"><span data-stu-id="7dedf-104">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7dedf-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7dedf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7dedf-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7dedf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7dedf-107">特性</span><span class="sxs-lookup"><span data-stu-id="7dedf-107">Attributes</span></span>  
  
|<span data-ttu-id="7dedf-108">属性</span><span class="sxs-lookup"><span data-stu-id="7dedf-108">Attribute</span></span>|<span data-ttu-id="7dedf-109">说明</span><span class="sxs-lookup"><span data-stu-id="7dedf-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7dedf-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="7dedf-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="7dedf-111">指定公共语言运行时是否优化附属程序集的探测。</span><span class="sxs-lookup"><span data-stu-id="7dedf-111">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7dedf-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="7dedf-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="7dedf-113">值</span><span class="sxs-lookup"><span data-stu-id="7dedf-113">Value</span></span>|<span data-ttu-id="7dedf-114">说明</span><span class="sxs-lookup"><span data-stu-id="7dedf-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7dedf-115">运行时不会优化附属程序集的探测。</span><span class="sxs-lookup"><span data-stu-id="7dedf-115">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="7dedf-116">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="7dedf-116">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="7dedf-117">运行时优化附属程序集的探测。</span><span class="sxs-lookup"><span data-stu-id="7dedf-117">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7dedf-118">子元素</span><span class="sxs-lookup"><span data-stu-id="7dedf-118">Child Elements</span></span>  
 <span data-ttu-id="7dedf-119">无。</span><span class="sxs-lookup"><span data-stu-id="7dedf-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7dedf-120">父元素</span><span class="sxs-lookup"><span data-stu-id="7dedf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7dedf-121">元素</span><span class="sxs-lookup"><span data-stu-id="7dedf-121">Element</span></span>|<span data-ttu-id="7dedf-122">描述</span><span class="sxs-lookup"><span data-stu-id="7dedf-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7dedf-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="7dedf-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7dedf-124">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="7dedf-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dedf-125">注解</span><span class="sxs-lookup"><span data-stu-id="7dedf-125">Remarks</span></span>  
 <span data-ttu-id="7dedf-126">一般情况下，资源管理器探测资源，如[打包和部署资源](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)主题中所述。</span><span class="sxs-lookup"><span data-stu-id="7dedf-126">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="7dedf-127">这意味着，当资源管理器探测资源的特定本地化版本时，它可能会在全局程序集缓存中查找，在应用程序的基本代码中查找特定于区域性的文件夹，为附属程序集查询 Windows Installer，并引发 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="7dedf-127">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="7dedf-128">`<relativeBindForResources>`元素优化资源管理器探测附属程序集的方式。</span><span class="sxs-lookup"><span data-stu-id="7dedf-128">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="7dedf-129">当在以下条件下探测资源时，它可以提高性能：</span><span class="sxs-lookup"><span data-stu-id="7dedf-129">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="7dedf-130">当附属程序集部署在与代码程序集相同的位置时。</span><span class="sxs-lookup"><span data-stu-id="7dedf-130">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="7dedf-131">换言之，如果代码程序集安装在全局程序集缓存中，则还必须在该程序集中安装附属程序集。</span><span class="sxs-lookup"><span data-stu-id="7dedf-131">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="7dedf-132">如果代码程序集安装在应用程序的代码库中，则附属程序集还必须安装在基本代码的特定于区域性的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7dedf-132">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="7dedf-133">如果未使用 Windows Installer 或只是很少使用附属程序集的按需安装。</span><span class="sxs-lookup"><span data-stu-id="7dedf-133">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="7dedf-134">当应用程序代码不处理 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件时。</span><span class="sxs-lookup"><span data-stu-id="7dedf-134">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="7dedf-135">设置 `enabled` 元素的属性 `<relativeBindForResources>` ，以 `true` 优化资源管理器的附属程序集探测，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7dedf-135">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="7dedf-136">它使用父代码程序集的位置来探测附属程序集。</span><span class="sxs-lookup"><span data-stu-id="7dedf-136">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="7dedf-137">它不会为附属程序集查询 Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="7dedf-137">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="7dedf-138">它不会引发 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件。</span><span class="sxs-lookup"><span data-stu-id="7dedf-138">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dedf-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="7dedf-139">See also</span></span>

- [<span data-ttu-id="7dedf-140">打包和部署资源</span><span class="sxs-lookup"><span data-stu-id="7dedf-140">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="7dedf-141">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="7dedf-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7dedf-142">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="7dedf-142">Configuration File Schema</span></span>](../index.md)
