---
title: 重载过程注意事项
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: c4075c87df8b9daa56ca1d35e0d6661598895fdc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403364"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="1edbd-102">重载过程注意事项 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1edbd-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="1edbd-103">重载过程时，必须为每个重载版本使用不同的*签名*。</span><span class="sxs-lookup"><span data-stu-id="1edbd-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="1edbd-104">这通常意味着每个版本都必须指定不同的参数列表。</span><span class="sxs-lookup"><span data-stu-id="1edbd-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="1edbd-105">有关详细信息，请参阅[过程重载](./procedure-overloading.md)中的 "不同签名"。</span><span class="sxs-lookup"><span data-stu-id="1edbd-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="1edbd-106">如果过程具有不同的签名，则可以 `Function` 使用过程重载过程 `Sub` ，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="1edbd-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="1edbd-107">两个重载只能不同于有一个返回值，而另一个没有返回值。</span><span class="sxs-lookup"><span data-stu-id="1edbd-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="1edbd-108">您可以重载属性，方法与重载过程的方法相同，并且具有相同的限制。</span><span class="sxs-lookup"><span data-stu-id="1edbd-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="1edbd-109">但是，不能使用属性重载过程，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="1edbd-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="1edbd-110">重载版本的替代项</span><span class="sxs-lookup"><span data-stu-id="1edbd-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="1edbd-111">有时会有一些重载版本的替代方法，特别是在有可选参数时，或参数的数目是可变的。</span><span class="sxs-lookup"><span data-stu-id="1edbd-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="1edbd-112">请记住，可选参数并不一定支持所有语言，参数数组仅限 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="1edbd-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="1edbd-113">如果要编写的过程可能会从用多种不同语言的任意语言编写的代码中调用，则重载版本提供最大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="1edbd-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="1edbd-114">重载和可选参数</span><span class="sxs-lookup"><span data-stu-id="1edbd-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="1edbd-115">如果调用代码可以选择提供或忽略一个或多个参数，则可以定义多个重载版本或使用可选参数。</span><span class="sxs-lookup"><span data-stu-id="1edbd-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="1edbd-116">何时使用重载版本</span><span class="sxs-lookup"><span data-stu-id="1edbd-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="1edbd-117">可以考虑在以下情况下定义一系列重载版本：</span><span class="sxs-lookup"><span data-stu-id="1edbd-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="1edbd-118">过程代码中的逻辑明显不同，具体取决于调用代码是否提供可选参数。</span><span class="sxs-lookup"><span data-stu-id="1edbd-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="1edbd-119">过程代码无法可靠地测试调用代码是否提供了可选参数。</span><span class="sxs-lookup"><span data-stu-id="1edbd-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="1edbd-120">例如，如果不能提供调用代码预期无法提供的默认值，则会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="1edbd-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="1edbd-121">何时使用可选参数</span><span class="sxs-lookup"><span data-stu-id="1edbd-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="1edbd-122">在以下情况下，你可能更倾向于使用一个或多个可选参数：</span><span class="sxs-lookup"><span data-stu-id="1edbd-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="1edbd-123">调用代码未提供可选参数时唯一必需的操作是将参数设置为默认值。</span><span class="sxs-lookup"><span data-stu-id="1edbd-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="1edbd-124">在这种情况下，如果使用一个或多个参数定义单个版本，则过程代码可能会比较复杂 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="1edbd-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="1edbd-125">有关详细信息，请参阅[可选参数](./optional-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="1edbd-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="1edbd-126">重载和 ParamArrays</span><span class="sxs-lookup"><span data-stu-id="1edbd-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="1edbd-127">当调用代码可以传递可变数量的参数时，可以定义多个重载版本或使用参数数组。</span><span class="sxs-lookup"><span data-stu-id="1edbd-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="1edbd-128">何时使用重载版本</span><span class="sxs-lookup"><span data-stu-id="1edbd-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="1edbd-129">可以考虑在以下情况下定义一系列重载版本：</span><span class="sxs-lookup"><span data-stu-id="1edbd-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="1edbd-130">您知道，调用代码永远不会向参数数组传递超过少量的值。</span><span class="sxs-lookup"><span data-stu-id="1edbd-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="1edbd-131">过程代码中的逻辑明显不同，具体取决于调用代码传递的值的数量。</span><span class="sxs-lookup"><span data-stu-id="1edbd-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="1edbd-132">调用代码可以传递不同数据类型的值。</span><span class="sxs-lookup"><span data-stu-id="1edbd-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="1edbd-133">何时使用参数数组</span><span class="sxs-lookup"><span data-stu-id="1edbd-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="1edbd-134">在以下情况下，你可以更好地处理 `ParamArray` 参数：</span><span class="sxs-lookup"><span data-stu-id="1edbd-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="1edbd-135">您无法预测调用代码可传递给参数数组的值数量，并且它可能是一个较大的数值。</span><span class="sxs-lookup"><span data-stu-id="1edbd-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="1edbd-136">过程逻辑适合于循环访问调用代码所通过的所有值，实际上对每个值执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="1edbd-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="1edbd-137">有关详细信息，请参阅[参数数组](./parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="1edbd-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="1edbd-138">可选参数的隐式重载</span><span class="sxs-lookup"><span data-stu-id="1edbd-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="1edbd-139">带有[可选](../../../language-reference/modifiers/optional.md)参数的过程等效于两个重载过程，其中一个参数具有可选参数，一个参数不包含它。</span><span class="sxs-lookup"><span data-stu-id="1edbd-139">A procedure with an [Optional](../../../language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="1edbd-140">不能使用与上述任一方法对应的参数列表重载此类过程。</span><span class="sxs-lookup"><span data-stu-id="1edbd-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="1edbd-141">以下声明阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="1edbd-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="1edbd-142">对于具有多个可选参数的过程，有一组隐式重载，它们与前面示例中的逻辑类似。</span><span class="sxs-lookup"><span data-stu-id="1edbd-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="1edbd-143">ParamArray 参数的隐式重载</span><span class="sxs-lookup"><span data-stu-id="1edbd-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="1edbd-144">编译器将具有[ParamArray](../../../language-reference/modifiers/paramarray.md)参数的过程视为具有无限数目的重载，这些重载在调用代码传递给参数数组的内容中彼此不同，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1edbd-144">The compiler considers a procedure with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="1edbd-145">调用代码未向以下项提供参数时的一个重载`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="1edbd-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="1edbd-146">如果调用代码提供一维元素类型的数组，则为一个重载 `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="1edbd-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="1edbd-147">对于每个正整数，调用代码提供该数量的参数的重载，每个 `ParamArray` 元素类型</span><span class="sxs-lookup"><span data-stu-id="1edbd-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="1edbd-148">以下声明阐释了这些隐式重载。</span><span class="sxs-lookup"><span data-stu-id="1edbd-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="1edbd-149">不能使用参数列表重载此类过程，该参数列表采用一维数组作为参数数组。</span><span class="sxs-lookup"><span data-stu-id="1edbd-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="1edbd-150">但是，可以使用其他隐式重载的签名。</span><span class="sxs-lookup"><span data-stu-id="1edbd-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="1edbd-151">以下声明阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="1edbd-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="1edbd-152">作为重载替代的替代方法</span><span class="sxs-lookup"><span data-stu-id="1edbd-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="1edbd-153">如果要允许调用代码将不同数据类型传递给参数，则可以使用一种无类型编程方法。</span><span class="sxs-lookup"><span data-stu-id="1edbd-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="1edbd-154">你可以将类型检查开关设置为， `Off` 同时[选择 Option Strict 语句](../../../language-reference/statements/option-strict-statement.md)或[-optionstrict](../../../reference/command-line-compiler/optionstrict.md)编译器选项。</span><span class="sxs-lookup"><span data-stu-id="1edbd-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="1edbd-155">然后不必声明参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="1edbd-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="1edbd-156">不过，与重载相比，此方法具有以下缺点：</span><span class="sxs-lookup"><span data-stu-id="1edbd-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="1edbd-157">无程序编程产生的执行代码效率较低。</span><span class="sxs-lookup"><span data-stu-id="1edbd-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="1edbd-158">此过程必须测试其预期要传递的每个数据类型。</span><span class="sxs-lookup"><span data-stu-id="1edbd-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="1edbd-159">如果调用代码传递了过程不支持的数据类型，则编译器无法发出错误信号。</span><span class="sxs-lookup"><span data-stu-id="1edbd-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1edbd-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1edbd-160">See also</span></span>

- [<span data-ttu-id="1edbd-161">过程</span><span class="sxs-lookup"><span data-stu-id="1edbd-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1edbd-162">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="1edbd-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1edbd-163">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="1edbd-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="1edbd-164">如何：定义一个过程的多个版本</span><span class="sxs-lookup"><span data-stu-id="1edbd-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="1edbd-165">如何：调用重载过程</span><span class="sxs-lookup"><span data-stu-id="1edbd-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="1edbd-166">如何：重载带有可选参数的过程</span><span class="sxs-lookup"><span data-stu-id="1edbd-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="1edbd-167">如何：重载参数数量不确定的过程</span><span class="sxs-lookup"><span data-stu-id="1edbd-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="1edbd-168">重载决策</span><span class="sxs-lookup"><span data-stu-id="1edbd-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="1edbd-169">重载</span><span class="sxs-lookup"><span data-stu-id="1edbd-169">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
