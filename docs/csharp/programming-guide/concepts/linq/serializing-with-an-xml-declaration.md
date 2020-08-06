---
title: 带 XML 声明的序列化 (C#)
description: 了解 C# 格式的序列化生成 XML 声明的配置，其中包括序列化到文件、TextWriter 和 XmlWriter。
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 7e91b61f037d28149f7c2355f4233dc319b54627
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302355"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="63cee-103">带 XML 声明的序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="63cee-103">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="63cee-104">本主题说明如何控制序列化是否生成 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="63cee-104">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="63cee-105">XML 声明的生成</span><span class="sxs-lookup"><span data-stu-id="63cee-105">XML Declaration Generation</span></span>  
 <span data-ttu-id="63cee-106">使用 <xref:System.IO.File> 方法或 <xref:System.IO.TextWriter> 方法序列化为 <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> 将生成 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="63cee-106">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="63cee-107">在序列化为 <xref:System.Xml.XmlWriter> 时，编写器设置（在 <xref:System.Xml.XmlWriterSettings> 对象中指定）将确定是否生成 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="63cee-107">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="63cee-108">如果要使用 `ToString` 方法序列化为字符串，则生成的 XML 不会包括 XML 声明。</span><span class="sxs-lookup"><span data-stu-id="63cee-108">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="63cee-109">使用 XML 声明进行序列化</span><span class="sxs-lookup"><span data-stu-id="63cee-109">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="63cee-110">下面的示例创建一个 <xref:System.Xml.Linq.XElement>，将文档保存到文件，然后将文件打印到控制台：</span><span class="sxs-lookup"><span data-stu-id="63cee-110">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="63cee-111">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="63cee-111">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="63cee-112">不带 XML 声明的序列化</span><span class="sxs-lookup"><span data-stu-id="63cee-112">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="63cee-113">下面的示例演示如何将一个 <xref:System.Xml.Linq.XElement> 保存到一个 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="63cee-113">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 <span data-ttu-id="63cee-114">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="63cee-114">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63cee-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="63cee-115">See also</span></span>

- [<span data-ttu-id="63cee-116">序列化 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="63cee-116">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
