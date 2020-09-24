---
title: 在 LINQ to Entities 查询中调用函数
description: 使用这些文章可以查看 EntityFunctions 和 SqlFunctions 类如何作为实体框架的一部分，提供对规范和数据库函数的访问权限。
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 8c771c93e0c3ed82f3ad550613dd855fd06b6f48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177483"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="6d14b-103">在 LINQ to Entities 查询中调用函数</span><span class="sxs-lookup"><span data-stu-id="6d14b-103">Calling Functions in LINQ to Entities Queries</span></span>

<span data-ttu-id="6d14b-104">本节中的主题说明如何调用 LINQ to Entities 查询中的函数。</span><span class="sxs-lookup"><span data-stu-id="6d14b-104">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="6d14b-105"><xref:System.Data.Objects.EntityFunctions> 和 <xref:System.Data.Objects.SqlClient.SqlFunctions> 类提供了对作为实体框架的一部分的规范函数和数据库函数的访问功能。</span><span class="sxs-lookup"><span data-stu-id="6d14b-105">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="6d14b-106">有关详细信息，请参阅 [如何：调用规范函数](how-to-call-canonical-functions.md) 和 [如何：调用数据库函数](how-to-call-database-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="6d14b-106">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="6d14b-107">调用自定义函数的过程需要三个基本步骤：</span><span class="sxs-lookup"><span data-stu-id="6d14b-107">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="6d14b-108">在概念模型中定义函数或在存储模型中声明函数。</span><span class="sxs-lookup"><span data-stu-id="6d14b-108">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="6d14b-109">将方法添加到应用程序并将其映射到具有 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 的模型中的函数。</span><span class="sxs-lookup"><span data-stu-id="6d14b-109">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="6d14b-110">在 LINQ to Entities 查询中调用该函数。</span><span class="sxs-lookup"><span data-stu-id="6d14b-110">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="6d14b-111">有关更多信息，请参见本节中的各主题。</span><span class="sxs-lookup"><span data-stu-id="6d14b-111">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d14b-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="6d14b-112">In This Section</span></span>  

 [<span data-ttu-id="6d14b-113">如何：调用规范函数</span><span class="sxs-lookup"><span data-stu-id="6d14b-113">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="6d14b-114">如何：调用数据库函数</span><span class="sxs-lookup"><span data-stu-id="6d14b-114">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="6d14b-115">如何：调用自定义数据库函数</span><span class="sxs-lookup"><span data-stu-id="6d14b-115">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="6d14b-116">如何：在查询中调用模型定义的函数</span><span class="sxs-lookup"><span data-stu-id="6d14b-116">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="6d14b-117">如何：调用模型定义的函数作为对象方法</span><span class="sxs-lookup"><span data-stu-id="6d14b-117">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="6d14b-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="6d14b-118">See also</span></span>

- [<span data-ttu-id="6d14b-119">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="6d14b-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="6d14b-120">规范函数</span><span class="sxs-lookup"><span data-stu-id="6d14b-120">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="6d14b-121">[.edmx 文件概述](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6d14b-121">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="6d14b-122">[如何：在概念模型中定义自定义函数](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6d14b-122">[How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
