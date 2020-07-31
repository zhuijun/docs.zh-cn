---
title: 如何检索单个特性 (LINQ to XML) (C#)
description: 了解在给定属性名称的情况下，如何使用 LINQ to XML 检索 C# 中元素的单个属性。
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4efcae5324ad5a2e4664e68e35e15ec2053daece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103432"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="3b9b5-103">如何检索单个特性 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3b9b5-103">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="3b9b5-104">本主题说明在给定属性名称的情况下，如何检索元素的单个属性。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-104">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="3b9b5-105">这对于编写查询表达式查找具有特定属性的元素十分有用。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="3b9b5-106"><xref:System.Xml.Linq.XElement.Attribute%2A> 类的 <xref:System.Xml.Linq.XElement> 方法返回具有指定名称的 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b9b5-107">示例</span><span class="sxs-lookup"><span data-stu-id="3b9b5-107">Example</span></span>  
 <span data-ttu-id="3b9b5-108">下面的示例使用 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-108">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="3b9b5-109">本示例首先在名为 `Phone` 的树中查找所有后代，然后查找名为 `type` 的属性。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-109">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="3b9b5-110">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="3b9b5-110">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="3b9b5-111">示例</span><span class="sxs-lookup"><span data-stu-id="3b9b5-111">Example</span></span>  
 <span data-ttu-id="3b9b5-112">如果希望检索属性的值，可以强制转换该值，就像使用 <xref:System.Xml.Linq.XElement> 对象时一样。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-112">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="3b9b5-113">下面的示例演示这一操作。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-113">The following example demonstrates this.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="3b9b5-114">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="3b9b5-114">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="3b9b5-115">为 <xref:System.Xml.Linq.XAttribute> 类提供了以下类型的显式强制转换运算符：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-115">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b9b5-116">示例</span><span class="sxs-lookup"><span data-stu-id="3b9b5-116">Example</span></span>  
 <span data-ttu-id="3b9b5-117">下面的示例显式命名空间中的属性的相同代码。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-117">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="3b9b5-118">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="3b9b5-118">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 <span data-ttu-id="3b9b5-119">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="3b9b5-119">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b9b5-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="3b9b5-120">See also</span></span>

- [<span data-ttu-id="3b9b5-121">LINQ to XML 轴 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b9b5-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
