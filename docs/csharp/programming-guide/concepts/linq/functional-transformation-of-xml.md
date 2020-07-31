---
title: XML 的功能转换 (C#)
description: 了解如何使用 C# 中的纯函数转换方法修改 XML 文档，以及该方法与过程方法有何不同。
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: 4ccc6859f3663eb3760c7faeaf115a5e88a2278a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103673"
---
# <a name="functional-transformation-of-xml-c"></a><span data-ttu-id="0a4f9-103">XML 的功能转换 (C#)</span><span class="sxs-lookup"><span data-stu-id="0a4f9-103">Functional Transformation of XML (C#)</span></span>
<span data-ttu-id="0a4f9-104">本主题讨论用于修改 XML 文档的纯函数转换方法，并将该方法与过程方法进行比较。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-104">This topic discusses the pure functional transformation approach to modifying XML documents, and contrasts it with a procedural approach.</span></span>  
  
## <a name="modifying-an-xml-document"></a><span data-ttu-id="0a4f9-105">修改 XML 文档</span><span class="sxs-lookup"><span data-stu-id="0a4f9-105">Modifying an XML Document</span></span>  
 <span data-ttu-id="0a4f9-106">对 XML 程序员来说，最常见的任务之一就是将 XML 从一种形状转换为另一种形状。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-106">One of the most common tasks for an XML programmer is transforming XML from one shape to another.</span></span> <span data-ttu-id="0a4f9-107">XML 文档的形状就是文档的结构，包括下列内容：</span><span class="sxs-lookup"><span data-stu-id="0a4f9-107">The shape of an XML document is the structure of the document, which includes the following:</span></span>  
  
- <span data-ttu-id="0a4f9-108">文档所表达的层次结构。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-108">The hierarchy expressed by the document.</span></span>  
  
- <span data-ttu-id="0a4f9-109">元素和属性的名称。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-109">The element and attribute names.</span></span>  
  
- <span data-ttu-id="0a4f9-110">元素和属性的数据类型。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-110">The data types of the elements and attributes.</span></span>  
  
 <span data-ttu-id="0a4f9-111">通常，将 XML 从一种形状转换为另一种形状的最有效方法是纯函数转换方法。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-111">In general, the most effective approach to transforming XML from one shape to another is that of pure functional transformation.</span></span> <span data-ttu-id="0a4f9-112">在这种方法中，程序员的主要任务是创建一个转换，该转换将应用到整个 XML 文档（或应用到一个或多个严格定义的节点）。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-112">In this approach, the primary programmer task is to create a transformation which is applied to the entire XML document (or to one or more strictly defined nodes).</span></span> <span data-ttu-id="0a4f9-113">可以说，函数转换最容易进行编码（如果程序员熟悉这种方法），生成的代码最容易维护，并且相比其他方法通常更加简洁。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-113">Functional transformation is arguably the easiest to code (after a programmer is familiar with the approach), yields the most maintainable code, and is often more compact than alternative approaches.</span></span>  
  
### <a name="xml-functional-transformational-technologies"></a><span data-ttu-id="0a4f9-114">XML 函数转换技术</span><span class="sxs-lookup"><span data-stu-id="0a4f9-114">XML Functional Transformational Technologies</span></span>  
 <span data-ttu-id="0a4f9-115">Microsoft 提供两种用于 XML 文档的功能转换技术：XSLT 和 LINQ to XML。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-115">Microsoft offers two functional transformation technologies for use on XML documents: XSLT and LINQ to XML.</span></span> <span data-ttu-id="0a4f9-116">在 <xref:System.Xml.Xsl> 托管命名空间和 MSXML 的本机 COM 实现中都支持 XSLT。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-116">XSLT is supported in the <xref:System.Xml.Xsl> managed namespace and in the native COM implementation of MSXML.</span></span> <span data-ttu-id="0a4f9-117">尽管 XSLT 是操作 XML 文档的可靠技术，但它要求专门领域的专业知识，即 XSLT 语言和支持它的 API。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-117">Although XSLT is a robust technology for manipulating XML documents, it requires expertise in a specialized domain, namely the XSLT language and its supporting APIs.</span></span>  
  
 <span data-ttu-id="0a4f9-118">LINQ to XML 提供了必要的工具，使用这些工具可以在 C# 或 Visual Basic 代码中以富于表现力而又强有力的方式编写纯函数转换。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-118">LINQ to XML provides the tools necessary to code pure functional transformations in an expressive and powerful way, within C# or Visual Basic code.</span></span> <span data-ttu-id="0a4f9-119">例如，LINQ to XML 文档中的很多示例都使用纯函数方法。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-119">For example, many of the examples in the LINQ to XML documentation use a pure functional approach.</span></span> <span data-ttu-id="0a4f9-120">此外，在[教程：在 WordprocessingML 文档中处理内容 (C#)](./shape-of-wordprocessingml-documents.md) 教程中，我们在函数方法中使用 LINQ to XML 处理 Microsoft Word 文档中的信息。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-120">Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.</span></span>  
  
 <span data-ttu-id="0a4f9-121">有关 LINQ to XML 与其他 Microsoft XML 技术的更全面比较，请参见 [LINQ to XML 和其他 XML 技术](./linq-to-xml-vs-other-xml-technologies.md)。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-121">For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. Other XML Technologies](./linq-to-xml-vs-other-xml-technologies.md).</span></span>  
  
<span data-ttu-id="0a4f9-122">如果源文档具有不规则的结构，则推荐使用 XSLT 工具进行以文档为中心的转换。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-122">XSLT is the recommended tool for  document-centric transformations when the source document has an irregular structure.</span></span> <span data-ttu-id="0a4f9-123">但是 LINQ to XML 也可以执行以文档为中心的转换。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-123">However, LINQ to XML can also perform document-centric transforms.</span></span> <span data-ttu-id="0a4f9-124">有关详细信息，请参阅[如何使用批注以 XSLT 样式转换 LINQ to XML 树 (C#)](./how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md)。</span><span class="sxs-lookup"><span data-stu-id="0a4f9-124">For more information, see [How to use annotations to transform LINQ to XML trees in an XSLT style (C#)](./how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0a4f9-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="0a4f9-125">See also</span></span>

- [<span data-ttu-id="0a4f9-126">纯函数转换简介 (C#)</span><span class="sxs-lookup"><span data-stu-id="0a4f9-126">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="0a4f9-127">教程：操作 WordprocessingML 文档中的内容 (C#)</span><span class="sxs-lookup"><span data-stu-id="0a4f9-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="0a4f9-128">LINQ to XML 与其他 XML 技术</span><span class="sxs-lookup"><span data-stu-id="0a4f9-128">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
