---
title: <add>的元素 <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: a5abaffbad986785b8879297883da9614f0a8103
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201689"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="94313-102">\<add>的元素 \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="94313-102">\<add> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="94313-103">将侦听器添加到跟踪源的 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="94313-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="94313-104">语法</span><span class="sxs-lookup"><span data-stu-id="94313-104">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94313-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="94313-105">Attributes and Elements</span></span>  

 <span data-ttu-id="94313-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="94313-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94313-107">特性</span><span class="sxs-lookup"><span data-stu-id="94313-107">Attributes</span></span>  
  
|<span data-ttu-id="94313-108">属性</span><span class="sxs-lookup"><span data-stu-id="94313-108">Attribute</span></span>|<span data-ttu-id="94313-109">描述</span><span class="sxs-lookup"><span data-stu-id="94313-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="94313-110">必需的属性，除非引用集合中的侦听器 `sharedListeners` ，在这种情况下，你只需按名称引用它 (请参阅 [示例](#example)) 。</span><span class="sxs-lookup"><span data-stu-id="94313-110">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="94313-111">指定侦听器的类型。</span><span class="sxs-lookup"><span data-stu-id="94313-111">Specifies the type of the listener.</span></span> <span data-ttu-id="94313-112">必须使用满足指定 [完全限定的类型名称](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)中指定的要求的字符串。</span><span class="sxs-lookup"><span data-stu-id="94313-112">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="94313-113">可选特性。</span><span class="sxs-lookup"><span data-stu-id="94313-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="94313-114">传递到指定类的构造函数的字符串。</span><span class="sxs-lookup"><span data-stu-id="94313-114">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="94313-115"><xref:System.Configuration.ConfigurationException>如果类不具有采用字符串的构造函数，则会引发。</span><span class="sxs-lookup"><span data-stu-id="94313-115">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="94313-116">可选特性。</span><span class="sxs-lookup"><span data-stu-id="94313-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="94313-117">指定侦听器的名称。</span><span class="sxs-lookup"><span data-stu-id="94313-117">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="94313-118">可选特性。</span><span class="sxs-lookup"><span data-stu-id="94313-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="94313-119">指定 <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> 跟踪侦听器的属性值。</span><span class="sxs-lookup"><span data-stu-id="94313-119">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="94313-120">[自定义属性]</span><span class="sxs-lookup"><span data-stu-id="94313-120">[custom attributes]</span></span>|<span data-ttu-id="94313-121">可选属性。</span><span class="sxs-lookup"><span data-stu-id="94313-121">Optional attributes.</span></span><br /><br /> <span data-ttu-id="94313-122">为该侦听器的方法所标识的侦听器特定的特性指定值 <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> 。</span><span class="sxs-lookup"><span data-stu-id="94313-122">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="94313-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 是类独有的额外特性的一个示例 <xref:System.Diagnostics.DelimitedListTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="94313-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94313-124">子元素</span><span class="sxs-lookup"><span data-stu-id="94313-124">Child Elements</span></span>  
  
