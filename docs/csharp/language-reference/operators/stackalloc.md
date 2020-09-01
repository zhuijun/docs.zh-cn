---
description: stackalloc 表达式 - C# 参考
title: stackalloc 表达式 - C# 参考
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 72d91cf9aa67957ed8e1cad5b2c4a1f3b6382c1f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136845"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="e2fc5-103">stackalloc 表达式（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="e2fc5-103">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="e2fc5-104">`stackalloc` 表达式在堆栈上分配内存块。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-104">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="e2fc5-105">该方法返回时，将自动丢弃在方法执行期间创建的堆栈中分配的内存块。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-105">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="e2fc5-106">不能显式释放使用 `stackalloc` 分配的内存。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-106">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="e2fc5-107">堆栈中分配的内存块不受[垃圾回收](../../../standard/garbage-collection/index.md)的影响，也不必通过 [`fixed` 语句](../keywords/fixed-statement.md)固定。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-107">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="e2fc5-108">可以将 `stackalloc` 表达式的结果分配给以下任一类型的变量：</span><span class="sxs-lookup"><span data-stu-id="e2fc5-108">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="e2fc5-109">从 C# 7.2 开始，<xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 将如下例所示：</span><span class="sxs-lookup"><span data-stu-id="e2fc5-109">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="e2fc5-110">将堆栈中分配的内存块分配给 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 变量时，不必使用 [unsafe](../keywords/unsafe.md) 上下文。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="e2fc5-111">使用这些类型时，可以在[条件表达式](conditional-operator.md)或赋值表达式中使用 `stackalloc` 表达式，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e2fc5-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="e2fc5-112">从 C#8.0 开始，只要允许使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 变量，就可以在其他表达式中使用 `stackalloc` 表达式，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="e2fc5-112">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="e2fc5-113">建议尽可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 类型来处理堆栈中分配的内存。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-113">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="e2fc5-114">[指针类型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="e2fc5-114">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="e2fc5-115">如前面的示例所示，在使用指针类型时必须使用 `unsafe` 上下文。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-115">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="e2fc5-116">对于指针类型，只能在局部变量声明中使用 `stackalloc` 表达式来初始化变量。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-116">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="e2fc5-117">堆栈上可用的内存量存在限制。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-117">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="e2fc5-118">如果在堆栈上分配过多的内存，会引发 <xref:System.StackOverflowException>。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-118">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="e2fc5-119">为避免这种情况，请遵循以下规则：</span><span class="sxs-lookup"><span data-stu-id="e2fc5-119">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="e2fc5-120">限制使用 `stackalloc` 分配的内存量：</span><span class="sxs-lookup"><span data-stu-id="e2fc5-120">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="e2fc5-121">由于堆栈上可用的内存量取决于执行代码的环境，因此在定义实际限值时请持保守态度。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-121">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="e2fc5-122">避免在循环内使用 `stackalloc`。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-122">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="e2fc5-123">在循环外分配内存块，然后在循环内重用它。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-123">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="e2fc5-124">新分配的内存的内容未定义。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-124">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="e2fc5-125">在使用之前应对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-125">You should initialize it before the use.</span></span> <span data-ttu-id="e2fc5-126">例如，可以使用 <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> 方法将所有项设置为 `T` 类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-126">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="e2fc5-127">从 C# 7.3 开始，可以使用数组初始值设定项语法来定义新分配内存的内容。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-127">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="e2fc5-128">下面的示例演示执行此操作的各种方法：</span><span class="sxs-lookup"><span data-stu-id="e2fc5-128">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="e2fc5-129">在表达式 `stackalloc T[E]` 中，`T` 必须是[非托管类型](../builtin-types/unmanaged-types.md)，并且 `E` 的计算结果必须为非负 [int](../builtin-types/integral-numeric-types.md) 值。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-129">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="e2fc5-130">安全性</span><span class="sxs-lookup"><span data-stu-id="e2fc5-130">Security</span></span>

<span data-ttu-id="e2fc5-131">使用 `stackalloc` 会自动启用公共语言运行时 (CLR) 中的缓冲区溢出检测功能。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-131">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="e2fc5-132">如果检测到缓冲区溢出，则将尽快终止进程，以便将执行恶意代码的可能性降到最低。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-132">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e2fc5-133">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="e2fc5-133">C# language specification</span></span>

<span data-ttu-id="e2fc5-134">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)以及[允许嵌入上下文中的 `stackalloc`](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) 功能建议说明的[堆栈分配](~/_csharplang/spec/unsafe-code.md#stack-allocation)部分。</span><span class="sxs-lookup"><span data-stu-id="e2fc5-134">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2fc5-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="e2fc5-135">See also</span></span>

- [<span data-ttu-id="e2fc5-136">C# 参考</span><span class="sxs-lookup"><span data-stu-id="e2fc5-136">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e2fc5-137">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="e2fc5-137">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="e2fc5-138">指针相关的运算符</span><span class="sxs-lookup"><span data-stu-id="e2fc5-138">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="e2fc5-139">指针类型</span><span class="sxs-lookup"><span data-stu-id="e2fc5-139">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e2fc5-140">内存和跨度相关类型</span><span class="sxs-lookup"><span data-stu-id="e2fc5-140">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="e2fc5-141">stackalloc 注意事项</span><span class="sxs-lookup"><span data-stu-id="e2fc5-141">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
