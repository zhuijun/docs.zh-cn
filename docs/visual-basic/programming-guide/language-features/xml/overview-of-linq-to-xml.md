---
title: LINQ to XML 概述
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 044aca634f5a0aa6e557a7dd9c0e1de64e35dc15
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374650"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="bb9e2-102">Visual Basic 中的 LINQ to XML 概述</span><span class="sxs-lookup"><span data-stu-id="bb9e2-102">Overview of LINQ to XML in Visual Basic</span></span>
<span data-ttu-id="bb9e2-103">Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 通过 xml 文本和 xml 轴属性提供对的支持。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-103">Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="bb9e2-104">这使你可以使用熟悉的方便语法在 Visual Basic 代码中处理 XML。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-104">This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code.</span></span> <span data-ttu-id="bb9e2-105">使用*xml 文本*可以将 xml 直接包含在代码中。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="bb9e2-106">利用*xml 轴属性*，您可以访问 xml 文本的子节点、子代节点和属性。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="bb9e2-107">有关详细信息，请参阅[Xml 文本概述](xml-literals-overview.md)和[访问 VISUAL BASIC 中的 xml](accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-107">For more information, see [XML Literals Overview](xml-literals-overview.md) and [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="bb9e2-108">是内存中的 XML 编程 API，专门设计用于利用语言集成查询（LINQ）。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-108">is an in-memory XML programming API designed specifically to take advantage of Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="bb9e2-109">尽管可以直接调用 LINQ Api，但只有 Visual Basic 允许你声明 XML 文本和直接访问 XML 轴属性。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-109">Although you can call the LINQ APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb9e2-110">ASP.NET 页面中的声明性代码不支持 XML 文本和 XML 轴属性。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="bb9e2-111">若要使用 Visual Basic XML 功能，请将代码放在 ASP.NET 应用程序的代码隐藏页中。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="bb9e2-112">[播放按钮](./media/overview-of-linq-to-xml/play-video-icon-example.gif)有关相关的视频演示，请参阅[如何开始使用 LINQ to XML？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)和[如何使用 LINQ to XML 创建 Excel 电子表格？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-112">[Play button](./media/overview-of-linq-to-xml/play-video-icon-example.gif) For related video demonstrations, see [How Do I Get Started with LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) and [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span></span>
  
## <a name="creating-xml"></a><span data-ttu-id="bb9e2-113">创建 XML</span><span class="sxs-lookup"><span data-stu-id="bb9e2-113">Creating XML</span></span>  
 <span data-ttu-id="bb9e2-114">可以通过两种方式在 Visual Basic 中创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-114">There are two ways to create XML trees in Visual Basic.</span></span> <span data-ttu-id="bb9e2-115">你可以直接在代码中声明 XML 文本，或者可以使用 LINQ Api 创建树。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-115">You can declare an XML literal directly in code, or you can use the LINQ APIs to create the tree.</span></span> <span data-ttu-id="bb9e2-116">这两个进程都使代码可以反映 XML 树的最终结构。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="bb9e2-117">例如，下面的代码示例创建一个 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="bb9e2-117">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 <span data-ttu-id="bb9e2-118">有关详细信息，请参阅[在 Visual Basic 中创建 XML](creating-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-118">For more information, see [Creating XML in Visual Basic](creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="bb9e2-119">访问和导航 XML</span><span class="sxs-lookup"><span data-stu-id="bb9e2-119">Accessing and Navigating XML</span></span>  
 <span data-ttu-id="bb9e2-120">Visual Basic 提供了用于访问和导航 XML 结构的 XML 轴属性。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-120">Visual Basic provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="bb9e2-121">这些属性使你可以通过指定 XML 子元素名称来访问 XML 元素和特性。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-121">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="bb9e2-122">或者，你可以显式调用用于导航和查找元素和属性的 LINQ 方法。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-122">Alternatively, you can explicitly call the LINQ methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="bb9e2-123">例如，下面的代码示例使用 XML 轴属性来引用 XML 元素的特性和子元素。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-123">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="bb9e2-124">此代码示例使用 LINQ 查询来检索子元素，并将其输出为 XML 元素，从而有效地执行转换。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-124">The code example uses a LINQ query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 <span data-ttu-id="bb9e2-125">有关详细信息，请参阅[Visual Basic 中的访问 XML](accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-125">For more information, see [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="bb9e2-126">XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="bb9e2-126">XML Namespaces</span></span>  
 <span data-ttu-id="bb9e2-127">Visual Basic 使你能够使用语句指定全局 XML 命名空间的别名 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-127">Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="bb9e2-128">下面的示例演示如何使用 `Imports` 语句导入 XML 命名空间：</span><span class="sxs-lookup"><span data-stu-id="bb9e2-128">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 <span data-ttu-id="bb9e2-129">访问 XML 轴属性并声明 xml 文档和元素的 XML 文本时，可以使用 XML 命名空间别名。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-129">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="bb9e2-130">可以 <xref:System.Xml.Linq.XNamespace> 使用[GetXmlNamespace 运算符](../../../language-reference/operators/getxmlnamespace-operator.md)检索特定命名空间前缀的对象。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-130">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="bb9e2-131">有关详细信息，请参阅[Imports 语句（XML 命名空间）](../../../language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-131">For more information, see [Imports Statement (XML Namespace)](../../../language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="bb9e2-132">在 XML 文本中使用 XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="bb9e2-132">Using XML Namespaces in XML Literals</span></span>  
 <span data-ttu-id="bb9e2-133">下面的示例演示如何创建 <xref:System.Xml.Linq.XElement> 使用 global 命名空间的对象 `ns` ：</span><span class="sxs-lookup"><span data-stu-id="bb9e2-133">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 <span data-ttu-id="bb9e2-134">Visual Basic 编译器将包含 XML 命名空间别名的 XML 文本转换为等效代码，该代码使用 XML 表示法，使用 xml 命名空间和 `xmlns` 属性。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-134">The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="bb9e2-135">在编译时，上一部分的示例中的代码将产生实质上与以下示例相同的可执行代码：</span><span class="sxs-lookup"><span data-stu-id="bb9e2-135">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="bb9e2-136">在 XML 轴属性中使用 XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="bb9e2-136">Using XML Namespaces in XML Axis Properties</span></span>  
 <span data-ttu-id="bb9e2-137">在 xml 文本中声明的 XML 命名空间不可用于 XML 轴属性。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-137">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="bb9e2-138">但是，可以将全局命名空间与 XML 轴属性一起使用。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-138">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="bb9e2-139">使用冒号分隔 XML 命名空间前缀和本地元素名称。</span><span class="sxs-lookup"><span data-stu-id="bb9e2-139">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="bb9e2-140">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="bb9e2-140">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bb9e2-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb9e2-141">See also</span></span>

- [<span data-ttu-id="bb9e2-142">XML</span><span class="sxs-lookup"><span data-stu-id="bb9e2-142">XML</span></span>](index.md)
- [<span data-ttu-id="bb9e2-143">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="bb9e2-143">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="bb9e2-144">在 Visual Basic 中访问 XML</span><span class="sxs-lookup"><span data-stu-id="bb9e2-144">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="bb9e2-145">在 Visual Basic 中操作 XML</span><span class="sxs-lookup"><span data-stu-id="bb9e2-145">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