|<span data-ttu-id="94313-125">元素</span><span class="sxs-lookup"><span data-stu-id="94313-125">Element</span></span>|<span data-ttu-id="94313-126">描述</span><span class="sxs-lookup"><span data-stu-id="94313-126">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="94313-127">将筛选器添加到跟踪源的 `Listeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="94313-127">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94313-128">父元素</span><span class="sxs-lookup"><span data-stu-id="94313-128">Parent Elements</span></span>  
  
|<span data-ttu-id="94313-129">元素</span><span class="sxs-lookup"><span data-stu-id="94313-129">Element</span></span>|<span data-ttu-id="94313-130">描述</span><span class="sxs-lookup"><span data-stu-id="94313-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="94313-131">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="94313-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="94313-132">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="94313-132">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="94313-133">包含用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="94313-133">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="94313-134">指定用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="94313-134">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="94313-135">指定用于收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="94313-135">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94313-136">备注</span><span class="sxs-lookup"><span data-stu-id="94313-136">Remarks</span></span>  

 <span data-ttu-id="94313-137">随 .NET Framework 附带的侦听器类派生自 <xref:System.Diagnostics.TraceListener> 类。</span><span class="sxs-lookup"><span data-stu-id="94313-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="94313-138">如果未指定 `name` 跟踪侦听器的属性，则 <xref:System.Diagnostics.TraceListener.Name%2A> 跟踪侦听器的属性默认为空字符串 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="94313-138">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="94313-139">如果你的应用程序只有一个侦听器，则可以在不指定名称的情况下添加它，并且可以通过为名称指定空字符串来删除它。</span><span class="sxs-lookup"><span data-stu-id="94313-139">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="94313-140">但是，如果你的应用程序有多个侦听器，则应为每个跟踪侦听器指定唯一的名称，以便你可以在集合中标识和管理单个跟踪侦听器 <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="94313-140">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94313-141">添加具有相同类型且具有相同名称的多个跟踪侦听器会导致只将该类型和名称的一个跟踪侦听器添加到 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="94313-141">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="94313-142">但是，可以通过编程方式将多个相同的侦听器添加到 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="94313-142">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="94313-143">该属性的值 `initializeData` 取决于所创建的侦听器的类型。</span><span class="sxs-lookup"><span data-stu-id="94313-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="94313-144">并非所有跟踪侦听器都要求您指定 `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="94313-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94313-145">使用 `initializeData` 属性时，可能会收到编译器警告 "未声明 ' initializeData ' 特性"。</span><span class="sxs-lookup"><span data-stu-id="94313-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="94313-146">之所以出现此警告，是因为配置设置是针对抽象基类验证的 <xref:System.Diagnostics.TraceListener> ，后者不识别 `initializeData` 属性。</span><span class="sxs-lookup"><span data-stu-id="94313-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="94313-147">通常，对于具有采用参数的构造函数的跟踪侦听器实现，你可以忽略此警告。</span><span class="sxs-lookup"><span data-stu-id="94313-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="94313-148">下表显示了 .NET Framework 附带的跟踪侦听器，并描述了其属性的值 `initializeData` 。</span><span class="sxs-lookup"><span data-stu-id="94313-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="94313-149">跟踪侦听器类</span><span class="sxs-lookup"><span data-stu-id="94313-149">Trace listener class</span></span>|<span data-ttu-id="94313-150">initializeData 特性值</span><span class="sxs-lookup"><span data-stu-id="94313-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="94313-151">`useErrorStream`构造函数的值 <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="94313-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="94313-152">将 `initializeData` 属性设置为 " `true` " 可将跟踪和调试输出写入标准错误流; 将该属性设置为 " `false` " 可写入标准输出流。</span><span class="sxs-lookup"><span data-stu-id="94313-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="94313-153"><xref:System.Diagnostics.DelimitedListTraceListener> 写入的文件名。</span><span class="sxs-lookup"><span data-stu-id="94313-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="94313-154">现有的事件日志源的名称。</span><span class="sxs-lookup"><span data-stu-id="94313-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="94313-155">写入的文件的名称 <xref:System.Diagnostics.EventSchemaTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="94313-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="94313-156">写入的文件的名称 <xref:System.Diagnostics.TextWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="94313-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="94313-157">写入的文件的名称 <xref:System.Diagnostics.XmlWriterTraceListener> 。</span><span class="sxs-lookup"><span data-stu-id="94313-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="94313-158">配置文件</span><span class="sxs-lookup"><span data-stu-id="94313-158">Configuration File</span></span>  

 <span data-ttu-id="94313-159">此元素可在计算机配置文件中使用 ( # A0) 和应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="94313-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94313-160">示例</span><span class="sxs-lookup"><span data-stu-id="94313-160">Example</span></span>  

 <span data-ttu-id="94313-161">下面的示例演示如何使用 `<add>` 元素将侦听器 `console` 和 `textListener` 集合添加到 `Listeners` 跟踪源的集合中 `TraceSourceApp` 。</span><span class="sxs-lookup"><span data-stu-id="94313-161">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="94313-162">`textListener`侦听器将跟踪输出写入文件 myListener。</span><span class="sxs-lookup"><span data-stu-id="94313-162">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94313-163">请参阅</span><span class="sxs-lookup"><span data-stu-id="94313-163">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="94313-164">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="94313-164">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="94313-165">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="94313-165">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
