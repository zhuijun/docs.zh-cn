---
title: 枚举设计
description: 枚举的设计，这是一种特殊类型的值类型。 简单枚举保留小型的已关闭选择集。 标记枚举支持对枚举值执行按位运算。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 40a9faf53dc8a03674cd59074244c15cd304bdd2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768532"
---
# <a name="enum-design"></a><span data-ttu-id="d720f-105">枚举设计</span><span class="sxs-lookup"><span data-stu-id="d720f-105">Enum Design</span></span>

<span data-ttu-id="d720f-106">枚举是一种特殊类型的值类型。</span><span class="sxs-lookup"><span data-stu-id="d720f-106">Enums are a special kind of value type.</span></span> <span data-ttu-id="d720f-107">有两种类型的枚举：简单枚举和标记枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-107">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="d720f-108">简单枚举表示小型关闭的选项集。</span><span class="sxs-lookup"><span data-stu-id="d720f-108">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="d720f-109">简单枚举的一个常见示例是一组颜色。</span><span class="sxs-lookup"><span data-stu-id="d720f-109">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="d720f-110">标记枚举旨在支持枚举值的按位运算。</span><span class="sxs-lookup"><span data-stu-id="d720f-110">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="d720f-111">标志枚举的一个常见示例是选项的列表。</span><span class="sxs-lookup"><span data-stu-id="d720f-111">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="d720f-112">✔️确实使用枚举来表示值集的强类型参数、属性和返回值。</span><span class="sxs-lookup"><span data-stu-id="d720f-112">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="d720f-113">✔️使用枚举而不是静态常量。</span><span class="sxs-lookup"><span data-stu-id="d720f-113">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="d720f-114">❌不要对开放集（如操作系统版本、朋友名称等）使用枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-114">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="d720f-115">❌不要提供旨在供将来使用的保留枚举值。</span><span class="sxs-lookup"><span data-stu-id="d720f-115">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="d720f-116">你始终可以在以后的阶段将值添加到现有枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-116">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="d720f-117">有关向枚举添加值的详细信息，请参阅[将值添加到枚举](#add_value)。</span><span class="sxs-lookup"><span data-stu-id="d720f-117">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="d720f-118">保留值只是污染一组真实值，往往导致用户错误。</span><span class="sxs-lookup"><span data-stu-id="d720f-118">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="d720f-119">❌避免公开只包含一个值的枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-119">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="d720f-120">若要确保未来的 C Api 可扩展性，常见的做法是将保留参数添加到方法签名。</span><span class="sxs-lookup"><span data-stu-id="d720f-120">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="d720f-121">此类保留参数可表示为具有单个默认值的枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-121">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="d720f-122">不应在托管 Api 中完成此操作。</span><span class="sxs-lookup"><span data-stu-id="d720f-122">This should not be done in managed APIs.</span></span> <span data-ttu-id="d720f-123">方法重载允许在未来版本中添加参数。</span><span class="sxs-lookup"><span data-stu-id="d720f-123">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="d720f-124">❌不要在枚举中包含 sentinel 值。</span><span class="sxs-lookup"><span data-stu-id="d720f-124">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="d720f-125">尽管它们有时对框架开发人员很有帮助，但对于框架的用户来说，sentinel 值会令人感到困惑。</span><span class="sxs-lookup"><span data-stu-id="d720f-125">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="d720f-126">它们用于跟踪枚举的状态，而不是由枚举表示的集中的值之一。</span><span class="sxs-lookup"><span data-stu-id="d720f-126">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="d720f-127">✔️在简单枚举上提供零值。</span><span class="sxs-lookup"><span data-stu-id="d720f-127">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="d720f-128">请考虑调用值，如 "None"。</span><span class="sxs-lookup"><span data-stu-id="d720f-128">Consider calling the value something like "None."</span></span> <span data-ttu-id="d720f-129">如果此类值不适合于此特定枚举，则应将基础值指定为零的最常见默认值。</span><span class="sxs-lookup"><span data-stu-id="d720f-129">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="d720f-130">✔️考虑使用 <xref:System.Int32> （大多数编程语言中的默认值）作为枚举的基础类型，除非满足以下任一条件：</span><span class="sxs-lookup"><span data-stu-id="d720f-130">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="d720f-131">枚举是一个标志枚举，你有超过32个标志，或者预计将来会有更多的标志。</span><span class="sxs-lookup"><span data-stu-id="d720f-131">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="d720f-132">基础类型需要不同于 <xref:System.Int32> ，与需要不同大小枚举的非托管代码的互操作性更简单。</span><span class="sxs-lookup"><span data-stu-id="d720f-132">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="d720f-133">较小的基础类型会显著节省空间。</span><span class="sxs-lookup"><span data-stu-id="d720f-133">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="d720f-134">如果希望枚举主要作为控制流的参数使用，则大小没有差别。</span><span class="sxs-lookup"><span data-stu-id="d720f-134">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="d720f-135">如果存在以下情况，大小节省可能会很大：</span><span class="sxs-lookup"><span data-stu-id="d720f-135">The size savings might be significant if:</span></span>

  - <span data-ttu-id="d720f-136">希望枚举在非常频繁实例化的结构或类中用作字段。</span><span class="sxs-lookup"><span data-stu-id="d720f-136">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="d720f-137">您希望用户创建枚举实例的大型数组或集合。</span><span class="sxs-lookup"><span data-stu-id="d720f-137">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="d720f-138">需要序列化大量枚举实例。</span><span class="sxs-lookup"><span data-stu-id="d720f-138">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="d720f-139">对于内存中使用，请注意，托管对象始终是 `DWORD` 一致的，因此，你可以在一个实例中有效地使用多个枚举或其他小型结构将一个较小的枚举打包，以便进行差别，因为总实例大小始终会向上舍入为 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="d720f-139">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="d720f-140">✔️用名词或名词短语复数和简单枚举作为名词或名词短语来命名标志枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-140">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="d720f-141">❌不要直接扩展 <xref:System.Enum?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d720f-141">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="d720f-142"><xref:System.Enum?displayProperty=nameWithType>是 CLR 用来创建用户定义的枚举的特殊类型。</span><span class="sxs-lookup"><span data-stu-id="d720f-142"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="d720f-143">大多数编程语言都提供了一个编程元素，该元素可让你访问此功能。</span><span class="sxs-lookup"><span data-stu-id="d720f-143">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="d720f-144">例如，在 c # 中， `enum` 关键字用于定义枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-144">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="d720f-145">设计标志枚举</span><span class="sxs-lookup"><span data-stu-id="d720f-145">Designing Flag Enums</span></span>

