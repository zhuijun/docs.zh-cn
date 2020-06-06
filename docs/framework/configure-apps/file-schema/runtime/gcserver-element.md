---
title: r 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968946"
---
# <a name="gcserver-element"></a><span data-ttu-id="6aad6-102">\<gcServer> 元素</span><span class="sxs-lookup"><span data-stu-id="6aad6-102">\<gcServer> element</span></span>

<span data-ttu-id="6aad6-103">指定公共语言运行时是否运行服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="6aad6-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="6aad6-104">语法</span><span class="sxs-lookup"><span data-stu-id="6aad6-104">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6aad6-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6aad6-105">Attributes and elements</span></span>

<span data-ttu-id="6aad6-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6aad6-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6aad6-107">特性</span><span class="sxs-lookup"><span data-stu-id="6aad6-107">Attributes</span></span>

|<span data-ttu-id="6aad6-108">属性</span><span class="sxs-lookup"><span data-stu-id="6aad6-108">Attribute</span></span>|<span data-ttu-id="6aad6-109">说明</span><span class="sxs-lookup"><span data-stu-id="6aad6-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="6aad6-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="6aad6-110">Required attribute.</span></span><br /><br /><span data-ttu-id="6aad6-111">指定运行时是否运行服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="6aad6-111">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="6aad6-112">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="6aad6-112">enabled attribute</span></span>

|<span data-ttu-id="6aad6-113">值</span><span class="sxs-lookup"><span data-stu-id="6aad6-113">Value</span></span>|<span data-ttu-id="6aad6-114">说明</span><span class="sxs-lookup"><span data-stu-id="6aad6-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="6aad6-115">请勿运行服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="6aad6-115">Does not run server garbage collection.</span></span> <span data-ttu-id="6aad6-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="6aad6-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="6aad6-117">运行服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="6aad6-117">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6aad6-118">子元素</span><span class="sxs-lookup"><span data-stu-id="6aad6-118">Child elements</span></span>

<span data-ttu-id="6aad6-119">无。</span><span class="sxs-lookup"><span data-stu-id="6aad6-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6aad6-120">父元素</span><span class="sxs-lookup"><span data-stu-id="6aad6-120">Parent elements</span></span>

|<span data-ttu-id="6aad6-121">元素</span><span class="sxs-lookup"><span data-stu-id="6aad6-121">Element</span></span>|<span data-ttu-id="6aad6-122">描述</span><span class="sxs-lookup"><span data-stu-id="6aad6-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="6aad6-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="6aad6-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="6aad6-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="6aad6-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6aad6-125">注解</span><span class="sxs-lookup"><span data-stu-id="6aad6-125">Remarks</span></span>

<span data-ttu-id="6aad6-126">公共语言运行时 (CLR) 支持两种类型的垃圾回收：工作站垃圾回收（适用于所有系统）和服务器垃圾回收（适用于多处理器系统）。</span><span class="sxs-lookup"><span data-stu-id="6aad6-126">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="6aad6-127">使用**r**元素可控制 CLR 执行的垃圾回收的类型。</span><span class="sxs-lookup"><span data-stu-id="6aad6-127">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="6aad6-128">使用 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> 属性以确定是否启用服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="6aad6-128">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="6aad6-129">对于单处理器计算机，默认的工作站垃圾回收应该是最快捷的选项。</span><span class="sxs-lookup"><span data-stu-id="6aad6-129">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="6aad6-130">对于双处理器计算机，最快捷的选项既可以是工作站垃圾回收又可以是服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="6aad6-130">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="6aad6-131">对于两个以上处理器的计算机，服务器垃圾回收应该是最快捷的选项。</span><span class="sxs-lookup"><span data-stu-id="6aad6-131">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="6aad6-132">在同一台计算机上运行多个服务器应用实例时，最常见的多处理器服务器系统禁用服务器 GC 并使用工作站 GC。</span><span class="sxs-lookup"><span data-stu-id="6aad6-132">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="6aad6-133">此元素只能在应用程序配置文件中使用；如果此元素在计算机配置文件中，请忽略。</span><span class="sxs-lookup"><span data-stu-id="6aad6-133">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="6aad6-134">在 .NET Framework 4 和更低版本中，启用服务器垃圾回收之后，并发垃圾回收不可用。</span><span class="sxs-lookup"><span data-stu-id="6aad6-134">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="6aad6-135">从 .NET Framework 4.5 开始，服务器垃圾回收将并发执行。</span><span class="sxs-lookup"><span data-stu-id="6aad6-135">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="6aad6-136">若要使用非并发服务器垃圾回收，请将**r**元素设置为， `true` 并将[t 元素](gcconcurrent-element.md)设置为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="6aad6-136">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="6aad6-137">从 .NET Framework 4.6.2 开始，你还可以使用以下元素来配置服务器 GC：</span><span class="sxs-lookup"><span data-stu-id="6aad6-137">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="6aad6-138">[GCNoAffinitize](gcnoaffinitize-element.md)，用于指定服务器 GC 堆与处理器之间是否存在关联。</span><span class="sxs-lookup"><span data-stu-id="6aad6-138">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="6aad6-139">默认情况下，每个处理器都有一个服务器 GC 堆。</span><span class="sxs-lookup"><span data-stu-id="6aad6-139">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="6aad6-140">[GCHeapCount](gcheapcount-element.md)，用于限制进程使用的堆数。</span><span class="sxs-lookup"><span data-stu-id="6aad6-140">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="6aad6-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)，用于定义可用服务器 GC 堆和单个处理器之间的关联。</span><span class="sxs-lookup"><span data-stu-id="6aad6-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="6aad6-142">示例</span><span class="sxs-lookup"><span data-stu-id="6aad6-142">Example</span></span>

<span data-ttu-id="6aad6-143">下面的示例启用服务器垃圾回收：</span><span class="sxs-lookup"><span data-stu-id="6aad6-143">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6aad6-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6aad6-144">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6aad6-145">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="6aad6-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6aad6-146">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="6aad6-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6aad6-147">禁用并发垃圾回收</span><span class="sxs-lookup"><span data-stu-id="6aad6-147">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
