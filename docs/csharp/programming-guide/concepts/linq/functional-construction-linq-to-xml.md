---
title: 函数构造 (LINQ to XML) (C#)
description: 了解 LINQ to XML 编程接口如何启用函数构造，即在 C# 中的单个语句中创建 XML 树的能力。
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: f209a7ef2a4597ec8eeccb3083b77223a27e7a65
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103769"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="4b462-103">函数构造 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4b462-103">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="4b462-104">为创建 XML 元素提供了一种称为“函数构造”的有效方式。</span><span class="sxs-lookup"><span data-stu-id="4b462-104">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="4b462-105">函数构造是指在单个语句中创建 XML 树的能力。</span><span class="sxs-lookup"><span data-stu-id="4b462-105">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="4b462-106">启用函数构造的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 编程接口有几个重要功能：</span><span class="sxs-lookup"><span data-stu-id="4b462-106">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="4b462-107"><xref:System.Xml.Linq.XElement> 构造函数可以对内容采用多种类型的参数。</span><span class="sxs-lookup"><span data-stu-id="4b462-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="4b462-108">例如，可以传递另一个 <xref:System.Xml.Linq.XElement> 对象，该对象将成为一个子元素。</span><span class="sxs-lookup"><span data-stu-id="4b462-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="4b462-109">可以传递一个 <xref:System.Xml.Linq.XAttribute> 对象，该对象将成为该元素的一个属性。</span><span class="sxs-lookup"><span data-stu-id="4b462-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="4b462-110">也可以传递任何其他类型的对象，该对象将转换为字符串并成为该元素的文本内容。</span><span class="sxs-lookup"><span data-stu-id="4b462-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="4b462-111"><xref:System.Xml.Linq.XElement> 函数采用类型为 `params` 的 <xref:System.Object> 数组，因此可以向该构造函数传递任意数目的对象。</span><span class="sxs-lookup"><span data-stu-id="4b462-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="4b462-112">这使您可以创建具有复杂内容的元素。</span><span class="sxs-lookup"><span data-stu-id="4b462-112">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="4b462-113">如果对象实现 <xref:System.Collections.Generic.IEnumerable%601>，则枚举对象中的集合，并添加集合中的所有项。</span><span class="sxs-lookup"><span data-stu-id="4b462-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="4b462-114">如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 对象，则单独添加集合中的每一项。</span><span class="sxs-lookup"><span data-stu-id="4b462-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="4b462-115">这一功能很重要，因为它允许你将 LINQ 查询的结果传递给构造函数。</span><span class="sxs-lookup"><span data-stu-id="4b462-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="4b462-116">这些功能使你能够编写代码来创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="4b462-116">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="4b462-117">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="4b462-117">The following is an example:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="4b462-118">这些功能还使你能够在创建 XML 树时，编写使用 LINQ 查询结果的代码，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b462-118">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="4b462-119">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="4b462-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  