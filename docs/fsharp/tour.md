---
title: F# 教程
description: '在本教程中，通过代码示例检查 F # 编程语言的一些重要功能。'
ms.date: 08/14/2020
ms.openlocfilehash: b115317e1f47ef7e18333cae4145b99e11645579
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558590"
---
# <a name="tour-of-f"></a><span data-ttu-id="da09e-103">F 教程\#</span><span class="sxs-lookup"><span data-stu-id="da09e-103">Tour of F\#</span></span>

<span data-ttu-id="da09e-104">了解 F # 的最佳方式是读取和写入 F # 代码。</span><span class="sxs-lookup"><span data-stu-id="da09e-104">The best way to learn about F# is to read and write F# code.</span></span> <span data-ttu-id="da09e-105">本文将通过 F # 语言的某些重要功能来提供教程，并提供可在计算机上执行的一些代码片段。</span><span class="sxs-lookup"><span data-stu-id="da09e-105">This article will act as a tour through some of the key features of the F# language and give you some code snippets that you can execute on your machine.</span></span> <span data-ttu-id="da09e-106">若要了解如何设置开发环境，请查看 [入门](get-started/index.md)。</span><span class="sxs-lookup"><span data-stu-id="da09e-106">To learn about setting up a development environment, check out [Getting Started](get-started/index.md).</span></span>

<span data-ttu-id="da09e-107">F #：函数和类型中有两个主要概念。</span><span class="sxs-lookup"><span data-stu-id="da09e-107">There are two primary concepts in F#: functions and types.</span></span>  <span data-ttu-id="da09e-108">本教程将重点介绍这两个概念的语言功能。</span><span class="sxs-lookup"><span data-stu-id="da09e-108">This tour will emphasize features of the language which fall into these two concepts.</span></span>

## <a name="executing-the-code-online"></a><span data-ttu-id="da09e-109">联机执行代码</span><span class="sxs-lookup"><span data-stu-id="da09e-109">Executing the code online</span></span>

<span data-ttu-id="da09e-110">如果你的计算机上未安装 F #，则可以在 [WebAssembly 上使用 Try F #](https://tryfsharp.fsbolero.io/)执行浏览器中的所有示例。</span><span class="sxs-lookup"><span data-stu-id="da09e-110">If you don't have F# installed on your machine, you can execute all of the samples in your browser with [Try F# on WebAssembly](https://tryfsharp.fsbolero.io/).</span></span> <span data-ttu-id="da09e-111">Fable 是在浏览器中直接执行的 F # 的方言。</span><span class="sxs-lookup"><span data-stu-id="da09e-111">Fable is a dialect of F# that executes directly in your browser.</span></span> <span data-ttu-id="da09e-112">若要查看复制中跟随的示例，请查看示例 > 了解 Fable 复制的左侧菜单栏中 **的 F # > 教程** 。</span><span class="sxs-lookup"><span data-stu-id="da09e-112">To view the samples that follow in the REPL, check out **Samples > Learn > Tour of F#** in the left-hand menu bar of the Fable REPL.</span></span>

## <a name="functions-and-modules"></a><span data-ttu-id="da09e-113">函数和模块</span><span class="sxs-lookup"><span data-stu-id="da09e-113">Functions and Modules</span></span>

<span data-ttu-id="da09e-114">任何 F # 程序的最基本部分都是组织到***模块***中的***函数***。</span><span class="sxs-lookup"><span data-stu-id="da09e-114">The most fundamental pieces of any F# program are ***functions*** organized into ***modules***.</span></span>  <span data-ttu-id="da09e-115">[函数](./language-reference/functions/index.md) 对输入进行操作以生成输出，并按模块进行组织，这些 [模块](./language-reference/modules.md)是在 F # 中对项进行分组的主要方式。</span><span class="sxs-lookup"><span data-stu-id="da09e-115">[Functions](./language-reference/functions/index.md) perform work on inputs to produce outputs, and they are organized under [Modules](./language-reference/modules.md), which are the primary way you group things in F#.</span></span>  <span data-ttu-id="da09e-116">它们是使用绑定定义的，该[ `let` 绑定](./language-reference/functions/let-bindings.md)为函数指定名称并定义其参数。</span><span class="sxs-lookup"><span data-stu-id="da09e-116">They are defined using the [`let` binding](./language-reference/functions/let-bindings.md), which give the function a name and define its arguments.</span></span>

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

