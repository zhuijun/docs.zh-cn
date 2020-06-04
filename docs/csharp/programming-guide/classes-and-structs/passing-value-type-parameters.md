---
title: 传递值类型参数 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: 13982254922d72337feeb502d2c84ebb42cf27bb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004551"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a><span data-ttu-id="dbaa3-102">传递值类型参数（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="dbaa3-102">Passing Value-Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="dbaa3-103">一个[值类型](../../language-reference/builtin-types/value-types.md)变量包含它直接与[引用类型](../../language-reference/keywords/reference-types.md)变量相对的数据，其中包含对其数据的引用。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-103">A [value-type](../../language-reference/builtin-types/value-types.md) variable contains its data directly as opposed to a [reference-type](../../language-reference/keywords/reference-types.md) variable, which contains a reference to its data.</span></span> <span data-ttu-id="dbaa3-104">按值将值-类型变量传递给方法，意味着将变量副本传递给该方法。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-104">Passing a value-type variable to a method by value means passing a copy of the variable to the method.</span></span> <span data-ttu-id="dbaa3-105">在方法内发生的对该实参进行的任何更改都不会影响存储在形参变量中的原始数据。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-105">Any changes to the parameter that take place inside the method have no effect on the original data stored in the argument variable.</span></span> <span data-ttu-id="dbaa3-106">若要使用已调用的方法来更改参数值，必须使用 [ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 关键字通过引用传递它。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-106">If you want the called method to change the value of the argument, you must pass it by reference, using the [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) keyword.</span></span> <span data-ttu-id="dbaa3-107">还可以使用 [in](../../language-reference/keywords/in-parameter-modifier.md) 关键字来按引用传递值参数，以避免复制并同时保证不更改值。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-107">You may also use the [in](../../language-reference/keywords/in-parameter-modifier.md) keyword to pass a value parameter by reference to avoid the copy while guaranteeing that the value will not be changed.</span></span> <span data-ttu-id="dbaa3-108">为简单起见，下面的示例使用 `ref`。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-108">For simplicity, the following examples use `ref`.</span></span>  
  
## <a name="passing-value-types-by-value"></a><span data-ttu-id="dbaa3-109">按值传递值类型</span><span class="sxs-lookup"><span data-stu-id="dbaa3-109">Passing Value Types by Value</span></span>  
 <span data-ttu-id="dbaa3-110">下面的示例演示按值传递值-类型参数。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-110">The following example demonstrates passing value-type parameters by value.</span></span> <span data-ttu-id="dbaa3-111">变量 `n` 按值传递给方法 `SquareIt`。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-111">The variable `n` is passed by value to the method `SquareIt`.</span></span> <span data-ttu-id="dbaa3-112">在方法内发生的任何更改都不会影响该变量的原始值。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-112">Any changes that take place inside the method have no effect on the original value of the variable.</span></span>  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 <span data-ttu-id="dbaa3-113">变量 `n` 是值类型。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-113">The variable `n` is a value type.</span></span> <span data-ttu-id="dbaa3-114">它包含其数据，值为 `5`。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-114">It contains its data, the value `5`.</span></span> <span data-ttu-id="dbaa3-115">调用 `SquareIt` 时，`n` 的内容复制到参数 `x` 中，这是该方法内的平方值。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-115">When `SquareIt` is invoked, the contents of `n` are copied into the parameter `x`, which is squared inside the method.</span></span> <span data-ttu-id="dbaa3-116">但是在 `Main` 中，`n` 的值在调用 `SquareIt` 方法之后与之前相同。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-116">In `Main`, however, the value of `n` is the same after calling the `SquareIt` method as it was before.</span></span> <span data-ttu-id="dbaa3-117">在方法内发生的更改只影响本地变量 `x`。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-117">The change that takes place inside the method only affects the local variable `x`.</span></span>  
  
## <a name="passing-value-types-by-reference"></a><span data-ttu-id="dbaa3-118">按引用传递值类型</span><span class="sxs-lookup"><span data-stu-id="dbaa3-118">Passing Value Types by Reference</span></span>  
 <span data-ttu-id="dbaa3-119">下面的示例与上述示例相同，除了自变量是作为 `ref` 参数传递的。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-119">The following example is the same as the previous example, except that the argument is passed as a `ref` parameter.</span></span> <span data-ttu-id="dbaa3-120">`x` 在方法中更改时，基础自变量的值 `n` 也更改。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-120">The value of the underlying argument, `n`, is changed when `x` is changed in the method.</span></span>  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 <span data-ttu-id="dbaa3-121">在此示例中，它传递的不是 `n` 的值；而是传递 `n` 的引用。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-121">In this example, it is not the value of `n` that is passed; rather, a reference to `n` is passed.</span></span> <span data-ttu-id="dbaa3-122">参数 `x` 不是 [int](../../language-reference/builtin-types/integral-numeric-types.md)；它是对 `int` 的引用，在这种情况下，是对 `n` 的引用。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-122">The parameter `x` is not an [int](../../language-reference/builtin-types/integral-numeric-types.md); it is a reference to an `int`, in this case, a reference to `n`.</span></span> <span data-ttu-id="dbaa3-123">因此，当 `x` 在方法中进行平方计算时，实际求平方值的就是 `x` 所指的 `n`。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-123">Therefore, when `x` is squared inside the method, what actually is squared is what `x` refers to, `n`.</span></span>  
  
## <a name="swapping-value-types"></a><span data-ttu-id="dbaa3-124">交换值类型</span><span class="sxs-lookup"><span data-stu-id="dbaa3-124">Swapping Value Types</span></span>  
 <span data-ttu-id="dbaa3-125">更改自变量值的一个常见示例是交换方法，其中将两个变量传递给方法，并由该方法交换其内容。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-125">A common example of changing the values of arguments is a swap method, where you pass two variables to the method, and the method swaps their contents.</span></span> <span data-ttu-id="dbaa3-126">必须通过引用将自变量传递给交换方法。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-126">You must pass the arguments to the swap method by reference.</span></span> <span data-ttu-id="dbaa3-127">否则，交换参数在方法中的本地副本，并且调用方法中不会发生更改。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-127">Otherwise, you swap local copies of the parameters inside the method, and no change occurs in the calling method.</span></span> <span data-ttu-id="dbaa3-128">下面的示例交换整数值。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-128">The following example swaps integer values.</span></span>  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 <span data-ttu-id="dbaa3-129">调用 `SwapByRef` 方法时，在调用中使用 `ref` 关键字，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="dbaa3-129">When you call the `SwapByRef` method, use the `ref` keyword in the call, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="dbaa3-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="dbaa3-130">See also</span></span>

- [<span data-ttu-id="dbaa3-131">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="dbaa3-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dbaa3-132">传递参数</span><span class="sxs-lookup"><span data-stu-id="dbaa3-132">Passing Parameters</span></span>](./passing-parameters.md)
- [<span data-ttu-id="dbaa3-133">传递引用类型参数</span><span class="sxs-lookup"><span data-stu-id="dbaa3-133">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)
