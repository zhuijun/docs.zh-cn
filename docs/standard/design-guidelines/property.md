---
title: 属性设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: c49b42ab369ace582c76d7f326da309415e8c45b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291937"
---
# <a name="property-design"></a><span data-ttu-id="9128e-102">属性设计</span><span class="sxs-lookup"><span data-stu-id="9128e-102">Property Design</span></span>
<span data-ttu-id="9128e-103">尽管从技术上讲，属性非常类似于方法，但它们的使用方案非常不同。</span><span class="sxs-lookup"><span data-stu-id="9128e-103">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="9128e-104">它们应显示为智能字段。</span><span class="sxs-lookup"><span data-stu-id="9128e-104">They should be seen as smart fields.</span></span> <span data-ttu-id="9128e-105">它们具有字段的调用语法以及方法的灵活性。</span><span class="sxs-lookup"><span data-stu-id="9128e-105">They have the calling syntax of fields, and the flexibility of methods.</span></span>

 <span data-ttu-id="9128e-106">如果调用方不能更改属性的值，✔️确实要创建只获得属性。</span><span class="sxs-lookup"><span data-stu-id="9128e-106">✔️ DO create get-only properties if the caller should not be able to change the value of the property.</span></span>

 <span data-ttu-id="9128e-107">请记住，如果属性的类型是可变的引用类型，则即使属性是只读的，也可以更改属性值。</span><span class="sxs-lookup"><span data-stu-id="9128e-107">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>

 <span data-ttu-id="9128e-108">❌不要提供仅限集的属性或属性，其中 setter 具有比 getter 更广泛的可访问性。</span><span class="sxs-lookup"><span data-stu-id="9128e-108">❌ DO NOT provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>

 <span data-ttu-id="9128e-109">例如，不要将属性与公共资源库和受保护的 getter 一起使用。</span><span class="sxs-lookup"><span data-stu-id="9128e-109">For example, do not use properties with a public setter and a protected getter.</span></span>

 <span data-ttu-id="9128e-110">如果无法提供属性 getter，请改为将该功能作为方法实现。</span><span class="sxs-lookup"><span data-stu-id="9128e-110">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="9128e-111">考虑使用启动方法名称 `Set` ，并遵循您命名的属性。</span><span class="sxs-lookup"><span data-stu-id="9128e-111">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="9128e-112">例如， <xref:System.AppDomain> 有一个名为的方法， `SetCachePath` 而不是只调用一个设置的属性 `CachePath` 。</span><span class="sxs-lookup"><span data-stu-id="9128e-112">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>

 <span data-ttu-id="9128e-113">✔️为所有属性提供合理的默认值，确保默认值不会导致安全漏洞或极低效的代码。</span><span class="sxs-lookup"><span data-stu-id="9128e-113">✔️ DO provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>

 <span data-ttu-id="9128e-114">✔️允许以任意顺序设置属性，即使这样会导致对象的临时无效状态。</span><span class="sxs-lookup"><span data-stu-id="9128e-114">✔️ DO allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>

 <span data-ttu-id="9128e-115">将两个或更多属性关联到一个点，在该点上，对于同一对象的其他属性的值，可能会有一个属性的值无效。</span><span class="sxs-lookup"><span data-stu-id="9128e-115">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="9128e-116">在这种情况下，不应延迟由无效状态引发的异常，直到对象实际使用相关属性。</span><span class="sxs-lookup"><span data-stu-id="9128e-116">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>

 <span data-ttu-id="9128e-117">如果属性 setter 引发异常，✔️保留以前的值。</span><span class="sxs-lookup"><span data-stu-id="9128e-117">✔️ DO preserve the previous value if a property setter throws an exception.</span></span>

 <span data-ttu-id="9128e-118">❌避免从属性 getter 引发异常。</span><span class="sxs-lookup"><span data-stu-id="9128e-118">❌ AVOID throwing exceptions from property getters.</span></span>

 <span data-ttu-id="9128e-119">属性 getter 应为简单操作，不应具有任何前置条件。</span><span class="sxs-lookup"><span data-stu-id="9128e-119">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="9128e-120">如果 getter 可能引发异常，则可能会将其重新设计为方法。</span><span class="sxs-lookup"><span data-stu-id="9128e-120">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="9128e-121">请注意，此规则不适用于索引器，在这种情况下，我们预期会在验证参数时引发异常。</span><span class="sxs-lookup"><span data-stu-id="9128e-121">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>

