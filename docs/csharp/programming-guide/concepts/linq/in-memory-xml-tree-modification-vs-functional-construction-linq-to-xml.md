---
title: 内存中 XML 树修改与函数构造 (LINQ to XML) (C#)
description: 这些示例通过就地修改 XML 文档并使用 C# 中的 LINQ to XML 函数构造来更改 XML 文档的形状。
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 7a2e3d2ddcd452cf6a58e9d5cc886f3e8b8dd325
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165784"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="5d8b6-103">内存中 XML 树修改与函数构造 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5d8b6-103">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5d8b6-104">就地修改 XML 树是更改 XML 文档形状的传统方法。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="5d8b6-105">典型的应用程序将文档加载到数据存储区（如 DOM 或 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]）；使用编程接口插入节点、删除节点或更改节点的内容；然后将 XML 保存到文件或通过网络传输。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-105">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5d8b6-106">允许使用另一种可在许多方案中使用的方法：函数构造。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-106">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="5d8b6-107">函数构造将修改数据视为转换问题，而不是数据存储区的具体操作。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="5d8b6-108">如果您采用某种数据表示形式并有效地将其从一种形式转换为另一种形式，其结果等效于您采用一个数据存储区并对其以某种方式进行操作以采用另一种形状。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="5d8b6-109">函数构造方法的关键是将查询的结果传递给 <xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 构造函数。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="5d8b6-110">在许多情况下，您可以在操作数据存储区所需的很短时间内编写转换代码，并且该代码更稳定、更易于维护。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="5d8b6-111">在这些情况下，虽然转换方法可能具有较强的处理能力，但它更适合用于修改数据。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-111">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="5d8b6-112">如果开发人员熟悉函数方法，则在很多情况下，生成的代码会更易于理解。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="5d8b6-113">可以很容易地找到修改树的每部分的代码。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-113">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="5d8b6-114">DOM 程序员更熟悉就地修改 XML 树的方法，而不了解这种方法的开发人员可能会对使用函数方法编写的代码感到陌生。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-114">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="5d8b6-115">如果您必须对大型 XML 树进行小修改，则在很多情况下，用于就地修改树的方法将花费更少的 CPU 时间。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-115">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="5d8b6-116">本主题提供用这两种方法实现的一个示例。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-116">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="5d8b6-117">将属性转换为元素</span><span class="sxs-lookup"><span data-stu-id="5d8b6-117">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="5d8b6-118">此示例假设您想修改下面的简单 XML 文档，使属性变为元素。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-118">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="5d8b6-119">本节首先介绍传统的就地修改方法。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-119">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="5d8b6-120">然后显示函数构造方法。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-120">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="5d8b6-121">修改 XML 树</span><span class="sxs-lookup"><span data-stu-id="5d8b6-121">Modifying the XML Tree</span></span>  
 <span data-ttu-id="5d8b6-122">您可以编写一些过程代码以便从属性创建元素，然后删除属性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d8b6-122">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="5d8b6-123">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="5d8b6-123">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="5d8b6-124">函数构造方法</span><span class="sxs-lookup"><span data-stu-id="5d8b6-124">Functional Construction Approach</span></span>  
 <span data-ttu-id="5d8b6-125">相比之下，函数方法包含用于形成新树的代码、从源树中选择元素和属性并在将其添加到新树中时进行相应的转换。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-125">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="5d8b6-126">函数方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d8b6-126">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="5d8b6-127">本示例与第一个示例输出相同的 XML。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-127">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="5d8b6-128">但请注意，您可以在函数方法中实际看到生成的新 XML 的结构。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-128">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="5d8b6-129">您可以看到创建 `Root` 元素的代码、从源树中提取 `Child1` 元素的代码和将源树中的属性转换为新树中的元素的代码。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-129">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="5d8b6-130">在本例中，函数示例一点也不比第一个示例简短，而且一点也不比第一个示例简单。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-130">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="5d8b6-131">但如果要对一个 XML 树进行很多更改，则非函数方法将变得非常复杂，而且会显得很笨拙。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-131">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="5d8b6-132">相比之下，使用函数方法时，您只需形成所需的 XML，嵌入适当的查询和表达式以提取需要的内容。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-132">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="5d8b6-133">函数方法生成的代码更易于维护。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-133">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="5d8b6-134">请注意，在本例中，函数方法的执行效果可能没有树操作方法好。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-134">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="5d8b6-135">主要问题是函数方法创建了更多短生存期的对象。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-135">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="5d8b6-136">但是，如果使用函数方法能够提高程序员的效率，则折中也是一种有效的方式。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-136">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="5d8b6-137">这是一个很简单的示例，但它显示了这两种方法之间基本原理上的差异。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-137">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="5d8b6-138">对于转换较大的 XML 文档，函数方法可以产生更高的效率增益。</span><span class="sxs-lookup"><span data-stu-id="5d8b6-138">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  