<span data-ttu-id="da09e-117">`let` 绑定还介绍如何将值绑定到名称，类似于其他语言中的变量。</span><span class="sxs-lookup"><span data-stu-id="da09e-117">`let` bindings are also how you bind a value to a name, similar to a variable in other languages.</span></span>  <span data-ttu-id="da09e-118">`let` 默认情况下，绑定是 ***不可变*** 的，这意味着一旦值或函数绑定到名称，就不能就地更改。</span><span class="sxs-lookup"><span data-stu-id="da09e-118">`let` bindings are ***immutable*** by default, which means that once a value or function is bound to a name, it cannot be changed in-place.</span></span>  <span data-ttu-id="da09e-119">这与其他语言中的变量不同，后者是 ***可变***的，这意味着在任何时间点都可以更改其值。</span><span class="sxs-lookup"><span data-stu-id="da09e-119">This is in contrast to variables in other languages, which are ***mutable***, meaning their values can be changed at any point in time.</span></span>  <span data-ttu-id="da09e-120">如果需要可变绑定，可使用 `let mutable ...` 语法。</span><span class="sxs-lookup"><span data-stu-id="da09e-120">If you require a mutable binding, you can use `let mutable ...` syntax.</span></span>

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a><span data-ttu-id="da09e-121">数字、布尔值和字符串</span><span class="sxs-lookup"><span data-stu-id="da09e-121">Numbers, Booleans, and Strings</span></span>

<span data-ttu-id="da09e-122">作为一种 .NET 语言，F # 支持 .NET 中存在的相同基础 [基元类型](language-reference/basic-types.md) 。</span><span class="sxs-lookup"><span data-stu-id="da09e-122">As a .NET language, F# supports the same underlying [primitive types](language-reference/basic-types.md) that exist in .NET.</span></span>

<span data-ttu-id="da09e-123">下面是 F # 中的各种数值类型的表示方式：</span><span class="sxs-lookup"><span data-stu-id="da09e-123">Here is how various numeric types are represented in F#:</span></span>

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

<span data-ttu-id="da09e-124">下面是布尔值和执行基本条件逻辑的形式：</span><span class="sxs-lookup"><span data-stu-id="da09e-124">Here's what Boolean values and performing basic conditional logic looks like:</span></span>

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

<span data-ttu-id="da09e-125">基本 [字符串](./language-reference/strings.md) 操作如下所示：</span><span class="sxs-lookup"><span data-stu-id="da09e-125">And here's what basic [string](./language-reference/strings.md) manipulation looks like:</span></span>

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a><span data-ttu-id="da09e-126">元组</span><span class="sxs-lookup"><span data-stu-id="da09e-126">Tuples</span></span>

<span data-ttu-id="da09e-127">[元组](./language-reference/tuples.md) 是 F # 中的一个大型交易。</span><span class="sxs-lookup"><span data-stu-id="da09e-127">[Tuples](./language-reference/tuples.md) are a big deal in F#.</span></span>  <span data-ttu-id="da09e-128">它们是未命名但有序值的分组，可被视为值本身。</span><span class="sxs-lookup"><span data-stu-id="da09e-128">They are a grouping of unnamed, but ordered values, that can be treated as values themselves.</span></span>  <span data-ttu-id="da09e-129">将它们视为聚合自其他值的值。</span><span class="sxs-lookup"><span data-stu-id="da09e-129">Think of them as values which are aggregated from other values.</span></span>  <span data-ttu-id="da09e-130">它们有很多用途，如从函数中方便地返回多个值，或者为某些即席的便利分组值。</span><span class="sxs-lookup"><span data-stu-id="da09e-130">They have many uses, such as conveniently returning multiple values from a function, or grouping values for some ad-hoc convenience.</span></span>

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

<span data-ttu-id="da09e-131">你还可以创建 `struct` 元组。</span><span class="sxs-lookup"><span data-stu-id="da09e-131">You can also create `struct` tuples.</span></span>  <span data-ttu-id="da09e-132">它们还与 c # 7/Visual Basic 15 元组完全互操作，后者也是 `struct` 元组：</span><span class="sxs-lookup"><span data-stu-id="da09e-132">These also interoperate fully with C#7/Visual Basic 15 tuples, which are also `struct` tuples:</span></span>

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

<span data-ttu-id="da09e-133">请务必注意，因为 `struct` 元组是值类型，所以它们不能隐式转换为引用元组，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="da09e-133">It's important to note that because `struct` tuples are value types, they cannot be implicitly converted to reference tuples, or vice versa.</span></span>  <span data-ttu-id="da09e-134">必须在 reference 和 struct 元组之间显式转换。</span><span class="sxs-lookup"><span data-stu-id="da09e-134">You must explicitly convert between a reference and struct tuple.</span></span>

