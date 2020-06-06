---
title: t 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102900"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="65969-102">\<gcConcurrent> 元素</span><span class="sxs-lookup"><span data-stu-id="65969-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="65969-103">指定公共语言运行时是否在单独线程上运行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="65969-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="65969-104">语法</span><span class="sxs-lookup"><span data-stu-id="65969-104">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65969-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="65969-105">Attributes and elements</span></span>

<span data-ttu-id="65969-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="65969-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="65969-107">特性</span><span class="sxs-lookup"><span data-stu-id="65969-107">Attributes</span></span>

|<span data-ttu-id="65969-108">属性</span><span class="sxs-lookup"><span data-stu-id="65969-108">Attribute</span></span>|<span data-ttu-id="65969-109">说明</span><span class="sxs-lookup"><span data-stu-id="65969-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="65969-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="65969-110">Required attribute.</span></span><br /><br /><span data-ttu-id="65969-111">指定运行时是否并发运行服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="65969-111">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="65969-112">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="65969-112">enabled attribute</span></span>

|<span data-ttu-id="65969-113">值</span><span class="sxs-lookup"><span data-stu-id="65969-113">Value</span></span>|<span data-ttu-id="65969-114">说明</span><span class="sxs-lookup"><span data-stu-id="65969-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="65969-115">不并发运行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="65969-115">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="65969-116">并发运行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="65969-116">Runs garbage collection concurrently.</span></span> <span data-ttu-id="65969-117">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="65969-117">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="65969-118">子元素</span><span class="sxs-lookup"><span data-stu-id="65969-118">Child elements</span></span>

<span data-ttu-id="65969-119">无。</span><span class="sxs-lookup"><span data-stu-id="65969-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65969-120">父元素</span><span class="sxs-lookup"><span data-stu-id="65969-120">Parent elements</span></span>

|<span data-ttu-id="65969-121">元素</span><span class="sxs-lookup"><span data-stu-id="65969-121">Element</span></span>|<span data-ttu-id="65969-122">描述</span><span class="sxs-lookup"><span data-stu-id="65969-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="65969-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="65969-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="65969-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="65969-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="65969-125">注解</span><span class="sxs-lookup"><span data-stu-id="65969-125">Remarks</span></span>

<span data-ttu-id="65969-126">在 .NET Framework 4 之前，工作站垃圾回收支持并发垃圾回收，这会在单独的线程上以后台执行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="65969-126">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="65969-127">在 .NET Framework 4 中，并发垃圾回收已替换为后台 GC，此操作还在单独的线程上的后台执行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="65969-127">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="65969-128">从 .NET Framework 4.5 开始，后台收集在服务器垃圾回收中变为可用。</span><span class="sxs-lookup"><span data-stu-id="65969-128">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="65969-129">**T**元素控制运行时是执行并发还是后台垃圾回收（如果可用），或者是否执行前台垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="65969-129">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="65969-130">禁用后台垃圾回收</span><span class="sxs-lookup"><span data-stu-id="65969-130">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="65969-131">从 .NET Framework 4 开始，将由后台垃圾回收取代了并发垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="65969-131">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="65969-132">在 .NET Framework 文档中，术语 "*并发*" 和 "*背景*" 可互换使用。</span><span class="sxs-lookup"><span data-stu-id="65969-132">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="65969-133">若要禁用后台垃圾回收，请使用**t**元素，如本文所述。</span><span class="sxs-lookup"><span data-stu-id="65969-133">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="65969-134">默认情况下，运行时使用并发或后台垃圾回收，回收针对延迟进行了优化。</span><span class="sxs-lookup"><span data-stu-id="65969-134">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="65969-135">如果应用程序涉及大量用户交互，则通过让并发垃圾回收保持启用状态，可最大限度缩短应用程序执行垃圾回收时的暂停时间。</span><span class="sxs-lookup"><span data-stu-id="65969-135">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="65969-136">如果将 `enabled` **t**元素的属性设置为，则 `false` 运行时将使用非并发垃圾回收，这是针对吞吐量进行优化的。</span><span class="sxs-lookup"><span data-stu-id="65969-136">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="65969-137">以下配置文件禁用后台垃圾回收：</span><span class="sxs-lookup"><span data-stu-id="65969-137">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="65969-138">如果计算机配置文件中存在**gcConcurrentSetting**设置，则它将为所有 .NET Framework 应用程序定义默认值。</span><span class="sxs-lookup"><span data-stu-id="65969-138">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="65969-139">计算机配置文件设置将重写应用程序配置文件设置。</span><span class="sxs-lookup"><span data-stu-id="65969-139">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="65969-140">有关并发和后台垃圾回收的详细信息，请参阅[后台垃圾](../../../../standard/garbage-collection/background-gc.md)回收。</span><span class="sxs-lookup"><span data-stu-id="65969-140">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="65969-141">示例</span><span class="sxs-lookup"><span data-stu-id="65969-141">Example</span></span>

<span data-ttu-id="65969-142">下面的示例启用后台垃圾回收：</span><span class="sxs-lookup"><span data-stu-id="65969-142">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="65969-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65969-143">See also</span></span>

- [<span data-ttu-id="65969-144">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="65969-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="65969-145">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="65969-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="65969-146">垃圾回收基础</span><span class="sxs-lookup"><span data-stu-id="65969-146">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
