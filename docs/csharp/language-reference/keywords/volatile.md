---
description: volatile - C# 参考
title: volatile - C# 参考
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: bb89e99e8e28ff1e263817f498619dbfae700a50
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141694"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="7cc32-103">volatile（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="7cc32-103">volatile (C# Reference)</span></span>

<span data-ttu-id="7cc32-104">`volatile` 关键字指示一个字段可以由多个同时执行的线程修改。</span><span class="sxs-lookup"><span data-stu-id="7cc32-104">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="7cc32-105">出于性能原因，编译器，运行时系统甚至硬件都可能重新排列对存储器位置的读取和写入。</span><span class="sxs-lookup"><span data-stu-id="7cc32-105">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="7cc32-106">声明了 `volatile` 的字段不进行这些优化。</span><span class="sxs-lookup"><span data-stu-id="7cc32-106">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="7cc32-107">添加 `volatile` 修饰符可确保所有线程观察易失性写入操作（由任何其他线程执行）时的观察顺序与写入操作的执行顺序一致。</span><span class="sxs-lookup"><span data-stu-id="7cc32-107">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="7cc32-108">不确保从所有执行线程整体来看时所有易失性写入操作均按执行顺序排序。</span><span class="sxs-lookup"><span data-stu-id="7cc32-108">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="7cc32-109">`volatile` 关键字可应用于以下类型的字段：</span><span class="sxs-lookup"><span data-stu-id="7cc32-109">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="7cc32-110">引用类型。</span><span class="sxs-lookup"><span data-stu-id="7cc32-110">Reference types.</span></span>
- <span data-ttu-id="7cc32-111">指针类型（在不安全的上下文中）。</span><span class="sxs-lookup"><span data-stu-id="7cc32-111">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="7cc32-112">请注意，虽然指针本身可以是可变的，但是它指向的对象不能是可变的。</span><span class="sxs-lookup"><span data-stu-id="7cc32-112">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="7cc32-113">换句话说，不能声明“指向可变对象的指针”。</span><span class="sxs-lookup"><span data-stu-id="7cc32-113">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="7cc32-114">简单类型，如 `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`char`、`float` 和 `bool`。</span><span class="sxs-lookup"><span data-stu-id="7cc32-114">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="7cc32-115">具有以下基本类型之一的 `enum` 类型：`byte`、`sbyte`、`short`、`ushort`、`int` 或 `uint`。</span><span class="sxs-lookup"><span data-stu-id="7cc32-115">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="7cc32-116">已知为引用类型的泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="7cc32-116">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="7cc32-117"><xref:System.IntPtr> 和 <xref:System.UIntPtr>。</span><span class="sxs-lookup"><span data-stu-id="7cc32-117"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="7cc32-118">其他类型（包括 `double` 和 `long`）无法标记为 `volatile`，因为对这些类型的字段的读取和写入不能保证是原子的。</span><span class="sxs-lookup"><span data-stu-id="7cc32-118">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="7cc32-119">若要保护对这些类型字段的多线程访问，请使用 <xref:System.Threading.Interlocked> 类成员或使用 [`lock`](lock-statement.md) 语句保护访问权限。</span><span class="sxs-lookup"><span data-stu-id="7cc32-119">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="7cc32-120">`volatile` 关键字只能应用于 `class` 或 `struct` 的字段。</span><span class="sxs-lookup"><span data-stu-id="7cc32-120">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="7cc32-121">不能将局部变量声明为 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="7cc32-121">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="7cc32-122">示例</span><span class="sxs-lookup"><span data-stu-id="7cc32-122">Example</span></span>

<span data-ttu-id="7cc32-123">下面的示例说明如何将公共字段变量声明为 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="7cc32-123">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="7cc32-124">下面的示例演示如何创建辅助线程，并用它与主线程并行执行处理。</span><span class="sxs-lookup"><span data-stu-id="7cc32-124">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="7cc32-125">有关多线程处理的详细信息，请参阅[托管线程处理](../../../standard/threading/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7cc32-125">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="7cc32-126">将 `volatile` 修饰符添加到 `_shouldStop` 的声明后，将始终获得相同的结果（类似于前面代码中显示的片段）。</span><span class="sxs-lookup"><span data-stu-id="7cc32-126">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="7cc32-127">但是，如果 `_shouldStop` 成员上没有该修饰符，则行为是不可预测的。</span><span class="sxs-lookup"><span data-stu-id="7cc32-127">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="7cc32-128">`DoWork` 方法可能会优化成员访问，从而导致读取陈旧数据。</span><span class="sxs-lookup"><span data-stu-id="7cc32-128">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="7cc32-129">鉴于多线程编程的性质，读取陈旧数据的次数是不可预测的。</span><span class="sxs-lookup"><span data-stu-id="7cc32-129">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="7cc32-130">不同的程序运行会产生一些不同的结果。</span><span class="sxs-lookup"><span data-stu-id="7cc32-130">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7cc32-131">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="7cc32-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7cc32-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="7cc32-132">See also</span></span>

- [<span data-ttu-id="7cc32-133">C# 语言规范：可变关键字</span><span class="sxs-lookup"><span data-stu-id="7cc32-133">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="7cc32-134">C# 参考</span><span class="sxs-lookup"><span data-stu-id="7cc32-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7cc32-135">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="7cc32-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7cc32-136">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="7cc32-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7cc32-137">修饰符</span><span class="sxs-lookup"><span data-stu-id="7cc32-137">Modifiers</span></span>](index.md)
- [<span data-ttu-id="7cc32-138">lock 语句</span><span class="sxs-lookup"><span data-stu-id="7cc32-138">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
