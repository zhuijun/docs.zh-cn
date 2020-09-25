---
title: <filter>的元素 <add><sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: e140148a342e31d6ade7def8849d8a7738301704
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173921"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="234bf-102">\<filter>的元素 \<add>\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="234bf-102">\<filter> Element for \<add> for \<sharedListeners></span></span>

<span data-ttu-id="234bf-103">将筛选器添加到 `sharedListeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="234bf-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="234bf-104">语法</span><span class="sxs-lookup"><span data-stu-id="234bf-104">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="234bf-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="234bf-105">Attributes and Elements</span></span>  

 <span data-ttu-id="234bf-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="234bf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="234bf-107">特性</span><span class="sxs-lookup"><span data-stu-id="234bf-107">Attributes</span></span>  
  
|<span data-ttu-id="234bf-108">属性</span><span class="sxs-lookup"><span data-stu-id="234bf-108">Attribute</span></span>|<span data-ttu-id="234bf-109">说明</span><span class="sxs-lookup"><span data-stu-id="234bf-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="234bf-110">type</span><span class="sxs-lookup"><span data-stu-id="234bf-110">**type**</span></span>|<span data-ttu-id="234bf-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="234bf-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="234bf-112">指定筛选器的类型。</span><span class="sxs-lookup"><span data-stu-id="234bf-112">Specifies the type of the filter.</span></span> <span data-ttu-id="234bf-113">只能使用) 属性格式 (类型的全名 <xref:System.Type.FullName%2A?displayProperty=nameWithType> ，也可以使用完全限定的类型名称，包括 (格式的程序集信息， <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>) 属性。</span><span class="sxs-lookup"><span data-stu-id="234bf-113">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="234bf-114">有关创建完全限定类型名称的信息，请参阅 [指定完全限定的类型](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)名称。</span><span class="sxs-lookup"><span data-stu-id="234bf-114">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="234bf-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="234bf-115">**initializeData**</span></span>|<span data-ttu-id="234bf-116">可选特性。</span><span class="sxs-lookup"><span data-stu-id="234bf-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="234bf-117">传递到指定类的构造函数的字符串。</span><span class="sxs-lookup"><span data-stu-id="234bf-117">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="234bf-118">子元素</span><span class="sxs-lookup"><span data-stu-id="234bf-118">Child Elements</span></span>  

 <span data-ttu-id="234bf-119">无。</span><span class="sxs-lookup"><span data-stu-id="234bf-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="234bf-120">父元素</span><span class="sxs-lookup"><span data-stu-id="234bf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="234bf-121">元素</span><span class="sxs-lookup"><span data-stu-id="234bf-121">Element</span></span>|<span data-ttu-id="234bf-122">描述</span><span class="sxs-lookup"><span data-stu-id="234bf-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="234bf-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="234bf-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="234bf-124">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="234bf-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="234bf-125">任何源或跟踪元素都可以引用的侦听器的集合。</span><span class="sxs-lookup"><span data-stu-id="234bf-125">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="234bf-126">将侦听器添加到 **sharedListeners** 集合。</span><span class="sxs-lookup"><span data-stu-id="234bf-126">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="234bf-127">备注</span><span class="sxs-lookup"><span data-stu-id="234bf-127">Remarks</span></span>  

 <span data-ttu-id="234bf-128">如果侦听器是在 `<add>` 元素的元素中定义的 `<sharedListeners>` ，则应在作为元素的子元素的元素中定义该侦听器的筛选器 `<filter>` `<add>` 。</span><span class="sxs-lookup"><span data-stu-id="234bf-128">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="234bf-129">此元素可在计算机配置文件中使用 ( # A0) 和应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="234bf-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="234bf-130">示例</span><span class="sxs-lookup"><span data-stu-id="234bf-130">Example</span></span>  

 <span data-ttu-id="234bf-131">下面的示例演示如何使用 `<filter>` 元素将筛选器添加到集合中的跟踪侦听器 `console` `sharedListeners` 。</span><span class="sxs-lookup"><span data-stu-id="234bf-131">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="234bf-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="234bf-132">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="234bf-133">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="234bf-133">Trace and Debug Settings Schema</span></span>](index.md)
