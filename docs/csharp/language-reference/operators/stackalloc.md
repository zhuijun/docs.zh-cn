---
title: stackalloc 表达式 - C# 参考
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 4f20f3262b77cc2fe16480e53d13960e68d230b5
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916667"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="6b8e8-102">stackalloc 表达式（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="6b8e8-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="6b8e8-103">`stackalloc` 表达式在堆栈上分配内存块。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="6b8e8-104">该方法返回时，将自动丢弃在方法执行期间创建的堆栈中分配的内存块。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="6b8e8-105">不能显式释放使用 `stackalloc` 分配的内存。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="6b8e8-106">堆栈中分配的内存块不受[垃圾回收](../../../standard/garbage-collection/index.md)的影响，也不必通过 [`fixed` 语句](../keywords/fixed-statement.md)固定。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="6b8e8-107">可以将 `stackalloc` 表达式的结果分配给以下任一类型的变量：</span><span class="sxs-lookup"><span data-stu-id="6b8e8-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="6b8e8-108">从 C# 7.2 开始，<xref:System.Span%601?displayProperty=nameWithType> 或 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 将如下例所示：</span><span class="sxs-lookup"><span data-stu-id="6b8e8-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="6b8e8-109">将堆栈中分配的内存块分配给 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 变量时，不必使用 [unsafe](../keywords/unsafe.md) 上下文。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="6b8e8-110">使用这些类型时，可以在[条件表达式](conditional-operator.md)或赋值表达式中使用 `stackalloc` 表达式，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="6b8e8-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="6b8e8-111">从 C#8.0 开始，只要允许使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 变量，就可以在其他表达式中使用 `stackalloc` 表达式，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="6b8e8-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="6b8e8-112">建议尽可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601> 类型来处理堆栈中分配的内存。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="6b8e8-113">[指针类型](../../programming-guide/unsafe-code-pointers/pointer-types.md)，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="6b8e8-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="6b8e8-114">如前面的示例所示，在使用指针类型时必须使用 `unsafe` 上下文。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="6b8e8-115">对于指针类型，只能在局部变量声明中使用 `stackalloc` 表达式来初始化变量。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="6b8e8-116">堆栈上可用的内存量存在限制。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="6b8e8-117">如果在堆栈上分配过多的内存，会引发 <xref:System.StackOverflowException>。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="6b8e8-118">为避免这种情况，请遵循以下规则：</span><span class="sxs-lookup"><span data-stu-id="6b8e8-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="6b8e8-119">限制使用 `stackalloc` 分配的内存量：</span><span class="sxs-lookup"><span data-stu-id="6b8e8-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="6b8e8-120">由于堆栈上可用的内存量取决于执行代码的环境，因此在定义实际限值时请持保守态度。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="6b8e8-121">避免在循环内使用 `stackalloc`。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="6b8e8-122">在循环外分配内存块，然后在循环内重用它。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="6b8e8-123">新分配的内存的内容未定义。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="6b8e8-124">在使用之前应对其进行初始化。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-124">You should initialize it before the use.</span></span> <span data-ttu-id="6b8e8-125">例如，可以使用 <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> 方法将所有项设置为 `T` 类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="6b8e8-126">从 C# 7.3 开始，可以使用数组初始值设定项语法来定义新分配内存的内容。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="6b8e8-127">下面的示例演示执行此操作的各种方法：</span><span class="sxs-lookup"><span data-stu-id="6b8e8-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="6b8e8-128">在表达式 `stackalloc T[E]` 中，`T` 必须是[非托管类型](../builtin-types/unmanaged-types.md)，并且 `E` 的计算结果必须为非负 [int](../builtin-types/integral-numeric-types.md) 值。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="6b8e8-129">安全性</span><span class="sxs-lookup"><span data-stu-id="6b8e8-129">Security</span></span>

<span data-ttu-id="6b8e8-130">使用 `stackalloc` 会自动启用公共语言运行时 (CLR) 中的缓冲区溢出检测功能。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="6b8e8-131">如果检测到缓冲区溢出，则将尽快终止进程，以便将执行恶意代码的可能性降到最低。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6b8e8-132">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="6b8e8-132">C# language specification</span></span>

<span data-ttu-id="6b8e8-133">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)以及[允许嵌入上下文中的 `stackalloc`](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) 功能建议说明的[堆栈分配](~/_csharplang/spec/unsafe-code.md#stack-allocation)部分。</span><span class="sxs-lookup"><span data-stu-id="6b8e8-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b8e8-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b8e8-134">See also</span></span>

- [<span data-ttu-id="6b8e8-135">C# 参考</span><span class="sxs-lookup"><span data-stu-id="6b8e8-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6b8e8-136">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="6b8e8-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="6b8e8-137">指针相关的运算符</span><span class="sxs-lookup"><span data-stu-id="6b8e8-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="6b8e8-138">指针类型</span><span class="sxs-lookup"><span data-stu-id="6b8e8-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="6b8e8-139">内存和跨度相关类型</span><span class="sxs-lookup"><span data-stu-id="6b8e8-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="6b8e8-140">stackalloc 注意事项</span><span class="sxs-lookup"><span data-stu-id="6b8e8-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
