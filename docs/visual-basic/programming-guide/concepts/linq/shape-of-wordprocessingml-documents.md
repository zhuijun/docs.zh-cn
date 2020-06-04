---
title: WordprocessingML 文档的形状
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: eb4acef2caa731d17e8daf1955d50f0d2585c175
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406802"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="47d7e-102">WordprocessingML 文档的形状（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="47d7e-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="47d7e-103">本主题介绍 WordprocessingML 文档的 XML 形状。</span><span class="sxs-lookup"><span data-stu-id="47d7e-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="47d7e-104">Microsoft Office 格式</span><span class="sxs-lookup"><span data-stu-id="47d7e-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="47d7e-105">2007 Microsoft Office 系统的本机文件格式为 Office Open XML（通常称为 Open XML）。</span><span class="sxs-lookup"><span data-stu-id="47d7e-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="47d7e-106">Open XML 是一种基于 XML 的格式（Ecma 标准），当前即将通过 ISO-IEC 标准流程。</span><span class="sxs-lookup"><span data-stu-id="47d7e-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="47d7e-107">Open XML 中用于文字处理文件的标记语言称为 WordprocessingML。</span><span class="sxs-lookup"><span data-stu-id="47d7e-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="47d7e-108">本教程使用 WordprocessingML 源文件作为示例的输入。</span><span class="sxs-lookup"><span data-stu-id="47d7e-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="47d7e-109">如果使用 Microsoft Office 2003，则在已安装适用于 Word、Excel 和 PowerPoint 2007 文件格式的 Microsoft Office 兼容包的情况下，可以将文档保存为 Office Open XML 格式。</span><span class="sxs-lookup"><span data-stu-id="47d7e-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="47d7e-110">WordprocessingML 文档的形状</span><span class="sxs-lookup"><span data-stu-id="47d7e-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="47d7e-111">首先要了解的是 WordprocessingML 文档的形状。</span><span class="sxs-lookup"><span data-stu-id="47d7e-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="47d7e-112">WordprocessingML 文档包含一个正文元素（称为 `w:body`），该元素包含文档的各个段落。</span><span class="sxs-lookup"><span data-stu-id="47d7e-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="47d7e-113">每个段落包含一个或多个文本域（称为 `w:r`）。</span><span class="sxs-lookup"><span data-stu-id="47d7e-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="47d7e-114">每个文本域包含一个或多个文本块（称为 `w:t`）。</span><span class="sxs-lookup"><span data-stu-id="47d7e-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="47d7e-115">下面是一个非常简单的 WordprocessingML 文档：</span><span class="sxs-lookup"><span data-stu-id="47d7e-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="47d7e-116">此文档包含两个段落。</span><span class="sxs-lookup"><span data-stu-id="47d7e-116">This document contains two paragraphs.</span></span> <span data-ttu-id="47d7e-117">这两个段落都包含单个文本域，每个文本域都包含单个文本块。</span><span class="sxs-lookup"><span data-stu-id="47d7e-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="47d7e-118">查看 XML 格式的 WordprocessingML 文档内容的最简单方式是使用 Microsoft Word 创建一个 XML 文档，保存该文档，然后运行下面的程序，将该 XML 打印到控制台。</span><span class="sxs-lookup"><span data-stu-id="47d7e-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="47d7e-119">本示例使用 WindowsBase 程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="47d7e-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="47d7e-120">它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="47d7e-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="47d7e-121">外部资源</span><span class="sxs-lookup"><span data-stu-id="47d7e-121">External resources</span></span>

- <span data-ttu-id="47d7e-122">[介绍 Office (2007) Open XML 文件格式](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="47d7e-122">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>
- <span data-ttu-id="47d7e-123">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))（WordprocessingML 概述）</span><span class="sxs-lookup"><span data-stu-id="47d7e-123">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span></span>

## <a name="see-also"></a><span data-ttu-id="47d7e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47d7e-124">See also</span></span>

- [<span data-ttu-id="47d7e-125">教程：在 WordprocessingML 文档中操作内容（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="47d7e-125">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)
