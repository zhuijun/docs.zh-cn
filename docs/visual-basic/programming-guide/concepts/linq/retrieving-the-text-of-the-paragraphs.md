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
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a>检索段落的文本（Visual Basic）
此示例基于上一示例，[检索段落及其样式（Visual Basic）](retrieving-the-paragraphs-and-their-styles.md)。 这个新示例将每个段落的文本作为字符串进行检索。  
  
 为检索文本，此示例另外添加了一个查询，该查询循环访问匿名类型的集合，并通过添加新成员 `Text` 对一个匿名类型的新集合进行投影。 该示例使用 <xref:System.Linq.Enumerable.Aggregate%2A> 标准查询运算符将多个字符串串联为一个字符串。  
  
 这种方法（即首先投影到一个匿名类型集合，然后使用该集合投影到一个新的匿名类型集合）是一种既常用又有效的方法。 此查询在编写时本来可以不投影到第一个匿名类型。 但是因为使用迟缓计算，即使这样做也并不会过多占用额外的处理能力。 此方法在堆上创建更多生存时间很短的对象，但这并不会显著降低性能。  
  
 当然，可以只编写一个查询，使之包含检索段落、每个段落的样式以及每个段落的文本这些功能。 但是，将一个比较复杂的查询分解成多个查询通常很有好处，因为这样产生的代码更加模块化，更易于维护。 而且，如果需要重用查询的某一部分，使用此方式编写的查询更容易重构。  
  
 这些查询链接在一起，使用主题[教程：延迟执行（Visual Basic）](tutorial-deferred-execution.md)中详细检查的处理模型。  
  
## <a name="example"></a>示例  
 本示例处理一个 WordprocessingML 文档，它确定元素节点、样式名称和每个段落的文本。 本示例以本教程中前面的一些示例为基础构建。 下面代码中的注释标识出了这个新查询。  
  
 有关创建此示例的源文档的说明，请参阅[创建源 Office OPEN XML 文档（Visual Basic）](creating-the-source-office-open-xml-document.md)。  
  
 本示例使用 WindowsBase 程序集中的类。 它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。  
  
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
  
 当应用于[创建源 Office OPEN XML 文档（Visual Basic）](creating-the-source-office-open-xml-document.md)中所述的文档时，此示例生成以下输出。  
  
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
  
## <a name="next-steps"></a>后续步骤  
 下面的示例演示如何使用扩展方法而不是 <xref:System.Linq.Enumerable.Aggregate%2A> 将多个字符串串联为一个字符串。  
  
- [使用扩展方法重构（Visual Basic）](refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>另请参阅

- [教程：在 WordprocessingML 文档中操作内容（Visual Basic）](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [LINQ to XML （Visual Basic）中的延迟执行和迟缓计算](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
