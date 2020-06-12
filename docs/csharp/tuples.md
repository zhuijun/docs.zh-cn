---
title: 元组类型 - C# 指南
description: 了解 C# 中的未命名元组类型和命名元组类型
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 497f95811677c300e1fadad65eb495dced7f2da3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374611"
---
# <a name="c-tuple-types"></a><span data-ttu-id="3bf05-103">C# 元组类型</span><span class="sxs-lookup"><span data-stu-id="3bf05-103">C# tuple types</span></span>

<span data-ttu-id="3bf05-104">C# 元组是使用轻量语法定义的类型。</span><span class="sxs-lookup"><span data-stu-id="3bf05-104">C# tuples are types that you define using a lightweight syntax.</span></span> <span data-ttu-id="3bf05-105">其优点包括：更简单的语法，基于元素数量（称为“基数”）和元素类型的转换规则，以及一致的副本、相等测试和赋值规则。</span><span class="sxs-lookup"><span data-stu-id="3bf05-105">The advantages include a simpler syntax, rules for conversions based on number (referred to as cardinality) and types of elements, and consistent rules for copies, equality tests, and assignments.</span></span> <span data-ttu-id="3bf05-106">但另一方面，元组不支持一些与继承相关的面向对象的语法。</span><span class="sxs-lookup"><span data-stu-id="3bf05-106">As a tradeoff, tuples do not support some of the object-oriented idioms associated with inheritance.</span></span> <span data-ttu-id="3bf05-107">[C# 7.0 中的新增功能](whats-new/csharp-7.md#tuples)文章中的“元组”一节对其进行了概述。</span><span class="sxs-lookup"><span data-stu-id="3bf05-107">You can get an overview in the section on [tuples in the What's new in C# 7.0](whats-new/csharp-7.md#tuples) article.</span></span>

<span data-ttu-id="3bf05-108">在本文中，你将了解用于控制 C# 7.0 及更高版本中的元组的语言规则、这些规则的各种用法，以及有关如何使用元组的初步指导。</span><span class="sxs-lookup"><span data-stu-id="3bf05-108">In this article, you'll learn the language rules governing tuples in C# 7.0 and later versions, different ways to use them, and initial guidance on working with tuples.</span></span>

> [!NOTE]
> <span data-ttu-id="3bf05-109">新的元组功能需要 <xref:System.ValueTuple> 类型。</span><span class="sxs-lookup"><span data-stu-id="3bf05-109">The new tuples features require the <xref:System.ValueTuple> types.</span></span>
> <span data-ttu-id="3bf05-110">为在不包括该类型的平台上使用它，必须添加 NuGet 包 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/)。</span><span class="sxs-lookup"><span data-stu-id="3bf05-110">You must add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) in order to use it on platforms that do not include the types.</span></span>
>
> <span data-ttu-id="3bf05-111">这类似于依赖框架提供的类型的其他语言功能。</span><span class="sxs-lookup"><span data-stu-id="3bf05-111">This is similar to other language features that rely on types delivered in the framework.</span></span> <span data-ttu-id="3bf05-112">例如，依赖 `INotifyCompletion` 接口的 `async` 和 `await`，依赖 `IEnumerable<T>` 的 LINQ。</span><span class="sxs-lookup"><span data-stu-id="3bf05-112">Examples include `async` and `await` relying on the `INotifyCompletion` interface, and LINQ relying on `IEnumerable<T>`.</span></span> <span data-ttu-id="3bf05-113">但是，随着 .NET 越来越不依赖平台，交付机制也在发生改变。</span><span class="sxs-lookup"><span data-stu-id="3bf05-113">However, the delivery mechanism is changing as .NET is becoming more platform independent.</span></span> <span data-ttu-id="3bf05-114">.NET Framework 交付频率可能不会与语言编译器的始终相同。</span><span class="sxs-lookup"><span data-stu-id="3bf05-114">The .NET Framework may not always ship on the same cadence as the language compiler.</span></span> <span data-ttu-id="3bf05-115">新语言功能依赖于新类型时，这些类型将在交付语言功能时以 NuGet 包的形式提供。</span><span class="sxs-lookup"><span data-stu-id="3bf05-115">When new language features rely on new types, those types will be available as NuGet packages when the language features ship.</span></span> <span data-ttu-id="3bf05-116">这些新类型添加到 .NET 标准 API 并作为框架的一部分交付后，将删除 NuGet 包要求。</span><span class="sxs-lookup"><span data-stu-id="3bf05-116">As these new types get added to the .NET Standard API and delivered as part of the framework, the NuGet package requirement will be removed.</span></span>

<span data-ttu-id="3bf05-117">我们先解释一下为什么要添加新的元组支持。</span><span class="sxs-lookup"><span data-stu-id="3bf05-117">Let's start with the reasons for adding new tuple support.</span></span> <span data-ttu-id="3bf05-118">方法返回单个对象。</span><span class="sxs-lookup"><span data-stu-id="3bf05-118">Methods return a single object.</span></span> <span data-ttu-id="3bf05-119">借助元组，可以更轻松地对该单个对象中的多个值打包。</span><span class="sxs-lookup"><span data-stu-id="3bf05-119">Tuples enable you to package multiple values in that single object more easily.</span></span>

