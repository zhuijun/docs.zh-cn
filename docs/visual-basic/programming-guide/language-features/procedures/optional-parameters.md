---
title: 可选参数
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
ms.openlocfilehash: 73a51ab65a8ea4c38b6fd6737279fb19fb1cfe73
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071854"
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="eab24-102">可选参数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eab24-102">Optional Parameters (Visual Basic)</span></span>

<span data-ttu-id="eab24-103">可以指定过程参数是可选的，并且在调用过程时不必为其提供自变量。</span><span class="sxs-lookup"><span data-stu-id="eab24-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="eab24-104">*可选参数* 由 `Optional` 过程定义中的关键字指示。</span><span class="sxs-lookup"><span data-stu-id="eab24-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="eab24-105">下列规则适用：</span><span class="sxs-lookup"><span data-stu-id="eab24-105">The following rules apply:</span></span>  
  
- <span data-ttu-id="eab24-106">过程定义中的每个可选参数都必须指定默认值。</span><span class="sxs-lookup"><span data-stu-id="eab24-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
- <span data-ttu-id="eab24-107">可选参数的默认值必须是一个常数表达式。</span><span class="sxs-lookup"><span data-stu-id="eab24-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
- <span data-ttu-id="eab24-108">过程定义中跟在可选参数后的每个参数也都必须是可选的。</span><span class="sxs-lookup"><span data-stu-id="eab24-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="eab24-109">下面的语法显示带可选参数的过程声明：</span><span class="sxs-lookup"><span data-stu-id="eab24-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="eab24-110">调用带可选参数的过程</span><span class="sxs-lookup"><span data-stu-id="eab24-110">Calling Procedures with Optional Parameters</span></span>  

 <span data-ttu-id="eab24-111">调用带可选参数的过程时，可以选择是否提供该自变量。</span><span class="sxs-lookup"><span data-stu-id="eab24-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="eab24-112">如果不提供，过程将使用为该参数声明的默认值。</span><span class="sxs-lookup"><span data-stu-id="eab24-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="eab24-113">当省略自变量列表中的一个或多个可选自变量时，使用连续的逗号来标记它们的位置。</span><span class="sxs-lookup"><span data-stu-id="eab24-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="eab24-114">下面的调用示例提供了第一个和第四个自变量，省略了第二个和第三个：</span><span class="sxs-lookup"><span data-stu-id="eab24-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="eab24-115">下面的示例对 `MsgBox` 函数进行多次调用。</span><span class="sxs-lookup"><span data-stu-id="eab24-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="eab24-116">`MsgBox` 有一个必需参数和两个可选参数。</span><span class="sxs-lookup"><span data-stu-id="eab24-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="eab24-117">对 `MsgBox` 的第一个调用将按照 `MsgBox` 定义参数的顺序提供所有三个参数。</span><span class="sxs-lookup"><span data-stu-id="eab24-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="eab24-118">第二个调用仅提供必选自变量。</span><span class="sxs-lookup"><span data-stu-id="eab24-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="eab24-119">第三个和第四个调用分别提供第一个和第三个自变量。</span><span class="sxs-lookup"><span data-stu-id="eab24-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="eab24-120">第三个调用按位置提供参数，第四个调用按名称提供参数。</span><span class="sxs-lookup"><span data-stu-id="eab24-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#47)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="eab24-121">确定可选自变量是否存在</span><span class="sxs-lookup"><span data-stu-id="eab24-121">Determining Whether an Optional Argument Is Present</span></span>  

 <span data-ttu-id="eab24-122">过程在运行时无法检测到给定的自变量是否已被省略，或者调用代码是否已显式提供默认值。</span><span class="sxs-lookup"><span data-stu-id="eab24-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="eab24-123">如果需要弄清楚这一点，可以设置一个不可能的值作为默认值。</span><span class="sxs-lookup"><span data-stu-id="eab24-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="eab24-124">下面的过程定义可选参数 `office` ，并测试其默认值， `QJZ` 以确定是否在调用中省略了该参数：</span><span class="sxs-lookup"><span data-stu-id="eab24-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#46)]  
  
 <span data-ttu-id="eab24-125">如果可选参数是像 `String` 这样的引用类型，只要它不是该自变量所预期的值，就可以使用 `Nothing` 作为默认值。</span><span class="sxs-lookup"><span data-stu-id="eab24-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="eab24-126">可选参数和重载</span><span class="sxs-lookup"><span data-stu-id="eab24-126">Optional Parameters and Overloading</span></span>  

 <span data-ttu-id="eab24-127">定义带可选参数的过程的另一种方法是使用重载。</span><span class="sxs-lookup"><span data-stu-id="eab24-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="eab24-128">如果有一个可选参数，可以定义过程的两个重载版本，一个接受此参数，另一个则不带参数。</span><span class="sxs-lookup"><span data-stu-id="eab24-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="eab24-129">此方法随可选参数数目的增加而变得更复杂。</span><span class="sxs-lookup"><span data-stu-id="eab24-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="eab24-130">然而，这样做的优点是可以完全确定调用程序是否提供了每个可选自变量。</span><span class="sxs-lookup"><span data-stu-id="eab24-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab24-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="eab24-131">See also</span></span>

- [<span data-ttu-id="eab24-132">过程</span><span class="sxs-lookup"><span data-stu-id="eab24-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="eab24-133">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="eab24-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="eab24-134">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="eab24-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="eab24-135">按位置和按名称传递自变量</span><span class="sxs-lookup"><span data-stu-id="eab24-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="eab24-136">参数数组</span><span class="sxs-lookup"><span data-stu-id="eab24-136">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="eab24-137">过程重载</span><span class="sxs-lookup"><span data-stu-id="eab24-137">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="eab24-138">可选</span><span class="sxs-lookup"><span data-stu-id="eab24-138">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="eab24-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="eab24-139">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
