---
title: 如何：重载参数数量不确定的过程
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 10cd7d11b0efe9fa5eb3ae24269a4cdbe33bc08a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071542"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="9798e-102">如何：重载参数数量不确定的过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9798e-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>

<span data-ttu-id="9798e-103">如果过程具有 [ParamArray](../../../language-reference/modifiers/paramarray.md) 参数，则不能为参数数组定义采用一维数组的重载版本。</span><span class="sxs-lookup"><span data-stu-id="9798e-103">If a procedure has a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="9798e-104">有关详细信息，请参阅 [重载过程](./considerations-in-overloading-procedures.md)中的注意事项中的 "ParamArray 参数的隐式重载"。</span><span class="sxs-lookup"><span data-stu-id="9798e-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="9798e-105">重载采用可变数量的参数的过程</span><span class="sxs-lookup"><span data-stu-id="9798e-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="9798e-106">确定过程和调用代码逻辑从重载版本中受益于比参数更多 `ParamArray` 。</span><span class="sxs-lookup"><span data-stu-id="9798e-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="9798e-107">有关 [重载过程的注意事项](./considerations-in-overloading-procedures.md)，请参阅 "Overloads and ParamArrays"。</span><span class="sxs-lookup"><span data-stu-id="9798e-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="9798e-108">确定过程应在参数列表的变量部分中接受的所提供值的数量。</span><span class="sxs-lookup"><span data-stu-id="9798e-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="9798e-109">这可能包括无值的情况，还可能包括单个一维数组的大小写。</span><span class="sxs-lookup"><span data-stu-id="9798e-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="9798e-110">对于提供的每个可接受的值， `Sub` 编写 `Function` 定义相应参数列表的或声明语句。</span><span class="sxs-lookup"><span data-stu-id="9798e-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="9798e-111">不要 `Optional` `ParamArray` 在此重载版本中使用或关键字。</span><span class="sxs-lookup"><span data-stu-id="9798e-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="9798e-112">在每个声明中，在或关键字之前加上 `Sub` `Function` [Overloads](../../../language-reference/modifiers/overloads.md) 关键字。</span><span class="sxs-lookup"><span data-stu-id="9798e-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="9798e-113">遵循每个声明，编写调用代码提供与声明的参数列表对应的值时应执行的过程代码。</span><span class="sxs-lookup"><span data-stu-id="9798e-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="9798e-114">根据需要，用或语句终止每个过程 `End Sub` `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="9798e-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9798e-115">示例</span><span class="sxs-lookup"><span data-stu-id="9798e-115">Example</span></span>  

 <span data-ttu-id="9798e-116">下面的示例演示了一个使用 [ParamArray](../../../language-reference/modifiers/paramarray.md) 参数定义的过程，以及一个等效的重载过程集。</span><span class="sxs-lookup"><span data-stu-id="9798e-116">The following example shows a procedure defined with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="9798e-117">不能使用参数列表重载此类过程，该参数列表采用一维数组作为参数数组。</span><span class="sxs-lookup"><span data-stu-id="9798e-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="9798e-118">但是，可以使用其他隐式重载的签名。</span><span class="sxs-lookup"><span data-stu-id="9798e-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="9798e-119">以下声明阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="9798e-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="9798e-120">重载版本中的代码无需测试调用代码是否为参数提供了一个或多个值，如果有，则不需要测试 `ParamArray` 。</span><span class="sxs-lookup"><span data-stu-id="9798e-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="9798e-121">Visual Basic 将控制传递到与调用参数列表匹配的版本。</span><span class="sxs-lookup"><span data-stu-id="9798e-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="9798e-122">编译代码</span><span class="sxs-lookup"><span data-stu-id="9798e-122">Compile the code</span></span>  

 <span data-ttu-id="9798e-123">由于具有参数的过程 `ParamArray` 等效于一组重载版本，因此不能使用与任何这些隐式重载对应的参数列表重载此类过程。</span><span class="sxs-lookup"><span data-stu-id="9798e-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="9798e-124">有关详细信息，请参阅 [重载过程中的注意事项](./considerations-in-overloading-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="9798e-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9798e-125">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="9798e-125">.NET Framework Security</span></span>  

 <span data-ttu-id="9798e-126">无论何时处理可能会无限大的阵列，都有 overrunning 应用程序的一些内部容量的风险。</span><span class="sxs-lookup"><span data-stu-id="9798e-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="9798e-127">如果接受参数数组，则应测试调用代码传递给它的数组长度，如果该数组对您的应用程序而言太大，则采取适当的措施。</span><span class="sxs-lookup"><span data-stu-id="9798e-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9798e-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="9798e-128">See also</span></span>

- [<span data-ttu-id="9798e-129">过程</span><span class="sxs-lookup"><span data-stu-id="9798e-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9798e-130">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="9798e-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9798e-131">可选参数</span><span class="sxs-lookup"><span data-stu-id="9798e-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="9798e-132">参数数组</span><span class="sxs-lookup"><span data-stu-id="9798e-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="9798e-133">过程重载</span><span class="sxs-lookup"><span data-stu-id="9798e-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="9798e-134">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="9798e-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="9798e-135">如何：定义一个过程的多个版本</span><span class="sxs-lookup"><span data-stu-id="9798e-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="9798e-136">如何：调用重载过程</span><span class="sxs-lookup"><span data-stu-id="9798e-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="9798e-137">如何：重载带有可选参数的过程</span><span class="sxs-lookup"><span data-stu-id="9798e-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="9798e-138">重载决策</span><span class="sxs-lookup"><span data-stu-id="9798e-138">Overload Resolution</span></span>](./overload-resolution.md)
