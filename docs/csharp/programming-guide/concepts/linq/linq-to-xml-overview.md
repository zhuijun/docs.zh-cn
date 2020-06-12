---
title: LINQ to XML 概述 (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: dd41d8607ef3f2e6e6be9a1f3964ef0ae937e2ac
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241833"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="5b44a-102">LINQ to XML 概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="5b44a-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="5b44a-103">LINQ to XML 提供使用 .NET 语言集成查询 (LINQ) Framework 的内存中 XML 编程接口。</span><span class="sxs-lookup"><span data-stu-id="5b44a-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="5b44a-104">LINQ to XML 使用 .NET 功能，相当于更新的和重新设计的文档对象模型 (DOM) XML 编程接口。</span><span class="sxs-lookup"><span data-stu-id="5b44a-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="5b44a-105">在很多环境中，XML 已广泛采用为格式化数据的方式。</span><span class="sxs-lookup"><span data-stu-id="5b44a-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="5b44a-106">例如，在 Web 上，在配置文件、Microsoft Office Word 文件以及数据库中，都可以看到 XML。</span><span class="sxs-lookup"><span data-stu-id="5b44a-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5b44a-107">经过了重新设计，是最新的 XML 编程方法。</span><span class="sxs-lookup"><span data-stu-id="5b44a-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="5b44a-108">提供文档对象模型 (DOM) 的内存中文档修改功能，并支持 LINQ 查询表达式。</span><span class="sxs-lookup"><span data-stu-id="5b44a-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="5b44a-109">尽管这些查询表达式在语法上与 XPath 不同，但它们提供类似的功能。</span><span class="sxs-lookup"><span data-stu-id="5b44a-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="5b44a-110">LINQ to XML 开发人员</span><span class="sxs-lookup"><span data-stu-id="5b44a-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5b44a-111">是面向各种开发人员的。</span><span class="sxs-lookup"><span data-stu-id="5b44a-111">targets a variety of developers.</span></span> <span data-ttu-id="5b44a-112">对于只想完成某项工作的普通开发人员，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 通过提供与 SQL 相似的查询表达式，使 XML 变得更加简单。</span><span class="sxs-lookup"><span data-stu-id="5b44a-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="5b44a-113">只要稍加学习，程序员就能学会以自己选择的编程语言编写简洁、功能强大的查询。</span><span class="sxs-lookup"><span data-stu-id="5b44a-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="5b44a-114">专业开发人员可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 来大幅提高他们的工作效率。</span><span class="sxs-lookup"><span data-stu-id="5b44a-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="5b44a-115">通过使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，他们可以编写出表达能力更强、更为紧凑、功能更强的代码。</span><span class="sxs-lookup"><span data-stu-id="5b44a-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="5b44a-116">他们可以同时对多个数据域使用查询表达式。</span><span class="sxs-lookup"><span data-stu-id="5b44a-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="5b44a-117">什么是 LINQ to XML？</span><span class="sxs-lookup"><span data-stu-id="5b44a-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5b44a-118">是一种启用了 LINQ 的内存中 XML 编程接口，支持在 .NET 编程语言中处理 XML。</span><span class="sxs-lookup"><span data-stu-id="5b44a-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5b44a-119">将 XML 文档置于内存中，这一点很像文档对象模型 (DOM)。</span><span class="sxs-lookup"><span data-stu-id="5b44a-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="5b44a-120">您可以查询和修改 XML 文档，修改之后，可以将其另存为文件，也可以将其序列化然后通过 Internet 发送。</span><span class="sxs-lookup"><span data-stu-id="5b44a-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="5b44a-121">但是，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 与 DOM 不同：它提供一种新的对象模型，这是一种更轻量的模型，使用也更方便，这种模型利用了 C# 中的语言功能。</span><span class="sxs-lookup"><span data-stu-id="5b44a-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="5b44a-122">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 最重要的优势是它与语言集成查询 (LINQ) 的集成。</span><span class="sxs-lookup"><span data-stu-id="5b44a-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="5b44a-123">由于实现了这一集成，因此，可以对内存 XML 文档编写查询，以检索元素和属性的集合。</span><span class="sxs-lookup"><span data-stu-id="5b44a-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="5b44a-124">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的查询功能在功能上（尽管不是在语法上）与 XPath 和 XQuery 具有可比性。</span><span class="sxs-lookup"><span data-stu-id="5b44a-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="5b44a-125">C# 中的 LINQ 集成可提供更强的类型化功能、编译时检查和改进的调试器支持。</span><span class="sxs-lookup"><span data-stu-id="5b44a-125">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="5b44a-126">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的另一个优势是通过将查询结果用作 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 对象构造函数的参数，实现了一种功能强大的创建 XML 树的方法。</span><span class="sxs-lookup"><span data-stu-id="5b44a-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="5b44a-127">此方法称为*功能构造*，可使开发人员轻松地将 XML 树从一个形状转换成另一个形状。</span><span class="sxs-lookup"><span data-stu-id="5b44a-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="5b44a-128">例如，可能有典型 XML 采购订单，如[示例 XML 文件：典型采购订单 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md) 中所述。</span><span class="sxs-lookup"><span data-stu-id="5b44a-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="5b44a-129">通过使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，可以运行以下查询，以获取采购单每个项元素的部件号属性值：</span><span class="sxs-lookup"><span data-stu-id="5b44a-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="5b44a-130">这可以采用方法语法形式重写：</span><span class="sxs-lookup"><span data-stu-id="5b44a-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="5b44a-131">另一个示例，您可能需要一个列表，列出值大于 100 美元的项，并根据部件号排序。</span><span class="sxs-lookup"><span data-stu-id="5b44a-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="5b44a-132">若要获取此信息，可以运行下面的查询：</span><span class="sxs-lookup"><span data-stu-id="5b44a-132">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

<span data-ttu-id="5b44a-133">同样，这也可采用方法语法形式重写：</span><span class="sxs-lookup"><span data-stu-id="5b44a-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="5b44a-134">除了这些 LINQ 功能以外，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供了改进的 XML 编程接口。</span><span class="sxs-lookup"><span data-stu-id="5b44a-134">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="5b44a-135">使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，您可以：</span><span class="sxs-lookup"><span data-stu-id="5b44a-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="5b44a-136">从[文件](how-to-load-xml-from-a-file.md)或[流](how-to-stream-xml-fragments-from-an-xmlreader.md)加载 XML。</span><span class="sxs-lookup"><span data-stu-id="5b44a-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="5b44a-137">将 XML 序列化为文件或流。</span><span class="sxs-lookup"><span data-stu-id="5b44a-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="5b44a-138">使用函数构造从头开始创建 XML。</span><span class="sxs-lookup"><span data-stu-id="5b44a-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="5b44a-139">使用类似 XPath 的轴查询 XML。</span><span class="sxs-lookup"><span data-stu-id="5b44a-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="5b44a-140">使用 <xref:System.Xml.Linq.XContainer.Add%2A>、<xref:System.Xml.Linq.XNode.Remove%2A>、<xref:System.Xml.Linq.XNode.ReplaceWith%2A> 和 <xref:System.Xml.Linq.XElement.SetValue%2A> 等方法对内存 XML 树进行操作。</span><span class="sxs-lookup"><span data-stu-id="5b44a-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="5b44a-141">使用 XSD 验证 XML 树。</span><span class="sxs-lookup"><span data-stu-id="5b44a-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="5b44a-142">使用这些功能的组合，可将 XML 树从一种形状转换为另一种形状。</span><span class="sxs-lookup"><span data-stu-id="5b44a-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="5b44a-143">创建 XML 树</span><span class="sxs-lookup"><span data-stu-id="5b44a-143">Creating XML Trees</span></span>

<span data-ttu-id="5b44a-144">使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 编程的一个明显优势是易于创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="5b44a-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="5b44a-145">例如，若要创建一个小型 XML 树，可以编写以下代码：</span><span class="sxs-lookup"><span data-stu-id="5b44a-145">For example, to create a small XML tree, you can write code as follows:</span></span>

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
        new XElement("Address",
            new XElement("Street1", "123 Main St"),
            new XElement("City", "Mercer Island"),
            new XElement("State", "WA"),
            new XElement("Postal", "68042")
        )
    )
);
```

<span data-ttu-id="5b44a-146">有关详细信息，请参阅[创建 XML 树 (C#)](./creating-xml-trees-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="5b44a-146">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b44a-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="5b44a-147">See also</span></span>

- [<span data-ttu-id="5b44a-148">参考 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5b44a-148">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="5b44a-149">LINQ to XML 与DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="5b44a-149">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="5b44a-150">LINQ to XML 与其他 XML 技术</span><span class="sxs-lookup"><span data-stu-id="5b44a-150">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
