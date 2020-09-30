---
title: 弃元 - C# 指南
description: 介绍 C# 对弃元的支持（弃元是未赋值的可丢弃变量），以及弃元的使用方式。
ms.technology: csharp-fundamentals
ms.date: 09/22/2020
ms.openlocfilehash: 4de48aebaeb896b198b2e9f2431c6a38ba11469e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869323"
---
# <a name="discards---c-guide"></a><span data-ttu-id="0d08c-103">弃元 - C# 指南</span><span class="sxs-lookup"><span data-stu-id="0d08c-103">Discards - C# Guide</span></span>

<span data-ttu-id="0d08c-104">从 C# 7.0 开始，C# 支持弃元，这是一种在应用程序代码中人为取消使用的临时虚拟变量。</span><span class="sxs-lookup"><span data-stu-id="0d08c-104">Starting with C# 7.0, C# supports discards, which are temporary, dummy variables that are intentionally unused in application code.</span></span> <span data-ttu-id="0d08c-105">弃元相当于未赋值的变量；它们没有值。</span><span class="sxs-lookup"><span data-stu-id="0d08c-105">Discards are equivalent to unassigned variables; they do not have a value.</span></span> <span data-ttu-id="0d08c-106">因为只有一个弃元变量，甚至不为该变量分配存储空间，所以弃元可减少内存分配。</span><span class="sxs-lookup"><span data-stu-id="0d08c-106">Because there is only a single discard variable, and that variable may not even be allocated storage, discards can reduce memory allocations.</span></span> <span data-ttu-id="0d08c-107">因为它们使代码的意图清楚，增强了其可读性和可维护性。</span><span class="sxs-lookup"><span data-stu-id="0d08c-107">Because they make the intent of your code clear, they enhance its readability and maintainability.</span></span>

<span data-ttu-id="0d08c-108">通过将下划线 (`_`) 赋给一个变量作为其变量名，指示该变量为一个占位符变量。</span><span class="sxs-lookup"><span data-stu-id="0d08c-108">You indicate that a variable is a discard by assigning it the underscore (`_`) as its name.</span></span> <span data-ttu-id="0d08c-109">例如，下面的方法调用返回 3 元组，其中的第一个和第二个值是弃元，*area* 是一个以前声明的变量，它将设置为 *GetCityInformation* 返回的相应的第三个部分:</span><span class="sxs-lookup"><span data-stu-id="0d08c-109">For example, the following method call returns a 3-tuple in which the first and second values are discards and *area* is a previously declared variable to be set to the corresponding third component returned by *GetCityInformation*:</span></span>

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

<span data-ttu-id="0d08c-110">在 C# 7.0 及更高版本中，支持在以下上下文的分配中使用弃元：</span><span class="sxs-lookup"><span data-stu-id="0d08c-110">In C# 7.0 and later, discards are supported in assignments in the following contexts:</span></span>

- <span data-ttu-id="0d08c-111">元组和对象[析构](deconstruct.md)。</span><span class="sxs-lookup"><span data-stu-id="0d08c-111">Tuple and object [deconstruction](deconstruct.md).</span></span>
- <span data-ttu-id="0d08c-112">使用 [is](language-reference/keywords/is.md) 和 [switch](language-reference/keywords/switch.md) 的模式匹配。</span><span class="sxs-lookup"><span data-stu-id="0d08c-112">Pattern matching with [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md).</span></span>
- <span data-ttu-id="0d08c-113">对具有 `out` 参数的方法的调用。</span><span class="sxs-lookup"><span data-stu-id="0d08c-113">Calls to methods with `out` parameters.</span></span>
- <span data-ttu-id="0d08c-114">当范围内没有 `_` 时，独立的 `_`。</span><span class="sxs-lookup"><span data-stu-id="0d08c-114">A standalone `_` when no `_` is in scope.</span></span>

