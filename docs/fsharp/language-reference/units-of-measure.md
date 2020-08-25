---
title: 度量单位
description: '了解 F # 中的浮点和有符号整数值如何具有关联的度量单位，这些度量值通常用于指示长度、数量和质量。'
ms.date: 08/15/2020
ms.openlocfilehash: 0262f89e80697dd86161c93fe37381122972b56f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811569"
---
# <a name="units-of-measure"></a><span data-ttu-id="1b871-103">度量单位</span><span class="sxs-lookup"><span data-stu-id="1b871-103">Units of Measure</span></span>

<span data-ttu-id="1b871-104">F # 中的浮点和有符号整数值可以具有关联的度量单位，这通常用于指示长度、数量和质量等。</span><span class="sxs-lookup"><span data-stu-id="1b871-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="1b871-105">通过使用具有单位的数量，可以使编译器验证算术关系是否具有正确的单位，这有助于防止编程错误。</span><span class="sxs-lookup"><span data-stu-id="1b871-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b871-106">语法</span><span class="sxs-lookup"><span data-stu-id="1b871-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="1b871-107">备注</span><span class="sxs-lookup"><span data-stu-id="1b871-107">Remarks</span></span>

<span data-ttu-id="1b871-108">前面的语法将 *单位名称* 定义为度量单位。</span><span class="sxs-lookup"><span data-stu-id="1b871-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="1b871-109">可选部分用于根据以前定义的单元定义新的度量值。</span><span class="sxs-lookup"><span data-stu-id="1b871-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="1b871-110">例如，下面的行定义 `cm` (厘米) 的度量值。</span><span class="sxs-lookup"><span data-stu-id="1b871-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="1b871-111">以下行将 (milliliter) 的度量值定义 `ml` 为三厘米 (`cm^3`) 。</span><span class="sxs-lookup"><span data-stu-id="1b871-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="1b871-112">在前面的语法中， *measure* 是涉及单元的公式。</span><span class="sxs-lookup"><span data-stu-id="1b871-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="1b871-113">在涉及单元的公式中，支持整数幂 (正和负) ，单位之间的空格指示两个单位的积， `*` 还指示单位的积，并 `/` 指示单位的商。</span><span class="sxs-lookup"><span data-stu-id="1b871-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="1b871-114">对于倒数单元，可以使用负整数幂或 `/` 指示单元公式的分子和分母之间的分隔。</span><span class="sxs-lookup"><span data-stu-id="1b871-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="1b871-115">分母中的多个单元应括在括号中。</span><span class="sxs-lookup"><span data-stu-id="1b871-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="1b871-116">后面由空格分隔的单位 `/` 被解释为分母的一部分，但后面的任何单位会被 `*` 解释为作为分子的一部分。</span><span class="sxs-lookup"><span data-stu-id="1b871-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="1b871-117">您可以在单位表达式中使用1，而不是将其用于表示一种单量维度，也可以与其他单位（如分子）一起使用。</span><span class="sxs-lookup"><span data-stu-id="1b871-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="1b871-118">例如，费率的单位将写为 `1/s` ，其中 `s` 指示秒。</span><span class="sxs-lookup"><span data-stu-id="1b871-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="1b871-119">单元公式中不使用括号。</span><span class="sxs-lookup"><span data-stu-id="1b871-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="1b871-120">不在单元公式中指定数值转换常量;但是，您可以单独定义单位的转换常量，并在单元检查计算中使用它们。</span><span class="sxs-lookup"><span data-stu-id="1b871-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="1b871-121">可以采用各种等效方式编写表示相同内容的单位公式。</span><span class="sxs-lookup"><span data-stu-id="1b871-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="1b871-122">因此，编译器将单元公式转换为一致的窗体，该窗体将负幂转换为 reciprocals，将单位分组为单个分子和分母，并 alphabetizes 分子和分母中的单位。</span><span class="sxs-lookup"><span data-stu-id="1b871-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="1b871-123">例如，单位公式 `kg m s^-2` 和 `m /s s * kg` 都转换为 `kg m/s^2` 。</span><span class="sxs-lookup"><span data-stu-id="1b871-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="1b871-124">在浮点表达式中使用度量单位。</span><span class="sxs-lookup"><span data-stu-id="1b871-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="1b871-125">将浮点数与关联的度量单位一起使用可以添加另一个级别的安全性，并有助于避免使用弱类型化浮点数时，公式中可能发生的单元不匹配错误。</span><span class="sxs-lookup"><span data-stu-id="1b871-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="1b871-126">如果您编写使用单元的浮点表达式，则表达式中的单位必须匹配。</span><span class="sxs-lookup"><span data-stu-id="1b871-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="1b871-127">您可以使用尖括号中的单元公式来注释文本，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="1b871-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="1b871-128">不在数字与尖括号之间放置空格;但是，可以包含文本后缀（如 `f` ），如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="1b871-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="1b871-129">此类批注将文本的类型从其基元类型更改 (例如， `float`) 为维度类型（ `float<cm>` 在本例中为） `float<miles/hour>` 。</span><span class="sxs-lookup"><span data-stu-id="1b871-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="1b871-130">的单位批注 `<1>` 指示一个有量的量，其类型等效于不带 unit 参数的基元类型。</span><span class="sxs-lookup"><span data-stu-id="1b871-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="1b871-131">度量单位的类型是一个浮点型或有符号整型，以及一个额外的单位批注，用方括号括起来。</span><span class="sxs-lookup"><span data-stu-id="1b871-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="1b871-132">因此，当您将转换类型从 `g` (克) 转换为 `kg` (千克) 时，请按如下所示描述类型。</span><span class="sxs-lookup"><span data-stu-id="1b871-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="1b871-133">度量单位用于编译时单元检查，但不会在运行时环境中保留。</span><span class="sxs-lookup"><span data-stu-id="1b871-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="1b871-134">因此，它们不会影响性能。</span><span class="sxs-lookup"><span data-stu-id="1b871-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="1b871-135">度量单位可以应用于任何类型，而不只是浮点类型;但是，只有浮点类型、有符号的整数类型和 decimal 类型支持已标注数量。</span><span class="sxs-lookup"><span data-stu-id="1b871-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="1b871-136">因此，只对基元类型和包含这些基元类型的聚合使用度量单位有意义。</span><span class="sxs-lookup"><span data-stu-id="1b871-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="1b871-137">下面的示例阐释了度量单位的用法。</span><span class="sxs-lookup"><span data-stu-id="1b871-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="1b871-138">下面的代码示例演示如何从有量可变浮点数转换为有尺寸的浮点值。</span><span class="sxs-lookup"><span data-stu-id="1b871-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="1b871-139">你只需乘以1.0，然后将维度应用于1.0。</span><span class="sxs-lookup"><span data-stu-id="1b871-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="1b871-140">可以将此抽象到类似的函数 `degreesFahrenheit` 。</span><span class="sxs-lookup"><span data-stu-id="1b871-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="1b871-141">此外，当你将已确定维度的值传递到需要有量维度浮点数的函数时，必须使用运算符取消单元或强制转换为 `float` `float` 。</span><span class="sxs-lookup"><span data-stu-id="1b871-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="1b871-142">在此示例中，将对的自变量进行除数， `1.0<degC>` `printf` 因为需要有 `printf` 量维度。</span><span class="sxs-lookup"><span data-stu-id="1b871-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="1b871-143">下面的示例会话显示了输出以及此代码的输入。</span><span class="sxs-lookup"><span data-stu-id="1b871-143">The following example session shows the outputs from and inputs to this code.</span></span>

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="1b871-144">使用通用单位</span><span class="sxs-lookup"><span data-stu-id="1b871-144">Using Generic Units</span></span>

