---
title: 元组
description: '了解 F # 元组，这是一组未命名但有序值，可能不同类型。'
ms.date: 05/16/2016
ms.openlocfilehash: 5d26fd5d7ec5b4939a895a6d2a6a0d7fc6c6c733
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173284"
---
# <a name="tuples"></a><span data-ttu-id="e34b1-103">元组</span><span class="sxs-lookup"><span data-stu-id="e34b1-103">Tuples</span></span>

<span data-ttu-id="e34b1-104">*元组*是未命名但有序值的分组，可能不同类型。</span><span class="sxs-lookup"><span data-stu-id="e34b1-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="e34b1-105">元组可以是引用类型或结构。</span><span class="sxs-lookup"><span data-stu-id="e34b1-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="e34b1-106">语法</span><span class="sxs-lookup"><span data-stu-id="e34b1-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="e34b1-107">备注</span><span class="sxs-lookup"><span data-stu-id="e34b1-107">Remarks</span></span>

<span data-ttu-id="e34b1-108">前面的语法中的每个*元素*可以是任何有效的 F # 表达式。</span><span class="sxs-lookup"><span data-stu-id="e34b1-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="e34b1-109">示例</span><span class="sxs-lookup"><span data-stu-id="e34b1-109">Examples</span></span>

<span data-ttu-id="e34b1-110">元组的示例包括对相同类型或不同类型的成对、三元组等。</span><span class="sxs-lookup"><span data-stu-id="e34b1-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="e34b1-111">下面的代码演示了一些示例。</span><span class="sxs-lookup"><span data-stu-id="e34b1-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="e34b1-112">获取单个值</span><span class="sxs-lookup"><span data-stu-id="e34b1-112">Obtaining Individual Values</span></span>

