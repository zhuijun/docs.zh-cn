---
title: 析构元组和其他类型
description: 了解如何析构元组和其他类型。
ms.technology: csharp-fundamentals
ms.date: 11/23/2017
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 8defd75a7cdff3490d2b0a6097ec2a898576e113
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174161"
---
# <a name="deconstructing-tuples-and-other-types"></a><span data-ttu-id="ad683-103">析构元组和其他类型</span><span class="sxs-lookup"><span data-stu-id="ad683-103">Deconstructing tuples and other types</span></span>

<span data-ttu-id="ad683-104">元组提供一种从方法调用中检索多个值的轻量级方法。</span><span class="sxs-lookup"><span data-stu-id="ad683-104">A tuple provides a lightweight way to retrieve multiple values from a method call.</span></span> <span data-ttu-id="ad683-105">但是，一旦检索到元组，就必须处理它的各个元素。</span><span class="sxs-lookup"><span data-stu-id="ad683-105">But once you retrieve the tuple, you have to handle its individual elements.</span></span> <span data-ttu-id="ad683-106">按元素逐个执行此操作会比较麻烦，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="ad683-106">Doing this on an element-by-element basis is cumbersome, as the following example shows.</span></span> <span data-ttu-id="ad683-107">`QueryCityData` 方法返回一个 3 元组，并通过单独的操作将其每个元素分配给一个变量。</span><span class="sxs-lookup"><span data-stu-id="ad683-107">The `QueryCityData` method returns a 3-tuple, and each of its elements is assigned to a variable in a separate operation.</span></span>

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

<span data-ttu-id="ad683-108">从对象检索多个字段值和属性值可能同样麻烦：必须按成员逐个将字段值或属性值赋给一个变量。</span><span class="sxs-lookup"><span data-stu-id="ad683-108">Retrieving multiple field and property values from an object can be equally cumbersome: you have to assign a field or property value to a variable on a member-by-member basis.</span></span>

<span data-ttu-id="ad683-109">从 C# 7.0 开始，用户可从元组中检索多个元素，或在单个析构操作中从对象检索多个字段值、属性值和计算值。</span><span class="sxs-lookup"><span data-stu-id="ad683-109">Starting with C# 7.0, you can retrieve multiple elements from a tuple or retrieve multiple field, property, and computed values from an object in a single *deconstruct* operation.</span></span> <span data-ttu-id="ad683-110">析构元组时，将其元素分配给各个变量。</span><span class="sxs-lookup"><span data-stu-id="ad683-110">When you deconstruct a tuple, you assign its elements to individual variables.</span></span> <span data-ttu-id="ad683-111">析构对象时，将选定值分配给各个变量。</span><span class="sxs-lookup"><span data-stu-id="ad683-111">When you deconstruct an object, you assign selected values to individual variables.</span></span>

## <a name="deconstructing-a-tuple"></a><span data-ttu-id="ad683-112">析构元组</span><span class="sxs-lookup"><span data-stu-id="ad683-112">Deconstructing a tuple</span></span>

<span data-ttu-id="ad683-113">C# 提供内置的元组析构支持，可在单个操作中解包一个元组中的所有项。</span><span class="sxs-lookup"><span data-stu-id="ad683-113">C# features built-in support for deconstructing tuples, which lets you unpackage all the items in a tuple in a single operation.</span></span> <span data-ttu-id="ad683-114">用于析构元组的常规语法与用于定义元组的语法相似：将要向其分配元素的变量放在赋值语句左侧的括号中。</span><span class="sxs-lookup"><span data-stu-id="ad683-114">The general syntax for deconstructing a tuple is similar to the syntax for defining one: you enclose the variables to which each element is to be assigned in parentheses in the left side of an assignment statement.</span></span> <span data-ttu-id="ad683-115">例如，以下语句将 4 元组的元素分配给 4 个单独的变量：</span><span class="sxs-lookup"><span data-stu-id="ad683-115">For example, the following statement assigns the elements of a 4-tuple to four separate variables:</span></span>

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

