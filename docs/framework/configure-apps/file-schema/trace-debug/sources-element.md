---
title: <sources> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: 2a76816ee73f516b3c7544877a77531acaa8e09c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153264"
---
# <a name="sources-element"></a><span data-ttu-id="6ef4d-102">\<sources> 元素</span><span class="sxs-lookup"><span data-stu-id="6ef4d-102">\<sources> Element</span></span>
<span data-ttu-id="6ef4d-103">指定启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-103">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="6ef4d-104">语法</span><span class="sxs-lookup"><span data-stu-id="6ef4d-104">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ef4d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6ef4d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6ef4d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ef4d-107">特性</span><span class="sxs-lookup"><span data-stu-id="6ef4d-107">Attributes</span></span>  
 <span data-ttu-id="6ef4d-108">无。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6ef4d-109">子元素</span><span class="sxs-lookup"><span data-stu-id="6ef4d-109">Child Elements</span></span>  
  
|<span data-ttu-id="6ef4d-110">元素</span><span class="sxs-lookup"><span data-stu-id="6ef4d-110">Element</span></span>|<span data-ttu-id="6ef4d-111">说明</span><span class="sxs-lookup"><span data-stu-id="6ef4d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="6ef4d-112">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-112">Required element.</span></span><br /><br /> <span data-ttu-id="6ef4d-113">指定用于启动跟踪消息的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-113">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ef4d-114">父元素</span><span class="sxs-lookup"><span data-stu-id="6ef4d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6ef4d-115">元素</span><span class="sxs-lookup"><span data-stu-id="6ef4d-115">Element</span></span>|<span data-ttu-id="6ef4d-116">说明</span><span class="sxs-lookup"><span data-stu-id="6ef4d-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ef4d-117">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6ef4d-118">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ef4d-119">注解</span><span class="sxs-lookup"><span data-stu-id="6ef4d-119">Remarks</span></span>  
 <span data-ttu-id="6ef4d-120">此元素可在计算机配置文件（Machine.config）和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-120">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ef4d-121">示例</span><span class="sxs-lookup"><span data-stu-id="6ef4d-121">Example</span></span>  
 <span data-ttu-id="6ef4d-122">下面的示例演示如何使用 `<sources>` 元素添加跟踪源 `mySource` ，并设置名为的源开关的级别 `sourceSwitch` 。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-122">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="6ef4d-123">添加了控制台跟踪侦听器，用于将跟踪信息写入控制台。</span><span class="sxs-lookup"><span data-stu-id="6ef4d-123">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"
                     initializeData="Error" />  
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
  
## <a name="see-also"></a><span data-ttu-id="6ef4d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ef4d-124">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="6ef4d-125">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="6ef4d-125">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
