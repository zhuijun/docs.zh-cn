---
title: 未设置对象变量或 With 块变量
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 0264a4235a056c93edb703ec2ef70e7124e0df4e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873631"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="e9ee9-102">未设置对象变量或 With 块变量</span><span class="sxs-lookup"><span data-stu-id="e9ee9-102">Object variable or With block variable not set</span></span>

<span data-ttu-id="e9ee9-103">正在引用无效的对象变量。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="e9ee9-104">出现此错误的原因可能有多种：</span><span class="sxs-lookup"><span data-stu-id="e9ee9-104">This error can occur for several reasons:</span></span>

- <span data-ttu-id="e9ee9-105">声明了变量，但未指定类型。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="e9ee9-106">如果在未指定类型的情况下声明了变量，则默认为类型 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>

    <span data-ttu-id="e9ee9-107">例如，使用声明的变量 `Dim x` 的类型将为类型 `Object;` `Dim x As String` `String` 。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>

    > [!TIP]
    > <span data-ttu-id="e9ee9-108">`Option Strict`语句不允许使用导致类型的隐式 `Object` 类型。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="e9ee9-109">如果省略该类型，则会发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="e9ee9-110">请参阅 [Option Strict 语句](../statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-110">See [Option Strict Statement](../statements/option-strict-statement.md).</span></span>

- <span data-ttu-id="e9ee9-111">你正在尝试引用已设置为的对象 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-111">You are attempting to reference an object that has been set to `Nothing`.</span></span>

- <span data-ttu-id="e9ee9-112">您正在尝试访问未正确声明的数组变量的元素。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-112">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>

    <span data-ttu-id="e9ee9-113">例如， `products() As String` 如果您尝试引用数组的元素，则声明为的数组将触发错误 `products(3) = "Widget"` 。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-113">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="e9ee9-114">数组没有元素，被视为对象。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-114">The array has no elements and is treated as an object.</span></span>

- <span data-ttu-id="e9ee9-115">在初始化块之前，您正尝试访问代码块中的代码 `With...End With` 。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-115">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="e9ee9-116">`With...End With`必须通过执行 `With` 语句入口点初始化块。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-116">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>

> [!NOTE]
> <span data-ttu-id="e9ee9-117">在 Visual Basic 或 VBA 的早期版本中，还会通过在不使用 `Set` 关键字 (`x = "name"` 而不是) 的情况下将值赋给变量来触发此错误 `Set x = "name"` 。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-117">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="e9ee9-118">`Set`关键字在 Visual Basic .net 中不再有效。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-118">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e9ee9-119">更正此错误</span><span class="sxs-lookup"><span data-stu-id="e9ee9-119">To correct this error</span></span>

1. <span data-ttu-id="e9ee9-120">`Option Strict` `On` 通过将以下代码添加到文件的开头，将设置为：</span><span class="sxs-lookup"><span data-stu-id="e9ee9-120">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>

    ```vb
    Option Strict On
    ```

    <span data-ttu-id="e9ee9-121">运行该项目时，将在 **错误列表** 中为没有类型指定的任何变量显示编译器错误。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-121">When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.</span></span>

2. <span data-ttu-id="e9ee9-122">如果你不想启用 `Option Strict` ，请在代码中搜索没有类型 (指定的任何变量， `Dim x` 而不是 `Dim x As String`) 并将目标类型添加到声明。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>

3. <span data-ttu-id="e9ee9-123">请确保未引用已设置为的对象变量 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="e9ee9-124">在代码中搜索关键字 `Nothing` ，然后修改代码，使对象在引用之前不会设置为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>

4. <span data-ttu-id="e9ee9-125">在访问数组变量之前，请确保对其进行标注。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="e9ee9-126">您可以在第一次创建数组时分配维度 (`Dim x(5) As String` 而不是 `Dim x() As String`) ，或者使用 `ReDim` 关键字在第一次访问数组之前设置数组的尺寸。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>

5. <span data-ttu-id="e9ee9-127">请确保 `With` 通过执行 `With` 语句入口点初始化块。</span><span class="sxs-lookup"><span data-stu-id="e9ee9-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9ee9-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9ee9-128">See also</span></span>

- [<span data-ttu-id="e9ee9-129">对象变量声明</span><span class="sxs-lookup"><span data-stu-id="e9ee9-129">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="e9ee9-130">ReDim 语句</span><span class="sxs-lookup"><span data-stu-id="e9ee9-130">ReDim Statement</span></span>](../statements/redim-statement.md)
- [<span data-ttu-id="e9ee9-131">With...End With 语句</span><span class="sxs-lookup"><span data-stu-id="e9ee9-131">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