## <a name="pipelines-and-composition"></a><span data-ttu-id="da09e-135">管道和组合</span><span class="sxs-lookup"><span data-stu-id="da09e-135">Pipelines and Composition</span></span>

<span data-ttu-id="da09e-136">`|>`处理 F # 中的数据时，会广泛使用管道运算符（例如）。</span><span class="sxs-lookup"><span data-stu-id="da09e-136">Pipe operators such as `|>` are used extensively when processing data in F#.</span></span> <span data-ttu-id="da09e-137">这些运算符是允许您以灵活的方式建立函数的 "管道" 的函数。</span><span class="sxs-lookup"><span data-stu-id="da09e-137">These operators are functions that allow you to establish "pipelines" of functions in a flexible manner.</span></span> <span data-ttu-id="da09e-138">下面的示例演示如何利用这些运算符来生成简单的功能管道：</span><span class="sxs-lookup"><span data-stu-id="da09e-138">The following example walks through how you can take advantage of these operators to build a simple functional pipeline:</span></span>

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

<span data-ttu-id="da09e-139">之前的示例使用了 F # 的许多功能，包括列表处理函数、第一类函数和 [部分应用程序](./language-reference/functions/index.md#partial-application-of-arguments)。</span><span class="sxs-lookup"><span data-stu-id="da09e-139">The previous sample made use of many features of F#, including list processing functions, first-class functions, and [partial application](./language-reference/functions/index.md#partial-application-of-arguments).</span></span> <span data-ttu-id="da09e-140">尽管深入了解其中每个概念可能会变得很简单，但应清楚地了解如何在生成管道时使用函数来处理数据。</span><span class="sxs-lookup"><span data-stu-id="da09e-140">Although a deep understanding of each of those concepts can become somewhat advanced, it should be clear how easily functions can be used to process data when building pipelines.</span></span>

## <a name="lists-arrays-and-sequences"></a><span data-ttu-id="da09e-141">列表、数组和序列</span><span class="sxs-lookup"><span data-stu-id="da09e-141">Lists, Arrays, and Sequences</span></span>

<span data-ttu-id="da09e-142">列表、数组和序列是 F # 核心库中的三种主要集合类型。</span><span class="sxs-lookup"><span data-stu-id="da09e-142">Lists, Arrays, and Sequences are three primary collection types in the F# core library.</span></span>

<span data-ttu-id="da09e-143">[列表](./language-reference/lists.md) 是具有相同类型的元素的有序集合，不可变集合。</span><span class="sxs-lookup"><span data-stu-id="da09e-143">[Lists](./language-reference/lists.md) are ordered, immutable collections of elements of the same type.</span></span>  <span data-ttu-id="da09e-144">它们是一种单向链接列表，这意味着它们适用于枚举，但如果它们很大，则随机访问和串联的选择会很糟糕。</span><span class="sxs-lookup"><span data-stu-id="da09e-144">They are singly-linked lists, which means they are meant for enumeration, but a poor choice for random access and concatenation if they're large.</span></span>  <span data-ttu-id="da09e-145">这与其他常用语言的列表相反，后者通常不使用单向链接列表来表示列表。</span><span class="sxs-lookup"><span data-stu-id="da09e-145">This in contrast to Lists in other popular languages, which typically do not use a singly-linked list to represent Lists.</span></span>

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

<span data-ttu-id="da09e-146">[数组](./language-reference/arrays.md) 是具有相同类型的元素的固定大小、 *可变* 集合。</span><span class="sxs-lookup"><span data-stu-id="da09e-146">[Arrays](./language-reference/arrays.md) are fixed-size, *mutable* collections of elements of the same type.</span></span>  <span data-ttu-id="da09e-147">它们支持快速随机访问元素，并且速度快于 F # 列表，因为它们只是连续的内存块。</span><span class="sxs-lookup"><span data-stu-id="da09e-147">They support fast random access of elements, and are faster than F# lists because they are just contiguous blocks of memory.</span></span>

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

<span data-ttu-id="da09e-148">[序列](./language-reference/sequences.md) 是一系列逻辑元素，它们都属于同一类型。</span><span class="sxs-lookup"><span data-stu-id="da09e-148">[Sequences](./language-reference/sequences.md) are a logical series of elements, all of the same type.</span></span>  <span data-ttu-id="da09e-149">这些是比列表和数组更通用的类型，可以是 "视图" 到任何逻辑序列的元素。</span><span class="sxs-lookup"><span data-stu-id="da09e-149">These are a more general type than Lists and Arrays, capable of being your "view" into any logical series of elements.</span></span>  <span data-ttu-id="da09e-150">它们还会显得很明显，因为它们可能是 ***延迟***的，也就是说，仅当需要时才可以计算元素。</span><span class="sxs-lookup"><span data-stu-id="da09e-150">They also stand out because they can be ***lazy***, which means that elements can be computed only when they are needed.</span></span>

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a><span data-ttu-id="da09e-151">递归函数</span><span class="sxs-lookup"><span data-stu-id="da09e-151">Recursive Functions</span></span>