<span data-ttu-id="d720f-146">✔️应用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 来标记枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-146">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="d720f-147">不要将此属性应用于简单枚举。</span><span class="sxs-lookup"><span data-stu-id="d720f-147">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="d720f-148">✔️对标志枚举值使用2的幂，以便可以使用按位 "或" 运算自由合并这些值。</span><span class="sxs-lookup"><span data-stu-id="d720f-148">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="d720f-149">✔️考虑为常用的标志组合提供特殊的枚举值。</span><span class="sxs-lookup"><span data-stu-id="d720f-149">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="d720f-150">按位运算是一个高级概念，对于简单任务，不应是必需的。</span><span class="sxs-lookup"><span data-stu-id="d720f-150">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="d720f-151"><xref:System.IO.FileAccess.ReadWrite>这是一个特殊值的示例。</span><span class="sxs-lookup"><span data-stu-id="d720f-151"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="d720f-152">❌避免创建标志枚举，其中某些值的组合无效。</span><span class="sxs-lookup"><span data-stu-id="d720f-152">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="d720f-153">❌避免使用值为零的标记枚举值，除非该值表示 "所有标志均已清除" 并正确命名，如下一个准则所述。</span><span class="sxs-lookup"><span data-stu-id="d720f-153">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="d720f-154">✔️ DO name 标记枚举的零值 `None` 。</span><span class="sxs-lookup"><span data-stu-id="d720f-154">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="d720f-155">对于标志枚举，值始终为 "清除所有标志"。</span><span class="sxs-lookup"><span data-stu-id="d720f-155">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="d720f-156">向枚举添加值</span><span class="sxs-lookup"><span data-stu-id="d720f-156">Adding Value to Enums</span></span>

<span data-ttu-id="d720f-157">很常见的情况是，在已交付枚举后，需要向其添加值。</span><span class="sxs-lookup"><span data-stu-id="d720f-157">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="d720f-158">在从现有 API 返回新添加的值时存在潜在的应用程序兼容性问题，因为编写不当的应用程序可能无法正确处理新值。</span><span class="sxs-lookup"><span data-stu-id="d720f-158">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="d720f-159">✔️考虑向枚举添加值，而不考虑较小的兼容性风险。</span><span class="sxs-lookup"><span data-stu-id="d720f-159">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="d720f-160">如果对枚举的添加操作导致应用程序不兼容，请考虑添加一个新的 API，该 API 将返回新的和旧的值，并弃用旧的 API，该 API 应继续只返回旧值。</span><span class="sxs-lookup"><span data-stu-id="d720f-160">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="d720f-161">这将确保现有的应用程序保持兼容。</span><span class="sxs-lookup"><span data-stu-id="d720f-161">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="d720f-162">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="d720f-162">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="d720f-163">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="d720f-163">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d720f-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d720f-164">See also</span></span>

- [<span data-ttu-id="d720f-165">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="d720f-165">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="d720f-166">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="d720f-166">Framework Design Guidelines</span></span>](index.md)
