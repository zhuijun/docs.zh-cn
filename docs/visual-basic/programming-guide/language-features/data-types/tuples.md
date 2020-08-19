---
title: 元组
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: b169a1c13b3f20d7b5e2a1386cfb28a9cc093dcd
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559084"
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="e136b-102">元组 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e136b-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="e136b-103">从 Visual Basic 2017 开始，Visual Basic 语言为元组提供内置支持，使创建元组和访问元组的元素变得更加容易。</span><span class="sxs-lookup"><span data-stu-id="e136b-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="e136b-104">元组是一种轻量级数据结构，它具有特定数量和值序列。</span><span class="sxs-lookup"><span data-stu-id="e136b-104">A tuple is a lightweight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="e136b-105">实例化元组时，可以定义每个值的数量和数据类型 (或元素) 。</span><span class="sxs-lookup"><span data-stu-id="e136b-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="e136b-106">例如，2元组 (或对) 具有两个元素。</span><span class="sxs-lookup"><span data-stu-id="e136b-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="e136b-107">第一个可能是一个 `Boolean` 值，而第二个是 `String` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="e136b-108">因为元组可以轻松地将多个值存储在一个对象中，所以它们通常用作从方法返回多个值的一种简便方法。</span><span class="sxs-lookup"><span data-stu-id="e136b-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e136b-109">元组支持需要 <xref:System.ValueTuple> 类型。</span><span class="sxs-lookup"><span data-stu-id="e136b-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="e136b-110">如果未安装 .NET Framework 4.7，你必须添加 nuget 包 `System.ValueTuple` ，它在 Nuget 库中可用。</span><span class="sxs-lookup"><span data-stu-id="e136b-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="e136b-111">如果不使用此包，可能会出现类似于 "预定义类型" ValueTuple (,,, ) "未定义或未导入" 的编译错误。</span><span class="sxs-lookup"><span data-stu-id="e136b-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="e136b-112">实例化和使用元组</span><span class="sxs-lookup"><span data-stu-id="e136b-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="e136b-113">您可以通过将元组的逗号分隔值括在括号中来实例化元组。</span><span class="sxs-lookup"><span data-stu-id="e136b-113">You instantiate a tuple by enclosing its comma-delimited values in parentheses.</span></span> <span data-ttu-id="e136b-114">然后，这些值将成为元组的字段。</span><span class="sxs-lookup"><span data-stu-id="e136b-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="e136b-115">例如，下面的代码定义了三 (或3元组) `Date` ，其第一个值为，第二个值为，另一个为第二个值 `String` `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="e136b-116">默认情况下，元组中每个字段的名称都包含字符串 `Item` 和该字段在元组中的基于1的位置。</span><span class="sxs-lookup"><span data-stu-id="e136b-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="e136b-117">对于此3元组， `Date` 字段是 `Item1` ，字段为 `String` `Item2` ， `Boolean` 字段为 `Item3` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="e136b-118">下面的示例显示了在上一行代码中实例化的元组字段的值。</span><span class="sxs-lookup"><span data-stu-id="e136b-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="e136b-119">Visual Basic 元组的字段是读写的;实例化元组后，可以修改其值。</span><span class="sxs-lookup"><span data-stu-id="e136b-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="e136b-120">下面的示例修改了上一示例中创建的元组的三个字段中的两个，并显示结果。</span><span class="sxs-lookup"><span data-stu-id="e136b-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="e136b-121">实例化和使用命名元组</span><span class="sxs-lookup"><span data-stu-id="e136b-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="e136b-122">您可以通过将您自己的名称分配给元组的元素，来实例化 *命名元组* ，而不是使用元组字段的默认名称。</span><span class="sxs-lookup"><span data-stu-id="e136b-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="e136b-123">然后，可以通过其分配的名称 *或* 默认名称访问元组的字段。</span><span class="sxs-lookup"><span data-stu-id="e136b-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="e136b-124">下面的示例实例化与之前相同的3元组，只不过它显式命名第一个字段 `EventDate` 、第二个字段和第三个字段 `Name` `IsHoliday` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="e136b-125">然后，它将显示字段值并对其进行修改，并再次显示字段值。</span><span class="sxs-lookup"><span data-stu-id="e136b-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="e136b-126">推断元组元素名称</span><span class="sxs-lookup"><span data-stu-id="e136b-126">Inferred tuple element names</span></span>

<span data-ttu-id="e136b-127">从 Visual Basic 15.3 开始，Visual Basic 可以推断元组元素的名称;无需显式分配它们。</span><span class="sxs-lookup"><span data-stu-id="e136b-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="e136b-128">当你从一组变量初始化元组，并且你希望元组元素名称与变量名称相同时，推理的元组名称很有用。</span><span class="sxs-lookup"><span data-stu-id="e136b-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span>

<span data-ttu-id="e136b-129">下面的示例创建一个 `stateInfo` 包含三个显式命名元素（、和）的元组 `state` `stateName` `capital` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="e136b-130">请注意，在为元素命名时，元组初始化语句只将命名元素命名为同名变量的值。</span><span class="sxs-lookup"><span data-stu-id="e136b-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]

<span data-ttu-id="e136b-131">由于元素和变量具有相同的名称，因此 Visual Basic 编译器可以推断字段的名称，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="e136b-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="e136b-132">若要启用推断元组元素名称，你必须定义要在 Visual Basic 项目中使用的 Visual Basic 编译器版本 (\* .vbproj) 文件：</span><span class="sxs-lookup"><span data-stu-id="e136b-132">To enable inferred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.3</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="e136b-133">版本号可以是从15.3 开始的 Visual Basic 编译器的任何版本。</span><span class="sxs-lookup"><span data-stu-id="e136b-133">The version number can be any version of the Visual Basic compiler starting with 15.3.</span></span> <span data-ttu-id="e136b-134">您还可以将 "最新版本" 指定为 `LangVersion` 使用您的系统上安装的 Visual Basic 编译器的最新版本，而不是对特定编译器版本进行硬编码。</span><span class="sxs-lookup"><span data-stu-id="e136b-134">Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.</span></span>

<span data-ttu-id="e136b-135">有关详细信息，请参阅 [设置 Visual Basic 语言版本](../../../language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="e136b-135">For more information, see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="e136b-136">在某些情况下，Visual Basic 编译器无法从候选名称推断元组元素名称，并且只能使用其默认名称（如、等）来引用元组字段 `Item1` `Item2` 。其中包括：</span><span class="sxs-lookup"><span data-stu-id="e136b-136">In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:</span></span>

- <span data-ttu-id="e136b-137">候选名称与元组成员的名称相同，例如 `Item3` 、 `Rest` 或 `ToString` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-137">The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.</span></span>

- <span data-ttu-id="e136b-138">候选名称在元组中重复。</span><span class="sxs-lookup"><span data-stu-id="e136b-138">The candidate name is duplicated in the tuple.</span></span>

<span data-ttu-id="e136b-139">当字段名称推理失败时，Visual Basic 不会生成编译器错误，也不会在运行时引发异常。</span><span class="sxs-lookup"><span data-stu-id="e136b-139">When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime.</span></span> <span data-ttu-id="e136b-140">相反，元组字段必须由它们的预定义名称引用，例如 `Item1` 和 `Item2` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-140">Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`.</span></span>

