---
title: With...End With 语句
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 50f3bd0c6e96254274b429794901e2e4ac719ad0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401376"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="7dff8-102">With...End With 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dff8-102">With...End With Statement (Visual Basic)</span></span>

<span data-ttu-id="7dff8-103">执行一系列反复引用单个对象或结构的语句，以便这些语句可在访问对象或结构的成员时使用简化语法。</span><span class="sxs-lookup"><span data-stu-id="7dff8-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="7dff8-104">使用结构时，你只能读取成员或调用的方法的值，如果你尝试为 `With...End With` 语句中使用的结构的成员赋值，则将收到错误。</span><span class="sxs-lookup"><span data-stu-id="7dff8-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>

## <a name="syntax"></a><span data-ttu-id="7dff8-105">语法</span><span class="sxs-lookup"><span data-stu-id="7dff8-105">Syntax</span></span>

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a><span data-ttu-id="7dff8-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="7dff8-106">Parts</span></span>

|<span data-ttu-id="7dff8-107">术语</span><span class="sxs-lookup"><span data-stu-id="7dff8-107">Term</span></span>|<span data-ttu-id="7dff8-108">定义</span><span class="sxs-lookup"><span data-stu-id="7dff8-108">Definition</span></span>|
|---|---|
|`objectExpression`|<span data-ttu-id="7dff8-109">必需。</span><span class="sxs-lookup"><span data-stu-id="7dff8-109">Required.</span></span> <span data-ttu-id="7dff8-110">计算结果为对象的表达式。</span><span class="sxs-lookup"><span data-stu-id="7dff8-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="7dff8-111">表达式可能是任意复杂的，并且只能计算一次。</span><span class="sxs-lookup"><span data-stu-id="7dff8-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="7dff8-112">表达式可以计算为任何数据类型，包括基本类型。</span><span class="sxs-lookup"><span data-stu-id="7dff8-112">The expression can evaluate to any data type, including elementary types.</span></span>|
|`statements`|<span data-ttu-id="7dff8-113">可选。</span><span class="sxs-lookup"><span data-stu-id="7dff8-113">Optional.</span></span> <span data-ttu-id="7dff8-114">`With` 和 `End With` 之间的一个或多个语句，这些语句可能引用通过计算 `objectExpression` 生成的对象的成员。</span><span class="sxs-lookup"><span data-stu-id="7dff8-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|
|`End With`|<span data-ttu-id="7dff8-115">必需。</span><span class="sxs-lookup"><span data-stu-id="7dff8-115">Required.</span></span> <span data-ttu-id="7dff8-116">终止 `With` 块的定义。</span><span class="sxs-lookup"><span data-stu-id="7dff8-116">Terminates the definition of the `With` block.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7dff8-117">备注</span><span class="sxs-lookup"><span data-stu-id="7dff8-117">Remarks</span></span>

<span data-ttu-id="7dff8-118">通过使用 `With...End With`，你可对指定对象执行一系列语句，而无需多次指定对象名称。</span><span class="sxs-lookup"><span data-stu-id="7dff8-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="7dff8-119">在 `With` 语句块内，你可指定以句点开头的对象的成员，就像它前面有 `With` 语句对象一样。</span><span class="sxs-lookup"><span data-stu-id="7dff8-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>

<span data-ttu-id="7dff8-120">例如，若要更改单个对象的多个属性，请将属性分配语句放在 `With...End With` 块中，这样只需引用一次对象，而不是为每个属性分配都引用一次对象。</span><span class="sxs-lookup"><span data-stu-id="7dff8-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>

<span data-ttu-id="7dff8-121">如果代码访问多个语句中的同一个对象，则使用 `With` 语句将获得下列好处：</span><span class="sxs-lookup"><span data-stu-id="7dff8-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>

- <span data-ttu-id="7dff8-122">你不必多次计算复杂的表达式，或者多次将结果分配给临时变量来引用其成员。</span><span class="sxs-lookup"><span data-stu-id="7dff8-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>

- <span data-ttu-id="7dff8-123">通过消除反复限定表达式，你提高了代码的可读取性。</span><span class="sxs-lookup"><span data-stu-id="7dff8-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>

