---
title: 递归函数：rec 关键字
description: '了解如何使用 F # "rec" 关键字来定义递归函数。'
ms.date: 05/16/2016
ms.openlocfilehash: c2374f90b4585327c6f5208a3d6bca75a23d0cbb
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455653"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="68bd8-103">递归函数：rec 关键字</span><span class="sxs-lookup"><span data-stu-id="68bd8-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="68bd8-104">`rec`关键字与关键字一起用于 `let` 定义递归函数。</span><span class="sxs-lookup"><span data-stu-id="68bd8-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="68bd8-105">语法</span><span class="sxs-lookup"><span data-stu-id="68bd8-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="68bd8-106">备注</span><span class="sxs-lookup"><span data-stu-id="68bd8-106">Remarks</span></span>

<span data-ttu-id="68bd8-107">递归函数（调用自身的函数）在 F # 语言中显式标识。</span><span class="sxs-lookup"><span data-stu-id="68bd8-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="68bd8-108">这会使正在定义的标识符在函数作用域内可用。</span><span class="sxs-lookup"><span data-stu-id="68bd8-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="68bd8-109">下面的代码演示了一个使用数学定义计算*n*<sup>第</sup>n 个斐波那契数的递归函数。</span><span class="sxs-lookup"><span data-stu-id="68bd8-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="68bd8-110">实际上，与上一示例类似的代码并不理想，因为它 unecessarily 已计算的重新计算值。</span><span class="sxs-lookup"><span data-stu-id="68bd8-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="68bd8-111">这是因为它不是尾递归，本文对此进行了进一步说明。</span><span class="sxs-lookup"><span data-stu-id="68bd8-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="68bd8-112">方法在类型内隐式递归;无需添加 `rec` 关键字。</span><span class="sxs-lookup"><span data-stu-id="68bd8-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="68bd8-113">类中的 Let 绑定不隐式递归。</span><span class="sxs-lookup"><span data-stu-id="68bd8-113">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="68bd8-114">结尾递归</span><span class="sxs-lookup"><span data-stu-id="68bd8-114">Tail recursion</span></span>

<span data-ttu-id="68bd8-115">对于某些递归函数，必须将更多 "纯" 定义重构为[尾递归](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)。</span><span class="sxs-lookup"><span data-stu-id="68bd8-115">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="68bd8-116">这可以防止不必要的 recomputations。</span><span class="sxs-lookup"><span data-stu-id="68bd8-116">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="68bd8-117">例如，可以按如下所示重写上一个波那契数字生成器：</span><span class="sxs-lookup"><span data-stu-id="68bd8-117">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="68bd8-118">这是一个更复杂的实现。</span><span class="sxs-lookup"><span data-stu-id="68bd8-118">This is a more complicated implementation.</span></span> <span data-ttu-id="68bd8-119">生成波那契数字是 "简单" 算法的一个很好的示例，它在数学上纯粹简单，但实际上是低效的。</span><span class="sxs-lookup"><span data-stu-id="68bd8-119">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="68bd8-120">在 F # 中，有几个方面使其效率更高，同时仍以递归方式定义：</span><span class="sxs-lookup"><span data-stu-id="68bd8-120">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="68bd8-121">名为的递归内部函数 `loop` ，它是一个惯用 F # 模式。</span><span class="sxs-lookup"><span data-stu-id="68bd8-121">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="68bd8-122">将累积值传递到递归调用的两个累加器参数。</span><span class="sxs-lookup"><span data-stu-id="68bd8-122">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="68bd8-123">对的值 `n` 进行检查以返回特定的累计。</span><span class="sxs-lookup"><span data-stu-id="68bd8-123">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="68bd8-124">如果此示例是用循环迭代编写的，则在满足特定条件之前，代码将类似于两个不同的值累积号。</span><span class="sxs-lookup"><span data-stu-id="68bd8-124">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="68bd8-125">这是结尾递归的原因是因为递归调用不需要在调用堆栈上保存任何值。</span><span class="sxs-lookup"><span data-stu-id="68bd8-125">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="68bd8-126">所有计算的中间值都将通过输入累积到内部函数。</span><span class="sxs-lookup"><span data-stu-id="68bd8-126">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="68bd8-127">这也允许 F # 编译器优化代码，就像编写了像循环一样快 `while` 。</span><span class="sxs-lookup"><span data-stu-id="68bd8-127">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="68bd8-128">如前面的示例所示，编写以递归方式处理与内部和外部函数有关的内容的 F # 代码是很常见的。</span><span class="sxs-lookup"><span data-stu-id="68bd8-128">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="68bd8-129">内部函数使用尾递归，而外部函数具有更好的调用方接口。</span><span class="sxs-lookup"><span data-stu-id="68bd8-129">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="68bd8-130">相互递归函数</span><span class="sxs-lookup"><span data-stu-id="68bd8-130">Mutually Recursive Functions</span></span>

<span data-ttu-id="68bd8-131">有时，函数是*相互递归*的，这意味着，调用会形成一个圆圈，其中一个函数调用另一个函数，而后者又调用第一个，并在之间进行任意数量的调用。</span><span class="sxs-lookup"><span data-stu-id="68bd8-131">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="68bd8-132">必须在一个绑定中一起定义此类函数 `let` ，使用 `and` 关键字将它们链接在一起。</span><span class="sxs-lookup"><span data-stu-id="68bd8-132">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="68bd8-133">下面的示例演示两个相互递归函数。</span><span class="sxs-lookup"><span data-stu-id="68bd8-133">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="68bd8-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="68bd8-134">See also</span></span>

- [<span data-ttu-id="68bd8-135">函数</span><span class="sxs-lookup"><span data-stu-id="68bd8-135">Functions</span></span>](index.md)
