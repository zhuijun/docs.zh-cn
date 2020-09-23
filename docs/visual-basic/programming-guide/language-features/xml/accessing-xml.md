---
title: 访问 XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 8ffe6d5ed368aee6d6984ec6ab28c8832921a3f8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080174"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="49dfd-102">在 Visual Basic 中访问 XML</span><span class="sxs-lookup"><span data-stu-id="49dfd-102">Accessing XML in Visual Basic</span></span>

<span data-ttu-id="49dfd-103">Visual Basic 提供了用于访问和导航结构的 XML 轴属性 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="49dfd-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="49dfd-104">这些属性使用特殊语法，使你能够通过指定 XML 名称访问元素和属性。</span><span class="sxs-lookup"><span data-stu-id="49dfd-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="49dfd-105">下表列出了可用于访问 Visual Basic 中的 XML 元素和属性的语言功能。</span><span class="sxs-lookup"><span data-stu-id="49dfd-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="49dfd-106">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="49dfd-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="49dfd-107">属性说明</span><span class="sxs-lookup"><span data-stu-id="49dfd-107">Property description</span></span>|<span data-ttu-id="49dfd-108">示例</span><span class="sxs-lookup"><span data-stu-id="49dfd-108">Example</span></span>|<span data-ttu-id="49dfd-109">描述</span><span class="sxs-lookup"><span data-stu-id="49dfd-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="49dfd-110">*child 轴*</span><span class="sxs-lookup"><span data-stu-id="49dfd-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="49dfd-111">获取 `phone` 作为元素的子元素的所有元素 `contact` 。</span><span class="sxs-lookup"><span data-stu-id="49dfd-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="49dfd-112">*属性轴*</span><span class="sxs-lookup"><span data-stu-id="49dfd-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="49dfd-113">获取 `type` 元素的所有属性 `phone` 。</span><span class="sxs-lookup"><span data-stu-id="49dfd-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="49dfd-114">*descendant 轴*</span><span class="sxs-lookup"><span data-stu-id="49dfd-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="49dfd-115">获取元素的所有 `name` 元素 `contacts` ，而不考虑它们在层次结构中出现的深度。</span><span class="sxs-lookup"><span data-stu-id="49dfd-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="49dfd-116">*扩展索引器*</span><span class="sxs-lookup"><span data-stu-id="49dfd-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="49dfd-117">获取序列中的第一个 `name` 元素。</span><span class="sxs-lookup"><span data-stu-id="49dfd-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="49dfd-118">*value*</span><span class="sxs-lookup"><span data-stu-id="49dfd-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="49dfd-119">获取序列中第一个对象的字符串表示形式; `Nothing` 如果序列为空，则为。</span><span class="sxs-lookup"><span data-stu-id="49dfd-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="49dfd-120">本节内容</span><span class="sxs-lookup"><span data-stu-id="49dfd-120">In This Section</span></span>  

 [<span data-ttu-id="49dfd-121">如何：访问 XML 子代元素</span><span class="sxs-lookup"><span data-stu-id="49dfd-121">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="49dfd-122">演示如何使用子代轴属性访问具有指定名称并包含在指定的 XML 元素下的所有 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="49dfd-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="49dfd-123">如何：访问 XML 子元素</span><span class="sxs-lookup"><span data-stu-id="49dfd-123">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="49dfd-124">演示如何使用子轴属性访问 XML 元素中具有指定名称的所有 XML 子元素。</span><span class="sxs-lookup"><span data-stu-id="49dfd-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="49dfd-125">如何：访问 XML 属性</span><span class="sxs-lookup"><span data-stu-id="49dfd-125">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="49dfd-126">演示如何使用属性轴属性访问 XML 元素中具有指定名称的所有 XML 属性。</span><span class="sxs-lookup"><span data-stu-id="49dfd-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="49dfd-127">如何：声明和使用 XML 命名空间前缀</span><span class="sxs-lookup"><span data-stu-id="49dfd-127">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="49dfd-128">演示如何声明 XML 命名空间前缀并使用它来创建和访问 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="49dfd-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="49dfd-129">相关章节</span><span class="sxs-lookup"><span data-stu-id="49dfd-129">Related Sections</span></span>  

 [<span data-ttu-id="49dfd-130">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="49dfd-130">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="49dfd-131">提供一些链接，这些链接指向描述各种 XML 访问属性的部分。</span><span class="sxs-lookup"><span data-stu-id="49dfd-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="49dfd-132">Visual Basic 中的 LINQ to XML 概述</span><span class="sxs-lookup"><span data-stu-id="49dfd-132">Overview of LINQ to XML in Visual Basic</span></span>](overview-of-linq-to-xml.md)  
 <span data-ttu-id="49dfd-133">介绍如何 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 在 Visual Basic 中使用。</span><span class="sxs-lookup"><span data-stu-id="49dfd-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="49dfd-134">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="49dfd-134">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="49dfd-135">介绍如何使用 Visual Basic 中的 XML 文本。</span><span class="sxs-lookup"><span data-stu-id="49dfd-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="49dfd-136">在 Visual Basic 中操作 XML</span><span class="sxs-lookup"><span data-stu-id="49dfd-136">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="49dfd-137">提供一些链接，这些链接指向有关在 Visual Basic 中加载和修改 XML 的部分。</span><span class="sxs-lookup"><span data-stu-id="49dfd-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="49dfd-138">XML</span><span class="sxs-lookup"><span data-stu-id="49dfd-138">XML</span></span>](index.md)  
 <span data-ttu-id="49dfd-139">提供一些链接，这些链接指向介绍如何 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 在 Visual Basic 中使用的部分。</span><span class="sxs-lookup"><span data-stu-id="49dfd-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
