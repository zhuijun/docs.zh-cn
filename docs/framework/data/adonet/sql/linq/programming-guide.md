---
title: 编程指南
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 50c4370e23faf8400eb23f1e8c0cc74cd4dce80e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203561"
---
# <a name="programming-guide"></a><span data-ttu-id="73136-102">编程指南</span><span class="sxs-lookup"><span data-stu-id="73136-102">Programming Guide</span></span>

<span data-ttu-id="73136-103">本节包含有关如何创建和使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 对象模型的信息。</span><span class="sxs-lookup"><span data-stu-id="73136-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="73136-104">如果你使用的是 Visual Studio，还可以使用对象关系设计器来执行其中许多相同的任务。</span><span class="sxs-lookup"><span data-stu-id="73136-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="73136-105">你还可以在 Microsoft Docs 中搜索特定问题，并且可以参与 [LINQ 论坛](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)，其中你可以与专家详细讨论更复杂的主题。</span><span class="sxs-lookup"><span data-stu-id="73136-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="73136-106">最后， [LINQ to SQL：用于关系数据的 .Net 语言集成查询](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) 白皮书详细信息 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技术，已完成 Visual Basic 和 c # 代码示例。</span><span class="sxs-lookup"><span data-stu-id="73136-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73136-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="73136-107">In This Section</span></span>  

 [<span data-ttu-id="73136-108">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="73136-108">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="73136-109">说明如何生成对象模型。</span><span class="sxs-lookup"><span data-stu-id="73136-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="73136-110">与数据库通信</span><span class="sxs-lookup"><span data-stu-id="73136-110">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="73136-111">说明如何将 <xref:System.Data.Linq.DataContext> 对象用作与数据库交互的媒介。</span><span class="sxs-lookup"><span data-stu-id="73136-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="73136-112">查询数据库</span><span class="sxs-lookup"><span data-stu-id="73136-112">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="73136-113">说明如何在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中执行查询，并提供了许多示例。</span><span class="sxs-lookup"><span data-stu-id="73136-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="73136-114">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="73136-114">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="73136-115">说明如何更改数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="73136-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="73136-116">调试支持</span><span class="sxs-lookup"><span data-stu-id="73136-116">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="73136-117">说明可用于调试 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 项目的支持。</span><span class="sxs-lookup"><span data-stu-id="73136-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="73136-118">背景信息</span><span class="sxs-lookup"><span data-stu-id="73136-118">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="73136-119">包括针对更高级用户的附加项，如并发冲突解决方法、创建新数据库等。</span><span class="sxs-lookup"><span data-stu-id="73136-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="73136-120">相关章节</span><span class="sxs-lookup"><span data-stu-id="73136-120">Related Sections</span></span>  

 [<span data-ttu-id="73136-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="73136-121">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="73136-122">提供指向一些主题的链接，这些主题阐释了 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技术并演示了一些功能。</span><span class="sxs-lookup"><span data-stu-id="73136-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="73136-123">存储过程</span><span class="sxs-lookup"><span data-stu-id="73136-123">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="73136-124">包含指向一些主题的链接，这些主题演示了如何使用存储过程。</span><span class="sxs-lookup"><span data-stu-id="73136-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="73136-125">LINQ 简介 (C#)</span><span class="sxs-lookup"><span data-stu-id="73136-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="73136-126">提供可帮助您开始了解使用 c # LINQ to SQL 的资源。</span><span class="sxs-lookup"><span data-stu-id="73136-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="73136-127">LINQ 简介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73136-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="73136-128">提供有助于您开始了解使用 Visual Basic LINQ to SQL 的资源。</span><span class="sxs-lookup"><span data-stu-id="73136-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
