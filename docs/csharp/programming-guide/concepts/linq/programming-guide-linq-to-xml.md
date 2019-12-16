---
title: "编程指南 (LINQ to XML) (C#)"
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
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ed4b0aff72654b9ac0928fae933e34268aede7fe
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="programming-guide-linq-to-xml-c"></a><span data-ttu-id="8b265-102">编程指南 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-102">Programming Guide (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8b265-103">本节提供有关使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 进行编程的概念性和指导性信息。</span><span class="sxs-lookup"><span data-stu-id="8b265-103">This section provides conceptual and how-to information about programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
## <a name="who-should-read-this-documentation"></a><span data-ttu-id="8b265-104">本文档的目标读者</span><span class="sxs-lookup"><span data-stu-id="8b265-104">Who Should Read This Documentation</span></span>  
 <span data-ttu-id="8b265-105">本文档面向已经了解 C# 以及 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 的一些基本知识的开发人员。</span><span class="sxs-lookup"><span data-stu-id="8b265-105">This documentation targets developers who already understand C# and some basic aspects of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="8b265-106">本文档的目的在于降低各类开发人员对 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的使用难度。</span><span class="sxs-lookup"><span data-stu-id="8b265-106">The goal of this documentation is to make [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] easy to use for all kinds of developers.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="8b265-107"> 使 XML 编程变得更容易。</span><span class="sxs-lookup"><span data-stu-id="8b265-107"> makes XML programming easier.</span></span> <span data-ttu-id="8b265-108">您无需成为一名专家级开发人员就可以使用它。</span><span class="sxs-lookup"><span data-stu-id="8b265-108">You do not have to be an expert developer to use it.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="8b265-109"> 非常依赖于泛型类。</span><span class="sxs-lookup"><span data-stu-id="8b265-109"> relies heavily on generic classes.</span></span> <span data-ttu-id="8b265-110">因此，了解泛型类的使用非常重要。</span><span class="sxs-lookup"><span data-stu-id="8b265-110">Therefore, is very important that you understand the use of generic classes.</span></span> <span data-ttu-id="8b265-111">此外，熟悉作为参数化类型声明的委托也很有帮助。</span><span class="sxs-lookup"><span data-stu-id="8b265-111">Further, it is helpful if you are familiar with delegates that are declared as parameterized types.</span></span> <span data-ttu-id="8b265-112">如果不熟悉 C# 泛型类，请参阅[泛型类](../../../../csharp/programming-guide/generics/generic-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="8b265-112">If you are not familiar with C# generic classes, see [Generic Classes](../../../../csharp/programming-guide/generics/generic-classes.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b265-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="8b265-113">In This Section</span></span>  
  
|<span data-ttu-id="8b265-114">主题</span><span class="sxs-lookup"><span data-stu-id="8b265-114">Topic</span></span>|<span data-ttu-id="8b265-115">描述</span><span class="sxs-lookup"><span data-stu-id="8b265-115">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8b265-116">LINQ to XML 编程概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-116">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|<span data-ttu-id="8b265-117">提供对 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 类的概述以及有关以下三个最重要类的详细信息：<xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="8b265-117">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, and detailed information about three of the most important classes: <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, and <xref:System.Xml.Linq.XDocument>.</span></span>|  
|[<span data-ttu-id="8b265-118">创建 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-118">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|<span data-ttu-id="8b265-119">提供有关创建 XML 树的概念性和基于任务的信息。</span><span class="sxs-lookup"><span data-stu-id="8b265-119">Provides conceptual and task-based information about creating XML trees.</span></span> <span data-ttu-id="8b265-120">可以通过使用函数构造，或通过从字符串或文件解析 XML 文本来创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="8b265-120">You can create XML trees by using functional construction, or by parsing XML text from a string or a file.</span></span> <span data-ttu-id="8b265-121">也可以使用 <xref:System.Xml.XmlReader> 来填充 XML 树。</span><span class="sxs-lookup"><span data-stu-id="8b265-121">You can also use an <xref:System.Xml.XmlReader> to populate an XML tree.</span></span>|  
|[<span data-ttu-id="8b265-122">使用 XML 命名空间 (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-122">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|<span data-ttu-id="8b265-123">提供有关创建使用命名空间的 XML 树的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8b265-123">Provides detailed information about creating XML trees that use namespaces.</span></span>|  
|[<span data-ttu-id="8b265-124">序列化 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-124">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|<span data-ttu-id="8b265-125">描述序列化 XML 树的多种方法，并给出选择使用方法的指导。</span><span class="sxs-lookup"><span data-stu-id="8b265-125">Describes multiple approaches to serializing an XML tree, and gives guidance on which approach to use.</span></span>|  
|[<span data-ttu-id="8b265-126">LINQ to XML 轴 (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-126">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|<span data-ttu-id="8b265-127">列举并介绍 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 轴方法，您必须了解轴方法才能编写 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="8b265-127">Enumerates and describes the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis methods, which you must understand before you can write [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>|  
|[<span data-ttu-id="8b265-128">查询 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-128">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|<span data-ttu-id="8b265-129">提供查询 XML 树的常见示例。</span><span class="sxs-lookup"><span data-stu-id="8b265-129">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="8b265-130">修改 XML 树 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-130">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|<span data-ttu-id="8b265-131">如同文档对象模型 (DOM) 一样，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 也允许您就地修改 XML 树。</span><span class="sxs-lookup"><span data-stu-id="8b265-131">Like the Document Object Model (DOM), [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enables you to modify an XML tree in place.</span></span>|  
|[<span data-ttu-id="8b265-132">高级 LINQ to XML 编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|<span data-ttu-id="8b265-133">提供有关批注、事件、流处理和其他高级方案的信息。</span><span class="sxs-lookup"><span data-stu-id="8b265-133">Provides information about annotations, events, streaming, and other advanced scenarios.</span></span>|  
|[<span data-ttu-id="8b265-134">LINQ to XML 安全性 (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-134">LINQ to XML Security (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|<span data-ttu-id="8b265-135">描述与 LINQ to XML 相关的安全问题并提供减小安全隐患的一些指导。</span><span class="sxs-lookup"><span data-stu-id="8b265-135">Describes security issues associated with LINQ to XML and provides some guidance for mitigating security exposure.</span></span>|  
|[<span data-ttu-id="8b265-136">示例 XML 文档 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8b265-136">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|<span data-ttu-id="8b265-137">包含本文档中许多示例使用的示例 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="8b265-137">Contains the sample XML documents that are used by many examples in this documentation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b265-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="8b265-138">See Also</span></span>  
 <span data-ttu-id="8b265-139">[入门 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="8b265-139">[Getting Started (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md) </span></span>  
 [<span data-ttu-id="8b265-140">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8b265-140">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