<span data-ttu-id="3bf05-120">.NET Framework 已具有泛型 `Tuple` 类。</span><span class="sxs-lookup"><span data-stu-id="3bf05-120">The .NET Framework already has generic `Tuple` classes.</span></span> <span data-ttu-id="3bf05-121">但这些类有两个主要限制。</span><span class="sxs-lookup"><span data-stu-id="3bf05-121">These classes, however, had two major limitations.</span></span> <span data-ttu-id="3bf05-122">其一，`Tuple` 类将其属性命名为 `Item1`、`Item2` 等。</span><span class="sxs-lookup"><span data-stu-id="3bf05-122">For one, the `Tuple` classes named their properties `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="3bf05-123">这些名称未承载任何语义信息。</span><span class="sxs-lookup"><span data-stu-id="3bf05-123">Those names carry no semantic information.</span></span> <span data-ttu-id="3bf05-124">使用这些 `Tuple` 类型无法表达各属性的含义。</span><span class="sxs-lookup"><span data-stu-id="3bf05-124">Using these `Tuple` types does not enable communicating the meaning of each of the properties.</span></span> <span data-ttu-id="3bf05-125">通过新的语言功能，可对元组中的各元素进行声明并为其赋予有意义的语义名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-125">The new language features enable you to declare and use semantically meaningful names for the elements in a tuple.</span></span>

<span data-ttu-id="3bf05-126">`Tuple` 类因其引用类型会导致更多性能问题。</span><span class="sxs-lookup"><span data-stu-id="3bf05-126">The `Tuple` classes cause more performance concerns because they are reference types.</span></span> <span data-ttu-id="3bf05-127">使用任一 `Tuple` 类型即意味着分配对象。</span><span class="sxs-lookup"><span data-stu-id="3bf05-127">Using one of the `Tuple` types means allocating objects.</span></span> <span data-ttu-id="3bf05-128">在热路径中，分配许多小型对象可能会对应用程序性能产生明显的影响。</span><span class="sxs-lookup"><span data-stu-id="3bf05-128">On hot paths, allocating many small objects can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="3bf05-129">因此，元组的语言支持使用新的 `ValueTuple` 结构。</span><span class="sxs-lookup"><span data-stu-id="3bf05-129">Therefore, the language support for tuples leverages the new `ValueTuple` structs.</span></span>

<span data-ttu-id="3bf05-130">为避免这些缺陷，可创建 `class` 或 `struct` 来承载多个元素。</span><span class="sxs-lookup"><span data-stu-id="3bf05-130">To avoid those deficiencies, you could create a `class` or a `struct` to carry multiple elements.</span></span> <span data-ttu-id="3bf05-131">但这样做不仅加大了工作量，还掩盖了你的设计意图。</span><span class="sxs-lookup"><span data-stu-id="3bf05-131">Unfortunately, that's more work for you, and it obscures your design intent.</span></span> <span data-ttu-id="3bf05-132">创建 `struct` 或 `class` 意味着定义一个具有数据和行为的类型。</span><span class="sxs-lookup"><span data-stu-id="3bf05-132">Making a `struct` or `class` implies that you are defining a type with both data and behavior.</span></span> <span data-ttu-id="3bf05-133">很多时候，你其实只是想存储单个对象中的多个值而已。</span><span class="sxs-lookup"><span data-stu-id="3bf05-133">Many times, you simply want to store multiple values in a single object.</span></span>

<span data-ttu-id="3bf05-134">这些语言功能和 `ValueTuple` 泛型结构共同实施以下规则：不能向这些元组类型添加任何行为（方法）。</span><span class="sxs-lookup"><span data-stu-id="3bf05-134">The language features and the `ValueTuple` generic structs enforce the rule that you cannot add any behavior (methods) to these tuple types.</span></span>
<span data-ttu-id="3bf05-135">所有 `ValueTuple` 类型都是*可变结构*。</span><span class="sxs-lookup"><span data-stu-id="3bf05-135">All the `ValueTuple` types are *mutable structs*.</span></span> <span data-ttu-id="3bf05-136">每个成员字段都是公共字段。</span><span class="sxs-lookup"><span data-stu-id="3bf05-136">Each member field is a public field.</span></span> <span data-ttu-id="3bf05-137">这使它们变得非常轻量。</span><span class="sxs-lookup"><span data-stu-id="3bf05-137">That makes them very lightweight.</span></span> <span data-ttu-id="3bf05-138">但是，这意味着在要求永久性的场合无法使用元组。</span><span class="sxs-lookup"><span data-stu-id="3bf05-138">However, that means tuples should not be used where immutability is important.</span></span>

<span data-ttu-id="3bf05-139">元组是比 `class` 和 `struct` 类型更为简单灵活的数据容器。</span><span class="sxs-lookup"><span data-stu-id="3bf05-139">Tuples are both simpler and more flexible data containers than `class` and `struct` types.</span></span> <span data-ttu-id="3bf05-140">我们来探讨一下它们之间的差异。</span><span class="sxs-lookup"><span data-stu-id="3bf05-140">Let's explore those differences.</span></span>

## <a name="named-and-unnamed-tuples"></a><span data-ttu-id="3bf05-141">命名元组和未命名元组</span><span class="sxs-lookup"><span data-stu-id="3bf05-141">Named and unnamed tuples</span></span>

<span data-ttu-id="3bf05-142">`ValueTuple` 结构具有名为 `Item1`、`Item2`、`Item3` 等的字段，与现有 `Tuple` 类型中定义的属性类似。</span><span class="sxs-lookup"><span data-stu-id="3bf05-142">The `ValueTuple` struct has fields named `Item1`, `Item2`, `Item3`, and so on, similar to the properties defined in the existing `Tuple` types.</span></span>
<span data-ttu-id="3bf05-143">这些名称是可用于*未命名元组*的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-143">These names are the only names you can use for *unnamed tuples*.</span></span> <span data-ttu-id="3bf05-144">如果不为元组提供任何备用字段名称，即表示创建了一个未命名元组：</span><span class="sxs-lookup"><span data-stu-id="3bf05-144">When you do not provide any alternative field names to a tuple, you've created an unnamed tuple:</span></span>

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

<span data-ttu-id="3bf05-145">上例中的元组已使用文本常量进行初始化，并且不会有 C# 7.1 中使用“元组字段名称投影”创建的元素名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-145">The tuple in the previous example was initialized using literal constants and won't have element names created using *tuple field name projections* in C# 7.1.</span></span>

<span data-ttu-id="3bf05-146">但是，在初始化元组时，可以使用新语言功能为每个字段提供更好的名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-146">However, when you initialize a tuple, you can use new language features that give better names to each field.</span></span> <span data-ttu-id="3bf05-147">如此便创建了*命名元组*。</span><span class="sxs-lookup"><span data-stu-id="3bf05-147">Doing so creates a *named tuple*.</span></span>
<span data-ttu-id="3bf05-148">命名元组仍将元素命名为 `Item1`、`Item2`、`Item3` 等。</span><span class="sxs-lookup"><span data-stu-id="3bf05-148">Named tuples still have elements named `Item1`, `Item2`, `Item3` and so on.</span></span>
<span data-ttu-id="3bf05-149">不过，它们还会为这些已命名的元素提供同义词。</span><span class="sxs-lookup"><span data-stu-id="3bf05-149">But they also have synonyms for any of those elements that you have named.</span></span>
<span data-ttu-id="3bf05-150">通过为每个元素指定名称即可创建命名元组。</span><span class="sxs-lookup"><span data-stu-id="3bf05-150">You create a named tuple by specifying the names for each element.</span></span> <span data-ttu-id="3bf05-151">其中一种方式是在元组初始化过程中指定名称：</span><span class="sxs-lookup"><span data-stu-id="3bf05-151">One way is to specify the names as part of the tuple initialization:</span></span>

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

<span data-ttu-id="3bf05-152">这些同义词由编译器和语言处理，因此，你可以高效地使用命名元组。</span><span class="sxs-lookup"><span data-stu-id="3bf05-152">These synonyms are handled by the compiler and the language so that you can use named tuples effectively.</span></span> <span data-ttu-id="3bf05-153">IDE 和编辑器可以使用 Roslyn API 读取这些语义名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-153">IDEs and editors can read these semantic names using the Roslyn APIs.</span></span> <span data-ttu-id="3bf05-154">可以在同一程序集中的任何位置通过这些语义名称引用命名元组的元素。</span><span class="sxs-lookup"><span data-stu-id="3bf05-154">You can reference the elements of a named tuple by those semantic names anywhere in the same assembly.</span></span> <span data-ttu-id="3bf05-155">编译器在生成已编译的输出时，会将已定义的名称替换为 `Item*` 等效项。</span><span class="sxs-lookup"><span data-stu-id="3bf05-155">The compiler replaces the names you've defined with `Item*` equivalents when generating the compiled output.</span></span> <span data-ttu-id="3bf05-156">已编译的 Microsoft 中间语言 (MSIL) 不包括为这些元素赋予的名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-156">The compiled Microsoft Intermediate Language (MSIL) does not include the names you've given these elements.</span></span>

<span data-ttu-id="3bf05-157">从 C# 7.1 开始，元组的字段名称可能会通过用于初始化此元组的变量提供。</span><span class="sxs-lookup"><span data-stu-id="3bf05-157">Beginning with C# 7.1, the field names for a tuple may be provided from the variables used to initialize the tuple.</span></span> <span data-ttu-id="3bf05-158">这称为[元组投影初始值设定项](#tuple-projection-initializers)。</span><span class="sxs-lookup"><span data-stu-id="3bf05-158">This is referred to as **[tuple projection initializers](#tuple-projection-initializers)**.</span></span> <span data-ttu-id="3bf05-159">以下代码用于创建名为 `accumulation` 的元组，包含元素 `count`（整数）和 `sum`（双精度）。</span><span class="sxs-lookup"><span data-stu-id="3bf05-159">The following code creates a tuple named `accumulation` with elements `count` (an integer), and `sum` (a double).</span></span>

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

<span data-ttu-id="3bf05-160">编译器必须传达为从公共方法或属性返回的元组创建的这些名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-160">The compiler must communicate those names you created for tuples that are returned from public methods or properties.</span></span> <span data-ttu-id="3bf05-161">在这种情况下，编译器会在方法上添加 <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="3bf05-161">In those cases, the compiler adds a <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> attribute on the method.</span></span> <span data-ttu-id="3bf05-162">此特性包含一个 <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> 列表属性，该属性包含为元组中的每个元素赋予的名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-162">This attribute contains a <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> list property that contains the names given to each of the elements in the tuple.</span></span>

> [!NOTE]
> <span data-ttu-id="3bf05-163">Visual Studio 等开发工具还读取其元数据，并提供 IntelliSense 和其他使用元数据字段名称的功能。</span><span class="sxs-lookup"><span data-stu-id="3bf05-163">Development Tools, such as Visual Studio, also read that metadata, and provide IntelliSense and other features using the metadata field names.</span></span>

<span data-ttu-id="3bf05-164">请务必理解新元组和 `ValueTuple` 类型的这些基础知识，这样才能理解将命名元组赋给彼此的规则。</span><span class="sxs-lookup"><span data-stu-id="3bf05-164">It is important to understand these underlying fundamentals of the new tuples and the `ValueTuple` type in order to understand the rules for assigning named tuples to each other.</span></span>

## <a name="tuple-projection-initializers"></a><span data-ttu-id="3bf05-165">元组投影初始值设定项</span><span class="sxs-lookup"><span data-stu-id="3bf05-165">Tuple projection initializers</span></span>

<span data-ttu-id="3bf05-166">一般情况下，元组投影初始值设定项使用元组初始化语句右侧的变量或字段名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-166">In general, tuple projection initializers work by using the variable or field names from the right-hand side of a tuple initialization statement.</span></span>
<span data-ttu-id="3bf05-167">如果未提供显式名称，上述名称将优先于任何投影的名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-167">If an explicit name is given, that takes precedence over any projected name.</span></span> <span data-ttu-id="3bf05-168">例如，在以下初始值设定项中，元素为 `explicitFieldOne` 和 `explicitFieldTwo`，而非 `localVariableOne` 和 `localVariableTwo`：</span><span class="sxs-lookup"><span data-stu-id="3bf05-168">For example, in the following initializer, the elements are `explicitFieldOne` and `explicitFieldTwo`, not `localVariableOne` and `localVariableTwo`:</span></span>

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

<span data-ttu-id="3bf05-169">对于任何未提供显式名称的字段，将投影适用的隐式名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-169">For any field where an explicit name is not provided, an applicable implicit name is projected.</span></span> <span data-ttu-id="3bf05-170">不要求提供显式或隐式语义名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-170">There is no requirement to provide semantic names, either explicitly or implicitly.</span></span> <span data-ttu-id="3bf05-171">以下初始化表达式具有字段名称 `Item1`其值为 `42`和 `stringContent`（其值为“The answer to everything”）：</span><span class="sxs-lookup"><span data-stu-id="3bf05-171">The following initializer has     field names `Item1`, whose value is `42` and `stringContent`, whose value is "The answer to everything":</span></span>

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

<span data-ttu-id="3bf05-172">在以下两种情况下，不会将候选字段名称投影到元组字段：</span><span class="sxs-lookup"><span data-stu-id="3bf05-172">There are two conditions where candidate field names are not projected onto the tuple field:</span></span>

1. <span data-ttu-id="3bf05-173">候选名称是保留元组名称时。</span><span class="sxs-lookup"><span data-stu-id="3bf05-173">When the candidate name is a reserved tuple name.</span></span> <span data-ttu-id="3bf05-174">示例包括 `Item3`、`ToString` 或 `Rest`。</span><span class="sxs-lookup"><span data-stu-id="3bf05-174">Examples include `Item3`, `ToString`, or `Rest`.</span></span>
1. <span data-ttu-id="3bf05-175">候选名称重复了另一元组的显式或隐式字段名称时。</span><span class="sxs-lookup"><span data-stu-id="3bf05-175">When the candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="3bf05-176">这两个条件可避免多义性。</span><span class="sxs-lookup"><span data-stu-id="3bf05-176">These conditions avoid ambiguity.</span></span> <span data-ttu-id="3bf05-177">如果这些名称已用作元组中某字段的字段名称，它们将导致多义。</span><span class="sxs-lookup"><span data-stu-id="3bf05-177">These names would cause an ambiguity if they were used as the field names for a field in a tuple.</span></span> <span data-ttu-id="3bf05-178">这两个条件都不会导致编译时错误。</span><span class="sxs-lookup"><span data-stu-id="3bf05-178">Neither of these conditions cause compile-time errors.</span></span> <span data-ttu-id="3bf05-179">但不会向没有投影名称的元素投影语义名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-179">Instead, the elements without projected names do not have semantic names projected for them.</span></span>  <span data-ttu-id="3bf05-180">以下示例说明了这两个条件：</span><span class="sxs-lookup"><span data-stu-id="3bf05-180">The following examples demonstrate these conditions:</span></span>

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

<span data-ttu-id="3bf05-181">这些情况不会导致编译器错误，因为当元组字段名称投影不可用时，它将成为使用 C# 7.0 编写的代码的一项重大改变。</span><span class="sxs-lookup"><span data-stu-id="3bf05-181">These situations do not cause compiler errors because that would be a breaking change for code written with C# 7.0, when tuple field name projections were not available.</span></span>

## <a name="equality-and-tuples"></a><span data-ttu-id="3bf05-182">相等和元组</span><span class="sxs-lookup"><span data-stu-id="3bf05-182">Equality and tuples</span></span>

<span data-ttu-id="3bf05-183">从 C# 7.3 开始，元组类型支持 `==` 和 `!=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="3bf05-183">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="3bf05-184">这些运算符按顺序将左边参数的每个成员与右边参数的每个成员进行比较。</span><span class="sxs-lookup"><span data-stu-id="3bf05-184">These operators work by comparing each member of the left argument to each member of the right argument in order.</span></span> <span data-ttu-id="3bf05-185">这些比较将发生短路。</span><span class="sxs-lookup"><span data-stu-id="3bf05-185">These comparisons short-circuit.</span></span> <span data-ttu-id="3bf05-186">只要有一对不相等，它们即会停止计算成员。</span><span class="sxs-lookup"><span data-stu-id="3bf05-186">They will stop evaluating members as soon as one pair is not equal.</span></span> <span data-ttu-id="3bf05-187">以下代码示例使用 `==`，但比较规则均适用于 `!=`。</span><span class="sxs-lookup"><span data-stu-id="3bf05-187">The following code examples use `==`, but the comparison rules all apply to `!=`.</span></span> <span data-ttu-id="3bf05-188">以下代码示例演示两对整数的相等比较：</span><span class="sxs-lookup"><span data-stu-id="3bf05-188">The following code example shows an equality comparison for two pairs of integers:</span></span>

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