<span data-ttu-id="7dff8-124">`objectExpression` 的数据类型可以是任何类或结构类型，甚至可以是 Visual Basic 基础类型（如 `Integer`）。</span><span class="sxs-lookup"><span data-stu-id="7dff8-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="7dff8-125">如果 `objectExpression` 生成对象之外的任何内容，则你只能读取其成员或调用的方法的值，如果你尝试为 `With...End With` 语句中使用的结构的成员赋值，则将收到错误。</span><span class="sxs-lookup"><span data-stu-id="7dff8-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="7dff8-126">此错误与你在调用返回一个结构的方法并立即访问函数结果（如 `GetAPoint().x = 1`）的成员并为其赋值时收到的错误一样。</span><span class="sxs-lookup"><span data-stu-id="7dff8-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="7dff8-127">这两种情况的问题是，结构仅存在于调用堆栈上，并且已修改的结构成员在这些情况下无法写入到一个位置以使程序中的所有其他代码可以观察到更改。</span><span class="sxs-lookup"><span data-stu-id="7dff8-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>

<span data-ttu-id="7dff8-128">在进入块时仅计算 `objectExpression` 一次。</span><span class="sxs-lookup"><span data-stu-id="7dff8-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="7dff8-129">你无法从 `objectExpression` 块中重新分配 `With`。</span><span class="sxs-lookup"><span data-stu-id="7dff8-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>

<span data-ttu-id="7dff8-130">在 `With` 块中，你可访问仅指定对象的方法和属性，而不必限定它们。</span><span class="sxs-lookup"><span data-stu-id="7dff8-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="7dff8-131">你可以使用其他对象的方法和属性，但是必须用其对象名限定它们。</span><span class="sxs-lookup"><span data-stu-id="7dff8-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>

<span data-ttu-id="7dff8-132">你可以将一个 `With...End With` 语句放置在另一个语句中。</span><span class="sxs-lookup"><span data-stu-id="7dff8-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="7dff8-133">如果未从上下文中清除引用的对象，则嵌套的 `With...End With` 语句可能产生混乱。</span><span class="sxs-lookup"><span data-stu-id="7dff8-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="7dff8-134">从内部的 `With` 块内引用外部的 `With` 块中的某个对象时，你必须提供对该对象的完全限定的引用。</span><span class="sxs-lookup"><span data-stu-id="7dff8-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>

<span data-ttu-id="7dff8-135">你不能从 `With` 语句块的外部分支到此语句块。</span><span class="sxs-lookup"><span data-stu-id="7dff8-135">You can't branch into a `With` statement block from outside the block.</span></span>

<span data-ttu-id="7dff8-136">除非此语句块包含循环，否则这些语句只运行一次。</span><span class="sxs-lookup"><span data-stu-id="7dff8-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="7dff8-137">你可嵌套不同类型的控制结构。</span><span class="sxs-lookup"><span data-stu-id="7dff8-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="7dff8-138">有关详细信息，请参阅[嵌套控制结构](../../programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="7dff8-138">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7dff8-139">你还可在对象初始值设定项中使用 `With` 关键字。</span><span class="sxs-lookup"><span data-stu-id="7dff8-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="7dff8-140">有关详细信息和示例，请参阅[对象初始值设定项：命名类型和匿名](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)类型和[匿名类型](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7dff8-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>
>
> <span data-ttu-id="7dff8-141">如果你使用 `With` 块只是为了初始化已实例化的对象的属性或字段，请考虑改用对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="7dff8-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>

## <a name="example"></a><span data-ttu-id="7dff8-142">示例</span><span class="sxs-lookup"><span data-stu-id="7dff8-142">Example</span></span>

<span data-ttu-id="7dff8-143">在下面的示例中，每个 `With` 块将对单个对象执行一系列语句。</span><span class="sxs-lookup"><span data-stu-id="7dff8-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a><span data-ttu-id="7dff8-144">示例</span><span class="sxs-lookup"><span data-stu-id="7dff8-144">Example</span></span>

<span data-ttu-id="7dff8-145">下面的示例嵌套 `With…End With` 语句。</span><span class="sxs-lookup"><span data-stu-id="7dff8-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="7dff8-146">在嵌套的 `With` 语句中，语法引用内部对象。</span><span class="sxs-lookup"><span data-stu-id="7dff8-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7dff8-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7dff8-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="7dff8-148">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="7dff8-148">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="7dff8-149">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="7dff8-149">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="7dff8-150">匿名类型</span><span class="sxs-lookup"><span data-stu-id="7dff8-150">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
