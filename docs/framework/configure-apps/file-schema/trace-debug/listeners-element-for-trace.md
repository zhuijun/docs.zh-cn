---
title: <trace> 的 <listeners> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153368"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="3ab4e-102">\<trace> 的 \<listeners> 元素</span><span class="sxs-lookup"><span data-stu-id="3ab4e-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="3ab4e-103">指定用于收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="3ab4e-104">侦听器将跟踪输出定向到适当的目标。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-104">Listeners direct the tracing output to an appropriate target.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a><span data-ttu-id="3ab4e-105">语法</span><span class="sxs-lookup"><span data-stu-id="3ab4e-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ab4e-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3ab4e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3ab4e-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ab4e-108">特性</span><span class="sxs-lookup"><span data-stu-id="3ab4e-108">Attributes</span></span>  
 <span data-ttu-id="3ab4e-109">无。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ab4e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="3ab4e-110">Child Elements</span></span>  
  
|<span data-ttu-id="3ab4e-111">元素</span><span class="sxs-lookup"><span data-stu-id="3ab4e-111">Element</span></span>|<span data-ttu-id="3ab4e-112">说明</span><span class="sxs-lookup"><span data-stu-id="3ab4e-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="3ab4e-113">将侦听器添加到 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="3ab4e-114">清除跟踪的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="3ab4e-115">从集合中移除侦听器 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-115">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ab4e-116">父元素</span><span class="sxs-lookup"><span data-stu-id="3ab4e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3ab4e-117">元素</span><span class="sxs-lookup"><span data-stu-id="3ab4e-117">Element</span></span>|<span data-ttu-id="3ab4e-118">说明</span><span class="sxs-lookup"><span data-stu-id="3ab4e-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3ab4e-119">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3ab4e-120">为 ASP.NET 配置节指定根元素。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-120">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="3ab4e-121">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ab4e-122">注解</span><span class="sxs-lookup"><span data-stu-id="3ab4e-122">Remarks</span></span>  
 <span data-ttu-id="3ab4e-123"><xref:System.Diagnostics.Debug>和 <xref:System.Diagnostics.Trace> 类共享相同的**侦听器**集合。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-123">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="3ab4e-124">如果将侦听器对象添加到其中一个类的集合中，则其他类将使用同一侦听器。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-124">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="3ab4e-125">随 .NET Framework 附带的侦听器类派生自 <xref:System.Diagnostics.TraceListener> 类。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-125">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3ab4e-126">配置文件</span><span class="sxs-lookup"><span data-stu-id="3ab4e-126">Configuration File</span></span>  
 <span data-ttu-id="3ab4e-127">此元素可在计算机配置文件（Machine.config）和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-127">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ab4e-128">示例</span><span class="sxs-lookup"><span data-stu-id="3ab4e-128">Example</span></span>  
 <span data-ttu-id="3ab4e-129">下面的示例演示如何使用 **\<listeners>** 元素将侦听器 `MyListener` 和添加 `MyEventListener` 到**侦听器**集合。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-129">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="3ab4e-130">`MyListener`创建一个名为的文件 `MyListener.log` ，并将输出写入文件。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-130">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="3ab4e-131">`MyEventListener`在事件日志中创建一个条目。</span><span class="sxs-lookup"><span data-stu-id="3ab4e-131">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ab4e-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ab4e-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3ab4e-133">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="3ab4e-133">Trace and Debug Settings Schema</span></span>](index.md)
