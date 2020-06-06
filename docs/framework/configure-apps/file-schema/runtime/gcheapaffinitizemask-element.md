---
title: GCHeapAffinitizeMask 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978419"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="22def-102">\<GCHeapAffinitizeMask> 元素</span><span class="sxs-lookup"><span data-stu-id="22def-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="22def-103">定义 GC 堆和单个处理器之间的关联。</span><span class="sxs-lookup"><span data-stu-id="22def-103">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="22def-104">语法</span><span class="sxs-lookup"><span data-stu-id="22def-104">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22def-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="22def-105">Attributes and elements</span></span>

<span data-ttu-id="22def-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="22def-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="22def-107">特性</span><span class="sxs-lookup"><span data-stu-id="22def-107">Attributes</span></span>

|<span data-ttu-id="22def-108">属性</span><span class="sxs-lookup"><span data-stu-id="22def-108">Attribute</span></span>|<span data-ttu-id="22def-109">说明</span><span class="sxs-lookup"><span data-stu-id="22def-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="22def-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="22def-110">Required attribute.</span></span><br /><br /><span data-ttu-id="22def-111">指定 GC 堆和单个处理器之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="22def-111">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="22def-112">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="22def-112">enabled attribute</span></span>

|<span data-ttu-id="22def-113">值</span><span class="sxs-lookup"><span data-stu-id="22def-113">Value</span></span>|<span data-ttu-id="22def-114">说明</span><span class="sxs-lookup"><span data-stu-id="22def-114">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="22def-115">一个十进制值，它构成一个位掩码，用于定义服务器 GC 堆和单个处理器之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="22def-115">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="22def-116">子元素</span><span class="sxs-lookup"><span data-stu-id="22def-116">Child elements</span></span>

<span data-ttu-id="22def-117">无。</span><span class="sxs-lookup"><span data-stu-id="22def-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="22def-118">父元素</span><span class="sxs-lookup"><span data-stu-id="22def-118">Parent elements</span></span>

|<span data-ttu-id="22def-119">元素</span><span class="sxs-lookup"><span data-stu-id="22def-119">Element</span></span>|<span data-ttu-id="22def-120">描述</span><span class="sxs-lookup"><span data-stu-id="22def-120">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="22def-121">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="22def-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="22def-122">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="22def-122">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="22def-123">注解</span><span class="sxs-lookup"><span data-stu-id="22def-123">Remarks</span></span>

<span data-ttu-id="22def-124">默认情况下，服务器 GC 线程使用各自的 CPU 进行关联，以便为每个处理器提供一个 GC 堆、一个服务器 GC 线程，以及一个后台服务器垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="22def-124">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="22def-125">从 .NET Framework 4.6.2 开始，当堆数受**GCHeapCount**元素限制时，可以使用**GCHeapAffinitizeMask**元素控制服务器 GC 堆与处理器之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="22def-125">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="22def-126">**GCHeapAffinitizeMask**通常与其他两个标志一起使用：</span><span class="sxs-lookup"><span data-stu-id="22def-126">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="22def-127">[GCNoAffinitize](gcnoaffinitize-element.md)，控制服务器 GC 线程/堆是否与 cpu 关联。</span><span class="sxs-lookup"><span data-stu-id="22def-127">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="22def-128">`enabled` [GCNoAffinitize](gcnoaffinitize-element.md)元素的属性必须为 `false` 要使用的**GCHeapAffinitizeMask**设置的（其默认值）。</span><span class="sxs-lookup"><span data-stu-id="22def-128">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="22def-129">[GCHeapCount](gcheapcount-element.md)，用于限制进程用于服务器 GC 的堆数。</span><span class="sxs-lookup"><span data-stu-id="22def-129">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="22def-130">默认情况下，每个处理器都有一个堆。</span><span class="sxs-lookup"><span data-stu-id="22def-130">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="22def-131">**nnnn**是以十进制值表示的位掩码。</span><span class="sxs-lookup"><span data-stu-id="22def-131">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="22def-132">字节0的位0表示处理器0，第1个字节表示处理器1，依此类推。</span><span class="sxs-lookup"><span data-stu-id="22def-132">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="22def-133">例如：</span><span class="sxs-lookup"><span data-stu-id="22def-133">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="22def-134">值1023为0x3FF 或 0011 1111 1111b。</span><span class="sxs-lookup"><span data-stu-id="22def-134">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="22def-135">此过程使用10个处理器，从处理器0到处理器9。</span><span class="sxs-lookup"><span data-stu-id="22def-135">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="22def-136">示例</span><span class="sxs-lookup"><span data-stu-id="22def-136">Example</span></span>

<span data-ttu-id="22def-137">下面的示例指示应用程序使用具有10个堆/线程的服务器 GC。</span><span class="sxs-lookup"><span data-stu-id="22def-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="22def-138">由于不希望这些堆与系统上运行的其他应用程序中的堆重叠，因此，请使用**GCHeapAffinitizeMask**指定进程应使用 cpu 0 到9。</span><span class="sxs-lookup"><span data-stu-id="22def-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="22def-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22def-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="22def-140">GCNoAffinitize 元素</span><span class="sxs-lookup"><span data-stu-id="22def-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="22def-141">GCHeapCount 元素</span><span class="sxs-lookup"><span data-stu-id="22def-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="22def-142">垃圾回收的基本知识</span><span class="sxs-lookup"><span data-stu-id="22def-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="22def-143">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="22def-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="22def-144">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="22def-144">Configuration File Schema</span></span>](../index.md)
