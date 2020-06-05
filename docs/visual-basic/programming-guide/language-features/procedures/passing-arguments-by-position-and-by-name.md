---
title: 按位置和按名称传递参数
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: 686b64977f086c8128e56298a0ed8c5aa0c51efa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364027"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="562f0-102">按位置和名称传递自变量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="562f0-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="562f0-103">调用 `Sub` 或 `Function` 过程时，可以*按位置*（按照它们在过程定义中的显示顺序）传递参数，也可以*按名称*传递参数，而不考虑位置。</span><span class="sxs-lookup"><span data-stu-id="562f0-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="562f0-104">按名称传递参数时，请指定参数的声明名称，后跟冒号和等号（ `:=` ），后跟自变量值。</span><span class="sxs-lookup"><span data-stu-id="562f0-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="562f0-105">可以按任意顺序提供命名参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="562f0-106">例如，下面的 `Sub` 过程采用三个参数：</span><span class="sxs-lookup"><span data-stu-id="562f0-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="562f0-107">调用此过程时，可以按位置、名称或同时使用这两个参数来提供参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="562f0-108">按位置传递参数</span><span class="sxs-lookup"><span data-stu-id="562f0-108">Passing Arguments by Position</span></span>

<span data-ttu-id="562f0-109">可以调用方法，该 `Display` 方法的参数按位置传递，并用逗号进行分隔，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="562f0-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="562f0-110">如果在位置参数列表中省略了可选参数，则必须用逗号保存其位置。</span><span class="sxs-lookup"><span data-stu-id="562f0-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="562f0-111">下面的示例调用 `Display` 不带参数的方法 `age` ：</span><span class="sxs-lookup"><span data-stu-id="562f0-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="562f0-112">按名称传递参数</span><span class="sxs-lookup"><span data-stu-id="562f0-112">Passing Arguments by Name</span></span>

<span data-ttu-id="562f0-113">另外， `Display` 还可以使用按名称传递的自变量（也用逗号分隔）调用，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="562f0-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="562f0-114">当调用具有多个可选参数的过程时，以这种方式传递参数的方法特别有用。</span><span class="sxs-lookup"><span data-stu-id="562f0-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="562f0-115">如果按名称提供参数，则无需使用连续的逗号表示缺少的位置参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="562f0-116">通过按名称传递参数，还可以更轻松地跟踪正在传递的参数和要省略的参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="562f0-117">按位置和按名称混合参数</span><span class="sxs-lookup"><span data-stu-id="562f0-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="562f0-118">可以在单个过程调用中按位置和按名称提供参数，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="562f0-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="562f0-119">在前面的示例中， `age` 由于 `birth` 是按名称传递的，因此不需要额外的逗号来容纳省略的参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="562f0-120">在15.5 之前的 Visual Basic 版本中，当你通过位置和名称的组合提供参数时，位置参数必须是第一个。</span><span class="sxs-lookup"><span data-stu-id="562f0-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="562f0-121">按名称提供参数后，所有剩余参数都必须按名称传递。</span><span class="sxs-lookup"><span data-stu-id="562f0-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="562f0-122">例如，以下对方法的调用 `Display` 显示编译器错误[BC30241：应为命名参数](../../../misc/bc30241.md)。</span><span class="sxs-lookup"><span data-stu-id="562f0-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="562f0-123">从 Visual Basic 15.5 开始，如果结束位置参数位于正确的位置，则位置参数可以跟随命名参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="562f0-124">如果在 Visual Basic 15.5 下编译，则以前对方法的调用将 `Display` 成功编译，不再生成编译器错误[BC30241](../../../misc/bc30241.md)。</span><span class="sxs-lookup"><span data-stu-id="562f0-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="562f0-125">如果要使用命名参数使代码更具可读性，此功能可以按任意顺序混合并匹配命名参数和位置参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="562f0-126">例如，下面的 `Person` 类构造函数需要类型的两个参数，这两个参数 `Person` 都可以是 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="562f0-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="562f0-127">当和参数的值为时，使用混合的命名参数和位置参数可确保代码的 `father` 意图 `mother` `Nothing` ：</span><span class="sxs-lookup"><span data-stu-id="562f0-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="562f0-128">若要在位置参数后面添加命名参数，必须将以下元素添加到 Visual Basic 项目（ \* .vbproj）文件中：</span><span class="sxs-lookup"><span data-stu-id="562f0-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="562f0-129">有关详细信息，请参阅[设置 Visual Basic 语言版本](../../../language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="562f0-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="562f0-130">按名称提供参数的限制</span><span class="sxs-lookup"><span data-stu-id="562f0-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="562f0-131">不能按名称传递参数，以避免输入所需的参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="562f0-132">只能省略可选参数。</span><span class="sxs-lookup"><span data-stu-id="562f0-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="562f0-133">不能按名称传递参数数组。</span><span class="sxs-lookup"><span data-stu-id="562f0-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="562f0-134">这是因为，当你调用过程时，你为参数数组提供了不限数量的逗号分隔参数，且编译器无法将多个参数与单个名称相关联。</span><span class="sxs-lookup"><span data-stu-id="562f0-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="562f0-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="562f0-135">See also</span></span>

- [<span data-ttu-id="562f0-136">过程</span><span class="sxs-lookup"><span data-stu-id="562f0-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="562f0-137">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="562f0-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="562f0-138">如何：将参数传递给过程</span><span class="sxs-lookup"><span data-stu-id="562f0-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="562f0-139">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="562f0-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="562f0-140">可选参数</span><span class="sxs-lookup"><span data-stu-id="562f0-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="562f0-141">参数数组</span><span class="sxs-lookup"><span data-stu-id="562f0-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="562f0-142">可选</span><span class="sxs-lookup"><span data-stu-id="562f0-142">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="562f0-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="562f0-143">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
