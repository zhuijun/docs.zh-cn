---
title: for 语句 - C# 参考
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: db7cecc697a9cc9e5ff6b94b78747b799ed7e505
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401896"
---
# <a name="for-c-reference"></a><span data-ttu-id="70354-102">for（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="70354-102">for (C# reference)</span></span>

<span data-ttu-id="70354-103">在指定的布尔表达式的计算结果为 `true` 时，`for` 语句会执行一条语句或一个语句块。</span><span class="sxs-lookup"><span data-stu-id="70354-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="70354-104">在 `for` 语句块中的任何点上，可以使用 [break](break.md) 语句中断循环，或者可以使用 [continue](continue.md) 语句继续执行到循环中的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="70354-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="70354-105">还可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 语句退出 `for` 循环。</span><span class="sxs-lookup"><span data-stu-id="70354-105">You can also exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="70354-106">`for` 语句的结构</span><span class="sxs-lookup"><span data-stu-id="70354-106">Structure of the `for` statement</span></span>

<span data-ttu-id="70354-107">`for` 语句定义初始化表达式、条件和迭代器部分    ：</span><span class="sxs-lookup"><span data-stu-id="70354-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="70354-108">三个部分都是可选的。</span><span class="sxs-lookup"><span data-stu-id="70354-108">All three sections are optional.</span></span> <span data-ttu-id="70354-109">循环体是一个语句或一个语句块。</span><span class="sxs-lookup"><span data-stu-id="70354-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="70354-110">以下示例显示定义了所有部分的 `for`：</span><span class="sxs-lookup"><span data-stu-id="70354-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](snippets/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="70354-111">“初始化表达式”部分 </span><span class="sxs-lookup"><span data-stu-id="70354-111">The *initializer* section</span></span>

<span data-ttu-id="70354-112">“初始化表达式”部分的语句仅在进入循环前执行一次  。</span><span class="sxs-lookup"><span data-stu-id="70354-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="70354-113">“初始化表达式”部分是下列内容之一  ：</span><span class="sxs-lookup"><span data-stu-id="70354-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="70354-114">本地循环变量的声明和初始化，不能从循环外访问。</span><span class="sxs-lookup"><span data-stu-id="70354-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="70354-115">以下列表中显示用逗号分隔的零个或多个语句表达式：</span><span class="sxs-lookup"><span data-stu-id="70354-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="70354-116">[赋值](../operators/assignment-operator.md)语句</span><span class="sxs-lookup"><span data-stu-id="70354-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="70354-117">方法的调用</span><span class="sxs-lookup"><span data-stu-id="70354-117">invocation of a method</span></span>

  - <span data-ttu-id="70354-118">为 [increment](../operators/arithmetic-operators.md#increment-operator-) 表达式添加前缀或后缀，如 `++i` 或 `i++`</span><span class="sxs-lookup"><span data-stu-id="70354-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="70354-119">为 [decrement](../operators/arithmetic-operators.md#decrement-operator---) 表达式添加前缀或后缀，如 `--i` 或 `i--`</span><span class="sxs-lookup"><span data-stu-id="70354-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="70354-120">通过使用 [new](../operators/new-operator.md) 运算符来创建对象</span><span class="sxs-lookup"><span data-stu-id="70354-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="70354-121">[await](../operators/await.md) 表达式</span><span class="sxs-lookup"><span data-stu-id="70354-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="70354-122">上例中的“初始化表达式”部分声明和初始化本地循环变量 `i` ：</span><span class="sxs-lookup"><span data-stu-id="70354-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="70354-123">“条件”部分 </span><span class="sxs-lookup"><span data-stu-id="70354-123">The *condition* section</span></span>

<span data-ttu-id="70354-124">“条件”部分（如果存在）必须为布尔表达式  。</span><span class="sxs-lookup"><span data-stu-id="70354-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="70354-125">在每次循环迭代前计算该表达式。</span><span class="sxs-lookup"><span data-stu-id="70354-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="70354-126">如果“条件”部分不存在或者布尔表达式的计算结果为 `true`，则执行下一个循环迭代；否则退出循环  。</span><span class="sxs-lookup"><span data-stu-id="70354-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="70354-127">上例中的“条件”部分确定循环是否根据本地循环变量的值终止  ：</span><span class="sxs-lookup"><span data-stu-id="70354-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="70354-128">“迭代器”部分 </span><span class="sxs-lookup"><span data-stu-id="70354-128">The *iterator* section</span></span>

<span data-ttu-id="70354-129">“迭代器”部分定义循环主体的每次迭代后将执行的操作  。</span><span class="sxs-lookup"><span data-stu-id="70354-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="70354-130">“迭代器”部分包含用逗号分隔的零个或多个以下语句表达式  ：</span><span class="sxs-lookup"><span data-stu-id="70354-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="70354-131">[赋值](../operators/assignment-operator.md)语句</span><span class="sxs-lookup"><span data-stu-id="70354-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="70354-132">方法的调用</span><span class="sxs-lookup"><span data-stu-id="70354-132">invocation of a method</span></span>

- <span data-ttu-id="70354-133">为 [increment](../operators/arithmetic-operators.md#increment-operator-) 表达式添加前缀或后缀，如 `++i` 或 `i++`</span><span class="sxs-lookup"><span data-stu-id="70354-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="70354-134">为 [decrement](../operators/arithmetic-operators.md#decrement-operator---) 表达式添加前缀或后缀，如 `--i` 或 `i--`</span><span class="sxs-lookup"><span data-stu-id="70354-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="70354-135">通过使用 [new](../operators/new-operator.md) 运算符来创建对象</span><span class="sxs-lookup"><span data-stu-id="70354-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="70354-136">[await](../operators/await.md) 表达式</span><span class="sxs-lookup"><span data-stu-id="70354-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="70354-137">上例中的“迭代器”部分增加本地循环变量  ：</span><span class="sxs-lookup"><span data-stu-id="70354-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="70354-138">示例</span><span class="sxs-lookup"><span data-stu-id="70354-138">Examples</span></span>

<span data-ttu-id="70354-139">下面的示例阐释了几种不太常见的 `for` 语句部分的使用情况：为“初始化表达式”部分中的外部循环变量赋值、同时在“初始化表达式”部分和“迭代器”部分中调用一种方法，以及更改迭代器部分中的两个变量的值     。</span><span class="sxs-lookup"><span data-stu-id="70354-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="70354-140">选择“运行”以运行示例代码  。</span><span class="sxs-lookup"><span data-stu-id="70354-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="70354-141">然后可以修改代码并再次运行它。</span><span class="sxs-lookup"><span data-stu-id="70354-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](snippets/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="70354-142">以下示例定义无限 `for` 循环：</span><span class="sxs-lookup"><span data-stu-id="70354-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](snippets/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="70354-143">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="70354-143">C# language specification</span></span>

<span data-ttu-id="70354-144">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的 [for 语句](~/_csharplang/spec/statements.md#the-for-statement)部分。</span><span class="sxs-lookup"><span data-stu-id="70354-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="70354-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="70354-145">See also</span></span>

- [<span data-ttu-id="70354-146">C# 参考</span><span class="sxs-lookup"><span data-stu-id="70354-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="70354-147">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="70354-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="70354-148">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="70354-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="70354-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="70354-149">foreach, in</span></span>](foreach-in.md)
