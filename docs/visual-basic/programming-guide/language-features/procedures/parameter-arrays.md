---
title: 参数数组
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: dac0575d73ffd4159e89bff344915a33b9d0e5d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364274"
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="d0a19-102">参数数组 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0a19-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="d0a19-103">通常，使用的参数不能比过程声明指定的过程要多。</span><span class="sxs-lookup"><span data-stu-id="d0a19-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="d0a19-104">如果需要无数个参数，可以声明一个*参数数组*，该数组允许过程接受参数的值数组。</span><span class="sxs-lookup"><span data-stu-id="d0a19-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="d0a19-105">定义过程时，无需知道参数数组中的元素数目。</span><span class="sxs-lookup"><span data-stu-id="d0a19-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="d0a19-106">每次调用该过程时，都会单独确定数组大小。</span><span class="sxs-lookup"><span data-stu-id="d0a19-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="d0a19-107">声明 ParamArray</span><span class="sxs-lookup"><span data-stu-id="d0a19-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="d0a19-108">使用[ParamArray](../../../language-reference/modifiers/paramarray.md)关键字在参数列表中表示参数数组。</span><span class="sxs-lookup"><span data-stu-id="d0a19-108">You use the [ParamArray](../../../language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="d0a19-109">适用以下规则：</span><span class="sxs-lookup"><span data-stu-id="d0a19-109">The following rules apply:</span></span>  
  
- <span data-ttu-id="d0a19-110">一个过程只能定义一个参数数组，并且它必须是过程定义中的最后一个参数。</span><span class="sxs-lookup"><span data-stu-id="d0a19-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
- <span data-ttu-id="d0a19-111">必须通过值传递参数数组。</span><span class="sxs-lookup"><span data-stu-id="d0a19-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="d0a19-112">在过程定义中显式包含[ByVal](../../../language-reference/modifiers/byval.md)关键字是一种很好的编程做法。</span><span class="sxs-lookup"><span data-stu-id="d0a19-112">It is good programming practice to explicitly include the [ByVal](../../../language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
- <span data-ttu-id="d0a19-113">参数数组是自动可选的。</span><span class="sxs-lookup"><span data-stu-id="d0a19-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="d0a19-114">它的默认值是一个空的一维数组，它是参数数组的元素类型。</span><span class="sxs-lookup"><span data-stu-id="d0a19-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
- <span data-ttu-id="d0a19-115">参数数组前面的所有参数都必须是必需的。</span><span class="sxs-lookup"><span data-stu-id="d0a19-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="d0a19-116">参数数组必须是唯一的可选参数。</span><span class="sxs-lookup"><span data-stu-id="d0a19-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="d0a19-117">调用 ParamArray</span><span class="sxs-lookup"><span data-stu-id="d0a19-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="d0a19-118">调用定义参数数组的过程时，可以通过以下方式之一提供参数：</span><span class="sxs-lookup"><span data-stu-id="d0a19-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
- <span data-ttu-id="d0a19-119">无-也就是说，可以省略[ParamArray](../../../language-reference/modifiers/paramarray.md)参数。</span><span class="sxs-lookup"><span data-stu-id="d0a19-119">Nothing — that is, you can omit the [ParamArray](../../../language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="d0a19-120">在这种情况下，空数组将传递给该过程。</span><span class="sxs-lookup"><span data-stu-id="d0a19-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="d0a19-121">如果显式传递[Nothing](../../../language-reference/nothing.md)关键字，则空数组将传递给该过程，并且如果被调用的过程不检查此条件，则可能导致 NullReferenceException。</span><span class="sxs-lookup"><span data-stu-id="d0a19-121">If you explicitly pass the [Nothing](../../../language-reference/nothing.md) keyword, a null array is passed to the procedure and may result in a NullReferenceException if the called procedure does not check for this condition.</span></span>
  
- <span data-ttu-id="d0a19-122">任意数量的参数的列表（用逗号分隔）。</span><span class="sxs-lookup"><span data-stu-id="d0a19-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="d0a19-123">每个参数的数据类型必须可隐式转换为 `ParamArray` 元素类型。</span><span class="sxs-lookup"><span data-stu-id="d0a19-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
- <span data-ttu-id="d0a19-124">元素类型与参数数组的元素类型相同的数组。</span><span class="sxs-lookup"><span data-stu-id="d0a19-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="d0a19-125">在所有情况下，该过程中的代码将参数数组视为一维数组，其元素的数据类型与 `ParamArray` 数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="d0a19-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d0a19-126">无论何时处理可能会无限大的阵列，都有 overrunning 应用程序的一些内部容量的风险。</span><span class="sxs-lookup"><span data-stu-id="d0a19-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="d0a19-127">如果接受参数数组，则应测试调用代码传递给它的数组大小。</span><span class="sxs-lookup"><span data-stu-id="d0a19-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="d0a19-128">如果对应用程序来说太大，请采取适当的措施。</span><span class="sxs-lookup"><span data-stu-id="d0a19-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="d0a19-129">有关详细信息，请参阅 [array](../arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a19-129">For more information, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0a19-130">示例</span><span class="sxs-lookup"><span data-stu-id="d0a19-130">Example</span></span>  
 <span data-ttu-id="d0a19-131">下面的示例定义并调用函数 `calcSum` 。</span><span class="sxs-lookup"><span data-stu-id="d0a19-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="d0a19-132">`ParamArray`参数的修饰符 `args` 使函数接受数量可变的参数。</span><span class="sxs-lookup"><span data-stu-id="d0a19-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 <span data-ttu-id="d0a19-133">下面的示例使用参数数组定义过程，并输出传递给参数数组的所有数组元素的值。</span><span class="sxs-lookup"><span data-stu-id="d0a19-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a><span data-ttu-id="d0a19-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0a19-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="d0a19-135">过程</span><span class="sxs-lookup"><span data-stu-id="d0a19-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d0a19-136">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="d0a19-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d0a19-137">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="d0a19-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d0a19-138">按位置和按名称传递参数</span><span class="sxs-lookup"><span data-stu-id="d0a19-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="d0a19-139">可选参数</span><span class="sxs-lookup"><span data-stu-id="d0a19-139">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="d0a19-140">过程重载</span><span class="sxs-lookup"><span data-stu-id="d0a19-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="d0a19-141">数组</span><span class="sxs-lookup"><span data-stu-id="d0a19-141">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="d0a19-142">可选</span><span class="sxs-lookup"><span data-stu-id="d0a19-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