<span data-ttu-id="ad683-116">有三种方法可用于析构元组：</span><span class="sxs-lookup"><span data-stu-id="ad683-116">There are three ways to deconstruct a tuple:</span></span>

- <span data-ttu-id="ad683-117">可以在括号内显式声明每个字段的类型。</span><span class="sxs-lookup"><span data-stu-id="ad683-117">You can explicitly declare the type of each field inside parentheses.</span></span> <span data-ttu-id="ad683-118">以下示例使用此方法来析构由 `QueryCityData` 方法返回的 3 元组。</span><span class="sxs-lookup"><span data-stu-id="ad683-118">The following example uses this approach to deconstruct the 3-tuple returned by the `QueryCityData` method.</span></span>

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- <span data-ttu-id="ad683-119">可使用 `var` 关键字，以便 C# 推断每个变量的类型。</span><span class="sxs-lookup"><span data-stu-id="ad683-119">You can use the `var` keyword so that C# infers the type of each variable.</span></span> <span data-ttu-id="ad683-120">将 `var` 关键字放在括号外。</span><span class="sxs-lookup"><span data-stu-id="ad683-120">You place the `var` keyword outside of the parentheses.</span></span> <span data-ttu-id="ad683-121">以下示例在析构由 `QueryCityData` 方法返回的 3 元组时使用类型推理。</span><span class="sxs-lookup"><span data-stu-id="ad683-121">The following example uses type inference when deconstructing the 3-tuple returned by the `QueryCityData` method.</span></span>

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    <span data-ttu-id="ad683-122">还可在括号内将 `var` 关键字单独与任一或全部变量声明结合使用。</span><span class="sxs-lookup"><span data-stu-id="ad683-122">You can also use the `var` keyword individually with any or all of the variable declarations inside the parentheses.</span></span>

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    <span data-ttu-id="ad683-123">这很麻烦，不建议这样做。</span><span class="sxs-lookup"><span data-stu-id="ad683-123">This is cumbersome and is not recommended.</span></span>

- <span data-ttu-id="ad683-124">最后，可将元组析构到已声明的变量中。</span><span class="sxs-lookup"><span data-stu-id="ad683-124">Lastly, you may deconstruct the tuple into variables that have already been declared.</span></span>

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

<span data-ttu-id="ad683-125">请注意，即使元组中的每个字段都具有相同的类型，也不能在括号外指定特定类型。</span><span class="sxs-lookup"><span data-stu-id="ad683-125">Note that you cannot specify a specific type outside the parentheses even if every field in the tuple has the same type.</span></span> <span data-ttu-id="ad683-126">这会生成编译器错误 CS8136：“析构 var (...) 形式不允许对 var 使用特定类型。”</span><span class="sxs-lookup"><span data-stu-id="ad683-126">This generates compiler error CS8136, "Deconstruction 'var (...)' form disallows a specific type for 'var'.".</span></span>

<span data-ttu-id="ad683-127">请注意，还必须将元组的每个元素分配给一个变量。</span><span class="sxs-lookup"><span data-stu-id="ad683-127">Note that you must also assign each element of the tuple to a variable.</span></span> <span data-ttu-id="ad683-128">如果省略任何元素，编译器将生成错误 CS8132，“无法将 ‘x’ 元素的元组析构为 ‘y’ 变量”。</span><span class="sxs-lookup"><span data-stu-id="ad683-128">If you omit any elements, the compiler generates error CS8132, "Cannot deconstruct a tuple of 'x' elements into 'y' variables."</span></span>

<span data-ttu-id="ad683-129">请注意，不能混合析构左侧上现有变量的声明和赋值。</span><span class="sxs-lookup"><span data-stu-id="ad683-129">Note that you cannot mix declarations and assignments to existing variables on the left-hand side of a deconstruction.</span></span> <span data-ttu-id="ad683-130">编译器生成错误 CS8184“析构不能混合左侧的声明和表达式”。</span><span class="sxs-lookup"><span data-stu-id="ad683-130">The compiler generates error CS8184, "a deconstruction cannot mix declarations and expressions on the left-hand-side."</span></span> <span data-ttu-id="ad683-131">当成员包括新声明的和现有的变量。</span><span class="sxs-lookup"><span data-stu-id="ad683-131">when the members include newly declared and existing variables.</span></span>

