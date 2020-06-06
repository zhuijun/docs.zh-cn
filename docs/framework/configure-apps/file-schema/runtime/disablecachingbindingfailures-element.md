---
title: <disableCachingBindingFailures> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
ms.openlocfilehash: 23633cb282b8e59b4df4bcc2cd38717d805a207e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117502"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="74f98-102">\<disableCachingBindingFailures> 元素</span><span class="sxs-lookup"><span data-stu-id="74f98-102">\<disableCachingBindingFailures> Element</span></span>
<span data-ttu-id="74f98-103">指定是否禁止缓存发生的绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="74f98-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="74f98-104">语法</span><span class="sxs-lookup"><span data-stu-id="74f98-104">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74f98-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="74f98-105">Attributes and Elements</span></span>  
 <span data-ttu-id="74f98-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="74f98-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74f98-107">特性</span><span class="sxs-lookup"><span data-stu-id="74f98-107">Attributes</span></span>  
  
|<span data-ttu-id="74f98-108">属性</span><span class="sxs-lookup"><span data-stu-id="74f98-108">Attribute</span></span>|<span data-ttu-id="74f98-109">说明</span><span class="sxs-lookup"><span data-stu-id="74f98-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74f98-110">已启用</span><span class="sxs-lookup"><span data-stu-id="74f98-110">enabled</span></span>|<span data-ttu-id="74f98-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="74f98-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="74f98-112">指定是否禁止缓存发生的绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="74f98-112">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="74f98-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="74f98-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="74f98-114">值</span><span class="sxs-lookup"><span data-stu-id="74f98-114">Value</span></span>|<span data-ttu-id="74f98-115">说明</span><span class="sxs-lookup"><span data-stu-id="74f98-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="74f98-116">0</span><span class="sxs-lookup"><span data-stu-id="74f98-116">0</span></span>|<span data-ttu-id="74f98-117">请勿禁止缓存发生的绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="74f98-117">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="74f98-118">这是默认绑定行为，从 .NET Framework 版本2.0 开始。</span><span class="sxs-lookup"><span data-stu-id="74f98-118">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="74f98-119">1</span><span class="sxs-lookup"><span data-stu-id="74f98-119">1</span></span>|<span data-ttu-id="74f98-120">禁止缓存发生的绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="74f98-120">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="74f98-121">此设置将恢复为 .NET Framework 版本1.1 的绑定行为。</span><span class="sxs-lookup"><span data-stu-id="74f98-121">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74f98-122">子元素</span><span class="sxs-lookup"><span data-stu-id="74f98-122">Child Elements</span></span>  
 <span data-ttu-id="74f98-123">无。</span><span class="sxs-lookup"><span data-stu-id="74f98-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74f98-124">父元素</span><span class="sxs-lookup"><span data-stu-id="74f98-124">Parent Elements</span></span>  
  
|<span data-ttu-id="74f98-125">元素</span><span class="sxs-lookup"><span data-stu-id="74f98-125">Element</span></span>|<span data-ttu-id="74f98-126">描述</span><span class="sxs-lookup"><span data-stu-id="74f98-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="74f98-127">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="74f98-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="74f98-128">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="74f98-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74f98-129">注解</span><span class="sxs-lookup"><span data-stu-id="74f98-129">Remarks</span></span>  
 <span data-ttu-id="74f98-130">从 .NET Framework 版本2.0 开始，加载程序集的默认行为是缓存所有绑定和加载失败。</span><span class="sxs-lookup"><span data-stu-id="74f98-130">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="74f98-131">也就是说，如果尝试加载程序集失败，则加载同一程序集的后续请求将立即失败，而不会尝试查找程序集。</span><span class="sxs-lookup"><span data-stu-id="74f98-131">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="74f98-132">此元素将禁用发生的绑定故障的默认行为，因为在探测路径中找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="74f98-132">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="74f98-133">这些失败会引发 <xref:System.IO.FileNotFoundException> 。</span><span class="sxs-lookup"><span data-stu-id="74f98-133">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="74f98-134">某些绑定和加载失败不受此元素影响，并且始终会进行缓存。</span><span class="sxs-lookup"><span data-stu-id="74f98-134">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="74f98-135">出现这些失败是因为程序集已找到，但无法加载。</span><span class="sxs-lookup"><span data-stu-id="74f98-135">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="74f98-136">它们引发 <xref:System.BadImageFormatException> 或 <xref:System.IO.FileLoadException> 。</span><span class="sxs-lookup"><span data-stu-id="74f98-136">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="74f98-137">以下列表包括此类故障的一些示例。</span><span class="sxs-lookup"><span data-stu-id="74f98-137">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="74f98-138">如果尝试加载文件不是有效的程序集，则即使将错误文件替换为正确的程序集，以后尝试加载程序集也会失败。</span><span class="sxs-lookup"><span data-stu-id="74f98-138">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="74f98-139">如果尝试加载文件系统锁定的程序集，则即使在文件系统释放程序集之后，加载程序集的后续尝试也将失败。</span><span class="sxs-lookup"><span data-stu-id="74f98-139">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="74f98-140">如果尝试加载的程序集的一个或多个版本位于探测路径中，但你请求的特定版本不在其中，则即使将正确的版本移入探测路径，后续尝试加载该版本也会失败。</span><span class="sxs-lookup"><span data-stu-id="74f98-140">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74f98-141">示例</span><span class="sxs-lookup"><span data-stu-id="74f98-141">Example</span></span>  
 <span data-ttu-id="74f98-142">下面的示例演示如何禁止缓存发生的程序集绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="74f98-142">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74f98-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74f98-143">See also</span></span>

- [<span data-ttu-id="74f98-144">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="74f98-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="74f98-145">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="74f98-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="74f98-146">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="74f98-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
