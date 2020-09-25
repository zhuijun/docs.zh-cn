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
ms.openlocfilehash: c9e608bfd54b641564a9095076455e10dd8653fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176118"
---
# <a name="disablecachingbindingfailures-element"></a><span data-ttu-id="c1b7d-102">\<disableCachingBindingFailures> 元素</span><span class="sxs-lookup"><span data-stu-id="c1b7d-102">\<disableCachingBindingFailures> Element</span></span>

<span data-ttu-id="c1b7d-103">指定是否禁止缓存发生的绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a><span data-ttu-id="c1b7d-104">语法</span><span class="sxs-lookup"><span data-stu-id="c1b7d-104">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1b7d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c1b7d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c1b7d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1b7d-107">特性</span><span class="sxs-lookup"><span data-stu-id="c1b7d-107">Attributes</span></span>  
  
|<span data-ttu-id="c1b7d-108">属性</span><span class="sxs-lookup"><span data-stu-id="c1b7d-108">Attribute</span></span>|<span data-ttu-id="c1b7d-109">说明</span><span class="sxs-lookup"><span data-stu-id="c1b7d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1b7d-110">enabled</span><span class="sxs-lookup"><span data-stu-id="c1b7d-110">enabled</span></span>|<span data-ttu-id="c1b7d-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="c1b7d-112">指定是否禁止缓存发生的绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-112">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c1b7d-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="c1b7d-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="c1b7d-114">值</span><span class="sxs-lookup"><span data-stu-id="c1b7d-114">Value</span></span>|<span data-ttu-id="c1b7d-115">描述</span><span class="sxs-lookup"><span data-stu-id="c1b7d-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1b7d-116">0</span><span class="sxs-lookup"><span data-stu-id="c1b7d-116">0</span></span>|<span data-ttu-id="c1b7d-117">请勿禁止缓存发生的绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-117">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="c1b7d-118">这是默认绑定行为，从 .NET Framework 版本2.0 开始。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-118">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="c1b7d-119">1</span><span class="sxs-lookup"><span data-stu-id="c1b7d-119">1</span></span>|<span data-ttu-id="c1b7d-120">禁止缓存发生的绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-120">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="c1b7d-121">此设置将恢复为 .NET Framework 版本1.1 的绑定行为。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-121">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1b7d-122">子元素</span><span class="sxs-lookup"><span data-stu-id="c1b7d-122">Child Elements</span></span>  

 <span data-ttu-id="c1b7d-123">无。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1b7d-124">父元素</span><span class="sxs-lookup"><span data-stu-id="c1b7d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c1b7d-125">元素</span><span class="sxs-lookup"><span data-stu-id="c1b7d-125">Element</span></span>|<span data-ttu-id="c1b7d-126">描述</span><span class="sxs-lookup"><span data-stu-id="c1b7d-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c1b7d-127">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c1b7d-128">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1b7d-129">备注</span><span class="sxs-lookup"><span data-stu-id="c1b7d-129">Remarks</span></span>  

 <span data-ttu-id="c1b7d-130">从 .NET Framework 版本2.0 开始，加载程序集的默认行为是缓存所有绑定和加载失败。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-130">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="c1b7d-131">也就是说，如果尝试加载程序集失败，则加载同一程序集的后续请求将立即失败，而不会尝试查找程序集。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-131">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="c1b7d-132">此元素将禁用发生的绑定故障的默认行为，因为在探测路径中找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-132">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="c1b7d-133">这些失败会引发 <xref:System.IO.FileNotFoundException> 。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-133">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="c1b7d-134">某些绑定和加载失败不受此元素影响，并且始终会进行缓存。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-134">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="c1b7d-135">出现这些失败是因为程序集已找到，但无法加载。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-135">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="c1b7d-136">它们引发 <xref:System.BadImageFormatException> 或 <xref:System.IO.FileLoadException> 。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-136">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="c1b7d-137">以下列表包括此类故障的一些示例。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-137">The following list includes some examples of such failures.</span></span>  
  
- <span data-ttu-id="c1b7d-138">如果尝试加载文件不是有效的程序集，则即使将错误文件替换为正确的程序集，以后尝试加载程序集也会失败。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-138">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
- <span data-ttu-id="c1b7d-139">如果尝试加载文件系统锁定的程序集，则即使在文件系统释放程序集之后，加载程序集的后续尝试也将失败。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-139">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
- <span data-ttu-id="c1b7d-140">如果尝试加载的程序集的一个或多个版本位于探测路径中，但你请求的特定版本不在其中，则即使将正确的版本移入探测路径，后续尝试加载该版本也会失败。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-140">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b7d-141">示例</span><span class="sxs-lookup"><span data-stu-id="c1b7d-141">Example</span></span>  

 <span data-ttu-id="c1b7d-142">下面的示例演示如何禁止缓存发生的程序集绑定故障，因为探查找不到该程序集。</span><span class="sxs-lookup"><span data-stu-id="c1b7d-142">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1b7d-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="c1b7d-143">See also</span></span>

- [<span data-ttu-id="c1b7d-144">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="c1b7d-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c1b7d-145">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c1b7d-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c1b7d-146">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="c1b7d-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