<span data-ttu-id="3bf05-189">有几条规则，可使元组相等测试更方便。</span><span class="sxs-lookup"><span data-stu-id="3bf05-189">There are several rules that make tuple equality tests more convenient.</span></span> <span data-ttu-id="3bf05-190">如果其中一个元组是可以为空值的元组，则元组相等将执行[提升转换](~/_csharplang/spec/conversions.md#lifted-conversion-operators)，如以下代码中所示：</span><span class="sxs-lookup"><span data-stu-id="3bf05-190">Tuple equality performs [lifted conversions](~/_csharplang/spec/conversions.md#lifted-conversion-operators) if one of the tuples is a nullable tuple, as shown in the following code:</span></span>

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

<span data-ttu-id="3bf05-191">元组相等还将对这两个元组的每个成员执行隐式转换。</span><span class="sxs-lookup"><span data-stu-id="3bf05-191">Tuple equality also performs implicit conversions on each member of both tuples.</span></span> <span data-ttu-id="3bf05-192">这些转换包括提升转换、扩大转换或其他隐式转换。</span><span class="sxs-lookup"><span data-stu-id="3bf05-192">These include lifted conversions, widening conversions, or other implicit conversions.</span></span> <span data-ttu-id="3bf05-193">以下示例演示整数 2 元组可以与较长的 2 元组进行比较，因为进行了从整数元组到较长元组的隐式转换：</span><span class="sxs-lookup"><span data-stu-id="3bf05-193">The following examples show that an integer 2-tuple can be compared to a long 2-tuple because of the implicit conversion from integer to long:</span></span>

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

<span data-ttu-id="3bf05-194">元组成员名称不参与相等测试。</span><span class="sxs-lookup"><span data-stu-id="3bf05-194">The names of the tuple members do not participate in tests for equality.</span></span> <span data-ttu-id="3bf05-195">但是，如果其中一个操作数是含有显式名称的元组文本，则当这些名称与其他操作数的名称不匹配时，编译器将生成警告 CS8383。</span><span class="sxs-lookup"><span data-stu-id="3bf05-195">However, if one of the operands is a tuple literal with explicit names, the compiler generates warning CS8383 if those names do not match the names of the other operand.</span></span>
<span data-ttu-id="3bf05-196">在两个操作数都为元组文本的情况下，警告位于右侧操作数，如以下示例中所述：</span><span class="sxs-lookup"><span data-stu-id="3bf05-196">In the case where both operands are tuple literals, the warning is on the right operand as shown in the following example:</span></span>

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

<span data-ttu-id="3bf05-197">最后，元组可能包含嵌套元组。</span><span class="sxs-lookup"><span data-stu-id="3bf05-197">Finally, tuples may contain nested tuples.</span></span> <span data-ttu-id="3bf05-198">元组相等通过嵌套元组比较每个操作数的“形状”，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="3bf05-198">Tuple equality compares the "shape" of each operand through nested tuples as shown in the following example:</span></span>

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

<span data-ttu-id="3bf05-199">当两个元组具有不同形状时，比较它们是否相等（或不相等）将出现编译时错误。</span><span class="sxs-lookup"><span data-stu-id="3bf05-199">It's a compile time error to compare two tuples for equality (or inequality) when they have different shapes.</span></span> <span data-ttu-id="3bf05-200">编译器不会尝试对嵌套元组进行任何析构来比较它们。</span><span class="sxs-lookup"><span data-stu-id="3bf05-200">The compiler won't attempt any deconstruction of nested tuples in order to compare them.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="3bf05-201">赋值和元组</span><span class="sxs-lookup"><span data-stu-id="3bf05-201">Assignment and tuples</span></span>

<span data-ttu-id="3bf05-202">语言支持在具有相同元素数量的元组类型之间赋值，其中每个右侧元素都可被隐式转换为相应的左侧元素。</span><span class="sxs-lookup"><span data-stu-id="3bf05-202">The language supports assignment between tuple types that have the same number of elements, where each right-hand side element can be implicitly converted to its corresponding left-hand side element.</span></span> <span data-ttu-id="3bf05-203">对于其他转换，不考虑进行赋值。</span><span class="sxs-lookup"><span data-stu-id="3bf05-203">Other conversions aren't considered for assignments.</span></span> <span data-ttu-id="3bf05-204">当两个元组具有不同形状时，将一个元祖分配给另一个元祖将出现编译时错误。</span><span class="sxs-lookup"><span data-stu-id="3bf05-204">It's a compile time error to assign one tuple to another when they have different shapes.</span></span> <span data-ttu-id="3bf05-205">编译器不会尝试对嵌套元组进行任何析构来分配它们。</span><span class="sxs-lookup"><span data-stu-id="3bf05-205">The compiler won't attempt any deconstruction of nested tuples in order to assign them.</span></span>
<span data-ttu-id="3bf05-206">让我们看一下元组类型之间允许的赋值类型。</span><span class="sxs-lookup"><span data-stu-id="3bf05-206">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="3bf05-207">注意以下示例中使用的这些变量：</span><span class="sxs-lookup"><span data-stu-id="3bf05-207">Consider these variables used in the following examples:</span></span>

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

<span data-ttu-id="3bf05-208">前两个变量（`unnamed` 和 `anonymous`）没有为元素提供语义名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-208">The first two variables, `unnamed` and `anonymous` do not have semantic names provided for the elements.</span></span> <span data-ttu-id="3bf05-209">字段名称为 `Item1` 和 `Item2`。</span><span class="sxs-lookup"><span data-stu-id="3bf05-209">The field names are `Item1` and `Item2`.</span></span>
<span data-ttu-id="3bf05-210">后两个变量（`named` 和 `differentName`）为元素提供了语义名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-210">The last two variables, `named` and `differentName` have semantic names given for the elements.</span></span> <span data-ttu-id="3bf05-211">这两个元组具有不同的元素名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-211">These two tuples have different names for the elements.</span></span>

<span data-ttu-id="3bf05-212">这四个元组具有相同数量的元素（称为“基数”），这些元素的类型也完全一样。</span><span class="sxs-lookup"><span data-stu-id="3bf05-212">All four of these tuples have the same number of elements (referred to as 'cardinality') and the types of those elements are identical.</span></span> <span data-ttu-id="3bf05-213">因此可进行以下赋值：</span><span class="sxs-lookup"><span data-stu-id="3bf05-213">Therefore, all of these assignments work:</span></span>

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

<span data-ttu-id="3bf05-214">请注意，元组的名称未赋值。</span><span class="sxs-lookup"><span data-stu-id="3bf05-214">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="3bf05-215">元素的赋值顺序遵循元素在元组中的顺序。</span><span class="sxs-lookup"><span data-stu-id="3bf05-215">The values of the elements are assigned following the order of the elements in the tuple.</span></span>

<span data-ttu-id="3bf05-216">元素类型或数量不同的元组不可赋值：</span><span class="sxs-lookup"><span data-stu-id="3bf05-216">Tuples of different types or numbers of elements are not assignable:</span></span>

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="3bf05-217">作为方法返回值的元组</span><span class="sxs-lookup"><span data-stu-id="3bf05-217">Tuples as method return values</span></span>

<span data-ttu-id="3bf05-218">元组最常见的用途之一是作为方法返回值。</span><span class="sxs-lookup"><span data-stu-id="3bf05-218">One of the most common uses for tuples is as a method return value.</span></span> <span data-ttu-id="3bf05-219">我们来看一个示例。</span><span class="sxs-lookup"><span data-stu-id="3bf05-219">Let's walk through one example.</span></span> <span data-ttu-id="3bf05-220">以下面的方法为例，该方法计算一个数列的标准差：</span><span class="sxs-lookup"><span data-stu-id="3bf05-220">Consider this method that computes the standard deviation for a sequence of numbers:</span></span>

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> <span data-ttu-id="3bf05-221">这些示例计算得出未修正的样本标准差。</span><span class="sxs-lookup"><span data-stu-id="3bf05-221">These examples compute the uncorrected sample standard deviation.</span></span>
> <span data-ttu-id="3bf05-222">与 `Average` 扩展方法一样，修正后的样本标准差公式将与平均数之差的平方的总和除以 (N-1)，而不是 N。</span><span class="sxs-lookup"><span data-stu-id="3bf05-222">The corrected sample standard deviation formula would divide the sum of the squared differences from the mean by (N-1) instead of N, as the `Average` extension method does.</span></span> <span data-ttu-id="3bf05-223">有关这些标准差公式之间的区别的更多详细信息，请查看统计信息文本。</span><span class="sxs-lookup"><span data-stu-id="3bf05-223">Consult a statistics text for more details on the differences between these formulas for standard deviation.</span></span>

<span data-ttu-id="3bf05-224">前面的代码采用教科书上的标准差公式。</span><span class="sxs-lookup"><span data-stu-id="3bf05-224">The preceding code follows the textbook formula for the standard deviation.</span></span> <span data-ttu-id="3bf05-225">它会生成正确的答案，但实施起来非常低效。</span><span class="sxs-lookup"><span data-stu-id="3bf05-225">It produces the correct answer, but it's an inefficient implementation.</span></span> <span data-ttu-id="3bf05-226">此方法对数列进行两次计算：一次生成平均数，一次生成与平均数之差的平方的平均数。</span><span class="sxs-lookup"><span data-stu-id="3bf05-226">This method enumerates the sequence twice: Once to produce the average, and once to produce the average of the square of the difference of the average.</span></span>
<span data-ttu-id="3bf05-227">（请记住，LINQ 查询进行迟缓计算，因此，在计算与平均数的差以及这些差的平均数时只需计算一次。）</span><span class="sxs-lookup"><span data-stu-id="3bf05-227">(Remember that LINQ queries are evaluated lazily, so the computation of the differences from the mean and the average of those differences makes only one enumeration.)</span></span>

<span data-ttu-id="3bf05-228">有一个计算标准差的备用公式，它只对数列计算一次。</span><span class="sxs-lookup"><span data-stu-id="3bf05-228">There is an alternative formula that computes standard deviation using only one enumeration of the sequence.</span></span>  <span data-ttu-id="3bf05-229">此计算公式在计算数列时生成两个值：数列中所有项的总和，以及每个平方值的总和：</span><span class="sxs-lookup"><span data-stu-id="3bf05-229">This computation produces two values as it enumerates the sequence: the sum of all items in the sequence, and the sum of the each value squared:</span></span>

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

<span data-ttu-id="3bf05-230">此版本虽然只对序列进行一次枚举。</span><span class="sxs-lookup"><span data-stu-id="3bf05-230">This version enumerates the sequence exactly once.</span></span> <span data-ttu-id="3bf05-231">但其代码不可重复使用。</span><span class="sxs-lookup"><span data-stu-id="3bf05-231">But it's not reusable code.</span></span> <span data-ttu-id="3bf05-232">到后面，你会发现许多不同的统计计算会用到数列项数、数列总和以及数列平方和。</span><span class="sxs-lookup"><span data-stu-id="3bf05-232">As you keep working, you'll find that many different statistical computations use the number of items in the sequence, the sum of the sequence, and the sum of the squares of the sequence.</span></span> <span data-ttu-id="3bf05-233">让我们重构此方法，编写一个可生成这三个值的实用方法。</span><span class="sxs-lookup"><span data-stu-id="3bf05-233">Let's refactor this method and write a utility method that produces all three of those values.</span></span> <span data-ttu-id="3bf05-234">所有这三个值都可以作为一个元组返回。</span><span class="sxs-lookup"><span data-stu-id="3bf05-234">All three values can be returned as a tuple.</span></span>

<span data-ttu-id="3bf05-235">让我们更新此方法，以便将在计算过程中得出的三个值存储在一个元组中。</span><span class="sxs-lookup"><span data-stu-id="3bf05-235">Let's update this method so the three values computed during the enumeration are stored in a tuple.</span></span> <span data-ttu-id="3bf05-236">以下是更新后的版本：</span><span class="sxs-lookup"><span data-stu-id="3bf05-236">That creates this version:</span></span>

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

<span data-ttu-id="3bf05-237">在 Visual Studio 的重构支持下，可以轻松地将核心统计信息的功能提取到私有方法中。</span><span class="sxs-lookup"><span data-stu-id="3bf05-237">Visual Studio's Refactoring support makes it easy to extract the functionality for the core statistics into a private method.</span></span> <span data-ttu-id="3bf05-238">从而得到一个 `private static` 方法，该方法返回具有 `Sum`、`SumOfSquares` 和 `Count` 这三个值的元组类型：</span><span class="sxs-lookup"><span data-stu-id="3bf05-238">That gives you a `private static` method that returns the tuple type with the three values of `Sum`, `SumOfSquares`, and `Count`:</span></span>

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]