<span data-ttu-id="da09e-152">处理集合或元素序列通常是通过 F # 中的 [递归](./language-reference/functions/index.md#recursive-functions) 来完成的。</span><span class="sxs-lookup"><span data-stu-id="da09e-152">Processing collections or sequences of elements is typically done with [recursion](./language-reference/functions/index.md#recursive-functions) in F#.</span></span>  <span data-ttu-id="da09e-153">尽管 F # 支持循环和命令式编程，但递归是首选的，因为这样可以更轻松地保证正确性。</span><span class="sxs-lookup"><span data-stu-id="da09e-153">Although F# has support for loops and imperative programming, recursion is preferred because it is easier to guarantee correctness.</span></span>

> [!NOTE]
> <span data-ttu-id="da09e-154">下面的示例通过表达式利用模式匹配 `match` 。</span><span class="sxs-lookup"><span data-stu-id="da09e-154">The following example makes use of the pattern matching via the `match` expression.</span></span>  <span data-ttu-id="da09e-155">本文的后面部分介绍了这一基本构造。</span><span class="sxs-lookup"><span data-stu-id="da09e-155">This fundamental construct is covered later in this article.</span></span>

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

<span data-ttu-id="da09e-156">F # 还完全支持尾调用优化，这是一种优化递归调用的方法，使其与循环构造一样快。</span><span class="sxs-lookup"><span data-stu-id="da09e-156">F# also has full support for Tail Call Optimization, which is a way to optimize recursive calls so that they are just as fast as a loop construct.</span></span>

## <a name="record-and-discriminated-union-types"></a><span data-ttu-id="da09e-157">记录和可区分联合类型</span><span class="sxs-lookup"><span data-stu-id="da09e-157">Record and Discriminated Union Types</span></span>

<span data-ttu-id="da09e-158">记录类型和联合类型是 F # 代码中使用的两种基本数据类型，通常是在 F # 程序中表示数据的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="da09e-158">Record and Union types are two fundamental data types used in F# code, and are generally the best way to represent data in an F# program.</span></span>  <span data-ttu-id="da09e-159">虽然这使得它们类似于其他语言中的类，但其主要区别之一是它们具有结构相等语义。</span><span class="sxs-lookup"><span data-stu-id="da09e-159">Although this makes them similar to classes in other languages, one of their primary differences is that they have structural equality semantics.</span></span>  <span data-ttu-id="da09e-160">这意味着，它们是 "本机" 可比较的，相等非常简单-只需检查是否有一个与另一个相等。</span><span class="sxs-lookup"><span data-stu-id="da09e-160">This means that they are "natively" comparable and equality is straightforward - just check if one is equal to the other.</span></span>

<span data-ttu-id="da09e-161">[记录](./language-reference/records.md) 是命名值的聚合，可选成员 (如) 的方法。</span><span class="sxs-lookup"><span data-stu-id="da09e-161">[Records](./language-reference/records.md) are an aggregate of named values, with optional members (such as methods).</span></span>  <span data-ttu-id="da09e-162">如果熟悉 c # 或 Java，则这些内容应类似于 "Poco" 或 "Pojo"。</span><span class="sxs-lookup"><span data-stu-id="da09e-162">If you're familiar with C# or Java, then these should feel similar to POCOs or POJOs - just with structural equality and less ceremony.</span></span>

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

<span data-ttu-id="da09e-163">您还可以将记录表示为结构。</span><span class="sxs-lookup"><span data-stu-id="da09e-163">You can also represent Records as structs.</span></span> <span data-ttu-id="da09e-164">这是通过属性完成的 `[<Struct>]` ：</span><span class="sxs-lookup"><span data-stu-id="da09e-164">This is done with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

<span data-ttu-id="da09e-165">[Du) 的可区分联合 (](./language-reference/discriminated-unions.md) 是可能是一些命名窗体或事例的值。</span><span class="sxs-lookup"><span data-stu-id="da09e-165">[Discriminated Unions (DUs)](./language-reference/discriminated-unions.md) are values which could be a number of named forms or cases.</span></span>  <span data-ttu-id="da09e-166">类型中存储的数据可以是多个不同值之一。</span><span class="sxs-lookup"><span data-stu-id="da09e-166">Data stored in the type can be one of several distinct values.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

