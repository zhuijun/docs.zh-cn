---
title: dateTimeInvalidLocalFormat MDA
description: 查看 dateTimeInvalidLocalFormat 托管调试助手（MDA），当 UTC 存储的日期时间值获取仅本地日期时间格式时，将激活该助手。
ms.date: 03/30/2017
helpviewer_keywords:
- dates [.NET Framework], formatting
- invalid date time local format
- invalid local formats
- MDAs (managed debugging assistants), invalid local formats
- managed debugging assistants (MDAs), invalid local formats
- dateTimeInvalidLocalFormat MDA
- date formatting
- time formatting
- UTC formatting
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
ms.openlocfilehash: d092b93af55d2cdf14e9284d8cffcdc8440cbf81
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415987"
---
# <a name="datetimeinvalidlocalformat-mda"></a><span data-ttu-id="34949-103">dateTimeInvalidLocalFormat MDA</span><span class="sxs-lookup"><span data-stu-id="34949-103">dateTimeInvalidLocalFormat MDA</span></span>
<span data-ttu-id="34949-104">使用只打算用于本地 <xref:System.DateTime> 实例的格式对存储为协调世界时 (UTC) 的 <xref:System.DateTime> 实例设置格式时，将激活 `dateTimeInvalidLocalFormat` MDA。</span><span class="sxs-lookup"><span data-stu-id="34949-104">The `dateTimeInvalidLocalFormat` MDA is activated when a <xref:System.DateTime> instance that is stored as a Universal Coordinated Time (UTC) is formatted using a format that is intended to be used only for local <xref:System.DateTime> instances.</span></span> <span data-ttu-id="34949-105">对于未指定的或默认的 <xref:System.DateTime> 实例，不激活此 MDA。</span><span class="sxs-lookup"><span data-stu-id="34949-105">This MDA is not activated for unspecified or default <xref:System.DateTime> instances.</span></span>  
  
## <a name="symptom"></a><span data-ttu-id="34949-106">症状</span><span class="sxs-lookup"><span data-stu-id="34949-106">Symptom</span></span>  
 <span data-ttu-id="34949-107">应用程序使用本地格式手动序列化 UTC <xref:System.DateTime> 实例：</span><span class="sxs-lookup"><span data-stu-id="34949-107">An application is manually serializing a UTC <xref:System.DateTime> instance using a local format:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### <a name="cause"></a><span data-ttu-id="34949-108">原因</span><span class="sxs-lookup"><span data-stu-id="34949-108">Cause</span></span>  
 <span data-ttu-id="34949-109"><xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 方法的“z”格式包括本地时区偏移量，例如，“+10:00”表示悉尼时间。</span><span class="sxs-lookup"><span data-stu-id="34949-109">The 'z' format for the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> method includes the local time zone offset, for example, "+10:00" for Sydney time.</span></span> <span data-ttu-id="34949-110">就这一点而言，只有 <xref:System.DateTime> 值是本地时间时，它才会得出有意义的结果。</span><span class="sxs-lookup"><span data-stu-id="34949-110">As such, it will only produce a meaningful result if the value of the <xref:System.DateTime> is local.</span></span> <span data-ttu-id="34949-111">如果该值是 UTC 时间，则 <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> 包括本地时区偏移量，但是不显示或调整时区说明符。</span><span class="sxs-lookup"><span data-stu-id="34949-111">If the value is UTC time, <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> includes the local time zone offset, but it does not display or adjust the time zone specifier.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="34949-112">解决方法</span><span class="sxs-lookup"><span data-stu-id="34949-112">Resolution</span></span>  
 <span data-ttu-id="34949-113">应采用可表明 UTC <xref:System.DateTime> 实例为 UTC 时间的方式设置这些实例的格式。</span><span class="sxs-lookup"><span data-stu-id="34949-113">UTC <xref:System.DateTime> instances should be formatted in a way that indicates that they are UTC.</span></span> <span data-ttu-id="34949-114">对于 UTC 时间的格式，建议使用一个“Z”表示 UTC 时间：</span><span class="sxs-lookup"><span data-stu-id="34949-114">The recommended format for UTC times to use a 'Z' to denote UTC time:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 <span data-ttu-id="34949-115">还有一种利用正确序列化的 <xref:System.DateTime.Kind%2A> 属性序列化 <xref:System.DateTime> 的“o”格式，而不管实例是本地时间、UTC 时间还是未指定的时间：</span><span class="sxs-lookup"><span data-stu-id="34949-115">There is also an "o" format that serializes a <xref:System.DateTime> making use of the <xref:System.DateTime.Kind%2A> property that serializes correctly regardless of whether the instance is local, UTC, or unspecified:</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="34949-116">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="34949-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="34949-117">此 MDA 不影响运行时。</span><span class="sxs-lookup"><span data-stu-id="34949-117">This MDA does not affect the runtime.</span></span>  
  