<span data-ttu-id="3bf05-239">如果你想手动进行一些快速编辑，该语言可提供更多选项供你使用。</span><span class="sxs-lookup"><span data-stu-id="3bf05-239">The language enables a couple more options that you can use, if you want to make a few quick edits by hand.</span></span> <span data-ttu-id="3bf05-240">首先，可以使用 `var` 声明来初始化 `ComputeSumAndSumOfSquares` 方法调用的元组结果。</span><span class="sxs-lookup"><span data-stu-id="3bf05-240">First, you can use the `var` declaration to initialize the tuple result from the `ComputeSumAndSumOfSquares` method call.</span></span> <span data-ttu-id="3bf05-241">此外，还可以在 `ComputeSumAndSumOfSquares` 方法内创建三个离散变量。</span><span class="sxs-lookup"><span data-stu-id="3bf05-241">You can also create three discrete variables inside the `ComputeSumAndSumOfSquares` method.</span></span> <span data-ttu-id="3bf05-242">下面的代码演示了最终版本：</span><span class="sxs-lookup"><span data-stu-id="3bf05-242">The final version is shown in the following code:</span></span>

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

<span data-ttu-id="3bf05-243">这个最终版本可用于任何需要这三个值或其任意子集的方法。</span><span class="sxs-lookup"><span data-stu-id="3bf05-243">This final version can be used for any method that needs those three values, or any subset of them.</span></span>

