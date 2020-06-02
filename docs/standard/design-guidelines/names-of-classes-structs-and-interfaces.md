---
title: 类、结构和接口的名称
description: 使用这些准则来命名类、结构和接口，作为设计扩展和交互 .NET 库的库的指南的一部分。
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: b9de9329cc8e1bfc47a46523c7119bb3b2c244d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290209"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="dd8de-103">类、结构和接口的名称</span><span class="sxs-lookup"><span data-stu-id="dd8de-103">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="dd8de-104">遵循的命名准则适用于常规类型命名。</span><span class="sxs-lookup"><span data-stu-id="dd8de-104">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="dd8de-105">✔️使用 PascalCasing 将类和结构命名为名词或名词短语。</span><span class="sxs-lookup"><span data-stu-id="dd8de-105">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="dd8de-106">这区分了方法中的类型名称，这些类型名为带有谓词短语。</span><span class="sxs-lookup"><span data-stu-id="dd8de-106">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="dd8de-107">✔️利用形容词短语或偶尔用名词或名词短语来命名接口。</span><span class="sxs-lookup"><span data-stu-id="dd8de-107">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="dd8de-108">应很少使用名词和名词短语，它们可能会指示该类型应为抽象类，而不是接口。</span><span class="sxs-lookup"><span data-stu-id="dd8de-108">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="dd8de-109">❌不要为类名称指定前缀（例如，"C"）。</span><span class="sxs-lookup"><span data-stu-id="dd8de-109">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="dd8de-110">✔️考虑用基类的名称结束派生类的名称。</span><span class="sxs-lookup"><span data-stu-id="dd8de-110">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="dd8de-111">这是非常可读的，并且清楚地说明了该关系。</span><span class="sxs-lookup"><span data-stu-id="dd8de-111">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="dd8de-112">代码中的一些示例是：，它是一种 `ArgumentOutOfRangeException` `Exception` ，而 `SerializableAttribute` 是一种类型的 `Attribute` 。</span><span class="sxs-lookup"><span data-stu-id="dd8de-112">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="dd8de-113">但是，在应用此准则时使用合理的判断非常重要;例如， `Button` 类是一种 `Control` 事件，但 `Control` 它的名称中没有显示。</span><span class="sxs-lookup"><span data-stu-id="dd8de-113">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="dd8de-114">✔️使用字母 I 来为接口名称加上前缀，以指示该类型是接口。</span><span class="sxs-lookup"><span data-stu-id="dd8de-114">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="dd8de-115">例如， `IComponent` （描述性名词）、 `ICustomAttributeProvider` （名词短语）和 `IPersistable` （形容词）是适当的接口名称。</span><span class="sxs-lookup"><span data-stu-id="dd8de-115">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="dd8de-116">对于其他类型名称，请避免缩写形式。</span><span class="sxs-lookup"><span data-stu-id="dd8de-116">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="dd8de-117">✔️确保在定义类接口对（其中类是接口的标准实现）时，接口名称上的 "I" 前缀仅有不同的名称。</span><span class="sxs-lookup"><span data-stu-id="dd8de-117">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="dd8de-118">泛型类型参数的名称</span><span class="sxs-lookup"><span data-stu-id="dd8de-118">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="dd8de-119">已将泛型添加到 .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="dd8de-119">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="dd8de-120">此功能引入了一种称为*类型参数*的新标识符。</span><span class="sxs-lookup"><span data-stu-id="dd8de-120">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="dd8de-121">✔️使用描述性名称命名泛型类型参数，除非单个字母名称完全一目了然，并且描述性名称不会添加值。</span><span class="sxs-lookup"><span data-stu-id="dd8de-121">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="dd8de-122">✔️考虑使用 `T` 作为具有一个单字母类型参数的类型的类型参数名称。</span><span class="sxs-lookup"><span data-stu-id="dd8de-122">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="dd8de-123">✔️在中为描述性类型参数名称加上前缀 `T` 。</span><span class="sxs-lookup"><span data-stu-id="dd8de-123">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="dd8de-124">✔️考虑，指示对参数名称中的类型参数施加的约束。</span><span class="sxs-lookup"><span data-stu-id="dd8de-124">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="dd8de-125">例如，可以调用约束为的参数 `ISession` `TSession` 。</span><span class="sxs-lookup"><span data-stu-id="dd8de-125">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="dd8de-126">常见类型的名称</span><span class="sxs-lookup"><span data-stu-id="dd8de-126">Names of Common Types</span></span>
 <span data-ttu-id="dd8de-127">当命名类型派生自或实现某些 .NET Framework 类型时，✔️按照下表中所述的指导原则进行操作。</span><span class="sxs-lookup"><span data-stu-id="dd8de-127">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="dd8de-128">基类型</span><span class="sxs-lookup"><span data-stu-id="dd8de-128">Base Type</span></span>|<span data-ttu-id="dd8de-129">派生/实现类型准则</span><span class="sxs-lookup"><span data-stu-id="dd8de-129">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="dd8de-130">✔️将后缀 "Attribute" 添加到自定义特性类的名称中。</span><span class="sxs-lookup"><span data-stu-id="dd8de-130">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="dd8de-131">✔️将后缀 "EventHandler" 添加到在事件中使用的委托的名称。</span><span class="sxs-lookup"><span data-stu-id="dd8de-131">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="dd8de-132">✔️将后缀 "Callback" 添加到作为事件处理程序使用的委托的名称。</span><span class="sxs-lookup"><span data-stu-id="dd8de-132">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="dd8de-133">❌不要将后缀 "Delegate" 添加到委托。</span><span class="sxs-lookup"><span data-stu-id="dd8de-133">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="dd8de-134">✔️添加后缀 "EventArgs"。</span><span class="sxs-lookup"><span data-stu-id="dd8de-134">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="dd8de-135">❌不要从此类派生;改为使用您的语言支持的关键字;例如，在 c # 中，使用 `enum` 关键字。</span><span class="sxs-lookup"><span data-stu-id="dd8de-135">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="dd8de-136">❌不要添加后缀 "Enum" 或 "标志"。</span><span class="sxs-lookup"><span data-stu-id="dd8de-136">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="dd8de-137">✔️添加后缀 "Exception"。</span><span class="sxs-lookup"><span data-stu-id="dd8de-137">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="dd8de-138">✔️添加后缀 "Dictionary"。</span><span class="sxs-lookup"><span data-stu-id="dd8de-138">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="dd8de-139">请注意， `IDictionary` 是一种特定类型的集合，但是此准则优先于下面的更常见的集合原则。</span><span class="sxs-lookup"><span data-stu-id="dd8de-139">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="dd8de-140">✔️添加后缀 "Collection"。</span><span class="sxs-lookup"><span data-stu-id="dd8de-140">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="dd8de-141">✔️添加后缀 "Stream"。</span><span class="sxs-lookup"><span data-stu-id="dd8de-141">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="dd8de-142">✔️添加后缀 "权限"。</span><span class="sxs-lookup"><span data-stu-id="dd8de-142">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="dd8de-143">命名枚举</span><span class="sxs-lookup"><span data-stu-id="dd8de-143">Naming Enumerations</span></span>
 <span data-ttu-id="dd8de-144">通常，枚举类型的名称（也称为枚举）应遵循标准类型命名规则（PascalCasing 等）。</span><span class="sxs-lookup"><span data-stu-id="dd8de-144">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="dd8de-145">不过，还有其他一些准则专门适用于枚举。</span><span class="sxs-lookup"><span data-stu-id="dd8de-145">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="dd8de-146">✔️为枚举使用单数类型名称，除非其值为位域。</span><span class="sxs-lookup"><span data-stu-id="dd8de-146">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="dd8de-147">✔️对将位域作为值的枚举使用复数类型名称，也称为标志枚举。</span><span class="sxs-lookup"><span data-stu-id="dd8de-147">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="dd8de-148">❌不要在枚举类型名称中使用 "Enum" 后缀。</span><span class="sxs-lookup"><span data-stu-id="dd8de-148">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="dd8de-149">❌不要在枚举类型名称中使用 "标记" 或 "标志" 后缀。</span><span class="sxs-lookup"><span data-stu-id="dd8de-149">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="dd8de-150">❌不要在枚举值名称（例如，"ad" 表示 ADO 枚举，"rtf"，用于丰富文本枚举等）上使用前缀。</span><span class="sxs-lookup"><span data-stu-id="dd8de-150">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="dd8de-151">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="dd8de-151">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="dd8de-152">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="dd8de-152">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="dd8de-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd8de-153">See also</span></span>

- [<span data-ttu-id="dd8de-154">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="dd8de-154">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="dd8de-155">命名准则</span><span class="sxs-lookup"><span data-stu-id="dd8de-155">Naming Guidelines</span></span>](naming-guidelines.md)