<span data-ttu-id="da09e-167">你还可以使用 Du 作为 *单用例可区分联合*，以帮助进行基于基元类型的域建模。</span><span class="sxs-lookup"><span data-stu-id="da09e-167">You can also use DUs as *Single-Case Discriminated Unions*, to help with domain modeling over primitive types.</span></span>  <span data-ttu-id="da09e-168">通常情况下，字符串和其他基元类型用于表示某些内容，因此具有特定的含义。</span><span class="sxs-lookup"><span data-stu-id="da09e-168">Often times, strings and other primitive types are used to represent something, and are thus given a particular meaning.</span></span>  <span data-ttu-id="da09e-169">但是，仅使用数据的基元表示形式可能会导致错误地分配不正确的值！</span><span class="sxs-lookup"><span data-stu-id="da09e-169">However, using only the primitive representation of the data can result in mistakenly assigning an incorrect value!</span></span>  <span data-ttu-id="da09e-170">将每种类型的信息表示为不同的单用例联合可在这种情况下强制执行正确性。</span><span class="sxs-lookup"><span data-stu-id="da09e-170">Representing each type of information as a distinct single-case union can enforce correctness in this scenario.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

<span data-ttu-id="da09e-171">如上面的示例所示，若要获取单个用例可区分联合的基础值，必须将其显式解包。</span><span class="sxs-lookup"><span data-stu-id="da09e-171">As the above sample demonstrates, to get the underlying value in a single-case Discriminated Union, you must explicitly unwrap it.</span></span>

<span data-ttu-id="da09e-172">此外，Du 还支持递归定义，使你能够轻松地表示树和本质上递归的数据。</span><span class="sxs-lookup"><span data-stu-id="da09e-172">Additionally, DUs also support recursive definitions, allowing you to easily represent trees and inherently recursive data.</span></span>  <span data-ttu-id="da09e-173">例如，下面介绍了如何使用和函数表示二元搜索树 `exists` `insert` 。</span><span class="sxs-lookup"><span data-stu-id="da09e-173">For example, here's how you can represent a Binary Search Tree with `exists` and `insert` functions.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

<span data-ttu-id="da09e-174">由于 Du 允许您在数据类型中表示树的递归结构，因此，对此递归结构进行操作非常简单，并且保证正确性。</span><span class="sxs-lookup"><span data-stu-id="da09e-174">Because DUs allow you to represent the recursive structure of the tree in the data type, operating on this recursive structure is straightforward and guarantees correctness.</span></span>  <span data-ttu-id="da09e-175">它还支持模式匹配，如下所示。</span><span class="sxs-lookup"><span data-stu-id="da09e-175">It is also supported in pattern matching, as shown below.</span></span>

<span data-ttu-id="da09e-176">此外，还可以将 Du 表示为 `struct` 具有 `[<Struct>]` 属性的：</span><span class="sxs-lookup"><span data-stu-id="da09e-176">Additionally, you can represent DUs as `struct`s with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

<span data-ttu-id="da09e-177">但是，在执行此操作时，请记住以下两个重要事项：</span><span class="sxs-lookup"><span data-stu-id="da09e-177">However, there are two key things to keep in mind when doing so:</span></span>

1. <span data-ttu-id="da09e-178">不能以递归方式定义结构 DU。</span><span class="sxs-lookup"><span data-stu-id="da09e-178">A struct DU cannot be recursively-defined.</span></span>
2. <span data-ttu-id="da09e-179">结构 DU 的每个事例都必须具有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="da09e-179">A struct DU must have unique names for each of its cases.</span></span>

<span data-ttu-id="da09e-180">如果未遵循上述操作，则会导致编译错误。</span><span class="sxs-lookup"><span data-stu-id="da09e-180">Failure to follow the above will result in a compilation error.</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="da09e-181">模式匹配</span><span class="sxs-lookup"><span data-stu-id="da09e-181">Pattern Matching</span></span>