<span data-ttu-id="3bf05-244">该语言支持其他用于管理这些元组返回方法中的元素名称的选项。</span><span class="sxs-lookup"><span data-stu-id="3bf05-244">The language supports other options in managing the names of the elements in these tuple-returning methods.</span></span>

<span data-ttu-id="3bf05-245">可以删除返回值声明中的字段名称，返回一个未命名元组：</span><span class="sxs-lookup"><span data-stu-id="3bf05-245">You can remove the field names from the return value declaration and return an unnamed tuple:</span></span>

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

<span data-ttu-id="3bf05-246">此元组的字段被命名为 `Item1`、`Item2` 和 `Item3`。</span><span class="sxs-lookup"><span data-stu-id="3bf05-246">The fields of this tuple are named `Item1`, `Item2`, and `Item3`.</span></span>
<span data-ttu-id="3bf05-247">建议为从方法返回的元组的元素提供语义名称。</span><span class="sxs-lookup"><span data-stu-id="3bf05-247">It's recommended that you provide semantic names to the elements of tuples returned from methods.</span></span>

<span data-ttu-id="3bf05-248">元组另一个常见的用途是在你创作 LINQ 查询时。</span><span class="sxs-lookup"><span data-stu-id="3bf05-248">Another idiom where tuples can be useful is when you are authoring LINQ queries.</span></span> <span data-ttu-id="3bf05-249">最终投影的结果通常包含被选中的对象的某些（而不是全部）属性。</span><span class="sxs-lookup"><span data-stu-id="3bf05-249">The final projected result often contains some, but not all, of the properties of the objects being selected.</span></span>

