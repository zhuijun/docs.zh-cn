---
title: 将 XML 文档读入 DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 02338d72f51d3a7507c0dfa030383399b9e213f6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282397"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="4f2a6-102">将 XML 文档读入 DOM</span><span class="sxs-lookup"><span data-stu-id="4f2a6-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="4f2a6-103">XML 信息从不同的格式读入内存。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="4f2a6-104">读取源包括字符串、流、URL、文本读取器或 <xref:System.Xml.XmlReader> 的派生类。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="4f2a6-105"><xref:System.Xml.XmlDocument.Load%2A> 方法将文档置入内存中并包含可用于从每个不同的格式中获取数据的重载方法。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="4f2a6-106">还存在 <xref:System.Xml.XmlDocument.LoadXml%2A> 方法，该方法从字符串中读取 XML。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="4f2a6-107">不同的 <xref:System.Xml.XmlDocument.Load%2A> 方法影响在加载 XML 文档对象模型 (DOM) 时创建的节点。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="4f2a6-108">下表列出了一些 <xref:System.Xml.XmlDocument.Load%2A> 方法的区别以及讲述这些区别的主题。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="4f2a6-109">Subject</span><span class="sxs-lookup"><span data-stu-id="4f2a6-109">Subject</span></span>|<span data-ttu-id="4f2a6-110">主题</span><span class="sxs-lookup"><span data-stu-id="4f2a6-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="4f2a6-111">创建空白节点</span><span class="sxs-lookup"><span data-stu-id="4f2a6-111">Creation of white space nodes</span></span>|<span data-ttu-id="4f2a6-112">用来加载 DOM 的对象对 DOM 中生成的空白和有效空白节点有影响。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="4f2a6-113">有关详细信息，请参阅[加载 DOM 时处理空格和有效空格](white-space-and-significant-white-space-handling-when-loading-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="4f2a6-114">从特定节点开始加载 XML 或加载整个 XML 文档</span><span class="sxs-lookup"><span data-stu-id="4f2a6-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="4f2a6-115">使用 <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> 方法，可以将数据从特定节点加载到 DOM 中。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="4f2a6-116">有关详细信息，请参阅[从读取器加载数据](load-data-from-a-reader.md)。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-116">For more information, see [Load Data from a Reader](load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="4f2a6-117">在 XML 加载时进行验证</span><span class="sxs-lookup"><span data-stu-id="4f2a6-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="4f2a6-118">加载到 DOM 中的 XML 数据可以在加载时进行验证。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="4f2a6-119">使用验证 <xref:System.Xml.XmlReader> 可以完成此操作。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="4f2a6-120">若要详细了解如何在加载 XML 时验证它，请参阅[在 DOM 中验证 XML 文档](validating-an-xml-document-in-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="4f2a6-121">以下示例显示使用 <xref:System.Xml.XmlDocument.LoadXml%2A> 方法加载的 XML 以及之后保存到称为 `data.xml` 的文本文件的数据。</span><span class="sxs-lookup"><span data-stu-id="4f2a6-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f2a6-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="4f2a6-122">See also</span></span>

- [<span data-ttu-id="4f2a6-123">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="4f2a6-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