<span data-ttu-id="1b871-145">您可以编写对具有关联的度量单位的数据进行操作的泛型函数。</span><span class="sxs-lookup"><span data-stu-id="1b871-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="1b871-146">为此，可将一个类型与一个泛型单元一起指定为类型参数，如以下代码示例中所示。</span><span class="sxs-lookup"><span data-stu-id="1b871-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="1b871-147">用通用单位创建聚合类型</span><span class="sxs-lookup"><span data-stu-id="1b871-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="1b871-148">下面的代码演示如何创建一个聚合类型，该类型由具有泛型单元的单个浮点值组成。</span><span class="sxs-lookup"><span data-stu-id="1b871-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="1b871-149">这样，便可以创建适用于各种单位的单一类型。</span><span class="sxs-lookup"><span data-stu-id="1b871-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="1b871-150">此外，通过确保具有一组单位的泛型类型与具有不同单位集的相同泛型类型的类型不同，泛型单位会保留类型安全性。</span><span class="sxs-lookup"><span data-stu-id="1b871-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="1b871-151">此方法的基础是 `Measure` 特性可以应用于类型参数。</span><span class="sxs-lookup"><span data-stu-id="1b871-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="1b871-152">运行时单位</span><span class="sxs-lookup"><span data-stu-id="1b871-152">Units at Runtime</span></span>