<span data-ttu-id="3bf05-250">传统做法是将查询结果投影成一个匿名类型的对象序列。</span><span class="sxs-lookup"><span data-stu-id="3bf05-250">You would traditionally project the results of the query into a sequence of objects that were an anonymous type.</span></span> <span data-ttu-id="3bf05-251">这种做法存在很多限制，主要是因为匿名类型无法在方法的返回类型中方便地命名。</span><span class="sxs-lookup"><span data-stu-id="3bf05-251">That presented many limitations, primarily because anonymous types could not conveniently be named in the return type for a method.</span></span> <span data-ttu-id="3bf05-252">也可以将 `object` 或 `dynamic` 用作结果类型，但这种备用方法会产生高昂的性能成本。</span><span class="sxs-lookup"><span data-stu-id="3bf05-252">Alternatives using `object` or `dynamic` as the type of the result came with significant performance costs.</span></span>

<span data-ttu-id="3bf05-253">返回一个元组类型序列非常简单，并且不管是在编译时还是通过 IDE 工具，都可以获取其元素的名称和类型。</span><span class="sxs-lookup"><span data-stu-id="3bf05-253">Returning a sequence of a tuple type is easy, and the names and types of the elements are available at compile time and through IDE tools.</span></span>
<span data-ttu-id="3bf05-254">以 ToDo 应用程序为例。</span><span class="sxs-lookup"><span data-stu-id="3bf05-254">For example, consider a ToDo application.</span></span> <span data-ttu-id="3bf05-255">可以定义一个与下面类似的类，以表示待办事项列表中的某一项：</span><span class="sxs-lookup"><span data-stu-id="3bf05-255">You might define a class similar to the following to represent a single entry in the ToDo list:</span></span>

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

<span data-ttu-id="3bf05-256">移动应用程序可能支持当前待办事项的简洁版，即仅显示标题。</span><span class="sxs-lookup"><span data-stu-id="3bf05-256">Your mobile applications may support a compact form of the current ToDo items that only displays the title.</span></span> <span data-ttu-id="3bf05-257">该 LINQ 查询生成一个仅包含 ID 和标题的投影。</span><span class="sxs-lookup"><span data-stu-id="3bf05-257">That LINQ query would make a projection that includes only the ID and the title.</span></span> <span data-ttu-id="3bf05-258">返回一个元组序列的方法很好地表达了该设计：</span><span class="sxs-lookup"><span data-stu-id="3bf05-258">A method that returns a sequence of tuples expresses that design well:</span></span>

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> <span data-ttu-id="3bf05-259">在 C# 7.1 中，通过元组投影可使用元素，以类似于在匿名类型中命名属性的方式创建命名元组。</span><span class="sxs-lookup"><span data-stu-id="3bf05-259">In C# 7.1, tuple projections enable you to create named tuples using elements, in a manner similar to the property naming in anonymous types.</span></span> <span data-ttu-id="3bf05-260">在以上代码中，查询投影中的 `select` 语句将创建具有元素 `ID` 和 `Title` 的元组。</span><span class="sxs-lookup"><span data-stu-id="3bf05-260">In the above code, the `select` statement in the query projection creates a tuple that has elements `ID` and `Title`.</span></span>

