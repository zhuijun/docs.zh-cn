---
title: 功能构造 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f42cd6f31134c5f4c7d6a75f38997b2be0c317f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398059"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="92f59-102">函数构造（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="92f59-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="92f59-103">为创建 XML 元素提供了一种称为“函数构造”  的有效方式。</span><span class="sxs-lookup"><span data-stu-id="92f59-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="92f59-104">函数构造是指在单个语句中创建 XML 树的能力。</span><span class="sxs-lookup"><span data-stu-id="92f59-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="92f59-105">启用函数构造的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 编程接口有几个重要功能：</span><span class="sxs-lookup"><span data-stu-id="92f59-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="92f59-106"><xref:System.Xml.Linq.XElement> 构造函数可以对内容采用多种类型的参数。</span><span class="sxs-lookup"><span data-stu-id="92f59-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="92f59-107">例如，可以传递另一个 <xref:System.Xml.Linq.XElement> 对象，该对象将成为一个子元素。</span><span class="sxs-lookup"><span data-stu-id="92f59-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="92f59-108">可以传递一个 <xref:System.Xml.Linq.XAttribute> 对象，该对象将成为该元素的一个属性。</span><span class="sxs-lookup"><span data-stu-id="92f59-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="92f59-109">也可以传递任何其他类型的对象，该对象将转换为字符串并成为该元素的文本内容。</span><span class="sxs-lookup"><span data-stu-id="92f59-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="92f59-110"><xref:System.Xml.Linq.XElement> 函数采用类型为 `params` 的 <xref:System.Object> 数组，因此可以向该构造函数传递任意数目的对象。</span><span class="sxs-lookup"><span data-stu-id="92f59-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="92f59-111">这使您可以创建具有复杂内容的元素。</span><span class="sxs-lookup"><span data-stu-id="92f59-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="92f59-112">如果对象实现 <xref:System.Collections.Generic.IEnumerable%601>，则枚举对象中的集合，并添加集合中的所有项。</span><span class="sxs-lookup"><span data-stu-id="92f59-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="92f59-113">如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 对象，则单独添加集合中的每一项。</span><span class="sxs-lookup"><span data-stu-id="92f59-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="92f59-114">这一功能很重要，因为它允许你将 LINQ 查询的结果传递给构造函数。</span><span class="sxs-lookup"><span data-stu-id="92f59-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="92f59-115">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="92f59-115">The following is an example:</span></span>  
  
 <span data-ttu-id="92f59-116">这些功能使您可以使用 XML 文本编写代码来创建 XML 树，还可以编写在创建 XML 树时使用 LINQ 查询结果的代码：</span><span class="sxs-lookup"><span data-stu-id="92f59-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of LINQ queries when you create an XML tree:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="92f59-117">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="92f59-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92f59-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="92f59-118">See also</span></span>

- [<span data-ttu-id="92f59-119">创建 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="92f59-119">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
