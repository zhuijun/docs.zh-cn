---
title: <sharedListeners> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153316"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="6b252-102">\<sharedListeners> 元素</span><span class="sxs-lookup"><span data-stu-id="6b252-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="6b252-103">包含任何源或跟踪元素可以引用的侦听器。</span><span class="sxs-lookup"><span data-stu-id="6b252-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="6b252-104">默认情况下，这些侦听器不会接收任何跟踪，而且不能在运行时检索这些侦听器。</span><span class="sxs-lookup"><span data-stu-id="6b252-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="6b252-105">可以按名称将标识为共享侦听器的侦听器添加到源或跟踪。</span><span class="sxs-lookup"><span data-stu-id="6b252-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a><span data-ttu-id="6b252-106">语法</span><span class="sxs-lookup"><span data-stu-id="6b252-106">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b252-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6b252-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6b252-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6b252-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b252-109">特性</span><span class="sxs-lookup"><span data-stu-id="6b252-109">Attributes</span></span>  
 <span data-ttu-id="6b252-110">无。</span><span class="sxs-lookup"><span data-stu-id="6b252-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b252-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6b252-111">Child Elements</span></span>  
  
|<span data-ttu-id="6b252-112">元素</span><span class="sxs-lookup"><span data-stu-id="6b252-112">Element</span></span>|<span data-ttu-id="6b252-113">说明</span><span class="sxs-lookup"><span data-stu-id="6b252-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="6b252-114">将侦听器添加到 `sharedListeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="6b252-114">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b252-115">父元素</span><span class="sxs-lookup"><span data-stu-id="6b252-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6b252-116">元素</span><span class="sxs-lookup"><span data-stu-id="6b252-116">Element</span></span>|<span data-ttu-id="6b252-117">说明</span><span class="sxs-lookup"><span data-stu-id="6b252-117">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="6b252-118">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="6b252-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6b252-119">为 ASP.NET 配置节指定根元素。</span><span class="sxs-lookup"><span data-stu-id="6b252-119">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b252-120">注解</span><span class="sxs-lookup"><span data-stu-id="6b252-120">Remarks</span></span>  
 <span data-ttu-id="6b252-121">将侦听器添加到共享侦听器集合并不会使其成为活动侦听器。</span><span class="sxs-lookup"><span data-stu-id="6b252-121">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="6b252-122">还必须将其添加到跟踪源或跟踪，方法是将其添加到跟踪 `Listeners` 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="6b252-122">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="6b252-123">.NET Framework 中的侦听器类派生自 <xref:System.Diagnostics.TraceListener> 类。</span><span class="sxs-lookup"><span data-stu-id="6b252-123">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="6b252-124">此元素可在计算机配置文件（Machine.config）和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="6b252-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b252-125">示例</span><span class="sxs-lookup"><span data-stu-id="6b252-125">Example</span></span>  
 <span data-ttu-id="6b252-126">下面的示例演示如何使用 `<sharedListeners>` 元素将侦听器添加 `console` 到 `Listeners` <xref:System.Diagnostics.TraceSource> 和类的集合 <xref:System.Diagnostics.Trace> 。</span><span class="sxs-lookup"><span data-stu-id="6b252-126">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="6b252-127">控制台跟踪侦听器通过对或的调用将跟踪信息写入控制台 <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> 。</span><span class="sxs-lookup"><span data-stu-id="6b252-127">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="6b252-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b252-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="6b252-129">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="6b252-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6b252-130">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="6b252-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
