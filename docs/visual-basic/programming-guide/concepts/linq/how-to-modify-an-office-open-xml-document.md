---
title: 如何：修改 Office Open XML 文档
ms.date: 07/20/2015
ms.assetid: 1cefd7f5-8e39-44c4-869c-f8021538a777
ms.openlocfilehash: 9fb046f43686405a3d84cb68b49cd6dcd34e0839
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398020"
---
# <a name="how-to-modify-an-office-open-xml-document-visual-basic"></a><span data-ttu-id="aa543-102">如何：修改 Office Open XML 文档（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="aa543-102">How to: Modify an Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="aa543-103">本主题显演示一个打开、修改和保存 Office Open XML 文档的示例。</span><span class="sxs-lookup"><span data-stu-id="aa543-103">This topic presents an example that opens an Office Open XML document, modifies it, and saves it.</span></span>  
  
 <span data-ttu-id="aa543-104">有关 Office Open XML 的详细信息，请参阅[Eric 白的博客](http://www.ericwhite.com)。</span><span class="sxs-lookup"><span data-stu-id="aa543-104">For more information on Office Open XML, see [Eric White's Blog](http://www.ericwhite.com).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa543-105">示例</span><span class="sxs-lookup"><span data-stu-id="aa543-105">Example</span></span>  
 <span data-ttu-id="aa543-106">本示例查找文档中的第一个段落元素。</span><span class="sxs-lookup"><span data-stu-id="aa543-106">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="aa543-107">示例从段落中检索文本，然后删除段落中的所有文本域。</span><span class="sxs-lookup"><span data-stu-id="aa543-107">It retrieves the text from the paragraph, and then deletes all text runs in the paragraph.</span></span> <span data-ttu-id="aa543-108">它创建一个由第一个段落已转换为大写的文本构成的新文本域。</span><span class="sxs-lookup"><span data-stu-id="aa543-108">It creates a new text run that consists of the first paragraph text that has been converted to upper case.</span></span> <span data-ttu-id="aa543-109">然后将已更改的 XML 序列化为 Open XML 包并关闭该包。</span><span class="sxs-lookup"><span data-stu-id="aa543-109">It then serializes the changed XML into the Open XML package and closes it.</span></span>  
  
 <span data-ttu-id="aa543-110">本示例使用 WindowsBase 程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="aa543-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="aa543-111">它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="aa543-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                    .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", _  
                            UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart _  
                        .GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                Dim stylePart As PackagePart = Nothing  
                Dim styleDoc As XDocument = Nothing  
  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri( _  
                            documentUri, styleRelation.TargetUri)  
                    stylePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
  
                Dim paraNode As XElement = xDoc.Root.<w:body>...<w:p>.FirstOrDefault()  
  
                Dim paraText As String = ParagraphText(paraNode)  
  
                ' Remove all text runs.  
                paraNode...<w:r>.Remove()  
  
                paraNode.Add(<w:r><w:t><%= paraText.ToUpper() %></w:t></w:r>)  
  
                ' Save the XML into the package.  
                Using xw As XmlWriter = _  
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write))  
                    xDoc.Save(xw)  
                End Using  
  
                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper())  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="aa543-112">如果在运行此程序之后打开 `SampleDoc.docx`，则可以看到此程序已将文档中的第一个段落转换为大写。</span><span class="sxs-lookup"><span data-stu-id="aa543-112">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>  
  
 <span data-ttu-id="aa543-113">当与[创建源 Office OPEN Xml 文档（Visual Basic）](creating-the-source-office-open-xml-document.md)中所述的示例 Open xml 文档运行时，此示例将生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="aa543-113">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```console  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa543-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa543-114">See also</span></span>

- [<span data-ttu-id="aa543-115">高级查询技术（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="aa543-115">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
