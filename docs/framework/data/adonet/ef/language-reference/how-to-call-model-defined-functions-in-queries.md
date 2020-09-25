---
title: 如何：在查询中调用模型定义的函数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: b142ef820e964eaf5f1afed53a6b12a9344c7dda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189326"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="9b3e4-102">如何：在查询中调用模型定义的函数</span><span class="sxs-lookup"><span data-stu-id="9b3e4-102">How to: Call Model-Defined Functions in Queries</span></span>

<span data-ttu-id="9b3e4-103">本主题介绍如何从 LINQ to Entities 查询中调用在概念模型中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-103">This topic describes how to call functions that are defined in the conceptual model from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="9b3e4-104">下面的过程提供了从 LINQ to Entities 查询中调用模型定义函数的高级大纲。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-104">The procedure below provides a high-level outline for calling a model-defined function from within a LINQ to Entities query.</span></span> <span data-ttu-id="9b3e4-105">后面的示例提供了有关该过程中各个步骤的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="9b3e4-106">这些过程假定您在概念模型中定义了一个函数。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="9b3e4-107">有关详细信息，请参阅 [如何：在概念模型中定义自定义函数](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="9b3e4-108">调用在概念模型中定义的函数</span><span class="sxs-lookup"><span data-stu-id="9b3e4-108">To call a function defined in the conceptual model</span></span>  
  
1. <span data-ttu-id="9b3e4-109">向应用程序中添加一个公共语言运行时 (CLR) 方法，该方法将映射到概念模型中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="9b3e4-110">若要映射方法，必须将 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 应用于此方法。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="9b3e4-111">请注意，此特性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 参数分别是概念模型的命名空间名称和概念模型中的函数名称。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="9b3e4-112">LINQ 的函数名称解析区分大小写。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2. <span data-ttu-id="9b3e4-113">在 LINQ to Entities 查询中调用该函数。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-113">Call the function in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b3e4-114">示例</span><span class="sxs-lookup"><span data-stu-id="9b3e4-114">Example</span></span>  

 <span data-ttu-id="9b3e4-115">下面的示例演示如何从 LINQ to Entities 查询中调用在概念模型中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a LINQ to Entities query.</span></span> <span data-ttu-id="9b3e4-116">本示例使用 School 模型。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-116">The example uses the School model.</span></span> <span data-ttu-id="9b3e4-117">有关 School 模型的信息，请参阅 [创建 School 示例数据库](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) 和 [生成 school .edmx 文件](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-117">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="9b3e4-118">以下概念模型函数返回教师已聘用的年数。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="9b3e4-119">有关向概念模型添加函数的信息，请参阅 [如何：在概念模型中定义自定义函数](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))。 ) </span><span class="sxs-lookup"><span data-stu-id="9b3e4-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="9b3e4-120">示例</span><span class="sxs-lookup"><span data-stu-id="9b3e4-120">Example</span></span>  

 <span data-ttu-id="9b3e4-121">接下来，向应用程序添加以下方法，并使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 将其映射到概念模型函数：</span><span class="sxs-lookup"><span data-stu-id="9b3e4-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="9b3e4-122">示例</span><span class="sxs-lookup"><span data-stu-id="9b3e4-122">Example</span></span>  

 <span data-ttu-id="9b3e4-123">现在，可以从 LINQ to Entities 查询中调用概念模型函数。</span><span class="sxs-lookup"><span data-stu-id="9b3e4-123">Now you can call the conceptual model function from within a LINQ to Entities query.</span></span> <span data-ttu-id="9b3e4-124">下面的代码调用该方法以显示十年前雇佣的所有教师：</span><span class="sxs-lookup"><span data-stu-id="9b3e4-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9b3e4-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b3e4-125">See also</span></span>

- <span data-ttu-id="9b3e4-126">[.edmx 文件概述](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9b3e4-126">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="9b3e4-127">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="9b3e4-127">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="9b3e4-128">在 LINQ to Entities 查询中调用函数</span><span class="sxs-lookup"><span data-stu-id="9b3e4-128">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="9b3e4-129">如何：调用模型定义的函数作为对象方法</span><span class="sxs-lookup"><span data-stu-id="9b3e4-129">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)
