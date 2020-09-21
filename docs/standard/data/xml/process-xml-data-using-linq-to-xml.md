---
title: 使用 LINQ to XML 处理 XML 数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
ms.openlocfilehash: 5afa9fc84b7f41023eceb5c0734b0667dc55514e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556494"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="c8127-102">使用 LINQ to XML 处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="c8127-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="c8127-103">LINQ to XML 是 .NET Framework 3.5 版中用于处理 XML 数据的新模型。</span><span class="sxs-lookup"><span data-stu-id="c8127-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="c8127-104">LINQ to XML 允许开发人员对 XML 数据执行任何需要的操作：查询、修改、创建、保存，和序列化 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="c8127-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="c8127-105">真正的优势在于查询和创建功能。</span><span class="sxs-lookup"><span data-stu-id="c8127-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="c8127-106">LINQ to XML 中的查询简洁而易于表示，与 XPath 或 XQuery 相比，使用的语法更类似于 SQL。</span><span class="sxs-lookup"><span data-stu-id="c8127-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="c8127-107">由于查询结果可作为为元素或属性的集合而返回，并且可用作 XElement 对象的参数，因此可以容易地将 XML 树从一种形状转换为另一种形状。</span><span class="sxs-lookup"><span data-stu-id="c8127-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="c8127-108">LINQ to XML 利用 .NET Framework 3.5 版中的语言集成查询 (LINQ) 技术。</span><span class="sxs-lookup"><span data-stu-id="c8127-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="c8127-109">LINQ 扩展了 C# 和 Visual Basic 的语言语法，提供可以扩展到几乎任何数据存储区的强大的查询功能。</span><span class="sxs-lookup"><span data-stu-id="c8127-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="c8127-110">有关其用法的详细讨论，请参阅 [LINQ to XML (C#)](../../linq/linq-xml-overview.md) 和 [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c8127-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span> <span data-ttu-id="c8127-111">有关 LINQ 框架的概述，请参阅[语言集成查询 (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) 或[语言集成查询 (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c8127-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8127-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="c8127-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="c8127-113">LINQ to XML 与DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="c8127-113">LINQ to XML vs. DOM (C#)</span></span>](../../linq/linq-xml-vs-dom.md)
- [<span data-ttu-id="c8127-114">LINQ to XML 与DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8127-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../linq/linq-xml-vs-dom.md)
- [<span data-ttu-id="c8127-115">LINQ to XML 与其他 XML 技术 (C#)</span><span class="sxs-lookup"><span data-stu-id="c8127-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../linq/linq-xml-vs-xml-technologies.md)
- [<span data-ttu-id="c8127-116">LINQ to XML 与其他 XML 技术 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8127-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../linq/linq-xml-vs-xml-technologies.md)