### <a name="indexed-property-design"></a><span data-ttu-id="9128e-122">索引属性设计</span><span class="sxs-lookup"><span data-stu-id="9128e-122">Indexed Property Design</span></span>
 <span data-ttu-id="9128e-123">索引属性是一个特殊属性，它可以具有参数，并可使用类似于数组索引的特殊语法进行调用。</span><span class="sxs-lookup"><span data-stu-id="9128e-123">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>

 <span data-ttu-id="9128e-124">索引属性通常称为索引器。</span><span class="sxs-lookup"><span data-stu-id="9128e-124">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="9128e-125">索引器仅应在提供对逻辑集合中的项的访问的 Api 中使用。</span><span class="sxs-lookup"><span data-stu-id="9128e-125">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="9128e-126">例如，字符串是字符的集合，并添加了的索引器 <xref:System.String?displayProperty=nameWithType> 以访问其字符。</span><span class="sxs-lookup"><span data-stu-id="9128e-126">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>

 <span data-ttu-id="9128e-127">✔️考虑使用索引器来提供对存储在内部数组中的数据的访问。</span><span class="sxs-lookup"><span data-stu-id="9128e-127">✔️ CONSIDER using indexers to provide access to data stored in an internal array.</span></span>

 <span data-ttu-id="9128e-128">✔️考虑为表示项集合的类型提供索引器。</span><span class="sxs-lookup"><span data-stu-id="9128e-128">✔️ CONSIDER providing indexers on types representing collections of items.</span></span>

 <span data-ttu-id="9128e-129">❌避免使用具有多个参数的索引属性。</span><span class="sxs-lookup"><span data-stu-id="9128e-129">❌ AVOID using indexed properties with more than one parameter.</span></span>

 <span data-ttu-id="9128e-130">如果设计需要多个参数，请重新考虑属性是否确实表示逻辑集合的访问器。</span><span class="sxs-lookup"><span data-stu-id="9128e-130">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="9128e-131">如果不是，请改用方法。</span><span class="sxs-lookup"><span data-stu-id="9128e-131">If it does not, use methods instead.</span></span> <span data-ttu-id="9128e-132">请考虑以或开头的方法名称 `Get` `Set` 。</span><span class="sxs-lookup"><span data-stu-id="9128e-132">Consider starting the method name with `Get` or `Set`.</span></span>

 <span data-ttu-id="9128e-133">❌避免使用除 <xref:System.Int32?displayProperty=nameWithType> 、 <xref:System.Int64?displayProperty=nameWithType> 、 <xref:System.String?displayProperty=nameWithType> 、 <xref:System.Object?displayProperty=nameWithType> 或枚举以外的参数类型的索引器。</span><span class="sxs-lookup"><span data-stu-id="9128e-133">❌ AVOID indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>

 <span data-ttu-id="9128e-134">如果设计需要其他类型的参数，请强重新评估 API 是否确实表示逻辑集合的访问器。</span><span class="sxs-lookup"><span data-stu-id="9128e-134">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="9128e-135">否则，请使用方法。</span><span class="sxs-lookup"><span data-stu-id="9128e-135">If it does not, use a method.</span></span> <span data-ttu-id="9128e-136">请考虑以或开头的方法名称 `Get` `Set` 。</span><span class="sxs-lookup"><span data-stu-id="9128e-136">Consider starting the method name with `Get` or `Set`.</span></span>

 <span data-ttu-id="9128e-137">✔️使用 `Item` 索引属性的名称，除非有明显更好的名称（例如，请参阅上的 <xref:System.String.Chars%2A> 属性 `System.String` ）。</span><span class="sxs-lookup"><span data-stu-id="9128e-137">✔️ DO use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>

 <span data-ttu-id="9128e-138">在 c # 中，索引器默认命名为 Item。</span><span class="sxs-lookup"><span data-stu-id="9128e-138">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="9128e-139"><xref:System.Runtime.CompilerServices.IndexerNameAttribute>可用于自定义此名称。</span><span class="sxs-lookup"><span data-stu-id="9128e-139">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>

 <span data-ttu-id="9128e-140">❌不要提供在语义上等效的索引器和方法。</span><span class="sxs-lookup"><span data-stu-id="9128e-140">❌ DO NOT provide both an indexer and methods that are semantically equivalent.</span></span>

 <span data-ttu-id="9128e-141">❌不要提供一个类型的多个重载索引器系列。</span><span class="sxs-lookup"><span data-stu-id="9128e-141">❌ DO NOT provide more than one family of overloaded indexers in one type.</span></span>

 <span data-ttu-id="9128e-142">这是由 c # 编译器强制执行的。</span><span class="sxs-lookup"><span data-stu-id="9128e-142">This is enforced by the C# compiler.</span></span>

 <span data-ttu-id="9128e-143">❌不要使用非默认的索引属性。</span><span class="sxs-lookup"><span data-stu-id="9128e-143">❌ DO NOT use nondefault indexed properties.</span></span>

 <span data-ttu-id="9128e-144">这是由 c # 编译器强制执行的。</span><span class="sxs-lookup"><span data-stu-id="9128e-144">This is enforced by the C# compiler.</span></span>