<span data-ttu-id="da09e-182">[模式匹配](./language-reference/pattern-matching.md) 是 f # 语言功能，可实现对 f # 类型的操作的正确性。</span><span class="sxs-lookup"><span data-stu-id="da09e-182">[Pattern Matching](./language-reference/pattern-matching.md) is the F# language feature which enables correctness for operating on F# types.</span></span>  <span data-ttu-id="da09e-183">在上述示例中，您可能注意到了相当多的 `match x with ...` 语法。</span><span class="sxs-lookup"><span data-stu-id="da09e-183">In the above samples, you probably noticed quite a bit of `match x with ...` syntax.</span></span>  <span data-ttu-id="da09e-184">此构造允许编译器（可以理解数据类型的 "形状"）强制你考虑使用数据类型（通过所谓的 "完全模式匹配"）时的所有可能情况。</span><span class="sxs-lookup"><span data-stu-id="da09e-184">This construct allows the compiler, which can understand the "shape" of data types, to force you to account for all possible cases when using a data type through what is known as Exhaustive Pattern Matching.</span></span>  <span data-ttu-id="da09e-185">这是非常强大的功能，可以巧妙用于 "提升" 通常是运行时问题的编译时问题。</span><span class="sxs-lookup"><span data-stu-id="da09e-185">This is incredibly powerful for correctness, and can be cleverly used to "lift" what would normally be a runtime concern into compile-time.</span></span>

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

<span data-ttu-id="da09e-186">你可能注意到的是使用 `_` 模式。</span><span class="sxs-lookup"><span data-stu-id="da09e-186">Something you may have noticed is the use of the `_` pattern.</span></span>  <span data-ttu-id="da09e-187">这称为 [通配符模式](./language-reference/pattern-matching.md#wildcard-pattern)，这是一种 "我不在意什么内容" 的方法。</span><span class="sxs-lookup"><span data-stu-id="da09e-187">This is known as the [Wildcard Pattern](./language-reference/pattern-matching.md#wildcard-pattern), which is a way of saying "I don't care what something is".</span></span>  <span data-ttu-id="da09e-188">尽管很方便，但如果不小心使用，则可能会意外绕过穷举模式匹配，并且不再受益于编译时操作 `_` 。</span><span class="sxs-lookup"><span data-stu-id="da09e-188">Although convenient, you can accidentally bypass Exhaustive Pattern Matching and no longer benefit from compile-time enforcements if you aren't careful in using `_`.</span></span>  <span data-ttu-id="da09e-189">当您在模式匹配时不关心分解类型的某些部分时，最好使用此方法; 当您枚举了模式匹配表达式中的所有有意义的事例时，最好使用该方法。</span><span class="sxs-lookup"><span data-stu-id="da09e-189">It is best used when you don't care about certain pieces of a decomposed type when pattern matching, or the final clause when you have enumerated all meaningful cases in a pattern matching expression.</span></span>

<span data-ttu-id="da09e-190">在下面的示例中， `_` 分析操作失败时使用事例。</span><span class="sxs-lookup"><span data-stu-id="da09e-190">In the following example, the `_` case is used when a parse operation fails.</span></span>

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L744-L762)]

<span data-ttu-id="da09e-191">[活动模式](./language-reference/active-patterns.md) 是另一个功能强大的构造，可与模式匹配一起使用。</span><span class="sxs-lookup"><span data-stu-id="da09e-191">[Active Patterns](./language-reference/active-patterns.md) are another powerful construct to use with pattern matching.</span></span>  <span data-ttu-id="da09e-192">它们允许您将输入数据分区为自定义窗体，并在模式匹配调用站点分解它们。</span><span class="sxs-lookup"><span data-stu-id="da09e-192">They allow you to partition input data into custom forms, decomposing them at the pattern match call site.</span></span>  <span data-ttu-id="da09e-193">它们也可以参数化，从而允许将分区定义为函数。</span><span class="sxs-lookup"><span data-stu-id="da09e-193">They can also be parameterized, thus allowing to define the partition as a function.</span></span>  <span data-ttu-id="da09e-194">扩展前面的示例以支持活动模式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="da09e-194">Expanding the previous example to support Active Patterns looks something like this:</span></span>

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a><span data-ttu-id="da09e-195">可选类型</span><span class="sxs-lookup"><span data-stu-id="da09e-195">Optional Types</span></span>

<span data-ttu-id="da09e-196">可区分联合类型的一种特殊情况是 "选项类型"，它非常有用，因为它是 F # 核心库的一部分。</span><span class="sxs-lookup"><span data-stu-id="da09e-196">One special case of Discriminated Union types is the Option Type, which is so useful that it's a part of the F# core library.</span></span>

