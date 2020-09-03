---
title: 方法 - C# 编程指南
description: C# 中的方法是包含一系列语句的代码块。 程序通过调用该方法并指定参数来运行语句。
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 7b411283822360f3057b0d4f4e60ebade4fe45bc
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810932"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="dc143-104">方法（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="dc143-104">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="dc143-105">方法是包含一系列语句的代码块。</span><span class="sxs-lookup"><span data-stu-id="dc143-105">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="dc143-106">程序通过调用该方法并指定任何所需的方法参数使语句得以执行。</span><span class="sxs-lookup"><span data-stu-id="dc143-106">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="dc143-107">在 C# 中，每个执行的指令均在方法的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="dc143-107">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="dc143-108">`Main` 方法是每个 C# 应用程序的入口点，并在启动程序时由公共语言运行时 (CLR) 调用。</span><span class="sxs-lookup"><span data-stu-id="dc143-108">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="dc143-109">本文讨论命名的方法。</span><span class="sxs-lookup"><span data-stu-id="dc143-109">This article discusses named methods.</span></span> <span data-ttu-id="dc143-110">有关匿名函数的信息，请参阅[匿名函数](../statements-expressions-operators/anonymous-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="dc143-110">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="dc143-111">方法签名</span><span class="sxs-lookup"><span data-stu-id="dc143-111">Method signatures</span></span>

<span data-ttu-id="dc143-112">通过指定访问级别（如 `public` 或 `private`）、可选修饰符（如 `abstract` 或 `sealed`）、返回值、方法的名称以及任何方法参数，在[类](../../language-reference/keywords/class.md)、[结构](../../language-reference/builtin-types/struct.md)或[接口](../interfaces/index.md)中声明方法。</span><span class="sxs-lookup"><span data-stu-id="dc143-112">Methods are declared in a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../interfaces/index.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="dc143-113">这些部件一起构成方法的签名。</span><span class="sxs-lookup"><span data-stu-id="dc143-113">These parts together are the signature of the method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc143-114">出于方法重载的目的，方法的返回类型不是方法签名的一部分。</span><span class="sxs-lookup"><span data-stu-id="dc143-114">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="dc143-115">但是在确定委托和它所指向的方法之间的兼容性时，它是方法签名的一部分。</span><span class="sxs-lookup"><span data-stu-id="dc143-115">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="dc143-116">方法参数在括号内，并且用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="dc143-116">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="dc143-117">空括号指示方法不需要任何参数。</span><span class="sxs-lookup"><span data-stu-id="dc143-117">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="dc143-118">此类包含四种方法：</span><span class="sxs-lookup"><span data-stu-id="dc143-118">This class contains four methods:</span></span>

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a><span data-ttu-id="dc143-119">方法访问</span><span class="sxs-lookup"><span data-stu-id="dc143-119">Method access</span></span>

<span data-ttu-id="dc143-120">调用对象上的方法就像访问字段。</span><span class="sxs-lookup"><span data-stu-id="dc143-120">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="dc143-121">在对象名之后添加一个句点、方法名和括号。</span><span class="sxs-lookup"><span data-stu-id="dc143-121">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="dc143-122">参数列在括号里，并且用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="dc143-122">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="dc143-123">因此，可在以下示例中调用 `Motorcycle` 类的方法：</span><span class="sxs-lookup"><span data-stu-id="dc143-123">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="dc143-124">方法形参与实参</span><span class="sxs-lookup"><span data-stu-id="dc143-124">Method parameters vs. arguments</span></span>

