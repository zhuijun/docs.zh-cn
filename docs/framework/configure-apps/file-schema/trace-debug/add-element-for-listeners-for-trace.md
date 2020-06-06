---
title: <add>的元素 <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153667"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="3355c-102">\<add>的元素 \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="3355c-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="3355c-103">向**侦听器**集合添加侦听器。</span><span class="sxs-lookup"><span data-stu-id="3355c-103">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="3355c-104">语法</span><span class="sxs-lookup"><span data-stu-id="3355c-104">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3355c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3355c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3355c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3355c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3355c-107">特性</span><span class="sxs-lookup"><span data-stu-id="3355c-107">Attributes</span></span>  
  
|<span data-ttu-id="3355c-108">属性</span><span class="sxs-lookup"><span data-stu-id="3355c-108">Attribute</span></span>|<span data-ttu-id="3355c-109">说明</span><span class="sxs-lookup"><span data-stu-id="3355c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3355c-110">type</span><span class="sxs-lookup"><span data-stu-id="3355c-110">**type**</span></span>|<span data-ttu-id="3355c-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="3355c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="3355c-112">指定侦听器的类型。</span><span class="sxs-lookup"><span data-stu-id="3355c-112">Specifies the type of the listener.</span></span> <span data-ttu-id="3355c-113">必须使用满足指定[完全限定的类型名称](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)中指定的要求的字符串。</span><span class="sxs-lookup"><span data-stu-id="3355c-113">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="3355c-114">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="3355c-114">**initializeData**</span></span>|<span data-ttu-id="3355c-115">可选特性。</span><span class="sxs-lookup"><span data-stu-id="3355c-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3355c-116">传递到指定类的构造函数的字符串。</span><span class="sxs-lookup"><span data-stu-id="3355c-116">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="3355c-117">**name**</span><span class="sxs-lookup"><span data-stu-id="3355c-117">**name**</span></span>|<span data-ttu-id="3355c-118">可选特性。</span><span class="sxs-lookup"><span data-stu-id="3355c-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3355c-119">指定侦听器的名称。</span><span class="sxs-lookup"><span data-stu-id="3355c-119">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3355c-120">子元素</span><span class="sxs-lookup"><span data-stu-id="3355c-120">Child Elements</span></span>  
  
