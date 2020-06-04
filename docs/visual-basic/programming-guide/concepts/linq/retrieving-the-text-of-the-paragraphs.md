---
title: 检索段落的文本
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 24167ade2d0326ef9382536f79f9e45eb22c89c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413383"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="2b551-102">检索段落的文本（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2b551-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="2b551-103">此示例基于上一示例，[检索段落及其样式（Visual Basic）](retrieving-the-paragraphs-and-their-styles.md)。</span><span class="sxs-lookup"><span data-stu-id="2b551-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="2b551-104">这个新示例将每个段落的文本作为字符串进行检索。</span><span class="sxs-lookup"><span data-stu-id="2b551-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="2b551-105">为检索文本，此示例另外添加了一个查询，该查询循环访问匿名类型的集合，并通过添加新成员 `Text` 对一个匿名类型的新集合进行投影。</span><span class="sxs-lookup"><span data-stu-id="2b551-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="2b551-106">该示例使用 <xref:System.Linq.Enumerable.Aggregate%2A> 标准查询运算符将多个字符串串联为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="2b551-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="2b551-107">这种方法（即首先投影到一个匿名类型集合，然后使用该集合投影到一个新的匿名类型集合）是一种既常用又有效的方法。</span><span class="sxs-lookup"><span data-stu-id="2b551-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="2b551-108">此查询在编写时本来可以不投影到第一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="2b551-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="2b551-109">但是因为使用迟缓计算，即使这样做也并不会过多占用额外的处理能力。</span><span class="sxs-lookup"><span data-stu-id="2b551-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="2b551-110">此方法在堆上创建更多生存时间很短的对象，但这并不会显著降低性能。</span><span class="sxs-lookup"><span data-stu-id="2b551-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="2b551-111">当然，可以只编写一个查询，使之包含检索段落、每个段落的样式以及每个段落的文本这些功能。</span><span class="sxs-lookup"><span data-stu-id="2b551-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="2b551-112">但是，将一个比较复杂的查询分解成多个查询通常很有好处，因为这样产生的代码更加模块化，更易于维护。</span><span class="sxs-lookup"><span data-stu-id="2b551-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="2b551-113">而且，如果需要重用查询的某一部分，使用此方式编写的查询更容易重构。</span><span class="sxs-lookup"><span data-stu-id="2b551-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="2b551-114">这些查询链接在一起，使用主题[教程：延迟执行（Visual Basic）](tutorial-deferred-execution.md)中详细检查的处理模型。</span><span class="sxs-lookup"><span data-stu-id="2b551-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b551-115">示例</span><span class="sxs-lookup"><span data-stu-id="2b551-115">Example</span></span>  
 <span data-ttu-id="2b551-116">本示例处理一个 WordprocessingML 文档，它确定元素节点、样式名称和每个段落的文本。</span><span class="sxs-lookup"><span data-stu-id="2b551-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="2b551-117">本示例以本教程中前面的一些示例为基础构建。</span><span class="sxs-lookup"><span data-stu-id="2b551-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="2b551-118">下面代码中的注释标识出了这个新查询。</span><span class="sxs-lookup"><span data-stu-id="2b551-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="2b551-119">有关创建此示例的源文档的说明，请参阅[创建源 Office OPEN XML 文档（Visual Basic）](creating-the-source-office-open-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="2b551-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="2b551-120">本示例使用 WindowsBase 程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="2b551-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="2b551-121">它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="2b551-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because Visual Basic does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Following is the new query that retrieves the text of  
        ' each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t> _  
                    .Aggregate(New StringBuilder(), _  
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _  
                               Function(s As StringBuilder) s.ToString) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2b551-122">当应用于[创建源 Office OPEN XML 文档（Visual Basic）](creating-the-source-office-open-xml-document.md)中所述的文档时，此示例生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="2b551-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >Imports System<  
StyleName:Code ><  
StyleName:Code >Class Program<  
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >   End Sub<  
StyleName:Code >End Class<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="2b551-123">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2b551-123">Next Steps</span></span>  
 <span data-ttu-id="2b551-124">下面的示例演示如何使用扩展方法而不是 <xref:System.Linq.Enumerable.Aggregate%2A> 将多个字符串串联为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="2b551-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="2b551-125">使用扩展方法重构（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2b551-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b551-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2b551-126">See also</span></span>

- [<span data-ttu-id="2b551-127">教程：在 WordprocessingML 文档中操作内容（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2b551-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="2b551-128">LINQ to XML （Visual Basic）中的延迟执行和迟缓计算</span><span class="sxs-lookup"><span data-stu-id="2b551-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
