---
title: "教程：操作 WordprocessingML 文档中的内容 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bc9815f8-13d2-4f50-a4d1-b1c0d50d37b3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 293e8de848f83517211e3f3ed640102a2c534764
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-c"></a><span data-ttu-id="6d03f-102">教程：操作 WordprocessingML 文档中的内容 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-102">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>
<span data-ttu-id="6d03f-103">本教程演示如何应用函数转换方法和 LINQ to XML 来操作 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="6d03f-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="6d03f-104">C# 示例查询和操作用 Microsoft Word 保存的 Office Open XML WordprocessingML 文档中的信息。</span><span class="sxs-lookup"><span data-stu-id="6d03f-104">The C# examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="6d03f-105">有关详细信息，请参阅 [OpenXML 开发人员](http://go.microsoft.com/fwlink/?LinkID=95573)网站。</span><span class="sxs-lookup"><span data-stu-id="6d03f-105">For more information, see the [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) Web site.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d03f-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="6d03f-106">In This Section</span></span>  
  
|<span data-ttu-id="6d03f-107">主题</span><span class="sxs-lookup"><span data-stu-id="6d03f-107">Topic</span></span>|<span data-ttu-id="6d03f-108">描述</span><span class="sxs-lookup"><span data-stu-id="6d03f-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6d03f-109">WordprocessingML 文档的形状 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-109">Shape of WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="6d03f-110">提供有关 WordprocessingML 文档详细信息的简要说明。</span><span class="sxs-lookup"><span data-stu-id="6d03f-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="6d03f-111">创建源 Office Open XML 文档 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-111">Creating the Source Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="6d03f-112">为创建用于本教程中的查询的源文档提供分步说明。</span><span class="sxs-lookup"><span data-stu-id="6d03f-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="6d03f-113">查找默认段落样式 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-113">Finding the Default Paragraph Style (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="6d03f-114">演示用于查找文档默认样式名称的查询。</span><span class="sxs-lookup"><span data-stu-id="6d03f-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="6d03f-115">检索段落及其样式 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-115">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="6d03f-116">演示用于检索文档段落集合的查询。</span><span class="sxs-lookup"><span data-stu-id="6d03f-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="6d03f-117">检索段落的文本 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-117">Retrieving the Text of the Paragraphs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="6d03f-118">补充前一个查询以检索每个段落的文本。</span><span class="sxs-lookup"><span data-stu-id="6d03f-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="6d03f-119">使用扩展方法重构 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-119">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="6d03f-120">通过使用扩展方法进行重构来简化代码。</span><span class="sxs-lookup"><span data-stu-id="6d03f-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="6d03f-121">使用纯函数重构 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-121">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="6d03f-122">通过使用纯函数进行重构来进一步简化代码。</span><span class="sxs-lookup"><span data-stu-id="6d03f-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="6d03f-123">对不同形状的 XML 进行投影 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-123">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="6d03f-124">通过将 XML 投影为不同于原始文档的形状来完成 XML 转换。</span><span class="sxs-lookup"><span data-stu-id="6d03f-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="6d03f-125">查找 Word 文档中的文本 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-125">Finding Text in Word Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="6d03f-126">使用前面的查询在文档中查找指定的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="6d03f-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="6d03f-127">Office Open XML WordprocessingML 文档的详细信息 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-127">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="6d03f-128">提供 Office Open XML WordprocessingML 文档的一些详细信息。</span><span class="sxs-lookup"><span data-stu-id="6d03f-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d03f-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="6d03f-129">See Also</span></span>  
 <span data-ttu-id="6d03f-130">[XML 的纯功能转换 (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="6d03f-130">[Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span></span>  
 [<span data-ttu-id="6d03f-131">纯函数转换简介 (C#)</span><span class="sxs-lookup"><span data-stu-id="6d03f-131">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