<span data-ttu-id="dc143-125">该方法定义指定任何所需参数的名称和类型。</span><span class="sxs-lookup"><span data-stu-id="dc143-125">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="dc143-126">调用代码调用该方法时，它为每个参数提供了称为参数的具体值。</span><span class="sxs-lookup"><span data-stu-id="dc143-126">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="dc143-127">参数必须与参数类型兼容，但调用代码中使用的参数名（如果有）不需要与方法中定义的参数名相同。</span><span class="sxs-lookup"><span data-stu-id="dc143-127">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="dc143-128">例如：</span><span class="sxs-lookup"><span data-stu-id="dc143-128">For example:</span></span>

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="dc143-129">按引用传递与按值传递</span><span class="sxs-lookup"><span data-stu-id="dc143-129">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="dc143-130">默认情况下，将[值类型](../../language-reference/builtin-types/value-types.md)的实例传递给方法时，传递的是其副本而不是实例本身。</span><span class="sxs-lookup"><span data-stu-id="dc143-130">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="dc143-131">因此，对参数的更改不会影响调用方法中的原始实例。</span><span class="sxs-lookup"><span data-stu-id="dc143-131">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="dc143-132">若要按引用传递值类型实例，请使用 `ref` 关键字。</span><span class="sxs-lookup"><span data-stu-id="dc143-132">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="dc143-133">有关详细信息，请参阅[传递值类型参数](./passing-value-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="dc143-133">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="dc143-134">引用类型的对象传递到方法中时，将传递对对象的引用。</span><span class="sxs-lookup"><span data-stu-id="dc143-134">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="dc143-135">也就是说，该方法接收的不是对象本身，而是指示该对象位置的参数。</span><span class="sxs-lookup"><span data-stu-id="dc143-135">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="dc143-136">如果通过使用此引用更改对象的成员，即使是按值传递该对象，此更改也会反映在调用方法的参数中。</span><span class="sxs-lookup"><span data-stu-id="dc143-136">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="dc143-137">通过使用 `class` 关键字创建引用类型，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="dc143-137">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

<span data-ttu-id="dc143-138">现在，如果将基于此类型的对象传递到方法，则将传递对对象的引用。</span><span class="sxs-lookup"><span data-stu-id="dc143-138">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="dc143-139">下面的示例将 `SampleRefType` 类型的对象传递到 `ModifyObject` 方法：</span><span class="sxs-lookup"><span data-stu-id="dc143-139">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

<span data-ttu-id="dc143-140">该示例执行的内容实质上与先前示例相同，均按值将自变量传递到方法。</span><span class="sxs-lookup"><span data-stu-id="dc143-140">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="dc143-141">但是因为使用了引用类型，结果有所不同。</span><span class="sxs-lookup"><span data-stu-id="dc143-141">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="dc143-142">`ModifyObject` 中所做的对形参 `value` 的 `obj`字段的修改，也会更改 `value` 方法中实参 `rt`的 `TestRefType` 字段。</span><span class="sxs-lookup"><span data-stu-id="dc143-142">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="dc143-143">`TestRefType` 方法显示 33 作为输出。</span><span class="sxs-lookup"><span data-stu-id="dc143-143">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="dc143-144">有关如何通过引用和值传递引用类型的详细信息，请参阅[传递引用类型参数](./passing-reference-type-parameters.md)和[引用类型](../../language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="dc143-144">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="dc143-145">返回值</span><span class="sxs-lookup"><span data-stu-id="dc143-145">Return values</span></span>

<span data-ttu-id="dc143-146">方法可以将值返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="dc143-146">Methods can return a value to the caller.</span></span> <span data-ttu-id="dc143-147">如果列在方法名之前的返回类型不是 `void`，则该方法可通过使用 `return` 关键字返回值。</span><span class="sxs-lookup"><span data-stu-id="dc143-147">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="dc143-148">带 `return` 关键字，后跟与返回类型匹配的值的语句将该值返回到方法调用方。</span><span class="sxs-lookup"><span data-stu-id="dc143-148">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="dc143-149">值可以按值或[按引用](ref-returns.md)返回到调用方，以 C# 7.0 开头。</span><span class="sxs-lookup"><span data-stu-id="dc143-149">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="dc143-150">如果在方法签名中使用 `ref` 关键字且其跟随每个 `return` 关键字，值将按引用返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="dc143-150">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="dc143-151">例如，以下方法签名和返回语句指示该方法按对调用方的引用返回变量名 `estDistance`。</span><span class="sxs-lookup"><span data-stu-id="dc143-151">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="dc143-152">`return` 关键字还会停止执行该方法。</span><span class="sxs-lookup"><span data-stu-id="dc143-152">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="dc143-153">如果返回类型为 `void`，没有值的 `return` 语句仍可用于停止执行该方法。</span><span class="sxs-lookup"><span data-stu-id="dc143-153">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="dc143-154">没有 `return` 关键字，当方法到达代码块结尾时，将停止执行。</span><span class="sxs-lookup"><span data-stu-id="dc143-154">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="dc143-155">具有非空的返回类型的方法都需要使用 `return` 关键字来返回值。</span><span class="sxs-lookup"><span data-stu-id="dc143-155">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="dc143-156">例如，这两种方法都使用 `return` 关键字来返回整数：</span><span class="sxs-lookup"><span data-stu-id="dc143-156">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

<span data-ttu-id="dc143-157">若要使用从方法返回的值，调用方法可以在相同类型的值足够的地方使用该方法调用本身。</span><span class="sxs-lookup"><span data-stu-id="dc143-157">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="dc143-158">也可以将返回值分配给变量。</span><span class="sxs-lookup"><span data-stu-id="dc143-158">You can also assign the return value to a variable.</span></span> <span data-ttu-id="dc143-159">例如，以下两个代码示例实现了相同的目标：</span><span class="sxs-lookup"><span data-stu-id="dc143-159">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

<span data-ttu-id="dc143-160">在这种情况下，使用本地变量 `result`存储值是可选的。</span><span class="sxs-lookup"><span data-stu-id="dc143-160">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="dc143-161">此步骤可以帮助提高代码的可读性，或者如果需要存储该方法整个范围内自变量的原始值，则此步骤可能很有必要。</span><span class="sxs-lookup"><span data-stu-id="dc143-161">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="dc143-162">若要使用按引用从方法返回的值，必须声明 [ref local](ref-returns.md#ref-locals) 变量（如果想要修改其值）。</span><span class="sxs-lookup"><span data-stu-id="dc143-162">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="dc143-163">例如，如果 `Planet.GetEstimatedDistance` 方法按引用返回 <xref:System.Double> 值，则可以将其定义为具有如下所示代码的 ref local 变量：</span><span class="sxs-lookup"><span data-stu-id="dc143-163">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="dc143-164">如果调用函数将数组传递到 `M`，则无需从修改数组内容的方法 `M` 返回多维数组。</span><span class="sxs-lookup"><span data-stu-id="dc143-164">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="dc143-165">你可能会从 `M` 返回生成的数组以获得值的良好样式或功能流，但这是不必要的，因为 C# 按值传递所有引用类型，且数组引用的值是指向数组的指针。</span><span class="sxs-lookup"><span data-stu-id="dc143-165">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="dc143-166">在方法 `M` 中，引用该数组的任何代码都能观察到数组内容的任何更改，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="dc143-166">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

<span data-ttu-id="dc143-167">有关详细信息，请参阅 [return](../../language-reference/keywords/return.md)。</span><span class="sxs-lookup"><span data-stu-id="dc143-167">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="dc143-168">异步方法</span><span class="sxs-lookup"><span data-stu-id="dc143-168">Async methods</span></span>

<span data-ttu-id="dc143-169">通过使用异步功能，你可以调用异步方法而无需使用显式回调，也不需要跨多个方法或 lambda 表达式来手动拆分代码。</span><span class="sxs-lookup"><span data-stu-id="dc143-169">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="dc143-170">如果用 [async](../../language-reference/keywords/async.md) 修饰符标记方法，则可以在该方法中使用 [await](../../language-reference/operators/await.md) 运算符。</span><span class="sxs-lookup"><span data-stu-id="dc143-170">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="dc143-171">当控件到达异步方法中的 await 表达式时，控件将返回到调用方，并在等待任务完成前，方法中进度将一直处于挂起状态。</span><span class="sxs-lookup"><span data-stu-id="dc143-171">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="dc143-172">任务完成后，可以在方法中恢复执行。</span><span class="sxs-lookup"><span data-stu-id="dc143-172">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="dc143-173">异步方法在遇到第一个尚未完成的 awaited 对象或到达异步方法的末尾时（以先发生者为准），将返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="dc143-173">An async method returns to the caller when either it encounters the first awaited object that's not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="dc143-174">异步方法可以具有 <xref:System.Threading.Tasks.Task%601>、 <xref:System.Threading.Tasks.Task>或 void 返回类型。</span><span class="sxs-lookup"><span data-stu-id="dc143-174">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="dc143-175">Void 返回类型主要用于定义需要 void 返回类型的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="dc143-175">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="dc143-176">无法等待返回 void 的异步方法，并且返回 void 方法的调用方无法捕获该方法引发的异常。</span><span class="sxs-lookup"><span data-stu-id="dc143-176">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="dc143-177">在以下示例中， `DelayAsync` 是具有 <xref:System.Threading.Tasks.Task%601>返回类型的异步方法。</span><span class="sxs-lookup"><span data-stu-id="dc143-177">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="dc143-178">`DelayAsync` 具有返回整数的 `return` 语句。</span><span class="sxs-lookup"><span data-stu-id="dc143-178">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="dc143-179">因此， `DelayAsync` 的方法声明必须具有 `Task<int>`的返回类型。</span><span class="sxs-lookup"><span data-stu-id="dc143-179">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="dc143-180">因为返回类型是 `Task<int>`， `await` 中 `DoSomethingAsync` 表达式的计算如以下语句所示得出整数： `int result = await delayTask`。</span><span class="sxs-lookup"><span data-stu-id="dc143-180">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="dc143-181">`Main` 方法就是一个具有 <xref:System.Threading.Tasks.Task> 返回类型的异步方法示例。</span><span class="sxs-lookup"><span data-stu-id="dc143-181">The `Main` method is an example of an async method that has a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="dc143-182">它会转到 `DoSomethingAsync` 方法，因为它使用单个行进行表示，所以可省略 `async` 和 `await` 关键字。</span><span class="sxs-lookup"><span data-stu-id="dc143-182">It goes to the `DoSomethingAsync` method, and because it is expressed with a single line, it can omit the `async` and `await` keywords.</span></span> <span data-ttu-id="dc143-183">因为 `DoSomethingAsync` 是异步方法，调用 `DoSomethingAsync` 的任务必须等待，如以下语句所示： `await DoSomethingAsync();`。</span><span class="sxs-lookup"><span data-stu-id="dc143-183">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span>

:::code language="csharp" source="snippets/classes-and-structs/methods/Program.cs":::

<span data-ttu-id="dc143-184">异步方法不能声明任何 [ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 参数，但是可以调用具有这类参数的方法。</span><span class="sxs-lookup"><span data-stu-id="dc143-184">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="dc143-185">有关异步方法的详细信息，请参阅[使用 Async 和 Await 的异步编程](../concepts/async/index.md)和[异步返回类型](../concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="dc143-185">For more information about async methods, see [Asynchronous programming with async and await](../concepts/async/index.md) and [Async return types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="dc143-186">表达式主体定义</span><span class="sxs-lookup"><span data-stu-id="dc143-186">Expression body definitions</span></span>

<span data-ttu-id="dc143-187">具有立即仅返回表达式结果，或单个语句作为方法主题的方法定义很常见。</span><span class="sxs-lookup"><span data-stu-id="dc143-187">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="dc143-188">以下是使用 `=>`定义此类方法的语法快捷方式：</span><span class="sxs-lookup"><span data-stu-id="dc143-188">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="dc143-189">如果该方法返回 `void` 或是异步方法，则该方法的主体必须是语句表达式（与 lambda 相同）。</span><span class="sxs-lookup"><span data-stu-id="dc143-189">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="dc143-190">对于属性和索引器，两者必须是只读的，并且不使用 `get` 访问器关键字。</span><span class="sxs-lookup"><span data-stu-id="dc143-190">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="dc143-191">迭代器</span><span class="sxs-lookup"><span data-stu-id="dc143-191">Iterators</span></span>

<span data-ttu-id="dc143-192">迭代器对集合执行自定义迭代，如列表或数组。</span><span class="sxs-lookup"><span data-stu-id="dc143-192">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="dc143-193">迭代器使用 [yield return](../../language-reference/keywords/yield.md) 语句返回元素，每次返回一个。</span><span class="sxs-lookup"><span data-stu-id="dc143-193">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="dc143-194">当 [yield return](../../language-reference/keywords/yield.md) 语句到达时，将记住当前在代码中的位置。</span><span class="sxs-lookup"><span data-stu-id="dc143-194">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="dc143-195">下次调用迭代器时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="dc143-195">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="dc143-196">通过使用 [foreach](../../language-reference/keywords/foreach-in.md) 语句从客户端代码调用迭代器。</span><span class="sxs-lookup"><span data-stu-id="dc143-196">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="dc143-197">迭代器的返回类型可以是 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="dc143-197">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="dc143-198">有关更多信息，请参见 [迭代器](../concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="dc143-198">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dc143-199">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="dc143-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="dc143-200">请参阅</span><span class="sxs-lookup"><span data-stu-id="dc143-200">See also</span></span>

- [<span data-ttu-id="dc143-201">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="dc143-201">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dc143-202">类和结构</span><span class="sxs-lookup"><span data-stu-id="dc143-202">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="dc143-203">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="dc143-203">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="dc143-204">静态类和静态类成员</span><span class="sxs-lookup"><span data-stu-id="dc143-204">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="dc143-205">继承</span><span class="sxs-lookup"><span data-stu-id="dc143-205">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="dc143-206">抽象类、密封类及类成员</span><span class="sxs-lookup"><span data-stu-id="dc143-206">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="dc143-207">params</span><span class="sxs-lookup"><span data-stu-id="dc143-207">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="dc143-208">return</span><span class="sxs-lookup"><span data-stu-id="dc143-208">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="dc143-209">out</span><span class="sxs-lookup"><span data-stu-id="dc143-209">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="dc143-210">ref</span><span class="sxs-lookup"><span data-stu-id="dc143-210">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="dc143-211">传递参数</span><span class="sxs-lookup"><span data-stu-id="dc143-211">Passing Parameters</span></span>](passing-parameters.md)
