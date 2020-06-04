---
title: 如何：从 XmlReader 创建树
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 25c15ff08563b12b26041a536dfbca1c9cce260a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414603"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="52511-102">如何：从 XmlReader 创建树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="52511-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>

<span data-ttu-id="52511-103">本主题演示如何直接从 <xref:System.Xml.XmlReader> 创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="52511-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="52511-104">若要从 <xref:System.Xml.Linq.XElement> 创建 <xref:System.Xml.XmlReader>，必须将 <xref:System.Xml.XmlReader> 定位在元素节点上。</span><span class="sxs-lookup"><span data-stu-id="52511-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="52511-105"><xref:System.Xml.XmlReader> 将跳过注释和处理指令，但如果 <xref:System.Xml.XmlReader> 定位在文本节点上，则将引发错误。</span><span class="sxs-lookup"><span data-stu-id="52511-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="52511-106">若要避免这类错误，请在从 <xref:System.Xml.XmlReader> 创建 XML 树之前，始终将 <xref:System.Xml.XmlReader> 定位在元素上。</span><span class="sxs-lookup"><span data-stu-id="52511-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example"></a><span data-ttu-id="52511-107">示例</span><span class="sxs-lookup"><span data-stu-id="52511-107">Example</span></span>

<span data-ttu-id="52511-108">本示例使用以下 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="52511-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span></span>

<span data-ttu-id="52511-109">下面的代码创建一个 `T:System.Xml.XmlReader` 对象，然后读取节点，直到找到第一个元素节点。</span><span class="sxs-lookup"><span data-stu-id="52511-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="52511-110">然后加载 <xref:System.Xml.Linq.XElement> 对象。</span><span class="sxs-lookup"><span data-stu-id="52511-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="52511-111">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="52511-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="52511-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52511-112">See also</span></span>

- [<span data-ttu-id="52511-113">分析 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="52511-113">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)
