---
title: 使用索引器 - C# 编程指南
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: e742e4dd5ea92ec3baf37c915e024e713022b7b6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416243"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="8daa2-102">使用索引器（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="8daa2-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="8daa2-103">索引器使你可从语法上方便地创建[类](../../language-reference/keywords/class.md)、[结构](../../language-reference/builtin-types/struct.md)或[接口](../../language-reference/keywords/interface.md)，以便客户端应用程序可以像访问数组一样访问它们。</span><span class="sxs-lookup"><span data-stu-id="8daa2-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access as an array.</span></span> <span data-ttu-id="8daa2-104">编译器将生成一个 `Item` 属性（或者如果存在 <xref:System.Runtime.CompilerServices.IndexerNameAttribute>，也可以生成一个命名属性）和适当的访问器方法。</span><span class="sxs-lookup"><span data-stu-id="8daa2-104">The compiler will generate an `Item` property (or an alternatively named property if <xref:System.Runtime.CompilerServices.IndexerNameAttribute> is present), and the appropriate accessor methods.</span></span> <span data-ttu-id="8daa2-105">在主要目标是封装内部集合或数组的类型中，常常要实现索引器。</span><span class="sxs-lookup"><span data-stu-id="8daa2-105">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="8daa2-106">例如，假设有一个类 `TempRecord`，它表示 24 小时的周期内在 10 个不同时间点所记录的温度（单位为华氏度）。</span><span class="sxs-lookup"><span data-stu-id="8daa2-106">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24-hour period.</span></span> <span data-ttu-id="8daa2-107">此类包含一个 `float[]` 类型的数组 `temps`，用于存储温度值。</span><span class="sxs-lookup"><span data-stu-id="8daa2-107">The class contains a `temps` array of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="8daa2-108">通过在此类中实现索引器，客户端可采用 `float temp = tempRecord[4]` 的形式（而非 `float temp = tempRecord.temps[4]`）访问 `TempRecord` 实例中的温度。</span><span class="sxs-lookup"><span data-stu-id="8daa2-108">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tempRecord[4]` instead of as `float temp = tempRecord.temps[4]`.</span></span> <span data-ttu-id="8daa2-109">索引器表示法不但简化了客户端应用程序的语法；还使类及其目标更容易直观地为其它开发者所理解。</span><span class="sxs-lookup"><span data-stu-id="8daa2-109">The indexer notation not only simplifies the syntax for client applications; it also makes the class, and its purpose more intuitive for other developers to understand.</span></span>