<span data-ttu-id="da09e-197">[选项类型](./language-reference/options.md) 是一种类型，该类型表示以下两种情况之一：值或根本不显示任何内容。</span><span class="sxs-lookup"><span data-stu-id="da09e-197">[The Option Type](./language-reference/options.md) is a type which represents one of two cases: a value, or nothing at all.</span></span>  <span data-ttu-id="da09e-198">它用于某个值可能因特定操作而不会产生的任何情况。</span><span class="sxs-lookup"><span data-stu-id="da09e-198">It is used in any scenario where a value may or may not result from a particular operation.</span></span>  <span data-ttu-id="da09e-199">这会强制你考虑这两种情况，使其成为编译时问题，而不是运行时问题。</span><span class="sxs-lookup"><span data-stu-id="da09e-199">This then forces you to account for both cases, making it a compile-time concern rather than a runtime concern.</span></span>  <span data-ttu-id="da09e-200">这通常用于 Api 中，其中 `null` 用于表示 "无"，从而避免了 `NullReferenceException` 在许多情况下需要担心的情况。</span><span class="sxs-lookup"><span data-stu-id="da09e-200">These are often used in APIs where `null` is used to represent "nothing" instead, thus eliminating the need to worry about `NullReferenceException` in many circumstances.</span></span>

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a><span data-ttu-id="da09e-201">度量单位</span><span class="sxs-lookup"><span data-stu-id="da09e-201">Units of Measure</span></span>

<span data-ttu-id="da09e-202">F # 类型系统的一项独特功能是能够通过度量单位为数字文本提供上下文。</span><span class="sxs-lookup"><span data-stu-id="da09e-202">One unique feature of F#'s type system is the ability to provide context for numeric literals through Units of Measure.</span></span>

<span data-ttu-id="da09e-203">[度量单位](./language-reference/units-of-measure.md) 允许您将数值类型与单位（例如计量）相关联，并使函数可对单元（而不是数字文本）执行工作。</span><span class="sxs-lookup"><span data-stu-id="da09e-203">[Units of Measure](./language-reference/units-of-measure.md) allow you to associate a numeric type to a unit, such as Meters, and have functions perform work on units rather than numeric literals.</span></span>  <span data-ttu-id="da09e-204">这使编译器能够验证传入的数值类型在特定上下文中是否有效，从而消除了与此类工作相关的运行时错误。</span><span class="sxs-lookup"><span data-stu-id="da09e-204">This enables the compiler to verify that the types of numeric literals passed in make sense under a certain context, thus eliminating runtime errors associated with that kind of work.</span></span>

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

<span data-ttu-id="da09e-205">F # 核心库定义了许多 SI 单元类型和单位转换。</span><span class="sxs-lookup"><span data-stu-id="da09e-205">The F# Core library defines many SI unit types and unit conversions.</span></span>  <span data-ttu-id="da09e-206">若要了解详细信息，请查看 [UnitSystems 命名空间 fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitsymbols.html)。</span><span class="sxs-lookup"><span data-stu-id="da09e-206">To learn more, check out the [FSharp.Data.UnitSystems.SI.UnitSymbols Namespace](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitsymbols.html).</span></span>

## <a name="classes-and-interfaces"></a><span data-ttu-id="da09e-207">类和接口</span><span class="sxs-lookup"><span data-stu-id="da09e-207">Classes and Interfaces</span></span>

<span data-ttu-id="da09e-208">F # 还对 .NET 类、 [接口](./language-reference/interfaces.md)、 [抽象类](./language-reference/abstract-classes.md)、 [继承](./language-reference/inheritance.md)等提供完全支持。</span><span class="sxs-lookup"><span data-stu-id="da09e-208">F# also has full support for .NET classes, [Interfaces](./language-reference/interfaces.md), [Abstract Classes](./language-reference/abstract-classes.md), [Inheritance](./language-reference/inheritance.md), and so on.</span></span>

