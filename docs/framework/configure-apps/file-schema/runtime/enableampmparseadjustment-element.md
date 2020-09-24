---
title: <EnableAmPmParseAdjustment> 元素
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: f935f213e1bca8dac7a5401970bc6183575e2301
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167224"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="9fc53-102">\<EnableAmPmParseAdjustment> 元素</span><span class="sxs-lookup"><span data-stu-id="9fc53-102">\<EnableAmPmParseAdjustment> Element</span></span>

<span data-ttu-id="9fc53-103">确定日期和时间分析方法是否使用经过调整的规则集来分析包含 day、month、hour 和 AM/PM 指示符的日期字符串。</span><span class="sxs-lookup"><span data-stu-id="9fc53-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="9fc53-104">语法</span><span class="sxs-lookup"><span data-stu-id="9fc53-104">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fc53-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9fc53-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9fc53-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9fc53-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fc53-107">特性</span><span class="sxs-lookup"><span data-stu-id="9fc53-107">Attributes</span></span>  
  
|<span data-ttu-id="9fc53-108">属性</span><span class="sxs-lookup"><span data-stu-id="9fc53-108">Attribute</span></span>|<span data-ttu-id="9fc53-109">描述</span><span class="sxs-lookup"><span data-stu-id="9fc53-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9fc53-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="9fc53-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="9fc53-111">指定日期和时间分析方法是否使用经过调整的规则集来分析只包含 day、month、hour 和 AM/PM 指示符的日期字符串。</span><span class="sxs-lookup"><span data-stu-id="9fc53-111">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="9fc53-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="9fc53-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="9fc53-113">值</span><span class="sxs-lookup"><span data-stu-id="9fc53-113">Value</span></span>|<span data-ttu-id="9fc53-114">描述</span><span class="sxs-lookup"><span data-stu-id="9fc53-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9fc53-115">0</span><span class="sxs-lookup"><span data-stu-id="9fc53-115">0</span></span>|<span data-ttu-id="9fc53-116">日期和时间分析方法不使用调整的规则来分析日期字符串，这些字符串只包含日、月、小时和 AM/PM 指示符。</span><span class="sxs-lookup"><span data-stu-id="9fc53-116">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="9fc53-117">1</span><span class="sxs-lookup"><span data-stu-id="9fc53-117">1</span></span>|<span data-ttu-id="9fc53-118">日期和时间分析方法使用经过调整的规则，用于分析日期字符串，这些字符串只包含日、月、小时和 AM/PM 指示符。</span><span class="sxs-lookup"><span data-stu-id="9fc53-118">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fc53-119">子元素</span><span class="sxs-lookup"><span data-stu-id="9fc53-119">Child Elements</span></span>  

 <span data-ttu-id="9fc53-120">无。</span><span class="sxs-lookup"><span data-stu-id="9fc53-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9fc53-121">父元素</span><span class="sxs-lookup"><span data-stu-id="9fc53-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9fc53-122">元素</span><span class="sxs-lookup"><span data-stu-id="9fc53-122">Element</span></span>|<span data-ttu-id="9fc53-123">描述</span><span class="sxs-lookup"><span data-stu-id="9fc53-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9fc53-124">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="9fc53-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9fc53-125">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="9fc53-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fc53-126">备注</span><span class="sxs-lookup"><span data-stu-id="9fc53-126">Remarks</span></span>  

 <span data-ttu-id="9fc53-127">`<EnableAmPmParseAdjustment>`元素控制以下方法如何分析包含数字日和月后跟一个小时和 AM/PM 指示符的日期字符串， (例如 "4/10 6 AM" ) ：</span><span class="sxs-lookup"><span data-stu-id="9fc53-127">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="9fc53-128">其他模式不受影响。</span><span class="sxs-lookup"><span data-stu-id="9fc53-128">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="9fc53-129">`<EnableAmPmParseAdjustment>`元素对 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> 、 <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> 、 <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> 和方法不起作用 <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9fc53-129">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9fc53-130">在 .NET Core 和 .NET Native 中，将默认启用调整后的 AM/PM 分析规则。</span><span class="sxs-lookup"><span data-stu-id="9fc53-130">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="9fc53-131">如果未启用解析调整规则，则会将字符串的第一个数字解释为12小时制的小时，而除 AM/PM 指示符之外的字符串的其余部分将被忽略。</span><span class="sxs-lookup"><span data-stu-id="9fc53-131">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="9fc53-132">解析方法返回的日期和时间由当前日期和从日期字符串提取的日期中的小时组成。</span><span class="sxs-lookup"><span data-stu-id="9fc53-132">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="9fc53-133">如果启用了解析调整规则，则分析方法会将日期和月份解释为属于当前年份，并将时间解释为12小时制的小时。</span><span class="sxs-lookup"><span data-stu-id="9fc53-133">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="9fc53-134">下表说明了 <xref:System.DateTime> 当 <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> 使用方法分析字符串 "4/10 6 AM" （ `<EnableAmPmParseAdjustment>` 元素的 `enabled` 属性设置为 "0" 或 "1"）时，值中的差异。</span><span class="sxs-lookup"><span data-stu-id="9fc53-134">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="9fc53-135">它假定今天的日期为2017年1月5日，并使用指定的区域性的 "G" 格式字符串来显示日期。</span><span class="sxs-lookup"><span data-stu-id="9fc53-135">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="9fc53-136">区域性名称</span><span class="sxs-lookup"><span data-stu-id="9fc53-136">Culture name</span></span>|<span data-ttu-id="9fc53-137">enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="9fc53-137">enabled="0"</span></span>|<span data-ttu-id="9fc53-138">enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="9fc53-138">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="9fc53-139">zh-CN</span><span class="sxs-lookup"><span data-stu-id="9fc53-139">en-US</span></span>|<span data-ttu-id="9fc53-140">上午 1/5/2017 4:00:00</span><span class="sxs-lookup"><span data-stu-id="9fc53-140">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="9fc53-141">上午 4/10/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="9fc53-141">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="9fc53-142">en-GB</span><span class="sxs-lookup"><span data-stu-id="9fc53-142">en-GB</span></span>|<span data-ttu-id="9fc53-143">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="9fc53-143">5/1/2017 6:00:00</span></span>|<span data-ttu-id="9fc53-144">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="9fc53-144">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fc53-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="9fc53-145">See also</span></span>

- [<span data-ttu-id="9fc53-146">\<runtime> 元素</span><span class="sxs-lookup"><span data-stu-id="9fc53-146">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="9fc53-147">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="9fc53-147">\<configuration> Element</span></span>](../configuration-element.md)
