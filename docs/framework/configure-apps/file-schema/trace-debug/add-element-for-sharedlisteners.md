---
title: <sharedListeners> 的 <add> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: f0ede5f9dc19e9589afc888e7fcd01785bc1840c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174025"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="ad501-102">\<sharedListeners> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="ad501-102">\<add> Element for \<sharedListeners></span></span>

<span data-ttu-id="ad501-103">将侦听器添加到 `sharedListeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="ad501-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="ad501-104">`sharedListeners` 是任何 [\<source>](source-element.md) 或可引用的侦听器的集合 [\<trace>](trace-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="ad501-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="ad501-105">默认情况下，集合中的侦听器 `sharedListeners` 不会放置在 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="ad501-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="ad501-106">必须按名称将它们添加到 [\<source>](source-element.md) 或 [\<trace>](trace-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="ad501-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="ad501-107">在运行时，不能 `sharedListeners` 在代码中获取集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="ad501-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="ad501-108">语法</span><span class="sxs-lookup"><span data-stu-id="ad501-108">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad501-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ad501-109">Attributes and Elements</span></span>  

 <span data-ttu-id="ad501-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ad501-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad501-111">特性</span><span class="sxs-lookup"><span data-stu-id="ad501-111">Attributes</span></span>  
  
|<span data-ttu-id="ad501-112">属性</span><span class="sxs-lookup"><span data-stu-id="ad501-112">Attribute</span></span>|<span data-ttu-id="ad501-113">描述</span><span class="sxs-lookup"><span data-stu-id="ad501-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="ad501-114">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="ad501-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ad501-115">指定用于将共享侦听器添加到集合中的侦听器的名称 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="ad501-115">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="ad501-116">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="ad501-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ad501-117">指定侦听器的类型。</span><span class="sxs-lookup"><span data-stu-id="ad501-117">Specifies the type of the listener.</span></span> <span data-ttu-id="ad501-118">必须使用满足指定 [完全限定的类型名称](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)中指定的要求的字符串。</span><span class="sxs-lookup"><span data-stu-id="ad501-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="ad501-119">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ad501-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ad501-120">传递到指定类的构造函数的字符串。</span><span class="sxs-lookup"><span data-stu-id="ad501-120">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="ad501-121">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ad501-121">Optional attribute.</span></span><br/><br/><span data-ttu-id="ad501-122">指示要写入跟踪输出的数据的一个或多个枚举成员的字符串表示形式 <xref:System.Diagnostics.TraceOptions> 。</span><span class="sxs-lookup"><span data-stu-id="ad501-122">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="ad501-123">多个项之间以逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="ad501-123">Multiple items are separated by commas.</span></span> <span data-ttu-id="ad501-124">默认值为 "None"。</span><span class="sxs-lookup"><span data-stu-id="ad501-124">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ad501-125">子元素</span><span class="sxs-lookup"><span data-stu-id="ad501-125">Child Elements</span></span>  
  
|<span data-ttu-id="ad501-126">元素</span><span class="sxs-lookup"><span data-stu-id="ad501-126">Element</span></span>|<span data-ttu-id="ad501-127">描述</span><span class="sxs-lookup"><span data-stu-id="ad501-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="ad501-128">将筛选器添加到 `sharedListeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="ad501-128">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ad501-129">父元素</span><span class="sxs-lookup"><span data-stu-id="ad501-129">Parent Elements</span></span>  
  
|<span data-ttu-id="ad501-130">元素</span><span class="sxs-lookup"><span data-stu-id="ad501-130">Element</span></span>|<span data-ttu-id="ad501-131">描述</span><span class="sxs-lookup"><span data-stu-id="ad501-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad501-132">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="ad501-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ad501-133">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="ad501-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="ad501-134">任何源或跟踪元素都可以引用的侦听器的集合。</span><span class="sxs-lookup"><span data-stu-id="ad501-134">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad501-135">备注</span><span class="sxs-lookup"><span data-stu-id="ad501-135">Remarks</span></span>  

 <span data-ttu-id="ad501-136">随 .NET Framework 附带的侦听器类派生自 <xref:System.Diagnostics.TraceListener> 类。</span><span class="sxs-lookup"><span data-stu-id="ad501-136">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="ad501-137">特性的值 `name` 用于将共享侦听器添加到 `Listeners` 跟踪源或跟踪源的集合中。</span><span class="sxs-lookup"><span data-stu-id="ad501-137">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="ad501-138">该属性的值 `initializeData` 取决于所创建的侦听器的类型。</span><span class="sxs-lookup"><span data-stu-id="ad501-138">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="ad501-139">并非所有跟踪侦听器都要求您指定 `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="ad501-139">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad501-140">使用 `initializeData` 属性时，可能会收到编译器警告 "未声明 ' initializeData ' 特性"。</span><span class="sxs-lookup"><span data-stu-id="ad501-140">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="ad501-141">之所以出现此警告，是因为配置设置是针对抽象基类验证的 <xref:System.Diagnostics.TraceListener> ，后者不识别 `initializeData` 属性。</span><span class="sxs-lookup"><span data-stu-id="ad501-141">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="ad501-142">通常，对于具有采用参数的构造函数的跟踪侦听器实现，你可以忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="ad501-142">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="ad501-143">下表显示了 .NET Framework 附带的跟踪侦听器，并描述了其属性的值 `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="ad501-143">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="ad501-144">跟踪侦听器类</span><span class="sxs-lookup"><span data-stu-id="ad501-144">Trace listener class</span></span>|<span data-ttu-id="ad501-145">initializeData 特性值</span><span class="sxs-lookup"><span data-stu-id="ad501-145">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="ad501-146">`useErrorStream`构造函数的值 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ad501-146">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="ad501-147">将 `initializeData` 属性设置为 " `true` " 可将跟踪和调试输出写入标准错误流; 将该属性设置为 " `false` " 可写入标准输出流。</span><span class="sxs-lookup"><span data-stu-id="ad501-147">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="ad501-148"><xref:System.Diagnostics.DelimitedListTraceListener> 写入的文件名。</span><span class="sxs-lookup"><span data-stu-id="ad501-148">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ad501-149">现有的事件日志源的名称。</span><span class="sxs-lookup"><span data-stu-id="ad501-149">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ad501-150">写入的文件的名称 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="ad501-150">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="ad501-151">写入的文件的名称 <xref:System.Diagnostics.TextWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="ad501-151">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="ad501-152">写入的文件的名称 <xref:System.Diagnostics.XmlWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="ad501-152">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="ad501-153">配置文件</span><span class="sxs-lookup"><span data-stu-id="ad501-153">Configuration File</span></span>  

 <span data-ttu-id="ad501-154">此元素可在计算机配置文件中使用 ( # A0) 和应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="ad501-154">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad501-155">示例</span><span class="sxs-lookup"><span data-stu-id="ad501-155">Example</span></span>  

 <span data-ttu-id="ad501-156">下面的示例演示如何使用 `<add>` 元素将添加 <xref:System.Diagnostics.TextWriterTraceListener> `textListener` 到 `sharedListeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="ad501-156">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="ad501-157">`textListener` 按名称添加到 `Listeners` 跟踪源的集合中 `TraceSourceApp` 。</span><span class="sxs-lookup"><span data-stu-id="ad501-157">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="ad501-158">`textListener`侦听器将跟踪输出写入文件 myListener。</span><span class="sxs-lookup"><span data-stu-id="ad501-158">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="ad501-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad501-159">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="ad501-160">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="ad501-160">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ad501-161">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="ad501-161">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
