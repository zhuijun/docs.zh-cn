---
title: <clear>的元素 <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153537"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="e5f84-102">\<clear>的元素 \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="e5f84-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="e5f84-103">清除跟踪的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="e5f84-103">Clears the `Listeners` collection for trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="e5f84-104">语法</span><span class="sxs-lookup"><span data-stu-id="e5f84-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5f84-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e5f84-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e5f84-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5f84-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5f84-107">特性</span><span class="sxs-lookup"><span data-stu-id="e5f84-107">Attributes</span></span>  
 <span data-ttu-id="e5f84-108">无。</span><span class="sxs-lookup"><span data-stu-id="e5f84-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5f84-109">子元素</span><span class="sxs-lookup"><span data-stu-id="e5f84-109">Child Elements</span></span>  
 <span data-ttu-id="e5f84-110">无。</span><span class="sxs-lookup"><span data-stu-id="e5f84-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5f84-111">父元素</span><span class="sxs-lookup"><span data-stu-id="e5f84-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e5f84-112">元素</span><span class="sxs-lookup"><span data-stu-id="e5f84-112">Element</span></span>|<span data-ttu-id="e5f84-113">说明</span><span class="sxs-lookup"><span data-stu-id="e5f84-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e5f84-114">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="e5f84-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e5f84-115">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="e5f84-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e5f84-116">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="e5f84-116">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e5f84-117">包含收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="e5f84-117">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="e5f84-118">侦听器将跟踪输出定向到适当的目标。</span><span class="sxs-lookup"><span data-stu-id="e5f84-118">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5f84-119">注解</span><span class="sxs-lookup"><span data-stu-id="e5f84-119">Remarks</span></span>  
 <span data-ttu-id="e5f84-120">`<clear>`元素从跟踪的集合中移除所有侦听器 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="e5f84-120">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="e5f84-121">可以在使用元素 `<clear>` 之前使用元素 `<add>` ，以确定集合中没有其他活动的侦听器。</span><span class="sxs-lookup"><span data-stu-id="e5f84-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="e5f84-122">您可以 `Listeners` 通过 <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> 对 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> 属性（）调用方法，以编程方式清除该集合 `System.Diagnostics.Trace.Listeners.Clear()` 。</span><span class="sxs-lookup"><span data-stu-id="e5f84-122">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="e5f84-123">此元素可在计算机配置文件（Machine.config）和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="e5f84-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5f84-124">`<clear>`元素 <xref:System.Diagnostics.DefaultTraceListener> 从集合中移除， `Listeners` 并更改 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 、 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> 、 <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> 方法的行为。</span><span class="sxs-lookup"><span data-stu-id="e5f84-124">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e5f84-125">通常调用 `Assert` 或 `Fail` 方法会导致显示消息框。</span><span class="sxs-lookup"><span data-stu-id="e5f84-125">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="e5f84-126">但是，如果不在集合中，则不会显示消息框 <xref:System.Diagnostics.DefaultTraceListener> `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="e5f84-126">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5f84-127">示例</span><span class="sxs-lookup"><span data-stu-id="e5f84-127">Example</span></span>  
 <span data-ttu-id="e5f84-128">下面的示例演示如何 `<clear>` 在使用 `<add>` 元素将侦听器添加 `console` 到用于 trace 的集合之前使用元素 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="e5f84-128">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e5f84-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5f84-129">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="e5f84-130">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="e5f84-130">Trace and Debug Settings Schema</span></span>](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="e5f84-131">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="e5f84-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