<span data-ttu-id="0d08c-115">从 C# 9.0 开始，可以使用弃元指定 Lambda 表达式中不使用的输入参数。</span><span class="sxs-lookup"><span data-stu-id="0d08c-115">Beginning with C# 9.0, you can use discards to specify unused input parameters of a lambda expression.</span></span> <span data-ttu-id="0d08c-116">有关详细信息，请参阅 [Lambda 表达式](language-reference/operators/lambda-expressions.md)一文中的 [Lambda 表达式的输入参数](language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression)一节。</span><span class="sxs-lookup"><span data-stu-id="0d08c-116">For more information, see the [Input parameters of a lambda expression](language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression) section of the [Lambda expressions](language-reference/operators/lambda-expressions.md) article.</span></span>

<span data-ttu-id="0d08c-117">当 `_` 是有效占位符时，尝试检索其值或在赋值操作中使用它时会生成编译器错误 CS0301：当前上下文中不存在名称 "\_"。</span><span class="sxs-lookup"><span data-stu-id="0d08c-117">When `_` is a valid discard, attempting to retrieve its value or use it in an assignment operation generates compiler error CS0301, "The name '\_' does not exist in the current context".</span></span> <span data-ttu-id="0d08c-118">这是因为 `_` 未赋值，甚至可能未分配存储位置。</span><span class="sxs-lookup"><span data-stu-id="0d08c-118">This is because `_` is not assigned a value, and may not even be assigned a storage location.</span></span> <span data-ttu-id="0d08c-119">如果它是一个实际变量，则不能像之前的示例那样对多个值使用占位符。</span><span class="sxs-lookup"><span data-stu-id="0d08c-119">If it were an actual variable, you could not discard more than one value, as the previous example did.</span></span>

## <a name="tuple-and-object-deconstruction"></a><span data-ttu-id="0d08c-120">元组和对象析构</span><span class="sxs-lookup"><span data-stu-id="0d08c-120">Tuple and object deconstruction</span></span>

