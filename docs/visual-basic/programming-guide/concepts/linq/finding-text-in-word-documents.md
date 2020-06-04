---
title: 查找 Word 文档中的文本
ms.date: 07/20/2015
ms.assetid: eea9819b-a78a-4552-bf13-8837fc0e7a37
ms.openlocfilehash: 546703e3dbead64fd10c04fe52cb1dd98ba53049
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398085"
---
# <a name="finding-text-in-word-documents-visual-basic"></a><span data-ttu-id="e8916-102">查找 Word 文档中的文本（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e8916-102">Finding Text in Word Documents (Visual Basic)</span></span>

<span data-ttu-id="e8916-103">本主题扩展了以前的查询，以执行一些有用的任务：在文档中查找一个字符串的所有匹配项。</span><span class="sxs-lookup"><span data-stu-id="e8916-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>

## <a name="example"></a><span data-ttu-id="e8916-104">示例</span><span class="sxs-lookup"><span data-stu-id="e8916-104">Example</span></span>

<span data-ttu-id="e8916-105">本示例处理一个 WordprocessingML 文档，在该文档中查找特定文本片断的所有匹配项。</span><span class="sxs-lookup"><span data-stu-id="e8916-105">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="e8916-106">为演示此操作，我们使用一个查询，查找字符串“Hello”。</span><span class="sxs-lookup"><span data-stu-id="e8916-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="e8916-107">本示例以本教程中前面的一些示例为基础构建。</span><span class="sxs-lookup"><span data-stu-id="e8916-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="e8916-108">下面代码中的注释标识出了这个新查询。</span><span class="sxs-lookup"><span data-stu-id="e8916-108">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="e8916-109">有关创建此示例的源文档的说明，请参阅[创建源 Office OPEN XML 文档（Visual Basic）](creating-the-source-office-open-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="e8916-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="e8916-110">本示例使用 WindowsBase 程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="e8916-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="e8916-111">它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="e8916-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As String In source
            sb.Append(s)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item))
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As T In source
            sb.Append(s).Append(separator)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String), ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item)).Append(separator)
        Next
        Return sb.ToString()
    End Function

    Public Function ParagraphText(ByVal e As XElement) As String
        Dim w As XNamespace = e.Name.Namespace
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))
    End Function

    ' Following function is required because Visual Basic does not support short circuit evaluation
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"
        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
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

        ' Retrieve the text of each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = ParagraphText(para.ParagraphNode) _
            }

        ' Following is the new query that retrieves all paragraphs
        ' that have specific text in them.
        Dim helloParagraphs = _
            From para In paraWithText _
            Where para.Text.Contains("Hello") _
            Select New With _
            { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = para.Text _
            }

        For Each p In helloParagraphs
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next
    End Sub
End Module
```

<span data-ttu-id="e8916-112">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="e8916-112">This example produces the following output:</span></span>

```console
StyleName:Code >        Console.WriteLine("Hello World")<
StyleName:Code >Hello World<
```

<span data-ttu-id="e8916-113">当然，您可以修改搜索条件，使它搜索具有特定样式的行。</span><span class="sxs-lookup"><span data-stu-id="e8916-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="e8916-114">下面的查询查找具有“Code”样式的所有空行：</span><span class="sxs-lookup"><span data-stu-id="e8916-114">The following query finds all blank lines that have the Code style:</span></span>

```vb
Imports System.IO.Packaging
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As String In source
            sb.Append(s)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String)) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item))
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each s As T In source
            sb.Append(s).Append(separator)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String), ByVal separator As String) As String
        Dim sb As StringBuilder = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item)).Append(separator)
        Next
        Return sb.ToString()
    End Function

    Public Function ParagraphText(ByVal e As XElement) As String
        Dim w As XNamespace = e.Name.Namespace
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))
    End Function

    ' Following function is required because Visual Basic does not support short circuit evaluation
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"
        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
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

        ' Retrieve the text of each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = ParagraphText(para.ParagraphNode) _
            }

        ' Retrieve all paragraphs that have no text and are styled Code.
        Dim blankCodeParagraphs = _
            From para In paraWithText _
            Where String.IsNullOrEmpty(para.Text) And para.StyleName.Equals("Code") _
            Select New With _
            { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = para.Text _
            }

        For Each p In blankCodeParagraphs
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next
    End Sub
End Module
```

<span data-ttu-id="e8916-115">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="e8916-115">This example produces the following output:</span></span>

```console
StyleName:Code ><
```

<span data-ttu-id="e8916-116">当然，可以通过多种方式对此示例进行改进。</span><span class="sxs-lookup"><span data-stu-id="e8916-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="e8916-117">例如，可以使用正则表达式来搜索文本，可以循环访问某一特定目录下的所有 Word 文件等等。</span><span class="sxs-lookup"><span data-stu-id="e8916-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>

<span data-ttu-id="e8916-118">请注意，此示例的执行效果与将它编写为一个单个查询几乎同样好。</span><span class="sxs-lookup"><span data-stu-id="e8916-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="e8916-119">因为每个查询都以迟缓方式实现，每个查询直到循环到该查询时才生成结果。</span><span class="sxs-lookup"><span data-stu-id="e8916-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="e8916-120">有关执行和迟缓计算的详细信息，请参阅[LINQ to XML （Visual Basic）中的延迟执行和迟缓计算](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e8916-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e8916-121">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e8916-121">Next Steps</span></span>

<span data-ttu-id="e8916-122">下一节提供有关 WordprocessingML 文档的更多信息：</span><span class="sxs-lookup"><span data-stu-id="e8916-122">The next section provides more information about WordprocessingML documents:</span></span>

- [<span data-ttu-id="e8916-123">Office Open XML WordprocessingML 文档的详细信息（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e8916-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)

## <a name="see-also"></a><span data-ttu-id="e8916-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8916-124">See also</span></span>

- [<span data-ttu-id="e8916-125">教程：在 WordprocessingML 文档中操作内容（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e8916-125">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="e8916-126">使用纯函数重构 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8916-126">Refactoring Using a Pure Function (Visual Basic)</span></span>](refactoring-using-a-pure-function.md)
- [<span data-ttu-id="e8916-127">LINQ to XML （Visual Basic）中的延迟执行和迟缓计算</span><span class="sxs-lookup"><span data-stu-id="e8916-127">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