## <a name="tuples-versus-structures"></a><span data-ttu-id="e136b-141">元组与结构</span><span class="sxs-lookup"><span data-stu-id="e136b-141">Tuples versus structures</span></span>

<span data-ttu-id="e136b-142">Visual Basic 元组是一个值类型，它是 **ValueTuple** 泛型类型之一的实例。</span><span class="sxs-lookup"><span data-stu-id="e136b-142">A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types.</span></span> <span data-ttu-id="e136b-143">例如， `holiday` 在上一个示例中定义的元组是结构的实例 <xref:System.ValueTuple%603> 。</span><span class="sxs-lookup"><span data-stu-id="e136b-143">For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure.</span></span> <span data-ttu-id="e136b-144">它设计为数据的轻型容器。</span><span class="sxs-lookup"><span data-stu-id="e136b-144">It is designed to be a lightweight container for data.</span></span> <span data-ttu-id="e136b-145">由于元组旨在使创建包含多个数据项的对象变得更加容易，因此它缺少自定义结构可能具有的某些功能。</span><span class="sxs-lookup"><span data-stu-id="e136b-145">Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have.</span></span> <span data-ttu-id="e136b-146">其中包括：</span><span class="sxs-lookup"><span data-stu-id="e136b-146">These include:</span></span>