## <a name="deconstructing-tuple-elements-with-discards"></a><span data-ttu-id="ad683-132">使用弃元析构元组元素</span><span class="sxs-lookup"><span data-stu-id="ad683-132">Deconstructing tuple elements with discards</span></span>

<span data-ttu-id="ad683-133">析构元组时，通常只需要关注某些元素的值。</span><span class="sxs-lookup"><span data-stu-id="ad683-133">Often when deconstructing a tuple, you're interested in the values of only some elements.</span></span> <span data-ttu-id="ad683-134">从 C# 7.0 开始，便可利用 C# 对弃元的支持，弃元是一种仅能写入的变量，且其值将被忽略。</span><span class="sxs-lookup"><span data-stu-id="ad683-134">Starting with C# 7.0, you can take advantage of C#'s support for *discards*, which are write-only variables whose values you've chosen to ignore.</span></span> <span data-ttu-id="ad683-135">在赋值中，通过下划线字符 (\_) 指定弃元。</span><span class="sxs-lookup"><span data-stu-id="ad683-135">A discard is designated by an underscore character ("\_") in an assignment.</span></span> <span data-ttu-id="ad683-136">可弃元任意数量的值，且均由单个弃元  `_` 表示。</span><span class="sxs-lookup"><span data-stu-id="ad683-136">You can discard as many values as you like; all are represented by the single discard, `_`.</span></span>

