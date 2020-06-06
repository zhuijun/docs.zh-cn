---
title: <> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153202"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="e8898-102">\<system.diagnostics> 元素</span><span class="sxs-lookup"><span data-stu-id="e8898-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="e8898-103">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="e8898-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="e8898-104">语法</span><span class="sxs-lookup"><span data-stu-id="e8898-104">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8898-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e8898-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e8898-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e8898-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8898-107">特性</span><span class="sxs-lookup"><span data-stu-id="e8898-107">Attributes</span></span>  
 <span data-ttu-id="e8898-108">无。</span><span class="sxs-lookup"><span data-stu-id="e8898-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8898-109">子元素</span><span class="sxs-lookup"><span data-stu-id="e8898-109">Child Elements</span></span>  
  
|<span data-ttu-id="e8898-110">元素</span><span class="sxs-lookup"><span data-stu-id="e8898-110">Element</span></span>|<span data-ttu-id="e8898-111">说明</span><span class="sxs-lookup"><span data-stu-id="e8898-111">Description</span></span>|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|<span data-ttu-id="e8898-112">指定调用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法时是否显示消息框；另外指定要写入消息的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="e8898-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="e8898-113">指定由性能计数器共享的全局内存的大小。</span><span class="sxs-lookup"><span data-stu-id="e8898-113">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="e8898-114">包含任何源或跟踪元素可以引用的侦听器。</span><span class="sxs-lookup"><span data-stu-id="e8898-114">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="e8898-115">可以按名称将标识为共享侦听器的侦听器添加到源或跟踪。</span><span class="sxs-lookup"><span data-stu-id="e8898-115">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="e8898-116">指定启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="e8898-116">Specifies trace sources that initiate tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="e8898-117">包含跟踪开关和设置跟踪开关的级别。</span><span class="sxs-lookup"><span data-stu-id="e8898-117">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="e8898-118">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="e8898-118">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8898-119">父元素</span><span class="sxs-lookup"><span data-stu-id="e8898-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e8898-120">元素</span><span class="sxs-lookup"><span data-stu-id="e8898-120">Element</span></span>|<span data-ttu-id="e8898-121">说明</span><span class="sxs-lookup"><span data-stu-id="e8898-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e8898-122">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="e8898-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e8898-123">示例</span><span class="sxs-lookup"><span data-stu-id="e8898-123">Example</span></span>  
 <span data-ttu-id="e8898-124">下面的示例演示如何在元素内嵌入跟踪开关和跟踪侦听器 **\<system.diagnostics>** 。</span><span class="sxs-lookup"><span data-stu-id="e8898-124">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="e8898-125">`General`跟踪开关设置为 <xref:System.Diagnostics.TraceLevel> 级别。</span><span class="sxs-lookup"><span data-stu-id="e8898-125">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="e8898-126">跟踪侦听器会 `myListener` 创建一个名为的文件 `MyListener.log` ，并将输出写入文件。</span><span class="sxs-lookup"><span data-stu-id="e8898-126">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8898-127">在 .NET Framework 2.0 版中，你可以使用文本指定开关值。</span><span class="sxs-lookup"><span data-stu-id="e8898-127">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="e8898-128">例如，你可以为指定， `true` <xref:System.Diagnostics.BooleanSwitch> 也可以使用表示枚举值的文本（例如） `Error` <xref:System.Diagnostics.TraceSwitch> 。</span><span class="sxs-lookup"><span data-stu-id="e8898-128">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="e8898-129">行 `<add name="myTraceSwitch" value="Error" />` 等于 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="e8898-129">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8898-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8898-130">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="e8898-131">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="e8898-131">Trace and Debug Settings Schema</span></span>](index.md)
