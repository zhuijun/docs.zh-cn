---
title: 教程：操作 WordprocessingML 文档中的内容
ms.date: 07/20/2015
ms.assetid: f8028ba8-2dd1-4425-930c-8cc23176ebbc
ms.openlocfilehash: 9fd5fd5092a74ad8124a691d7d3bb479fa5dcdde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396267"
---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-visual-basic"></a><span data-ttu-id="918c3-102">教程：在 WordprocessingML 文档中操作内容（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-102">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>
<span data-ttu-id="918c3-103">本教程演示如何应用函数转换方法和 LINQ to XML 来操作 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="918c3-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="918c3-104">Visual Basic 示例查询并操作 Microsoft Word 保存的 Office Open XML WordprocessingML 文档中的信息。</span><span class="sxs-lookup"><span data-stu-id="918c3-104">The Visual Basic examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="918c3-105">有关详细信息，请参阅[Eric 白的博客](http://www.ericwhite.com)。</span><span class="sxs-lookup"><span data-stu-id="918c3-105">For more information, see the [Eric White's Blog](http://www.ericwhite.com).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="918c3-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="918c3-106">In This Section</span></span>  
  
|<span data-ttu-id="918c3-107">主题</span><span class="sxs-lookup"><span data-stu-id="918c3-107">Topic</span></span>|<span data-ttu-id="918c3-108">说明</span><span class="sxs-lookup"><span data-stu-id="918c3-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="918c3-109">WordprocessingML 文档的形状（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-109">Shape of WordprocessingML Documents (Visual Basic)</span></span>](shape-of-wordprocessingml-documents.md)|<span data-ttu-id="918c3-110">提供有关 WordprocessingML 文档详细信息的简要说明。</span><span class="sxs-lookup"><span data-stu-id="918c3-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="918c3-111">创建源 Office Open XML 文档（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-111">Creating the Source Office Open XML Document (Visual Basic)</span></span>](creating-the-source-office-open-xml-document.md)|<span data-ttu-id="918c3-112">为创建用于本教程中的查询的源文档提供分步说明。</span><span class="sxs-lookup"><span data-stu-id="918c3-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="918c3-113">查找默认段落样式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-113">Finding the Default Paragraph Style (Visual Basic)</span></span>](finding-the-default-paragraph-style.md)|<span data-ttu-id="918c3-114">演示用于查找文档默认样式名称的查询。</span><span class="sxs-lookup"><span data-stu-id="918c3-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="918c3-115">检索段落及其样式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-115">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="918c3-116">演示用于检索文档段落集合的查询。</span><span class="sxs-lookup"><span data-stu-id="918c3-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="918c3-117">检索段落的文本（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-117">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>](retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="918c3-118">补充前一个查询以检索每个段落的文本。</span><span class="sxs-lookup"><span data-stu-id="918c3-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="918c3-119">使用扩展方法重构（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-119">Refactoring Using an Extension Method (Visual Basic)</span></span>](refactoring-using-an-extension-method.md)|<span data-ttu-id="918c3-120">通过使用扩展方法进行重构来简化代码。</span><span class="sxs-lookup"><span data-stu-id="918c3-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="918c3-121">使用纯函数重构 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918c3-121">Refactoring Using a Pure Function (Visual Basic)</span></span>](refactoring-using-a-pure-function.md)|<span data-ttu-id="918c3-122">通过使用纯函数进行重构来进一步简化代码。</span><span class="sxs-lookup"><span data-stu-id="918c3-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="918c3-123">在不同形状中投影 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-123">Projecting XML in a Different Shape (Visual Basic)</span></span>](projecting-xml-in-a-different-shape.md)|<span data-ttu-id="918c3-124">通过将 XML 投影为不同于原始文档的形状来完成 XML 转换。</span><span class="sxs-lookup"><span data-stu-id="918c3-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="918c3-125">查找 Word 文档中的文本（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-125">Finding Text in Word Documents (Visual Basic)</span></span>](finding-text-in-word-documents.md)|<span data-ttu-id="918c3-126">使用前面的查询在文档中查找指定的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="918c3-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="918c3-127">Office Open XML WordprocessingML 文档的详细信息（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-127">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="918c3-128">提供 Office Open XML WordprocessingML 文档的一些详细信息。</span><span class="sxs-lookup"><span data-stu-id="918c3-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="918c3-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="918c3-129">See also</span></span>

- [<span data-ttu-id="918c3-130">XML 的纯功能转换（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-130">Pure Functional Transformations of XML (Visual Basic)</span></span>](pure-functional-transformations-of-xml.md)
- [<span data-ttu-id="918c3-131">纯功能转换简介（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="918c3-131">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)
