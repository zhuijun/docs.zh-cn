---
title: XML 类型支持实现说明
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 91a685f122ff846217ea7a8677b29df430b65363
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290274"
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="0249d-102">XML 类型支持实现说明</span><span class="sxs-lookup"><span data-stu-id="0249d-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="0249d-103">本主题介绍一些要注意的实现细节。</span><span class="sxs-lookup"><span data-stu-id="0249d-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="0249d-104">列表映射</span><span class="sxs-lookup"><span data-stu-id="0249d-104">List Mappings</span></span>  
 <span data-ttu-id="0249d-105"><xref:System.Collections.IList>、<xref:System.Collections.ICollection>、<xref:System.Collections.IEnumerable>、Type[]  和 <xref:System.String> 类型用于表示 XML 架构定义语言 (XSD) 列表类型。</span><span class="sxs-lookup"><span data-stu-id="0249d-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="0249d-106">联合映射</span><span class="sxs-lookup"><span data-stu-id="0249d-106">Union Mappings</span></span>  
 <span data-ttu-id="0249d-107">联合类型使用 <xref:System.Xml.Schema.XmlAtomicValue> 或 <xref:System.String> 类型表示。</span><span class="sxs-lookup"><span data-stu-id="0249d-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="0249d-108">因此，源类型或目标类型必须始终为 <xref:System.String> 或 <xref:System.Xml.Schema.XmlAtomicValue>。</span><span class="sxs-lookup"><span data-stu-id="0249d-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="0249d-109">如果 <xref:System.Xml.Schema.XmlSchemaDatatype> 对象表示列表类型，该对象会将输入字符串值转换为一个或多个对象的列表。</span><span class="sxs-lookup"><span data-stu-id="0249d-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="0249d-110">如果 <xref:System.Xml.Schema.XmlSchemaDatatype> 表示联合类型，则尝试将输入值作为联合的成员类型进行分析。</span><span class="sxs-lookup"><span data-stu-id="0249d-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="0249d-111">如果尝试分析失败，将尝试使用联合的下一个成员进行转换，依此类推，直到转换成功，或没有其他成员类型可以尝试，在这种情况下将引发异常。</span><span class="sxs-lookup"><span data-stu-id="0249d-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="0249d-112">CLR 和 XML 数据类型之间的区别</span><span class="sxs-lookup"><span data-stu-id="0249d-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="0249d-113">下文介绍 CLR 类型和 XML 数据类型之间可能发生的某些不匹配情况以及如何处理这些情况。</span><span class="sxs-lookup"><span data-stu-id="0249d-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0249d-114">`xs` 前缀映射到 <https://www.w3.org/2001/XMLSchema> 和命名空间 URL。</span><span class="sxs-lookup"><span data-stu-id="0249d-114">The `xs` prefix is mapped to the <https://www.w3.org/2001/XMLSchema> and namespace URI.</span></span>
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="0249d-115">System.TimeSpan 和 xs:duration</span><span class="sxs-lookup"><span data-stu-id="0249d-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="0249d-116">`xs:duration` 类型进行部分排序，因为存在某些不同但是等效的持续时间值。</span><span class="sxs-lookup"><span data-stu-id="0249d-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="0249d-117">这意味着对于 `xs:duration` 类型，1 个月 (P1M) 之类的值少于 32 天 (P32D)，多于 27 天 (P27D)，等效于 28、29 或 30 天。</span><span class="sxs-lookup"><span data-stu-id="0249d-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="0249d-118"><xref:System.TimeSpan> 类不支持此部分排序。</span><span class="sxs-lookup"><span data-stu-id="0249d-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="0249d-119">而是为 1 年和 1 个月选取特定的天数；分别为 365 天和 30 天。</span><span class="sxs-lookup"><span data-stu-id="0249d-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="0249d-120">有关 `xs:duration` 类型的详细信息，请参见 W3C [XML 架构第 2 部分：数据类型建议](https://www.w3.org/TR/xmlschema-2/)。</span><span class="sxs-lookup"><span data-stu-id="0249d-120">For more information on the `xs:duration` type, see the W3C [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="0249d-121">xs:time、公历数据类型和 System.DateTime</span><span class="sxs-lookup"><span data-stu-id="0249d-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="0249d-122">`xs:time` 值映射到 <xref:System.DateTime> 对象时，<xref:System.DateTime.MinValue> 字段用于将 <xref:System.DateTime> 对象的日期属性（例如 <xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A> 和 <xref:System.DateTime.Day%2A>）初始化为 <xref:System.DateTime> 可能的最小值。</span><span class="sxs-lookup"><span data-stu-id="0249d-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="0249d-123">同样，`xs:gMonth`、`xs:gDay`、`xs:gYear`、`xs:gYearMonth` 和 `xs:gMonthDay` 的实例也映射到 <xref:System.DateTime> 对象。</span><span class="sxs-lookup"><span data-stu-id="0249d-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="0249d-124"><xref:System.DateTime> 对象上未使用的属性初始化为 <xref:System.DateTime.MinValue> 中的值。</span><span class="sxs-lookup"><span data-stu-id="0249d-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0249d-125">如果内容类型化为 <xref:System.DateTime.Year%2A?displayProperty=nameWithType>，则不能使用 `xs:gMonthDay` 值。</span><span class="sxs-lookup"><span data-stu-id="0249d-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="0249d-126">在这种情况下，<xref:System.DateTime.Year%2A?displayProperty=nameWithType> 值始终设置为 1904。</span><span class="sxs-lookup"><span data-stu-id="0249d-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="0249d-127">xs:anyURI 和 System.Uri</span><span class="sxs-lookup"><span data-stu-id="0249d-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="0249d-128">表示相对 URI 的 `xs:anyURI` 的实例映射到 <xref:System.Uri> 时，<xref:System.Uri> 对象没有基 URI。</span><span class="sxs-lookup"><span data-stu-id="0249d-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0249d-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="0249d-129">See also</span></span>

- [<span data-ttu-id="0249d-130">System.Xml 类中的类型支持</span><span class="sxs-lookup"><span data-stu-id="0249d-130">Type Support in the System.Xml Classes</span></span>](type-support-in-the-system-xml-classes.md)
