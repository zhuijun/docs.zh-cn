---
title: Function 语句
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404623"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="e5a4a-102">Function 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5a4a-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="e5a4a-103">声明定义过程的名称、参数和代码 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="e5a4a-104">语法</span><span class="sxs-lookup"><span data-stu-id="e5a4a-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="e5a4a-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="e5a4a-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="e5a4a-106">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-106">Optional.</span></span> <span data-ttu-id="e5a4a-107">请参阅[特性列表](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="e5a4a-108">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-108">Optional.</span></span> <span data-ttu-id="e5a4a-109">可以是以下其中一个值：</span><span class="sxs-lookup"><span data-stu-id="e5a4a-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="e5a4a-110">公共</span><span class="sxs-lookup"><span data-stu-id="e5a4a-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="e5a4a-111">避免</span><span class="sxs-lookup"><span data-stu-id="e5a4a-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="e5a4a-112">友好</span><span class="sxs-lookup"><span data-stu-id="e5a4a-112">Friend</span></span>](../modifiers/friend.md)

  - <span data-ttu-id="e5a4a-113">专用 </span><span class="sxs-lookup"><span data-stu-id="e5a4a-113">[Private](../modifiers/private.md)</span></span>

  - [<span data-ttu-id="e5a4a-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="e5a4a-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="e5a4a-115">私有受保护</span><span class="sxs-lookup"><span data-stu-id="e5a4a-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="e5a4a-116">请参阅[Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="e5a4a-117">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-117">Optional.</span></span> <span data-ttu-id="e5a4a-118">可以是以下其中一个值：</span><span class="sxs-lookup"><span data-stu-id="e5a4a-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="e5a4a-119">重载</span><span class="sxs-lookup"><span data-stu-id="e5a4a-119">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="e5a4a-120">替代</span><span class="sxs-lookup"><span data-stu-id="e5a4a-120">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="e5a4a-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="e5a4a-121">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="e5a4a-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e5a4a-122">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="e5a4a-123">New</span><span class="sxs-lookup"><span data-stu-id="e5a4a-123">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="e5a4a-124">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-124">Optional.</span></span> <span data-ttu-id="e5a4a-125">请参阅[共享](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-125">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="e5a4a-126">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-126">Optional.</span></span> <span data-ttu-id="e5a4a-127">请参阅[阴影](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-127">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="e5a4a-128">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-128">Optional.</span></span> <span data-ttu-id="e5a4a-129">请参阅[Async](../modifiers/async.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-129">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="e5a4a-130">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-130">Optional.</span></span> <span data-ttu-id="e5a4a-131">请参阅[迭代器](../modifiers/iterator.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-131">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="e5a4a-132">必需。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-132">Required.</span></span> <span data-ttu-id="e5a4a-133">过程的名称。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-133">Name of the procedure.</span></span> <span data-ttu-id="e5a4a-134">请参阅 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="e5a4a-135">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-135">Optional.</span></span> <span data-ttu-id="e5a4a-136">泛型过程的类型参数的列表。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="e5a4a-137">请参阅[类型列表](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="e5a4a-138">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-138">Optional.</span></span> <span data-ttu-id="e5a4a-139">表示此过程参数的本地变量名称列表。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="e5a4a-140">请参阅[参数列表](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="e5a4a-141">如果 `Option Strict` 为，则为必需 `On` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="e5a4a-142">此过程返回的值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="e5a4a-143">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-143">Optional.</span></span> <span data-ttu-id="e5a4a-144">指示此过程实现了一个或多个 `Function` 过程，每个过程都在此过程的包含类或结构实现的接口中定义。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="e5a4a-145">请参阅[Implements 语句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="e5a4a-146">如果提供 `Implements`，则是必需的。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="e5a4a-147">所实现的 `Function` 过程的列表。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="e5a4a-148">每个 `implementedprocedure` 都具有以下语法和部件：</span><span class="sxs-lookup"><span data-stu-id="e5a4a-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="e5a4a-149">组成部分</span><span class="sxs-lookup"><span data-stu-id="e5a4a-149">Part</span></span>|<span data-ttu-id="e5a4a-150">说明</span><span class="sxs-lookup"><span data-stu-id="e5a4a-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="e5a4a-151">必需。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-151">Required.</span></span> <span data-ttu-id="e5a4a-152">此过程的包含类或结构实现的接口的名称。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="e5a4a-153">必需。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-153">Required.</span></span> <span data-ttu-id="e5a4a-154">在 `interface` 中用于定义过程的名称。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="e5a4a-155">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-155">Optional.</span></span> <span data-ttu-id="e5a4a-156">指示此过程可以处理一个或多个特定事件。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="e5a4a-157">请参阅[句柄](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="e5a4a-158">如果提供 `Handles`，则是必需的。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="e5a4a-159">此过程处理的事件列表。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="e5a4a-160">每个 `eventspecifier` 都具有以下语法和部件：</span><span class="sxs-lookup"><span data-stu-id="e5a4a-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="e5a4a-161">组成部分</span><span class="sxs-lookup"><span data-stu-id="e5a4a-161">Part</span></span>|<span data-ttu-id="e5a4a-162">说明</span><span class="sxs-lookup"><span data-stu-id="e5a4a-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="e5a4a-163">必需。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-163">Required.</span></span> <span data-ttu-id="e5a4a-164">用引发事件的类或结构的数据类型声明的对象变量。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="e5a4a-165">必需。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-165">Required.</span></span> <span data-ttu-id="e5a4a-166">此过程处理的事件的名称。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="e5a4a-167">可选。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-167">Optional.</span></span> <span data-ttu-id="e5a4a-168">要在此过程中执行的语句块。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="e5a4a-169">终止此过程的定义。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5a4a-170">备注</span><span class="sxs-lookup"><span data-stu-id="e5a4a-170">Remarks</span></span>

<span data-ttu-id="e5a4a-171">所有可执行代码都必须在过程内。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="e5a4a-172">反过来，每个过程都在类、结构或模块（称为包含类、结构或模块）中声明。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="e5a4a-173">若要将值返回到调用代码，请使用 `Function` 过程; 否则，请使用 `Sub` 过程。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="e5a4a-174">定义函数</span><span class="sxs-lookup"><span data-stu-id="e5a4a-174">Defining a Function</span></span>

<span data-ttu-id="e5a4a-175">只能 `Function` 在模块级别定义过程。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="e5a4a-176">因此，函数的声明上下文必须是类、结构、模块或接口，不能是源文件、命名空间、过程或块。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="e5a4a-177">有关详细信息，请参阅[声明上下文和默认访问级别](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="e5a4a-178">`Function`过程默认为公共访问。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="e5a4a-179">您可以使用访问修饰符调整其访问级别。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="e5a4a-180">`Function`过程可以声明过程返回的值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="e5a4a-181">您可以指定任何数据类型或枚举、结构、类或接口的名称。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="e5a4a-182">如果未指定 `returntype` 参数，则过程返回 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="e5a4a-183">如果此过程使用 `Implements` 关键字，则包含类或结构还必须具有紧跟在 `Implements` 其或语句后面的 `Class` 语句 `Structure` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="e5a4a-184">`Implements`语句必须包括在中指定的每个接口 `implementslist` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="e5a4a-185">但是，接口用于定义 `Function` （在中）的名称 `definedname` 不需要与此过程的名称匹配（在中为 `name` ）。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="e5a4a-186">您可以使用 lambda 表达式来定义内联函数表达式。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="e5a4a-187">有关详细信息，请参阅[函数表达式](../operators/function-expression.md)和[Lambda 表达式](../../programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-187">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="e5a4a-188">从函数返回</span><span class="sxs-lookup"><span data-stu-id="e5a4a-188">Returning from a Function</span></span>

<span data-ttu-id="e5a4a-189">当 `Function` 过程返回到调用代码时，执行将继续执行调用该过程的语句后面的语句。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="e5a4a-190">若要从函数返回值，可将值分配给函数名称或将其包含在 `Return` 语句中。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="e5a4a-191">`Return`语句同时分配返回值并退出函数，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="e5a4a-192">下面的示例将返回值分配给函数名称 `myFunction` ，然后使用 `Exit Function` 语句返回。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="e5a4a-193">`Exit Function`和 `Return` 语句导致直接从 `Function` 过程退出。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="e5a4a-194">任意数量的 `Exit Function` 和 `Return` 语句可以出现在过程中的任何位置，并且可以混合使用 `Exit Function` 和 `Return` 语句。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="e5a4a-195">如果在 `Exit Function` 不向赋值的情况下使用 `name` ，则该过程将返回中指定的数据类型的默认值 `returntype` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="e5a4a-196">如果 `returntype` 未指定，则过程返回 `Nothing` ，这是的默认值 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="e5a4a-197">调用函数</span><span class="sxs-lookup"><span data-stu-id="e5a4a-197">Calling a Function</span></span>

<span data-ttu-id="e5a4a-198">`Function`通过在表达式中使用过程名称，后跟括号中的参数列表，调用过程。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="e5a4a-199">仅当未提供任何参数时，才可以省略括号。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="e5a4a-200">但是，如果你始终包含括号，你的代码将更具可读性。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="e5a4a-201">调用 `Function` 过程的方法与调用任何库函数（如、或）的方法相同 `Sqrt` `Cos` `ChrW` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="e5a4a-202">还可以使用关键字调用函数 `Call` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="e5a4a-203">在这种情况下，将忽略返回值。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="e5a4a-204">`Call`在大多数情况下不建议使用关键字。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="e5a4a-205">有关详细信息，请参阅[Call 语句](call-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="e5a4a-206">Visual Basic 有时会重新排列算术表达式以提高内部效率。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="e5a4a-207">出于此原因， `Function` 当函数更改同一表达式中变量的值时，不应使用算术表达式中的过程。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="e5a4a-208">异步函数</span><span class="sxs-lookup"><span data-stu-id="e5a4a-208">Async Functions</span></span>

<span data-ttu-id="e5a4a-209">使用*异步*功能可以调用异步函数，而无需使用显式回调或在多个函数或 lambda 表达式中手动拆分代码。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="e5a4a-210">如果使用[Async](../modifiers/async.md)修饰符标记函数，则可以在函数中使用[Await](../operators/await-operator.md)运算符。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-210">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="e5a4a-211">当控件 `Await` 在函数中到达表达式时 `Async` ，控件将返回到调用方，在等待的任务完成之前，将挂起函数中的进度。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="e5a4a-212">任务完成后，可以在函数中继续执行。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="e5a4a-213">`Async`当过程遇到尚未完成的第一个等待对象时，或在过程结束时（以先发生者为准），过程返回到调用方 `Async` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="e5a4a-214">`Async`函数的返回类型可以是 <xref:System.Threading.Tasks.Task%601> 或 <xref:System.Threading.Tasks.Task> 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="e5a4a-215">`Async`下面提供了返回类型为的函数的示例 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="e5a4a-216">`Async`函数不能声明任何[ByRef](../modifiers/byref.md)参数。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-216">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="e5a4a-217">还可以使用修饰符来标记[Sub 语句](sub-statement.md) `Async` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="e5a4a-218">这主要用于事件处理程序，其中不能返回值。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="e5a4a-219">`Async` `Sub` 无法等待过程，并且过程的调用方 `Async` `Sub` 无法捕获过程所引发的异常 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="e5a4a-220">有关函数的详细信息 `Async` ，请参阅[采用 Async 和 Await 的异步编程](../../programming-guide/concepts/async/index.md)、[异步程序中的控制流](../../programming-guide/concepts/async/control-flow-in-async-programs.md)和[异步返回类型](../../programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="e5a4a-221">迭代器函数</span><span class="sxs-lookup"><span data-stu-id="e5a4a-221">Iterator Functions</span></span>

<span data-ttu-id="e5a4a-222">*迭代器*函数在集合上执行自定义迭代，如列表或数组。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="e5a4a-223">Iterator 函数使用[Yield](yield-statement.md)语句每次返回一个元素。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="e5a4a-224">当到达[Yield](yield-statement.md)语句时，将记住代码中的当前位置。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="e5a4a-225">下次调用迭代器函数时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="e5a4a-226">使用 For Each ... 将从客户端代码调用迭代器[下一](for-each-next-statement.md)语句。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="e5a4a-227">迭代器函数的返回类型可以是 <xref:System.Collections.IEnumerable> 、、 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601> 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="e5a4a-228">有关更多信息，请参见 [迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5a4a-229">示例</span><span class="sxs-lookup"><span data-stu-id="e5a4a-229">Example</span></span>

<span data-ttu-id="e5a4a-230">下面的示例使用 `Function` 语句来声明构成过程正文的名称、参数和代码 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="e5a4a-231">`ParamArray`修饰符使函数可以接受数量可变的参数。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="e5a4a-232">示例</span><span class="sxs-lookup"><span data-stu-id="e5a4a-232">Example</span></span>

<span data-ttu-id="e5a4a-233">下面的示例调用在前面的示例中声明的函数。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="e5a4a-234">示例</span><span class="sxs-lookup"><span data-stu-id="e5a4a-234">Example</span></span>

<span data-ttu-id="e5a4a-235">在下面的示例中， `DelayAsync` 是 `Async` `Function` 具有返回类型的 <xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e5a4a-236">`DelayAsync` 具有返回整数的 `Return` 语句。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="e5a4a-237">因此，的函数声明 `DelayAsync` 需要具有返回类型 `Task(Of Integer)` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="e5a4a-238">由于返回类型为 `Task(Of Integer)` ，因此中表达式的计算将 `Await` `DoSomethingAsync` 产生整数。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="e5a4a-239">此语句演示了这一点： `Dim result As Integer = Await delayTask` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="e5a4a-240">此 `startButton_Click` 过程是过程的示例 `Async Sub` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="e5a4a-241">由于 `DoSomethingAsync` 是一个 `Async` 函数，因此对的调用的任务 `DoSomethingAsync` 必须等待，如以下语句所示： `Await DoSomethingAsync()` 。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="e5a4a-242">此 `startButton_Click` `Sub` 过程必须使用修饰符进行定义， `Async` 因为它具有 `Await` 表达式。</span><span class="sxs-lookup"><span data-stu-id="e5a4a-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e5a4a-243">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5a4a-243">See also</span></span>

- [<span data-ttu-id="e5a4a-244">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="e5a4a-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="e5a4a-245">Function 过程</span><span class="sxs-lookup"><span data-stu-id="e5a4a-245">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="e5a4a-246">参数列表</span><span class="sxs-lookup"><span data-stu-id="e5a4a-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="e5a4a-247">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="e5a4a-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="e5a4a-248">Call 语句</span><span class="sxs-lookup"><span data-stu-id="e5a4a-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="e5a4a-249">个</span><span class="sxs-lookup"><span data-stu-id="e5a4a-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="e5a4a-250">参数数组</span><span class="sxs-lookup"><span data-stu-id="e5a4a-250">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="e5a4a-251">如何：使用泛型类</span><span class="sxs-lookup"><span data-stu-id="e5a4a-251">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="e5a4a-252">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="e5a4a-252">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="e5a4a-253">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="e5a4a-253">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="e5a4a-254">函数表达式</span><span class="sxs-lookup"><span data-stu-id="e5a4a-254">Function Expression</span></span>](../operators/function-expression.md)
