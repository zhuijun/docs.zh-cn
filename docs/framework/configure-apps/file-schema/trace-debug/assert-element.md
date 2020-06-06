---
title: <assert> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088947"
---
# <a name="assert-element"></a><span data-ttu-id="94269-102">\<assert> 元素</span><span class="sxs-lookup"><span data-stu-id="94269-102">\<assert> Element</span></span>
<span data-ttu-id="94269-103">指定调用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法时是否显示消息框；另外指定要写入消息的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="94269-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="94269-104">语法</span><span class="sxs-lookup"><span data-stu-id="94269-104">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94269-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="94269-105">Attributes and Elements</span></span>  
 <span data-ttu-id="94269-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="94269-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94269-107">特性</span><span class="sxs-lookup"><span data-stu-id="94269-107">Attributes</span></span>  
  
|<span data-ttu-id="94269-108">属性</span><span class="sxs-lookup"><span data-stu-id="94269-108">Attribute</span></span>|<span data-ttu-id="94269-109">说明</span><span class="sxs-lookup"><span data-stu-id="94269-109">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="94269-110">可选特性。</span><span class="sxs-lookup"><span data-stu-id="94269-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="94269-111">指定在**Debug 断言**方法的计算结果为**false**时是否显示消息框。</span><span class="sxs-lookup"><span data-stu-id="94269-111">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="94269-112">可选特性。</span><span class="sxs-lookup"><span data-stu-id="94269-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="94269-113">指定如果**debug.exe**的计算结果为**false**，则为要将消息写入到的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="94269-113">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="94269-114">assertuienabled 特性</span><span class="sxs-lookup"><span data-stu-id="94269-114">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="94269-115">值</span><span class="sxs-lookup"><span data-stu-id="94269-115">Value</span></span>|<span data-ttu-id="94269-116">说明</span><span class="sxs-lookup"><span data-stu-id="94269-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="94269-117">显示消息框。</span><span class="sxs-lookup"><span data-stu-id="94269-117">Displays the message box.</span></span> <span data-ttu-id="94269-118">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="94269-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="94269-119">不显示消息框。</span><span class="sxs-lookup"><span data-stu-id="94269-119">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94269-120">子元素</span><span class="sxs-lookup"><span data-stu-id="94269-120">Child Elements</span></span>  
 <span data-ttu-id="94269-121">无。</span><span class="sxs-lookup"><span data-stu-id="94269-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94269-122">父元素</span><span class="sxs-lookup"><span data-stu-id="94269-122">Parent Elements</span></span>  
  
|<span data-ttu-id="94269-123">元素</span><span class="sxs-lookup"><span data-stu-id="94269-123">Element</span></span>|<span data-ttu-id="94269-124">描述</span><span class="sxs-lookup"><span data-stu-id="94269-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="94269-125">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="94269-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="94269-126">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="94269-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94269-127">注解</span><span class="sxs-lookup"><span data-stu-id="94269-127">Remarks</span></span>  
 <span data-ttu-id="94269-128">元素中的两个特性 **\<assert>** 都是可选的。</span><span class="sxs-lookup"><span data-stu-id="94269-128">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="94269-129">您可以禁用消息框而不指定要向其中写入消息的文件，也可以指定在使消息框处于启用状态时要将消息写入到的文件。</span><span class="sxs-lookup"><span data-stu-id="94269-129">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94269-130">示例</span><span class="sxs-lookup"><span data-stu-id="94269-130">Example</span></span>  
 <span data-ttu-id="94269-131">下面的示例演示如何在调用**Debug. 断言**并将消息写入到时禁用显示消息框 `c:\log.txt` 。</span><span class="sxs-lookup"><span data-stu-id="94269-131">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94269-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94269-132">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="94269-133">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="94269-133">Trace and Debug Settings Schema</span></span>](index.md)