<span data-ttu-id="3bf05-261">命名元组可以是签名的一部分。</span><span class="sxs-lookup"><span data-stu-id="3bf05-261">The named tuple can be part of the signature.</span></span> <span data-ttu-id="3bf05-262">它让编译器和 IDE 工具提供静态检查，看结果的用法是否正确。</span><span class="sxs-lookup"><span data-stu-id="3bf05-262">It lets the compiler and IDE tools provide static checking that you are using the result correctly.</span></span> <span data-ttu-id="3bf05-263">命名元组还承载了静态类型信息，因此无需使用高成本的运行时功能（如反射或动态绑定）来处理结果。</span><span class="sxs-lookup"><span data-stu-id="3bf05-263">The named tuple also carries the static type information so there is no need to use expensive run time features like reflection or dynamic binding to work with the results.</span></span>

## <a name="deconstruction"></a><span data-ttu-id="3bf05-264">析构</span><span class="sxs-lookup"><span data-stu-id="3bf05-264">Deconstruction</span></span>

<span data-ttu-id="3bf05-265">通过对方法返回的元组进行析构，可以解封元组中的所有项。</span><span class="sxs-lookup"><span data-stu-id="3bf05-265">You can unpackage all the items in a tuple by *deconstructing* the tuple returned by a method.</span></span> <span data-ttu-id="3bf05-266">有三种元组析构方法。</span><span class="sxs-lookup"><span data-stu-id="3bf05-266">There are three different approaches to deconstructing tuples.</span></span>  <span data-ttu-id="3bf05-267">首先，可在括号内显式声明每个字段的类型，为元组中的每个元素创建离散变量：</span><span class="sxs-lookup"><span data-stu-id="3bf05-267">First, you can explicitly declare the type of each field inside parentheses to create discrete variables for each of the elements in the tuple:</span></span>

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

<span data-ttu-id="3bf05-268">也可以通过在括号外使用 `var` 关键字，隐式声明元组中每个字段的类型化变量：</span><span class="sxs-lookup"><span data-stu-id="3bf05-268">You can also declare implicitly typed variables for each field in a tuple by using the `var` keyword outside the parentheses:</span></span>

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

<span data-ttu-id="3bf05-269">还可以在括号内将 `var` 关键字与任意或全部变量声明结合使用。</span><span class="sxs-lookup"><span data-stu-id="3bf05-269">It is also legal to use the `var` keyword with any, or all of the variable declarations inside the parentheses.</span></span>

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

<span data-ttu-id="3bf05-270">即使元组中的每个字段都具有相同的类型，也不能在括号外使用特定类型。</span><span class="sxs-lookup"><span data-stu-id="3bf05-270">You cannot use a specific type outside the parentheses, even if every field in the tuple has the same type.</span></span>

<span data-ttu-id="3bf05-271">也可以使用现有声明析构元组：</span><span class="sxs-lookup"><span data-stu-id="3bf05-271">You can deconstruct tuples with existing declarations as well:</span></span>

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> <span data-ttu-id="3bf05-272">不能混合现有声明和括号内的声明。</span><span class="sxs-lookup"><span data-stu-id="3bf05-272">You cannot mix existing declarations with declarations inside the parentheses.</span></span> <span data-ttu-id="3bf05-273">例如，不允许以下内容：`(var x, y) = MyMethod();`。</span><span class="sxs-lookup"><span data-stu-id="3bf05-273">For instance, the following is not allowed: `(var x, y) = MyMethod();`.</span></span> <span data-ttu-id="3bf05-274">这将产生错误 CS8184，因为 x 在括号内声明，且 y 以前在其他位置声明。</span><span class="sxs-lookup"><span data-stu-id="3bf05-274">This produces error CS8184 because *x* is declared inside the parentheses and *y* is previously declared elsewhere.</span></span>

### <a name="deconstructing-user-defined-types"></a><span data-ttu-id="3bf05-275">析构用户定义类型</span><span class="sxs-lookup"><span data-stu-id="3bf05-275">Deconstructing user-defined types</span></span>

<span data-ttu-id="3bf05-276">如上所示，可以析构任何元组类型。</span><span class="sxs-lookup"><span data-stu-id="3bf05-276">Any tuple type can be deconstructed as shown above.</span></span> <span data-ttu-id="3bf05-277">也可以对任何用户定义的类型（类、结构甚至接口）轻松启用析构。</span><span class="sxs-lookup"><span data-stu-id="3bf05-277">It's also easy to enable deconstruction on any user-defined type (classes, structs, or even interfaces).</span></span>

<span data-ttu-id="3bf05-278">类型作者可定义一个或多个赋值给任意数量的 [`out` 变量](language-reference/keywords/out-parameter-modifier.md)的 `Deconstruct` 方法，这类变量表示构成该类型的数据元素。</span><span class="sxs-lookup"><span data-stu-id="3bf05-278">The type author can define one or more `Deconstruct` methods that assign values to any number of [`out` variables](language-reference/keywords/out-parameter-modifier.md) representing the data elements that make up the type.</span></span> <span data-ttu-id="3bf05-279">例如，以下 `Person` 类型定义 `Deconstruct` 方法，该方法将 person 对象析构成表示名字和姓氏的元素：</span><span class="sxs-lookup"><span data-stu-id="3bf05-279">For example, the following `Person` type defines a `Deconstruct` method that deconstructs a person object into the elements representing the first name and last name:</span></span>

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

<span data-ttu-id="3bf05-280">该析构方法支持从 `Person` 赋值给两个表示 `FirstName` 和 `LastName` 属性的字符串：</span><span class="sxs-lookup"><span data-stu-id="3bf05-280">The deconstruct method enables assignment from a `Person` to two strings, representing the `FirstName` and `LastName` properties:</span></span>

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

<span data-ttu-id="3bf05-281">即使对未创作的类型，也可以启用析构。</span><span class="sxs-lookup"><span data-stu-id="3bf05-281">You can enable deconstruction even for types you did not author.</span></span>
<span data-ttu-id="3bf05-282">`Deconstruct` 方法可以是一种扩展方法，用于解封对象的可访问数据成员。</span><span class="sxs-lookup"><span data-stu-id="3bf05-282">The `Deconstruct` method can be an extension method that unpackages the accessible data members of an object.</span></span> <span data-ttu-id="3bf05-283">以下示例显示从 `Person` 类型派生的 `Student` 类型，以及将 `Student` 析构成三个变量（表示 `FirstName`、`LastName` 和 `GPA`）的扩展方法：</span><span class="sxs-lookup"><span data-stu-id="3bf05-283">The example below shows a `Student` type, derived from the `Person` type, and an extension method that deconstructs a `Student` into three variables, representing the `FirstName`, the `LastName`, and the `GPA`:</span></span>

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

