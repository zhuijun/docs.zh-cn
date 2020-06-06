---
title: <filter>的的 <add> 的元素 <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153461"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="8805d-102">\<filter>的的 \<add> 的元素 \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="8805d-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="8805d-103">将筛选器添加到跟踪的集合中的侦听器 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="8805d-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="8805d-104">语法</span><span class="sxs-lookup"><span data-stu-id="8805d-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8805d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8805d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8805d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8805d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8805d-107">特性</span><span class="sxs-lookup"><span data-stu-id="8805d-107">Attributes</span></span>  
  
|<span data-ttu-id="8805d-108">属性</span><span class="sxs-lookup"><span data-stu-id="8805d-108">Attribute</span></span>|<span data-ttu-id="8805d-109">说明</span><span class="sxs-lookup"><span data-stu-id="8805d-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8805d-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="8805d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="8805d-111">指定筛选器的类型，该类型应继承自 <xref:System.Diagnostics.TraceFilter> 类。</span><span class="sxs-lookup"><span data-stu-id="8805d-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="8805d-112">你可以使用类型的命名空间限定名称，该名称与类型的属性相对应 <xref:System.Type.FullName%2A> ，或者你可以使用包含程序集信息（与属性相对应）的完全限定的类型名称 <xref:System.Type.AssemblyQualifiedName%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8805d-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="8805d-113">有关完全限定类型名称的信息，请参阅[指定完全限定的类型名称](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="8805d-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="8805d-114">可选特性。</span><span class="sxs-lookup"><span data-stu-id="8805d-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="8805d-115">传递给指定筛选器类的构造函数的字符串。</span><span class="sxs-lookup"><span data-stu-id="8805d-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8805d-116">子元素</span><span class="sxs-lookup"><span data-stu-id="8805d-116">Child Elements</span></span>  
 <span data-ttu-id="8805d-117">无。</span><span class="sxs-lookup"><span data-stu-id="8805d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8805d-118">父元素</span><span class="sxs-lookup"><span data-stu-id="8805d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8805d-119">元素</span><span class="sxs-lookup"><span data-stu-id="8805d-119">Element</span></span>|<span data-ttu-id="8805d-120">描述</span><span class="sxs-lookup"><span data-stu-id="8805d-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8805d-121">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="8805d-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8805d-122">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="8805d-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="8805d-123">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="8805d-123">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8805d-124">包含收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="8805d-124">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="8805d-125">侦听器将跟踪输出定向到适当的目标。</span><span class="sxs-lookup"><span data-stu-id="8805d-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="8805d-126">将侦听器添加到 `Listeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="8805d-126">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8805d-127">注解</span><span class="sxs-lookup"><span data-stu-id="8805d-127">Remarks</span></span>  
 <span data-ttu-id="8805d-128">`<filter>`元素必须包含在 `<add>` 跟踪侦听器的元素中，后者指定侦听器的类型，而不只是中定义的侦听器的名称 [\<sharedListeners>](sharedlisteners-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="8805d-128">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="8805d-129">如果侦听器是在中定义的 [\<sharedListeners>](sharedlisteners-element.md) ，则必须在该元素中定义该侦听器的筛选器。</span><span class="sxs-lookup"><span data-stu-id="8805d-129">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="8805d-130">此元素可在计算机配置文件（Machine.config）和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="8805d-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8805d-131">示例</span><span class="sxs-lookup"><span data-stu-id="8805d-131">Example</span></span>  
 <span data-ttu-id="8805d-132">下面的示例演示如何使用 `<filter>` 元素将筛选器添加到跟踪的集合中的侦听器，并将 `console` `Listeners` 筛选器事件级别指定为 `Error` 。</span><span class="sxs-lookup"><span data-stu-id="8805d-132">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8805d-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8805d-133">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="8805d-134">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="8805d-134">Trace and Debug Settings Schema</span></span>](index.md)
