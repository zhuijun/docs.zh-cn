---
title: 使用扩展方法重构
ms.date: 07/20/2015
ms.assetid: d87ae99a-cfa9-4a31-a5e4-9d6437be6810
ms.openlocfilehash: 5bb3ed44c0c3f7616468f820428fe1a384ab6d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413424"
---
# <a name="refactoring-using-an-extension-method-visual-basic"></a><span data-ttu-id="7608c-102">使用扩展方法重构（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7608c-102">Refactoring Using an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="7608c-103">此示例基于上一个示例，通过使用作为扩展方法实现的纯函数来重构字符串的串联来[检索段落的文本（Visual Basic）](retrieving-the-text-of-the-paragraphs.md)。</span><span class="sxs-lookup"><span data-stu-id="7608c-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (Visual Basic)](retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="7608c-104">前面的示例使用 <xref:System.Linq.Enumerable.Aggregate%2A> 标准查询运算符将多个字符串串联为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="7608c-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="7608c-105">不过，编写一个扩展方法来执行此操作会更方便，因为这样实现的查询会更小、更简单。</span><span class="sxs-lookup"><span data-stu-id="7608c-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7608c-106">示例</span><span class="sxs-lookup"><span data-stu-id="7608c-106">Example</span></span>  
 <span data-ttu-id="7608c-107">本示例处理一个 WordprocessingML 文档，检索段落、每个段落的样式以及每个段落的文本。</span><span class="sxs-lookup"><span data-stu-id="7608c-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="7608c-108">本示例以本教程中前面的一些示例为基础构建。</span><span class="sxs-lookup"><span data-stu-id="7608c-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="7608c-109">本示例包含 `StringConcatenate` 方法的多个重载。</span><span class="sxs-lookup"><span data-stu-id="7608c-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="7608c-110">您可以在[创建源 Office OPEN XML 文档（Visual Basic）](creating-the-source-office-open-xml-document.md)中找到用于创建此示例的源文档的说明。</span><span class="sxs-lookup"><span data-stu-id="7608c-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="7608c-111">本示例使用 WindowsBase 程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="7608c-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="7608c-112">它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="7608c-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
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
```  
  
## <a name="example"></a><span data-ttu-id="7608c-113">示例</span><span class="sxs-lookup"><span data-stu-id="7608c-113">Example</span></span>  
 <span data-ttu-id="7608c-114">`StringConcatenate` 方法有四个重载。</span><span class="sxs-lookup"><span data-stu-id="7608c-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="7608c-115">其中一个重载仅接受字符串集合并返回单个字符串。</span><span class="sxs-lookup"><span data-stu-id="7608c-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="7608c-116">另一个重载可以接受任何类型的集合，以及从该集合的单一实例映射到字符串的委托。</span><span class="sxs-lookup"><span data-stu-id="7608c-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="7608c-117">使用其余两个重载可以指定分隔符字符串。</span><span class="sxs-lookup"><span data-stu-id="7608c-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="7608c-118">下面的代码使用所有四个重载。</span><span class="sxs-lookup"><span data-stu-id="7608c-118">The following code uses all four overloads.</span></span>  
  
```vb  
Dim numbers As String() = {"one", "two", "three"}  
  
Console.WriteLine("{0}", numbers.StringConcatenate())  
Console.WriteLine("{0}", numbers.StringConcatenate(":"))  
  
Dim intNumbers As Integer() = {1, 2, 3}  
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString()))  
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString(), ":"))  
```  
  
 <span data-ttu-id="7608c-119">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="7608c-119">This example produces the following output:</span></span>  
  
```console  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="7608c-120">示例</span><span class="sxs-lookup"><span data-stu-id="7608c-120">Example</span></span>  
 <span data-ttu-id="7608c-121">现在，可以对示例进行修改，从而利用新扩展方法。</span><span class="sxs-lookup"><span data-stu-id="7608c-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t>.StringConcatenate(Function(e) CStr(e)) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7608c-122">当应用于[创建源 Office OPEN XML 文档（Visual Basic）](creating-the-source-office-open-xml-document.md)中所述的文档时，此示例生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="7608c-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>
  
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
  
 <span data-ttu-id="7608c-123">请注意，此重构是重构到纯函数的一种变体。</span><span class="sxs-lookup"><span data-stu-id="7608c-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="7608c-124">下一主题将更详细地介绍重构到纯函数的概念。</span><span class="sxs-lookup"><span data-stu-id="7608c-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7608c-125">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7608c-125">Next Steps</span></span>  
 <span data-ttu-id="7608c-126">下一示例演示如何使用纯函数以其他方式重构此代码：</span><span class="sxs-lookup"><span data-stu-id="7608c-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="7608c-127">使用纯函数重构 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7608c-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="7608c-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7608c-128">See also</span></span>

- [<span data-ttu-id="7608c-129">教程：在 WordprocessingML 文档中操作内容（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7608c-129">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="7608c-130">重构为纯函数（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7608c-130">Refactoring Into Pure Functions (Visual Basic)</span></span>](refactoring-into-pure-functions.md)
