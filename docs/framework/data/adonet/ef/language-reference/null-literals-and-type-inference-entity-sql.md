---
title: Null 文本和类型推理 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 5797c9f55b1a1c89cc27787af6f9ad7bfffc5767
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185062"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="2eb99-102">Null 文本和类型推理 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2eb99-102">Null Literals and Type Inference (Entity SQL)</span></span>

<span data-ttu-id="2eb99-103">Null 文本与 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 类型系统中的任何类型都兼容。</span><span class="sxs-lookup"><span data-stu-id="2eb99-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="2eb99-104">但是，为了正确进行 Null 文本类型推理，[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 对何处可以使用 Null 文本实施某些约束。</span><span class="sxs-lookup"><span data-stu-id="2eb99-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="2eb99-105">类型化 Null</span><span class="sxs-lookup"><span data-stu-id="2eb99-105">Typed Nulls</span></span>  

 <span data-ttu-id="2eb99-106">类型化 Null 可以在任意位置使用。</span><span class="sxs-lookup"><span data-stu-id="2eb99-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="2eb99-107">类型化 Null 是已知的，因此不需要类型推理。</span><span class="sxs-lookup"><span data-stu-id="2eb99-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="2eb99-108">例如，使用下面的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 构造可以构造 Int16 类型的 Null。</span><span class="sxs-lookup"><span data-stu-id="2eb99-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="2eb99-109">自由浮动 Null 文本</span><span class="sxs-lookup"><span data-stu-id="2eb99-109">Free-Floating Null Literals</span></span>  

 <span data-ttu-id="2eb99-110">自由浮动 Null 文本的用法如下：</span><span class="sxs-lookup"><span data-stu-id="2eb99-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
- <span data-ttu-id="2eb99-111">用作 CAST 或 TREAT 表达式的自变量。</span><span class="sxs-lookup"><span data-stu-id="2eb99-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="2eb99-112">建议用这种方式生成类型化 Null 表达式。</span><span class="sxs-lookup"><span data-stu-id="2eb99-112">This is the recommended way to produce a typed null expression.</span></span>  
  
- <span data-ttu-id="2eb99-113">用作方法或函数的参数。</span><span class="sxs-lookup"><span data-stu-id="2eb99-113">As an argument to a method or a function.</span></span> <span data-ttu-id="2eb99-114">标准重载规则适用。</span><span class="sxs-lookup"><span data-stu-id="2eb99-114">Standard overload rules apply.</span></span>  
  
- <span data-ttu-id="2eb99-115">用作算术表达式（例如 +、- 或 /）的一个参数。</span><span class="sxs-lookup"><span data-stu-id="2eb99-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="2eb99-116">其他自变量不能为 Null 文本，否则不能进行类型推理。</span><span class="sxs-lookup"><span data-stu-id="2eb99-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
- <span data-ttu-id="2eb99-117">用作逻辑表达式（AND、OR 或 NOT）的任何自变量。</span><span class="sxs-lookup"><span data-stu-id="2eb99-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="2eb99-118">所有自变量都已知为类型 Boolean。</span><span class="sxs-lookup"><span data-stu-id="2eb99-118">All the arguments are known to be of type Boolean.</span></span>  
  
- <span data-ttu-id="2eb99-119">用作 IS NULL 或 IS NOT NULL 表达式的参数。</span><span class="sxs-lookup"><span data-stu-id="2eb99-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
- <span data-ttu-id="2eb99-120">用作 LIKE 表达式的一个或多个自变量。</span><span class="sxs-lookup"><span data-stu-id="2eb99-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="2eb99-121">所有参数都应为字符串。</span><span class="sxs-lookup"><span data-stu-id="2eb99-121">All arguments are expected to be strings.</span></span>  
  
- <span data-ttu-id="2eb99-122">用作命名类型构造函数的一个或多个自变量。</span><span class="sxs-lookup"><span data-stu-id="2eb99-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
- <span data-ttu-id="2eb99-123">用作多集构造函数的一个或多个自变量。</span><span class="sxs-lookup"><span data-stu-id="2eb99-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="2eb99-124">多集构造函数至少有一个自变量必须为非 Null 文本的表达式。</span><span class="sxs-lookup"><span data-stu-id="2eb99-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
- <span data-ttu-id="2eb99-125">用作 CASE 表达式中的一个或多个 THEN 或 ELSE 表达式。</span><span class="sxs-lookup"><span data-stu-id="2eb99-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="2eb99-126">CASE 表达式中至少有一个 THEN 或 ELSE 表达式必须为非 Null 文本的表达式。</span><span class="sxs-lookup"><span data-stu-id="2eb99-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="2eb99-127">其他情况下不能使用自由浮动 Null 文本。</span><span class="sxs-lookup"><span data-stu-id="2eb99-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="2eb99-128">例如，它们不能用作行构造函数的自变量。</span><span class="sxs-lookup"><span data-stu-id="2eb99-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb99-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="2eb99-129">See also</span></span>

- [<span data-ttu-id="2eb99-130">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="2eb99-130">Entity SQL Overview</span></span>](entity-sql-overview.md)
