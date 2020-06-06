---
title: GCHeapCount 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74283074"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="5d2ba-102">\<GCHeapCount> 元素</span><span class="sxs-lookup"><span data-stu-id="5d2ba-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="5d2ba-103">指定用于服务器垃圾回收的堆/线程数。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a><span data-ttu-id="5d2ba-104">语法</span><span class="sxs-lookup"><span data-stu-id="5d2ba-104">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d2ba-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5d2ba-105">Attributes and elements</span></span>

<span data-ttu-id="5d2ba-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d2ba-107">特性</span><span class="sxs-lookup"><span data-stu-id="5d2ba-107">Attributes</span></span>

|<span data-ttu-id="5d2ba-108">属性</span><span class="sxs-lookup"><span data-stu-id="5d2ba-108">Attribute</span></span>|<span data-ttu-id="5d2ba-109">说明</span><span class="sxs-lookup"><span data-stu-id="5d2ba-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="5d2ba-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-110">Required attribute.</span></span><br /><br /><span data-ttu-id="5d2ba-111">指定用于服务器垃圾回收的堆数。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-111">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="5d2ba-112">堆的实际数量是指定的堆数的最小值以及允许进程使用的处理器数。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-112">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="5d2ba-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="5d2ba-113">enabled attribute</span></span>

|<span data-ttu-id="5d2ba-114">值</span><span class="sxs-lookup"><span data-stu-id="5d2ba-114">Value</span></span>|<span data-ttu-id="5d2ba-115">说明</span><span class="sxs-lookup"><span data-stu-id="5d2ba-115">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="5d2ba-116">要用于服务器 GC 的堆数。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-116">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5d2ba-117">子元素</span><span class="sxs-lookup"><span data-stu-id="5d2ba-117">Child elements</span></span>

<span data-ttu-id="5d2ba-118">无。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d2ba-119">父元素</span><span class="sxs-lookup"><span data-stu-id="5d2ba-119">Parent elements</span></span>

|<span data-ttu-id="5d2ba-120">元素</span><span class="sxs-lookup"><span data-stu-id="5d2ba-120">Element</span></span>|<span data-ttu-id="5d2ba-121">描述</span><span class="sxs-lookup"><span data-stu-id="5d2ba-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5d2ba-122">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="5d2ba-123">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5d2ba-124">注解</span><span class="sxs-lookup"><span data-stu-id="5d2ba-124">Remarks</span></span>

<span data-ttu-id="5d2ba-125">默认情况下，服务器 GC 线程使用各自的 CPU 进行关联，以便为每个处理器提供一个 GC 堆、一个服务器 GC 线程，以及一个后台服务器垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-125">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="5d2ba-126">从 .NET Framework 4.6.2 开始，可以使用**GCHeapCount**元素来限制应用程序用于服务器 GC 的堆数。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-126">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="5d2ba-127">如果运行多个服务器应用程序实例的系统，限制用于服务器 GC 的堆数将特别有用。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-127">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="5d2ba-128">**GCHeapCount**通常与其他两个标志一起使用：</span><span class="sxs-lookup"><span data-stu-id="5d2ba-128">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="5d2ba-129">[GCNoAffinitize](gcnoaffinitize-element.md)，控制服务器 GC 线程/堆是否与 cpu 关联。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-129">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="5d2ba-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)，它控制垃圾回收器与 cpu 之间的关联。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="5d2ba-131">如果设置了**GCHeapCount**并禁用了**GCNoAffinitize** （其默认设置），则*nn* GC threads/堆和第一个*nn*处理器之间存在关联。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-131">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="5d2ba-132">您可以使用**GCHeapAffinitizeMask**元素指定进程的服务器 GC 堆使用的处理器。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-132">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="5d2ba-133">否则，如果在一个系统上运行多个服务器进程，其处理器使用率将会重叠。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-133">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="5d2ba-134">如果设置了**GCHeapCount**并启用了**GCNoAffinitize** ，则垃圾回收器会限制服务器 gc 使用的处理器数量，但不会关联 GC 堆和处理器。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-134">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="5d2ba-135">示例</span><span class="sxs-lookup"><span data-stu-id="5d2ba-135">Example</span></span>

<span data-ttu-id="5d2ba-136">下面的示例指示应用程序使用具有10个堆/线程的服务器 GC。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-136">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="5d2ba-137">由于你不希望这些堆与系统上运行的其他应用程序中的堆重叠，因此你可以使用**GCHeapAffinitizeMask**来指定该进程应使用 cpu 0 到9。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-137">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="5d2ba-138">以下示例不关联服务器 GC 线程，并将 GC 堆/线程的数量限制为10个。</span><span class="sxs-lookup"><span data-stu-id="5d2ba-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5d2ba-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d2ba-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5d2ba-140">GCNoAffinitize 元素</span><span class="sxs-lookup"><span data-stu-id="5d2ba-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="5d2ba-141">GCHeapAffinitizeMask 元素</span><span class="sxs-lookup"><span data-stu-id="5d2ba-141">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="5d2ba-142">垃圾回收的基本知识</span><span class="sxs-lookup"><span data-stu-id="5d2ba-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="5d2ba-143">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="5d2ba-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5d2ba-144">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="5d2ba-144">Configuration File Schema</span></span>](../index.md)