|<span data-ttu-id="3355c-121">元素</span><span class="sxs-lookup"><span data-stu-id="3355c-121">Element</span></span>|<span data-ttu-id="3355c-122">描述</span><span class="sxs-lookup"><span data-stu-id="3355c-122">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="3355c-123">将筛选器添加到跟踪的集合中的侦听器 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="3355c-123">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3355c-124">父元素</span><span class="sxs-lookup"><span data-stu-id="3355c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3355c-125">元素</span><span class="sxs-lookup"><span data-stu-id="3355c-125">Element</span></span>|<span data-ttu-id="3355c-126">描述</span><span class="sxs-lookup"><span data-stu-id="3355c-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3355c-127">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="3355c-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="3355c-128">指定用于收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="3355c-128">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="3355c-129">侦听器将跟踪输出定向到适当的目标。</span><span class="sxs-lookup"><span data-stu-id="3355c-129">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3355c-130">为 ASP.NET 配置节指定根元素。</span><span class="sxs-lookup"><span data-stu-id="3355c-130">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="3355c-131">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="3355c-131">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3355c-132">注解</span><span class="sxs-lookup"><span data-stu-id="3355c-132">Remarks</span></span>  
 <span data-ttu-id="3355c-133"><xref:System.Diagnostics.Debug>和 <xref:System.Diagnostics.Trace> 类共享相同的**侦听器**集合。</span><span class="sxs-lookup"><span data-stu-id="3355c-133">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="3355c-134">如果将侦听器对象添加到其中一个类的集合中，则其他类将使用同一侦听器。</span><span class="sxs-lookup"><span data-stu-id="3355c-134">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="3355c-135">侦听器类派生自 <xref:System.Diagnostics.TraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="3355c-135">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="3355c-136">如果未指定 `name` 跟踪侦听器的属性，则 <xref:System.Diagnostics.TraceListener.Name%2A> 跟踪侦听器的默认值为空字符串（""）。</span><span class="sxs-lookup"><span data-stu-id="3355c-136">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="3355c-137">如果你的应用程序只有一个侦听器，则可以在不指定名称的情况下进行添加，并通过为该名称指定一个空字符串来将其删除。</span><span class="sxs-lookup"><span data-stu-id="3355c-137">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="3355c-138">但是，如果应用程序有多个侦听器，则应为每个跟踪侦听器指定唯一的名称，以便在和集合中标识和管理单个跟踪侦听器 <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3355c-138">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3355c-139">添加具有相同类型且具有相同名称的多个跟踪侦听器会导致只将该类型和名称的一个跟踪侦听器添加到 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="3355c-139">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="3355c-140">但是，可以通过编程方式将多个相同的侦听器添加到 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="3355c-140">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="3355c-141">**InitializeData**属性的值取决于所创建的侦听器的类型。</span><span class="sxs-lookup"><span data-stu-id="3355c-141">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="3355c-142">并非所有跟踪侦听器都需要指定**initializeData**。</span><span class="sxs-lookup"><span data-stu-id="3355c-142">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3355c-143">使用 `initializeData` 属性时，可能会收到编译器警告 "未声明 ' initializeData ' 特性"。</span><span class="sxs-lookup"><span data-stu-id="3355c-143">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="3355c-144">之所以出现此警告，是因为配置设置是针对抽象基类验证的 <xref:System.Diagnostics.TraceListener> ，后者不识别 `initializeData` 属性。</span><span class="sxs-lookup"><span data-stu-id="3355c-144">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="3355c-145">通常，对于具有采用参数的构造函数的跟踪侦听器实现，你可以忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="3355c-145">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="3355c-146">下表显示了 .NET Framework 附带的跟踪侦听器，并说明了其**initializeData**属性的值。</span><span class="sxs-lookup"><span data-stu-id="3355c-146">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="3355c-147">跟踪侦听器类</span><span class="sxs-lookup"><span data-stu-id="3355c-147">Trace listener class</span></span>|<span data-ttu-id="3355c-148">initializeData 特性值</span><span class="sxs-lookup"><span data-stu-id="3355c-148">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3355c-149">`useErrorStream`构造函数的值 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3355c-149">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="3355c-150">将 `initializeData` 属性设置为 " `true` " 可将跟踪和调试输出写入 <xref:System.Console.Error%2A?displayProperty=nameWithType> ;`false`要写入的 "" <xref:System.Console.Out%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="3355c-150">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3355c-151"><xref:System.Diagnostics.DelimitedListTraceListener> 写入的文件名。</span><span class="sxs-lookup"><span data-stu-id="3355c-151">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3355c-152">现有事件日志源的名称。</span><span class="sxs-lookup"><span data-stu-id="3355c-152">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3355c-153">写入的文件的名称 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="3355c-153">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3355c-154">写入的文件的名称 <xref:System.Diagnostics.TextWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="3355c-154">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3355c-155">写入的文件的名称 <xref:System.Diagnostics.XmlWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="3355c-155">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3355c-156">示例</span><span class="sxs-lookup"><span data-stu-id="3355c-156">Example</span></span>  
 <span data-ttu-id="3355c-157">下面的示例演示如何使用 **\<add>** 元素将侦听器 `MyListener` 和 `MyEventListener` 侦听器集合添加到**侦听器**。</span><span class="sxs-lookup"><span data-stu-id="3355c-157">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="3355c-158">`MyListener`创建一个名为的文件 `MyListener.log` ，并将输出写入文件。</span><span class="sxs-lookup"><span data-stu-id="3355c-158">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="3355c-159">`MyEventListener`在事件日志中创建一个条目。</span><span class="sxs-lookup"><span data-stu-id="3355c-159">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3355c-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3355c-160">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="3355c-161">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="3355c-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3355c-162">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="3355c-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
