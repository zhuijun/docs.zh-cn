---
title: <switches> 的 <add> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088961"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="27f5e-102">\<switches> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="27f5e-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="27f5e-103">指定对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="27f5e-103">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="27f5e-104">语法</span><span class="sxs-lookup"><span data-stu-id="27f5e-104">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27f5e-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="27f5e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="27f5e-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="27f5e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27f5e-107">特性</span><span class="sxs-lookup"><span data-stu-id="27f5e-107">Attributes</span></span>  
  
|<span data-ttu-id="27f5e-108">属性</span><span class="sxs-lookup"><span data-stu-id="27f5e-108">Attribute</span></span>|<span data-ttu-id="27f5e-109">说明</span><span class="sxs-lookup"><span data-stu-id="27f5e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27f5e-110">**name**</span><span class="sxs-lookup"><span data-stu-id="27f5e-110">**name**</span></span>|<span data-ttu-id="27f5e-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="27f5e-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="27f5e-112">指定开关的名称。</span><span class="sxs-lookup"><span data-stu-id="27f5e-112">Specifies the name of the switch.</span></span> <span data-ttu-id="27f5e-113">此属性的值对应于传递给 switch 构造函数的*displayName*参数。</span><span class="sxs-lookup"><span data-stu-id="27f5e-113">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="27f5e-114">**value**</span><span class="sxs-lookup"><span data-stu-id="27f5e-114">**value**</span></span>|<span data-ttu-id="27f5e-115">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="27f5e-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="27f5e-116">指定开关的级别。</span><span class="sxs-lookup"><span data-stu-id="27f5e-116">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27f5e-117">子元素</span><span class="sxs-lookup"><span data-stu-id="27f5e-117">Child Elements</span></span>  
 <span data-ttu-id="27f5e-118">无。</span><span class="sxs-lookup"><span data-stu-id="27f5e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27f5e-119">父元素</span><span class="sxs-lookup"><span data-stu-id="27f5e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="27f5e-120">元素</span><span class="sxs-lookup"><span data-stu-id="27f5e-120">Element</span></span>|<span data-ttu-id="27f5e-121">描述</span><span class="sxs-lookup"><span data-stu-id="27f5e-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="27f5e-122">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="27f5e-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="27f5e-123">包含跟踪开关和对该跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="27f5e-123">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="27f5e-124">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="27f5e-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27f5e-125">注解</span><span class="sxs-lookup"><span data-stu-id="27f5e-125">Remarks</span></span>  
 <span data-ttu-id="27f5e-126">可以通过将跟踪开关置于配置文件中来更改其级别。</span><span class="sxs-lookup"><span data-stu-id="27f5e-126">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="27f5e-127">如果开关是 <xref:System.Diagnostics.BooleanSwitch> ，则可以将其打开或关闭。</span><span class="sxs-lookup"><span data-stu-id="27f5e-127">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="27f5e-128">如果开关是 <xref:System.Diagnostics.TraceSwitch> ，则可以为其分配不同的级别，以指定应用程序输出的跟踪或调试消息的类型。</span><span class="sxs-lookup"><span data-stu-id="27f5e-128">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27f5e-129">示例</span><span class="sxs-lookup"><span data-stu-id="27f5e-129">Example</span></span>  
 <span data-ttu-id="27f5e-130">下面的示例演示如何使用 **\<add>** 元素将 `General` 跟踪开关设置为 <xref:System.Diagnostics.TraceLevel> 级别，并启用 `Data` 布尔型跟踪开关。</span><span class="sxs-lookup"><span data-stu-id="27f5e-130">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27f5e-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27f5e-131">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="27f5e-132">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="27f5e-132">Trace and Debug Settings Schema</span></span>](index.md)
