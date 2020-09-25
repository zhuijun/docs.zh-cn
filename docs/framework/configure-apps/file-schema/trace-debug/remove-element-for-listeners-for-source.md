---
title: <remove>的元素 <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 53ba773ea1cb31955e59c1f57e1c0cc807227402
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173868"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="2625d-102">\<remove>的元素 \<listeners>\<source></span><span class="sxs-lookup"><span data-stu-id="2625d-102">\<remove> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="2625d-103">从跟踪源的 `Listeners` 集合中删除侦听器。</span><span class="sxs-lookup"><span data-stu-id="2625d-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="2625d-104">语法</span><span class="sxs-lookup"><span data-stu-id="2625d-104">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2625d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2625d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2625d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2625d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2625d-107">特性</span><span class="sxs-lookup"><span data-stu-id="2625d-107">Attributes</span></span>  
  
|<span data-ttu-id="2625d-108">属性</span><span class="sxs-lookup"><span data-stu-id="2625d-108">Attribute</span></span>|<span data-ttu-id="2625d-109">描述</span><span class="sxs-lookup"><span data-stu-id="2625d-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="2625d-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="2625d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="2625d-111">要从集合中删除的侦听器的名称 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="2625d-111">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2625d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2625d-112">Child Elements</span></span>  

 <span data-ttu-id="2625d-113">无。</span><span class="sxs-lookup"><span data-stu-id="2625d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2625d-114">父元素</span><span class="sxs-lookup"><span data-stu-id="2625d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2625d-115">元素</span><span class="sxs-lookup"><span data-stu-id="2625d-115">Element</span></span>|<span data-ttu-id="2625d-116">描述</span><span class="sxs-lookup"><span data-stu-id="2625d-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2625d-117">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="2625d-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2625d-118">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="2625d-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="2625d-119">包含用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="2625d-119">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="2625d-120">指定用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="2625d-120">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="2625d-121">指定用于收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="2625d-121">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2625d-122">备注</span><span class="sxs-lookup"><span data-stu-id="2625d-122">Remarks</span></span>  

 <span data-ttu-id="2625d-123">`<remove>`元素从跟踪源的集合中删除指定的侦听器 `Listeners` 。</span><span class="sxs-lookup"><span data-stu-id="2625d-123">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="2625d-124">您可以 `Listeners` 通过 <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> 对实例的属性调用方法，以编程方式从跟踪源的集合中移除一个元素 <xref:System.Diagnostics.TraceSource.Listeners%2A> <xref:System.Diagnostics.TraceSource> 。</span><span class="sxs-lookup"><span data-stu-id="2625d-124">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="2625d-125">此元素可在计算机配置文件中使用 ( # A0) 和应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="2625d-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2625d-126">示例</span><span class="sxs-lookup"><span data-stu-id="2625d-126">Example</span></span>  

 <span data-ttu-id="2625d-127">下面的示例演示如何 `<remove>` 在使用 `<add>` 元素将侦听器添加 `console` 到 `Listeners` 跟踪源的集合之前使用元素 `TraceSourceApp` 。</span><span class="sxs-lookup"><span data-stu-id="2625d-127">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="2625d-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="2625d-128">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="2625d-129">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="2625d-129">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="2625d-130">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="2625d-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
