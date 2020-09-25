---
title: <switches> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: bdd6efdec1e118075495002509c7367c1162baba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176092"
---
# <a name="switches-element"></a><span data-ttu-id="397a8-102">\<switches> 元素</span><span class="sxs-lookup"><span data-stu-id="397a8-102">\<switches> Element</span></span>

<span data-ttu-id="397a8-103">包含跟踪开关和对该跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="397a8-103">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="397a8-104">语法</span><span class="sxs-lookup"><span data-stu-id="397a8-104">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="397a8-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="397a8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="397a8-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="397a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="397a8-107">特性</span><span class="sxs-lookup"><span data-stu-id="397a8-107">Attributes</span></span>  

 <span data-ttu-id="397a8-108">无。</span><span class="sxs-lookup"><span data-stu-id="397a8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="397a8-109">子元素</span><span class="sxs-lookup"><span data-stu-id="397a8-109">Child Elements</span></span>  
  
|<span data-ttu-id="397a8-110">元素</span><span class="sxs-lookup"><span data-stu-id="397a8-110">Element</span></span>|<span data-ttu-id="397a8-111">描述</span><span class="sxs-lookup"><span data-stu-id="397a8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="397a8-112">指定对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="397a8-112">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="397a8-113">父元素</span><span class="sxs-lookup"><span data-stu-id="397a8-113">Parent Elements</span></span>  
  
|<span data-ttu-id="397a8-114">元素</span><span class="sxs-lookup"><span data-stu-id="397a8-114">Element</span></span>|<span data-ttu-id="397a8-115">描述</span><span class="sxs-lookup"><span data-stu-id="397a8-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="397a8-116">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="397a8-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="397a8-117">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="397a8-117">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="397a8-118">备注</span><span class="sxs-lookup"><span data-stu-id="397a8-118">Remarks</span></span>  

 <span data-ttu-id="397a8-119">可以通过将跟踪开关置于配置文件中来更改其级别。</span><span class="sxs-lookup"><span data-stu-id="397a8-119">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="397a8-120">如果开关是 <xref:System.Diagnostics.BooleanSwitch> ，则可以将其打开或关闭。</span><span class="sxs-lookup"><span data-stu-id="397a8-120">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="397a8-121">如果开关是 <xref:System.Diagnostics.TraceSwitch> ，则可以为其分配不同的级别，以指定应用程序输出的跟踪或调试消息的类型。</span><span class="sxs-lookup"><span data-stu-id="397a8-121">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="397a8-122">示例</span><span class="sxs-lookup"><span data-stu-id="397a8-122">Example</span></span>  

 <span data-ttu-id="397a8-123">下面的示例演示如何使用 **\<switch>** 元素将 `General` 跟踪开关设置为 <xref:System.Diagnostics.TraceLevel> 级别，并启用 `Data` 布尔型跟踪开关。</span><span class="sxs-lookup"><span data-stu-id="397a8-123">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="397a8-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="397a8-124">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="397a8-125">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="397a8-125">Trace and Debug Settings Schema</span></span>](index.md)
