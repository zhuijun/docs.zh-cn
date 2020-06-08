---
title: 保存和写出文档
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
ms.openlocfilehash: 40d031c06f0b76668a634fac46b8defccce62f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289039"
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="7a3b2-102">保存和写出文档</span><span class="sxs-lookup"><span data-stu-id="7a3b2-102">Saving and Writing a Document</span></span>
<span data-ttu-id="7a3b2-103">加载并保存 <xref:System.Xml.XmlDocument> 后，保存的文档在下列方面可能不同于原始文档：</span><span class="sxs-lookup"><span data-stu-id="7a3b2-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
- <span data-ttu-id="7a3b2-104">如果在调用 <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> 方法之间将 `true` 属性设置为 <xref:System.Xml.XmlDocument.Save%2A>，文档中的空白在输出中将保留；如果此属性为 `false`，<xref:System.Xml.XmlDocument> 将使输出自动缩进。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
- <span data-ttu-id="7a3b2-105">各个属性之间的所有空白都缩减为一个空白字符。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
- <span data-ttu-id="7a3b2-106">更改元素间的空白。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-106">The white space between elements is changed.</span></span> <span data-ttu-id="7a3b2-107">保留有效空白，但不保留无效空白。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="7a3b2-108">不过，在文档保存后，它默认使用 <xref:System.Xml.XmlTextWriter> 缩进  模式简洁打印输出，以提升文档的可读性。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
- <span data-ttu-id="7a3b2-109">属性值两边所用的引号字符在默认情况下更改为双引号。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="7a3b2-110">可以使用 <xref:System.Xml.XmlTextReader.QuoteChar%2A> 的 <xref:System.Xml.XmlTextWriter> 属性将引号字符设置为双引号或单引号。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
- <span data-ttu-id="7a3b2-111">默认情况下，扩展像 `{` 这样的数字字符实体。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
- <span data-ttu-id="7a3b2-112">不保留输入文档中的字节顺序标记。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="7a3b2-113">除非显式创建指定不同编码的 XML 声明，否则 UCS-2 保存为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
- <span data-ttu-id="7a3b2-114">如果要将 <xref:System.Xml.XmlDocument> 写出到文件或流中，则写出的输出与文档内容相同。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="7a3b2-115">也就是说，仅当文档中包含 <xref:System.Xml.XmlDeclaration> 时才写出 ，并且写出文档时所使用的编码与声明节点中给定的编码相同。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="7a3b2-116">写出 XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="7a3b2-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="7a3b2-117"><xref:System.Xml.XmlDocument>、<xref:System.Xml.XmlDeclaration> 和 <xref:System.Xml.XmlNode.OuterXml%2A> 的 <xref:System.Xml.XmlNode.InnerXml%2A> 和 <xref:System.Xml.XmlNode.WriteTo%2A> 成员与 <xref:System.Xml.XmlDocument> 和 <xref:System.Xml.XmlDocument.Save%2A> 的 <xref:System.Xml.XmlDocument.WriteContentTo%2A> 方法共同创建 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="7a3b2-118">对于 <xref:System.Xml.XmlDocument> 的 <xref:System.Xml.XmlNode.OuterXml%2A> 属性、<xref:System.Xml.XmlDocument.InnerXml%2A> 以及 <xref:System.Xml.XmlDocument.Save%2A>、<xref:System.Xml.XmlDocument.WriteTo%2A> 和 <xref:System.Xml.XmlDocument.WriteContentTo%2A> 方法，在 XML 声明中写出的编码从 <xref:System.Xml.XmlDeclaration> 节点获取。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="7a3b2-119">如果没有 <xref:System.Xml.XmlDeclaration> 节点，则不会写出 <xref:System.Xml.XmlDeclaration>。如果 <xref:System.Xml.XmlDeclaration> 节点中没有编码，则不会在 XML 声明中写出编码。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="7a3b2-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> 和 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> 方法始终写出 <xref:System.Xml.XmlDeclaration>。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="7a3b2-121">这些方法从其写入的编写器中获取编码。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="7a3b2-122">也就是说，编写器的编码值重写文档和 <xref:System.Xml.XmlDeclaration> 对象的编码。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="7a3b2-123">例如，下列代码不在输出文件 `out.xml` 中的 XML 声明中写出编码。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="7a3b2-124">对于 <xref:System.Xml.XmlDocument.Save%2A> 方法，XML 声明使用 <xref:System.Xml.XmlWriter.WriteStartDocument%2A> 类中的 <xref:System.Xml.XmlWriter> 方法写出。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="7a3b2-125">因此，重写 <xref:System.Xml.XmlWriter.WriteStartDocument%2A> 方法将更改如何编写文档的开头。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="7a3b2-126">对于 <xref:System.Xml.XmlNode.OuterXml%2A>、<xref:System.Xml.XmlDeclaration.WriteTo%2A> 和 <xref:System.Xml.XmlNode.InnerXml%2A> 的 <xref:System.Xml.XmlDeclaration> 成员，如果未设置 <xref:System.Xml.XmlDeclaration.Encoding%2A> 属性，则不会写出任何编码。否则，在 XML 声明中写出的编码与 <xref:System.Xml.XmlDeclaration.Encoding%2A> 属性中的编码相同。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="7a3b2-127">用 OuterXml 属性写出文档内容</span><span class="sxs-lookup"><span data-stu-id="7a3b2-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="7a3b2-128"><xref:System.Xml.XmlNode.OuterXml%2A> 属性是 Microsoft 对万维网联合会 (W3C) XML 文档对象模型 (DOM) 标准的扩展。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="7a3b2-129"><xref:System.Xml.XmlNode.OuterXml%2A> 属性用于获取整个 XML 文档的标记，或者只获取单个节点及其子节点的标记。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="7a3b2-130"><xref:System.Xml.XmlNode.OuterXml%2A> 返回表示给定节点及其所有子节点的标记。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="7a3b2-131">下面的代码示例显示了如何将整个文档保存为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="7a3b2-132">下面的代码示例显示了如何只保存文档元素。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="7a3b2-133">与此相反，如果您需要子节点的内容，可以使用 <xref:System.Xml.XmlNode.InnerText%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="7a3b2-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3b2-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="7a3b2-134">See also</span></span>

- [<span data-ttu-id="7a3b2-135">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="7a3b2-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
