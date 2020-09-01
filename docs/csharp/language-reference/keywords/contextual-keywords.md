---
description: 上下文关键字 - C# 参考
title: 上下文关键字 - C# 参考
ms.date: 03/07/2017
helpviewer_keywords:
- contextual keywords [C#]
ms.assetid: 7c76bc29-a754-4389-b0ab-f6b441018298
ms.openlocfilehash: ccd9bcfe2702083573cef979b40ff4d7167e8041
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128396"
---
# <a name="contextual-keywords-c-reference"></a><span data-ttu-id="955d1-103">上下文关键字（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="955d1-103">Contextual Keywords (C# Reference)</span></span>

<span data-ttu-id="955d1-104">上下文关键字用于在代码中提供特定含义，但它不是 C# 中的保留字。</span><span class="sxs-lookup"><span data-stu-id="955d1-104">A contextual keyword is used to provide a specific meaning in the code, but it is not a reserved word in C#.</span></span> <span data-ttu-id="955d1-105">本部分介绍下面这些上下文关键字：</span><span class="sxs-lookup"><span data-stu-id="955d1-105">The following contextual keywords are introduced in this section:</span></span>  
  
|<span data-ttu-id="955d1-106">关键字</span><span class="sxs-lookup"><span data-stu-id="955d1-106">Keyword</span></span>|<span data-ttu-id="955d1-107">说明</span><span class="sxs-lookup"><span data-stu-id="955d1-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="955d1-108">add</span><span class="sxs-lookup"><span data-stu-id="955d1-108">add</span></span>](./add.md)|<span data-ttu-id="955d1-109">定义一个自定义事件访问器，客户端代码订阅事件时会调用该访问器。</span><span class="sxs-lookup"><span data-stu-id="955d1-109">Defines a custom event accessor that is invoked when client code subscribes to the event.</span></span>|  
|[<span data-ttu-id="955d1-110">async</span><span class="sxs-lookup"><span data-stu-id="955d1-110">async</span></span>](./async.md)|<span data-ttu-id="955d1-111">指示修改后的方法、lambda 表达式或匿名方法是异步的。</span><span class="sxs-lookup"><span data-stu-id="955d1-111">Indicates that the modified method, lambda expression, or anonymous method is asynchronous.</span></span>|  
|[<span data-ttu-id="955d1-112">await</span><span class="sxs-lookup"><span data-stu-id="955d1-112">await</span></span>](../operators/await.md)|<span data-ttu-id="955d1-113">挂起异步方法，直到等待的任务完成。</span><span class="sxs-lookup"><span data-stu-id="955d1-113">Suspends an async method until an awaited task is completed.</span></span>|  
|[<span data-ttu-id="955d1-114">dynamic</span><span class="sxs-lookup"><span data-stu-id="955d1-114">dynamic</span></span>](../builtin-types/reference-types.md)|<span data-ttu-id="955d1-115">定义一个引用类型，实现发生绕过编译时类型检查的操作。</span><span class="sxs-lookup"><span data-stu-id="955d1-115">Defines a reference type that enables operations in which it occurs to bypass compile-time type checking.</span></span>|  
|[<span data-ttu-id="955d1-116">get</span><span class="sxs-lookup"><span data-stu-id="955d1-116">get</span></span>](./get.md)|<span data-ttu-id="955d1-117">为属性或索引器定义访问器方法。</span><span class="sxs-lookup"><span data-stu-id="955d1-117">Defines an accessor method for a property or an indexer.</span></span>|  
|[<span data-ttu-id="955d1-118">global</span><span class="sxs-lookup"><span data-stu-id="955d1-118">global</span></span>](../operators/namespace-alias-qualifier.md)|<span data-ttu-id="955d1-119">未以其他方式命名的全局命名空间的别名。</span><span class="sxs-lookup"><span data-stu-id="955d1-119">Alias of the global namespace, which is otherwise unnamed.</span></span>|  
|[<span data-ttu-id="955d1-120">partial</span><span class="sxs-lookup"><span data-stu-id="955d1-120">partial</span></span>](./partial-type.md)|<span data-ttu-id="955d1-121">在整个同一编译单元内定义分部类、结构和接口。</span><span class="sxs-lookup"><span data-stu-id="955d1-121">Defines partial classes, structs, and interfaces throughout the same compilation unit.</span></span>|  
|[<span data-ttu-id="955d1-122">remove</span><span class="sxs-lookup"><span data-stu-id="955d1-122">remove</span></span>](./remove.md)|<span data-ttu-id="955d1-123">定义一个自定义事件访问器，客户端代码取消订阅事件时会调用该访问器。</span><span class="sxs-lookup"><span data-stu-id="955d1-123">Defines a custom event accessor that is invoked when client code unsubscribes from the event.</span></span>|  
|[<span data-ttu-id="955d1-124">set</span><span class="sxs-lookup"><span data-stu-id="955d1-124">set</span></span>](./set.md)|<span data-ttu-id="955d1-125">为属性或索引器定义访问器方法。</span><span class="sxs-lookup"><span data-stu-id="955d1-125">Defines an accessor method for a property or an indexer.</span></span>|  
|[<span data-ttu-id="955d1-126">value</span><span class="sxs-lookup"><span data-stu-id="955d1-126">value</span></span>](./value.md)|<span data-ttu-id="955d1-127">用于设置访问器和添加或删除事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="955d1-127">Used to set accessors and to add or remove event handlers.</span></span>|  
|[<span data-ttu-id="955d1-128">var</span><span class="sxs-lookup"><span data-stu-id="955d1-128">var</span></span>](./var.md)|<span data-ttu-id="955d1-129">使编译器能够确定在方法作用域中声明的变量类型。</span><span class="sxs-lookup"><span data-stu-id="955d1-129">Enables the type of a variable declared at method scope to be determined by the compiler.</span></span>|  
|[<span data-ttu-id="955d1-130">when</span><span class="sxs-lookup"><span data-stu-id="955d1-130">when</span></span>](when.md)|<span data-ttu-id="955d1-131">指定 `catch` 块的筛选条件或 `switch` 语句的 `case` 标签。</span><span class="sxs-lookup"><span data-stu-id="955d1-131">Specifies a filter condition for a `catch` block or the `case` label of a `switch` statement.</span></span>|
|[<span data-ttu-id="955d1-132">where</span><span class="sxs-lookup"><span data-stu-id="955d1-132">where</span></span>](./where-generic-type-constraint.md)|<span data-ttu-id="955d1-133">将约束添加到泛型声明。</span><span class="sxs-lookup"><span data-stu-id="955d1-133">Adds constraints to a generic declaration.</span></span> <span data-ttu-id="955d1-134">（另请参阅 [where](./where-clause.md)）。</span><span class="sxs-lookup"><span data-stu-id="955d1-134">(See also [where](./where-clause.md)).</span></span>|  
|[<span data-ttu-id="955d1-135">yield</span><span class="sxs-lookup"><span data-stu-id="955d1-135">yield</span></span>](./yield.md)|<span data-ttu-id="955d1-136">在迭代器块中使用，用于向枚举数对象返回值或用于表示迭代结束。</span><span class="sxs-lookup"><span data-stu-id="955d1-136">Used in an iterator block to return a value to the enumerator object or to signal the end of iteration.</span></span>|  
  
 <span data-ttu-id="955d1-137">C# 3.0 中引入的所有查询关键字也都是上下文相关的。</span><span class="sxs-lookup"><span data-stu-id="955d1-137">All query keywords introduced in C# 3.0 are also contextual.</span></span> <span data-ttu-id="955d1-138">有关详细信息，请参阅[查询关键字 (LINQ)](./query-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="955d1-138">For more information, see [Query Keywords (LINQ)](./query-keywords.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955d1-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="955d1-139">See also</span></span>

- [<span data-ttu-id="955d1-140">C# 参考</span><span class="sxs-lookup"><span data-stu-id="955d1-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="955d1-141">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="955d1-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="955d1-142">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="955d1-142">C# Keywords</span></span>](./index.md)