<span data-ttu-id="3bf05-284">`Student` 对象现在有两个可访问的 `Deconstruct` 方法：为 `Student` 类型声明的扩展方法，以及 `Person` 类型的成员。</span><span class="sxs-lookup"><span data-stu-id="3bf05-284">A `Student` object now has two accessible `Deconstruct` methods: the extension method declared for `Student` types, and the member of the `Person` type.</span></span> <span data-ttu-id="3bf05-285">两者都可用，可将 `Student` 析构为两个或三个变量。</span><span class="sxs-lookup"><span data-stu-id="3bf05-285">Both are in scope, and that enables a `Student` to be deconstructed into either two variables or three.</span></span>
<span data-ttu-id="3bf05-286">如果为 student 分配三个变量，则返回名字、姓氏和 GPA。</span><span class="sxs-lookup"><span data-stu-id="3bf05-286">If you assign a student to three variables, the first name, last name, and GPA are all returned.</span></span> <span data-ttu-id="3bf05-287">如果为 student 分配两个变量，则仅返回名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="3bf05-287">If you assign a student to two variables, only the first name and the last name are returned.</span></span>

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

<span data-ttu-id="3bf05-288">在某个类或类层次结构中定义多个 `Deconstruct` 方法时应非常小心。</span><span class="sxs-lookup"><span data-stu-id="3bf05-288">You should be careful defining multiple `Deconstruct` methods in a class or a class hierarchy.</span></span> <span data-ttu-id="3bf05-289">具有相同数量的 `out` 参数的多个 `Deconstruct` 方法很快就会产生歧义。</span><span class="sxs-lookup"><span data-stu-id="3bf05-289">Multiple `Deconstruct` methods that have the same number of `out` parameters can quickly cause ambiguities.</span></span> <span data-ttu-id="3bf05-290">调用方可能无法轻松调用所需的 `Deconstruct` 方法。</span><span class="sxs-lookup"><span data-stu-id="3bf05-290">Callers may not be able to easily call the desired `Deconstruct` method.</span></span>

<span data-ttu-id="3bf05-291">在此示例中，发生有歧义的调用的几率很小，因为用于 `Person` 的 `Deconstruct` 方法有两个输出参数，而用于 `Student` 的 `Deconstruct` 方法有三个输出参数。</span><span class="sxs-lookup"><span data-stu-id="3bf05-291">In this example, there is minimal chance for an ambiguous call because the `Deconstruct` method for `Person` has two output parameters, and the `Deconstruct` method for `Student` has three.</span></span>

<span data-ttu-id="3bf05-292">析构运算符不参与测试相等。</span><span class="sxs-lookup"><span data-stu-id="3bf05-292">Deconstruction operators do not participate in testing equality.</span></span> <span data-ttu-id="3bf05-293">下面的示例生成编译器错误 CS0019：</span><span class="sxs-lookup"><span data-stu-id="3bf05-293">The following example generates compiler error CS0019:</span></span>

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

<span data-ttu-id="3bf05-294">`Deconstruct` 方法无法将 `Person` 对象 `p` 转换为包含两个字符串的元组，但它在相等测试上下文中不适用。</span><span class="sxs-lookup"><span data-stu-id="3bf05-294">The `Deconstruct` method could convert the `Person` object `p` to a tuple containing two strings, but it is not applicable in the context of equality tests.</span></span>

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="3bf05-295">元组作为 out 参数</span><span class="sxs-lookup"><span data-stu-id="3bf05-295">Tuples as out parameters</span></span>

<span data-ttu-id="3bf05-296">元组自身可用作 [`out` 参数](language-reference/keywords/out-parameter-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="3bf05-296">Tuples can be used as [`out` parameters](language-reference/keywords/out-parameter-modifier.md) *themselves*.</span></span> <span data-ttu-id="3bf05-297">不要与前面提到的[析构函数](#deconstruction)部分中的任何多义性混淆。</span><span class="sxs-lookup"><span data-stu-id="3bf05-297">Not to be confused with any ambiguity previously mentioned in the [Deconstruction](#deconstruction) section.</span></span> <span data-ttu-id="3bf05-298">在方法调用中，只需描述元组的形状：</span><span class="sxs-lookup"><span data-stu-id="3bf05-298">In a method call, you need only describe the tuple's shape:</span></span>

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

<span data-ttu-id="3bf05-299">另外，还可以使用 [unnamed](#named-and-unnamed-tuples) 元组，并将其字段作为 `Item1` 和 `Item2` 引用：</span><span class="sxs-lookup"><span data-stu-id="3bf05-299">Alternatively, you could use an [_unnamed_](#named-and-unnamed-tuples) tuple and refer to its fields as `Item1` and `Item2`:</span></span>

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a><span data-ttu-id="3bf05-300">结束语</span><span class="sxs-lookup"><span data-stu-id="3bf05-300">Conclusion</span></span>

<span data-ttu-id="3bf05-301">命名元组的新语言和库支持简化了设计工作：与类和结构一样，使用数据结构存储多个元素，但不定义行为。</span><span class="sxs-lookup"><span data-stu-id="3bf05-301">The new language and library support for named tuples makes it much easier to work with designs that use data structures that store multiple elements but do not define behavior, as classes and structs do.</span></span> <span data-ttu-id="3bf05-302">对这些类型使用元组非常简单明了。</span><span class="sxs-lookup"><span data-stu-id="3bf05-302">It's easy and concise to use tuples for those types.</span></span> <span data-ttu-id="3bf05-303">既可以获得静态类型检查的所有好处，又不需要使用更复杂的 `class` 或 `struct` 语法来创作类型。</span><span class="sxs-lookup"><span data-stu-id="3bf05-303">You get all the benefits of static type checking, without needing to author types using the more verbose `class` or `struct` syntax.</span></span> <span data-ttu-id="3bf05-304">即便如此，元组还是对 `private` 或 `internal` 这样的实用方法最有用。</span><span class="sxs-lookup"><span data-stu-id="3bf05-304">Even so, they are most useful for utility methods that are `private`, or `internal`.</span></span> <span data-ttu-id="3bf05-305">当公共方法返回具有多个元素的值时，请创建用户定义的类型（`class` 或 `struct` 类型）。</span><span class="sxs-lookup"><span data-stu-id="3bf05-305">Create user-defined types, either `class` or `struct` types when your public methods return a value that has multiple elements.</span></span>
