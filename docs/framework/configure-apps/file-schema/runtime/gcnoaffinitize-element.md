---
title: GCNoAffinitize 元素
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "84004733"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="a5465-102">\<GCNoAffinitize> 元素</span><span class="sxs-lookup"><span data-stu-id="a5465-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="a5465-103">指定是否关联服务器 GC 线程与 Cpu。</span><span class="sxs-lookup"><span data-stu-id="a5465-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="a5465-104">语法</span><span class="sxs-lookup"><span data-stu-id="a5465-104">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5465-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a5465-105">Attributes and elements</span></span>

<span data-ttu-id="a5465-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a5465-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5465-107">特性</span><span class="sxs-lookup"><span data-stu-id="a5465-107">Attributes</span></span>

|<span data-ttu-id="a5465-108">属性</span><span class="sxs-lookup"><span data-stu-id="a5465-108">Attribute</span></span>|<span data-ttu-id="a5465-109">说明</span><span class="sxs-lookup"><span data-stu-id="a5465-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a5465-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="a5465-110">Required attribute.</span></span><br /><br /><span data-ttu-id="a5465-111">指定服务器 GC 线程/堆是否与计算机上可用的处理器关联。</span><span class="sxs-lookup"><span data-stu-id="a5465-111">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="a5465-112">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="a5465-112">enabled attribute</span></span>

|<span data-ttu-id="a5465-113">值</span><span class="sxs-lookup"><span data-stu-id="a5465-113">Value</span></span>|<span data-ttu-id="a5465-114">说明</span><span class="sxs-lookup"><span data-stu-id="a5465-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a5465-115">包含 Cpu 的关联服务器 GC 线程。</span><span class="sxs-lookup"><span data-stu-id="a5465-115">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="a5465-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="a5465-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="a5465-117">不关联具有 Cpu 的服务器垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="a5465-117">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a5465-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a5465-118">Child elements</span></span>

<span data-ttu-id="a5465-119">无。</span><span class="sxs-lookup"><span data-stu-id="a5465-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a5465-120">父元素</span><span class="sxs-lookup"><span data-stu-id="a5465-120">Parent elements</span></span>

|<span data-ttu-id="a5465-121">元素</span><span class="sxs-lookup"><span data-stu-id="a5465-121">Element</span></span>|<span data-ttu-id="a5465-122">描述</span><span class="sxs-lookup"><span data-stu-id="a5465-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a5465-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="a5465-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a5465-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="a5465-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5465-125">注解</span><span class="sxs-lookup"><span data-stu-id="a5465-125">Remarks</span></span>

<span data-ttu-id="a5465-126">默认情况下，服务器 GC 线程使用各自的 Cpu 进行关联。</span><span class="sxs-lookup"><span data-stu-id="a5465-126">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="a5465-127">系统的每个可用处理器都有其自己的 GC 堆和线程。</span><span class="sxs-lookup"><span data-stu-id="a5465-127">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="a5465-128">这通常是首选的设置，因为它会优化缓存使用量。</span><span class="sxs-lookup"><span data-stu-id="a5465-128">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="a5465-129">从 .NET Framework 4.6.2 开始，通过将**GCNoAffinitize**元素的 `enabled` 属性设置为 `true` ，可以指定服务器 GC 线程和 cpu 不应紧耦合。</span><span class="sxs-lookup"><span data-stu-id="a5465-129">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="a5465-130">您可以单独指定**GCNoAffinitize**配置元素，以不关联服务器 GC 线程与 cpu 一起工作。</span><span class="sxs-lookup"><span data-stu-id="a5465-130">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="a5465-131">你还可以将它与[GCHeapCount](gcheapcount-element.md)元素结合使用，以控制应用程序使用的垃圾回收堆和线程的数目。</span><span class="sxs-lookup"><span data-stu-id="a5465-131">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="a5465-132">如果 `enabled` **GCNoAffinitize**元素的属性是 `false` （其默认值），则还可以使用[GCHeapCount](gcheapcount-element.md)元素来指定垃圾回收器线程和堆的数目，并使用[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md)元素来指定 gc 线程和堆关联的处理器。</span><span class="sxs-lookup"><span data-stu-id="a5465-132">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="a5465-133">示例</span><span class="sxs-lookup"><span data-stu-id="a5465-133">Example</span></span>

<span data-ttu-id="a5465-134">以下示例不关联服务器 GC 线程：</span><span class="sxs-lookup"><span data-stu-id="a5465-134">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="a5465-135">以下示例不关联服务器 GC 线程，并将 GC 堆/线程数限制为10：</span><span class="sxs-lookup"><span data-stu-id="a5465-135">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a5465-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a5465-136">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a5465-137">GCHeapAffinitizeMask 元素</span><span class="sxs-lookup"><span data-stu-id="a5465-137">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="a5465-138">GCHeapCount 元素</span><span class="sxs-lookup"><span data-stu-id="a5465-138">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="a5465-139">垃圾回收的基本知识</span><span class="sxs-lookup"><span data-stu-id="a5465-139">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="a5465-140">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="a5465-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a5465-141">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="a5465-141">Configuration File Schema</span></span>](../index.md)
