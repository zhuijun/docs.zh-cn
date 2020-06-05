---
title: 过程形参和实参
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 178206ca2ee103bbdb5a4ac03bca0df903c8c5d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406711"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="ebccd-102">过程参数和自变量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebccd-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="ebccd-103">在大多数情况下，过程需要一些有关调用环境的信息。</span><span class="sxs-lookup"><span data-stu-id="ebccd-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="ebccd-104">执行重复或共享任务的过程对每个调用使用不同的信息。</span><span class="sxs-lookup"><span data-stu-id="ebccd-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="ebccd-105">此信息包含变量、常量和在您调用过程时传递给该过程的表达式。</span><span class="sxs-lookup"><span data-stu-id="ebccd-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="ebccd-106">*参数*表示一个值，该过程期望在调用时提供。</span><span class="sxs-lookup"><span data-stu-id="ebccd-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="ebccd-107">过程声明定义了其参数。</span><span class="sxs-lookup"><span data-stu-id="ebccd-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="ebccd-108">您可以定义没有参数、一个参数或多个参数的过程。</span><span class="sxs-lookup"><span data-stu-id="ebccd-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="ebccd-109">过程定义中指定参数的部分称为*参数列表*。</span><span class="sxs-lookup"><span data-stu-id="ebccd-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="ebccd-110">*参数*表示在调用过程时提供给过程参数的值。</span><span class="sxs-lookup"><span data-stu-id="ebccd-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="ebccd-111">调用代码在调用过程时提供自变量。</span><span class="sxs-lookup"><span data-stu-id="ebccd-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="ebccd-112">过程调用中指定参数的部分称为*参数列表*。</span><span class="sxs-lookup"><span data-stu-id="ebccd-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="ebccd-113">下图显示了 `safeSquareRoot` 从两个不同的位置调用过程的代码。</span><span class="sxs-lookup"><span data-stu-id="ebccd-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="ebccd-114">第一次调用将变量的值 `x` （4.0）传递给参数 `number` ，并将（2.0）中的返回值 `root` 分配给变量 `y` 。</span><span class="sxs-lookup"><span data-stu-id="ebccd-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="ebccd-115">第二个调用将文本值9.0 传递到 `number` ，并将返回值（3.0）分配给变量 `z` 。</span><span class="sxs-lookup"><span data-stu-id="ebccd-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 ![显示将参数传递给参数的关系图](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 <span data-ttu-id="ebccd-117">有关详细信息，请参阅[参数和参数之间的差异](./differences-between-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="ebccd-117">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="ebccd-118">参数数据类型</span><span class="sxs-lookup"><span data-stu-id="ebccd-118">Parameter Data Type</span></span>  
 <span data-ttu-id="ebccd-119">可以通过 `As` 在其声明中使用子句来定义参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ebccd-119">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="ebccd-120">例如，以下函数接受字符串和整数。</span><span class="sxs-lookup"><span data-stu-id="ebccd-120">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 <span data-ttu-id="ebccd-121">如果类型检查开关（[Option Strict 语句](../../../language-reference/statements/option-strict-statement.md)）是 `Off,` 可选的 `As` ，则该子句是可选的，但如果有任何一个参数使用它，则所有参数都必须使用它。</span><span class="sxs-lookup"><span data-stu-id="ebccd-121">If the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="ebccd-122">如果类型检查为 `On` ，则 `As` 所有过程参数都需要子句。</span><span class="sxs-lookup"><span data-stu-id="ebccd-122">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="ebccd-123">如果调用代码希望提供的参数的数据类型与其对应参数的数据类型不同（如 `Byte` `String` 参数），则必须执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="ebccd-123">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
- <span data-ttu-id="ebccd-124">仅提供数据类型扩大到参数数据类型的自变量;</span><span class="sxs-lookup"><span data-stu-id="ebccd-124">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
- <span data-ttu-id="ebccd-125">设置 `Option Strict Off` 为允许隐式收缩转换; 或</span><span class="sxs-lookup"><span data-stu-id="ebccd-125">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
- <span data-ttu-id="ebccd-126">使用转换关键字显式转换数据类型。</span><span class="sxs-lookup"><span data-stu-id="ebccd-126">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="ebccd-127">类型参数</span><span class="sxs-lookup"><span data-stu-id="ebccd-127">Type Parameters</span></span>  
 <span data-ttu-id="ebccd-128">*泛型过程*除了定义其正常参数外，还定义了一个或多个*类型参数*。</span><span class="sxs-lookup"><span data-stu-id="ebccd-128">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="ebccd-129">泛型过程允许调用代码在每次调用该过程时传递不同的数据类型，因此它可以根据每个调用的要求来定制数据类型。</span><span class="sxs-lookup"><span data-stu-id="ebccd-129">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="ebccd-130">请参阅 [Generic Procedures in Visual Basic](../data-types/generic-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="ebccd-130">See [Generic Procedures in Visual Basic](../data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebccd-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ebccd-131">See also</span></span>

- [<span data-ttu-id="ebccd-132">过程</span><span class="sxs-lookup"><span data-stu-id="ebccd-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ebccd-133">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="ebccd-133">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="ebccd-134">Function 过程</span><span class="sxs-lookup"><span data-stu-id="ebccd-134">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="ebccd-135">Property 过程</span><span class="sxs-lookup"><span data-stu-id="ebccd-135">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="ebccd-136">运算符过程</span><span class="sxs-lookup"><span data-stu-id="ebccd-136">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="ebccd-137">如何：为过程定义参数</span><span class="sxs-lookup"><span data-stu-id="ebccd-137">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="ebccd-138">如何：将参数传递给过程</span><span class="sxs-lookup"><span data-stu-id="ebccd-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="ebccd-139">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="ebccd-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="ebccd-140">过程重载</span><span class="sxs-lookup"><span data-stu-id="ebccd-140">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="ebccd-141">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="ebccd-141">Type Conversions in Visual Basic</span></span>](../data-types/type-conversions.md)
