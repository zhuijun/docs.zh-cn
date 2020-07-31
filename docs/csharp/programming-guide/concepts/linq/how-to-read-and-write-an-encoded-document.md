---
title: 如何读取和写入编码的文档 (C#)
description: 了解如何通过向 XML 树中添加 XDeclaration 并将编码设置为所需的代码页名称，来使用 C# 创建编码的 XML 文档。
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: ed02b7467f4de71455da516a6c894070337684e7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104317"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="f49f8-103">如何读取和写入编码的文档 (C#)</span><span class="sxs-lookup"><span data-stu-id="f49f8-103">How to read and write an encoded document (C#)</span></span>
<span data-ttu-id="f49f8-104">若要创建编码的 XML 文档，请向 XML 树中添加一个 <xref:System.Xml.Linq.XDeclaration>，将编码设置为需要的代码页名称。</span><span class="sxs-lookup"><span data-stu-id="f49f8-104">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="f49f8-105">由 <xref:System.Text.Encoding.WebName%2A> 返回的任何值都是有效值。</span><span class="sxs-lookup"><span data-stu-id="f49f8-105">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="f49f8-106">如果您读取编码的文档，则要将 <xref:System.Xml.Linq.XDeclaration.Encoding%2A> 属性设置为该代码页名称。</span><span class="sxs-lookup"><span data-stu-id="f49f8-106">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="f49f8-107">如果将 <xref:System.Xml.Linq.XDeclaration.Encoding%2A> 设置为一个有效的代码页名称，则 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将用指定的编码进行序列化。</span><span class="sxs-lookup"><span data-stu-id="f49f8-107">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f49f8-108">示例</span><span class="sxs-lookup"><span data-stu-id="f49f8-108">Example</span></span>  
 <span data-ttu-id="f49f8-109">下面的示例创建两个文档，一个文档使用 utf-8 编码，另一个使用 utf-16 编码。</span><span class="sxs-lookup"><span data-stu-id="f49f8-109">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="f49f8-110">然后，该示例加载这两个文档并将编码输出到控制台。</span><span class="sxs-lookup"><span data-stu-id="f49f8-110">It then loads the documents and prints the encoding to the console.</span></span>  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 <span data-ttu-id="f49f8-111">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="f49f8-111">This example produces the following output:</span></span>  
  
```output  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a><span data-ttu-id="f49f8-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="f49f8-112">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
