---
title: LINQ to SQL
description: LINQ to SQL 是 .NET Framework 的一个组件，它提供用于将关系数据作为对象进行管理的运行时基础结构。
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 13502bfee3ee24764d190dace1512bc958343973
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286309"
---
# <a name="linq-to-sql"></a><span data-ttu-id="0b82f-103">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0b82f-103">LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0b82f-104">是 .NET Framework 版本3.5 的一个组件，它提供用于将关系数据作为对象管理的运行时基础结构。</span><span class="sxs-lookup"><span data-stu-id="0b82f-104">is a component of .NET Framework version 3.5 that provides a run-time infrastructure for managing relational data as objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b82f-105">关系数据显示为由二维表（关系\*\* 或平面文件\*\*）组成的集合，其中公共列将表互相关联起来。</span><span class="sxs-lookup"><span data-stu-id="0b82f-105">Relational data appears as a collection of two-dimensional tables (*relations* or *flat files*), where common columns relate tables to each other.</span></span> <span data-ttu-id="0b82f-106">若要有效地使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您必须略为熟悉关系数据库的基本原理。</span><span class="sxs-lookup"><span data-stu-id="0b82f-106">To use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] effectively, you must have some familiarity with the underlying principles of relational databases.</span></span>  
  
 <span data-ttu-id="0b82f-107">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，关系数据库的数据模型映射到用开发人员所用的编程语言表示的对象模型。</span><span class="sxs-lookup"><span data-stu-id="0b82f-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="0b82f-108">当应用程序运行时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会将对象模型中的语言集成查询转换为 SQL，然后将它们发送到数据库进行执行。</span><span class="sxs-lookup"><span data-stu-id="0b82f-108">When the application runs, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates into SQL the language-integrated queries in the object model and sends them to the database for execution.</span></span> <span data-ttu-id="0b82f-109">当数据库返回结果时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会将它们转换回您可以用您自己的编程语言处理的对象。</span><span class="sxs-lookup"><span data-stu-id="0b82f-109">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates them back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="0b82f-110">使用 Visual Studio 的开发人员通常使用对象关系设计器，后者提供了一个用于实现的许多功能的用户界面 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0b82f-110">Developers using Visual Studio typically use the Object Relational Designer, which provides a user interface for implementing many of the features of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="0b82f-111">此版本的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 附带的文档介绍了生成 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 应用程序所需的基本构造块、流程和技术。</span><span class="sxs-lookup"><span data-stu-id="0b82f-111">The documentation that is included with this release of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] describes the basic building blocks, processes, and techniques you need for building [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="0b82f-112">你还可以在 Microsoft Docs 中搜索特定问题，并且可以参与[LINQ 论坛](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)，其中你可以与专家详细讨论更复杂的主题。</span><span class="sxs-lookup"><span data-stu-id="0b82f-112">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="0b82f-113">最后， [LINQ to SQL：用于关系数据的 .Net 语言集成查询](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10))白皮书详细信息 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技术，已完成 Visual Basic 和 c # 代码示例。</span><span class="sxs-lookup"><span data-stu-id="0b82f-113">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b82f-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="0b82f-114">In This Section</span></span>  
 [<span data-ttu-id="0b82f-115">入门</span><span class="sxs-lookup"><span data-stu-id="0b82f-115">Getting Started</span></span>](getting-started.md)  
 <span data-ttu-id="0b82f-116">提供对 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的简要概述以及有关如何开始使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的信息。</span><span class="sxs-lookup"><span data-stu-id="0b82f-116">Provides a condensed overview of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] along with information about how to get started using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="0b82f-117">编程指南</span><span class="sxs-lookup"><span data-stu-id="0b82f-117">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="0b82f-118">提供映射、查询、更新、调试及类似任务的步骤。</span><span class="sxs-lookup"><span data-stu-id="0b82f-118">Provides steps for mapping, querying, updating, debugging, and similar tasks.</span></span>  
  
 [<span data-ttu-id="0b82f-119">引用</span><span class="sxs-lookup"><span data-stu-id="0b82f-119">Reference</span></span>](reference.md)  
 <span data-ttu-id="0b82f-120">提供有关 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的多个方面的参考信息。</span><span class="sxs-lookup"><span data-stu-id="0b82f-120">Provides reference information about several aspects of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="0b82f-121">相关主题包括“SQL-CLR 类型映射”、“标准查询运算符转换”等。</span><span class="sxs-lookup"><span data-stu-id="0b82f-121">Topics include SQL-CLR Type Mapping, Standard Query Operator Translation, and more.</span></span>  
  
 [<span data-ttu-id="0b82f-122">示例</span><span class="sxs-lookup"><span data-stu-id="0b82f-122">Samples</span></span>](samples.md)  
 <span data-ttu-id="0b82f-123">提供指向 Visual Basic 和 c # 示例的链接。</span><span class="sxs-lookup"><span data-stu-id="0b82f-123">Provides links to Visual Basic and C# samples.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0b82f-124">相关章节</span><span class="sxs-lookup"><span data-stu-id="0b82f-124">Related Sections</span></span>  
 <span data-ttu-id="0b82f-125">[语言集成查询（LINQ）-C#](../../../../../csharp/programming-guide/concepts/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="0b82f-125">[Language-Integrated Query (LINQ) - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)</span></span>\
 <span data-ttu-id="0b82f-126">概述 c # 中的 LINQ 技术。</span><span class="sxs-lookup"><span data-stu-id="0b82f-126">Provides overviews of LINQ technologies in C#.</span></span>

 [<span data-ttu-id="0b82f-127">语言集成查询 (LINQ) - Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b82f-127">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="0b82f-128">提供 Visual Basic 中 LINQ 技术的概述。</span><span class="sxs-lookup"><span data-stu-id="0b82f-128">Provides overviews of LINQ technologies in Visual Basic.</span></span>
  
 [<span data-ttu-id="0b82f-129">LINQ</span><span class="sxs-lookup"><span data-stu-id="0b82f-129">LINQ</span></span>](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 <span data-ttu-id="0b82f-130">介绍 Visual Basic 用户的 LINQ 技术。</span><span class="sxs-lookup"><span data-stu-id="0b82f-130">Describes LINQ technologies for Visual Basic users.</span></span>  
  
 [<span data-ttu-id="0b82f-131">LINQ 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0b82f-131">LINQ and ADO.NET</span></span>](../../linq-and-ado-net.md)  
 <span data-ttu-id="0b82f-132">指向 ADO.NET 门户的链接。</span><span class="sxs-lookup"><span data-stu-id="0b82f-132">Links to the ADO.NET portal.</span></span>  
  
 <span data-ttu-id="0b82f-133">[LINQ to SQL 演练](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0b82f-133">[LINQ to SQL Walkthroughs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))</span></span>  
 <span data-ttu-id="0b82f-134">列出可用于 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的演练。</span><span class="sxs-lookup"><span data-stu-id="0b82f-134">Lists walkthroughs available for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="0b82f-135">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="0b82f-135">Downloading Sample Databases</span></span>](downloading-sample-databases.md)  
 <span data-ttu-id="0b82f-136">介绍如何下载文档中使用的示例数据库。</span><span class="sxs-lookup"><span data-stu-id="0b82f-136">Describes how to download sample databases used in the documentation.</span></span>  
  
 <span data-ttu-id="0b82f-137">[LinqDataSource Web 服务器控件概述](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0b82f-137">[LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))</span></span>  
 <span data-ttu-id="0b82f-138">描述控件如何 <xref:System.Web.UI.WebControls.LinqDataSource> 通过 ASP.NET 数据源控件体系结构将语言集成查询（LINQ）公开给 Web 开发人员。</span><span class="sxs-lookup"><span data-stu-id="0b82f-138">Describes how the <xref:System.Web.UI.WebControls.LinqDataSource> control exposes Language-Integrated Query (LINQ) to Web developers through the ASP.NET data-source control architecture.</span></span>