<span data-ttu-id="da09e-209">[类](./language-reference/classes.md) 是表示 .net 对象的类型，这些对象可以具有属性、方法和事件作为其 [成员](./language-reference/members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="da09e-209">[Classes](./language-reference/classes.md) are types that represent .NET objects, which can have properties, methods, and events as its [Members](./language-reference/members/index.md).</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

<span data-ttu-id="da09e-210">定义泛型类也非常简单。</span><span class="sxs-lookup"><span data-stu-id="da09e-210">Defining generic classes is also very straightforward.</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

<span data-ttu-id="da09e-211">若要实现接口，可以使用 `interface ... with` 语法或 [对象表达式](./language-reference/object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="da09e-211">To implement an Interface, you can use either `interface ... with` syntax or an [Object Expression](./language-reference/object-expressions.md).</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a><span data-ttu-id="da09e-212">要使用的类型</span><span class="sxs-lookup"><span data-stu-id="da09e-212">Which Types to Use</span></span>

<span data-ttu-id="da09e-213">类、记录、可区分联合和元组的存在导致了重要问题：应使用哪一个？</span><span class="sxs-lookup"><span data-stu-id="da09e-213">The presence of Classes, Records, Discriminated Unions, and Tuples leads to an important question: which should you use?</span></span>  <span data-ttu-id="da09e-214">与生活中的大多数操作一样，答案取决于你的情况。</span><span class="sxs-lookup"><span data-stu-id="da09e-214">Like most everything in life, the answer depends on your circumstances.</span></span>

<span data-ttu-id="da09e-215">元组非常适合从函数返回多个值，并使用临时值聚合作为值本身。</span><span class="sxs-lookup"><span data-stu-id="da09e-215">Tuples are great for returning multiple values from a function, and using an ad-hoc aggregate of values as a value itself.</span></span>

<span data-ttu-id="da09e-216">记录是元组中的 "单步执行"，其命名标签和对可选成员的支持。</span><span class="sxs-lookup"><span data-stu-id="da09e-216">Records are a "step up" from Tuples, having named labels and support for optional members.</span></span>  <span data-ttu-id="da09e-217">它们非常适用于通过您的程序传输的数据的低计划表示形式。</span><span class="sxs-lookup"><span data-stu-id="da09e-217">They are great for a low-ceremony representation of data in-transit through your program.</span></span>  <span data-ttu-id="da09e-218">由于它们具有结构相等性，因此它们可用于比较。</span><span class="sxs-lookup"><span data-stu-id="da09e-218">Because they have structural equality, they are easy to use with comparison.</span></span>

<span data-ttu-id="da09e-219">可区分联合具有许多用途，但核心好处是能够将它们与模式匹配一起使用，以考虑数据可以具有的所有可能的 "形状"。</span><span class="sxs-lookup"><span data-stu-id="da09e-219">Discriminated Unions have many uses, but the core benefit is to be able to utilize them in conjunction with Pattern Matching to account for all possible "shapes" that a data can have.</span></span>  

<span data-ttu-id="da09e-220">类对于大量原因非常有用，例如，当你需要表示信息并将该信息绑定到功能时。</span><span class="sxs-lookup"><span data-stu-id="da09e-220">Classes are great for a huge number of reasons, such as when you need to represent information and also tie that information to functionality.</span></span>  <span data-ttu-id="da09e-221">作为经验法则，当你具有在概念上与某些数据关联的功能时，使用类和面向对象编程的原则是一项巨大的好处。</span><span class="sxs-lookup"><span data-stu-id="da09e-221">As a rule of thumb, when you have functionality which is conceptually tied to some data, using Classes and the principles of Object-Oriented Programming is a big benefit.</span></span>  <span data-ttu-id="da09e-222">与 c # 和 Visual Basic 进行互操作时，类也是首选的数据类型，因为这些语言几乎都使用类。</span><span class="sxs-lookup"><span data-stu-id="da09e-222">Classes are also the preferred data type when interoperating with C# and Visual Basic, as these languages use classes for nearly everything.</span></span>

## <a name="next-steps"></a><span data-ttu-id="da09e-223">后续步骤</span><span class="sxs-lookup"><span data-stu-id="da09e-223">Next Steps</span></span>

<span data-ttu-id="da09e-224">现在，您已了解了该语言的一些主要功能，您应该准备好编写您的第一个 F # 程序！</span><span class="sxs-lookup"><span data-stu-id="da09e-224">Now that you've seen some of the primary features of the language, you should be ready to write your first F# programs!</span></span>  <span data-ttu-id="da09e-225">请查看 [入门](get-started/index.md) ，了解如何设置开发环境并编写一些代码。</span><span class="sxs-lookup"><span data-stu-id="da09e-225">Check out [Getting Started](get-started/index.md) to learn how to set up your development environment and write some code.</span></span>

<span data-ttu-id="da09e-226">了解详细信息的后续步骤可以是你喜欢的任何内容，但建议 [在 F # 中介绍函数编程](./introduction-to-functional-programming/index.md) ，以熟悉核心功能编程概念。</span><span class="sxs-lookup"><span data-stu-id="da09e-226">The next steps for learning more can be whatever you like, but we recommend [Introduction to Functional Programming in F#](./introduction-to-functional-programming/index.md) to get comfortable with core Functional Programming concepts.</span></span>  <span data-ttu-id="da09e-227">在 F # 中构建可靠的程序时，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="da09e-227">These will be essential in building robust programs in F#.</span></span>

<span data-ttu-id="da09e-228">另外，请查看 [f # 语言参考](./language-reference/index.md) ，查看 f # 上的概念内容的完整集合。</span><span class="sxs-lookup"><span data-stu-id="da09e-228">Also, check out the [F# Language Reference](./language-reference/index.md) to see a comprehensive collection of conceptual content on F#.</span></span>