<span data-ttu-id="8daa2-110">若要在类或结构上声明索引器，请使用 [this](../../language-reference/keywords/this.md) 关键字，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="8daa2-110">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> <span data-ttu-id="8daa2-111">通过声明索引器，可自动在对象上生成一个名为 `Item` 的属性。</span><span class="sxs-lookup"><span data-stu-id="8daa2-111">Declaring an indexer will automatically generate a property named `Item` on the object.</span></span> <span data-ttu-id="8daa2-112">无法从实例[成员访问表达式](../../language-reference/operators/member-access-operators.md#member-access-expression-)直接访问 `Item` 属性。</span><span class="sxs-lookup"><span data-stu-id="8daa2-112">The `Item` property is not directly accessible from the instance [member access expression](../../language-reference/operators/member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="8daa2-113">此外，如果通过索引器向对象添加自己的 `Item` 属性，则将收到 [CS0102 编译器错误](../../misc/cs0102.md)。</span><span class="sxs-lookup"><span data-stu-id="8daa2-113">Additionally, if you add your own `Item` property to an object with an indexer, you'll get a [CS0102 compiler error](../../misc/cs0102.md).</span></span> <span data-ttu-id="8daa2-114">要避免此错误，请使用 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> 来重命名索引器，详细信息如下所示。</span><span class="sxs-lookup"><span data-stu-id="8daa2-114">To avoid this error, use the <xref:System.Runtime.CompilerServices.IndexerNameAttribute> rename the indexer as detailed below.</span></span>

## <a name="remarks"></a><span data-ttu-id="8daa2-115">备注</span><span class="sxs-lookup"><span data-stu-id="8daa2-115">Remarks</span></span>

<span data-ttu-id="8daa2-116">索引器及其参数的类型必须至少具有和索引器相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="8daa2-116">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="8daa2-117">有关可访问性级别的详细信息，请参阅[访问修饰符](../../language-reference/keywords/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="8daa2-117">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>

<span data-ttu-id="8daa2-118">有关如何在接口上使用索引器的详细信息，请参阅[接口索引器](./indexers-in-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="8daa2-118">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>

<span data-ttu-id="8daa2-119">索引器的签名由其形参的数目和类型所组成。</span><span class="sxs-lookup"><span data-stu-id="8daa2-119">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="8daa2-120">它不包含索引器类型或形参的名称。</span><span class="sxs-lookup"><span data-stu-id="8daa2-120">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="8daa2-121">如果要在相同类中声明多个索引器，则它们的签名必须不同。</span><span class="sxs-lookup"><span data-stu-id="8daa2-121">If you declare more than one indexer in the same class, they must have different signatures.</span></span>

<span data-ttu-id="8daa2-122">索引器值不分类为变量；因此，无法将索引器值作为 [ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 参数来传递。</span><span class="sxs-lookup"><span data-stu-id="8daa2-122">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>

<span data-ttu-id="8daa2-123">若要使索引器的名称可为其他语言所用，请使用 <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="8daa2-123">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

<span data-ttu-id="8daa2-124">此索引器被索引器名称属性重写，因此其名称将为 `TheItem`。</span><span class="sxs-lookup"><span data-stu-id="8daa2-124">This indexer will have the name `TheItem`, as it is overridden by the indexer name attribute.</span></span> <span data-ttu-id="8daa2-125">默认情况下，默认名称为 `Item`。</span><span class="sxs-lookup"><span data-stu-id="8daa2-125">By default, the indexer name is `Item`.</span></span>

## <a name="example-1"></a><span data-ttu-id="8daa2-126">示例 1</span><span class="sxs-lookup"><span data-stu-id="8daa2-126">Example 1</span></span>

<span data-ttu-id="8daa2-127">下列示例演示如何声明专用数组字段 `temps` 和索引器。</span><span class="sxs-lookup"><span data-stu-id="8daa2-127">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="8daa2-128">索引器可以实现对实例 `tempRecord[i]` 的直接访问。</span><span class="sxs-lookup"><span data-stu-id="8daa2-128">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="8daa2-129">若不使用索引器，则将数组声明为[公共](../../language-reference/keywords/public.md)成员，并直接访问其成员 `tempRecord.temps[i]`。</span><span class="sxs-lookup"><span data-stu-id="8daa2-129">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

<span data-ttu-id="8daa2-130">请注意，当评估索引器访问时（例如在 `Console.Write` 语句中），将调用 [get](../../language-reference/keywords/get.md) 访问器。</span><span class="sxs-lookup"><span data-stu-id="8daa2-130">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="8daa2-131">因此，如果不存在 `get` 访问器，则会发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="8daa2-131">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a><span data-ttu-id="8daa2-132">使用其他值进行索引</span><span class="sxs-lookup"><span data-stu-id="8daa2-132">Indexing using other values</span></span>

<span data-ttu-id="8daa2-133">C# 不将索引参数类型限制为整数。</span><span class="sxs-lookup"><span data-stu-id="8daa2-133">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="8daa2-134">例如，对索引器使用字符串可能有用。</span><span class="sxs-lookup"><span data-stu-id="8daa2-134">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="8daa2-135">通过搜索集合内的字符串并返回相应的值，可以实现此类索引器。</span><span class="sxs-lookup"><span data-stu-id="8daa2-135">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="8daa2-136">访问器可被重载，因此字符串和整数版本可以共存。</span><span class="sxs-lookup"><span data-stu-id="8daa2-136">As accessors can be overloaded, the string and integer versions can coexist.</span></span>

## <a name="example-2"></a><span data-ttu-id="8daa2-137">示例 2</span><span class="sxs-lookup"><span data-stu-id="8daa2-137">Example 2</span></span>

<span data-ttu-id="8daa2-138">下面的示例声明了存储星期几的类。</span><span class="sxs-lookup"><span data-stu-id="8daa2-138">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="8daa2-139">`get` 访问器采用字符串（星期几）并返回对应的整数。</span><span class="sxs-lookup"><span data-stu-id="8daa2-139">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="8daa2-140">例如，“Sunday”返回 0，“Monday”返回 1，依此类推。</span><span class="sxs-lookup"><span data-stu-id="8daa2-140">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a><span data-ttu-id="8daa2-141">使用示例 2</span><span class="sxs-lookup"><span data-stu-id="8daa2-141">Consuming example 2</span></span>

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a><span data-ttu-id="8daa2-142">示例 3</span><span class="sxs-lookup"><span data-stu-id="8daa2-142">Example 3</span></span>

<span data-ttu-id="8daa2-143">下面的示例声明了使用 <xref:System.DayOfWeek?displayProperty=fullName> 存储星期几的类。</span><span class="sxs-lookup"><span data-stu-id="8daa2-143">The following example declares a class that stores the days of the week using the <xref:System.DayOfWeek?displayProperty=fullName> enum.</span></span> <span data-ttu-id="8daa2-144">`get` 访问器采用 `DayOfWeek`（表示星期几的值）并返回对应的整数。</span><span class="sxs-lookup"><span data-stu-id="8daa2-144">A `get` accessor takes a `DayOfWeek`, the value of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="8daa2-145">例如，`DayOfWeek.Sunday` 返回 0，`DayOfWeek.Monday` 返回 1，依此类推。</span><span class="sxs-lookup"><span data-stu-id="8daa2-145">For example, `DayOfWeek.Sunday` returns 0, `DayOfWeek.Monday` returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a><span data-ttu-id="8daa2-146">使用示例 3</span><span class="sxs-lookup"><span data-stu-id="8daa2-146">Consuming example 3</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a><span data-ttu-id="8daa2-147">可靠编程</span><span class="sxs-lookup"><span data-stu-id="8daa2-147">Robust programming</span></span>

<span data-ttu-id="8daa2-148">提高索引器的安全性和可靠性有两种主要方法：</span><span class="sxs-lookup"><span data-stu-id="8daa2-148">There are two main ways in which the security and reliability of indexers can be improved:</span></span>

- <span data-ttu-id="8daa2-149">请确保结合某一类型的错误处理策略，以处理万一客户端代码传入无效索引值的情况。</span><span class="sxs-lookup"><span data-stu-id="8daa2-149">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="8daa2-150">在本主题前面的第一个示例中，TempRecord 类提供了 Length 属性，使客户端代码能在将输入传递给索引器之前对其进行验证。</span><span class="sxs-lookup"><span data-stu-id="8daa2-150">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="8daa2-151">也可将错误处理代码放入索引器自身内部。</span><span class="sxs-lookup"><span data-stu-id="8daa2-151">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="8daa2-152">请确保为用户记录在索引器的访问器中引发的任何异常。</span><span class="sxs-lookup"><span data-stu-id="8daa2-152">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>

- <span data-ttu-id="8daa2-153">在可接受的程度内，为 [get](../../language-reference/keywords/get.md) 和 [set](../../language-reference/keywords/set.md) 访问器的可访问性设置尽可能多的限制。</span><span class="sxs-lookup"><span data-stu-id="8daa2-153">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="8daa2-154">这一点对 `set` 访问器尤为重要。</span><span class="sxs-lookup"><span data-stu-id="8daa2-154">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="8daa2-155">有关详细信息，请参阅[限制访问器可访问性](../classes-and-structs/restricting-accessor-accessibility.md)。</span><span class="sxs-lookup"><span data-stu-id="8daa2-155">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8daa2-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="8daa2-156">See also</span></span>

- [<span data-ttu-id="8daa2-157">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="8daa2-157">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8daa2-158">索引器</span><span class="sxs-lookup"><span data-stu-id="8daa2-158">Indexers</span></span>](./index.md)
- [<span data-ttu-id="8daa2-159">属性</span><span class="sxs-lookup"><span data-stu-id="8daa2-159">Properties</span></span>](../classes-and-structs/properties.md)
