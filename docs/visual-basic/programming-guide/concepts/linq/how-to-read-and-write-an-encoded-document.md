---
title: 如何：读取和写入编码的文档
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: f66737429950e04f447dfbd58cf47b6434a22976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397903"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a><span data-ttu-id="f74a7-102">如何：读取和写入编码的文档（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f74a7-102">How to: Read and Write an Encoded Document (Visual Basic)</span></span>

<span data-ttu-id="f74a7-103">若要创建编码的 XML 文档，请向 XML 树中添加一个 <xref:System.Xml.Linq.XDeclaration>，将编码设置为需要的代码页名称。</span><span class="sxs-lookup"><span data-stu-id="f74a7-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>

<span data-ttu-id="f74a7-104">由 <xref:System.Text.Encoding.WebName%2A> 返回的任何值都是有效值。</span><span class="sxs-lookup"><span data-stu-id="f74a7-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>

<span data-ttu-id="f74a7-105">如果您读取编码的文档，则要将 <xref:System.Xml.Linq.XDeclaration.Encoding%2A> 属性设置为该代码页名称。</span><span class="sxs-lookup"><span data-stu-id="f74a7-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>

<span data-ttu-id="f74a7-106">如果将 <xref:System.Xml.Linq.XDeclaration.Encoding%2A> 设置为一个有效的代码页名称，则 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将用指定的编码进行序列化。</span><span class="sxs-lookup"><span data-stu-id="f74a7-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>

## <a name="example"></a><span data-ttu-id="f74a7-107">示例</span><span class="sxs-lookup"><span data-stu-id="f74a7-107">Example</span></span>

<span data-ttu-id="f74a7-108">下面的示例创建两个文档，一个文档使用 utf-8 编码，另一个使用 utf-16 编码。</span><span class="sxs-lookup"><span data-stu-id="f74a7-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="f74a7-109">然后，该示例加载这两个文档并将编码输出到控制台。</span><span class="sxs-lookup"><span data-stu-id="f74a7-109">It then loads the documents and prints the encoding to the console.</span></span>

```vb
Console.WriteLine("Creating a document with utf-8 encoding")
Dim encodedDoc8 As XDocument = _
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>
        <Root>Content</Root>

encodedDoc8.Save("EncodedUtf8.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)
Console.WriteLine()

Console.WriteLine("Creating a document with utf-16 encoding")
Dim encodedDoc16 As XDocument = _
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>
        <Root>Content</Root>

encodedDoc16.Save("EncodedUtf16.xml")
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)
Console.WriteLine()

Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)
Console.WriteLine()

Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")
Console.WriteLine("Encoded document:")
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))
Console.WriteLine()
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)
```

<span data-ttu-id="f74a7-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="f74a7-110">This example produces the following output:</span></span>

```console
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

## <a name="see-also"></a><span data-ttu-id="f74a7-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f74a7-111">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f74a7-112">高级 LINQ to XML 编程（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f74a7-112">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
