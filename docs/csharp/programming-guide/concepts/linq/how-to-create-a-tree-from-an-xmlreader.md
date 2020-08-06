---
title: 如何从 XmlReader 创建树 (C#)
description: 了解如何从 XmlReader 直接创建 XML 树。 查看演示如何创建 T:System.Xml.XmlReader 对象的示例。
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 3801177e664d142652d38748d44eaf3f274239dd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302654"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="06afc-104">如何从 XmlReader 创建树 (C#)</span><span class="sxs-lookup"><span data-stu-id="06afc-104">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="06afc-105">本主题演示如何直接从 <xref:System.Xml.XmlReader> 创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="06afc-105">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="06afc-106">若要从 <xref:System.Xml.Linq.XElement> 创建 <xref:System.Xml.XmlReader>，必须将 <xref:System.Xml.XmlReader> 定位在元素节点上。</span><span class="sxs-lookup"><span data-stu-id="06afc-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="06afc-107"><xref:System.Xml.XmlReader> 将跳过注释和处理指令，但如果 <xref:System.Xml.XmlReader> 定位在文本节点上，则将引发错误。</span><span class="sxs-lookup"><span data-stu-id="06afc-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="06afc-108">若要避免这类错误，请在从 <xref:System.Xml.XmlReader> 创建 XML 树之前，始终将 <xref:System.Xml.XmlReader> 定位在元素上。</span><span class="sxs-lookup"><span data-stu-id="06afc-108">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06afc-109">示例</span><span class="sxs-lookup"><span data-stu-id="06afc-109">Example</span></span>  
 <span data-ttu-id="06afc-110">本示例使用下面的 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="06afc-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="06afc-111">下面的代码创建一个 `T:System.Xml.XmlReader` 对象，然后读取节点，直到找到第一个元素节点。</span><span class="sxs-lookup"><span data-stu-id="06afc-111">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="06afc-112">然后加载 <xref:System.Xml.Linq.XElement> 对象。</span><span class="sxs-lookup"><span data-stu-id="06afc-112">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="06afc-113">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="06afc-113">This example produces the following output:</span></span>  
  
```xml  
<Catalog>  
   <Book id="bk101">  
      <Author>Garghentini, Davide</Author>  
      <Title>XML Developer's Guide</Title>  
      <Genre>Computer</Genre>  
      <Price>44.95</Price>  
      <PublishDate>2000-10-01</PublishDate>  
      <Description>An in-depth look at creating applications
      with XML.</Description>  
   </Book>  
   <Book id="bk102">  
      <Author>Garcia, Debra</Author>  
      <Title>Midnight Rain</Title>  
      <Genre>Fantasy</Genre>  
      <Price>5.95</Price>  
      <PublishDate>2000-12-16</PublishDate>  
      <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>  
   </Book>  
</Catalog>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06afc-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="06afc-114">See also</span></span>

- [<span data-ttu-id="06afc-115">分析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="06afc-115">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
