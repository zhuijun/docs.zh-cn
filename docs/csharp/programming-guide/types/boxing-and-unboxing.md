---
title: 装箱和取消装箱 - C# 编程指南
description: 了解 C# 编程中的装箱和取消装箱。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 5a5bfcc79de8ba3ff66ca8aab9d86d69d89f9221
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380691"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="57e6e-104">装箱和取消装箱（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="57e6e-104">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="57e6e-105">装箱是将[值类型](../../language-reference/builtin-types/value-types.md)转换为 `object` 类型或由此值类型实现的任何接口类型的过程。</span><span class="sxs-lookup"><span data-stu-id="57e6e-105">Boxing is the process of converting a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="57e6e-106">常见语言运行时 (CLR) 对值类型进行装箱时，会将值包装在 <xref:System.Object?displayProperty=nameWithType> 实例中并将其存储在托管堆中。</span><span class="sxs-lookup"><span data-stu-id="57e6e-106">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="57e6e-107">取消装箱将从对象中提取值类型。</span><span class="sxs-lookup"><span data-stu-id="57e6e-107">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="57e6e-108">装箱是隐式的；取消装箱是显式的。</span><span class="sxs-lookup"><span data-stu-id="57e6e-108">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="57e6e-109">装箱和取消装箱的概念是类型系统 C# 统一视图的基础，其中任一类型的值都被视为一个对象。</span><span class="sxs-lookup"><span data-stu-id="57e6e-109">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="57e6e-110">下例将整型变量 `i` 进行了装箱并分配给对象 `o`。</span><span class="sxs-lookup"><span data-stu-id="57e6e-110">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="57e6e-111">然后，可以将对象 `o` 取消装箱并分配给整型变量 `i`：</span><span class="sxs-lookup"><span data-stu-id="57e6e-111">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="57e6e-112">以下示例演示如何在 C# 中使用装箱。</span><span class="sxs-lookup"><span data-stu-id="57e6e-112">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="57e6e-113">性能</span><span class="sxs-lookup"><span data-stu-id="57e6e-113">Performance</span></span>

<span data-ttu-id="57e6e-114">相对于简单的赋值而言，装箱和取消装箱过程需要进行大量的计算。</span><span class="sxs-lookup"><span data-stu-id="57e6e-114">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="57e6e-115">对值类型进行装箱时，必须分配并构造一个新对象。</span><span class="sxs-lookup"><span data-stu-id="57e6e-115">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="57e6e-116">取消装箱所需的强制转换也需要进行大量的计算，只是程度较轻。</span><span class="sxs-lookup"><span data-stu-id="57e6e-116">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="57e6e-117">有关更多信息，请参阅[性能](../../../framework/performance/performance-tips.md)。</span><span class="sxs-lookup"><span data-stu-id="57e6e-117">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="57e6e-118">装箱</span><span class="sxs-lookup"><span data-stu-id="57e6e-118">Boxing</span></span>