## <a name="output"></a><span data-ttu-id="34949-118">输出</span><span class="sxs-lookup"><span data-stu-id="34949-118">Output</span></span>  
 <span data-ttu-id="34949-119">不存在作为此 MDA 激活的结果的特殊输出。但是，可使用调用堆栈确定激活此 MDA 的 <xref:System.DateTime.ToString%2A> 调用的位置。</span><span class="sxs-lookup"><span data-stu-id="34949-119">There is no special output as a result of this MDA activating., However, the call stack can be used to determine the location of the <xref:System.DateTime.ToString%2A> call that activated the MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="34949-120">配置</span><span class="sxs-lookup"><span data-stu-id="34949-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="34949-121">示例</span><span class="sxs-lookup"><span data-stu-id="34949-121">Example</span></span>  
 <span data-ttu-id="34949-122">假设应用程序按以下方式使用 <xref:System.Xml.XmlConvert> 或 <xref:System.Data.DataSet> 类间接序列化 UTC <xref:System.DateTime> 值。</span><span class="sxs-lookup"><span data-stu-id="34949-122">Consider an application that is indirectly serializing a UTC <xref:System.DateTime> value by using the <xref:System.Xml.XmlConvert> or <xref:System.Data.DataSet> class, in the following manner.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 <span data-ttu-id="34949-123"><xref:System.Xml.XmlConvert> 和 <xref:System.Data.DataSet> 序列化默认使用本地格式进行序列化。</span><span class="sxs-lookup"><span data-stu-id="34949-123">The <xref:System.Xml.XmlConvert> and <xref:System.Data.DataSet> serializations use local formats for serialization by default.</span></span> <span data-ttu-id="34949-124">序列化其他种类的 <xref:System.DateTime> 值（例如 UTC）需要其他选项。</span><span class="sxs-lookup"><span data-stu-id="34949-124">Additional options are required to serialize other kinds of <xref:System.DateTime> values, such as UTC.</span></span>  
  
 <span data-ttu-id="34949-125">对于此特定示例，将 `XmlDateTimeSerializationMode.RoundtripKind` 传递给 `XmlConvert` 上的 `ToString` 调用。</span><span class="sxs-lookup"><span data-stu-id="34949-125">For this specific example, pass in `XmlDateTimeSerializationMode.RoundtripKind` to the `ToString` call on `XmlConvert`.</span></span> <span data-ttu-id="34949-126">这会将数据序列化为 UTC 时间。</span><span class="sxs-lookup"><span data-stu-id="34949-126">This serializes the data as a UTC time.</span></span>  
  
 <span data-ttu-id="34949-127">如果使用 <xref:System.Data.DataSet>，则将 <xref:System.Data.DataColumn> 对象上的 <xref:System.Data.DataColumn.DateTimeMode%2A> 属性设置为 <xref:System.Data.DataSetDateTime.Utc>。</span><span class="sxs-lookup"><span data-stu-id="34949-127">If using a <xref:System.Data.DataSet>, set the <xref:System.Data.DataColumn.DateTimeMode%2A> property on the <xref:System.Data.DataColumn> object to <xref:System.Data.DataSetDateTime.Utc>.</span></span>  
  
```csharp
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## <a name="see-also"></a><span data-ttu-id="34949-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="34949-128">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="34949-129">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="34949-129">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