<span data-ttu-id="ad683-137">以下示例演示了对元组使用弃元时的用法。</span><span class="sxs-lookup"><span data-stu-id="ad683-137">The following example illustrates the use of tuples with discards.</span></span> <span data-ttu-id="ad683-138">`QueryCityDataForYears` 方法返回一个 6 元组，包含城市名称、城市面积、一个年份、该年份的城市人口、另一个年份及该年份的城市人口。</span><span class="sxs-lookup"><span data-stu-id="ad683-138">The `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="ad683-139">该示例显示了两个年份之间人口的变化。</span><span class="sxs-lookup"><span data-stu-id="ad683-139">The example shows the change in population between those two years.</span></span> <span data-ttu-id="ad683-140">对于元组提供的数据，我们不关注城市面积，并在一开始就知道城市名称和两个日期。</span><span class="sxs-lookup"><span data-stu-id="ad683-140">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="ad683-141">因此，我们只关注存储在元组中的两个人口数量值，可将其余值作为占位符处理。</span><span class="sxs-lookup"><span data-stu-id="ad683-141">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a><span data-ttu-id="ad683-142">析构用户定义类型</span><span class="sxs-lookup"><span data-stu-id="ad683-142">Deconstructing user-defined types</span></span>

<span data-ttu-id="ad683-143">对于非元组类型的解构，C# 不提供内置支持。</span><span class="sxs-lookup"><span data-stu-id="ad683-143">C# does not offer built-in support for deconstructing non-tuple types.</span></span> <span data-ttu-id="ad683-144">但是，用户作为类、结构或接口的创建者，可通过实现一个或多个 `Deconstruct`方法来析构该类型的实例。</span><span class="sxs-lookup"><span data-stu-id="ad683-144">However, as the author of a class, a struct, or an interface, you can allow instances of the type to be deconstructed by implementing one or more `Deconstruct` methods.</span></span> <span data-ttu-id="ad683-145">该方法返回 void，且要析构的每个值由方法签名中的 [out](language-reference/keywords/out-parameter-modifier.md) 参数指示。</span><span class="sxs-lookup"><span data-stu-id="ad683-145">The method returns void, and each value to be deconstructed is indicated by an [out](language-reference/keywords/out-parameter-modifier.md) parameter in the method signature.</span></span> <span data-ttu-id="ad683-146">例如，下面的 `Person` 类的 `Deconstruct` 方法返回名字、中间名和姓氏：</span><span class="sxs-lookup"><span data-stu-id="ad683-146">For example, the following `Deconstruct` method of a `Person` class returns the first, middle, and last name:</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

<span data-ttu-id="ad683-147">然后，可使用类似于以下的分配来析构名为 `p` 的 `Person` 类的实例：</span><span class="sxs-lookup"><span data-stu-id="ad683-147">You can then deconstruct an instance of the `Person` class named `p` with an assignment like the following:</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

<span data-ttu-id="ad683-148">以下示例重载 `Deconstruct` 方法以返回 `Person` 对象的各种属性组合。</span><span class="sxs-lookup"><span data-stu-id="ad683-148">The following example overloads the `Deconstruct` method to return various combinations of properties of a `Person` object.</span></span> <span data-ttu-id="ad683-149">单个重载返回：</span><span class="sxs-lookup"><span data-stu-id="ad683-149">Individual overloads return:</span></span>

- <span data-ttu-id="ad683-150">名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="ad683-150">A first and last name.</span></span>
- <span data-ttu-id="ad683-151">名字、姓氏和中间名。</span><span class="sxs-lookup"><span data-stu-id="ad683-151">A first, last, and middle name.</span></span>
- <span data-ttu-id="ad683-152">名字、姓氏、城市名和省/市/自治区名。</span><span class="sxs-lookup"><span data-stu-id="ad683-152">A first name, a last name, a city name, and a state name.</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

<span data-ttu-id="ad683-153">因为可重载 `Deconstruct` 方法来反映通常从对象中提取的数据组，所以应使用独特明确的签名来定义 `Deconstruct` 方法。</span><span class="sxs-lookup"><span data-stu-id="ad683-153">Because you can overload the `Deconstruct` method to reflect groups of data that are commonly extracted from an object, you should be careful to define `Deconstruct` methods with signatures that are distinctive and unambiguous.</span></span> <span data-ttu-id="ad683-154">如果有多个 `Deconstruct` 方法具有相同数量的 `out` 参数，或具有相同数量和类型的 `out` 参数且顺序不同，则可能会造成混淆。</span><span class="sxs-lookup"><span data-stu-id="ad683-154">Multiple `Deconstruct` methods that have the same number of `out` parameters or the same number and type of `out` parameters in a different order can cause confusion.</span></span>

<span data-ttu-id="ad683-155">以下示例中的重载 `Deconstruct` 方法演示一种混淆的可能性。</span><span class="sxs-lookup"><span data-stu-id="ad683-155">The overloaded `Deconstruct` method in the following example illustrates one possible source of confusion.</span></span> <span data-ttu-id="ad683-156">第一个重载按该顺序返回 `Person` 对象的名字、中间名、姓氏和年龄。</span><span class="sxs-lookup"><span data-stu-id="ad683-156">The first overload returns the first name, middle name, last name, and age of a `Person` object, in that order.</span></span> <span data-ttu-id="ad683-157">第二个重载仅将姓名信息与年收入一起返回，但名字、中间名和姓氏的顺序不同。</span><span class="sxs-lookup"><span data-stu-id="ad683-157">The second overload returns name information only along with annual income, but the first, middle, and last name are in a different order.</span></span> <span data-ttu-id="ad683-158">这使得在析构 `Person` 实例时容易混淆参数的顺序。</span><span class="sxs-lookup"><span data-stu-id="ad683-158">This makes it easy to confuse the order of arguments when deconstructing a `Person` instance.</span></span>

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a><span data-ttu-id="ad683-159">使用弃元析构用户定义类型</span><span class="sxs-lookup"><span data-stu-id="ad683-159">Deconstructing a user-defined type with discards</span></span>

<span data-ttu-id="ad683-160">就像使用[元组](#deconstructing-tuple-elements-with-discards)一样，可使用弃元来忽略 `Deconstruct` 方法返回的选定项。</span><span class="sxs-lookup"><span data-stu-id="ad683-160">Just as you do with [tuples](#deconstructing-tuple-elements-with-discards), you can use discards to ignore selected items returned by a `Deconstruct` method.</span></span> <span data-ttu-id="ad683-161">每个弃元均由名为“\_”的变量定义，一个析构操作可包含多个弃元。</span><span class="sxs-lookup"><span data-stu-id="ad683-161">Each discard is defined by a variable named "\_", and a single deconstruction operation can include multiple discards.</span></span>

<span data-ttu-id="ad683-162">以下示例将 `Person` 对象析构为四个字符串（名字、姓氏、城市和省/市/自治区），但舍弃姓氏和省/市/自治区。</span><span class="sxs-lookup"><span data-stu-id="ad683-162">The following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state) but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a><span data-ttu-id="ad683-163">使用扩展方法析构用户定义的类型</span><span class="sxs-lookup"><span data-stu-id="ad683-163">Deconstructing a user-defined type with an extension method</span></span>

<span data-ttu-id="ad683-164">如果没有创建类、结构或接口，仍可通过实现一个或多个 `Deconstruct` [扩展方法](programming-guide/classes-and-structs/extension-methods.md)来析构该类型的对象，以返回所需值。</span><span class="sxs-lookup"><span data-stu-id="ad683-164">If you didn't author a class, struct, or interface, you can still deconstruct objects of that type by implementing one or more `Deconstruct` [extension methods](programming-guide/classes-and-structs/extension-methods.md) to return the values in which you're interested.</span></span>

<span data-ttu-id="ad683-165">以下示例为 <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> 类定义了两个 `Deconstruct` 扩展方法。</span><span class="sxs-lookup"><span data-stu-id="ad683-165">The following example defines two `Deconstruct` extension methods for the <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ad683-166">第一个方法返回一组值，指示属性的特征，包括其类型、是静态还是实例、是否为只读，以及是否已编制索引。</span><span class="sxs-lookup"><span data-stu-id="ad683-166">The first returns a set of values that indicate the characteristics of the property, including its type, whether it's static or instance, whether it's read-only, and whether it's indexed.</span></span> <span data-ttu-id="ad683-167">第二个方法指示属性的可访问性。</span><span class="sxs-lookup"><span data-stu-id="ad683-167">The second indicates the property's accessibility.</span></span> <span data-ttu-id="ad683-168">因为 get 和 set 访问器的可访问性可能不同，所以布尔值指示属性是否具有单独的 get 和 set 访问器，如果是，则指示它们是否具有相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="ad683-168">Because the accessibility of get and set accessors can differ, Boolean values indicate whether the property has separate get and set accessors and, if it does, whether they have the same accessibility.</span></span> <span data-ttu-id="ad683-169">如果只有一个访问器，或者 get 和 set 访问器具有相同的可访问性，则 `access` 变量指示整个属性的可访问性。</span><span class="sxs-lookup"><span data-stu-id="ad683-169">If there is only one accessor or both the get and the set accessor have the same accessibility, the `access` variable indicates the accessibility of the property as a whole.</span></span> <span data-ttu-id="ad683-170">否则，get 和 set 访问器的可访问性由 `getAccess` 和 `setAccess` 变量指示。</span><span class="sxs-lookup"><span data-stu-id="ad683-170">Otherwise, the accessibility of the get and set accessors are indicated by the `getAccess` and `setAccess` variables.</span></span>

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a><span data-ttu-id="ad683-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad683-171">See also</span></span>

- [<span data-ttu-id="ad683-172">弃元</span><span class="sxs-lookup"><span data-stu-id="ad683-172">Discards</span></span>](discards.md)
- [<span data-ttu-id="ad683-173">元组类型</span><span class="sxs-lookup"><span data-stu-id="ad683-173">Tuple types</span></span>](language-reference/builtin-types/value-tuples.md)