<span data-ttu-id="57e6e-119">装箱用于在垃圾回收堆中存储值类型。</span><span class="sxs-lookup"><span data-stu-id="57e6e-119">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="57e6e-120">装箱是[值类型](../../language-reference/builtin-types/value-types.md)到 `object` 类型或到此值类型所实现的任何接口类型的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="57e6e-120">Boxing is an implicit conversion of a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="57e6e-121">对值类型装箱会在堆中分配一个对象实例，并将该值复制到新的对象中。</span><span class="sxs-lookup"><span data-stu-id="57e6e-121">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="57e6e-122">请看以下值类型变量的声明：</span><span class="sxs-lookup"><span data-stu-id="57e6e-122">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="57e6e-123">以下语句对变量 `i` 隐式应用了装箱操作：</span><span class="sxs-lookup"><span data-stu-id="57e6e-123">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="57e6e-124">此语句的结果是在堆栈上创建对象引用 `o`，而在堆上则引用 `int` 类型的值。</span><span class="sxs-lookup"><span data-stu-id="57e6e-124">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="57e6e-125">该值是赋给变量 `i` 的值类型值的一个副本。</span><span class="sxs-lookup"><span data-stu-id="57e6e-125">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="57e6e-126">以下装箱转换图说明了 `i` 和 `o` 这两个变量之间的差异：</span><span class="sxs-lookup"><span data-stu-id="57e6e-126">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![显示 i 和 o 变量之间的差异的图。](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="57e6e-128">还可以像下面的示例一样执行显式装箱，但显式装箱从来不是必需的：</span><span class="sxs-lookup"><span data-stu-id="57e6e-128">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="57e6e-129">描述</span><span class="sxs-lookup"><span data-stu-id="57e6e-129">Description</span></span>

<span data-ttu-id="57e6e-130">此示例使用装箱将整型变量 `i` 转换为对象 `o`。</span><span class="sxs-lookup"><span data-stu-id="57e6e-130">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="57e6e-131">这样一来，存储在变量 `i` 中的值就从 `123` 更改为 `456`。</span><span class="sxs-lookup"><span data-stu-id="57e6e-131">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="57e6e-132">该示例表明原始值类型和装箱的对象使用不同的内存位置，因此能够存储不同的值。</span><span class="sxs-lookup"><span data-stu-id="57e6e-132">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="57e6e-133">示例</span><span class="sxs-lookup"><span data-stu-id="57e6e-133">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="57e6e-134">取消装箱</span><span class="sxs-lookup"><span data-stu-id="57e6e-134">Unboxing</span></span>

<span data-ttu-id="57e6e-135">取消装箱是从 `object` 类型到[值类型](../../language-reference/builtin-types/value-types.md)或从接口类型到实现该接口的值类型的显式转换。</span><span class="sxs-lookup"><span data-stu-id="57e6e-135">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/builtin-types/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="57e6e-136">取消装箱操作包括：</span><span class="sxs-lookup"><span data-stu-id="57e6e-136">An unboxing operation consists of:</span></span>

- <span data-ttu-id="57e6e-137">检查对象实例，以确保它是给定值类型的装箱值。</span><span class="sxs-lookup"><span data-stu-id="57e6e-137">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="57e6e-138">将该值从实例复制到值类型变量中。</span><span class="sxs-lookup"><span data-stu-id="57e6e-138">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="57e6e-139">下面的语句演示装箱和取消装箱两种操作：</span><span class="sxs-lookup"><span data-stu-id="57e6e-139">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="57e6e-140">下图演示了上述语句的结果：</span><span class="sxs-lookup"><span data-stu-id="57e6e-140">The following figure demonstrates the result of the previous statements:</span></span>

![显示取消装箱转换的图。](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="57e6e-142">要在运行时成功取消装箱值类型，被取消装箱的项必须是对一个对象的引用，该对象是先前通过装箱该值类型的实例创建的。</span><span class="sxs-lookup"><span data-stu-id="57e6e-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="57e6e-143">尝试取消装箱 `null` 会导致 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="57e6e-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="57e6e-144">尝试取消装箱对不兼容值类型的引用会导致 <xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="57e6e-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="57e6e-145">示例</span><span class="sxs-lookup"><span data-stu-id="57e6e-145">Example</span></span>

<span data-ttu-id="57e6e-146">下面的示例演示无效的取消装箱及引发的 `InvalidCastException`。</span><span class="sxs-lookup"><span data-stu-id="57e6e-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="57e6e-147">使用 `try` 和 `catch`，在发生错误时显示错误信息。</span><span class="sxs-lookup"><span data-stu-id="57e6e-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="57e6e-148">此程序输出：</span><span class="sxs-lookup"><span data-stu-id="57e6e-148">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="57e6e-149">如果将下列语句：</span><span class="sxs-lookup"><span data-stu-id="57e6e-149">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="57e6e-150">更改为：</span><span class="sxs-lookup"><span data-stu-id="57e6e-150">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="57e6e-151">将执行转换，并将得到以下输出：</span><span class="sxs-lookup"><span data-stu-id="57e6e-151">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="57e6e-152">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="57e6e-152">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="57e6e-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="57e6e-153">See also</span></span>

- [<span data-ttu-id="57e6e-154">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="57e6e-154">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="57e6e-155">引用类型</span><span class="sxs-lookup"><span data-stu-id="57e6e-155">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="57e6e-156">值类型</span><span class="sxs-lookup"><span data-stu-id="57e6e-156">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