<span data-ttu-id="e34b1-113">可以使用模式匹配来访问和分配元组元素的名称，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e34b1-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="e34b1-114">还可以通过绑定，通过表达式外部的模式匹配析构元组 `match` `let` ：</span><span class="sxs-lookup"><span data-stu-id="e34b1-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="e34b1-115">或者，你可以将元组的匹配方式作为函数的输入进行模式：</span><span class="sxs-lookup"><span data-stu-id="e34b1-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="e34b1-116">如果只需要元组的一个元素，则可以使用下划线)  (通配符，以避免为不需要的值创建新名称。</span><span class="sxs-lookup"><span data-stu-id="e34b1-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="e34b1-117">将引用元组中的元素复制到结构元组中也很简单：</span><span class="sxs-lookup"><span data-stu-id="e34b1-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="e34b1-118">函数 `fst` 和 `snd` (引用元组仅) 返回元组的第一个和第二个元素。</span><span class="sxs-lookup"><span data-stu-id="e34b1-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="e34b1-119">没有任何内置函数返回三方的第三个元素，但您可以按如下所示轻松编写一个元素。</span><span class="sxs-lookup"><span data-stu-id="e34b1-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="e34b1-120">通常情况下，最好使用模式匹配来访问各个元组元素。</span><span class="sxs-lookup"><span data-stu-id="e34b1-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="e34b1-121">使用元组</span><span class="sxs-lookup"><span data-stu-id="e34b1-121">Using Tuples</span></span>

<span data-ttu-id="e34b1-122">元组提供一种从函数返回多个值的便捷方法，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="e34b1-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="e34b1-123">此示例执行整数除法运算，并将运算的舍入结果作为元组对的第一个成员，并将余数作为成对的第二个成员返回。</span><span class="sxs-lookup"><span data-stu-id="e34b1-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="e34b1-124">如果要避免使用常规函数语法所隐含的函数参数的隐式 currying，则元组也可以用作函数自变量。</span><span class="sxs-lookup"><span data-stu-id="e34b1-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="e34b1-125">定义函数的常用语法 `let sum a b = a + b` 允许您定义一个函数，该函数是函数的第一个自变量的部分应用程序，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e34b1-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="e34b1-126">使用元组作为参数将禁用 currying。</span><span class="sxs-lookup"><span data-stu-id="e34b1-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="e34b1-127">有关详细信息，请参阅[函数](./functions/index.md)中的 "参数的部分应用"。</span><span class="sxs-lookup"><span data-stu-id="e34b1-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="e34b1-128">元组类型的名称</span><span class="sxs-lookup"><span data-stu-id="e34b1-128">Names of Tuple Types</span></span>

<span data-ttu-id="e34b1-129">写出作为元组的类型的名称时，使用 `*` 符号分隔元素。</span><span class="sxs-lookup"><span data-stu-id="e34b1-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="e34b1-130">对于包含、和的元组（如），将 `int` `float` `string` `(10, 10.0, "ten")` 按如下方式编写类型。</span><span class="sxs-lookup"><span data-stu-id="e34b1-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="e34b1-131">与 c # 元组互操作</span><span class="sxs-lookup"><span data-stu-id="e34b1-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="e34b1-132">C # 7.0 将元组引入语言。</span><span class="sxs-lookup"><span data-stu-id="e34b1-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="e34b1-133">C # 中的元组是结构，等效于 F # 中的结构元组。</span><span class="sxs-lookup"><span data-stu-id="e34b1-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="e34b1-134">如果需要与 c # 互操作，则必须使用结构元组。</span><span class="sxs-lookup"><span data-stu-id="e34b1-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="e34b1-135">这很简单。</span><span class="sxs-lookup"><span data-stu-id="e34b1-135">This is easy to do.</span></span>  <span data-ttu-id="e34b1-136">例如，假设您必须将元组传递给 c # 类，然后使用它的结果，这也是一个元组：</span><span class="sxs-lookup"><span data-stu-id="e34b1-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="e34b1-137">在 F # 代码中，您可以将结构元组作为参数传递，并将结果用作结构元组。</span><span class="sxs-lookup"><span data-stu-id="e34b1-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="e34b1-138">引用元组与结构元组之间的转换</span><span class="sxs-lookup"><span data-stu-id="e34b1-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="e34b1-139">由于引用元组和结构元组具有完全不同的基础表示形式，因此它们不能隐式转换。</span><span class="sxs-lookup"><span data-stu-id="e34b1-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="e34b1-140">也就是说，以下代码将不会编译：</span><span class="sxs-lookup"><span data-stu-id="e34b1-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="e34b1-141">您必须对一个元组进行匹配模式，并用构成部分构造另一个元组。</span><span class="sxs-lookup"><span data-stu-id="e34b1-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="e34b1-142">例如：</span><span class="sxs-lookup"><span data-stu-id="e34b1-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="e34b1-143">引用元组的编译形式</span><span class="sxs-lookup"><span data-stu-id="e34b1-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="e34b1-144">本部分说明元组在编译时的形式。</span><span class="sxs-lookup"><span data-stu-id="e34b1-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="e34b1-145">除非目标 .NET Framework 3.5 或更低，否则此处不需要阅读此处的信息。</span><span class="sxs-lookup"><span data-stu-id="e34b1-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="e34b1-146">元组将编译为多个泛型类型之一的对象，这些泛型类型都 `System.Tuple` 是在 arity 上重载的，或者是类型参数的数目。</span><span class="sxs-lookup"><span data-stu-id="e34b1-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="e34b1-147">当你从另一种语言（如 c # 或 Visual Basic）查看这些元组类型时，或者使用不能识别 F # 构造的工具时，该类型将显示在此窗体中。</span><span class="sxs-lookup"><span data-stu-id="e34b1-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="e34b1-148">`Tuple`类型是在 .NET Framework 4 中引入的。</span><span class="sxs-lookup"><span data-stu-id="e34b1-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="e34b1-149">如果以 .NET Framework 的早期版本为目标，则编译器将使用2.0 版本的 F # 核心库中的[系统版本。](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3)</span><span class="sxs-lookup"><span data-stu-id="e34b1-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="e34b1-150">此库中的类型仅用于面向2.0、3.0 和3.5 版本的 .NET Framework 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e34b1-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="e34b1-151">类型转发用于确保 .NET Framework 2.0 和 .NET Framework 4 F # 组件之间的二进制兼容性。</span><span class="sxs-lookup"><span data-stu-id="e34b1-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="e34b1-152">结构元组的编译形式</span><span class="sxs-lookup"><span data-stu-id="e34b1-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="e34b1-153"> (例如) ，结构元组 `struct (x, y)` 在本质上不同于引用元组。</span><span class="sxs-lookup"><span data-stu-id="e34b1-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="e34b1-154">它们被编译到 <xref:System.ValueTuple> 类型中，由 arity 重载或类型参数的数目。</span><span class="sxs-lookup"><span data-stu-id="e34b1-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="e34b1-155">它们等效于[c # 7.0 元组](../../csharp/language-reference/builtin-types/value-tuples.md)和[Visual Basic 2017 元组](../../visual-basic/programming-guide/language-features/data-types/tuples.md)，并互操作双向。</span><span class="sxs-lookup"><span data-stu-id="e34b1-155">They are equivalent to [C# 7.0 Tuples](../../csharp/language-reference/builtin-types/value-tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="e34b1-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e34b1-156">See also</span></span>

- [<span data-ttu-id="e34b1-157">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="e34b1-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e34b1-158">F# 类型</span><span class="sxs-lookup"><span data-stu-id="e34b1-158">F# Types</span></span>](fsharp-types.md)