<span data-ttu-id="1b871-153">度量单位用于静态类型检查。</span><span class="sxs-lookup"><span data-stu-id="1b871-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="1b871-154">在编译浮点值时，将消除度量单位，以便在运行时单元丢失。</span><span class="sxs-lookup"><span data-stu-id="1b871-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="1b871-155">因此，尝试实现依赖于在运行时检查单元的功能是不可能的。</span><span class="sxs-lookup"><span data-stu-id="1b871-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="1b871-156">例如， `ToString` 不能实现函数来打印单元。</span><span class="sxs-lookup"><span data-stu-id="1b871-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="1b871-157">转换</span><span class="sxs-lookup"><span data-stu-id="1b871-157">Conversions</span></span>

<span data-ttu-id="1b871-158">若要将具有单位的类型 (例如， `float<'u>`) 为不具有单位的类型，则可以使用标准转换函数。</span><span class="sxs-lookup"><span data-stu-id="1b871-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="1b871-159">例如，可以使用 `float` 将转换为 `float` 不具有单位的值，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="1b871-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="1b871-160">若要将无单位的值转换为具有单位的值，可以将使用适当单位批注的1或1.0 值相乘。</span><span class="sxs-lookup"><span data-stu-id="1b871-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="1b871-161">但是，为了编写互操作性层，还可以使用某些显式函数将无单位值转换为具有单位的值。</span><span class="sxs-lookup"><span data-stu-id="1b871-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="1b871-162">它们位于 [fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) 模块中。</span><span class="sxs-lookup"><span data-stu-id="1b871-162">These are in the [FSharp.Core.LanguagePrimitives](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) module.</span></span> <span data-ttu-id="1b871-163">例如，若要从无单位转换 `float` 为 `float<cm>` ，请使用 [FloatWithMeasure](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure)，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="1b871-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="1b871-164">F # 核心库中的度量单位</span><span class="sxs-lookup"><span data-stu-id="1b871-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="1b871-165">命名空间中提供了一个单元库 `FSharp.Data.UnitSystems.SI` 。</span><span class="sxs-lookup"><span data-stu-id="1b871-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="1b871-166">它在其符号形式中包含 SI 单位， (`m` 例如子命名空间中的计量) `UnitSymbols` ，以及其全名 (如 `meter` 子命名空间中的) `UnitNames` 。</span><span class="sxs-lookup"><span data-stu-id="1b871-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b871-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b871-167">See also</span></span>

- [<span data-ttu-id="1b871-168">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="1b871-168">F# Language Reference</span></span>](index.md)
