---
title: <source> 元素
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153290"
---
# <a name="source-element"></a><span data-ttu-id="397ed-102">\<source> 元素</span><span class="sxs-lookup"><span data-stu-id="397ed-102">\<source> Element</span></span>
<span data-ttu-id="397ed-103">指定用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="397ed-103">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="397ed-104">语法</span><span class="sxs-lookup"><span data-stu-id="397ed-104">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="397ed-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="397ed-105">Attributes and Elements</span></span>  
 <span data-ttu-id="397ed-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="397ed-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="397ed-107">特性</span><span class="sxs-lookup"><span data-stu-id="397ed-107">Attributes</span></span>  
  
|<span data-ttu-id="397ed-108">属性</span><span class="sxs-lookup"><span data-stu-id="397ed-108">Attribute</span></span>|<span data-ttu-id="397ed-109">说明</span><span class="sxs-lookup"><span data-stu-id="397ed-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="397ed-110">可选特性。</span><span class="sxs-lookup"><span data-stu-id="397ed-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="397ed-111">指定跟踪源的名称。</span><span class="sxs-lookup"><span data-stu-id="397ed-111">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="397ed-112">可选特性。</span><span class="sxs-lookup"><span data-stu-id="397ed-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="397ed-113">指定应用程序中的跟踪开关实例的名称。</span><span class="sxs-lookup"><span data-stu-id="397ed-113">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="397ed-114">如果未在元素中标识开关 `<switches>` ，则值指定开关的级别。</span><span class="sxs-lookup"><span data-stu-id="397ed-114">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="397ed-115">可选特性。</span><span class="sxs-lookup"><span data-stu-id="397ed-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="397ed-116">指定跟踪开关的类型。</span><span class="sxs-lookup"><span data-stu-id="397ed-116">Specifies the type of the trace switch.</span></span> <span data-ttu-id="397ed-117">如果存在，则该类型必须是有效的类名，并且不能是空字符串。</span><span class="sxs-lookup"><span data-stu-id="397ed-117">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="397ed-118">可选特性。</span><span class="sxs-lookup"><span data-stu-id="397ed-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="397ed-119">指定跟踪源特定属性的值，该属性由 <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> 该跟踪源的方法标识。</span><span class="sxs-lookup"><span data-stu-id="397ed-119">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="397ed-120">子元素</span><span class="sxs-lookup"><span data-stu-id="397ed-120">Child Elements</span></span>  
  
|<span data-ttu-id="397ed-121">元素</span><span class="sxs-lookup"><span data-stu-id="397ed-121">Element</span></span>|<span data-ttu-id="397ed-122">描述</span><span class="sxs-lookup"><span data-stu-id="397ed-122">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="397ed-123">包含收集、存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="397ed-123">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="397ed-124">父元素</span><span class="sxs-lookup"><span data-stu-id="397ed-124">Parent Elements</span></span>  
  
|<span data-ttu-id="397ed-125">元素</span><span class="sxs-lookup"><span data-stu-id="397ed-125">Element</span></span>|<span data-ttu-id="397ed-126">描述</span><span class="sxs-lookup"><span data-stu-id="397ed-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="397ed-127">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="397ed-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="397ed-128">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="397ed-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="397ed-129">包含用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="397ed-129">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="397ed-130">注解</span><span class="sxs-lookup"><span data-stu-id="397ed-130">Remarks</span></span>  
 <span data-ttu-id="397ed-131">此元素可在计算机配置文件（Machine.config）和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="397ed-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="397ed-132">示例</span><span class="sxs-lookup"><span data-stu-id="397ed-132">Example</span></span>  
 <span data-ttu-id="397ed-133">下面的示例演示如何使用 `<source>` 元素添加跟踪源 `mySource` ，并设置名为的源开关的级别 `sourceSwitch` 。</span><span class="sxs-lookup"><span data-stu-id="397ed-133">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="397ed-134">添加了控制台跟踪侦听器，用于将跟踪信息写入控制台。</span><span class="sxs-lookup"><span data-stu-id="397ed-134">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>
  </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="397ed-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="397ed-135">See also</span></span>

- [<span data-ttu-id="397ed-136">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="397ed-136">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="397ed-137">跟踪开关</span><span class="sxs-lookup"><span data-stu-id="397ed-137">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