- <span data-ttu-id="e136b-147">自定义成员。</span><span class="sxs-lookup"><span data-stu-id="e136b-147">Custom members.</span></span> <span data-ttu-id="e136b-148">不能为元组定义自己的属性、方法或事件。</span><span class="sxs-lookup"><span data-stu-id="e136b-148">You cannot define your own properties, methods, or events for a tuple.</span></span>

- <span data-ttu-id="e136b-149">检查.</span><span class="sxs-lookup"><span data-stu-id="e136b-149">Validation.</span></span> <span data-ttu-id="e136b-150">您无法验证分配给字段的数据。</span><span class="sxs-lookup"><span data-stu-id="e136b-150">You cannot validate the data assigned to fields.</span></span>

- <span data-ttu-id="e136b-151">不可变性.</span><span class="sxs-lookup"><span data-stu-id="e136b-151">Immutability.</span></span> <span data-ttu-id="e136b-152">Visual Basic 元组是可变的。</span><span class="sxs-lookup"><span data-stu-id="e136b-152">Visual Basic tuples are mutable.</span></span> <span data-ttu-id="e136b-153">与此相反，自定义结构允许您控制实例是可变的还是不可变的。</span><span class="sxs-lookup"><span data-stu-id="e136b-153">In contrast, a custom structure allows you to control whether an instance is mutable or immutable.</span></span>

<span data-ttu-id="e136b-154">如果自定义成员、属性和字段验证或不可变性非常重要，则应使用 Visual Basic [结构](../../../language-reference/statements/structure-statement.md) 语句来定义自定义值类型。</span><span class="sxs-lookup"><span data-stu-id="e136b-154">If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.</span></span>

<span data-ttu-id="e136b-155">Visual Basic 元组将继承其 **ValueTuple** 类型的成员。</span><span class="sxs-lookup"><span data-stu-id="e136b-155">A Visual Basic tuple does inherit the members of its **ValueTuple** type.</span></span> <span data-ttu-id="e136b-156">除了其字段外，其中包括以下方法：</span><span class="sxs-lookup"><span data-stu-id="e136b-156">In addition to its fields, these include the following methods:</span></span>

| <span data-ttu-id="e136b-157">方法</span><span class="sxs-lookup"><span data-stu-id="e136b-157">Method</span></span> | <span data-ttu-id="e136b-158">说明</span><span class="sxs-lookup"><span data-stu-id="e136b-158">Description</span></span> |
| ---|---|
| <span data-ttu-id="e136b-159">CompareTo</span><span class="sxs-lookup"><span data-stu-id="e136b-159">CompareTo</span></span> | <span data-ttu-id="e136b-160">将当前元组与具有相同数量的元素的另一个元组进行比较。</span><span class="sxs-lookup"><span data-stu-id="e136b-160">Compares the current tuple to another tuple with the same number of elements.</span></span> |
| <span data-ttu-id="e136b-161">等于</span><span class="sxs-lookup"><span data-stu-id="e136b-161">Equals</span></span> | <span data-ttu-id="e136b-162">确定当前元组是否等于另一个元组或对象。</span><span class="sxs-lookup"><span data-stu-id="e136b-162">Determines whether the current tuple is equal to another tuple or object.</span></span> |
| <span data-ttu-id="e136b-163">GetHashCode</span><span class="sxs-lookup"><span data-stu-id="e136b-163">GetHashCode</span></span> | <span data-ttu-id="e136b-164">计算当前实例的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="e136b-164">Calculates the hash code for the current instance.</span></span> |
| <span data-ttu-id="e136b-165">ToString</span><span class="sxs-lookup"><span data-stu-id="e136b-165">ToString</span></span> | <span data-ttu-id="e136b-166">返回此元组的字符串表示形式，它采用格式 `(Item1, Item2...)` ，其中 `Item1` 和 `Item2` 表示元组字段的值。</span><span class="sxs-lookup"><span data-stu-id="e136b-166">Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields.</span></span> |