### <a name="property-change-notification-events"></a><span data-ttu-id="9128e-145">属性更改通知事件</span><span class="sxs-lookup"><span data-stu-id="9128e-145">Property Change Notification Events</span></span>
 <span data-ttu-id="9128e-146">有时，提供事件来向用户通知属性值的更改是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="9128e-146">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="9128e-147">例如， `System.Windows.Forms.Control` `TextChanged` 在其属性的值发生更改后引发事件 `Text` 。</span><span class="sxs-lookup"><span data-stu-id="9128e-147">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>

 <span data-ttu-id="9128e-148">✔️在修改高级 Api （通常是设计器组件）中的属性值时，请考虑引发更改通知事件。</span><span class="sxs-lookup"><span data-stu-id="9128e-148">✔️ CONSIDER raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>

 <span data-ttu-id="9128e-149">如果用户需要知道何时更改对象的属性，则该对象应该为属性引发更改通知事件。。</span><span class="sxs-lookup"><span data-stu-id="9128e-149">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>

 <span data-ttu-id="9128e-150">但是，对于低级别 Api （如基类型或集合），引发此类事件的开销不太大。</span><span class="sxs-lookup"><span data-stu-id="9128e-150">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="9128e-151">例如， <xref:System.Collections.Generic.List%601> 当向列表中添加新项并且 `Count` 属性发生更改时，将不会引发此类事件。</span><span class="sxs-lookup"><span data-stu-id="9128e-151">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>

 <span data-ttu-id="9128e-152">✔️考虑当属性的值通过外部强制更改时引发更改通知事件。</span><span class="sxs-lookup"><span data-stu-id="9128e-152">✔️ CONSIDER raising change notification events when the value of a property changes via external forces.</span></span>

 <span data-ttu-id="9128e-153">如果某个属性值通过某个外部强制（通过在对象上调用方法之外的方式）更改，则引发事件向开发人员指示值正在更改并且已更改。</span><span class="sxs-lookup"><span data-stu-id="9128e-153">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="9128e-154">一个很好的示例是 `Text` 文本框控件的属性。</span><span class="sxs-lookup"><span data-stu-id="9128e-154">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="9128e-155">当用户在中键入文本时 `TextBox` ，属性值将自动更改。</span><span class="sxs-lookup"><span data-stu-id="9128e-155">When the user types text in a `TextBox`, the property value automatically changes.</span></span>

 <span data-ttu-id="9128e-156">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="9128e-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9128e-157">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="9128e-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9128e-158">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9128e-158">See also</span></span>

- [<span data-ttu-id="9128e-159">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="9128e-159">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="9128e-160">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="9128e-160">Framework Design Guidelines</span></span>](index.md)