<span data-ttu-id="0d08c-121">如果应用程序代码使用某些元组元素，但忽略其他元素，这时使用占位符来处理元组就会特别有用。</span><span class="sxs-lookup"><span data-stu-id="0d08c-121">Discards are particularly useful in working with tuples when your application code uses some tuple elements but ignores others.</span></span> <span data-ttu-id="0d08c-122">例如，以下的 `QueryCityDataForYears` 方法返回一个 6 元组，包含城市名称、城市面积、一个年份、该年份的城市人口、另一个年份及该年份的城市人口。</span><span class="sxs-lookup"><span data-stu-id="0d08c-122">For example, the following `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="0d08c-123">该示例显示了两个年份之间人口的变化。</span><span class="sxs-lookup"><span data-stu-id="0d08c-123">The example shows the change in population between those two years.</span></span> <span data-ttu-id="0d08c-124">对于元组提供的数据，我们不关注城市面积，并在一开始就知道城市名称和两个日期。</span><span class="sxs-lookup"><span data-stu-id="0d08c-124">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="0d08c-125">因此，我们只关注存储在元组中的两个人口数量值，可将其余值作为占位符处理。</span><span class="sxs-lookup"><span data-stu-id="0d08c-125">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="0d08c-126">有关使用占位符析构元组的详细信息，请参阅 [析构元组和其他类型](deconstruct.md#deconstructing-tuple-elements-with-discards)。</span><span class="sxs-lookup"><span data-stu-id="0d08c-126">For more information on deconstructing tuples with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-tuple-elements-with-discards).</span></span>

<span data-ttu-id="0d08c-127">类、结构或接口的 `Deconstruct` 方法还允许从对象中检索和析构一组特定的数据。</span><span class="sxs-lookup"><span data-stu-id="0d08c-127">The `Deconstruct` method of a class, structure, or interface also allows you to retrieve and deconstruct a specific set of data from an object.</span></span> <span data-ttu-id="0d08c-128">如果想只使用析构值的一个子集时，可使用弃元。</span><span class="sxs-lookup"><span data-stu-id="0d08c-128">You can use discards when you are interested in working with only a subset of the deconstructed values.</span></span> <span data-ttu-id="0d08c-129">以下示例将 `Person` 对象析构为四个字符串（名字、姓氏、城市和省/市/自治区），但舍弃姓氏和省/市/自治区。</span><span class="sxs-lookup"><span data-stu-id="0d08c-129">The following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state), but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

<span data-ttu-id="0d08c-130">有关使用弃元析构用户定义的类型的详细信息，请参阅 [析构元组和其他类型](deconstruct.md#deconstructing-a-user-defined-type-with-discards)。</span><span class="sxs-lookup"><span data-stu-id="0d08c-130">For more information on deconstructing user-defined types with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span></span>

## <a name="pattern-matching-with-switch-and-is"></a><span data-ttu-id="0d08c-131">使用 `switch` 和 `is` 的模式匹配</span><span class="sxs-lookup"><span data-stu-id="0d08c-131">Pattern matching with `switch` and `is`</span></span>

<span data-ttu-id="0d08c-132">弃元模式可通过 [is](language-reference/keywords/is.md) 和 [switch](language-reference/keywords/switch.md) 关键字用于模式匹配。\*\*</span><span class="sxs-lookup"><span data-stu-id="0d08c-132">The *discard pattern* can be used in pattern matching with the [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md) keywords.</span></span> <span data-ttu-id="0d08c-133">每个表达式始终匹配弃元模式。</span><span class="sxs-lookup"><span data-stu-id="0d08c-133">Every expression always matches the discard pattern.</span></span>

<span data-ttu-id="0d08c-134">以下示例定义了一个 `ProvidesFormatInfo` 方法，该方法使用 [is](language-reference/keywords/is.md) 语句来确定对象是否提供 <xref:System.IFormatProvider> 实现并测试对象是否为 `null`。</span><span class="sxs-lookup"><span data-stu-id="0d08c-134">The following example defines a `ProvidesFormatInfo` method that uses [is](language-reference/keywords/is.md) statements to determine whether an object provides an <xref:System.IFormatProvider> implementation and tests whether the object is `null`.</span></span> <span data-ttu-id="0d08c-135">它还使用占位符模式来处理任何其他类型的非 null 对象。</span><span class="sxs-lookup"><span data-stu-id="0d08c-135">It also uses the discard pattern to handle non-null objects of any other type.</span></span>

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a><span data-ttu-id="0d08c-136">使用 out 参数调用方法</span><span class="sxs-lookup"><span data-stu-id="0d08c-136">Calls to methods with out parameters</span></span>

<span data-ttu-id="0d08c-137">当调用 `Deconstruct` 方法来析构用户定义类型（类、结构或接口的实例）时，可使用占位符表示单个 `out` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="0d08c-137">When calling the `Deconstruct` method to deconstruct a user-defined type (an instance of a class, structure, or interface), you can discard the values of individual `out` arguments.</span></span> <span data-ttu-id="0d08c-138">但当使用 out 参数调用任何方法时，也可使用占位符表示 `out` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="0d08c-138">But you can also discard the value of `out` arguments when calling any method with an out parameter.</span></span>

<span data-ttu-id="0d08c-139">以下示例调用 [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) 方法来确定日期的字符串表示形式在当前区域性中是否有效。</span><span class="sxs-lookup"><span data-stu-id="0d08c-139">The following example calls the [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) method to determine whether the string representation of a date is valid in the current culture.</span></span> <span data-ttu-id="0d08c-140">因为该示例侧重验证日期字符串，而不是解析它来提取日期，所以方法的 `out` 参数为占位符。</span><span class="sxs-lookup"><span data-stu-id="0d08c-140">Because the example is concerned only with validating the date string and not with parsing it to extract the date, the `out` argument to the method is a discard.</span></span>

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a><span data-ttu-id="0d08c-141">独立弃元</span><span class="sxs-lookup"><span data-stu-id="0d08c-141">A standalone discard</span></span>

<span data-ttu-id="0d08c-142">可使用独立弃元来指示要忽略的任何变量。</span><span class="sxs-lookup"><span data-stu-id="0d08c-142">You can use a standalone discard to indicate any variable that you choose to ignore.</span></span> <span data-ttu-id="0d08c-143">以下示例使用独立占位符来忽略异步操作返回的 <xref:System.Threading.Tasks.Task> 对象。</span><span class="sxs-lookup"><span data-stu-id="0d08c-143">The following example uses a standalone discard to ignore the <xref:System.Threading.Tasks.Task> object returned by an asynchronous operation.</span></span> <span data-ttu-id="0d08c-144">这一操作的效果等同于抑制操作即将完成时所引发的异常。</span><span class="sxs-lookup"><span data-stu-id="0d08c-144">This has the effect of suppressing the exception that the operation throws as it is about to complete.</span></span>

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

<span data-ttu-id="0d08c-145">请注意，`_` 也是有效标识符。</span><span class="sxs-lookup"><span data-stu-id="0d08c-145">Note that `_` is also a valid identifier.</span></span> <span data-ttu-id="0d08c-146">当在支持的上下文之外使用时，`_` 不视为占位符，而视为有效变量。</span><span class="sxs-lookup"><span data-stu-id="0d08c-146">When used outside of a supported context, `_` is treated not as a discard but as a valid variable.</span></span> <span data-ttu-id="0d08c-147">如果名为 `_` 的标识符已在范围内，则使用 `_` 作为独立占位符可能导致：</span><span class="sxs-lookup"><span data-stu-id="0d08c-147">If an identifier named `_` is already in scope, the use of `_` as a standalone discard can result in:</span></span>

- <span data-ttu-id="0d08c-148">将预期的占位符的值赋给范围内 `_` 变量，会导致该变量的值被意外修改。</span><span class="sxs-lookup"><span data-stu-id="0d08c-148">Accidental modification of the value of the in-scope `_` variable by assigning it the value of the intended discard.</span></span> <span data-ttu-id="0d08c-149">例如：</span><span class="sxs-lookup"><span data-stu-id="0d08c-149">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- <span data-ttu-id="0d08c-150">因违反类型安全而发生的编译器错误。</span><span class="sxs-lookup"><span data-stu-id="0d08c-150">A compiler error for violating type safety.</span></span> <span data-ttu-id="0d08c-151">例如：</span><span class="sxs-lookup"><span data-stu-id="0d08c-151">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- <span data-ttu-id="0d08c-152">编译器错误 CS0136：“无法在此范围中声明名为“\_”的局部变量或参数，因为该名称用于在封闭的局部范围中定义局部变量或参数”。</span><span class="sxs-lookup"><span data-stu-id="0d08c-152">Compiler error CS0136, "A local or parameter named '\_' cannot be declared in this scope because that name is used in an enclosing local scope to define a local or parameter."</span></span> <span data-ttu-id="0d08c-153">例如：</span><span class="sxs-lookup"><span data-stu-id="0d08c-153">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a><span data-ttu-id="0d08c-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d08c-154">See also</span></span>

- [<span data-ttu-id="0d08c-155">析构元组和其他类型</span><span class="sxs-lookup"><span data-stu-id="0d08c-155">Deconstructing tuples and other types</span></span>](deconstruct.md)
- [<span data-ttu-id="0d08c-156">`is` 关键字</span><span class="sxs-lookup"><span data-stu-id="0d08c-156">`is` keyword</span></span>](language-reference/keywords/is.md)
- [<span data-ttu-id="0d08c-157">`switch` 关键字</span><span class="sxs-lookup"><span data-stu-id="0d08c-157">`switch` keyword</span></span>](language-reference/keywords/switch.md)