<span data-ttu-id="e136b-167">此外， **ValueTuple** 类型实现 <xref:System.Collections.IStructuralComparable> 和 <xref:System.Collections.IStructuralEquatable> 接口，这允许您定义自定义比较器。</span><span class="sxs-lookup"><span data-stu-id="e136b-167">In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define custom comparers.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="e136b-168">赋值和元组</span><span class="sxs-lookup"><span data-stu-id="e136b-168">Assignment and tuples</span></span>

<span data-ttu-id="e136b-169">Visual Basic 支持在具有相同数量的字段的元组类型之间进行分配。</span><span class="sxs-lookup"><span data-stu-id="e136b-169">Visual Basic supports assignment between tuple types that have the same number of fields.</span></span> <span data-ttu-id="e136b-170">如果满足以下任一条件，则可以转换字段类型：</span><span class="sxs-lookup"><span data-stu-id="e136b-170">The field types can be converted if one of the following is true:</span></span>

- <span data-ttu-id="e136b-171">源和目标字段的类型相同。</span><span class="sxs-lookup"><span data-stu-id="e136b-171">The source and target field are of the same type.</span></span>

- <span data-ttu-id="e136b-172">定义了源类型到目标类型的扩大 (或隐式) 转换。</span><span class="sxs-lookup"><span data-stu-id="e136b-172">A widening (or implicit) conversion of the source type to the target type is defined.</span></span>

- <span data-ttu-id="e136b-173">`Option Strict` 为 `On` ，并且定义了从源类型到目标类型的收缩 (或显式) 转换。</span><span class="sxs-lookup"><span data-stu-id="e136b-173">`Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined.</span></span> <span data-ttu-id="e136b-174">如果源值超出了目标类型的范围，则此转换可能会引发异常。</span><span class="sxs-lookup"><span data-stu-id="e136b-174">This conversion can throw an exception if the source value is outside the range of the target type.</span></span>

<span data-ttu-id="e136b-175">对于其他转换，不考虑进行赋值。</span><span class="sxs-lookup"><span data-stu-id="e136b-175">Other conversions are not considered for assignments.</span></span> <span data-ttu-id="e136b-176">让我们看一下元组类型之间允许的赋值类型。</span><span class="sxs-lookup"><span data-stu-id="e136b-176">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="e136b-177">注意以下示例中使用的这些变量：</span><span class="sxs-lookup"><span data-stu-id="e136b-177">Consider these variables used in the following examples:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

<span data-ttu-id="e136b-178">前两个变量（ `unnamed` 和 `anonymous` ）没有为字段提供语义名称。</span><span class="sxs-lookup"><span data-stu-id="e136b-178">The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields.</span></span> <span data-ttu-id="e136b-179">它们的字段名称是默认值 `Item1` 和 `Item2` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-179">Their field names are the default `Item1` and `Item2`.</span></span> <span data-ttu-id="e136b-180">最后两个变量， `named` `differentName` 具有语义字段名称。</span><span class="sxs-lookup"><span data-stu-id="e136b-180">The last two variables, `named` and `differentName` have semantic field names.</span></span> <span data-ttu-id="e136b-181">请注意，这两个元组具有不同的字段名称。</span><span class="sxs-lookup"><span data-stu-id="e136b-181">Note that these two tuples have different names for the fields.</span></span>

<span data-ttu-id="e136b-182">这四个元组具有相同数目的字段 (称为 "arity" ) ，这些字段的类型相同。</span><span class="sxs-lookup"><span data-stu-id="e136b-182">All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical.</span></span> <span data-ttu-id="e136b-183">因此可进行以下赋值：</span><span class="sxs-lookup"><span data-stu-id="e136b-183">Therefore, all of these assignments work:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

<span data-ttu-id="e136b-184">请注意，元组的名称未赋值。</span><span class="sxs-lookup"><span data-stu-id="e136b-184">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="e136b-185">字段的赋值顺序遵循字段在元组中的顺序。</span><span class="sxs-lookup"><span data-stu-id="e136b-185">The values of the fields are assigned following the order of the fields in the tuple.</span></span>

<span data-ttu-id="e136b-186">最后请注意，我们可以将 `named` 元组分配给 `conversion` 元组，即使的第一个字段 `named` 是 `Integer` ，第一个字段 `conversion` 是 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-186">Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`.</span></span> <span data-ttu-id="e136b-187">此分配成功，因为转换 `Integer` 为 `Long` 是扩大转换。</span><span class="sxs-lookup"><span data-stu-id="e136b-187">This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

