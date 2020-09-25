---
title: <trace> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 617b42a0be2be272a78b33be997cce632d1c6dcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198920"
---
# <a name="trace-element"></a><span data-ttu-id="39f86-102">\<trace> 元素</span><span class="sxs-lookup"><span data-stu-id="39f86-102">\<trace> Element</span></span>

<span data-ttu-id="39f86-103">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="39f86-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="39f86-104">语法</span><span class="sxs-lookup"><span data-stu-id="39f86-104">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39f86-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="39f86-105">Attributes and Elements</span></span>  

 <span data-ttu-id="39f86-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="39f86-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39f86-107">特性</span><span class="sxs-lookup"><span data-stu-id="39f86-107">Attributes</span></span>  
  
|<span data-ttu-id="39f86-108">属性</span><span class="sxs-lookup"><span data-stu-id="39f86-108">Attribute</span></span>|<span data-ttu-id="39f86-109">描述</span><span class="sxs-lookup"><span data-stu-id="39f86-109">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="39f86-110">可选特性。</span><span class="sxs-lookup"><span data-stu-id="39f86-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="39f86-111">指定跟踪侦听器是否在每次写入操作后自动刷新输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="39f86-111">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="39f86-112">可选特性。</span><span class="sxs-lookup"><span data-stu-id="39f86-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="39f86-113">指定缩进的空格数。</span><span class="sxs-lookup"><span data-stu-id="39f86-113">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="39f86-114">可选特性。</span><span class="sxs-lookup"><span data-stu-id="39f86-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="39f86-115">指示是否应使用全局锁。</span><span class="sxs-lookup"><span data-stu-id="39f86-115">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="39f86-116">autoflush 特性</span><span class="sxs-lookup"><span data-stu-id="39f86-116">autoflush Attribute</span></span>  
  
|<span data-ttu-id="39f86-117">值</span><span class="sxs-lookup"><span data-stu-id="39f86-117">Value</span></span>|<span data-ttu-id="39f86-118">描述</span><span class="sxs-lookup"><span data-stu-id="39f86-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="39f86-119">不会自动刷新输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="39f86-119">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="39f86-120">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="39f86-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="39f86-121">自动刷新输出缓冲区。</span><span class="sxs-lookup"><span data-stu-id="39f86-121">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="39f86-122">useGlobalLock 特性</span><span class="sxs-lookup"><span data-stu-id="39f86-122">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="39f86-123">值</span><span class="sxs-lookup"><span data-stu-id="39f86-123">Value</span></span>|<span data-ttu-id="39f86-124">描述</span><span class="sxs-lookup"><span data-stu-id="39f86-124">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="39f86-125">如果侦听器是线程安全的，则不使用全局锁定;否则，将使用全局锁。</span><span class="sxs-lookup"><span data-stu-id="39f86-125">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="39f86-126">无论侦听器是否是线程安全的，都使用全局锁。</span><span class="sxs-lookup"><span data-stu-id="39f86-126">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="39f86-127">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="39f86-127">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39f86-128">子元素</span><span class="sxs-lookup"><span data-stu-id="39f86-128">Child Elements</span></span>  
  
|<span data-ttu-id="39f86-129">元素</span><span class="sxs-lookup"><span data-stu-id="39f86-129">Element</span></span>|<span data-ttu-id="39f86-130">描述</span><span class="sxs-lookup"><span data-stu-id="39f86-130">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="39f86-131">指定用于收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="39f86-131">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39f86-132">父元素</span><span class="sxs-lookup"><span data-stu-id="39f86-132">Parent Elements</span></span>  
  
|<span data-ttu-id="39f86-133">元素</span><span class="sxs-lookup"><span data-stu-id="39f86-133">Element</span></span>|<span data-ttu-id="39f86-134">描述</span><span class="sxs-lookup"><span data-stu-id="39f86-134">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39f86-135">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="39f86-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="39f86-136">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="39f86-136">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39f86-137">示例</span><span class="sxs-lookup"><span data-stu-id="39f86-137">Example</span></span>  

 <span data-ttu-id="39f86-138">下面的示例演示如何使用 `<trace>` 元素将侦听器添加 `MyListener` 到 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="39f86-138">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="39f86-139">`MyListener` 创建一个名为的文件 `MyListener.log` ，并将输出写入文件。</span><span class="sxs-lookup"><span data-stu-id="39f86-139">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="39f86-140">`useGlobalLock` `false` 如果跟踪侦听器是线程安全的，则属性设置为，这将导致不会使用全局锁。</span><span class="sxs-lookup"><span data-stu-id="39f86-140">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="39f86-141">`autoflush`特性设置为 `true` ，这将导致跟踪侦听器写入文件，而不管是否 <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> 调用了方法。</span><span class="sxs-lookup"><span data-stu-id="39f86-141">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="39f86-142">`indentsize`特性设置为 0 (零) ，这将导致侦听器在调用方法时缩进零个空格 <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="39f86-142">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39f86-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="39f86-143">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="39f86-144">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="39f86-144">Trace and Debug Settings Schema</span></span>](index.md)
