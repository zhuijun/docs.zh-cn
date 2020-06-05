---
title: 使用 XML 声明进行序列化
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: cd303a800efe42d3fa99d601f25d54320570bed3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411788"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="ce611-102">使用 XML 声明进行序列化（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ce611-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="ce611-103">本主题说明如何控制序列化是否生成 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="ce611-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="ce611-104">XML 声明的生成</span><span class="sxs-lookup"><span data-stu-id="ce611-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="ce611-105">使用 <xref:System.IO.File> 方法或 <xref:System.IO.TextWriter> 方法序列化为 <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> 将生成 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="ce611-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="ce611-106">在序列化为 <xref:System.Xml.XmlWriter> 时，编写器设置（在 <xref:System.Xml.XmlWriterSettings> 对象中指定）将确定是否生成 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="ce611-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="ce611-107">如果要使用 `ToString` 方法序列化为字符串，则生成的 XML 不会包括 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="ce611-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="ce611-108">使用 XML 声明进行序列化</span><span class="sxs-lookup"><span data-stu-id="ce611-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="ce611-109">下面的示例创建一个 <xref:System.Xml.Linq.XElement>，将文档保存到文件，然后将文件打印到控制台：</span><span class="sxs-lookup"><span data-stu-id="ce611-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="ce611-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="ce611-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="ce611-111">不带 XML 声明的序列化</span><span class="sxs-lookup"><span data-stu-id="ce611-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="ce611-112">下面的示例演示如何将一个 <xref:System.Xml.Linq.XElement> 保存到一个 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="ce611-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="ce611-113">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="ce611-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce611-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce611-114">See also</span></span>

- [<span data-ttu-id="ce611-115">序列化 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ce611-115">Serializing XML Trees (Visual Basic)</span></span>](serializing-xml-trees.md)