<span data-ttu-id="e136b-188">具有不同数量字段的元组不可赋值：</span><span class="sxs-lookup"><span data-stu-id="e136b-188">Tuples with different numbers of fields are not assignable:</span></span>

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="e136b-189">作为方法返回值的元组</span><span class="sxs-lookup"><span data-stu-id="e136b-189">Tuples as method return values</span></span>

<span data-ttu-id="e136b-190">一个方法只能返回一个值。</span><span class="sxs-lookup"><span data-stu-id="e136b-190">A method can return only a single value.</span></span> <span data-ttu-id="e136b-191">不过，通常会希望方法调用返回多个值。</span><span class="sxs-lookup"><span data-stu-id="e136b-191">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="e136b-192">有多种方法可以解决此限制：</span><span class="sxs-lookup"><span data-stu-id="e136b-192">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="e136b-193">你可以创建一个自定义类或结构，该类或结构的属性或字段表示方法返回的值。</span><span class="sxs-lookup"><span data-stu-id="e136b-193">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="e136b-194">因此，它是一个重型解决方案;它要求您定义一个仅用于从方法调用检索值的自定义类型。</span><span class="sxs-lookup"><span data-stu-id="e136b-194">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="e136b-195">你可以从方法返回单个值，并通过将引用传递给方法来返回其余值。</span><span class="sxs-lookup"><span data-stu-id="e136b-195">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="e136b-196">这涉及到实例化变量的开销以及意外覆盖按引用传递的变量值的风险。</span><span class="sxs-lookup"><span data-stu-id="e136b-196">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="e136b-197">可以使用元组，该元组提供用于检索多个返回值的轻型解决方案。</span><span class="sxs-lookup"><span data-stu-id="e136b-197">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="e136b-198">例如，.NET 中的 **TryParse** 方法返回一个 `Boolean` 值，该值指示分析操作是否成功。</span><span class="sxs-lookup"><span data-stu-id="e136b-198">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="e136b-199">分析操作的结果在通过引用传递给方法的变量中返回。</span><span class="sxs-lookup"><span data-stu-id="e136b-199">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="e136b-200">通常，对分析方法的调用如下所 <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> 示：</span><span class="sxs-lookup"><span data-stu-id="e136b-200">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="e136b-201">如果我们在自己的方法中包装对方法的调用，我们可以从分析操作返回元组 <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e136b-201">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="e136b-202">在下面的示例中， `NumericLibrary.ParseInteger` 调用 <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> 方法并返回具有两个元素的命名元组。</span><span class="sxs-lookup"><span data-stu-id="e136b-202">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="e136b-203">然后，可以通过如下所示的代码调用该方法：</span><span class="sxs-lookup"><span data-stu-id="e136b-203">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="e136b-204">.NET Framework 中的 Visual Basic 元组和元组</span><span class="sxs-lookup"><span data-stu-id="e136b-204">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="e136b-205">Visual Basic 元组是 .NET Framework 4.7 中引入的 ValueTuple 泛型类型之一的实例 **。**</span><span class="sxs-lookup"><span data-stu-id="e136b-205">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="e136b-206">.NET Framework 还包括一组通用的 **系统元组** 类。</span><span class="sxs-lookup"><span data-stu-id="e136b-206">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="e136b-207">不过，这些类与 Visual Basic 元组和 **ValueTuple** 泛型类型的不同之处在于：</span><span class="sxs-lookup"><span data-stu-id="e136b-207">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="e136b-208">**元组**类的元素是名为 `Item1` 、等的属性 `Item2` 。</span><span class="sxs-lookup"><span data-stu-id="e136b-208">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="e136b-209">在 Visual Basic 元组和 **ValueTuple** 类型中，元组元素是字段。</span><span class="sxs-lookup"><span data-stu-id="e136b-209">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="e136b-210">不能为 **元组** 实例或 **ValueTuple** 实例的元素分配有意义的名称。</span><span class="sxs-lookup"><span data-stu-id="e136b-210">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="e136b-211">Visual Basic 允许您分配用于传达字段含义的名称。</span><span class="sxs-lookup"><span data-stu-id="e136b-211">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="e136b-212">**元组**实例的属性是只读的;元组是不可变的。</span><span class="sxs-lookup"><span data-stu-id="e136b-212">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="e136b-213">在 Visual Basic 元组和 **ValueTuple** 类型中，元组字段是读写的;元组是可变的。</span><span class="sxs-lookup"><span data-stu-id="e136b-213">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="e136b-214">泛型 **元组** 类型为引用类型。</span><span class="sxs-lookup"><span data-stu-id="e136b-214">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="e136b-215">使用这些 **元组** 类型意味着分配对象。</span><span class="sxs-lookup"><span data-stu-id="e136b-215">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="e136b-216">在热路径中，这可能会对应用程序性能产生明显的影响。</span><span class="sxs-lookup"><span data-stu-id="e136b-216">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="e136b-217">Visual Basic 元组和 **ValueTuple** 类型为值类型。</span><span class="sxs-lookup"><span data-stu-id="e136b-217">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="e136b-218">类中的扩展方法可以轻松地在 <xref:System.TupleExtensions> Visual Basic 元组和 .Net **元组** 对象之间进行转换。</span><span class="sxs-lookup"><span data-stu-id="e136b-218">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="e136b-219">**ToTuple**方法将 Visual Basic 元组转换为 .Net**元组**对象， **ToValueTuple**方法将 .net**元组**对象转换为 Visual Basic 元组。</span><span class="sxs-lookup"><span data-stu-id="e136b-219">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="e136b-220">下面的示例创建一个元组，将其转换为 .NET **元组** 对象，然后将其转换回 Visual Basic 元组。</span><span class="sxs-lookup"><span data-stu-id="e136b-220">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="e136b-221">然后，该示例将此元组与原始元组进行比较以确保它们相等。</span><span class="sxs-lookup"><span data-stu-id="e136b-221">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e136b-222">请参阅</span><span class="sxs-lookup"><span data-stu-id="e136b-222">See also</span></span>

- [<span data-ttu-id="e136b-223">Visual Basic 语言参考</span><span class="sxs-lookup"><span data-stu-id="e136b-223">Visual Basic Language Reference</span></span>](index.md)
