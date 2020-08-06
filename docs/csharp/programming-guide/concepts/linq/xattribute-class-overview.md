---
title: XAttribute 类概述 (C#)
description: 属性是与元素关联的名称/值对。 XAttribute 表示 XML 属性。 了解如何使用 C# 在 LINQ to XML 中使用属性。
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 8a19de601041bbb20241c959e909483b97bcf797
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302225"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="4c39c-105">XAttribute 类概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="4c39c-105">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="4c39c-106">属性是与元素关联的名称/值对。</span><span class="sxs-lookup"><span data-stu-id="4c39c-106">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="4c39c-107"><xref:System.Xml.Linq.XAttribute> 类表示 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="4c39c-107">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="4c39c-108">概述</span><span class="sxs-lookup"><span data-stu-id="4c39c-108">Overview</span></span>  
 <span data-ttu-id="4c39c-109">使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的属性，与使用元素非常相似。</span><span class="sxs-lookup"><span data-stu-id="4c39c-109">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="4c39c-110">它们的构造函数相似。</span><span class="sxs-lookup"><span data-stu-id="4c39c-110">Their constructors are similar.</span></span> <span data-ttu-id="4c39c-111">用于检索它们的集合的方法相似。</span><span class="sxs-lookup"><span data-stu-id="4c39c-111">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="4c39c-112">属性集合的 LINQ 查询表达式与元素集合的 LINQ 查询表达式看起来非常相似。</span><span class="sxs-lookup"><span data-stu-id="4c39c-112">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="4c39c-113">将属性添加到元素中的顺序会保留下来。</span><span class="sxs-lookup"><span data-stu-id="4c39c-113">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="4c39c-114">也就是说，当循环访问属性时，所见到的属性顺序与它们的添加顺序相同。</span><span class="sxs-lookup"><span data-stu-id="4c39c-114">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="4c39c-115">XAttribute 构造函数</span><span class="sxs-lookup"><span data-stu-id="4c39c-115">The XAttribute Constructor</span></span>  
 <span data-ttu-id="4c39c-116">下面的 <xref:System.Xml.Linq.XAttribute> 类构造函数是您将最常使用的构造函数之一：</span><span class="sxs-lookup"><span data-stu-id="4c39c-116">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="4c39c-117">构造函数</span><span class="sxs-lookup"><span data-stu-id="4c39c-117">Constructor</span></span>|<span data-ttu-id="4c39c-118">说明</span><span class="sxs-lookup"><span data-stu-id="4c39c-118">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="4c39c-119">创建一个 <xref:System.Xml.Linq.XAttribute> 对象。</span><span class="sxs-lookup"><span data-stu-id="4c39c-119">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="4c39c-120">`name` 参数指定属性的名称；`content` 指定属性的内容。</span><span class="sxs-lookup"><span data-stu-id="4c39c-120">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="4c39c-121">创建具有属性的元素</span><span class="sxs-lookup"><span data-stu-id="4c39c-121">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="4c39c-122">下面的代码演示创建包含属性的元素的常见任务：</span><span class="sxs-lookup"><span data-stu-id="4c39c-122">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="4c39c-123">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="4c39c-123">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="4c39c-124">属性的函数构造</span><span class="sxs-lookup"><span data-stu-id="4c39c-124">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="4c39c-125">可以构造与 <xref:System.Xml.Linq.XAttribute> 对象的构造一致的 <xref:System.Xml.Linq.XElement> 对象，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4c39c-125">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 <span data-ttu-id="4c39c-126">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="4c39c-126">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="4c39c-127">属性不是节点</span><span class="sxs-lookup"><span data-stu-id="4c39c-127">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="4c39c-128">属性与元素之间有些区别。</span><span class="sxs-lookup"><span data-stu-id="4c39c-128">There are some differences between attributes and elements.</span></span> <span data-ttu-id="4c39c-129"><xref:System.Xml.Linq.XAttribute> 对象不是 XML 树中的节点。</span><span class="sxs-lookup"><span data-stu-id="4c39c-129"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="4c39c-130">它们是与 XML 元素关联的名称/值对。</span><span class="sxs-lookup"><span data-stu-id="4c39c-130">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="4c39c-131">与文档对象模型 (DOM) 相比，这更加贴切地反映了 XML 结构。</span><span class="sxs-lookup"><span data-stu-id="4c39c-131">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="4c39c-132">虽然 <xref:System.Xml.Linq.XAttribute> 对象实际上不是 XML 树的节点，但使用 <xref:System.Xml.Linq.XAttribute> 对象与使用 <xref:System.Xml.Linq.XElement> 对象非常相似。</span><span class="sxs-lookup"><span data-stu-id="4c39c-132">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="4c39c-133">这一区别仅对编写在节点级使用 XML 树的代码的开发人员特别重要。</span><span class="sxs-lookup"><span data-stu-id="4c39c-133">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="4c39c-134">许多开发人员不会关心这种区别。</span><span class="sxs-lookup"><span data-stu-id="4c39c-134">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c39c-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="4c39c-135">See also</span></span>

- [<span data-ttu-id="4c39c-136">LINQ to XML 编程概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="4c39c-136">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
