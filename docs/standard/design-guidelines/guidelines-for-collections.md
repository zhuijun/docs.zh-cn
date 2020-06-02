---
title: 集合准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: cc853be2310cf72c4eb559f625c6a37a44ed7db8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276044"
---
# <a name="guidelines-for-collections"></a><span data-ttu-id="6cee8-102">集合准则</span><span class="sxs-lookup"><span data-stu-id="6cee8-102">Guidelines for Collections</span></span>
<span data-ttu-id="6cee8-103">专门设计为操作一组具有某种常见特征的对象的任何类型都可以被视为集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-103">Any type designed specifically to manipulate a group of objects having some common characteristic can be considered a collection.</span></span> <span data-ttu-id="6cee8-104">对于这种类型的实现，几乎总是适当 <xref:System.Collections.IEnumerable> 的 <xref:System.Collections.Generic.IEnumerable%601> ，因此在本部分中，我们只考虑实现其中一个或两个接口都为集合的类型。</span><span class="sxs-lookup"><span data-stu-id="6cee8-104">It is almost always appropriate for such types to implement <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601>, so in this section we only consider types implementing one or both of those interfaces to be collections.</span></span>

 <span data-ttu-id="6cee8-105">❌不要在公共 Api 中使用弱类型集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-105">❌ DO NOT use weakly typed collections in public APIs.</span></span>

 <span data-ttu-id="6cee8-106">表示集合项的所有返回值和参数的类型应为确切项类型，而不是其任何基类型（这仅适用于集合的公共成员）。</span><span class="sxs-lookup"><span data-stu-id="6cee8-106">The type of all return values and parameters representing collection items should be the exact item type, not any of its base types (this applies only to public members of the collection).</span></span>

 <span data-ttu-id="6cee8-107">❌不要 <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.List%601> 在公共 api 中使用或。</span><span class="sxs-lookup"><span data-stu-id="6cee8-107">❌ DO NOT use <xref:System.Collections.ArrayList> or <xref:System.Collections.Generic.List%601> in public APIs.</span></span>

 <span data-ttu-id="6cee8-108">这些类型是设计用于内部实现的数据结构，而不是公共 Api。</span><span class="sxs-lookup"><span data-stu-id="6cee8-108">These types are data structures designed to be used in internal implementation, not in public APIs.</span></span> <span data-ttu-id="6cee8-109">`List<T>`针对性能和功能进行了优化，但代价是 cleanness Api 和灵活性。</span><span class="sxs-lookup"><span data-stu-id="6cee8-109">`List<T>` is optimized for performance and power at the cost of cleanness of the APIs and flexibility.</span></span> <span data-ttu-id="6cee8-110">例如，如果你返回 `List<T>` ，则在客户端代码修改集合时，你将不会收到通知。</span><span class="sxs-lookup"><span data-stu-id="6cee8-110">For example, if you return `List<T>`, you will not ever be able to receive notifications when client code modifies the collection.</span></span> <span data-ttu-id="6cee8-111">此外，还 `List<T>` 公开了许多成员（例如 <xref:System.Collections.Generic.List%601.BinarySearch%2A> ）在许多情况下都不起作用或适用的成员。</span><span class="sxs-lookup"><span data-stu-id="6cee8-111">Also, `List<T>` exposes many members, such as <xref:System.Collections.Generic.List%601.BinarySearch%2A>, that are not useful or applicable in many scenarios.</span></span> <span data-ttu-id="6cee8-112">以下两节介绍专用于在公共 Api 中使用的类型（抽象）。</span><span class="sxs-lookup"><span data-stu-id="6cee8-112">The following two sections describe types (abstractions) designed specifically for use in public APIs.</span></span>

 <span data-ttu-id="6cee8-113">❌不要 `Hashtable` `Dictionary<TKey,TValue>` 在公共 api 中使用或。</span><span class="sxs-lookup"><span data-stu-id="6cee8-113">❌ DO NOT use `Hashtable` or `Dictionary<TKey,TValue>` in public APIs.</span></span>

 <span data-ttu-id="6cee8-114">这些类型是设计用于内部实现的数据结构。</span><span class="sxs-lookup"><span data-stu-id="6cee8-114">These types are data structures designed to be used in internal implementation.</span></span> <span data-ttu-id="6cee8-115">公共 Api 应使用 <xref:System.Collections.IDictionary> 、 `IDictionary <TKey, TValue>` 或实现一个或两个接口的自定义类型。</span><span class="sxs-lookup"><span data-stu-id="6cee8-115">Public APIs should use <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, or a custom type implementing one or both of the interfaces.</span></span>

 <span data-ttu-id="6cee8-116">❌<xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.IEnumerator> 除了作为方法的返回类型之外，请不要使用、或任何其他实现这些接口的类型 `GetEnumerator` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-116">❌ DO NOT use <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, or any other type that implements either of these interfaces, except as the return type of a `GetEnumerator` method.</span></span>

 <span data-ttu-id="6cee8-117">从以外的方法返回枚举器的类型 `GetEnumerator` 不能与 `foreach` 语句一起使用。</span><span class="sxs-lookup"><span data-stu-id="6cee8-117">Types returning enumerators from methods other than `GetEnumerator` cannot be used with the `foreach` statement.</span></span>

 <span data-ttu-id="6cee8-118">❌不要 `IEnumerator<T>` `IEnumerable<T>` 在同一类型上实现和。</span><span class="sxs-lookup"><span data-stu-id="6cee8-118">❌ DO NOT implement both `IEnumerator<T>` and `IEnumerable<T>` on the same type.</span></span> <span data-ttu-id="6cee8-119">这同样适用于非泛型接口 `IEnumerator` 和 `IEnumerable` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-119">The same applies to the nongeneric interfaces `IEnumerator` and `IEnumerable`.</span></span>

## <a name="collection-parameters"></a><span data-ttu-id="6cee8-120">集合参数</span><span class="sxs-lookup"><span data-stu-id="6cee8-120">Collection Parameters</span></span>
 <span data-ttu-id="6cee8-121">✔️确实使用最小专用类型作为参数类型。</span><span class="sxs-lookup"><span data-stu-id="6cee8-121">✔️ DO use the least-specialized type possible as a parameter type.</span></span> <span data-ttu-id="6cee8-122">将集合作为参数的大多数成员使用 `IEnumerable<T>` 接口。</span><span class="sxs-lookup"><span data-stu-id="6cee8-122">Most members taking collections as parameters use the `IEnumerable<T>` interface.</span></span>

 <span data-ttu-id="6cee8-123">❌<xref:System.Collections.Generic.ICollection%601> <xref:System.Collections.ICollection> 只需使用或作为参数即可访问 `Count` 属性。</span><span class="sxs-lookup"><span data-stu-id="6cee8-123">❌ AVOID using <xref:System.Collections.Generic.ICollection%601> or <xref:System.Collections.ICollection> as a parameter just to access the `Count` property.</span></span>

 <span data-ttu-id="6cee8-124">相反，请考虑使用 `IEnumerable<T>` 或 `IEnumerable` 并动态检查该对象是否实现 `ICollection<T>` 或 `ICollection` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-124">Instead, consider using `IEnumerable<T>` or `IEnumerable` and dynamically checking whether the object implements `ICollection<T>` or `ICollection`.</span></span>

## <a name="collection-properties-and-return-values"></a><span data-ttu-id="6cee8-125">集合属性和返回值</span><span class="sxs-lookup"><span data-stu-id="6cee8-125">Collection Properties and Return Values</span></span>
 <span data-ttu-id="6cee8-126">❌不要提供可设置的集合属性。</span><span class="sxs-lookup"><span data-stu-id="6cee8-126">❌ DO NOT provide settable collection properties.</span></span>

 <span data-ttu-id="6cee8-127">用户可以通过先清除集合，然后添加新内容来替换集合的内容。</span><span class="sxs-lookup"><span data-stu-id="6cee8-127">Users can replace the contents of the collection by clearing the collection first and then adding the new contents.</span></span> <span data-ttu-id="6cee8-128">如果替换整个集合是一个常见方案，请考虑 `AddRange` 在集合上提供方法。</span><span class="sxs-lookup"><span data-stu-id="6cee8-128">If replacing the whole collection is a common scenario, consider providing the `AddRange` method on the collection.</span></span>

 <span data-ttu-id="6cee8-129">✔️ `Collection<T>` `Collection<T>` 对表示读/写集合的属性或返回值使用或的子类。</span><span class="sxs-lookup"><span data-stu-id="6cee8-129">✔️ DO use `Collection<T>` or a subclass of `Collection<T>` for properties or return values representing read/write collections.</span></span>

 <span data-ttu-id="6cee8-130">如果不 `Collection<T>` 满足某些要求（例如，集合不得实现 <xref:System.Collections.IList> ），请通过实现、或来使用自定义集合 `IEnumerable<T>` `ICollection<T>` <xref:System.Collections.Generic.IList%601> 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-130">If `Collection<T>` does not meet some requirement (e.g., the collection must not implement <xref:System.Collections.IList>), use a custom collection by implementing `IEnumerable<T>`, `ICollection<T>`, or <xref:System.Collections.Generic.IList%601>.</span></span>

 <span data-ttu-id="6cee8-131">✔️使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 、的子类 `ReadOnlyCollection<T>` 或在极少数情况下 `IEnumerable<T>` 表示只读集合的属性或返回值。</span><span class="sxs-lookup"><span data-stu-id="6cee8-131">✔️ DO use <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, a subclass of `ReadOnlyCollection<T>`, or in rare cases `IEnumerable<T>` for properties or return values representing read-only collections.</span></span>

 <span data-ttu-id="6cee8-132">通常情况下，首选 `ReadOnlyCollection<T>` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-132">In general, prefer `ReadOnlyCollection<T>`.</span></span> <span data-ttu-id="6cee8-133">如果它不满足某些要求（例如，集合不得实现 `IList` ），则通过实现、或来使用自定义集合 `IEnumerable<T>` `ICollection<T>` `IList<T>` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-133">If it does not meet some requirement (e.g., the collection must not implement `IList`), use a custom collection by implementing `IEnumerable<T>`, `ICollection<T>`, or `IList<T>`.</span></span> <span data-ttu-id="6cee8-134">如果实现自定义的只读集合，则实现 `ICollection<T>.IsReadOnly` 以返回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-134">If you do implement a custom read-only collection, implement `ICollection<T>.IsReadOnly` to return `true`.</span></span>

 <span data-ttu-id="6cee8-135">如果你确定要支持的唯一方案是只进迭代，只需使用即可 `IEnumerable<T>` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-135">In cases where you are sure that the only scenario you will ever want to support is forward-only iteration, you can simply use `IEnumerable<T>`.</span></span>

 <span data-ttu-id="6cee8-136">✔️考虑使用泛型基集合的子类，而不是直接使用集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-136">✔️ CONSIDER using subclasses of generic base collections instead of using the collections directly.</span></span>

 <span data-ttu-id="6cee8-137">这样，就可以更好地命名并添加基集合类型中不存在的帮助器成员。</span><span class="sxs-lookup"><span data-stu-id="6cee8-137">This allows for a better name and for adding helper members that are not present on the base collection types.</span></span> <span data-ttu-id="6cee8-138">这尤其适用于高级 Api。</span><span class="sxs-lookup"><span data-stu-id="6cee8-138">This is especially applicable to high-level APIs.</span></span>

 <span data-ttu-id="6cee8-139">✔️考虑 `Collection<T>` `ReadOnlyCollection<T>` 从非常常用的方法和属性返回或的子类。</span><span class="sxs-lookup"><span data-stu-id="6cee8-139">✔️ CONSIDER returning a subclass of `Collection<T>` or `ReadOnlyCollection<T>` from very commonly used methods and properties.</span></span>

 <span data-ttu-id="6cee8-140">这将使你可以在将来添加帮助器方法或更改集合实现。</span><span class="sxs-lookup"><span data-stu-id="6cee8-140">This will make it possible for you to add helper methods or change the collection implementation in the future.</span></span>

 <span data-ttu-id="6cee8-141">✔️如果集合中存储的项具有唯一键（名称、Id 等），请考虑使用键控集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-141">✔️ CONSIDER using a keyed collection if the items stored in the collection have unique keys (names, IDs, etc.).</span></span> <span data-ttu-id="6cee8-142">键控集合是可以由整数和键编制索引的集合，通常是通过从继承来实现的 `KeyedCollection<TKey,TItem>` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-142">Keyed collections are collections that can be indexed by both an integer and a key and are usually implemented by inheriting from `KeyedCollection<TKey,TItem>`.</span></span>

 <span data-ttu-id="6cee8-143">键控集合通常具有较大的内存占用量，因此，如果内存开销超过具有密钥的优点，则不应使用。</span><span class="sxs-lookup"><span data-stu-id="6cee8-143">Keyed collections usually have larger memory footprints and should not be used if the memory overhead outweighs the benefits of having the keys.</span></span>

 <span data-ttu-id="6cee8-144">❌不要从集合属性或返回集合的方法中返回 null 值。</span><span class="sxs-lookup"><span data-stu-id="6cee8-144">❌ DO NOT return null values from collection properties or from methods returning collections.</span></span> <span data-ttu-id="6cee8-145">改为返回空集合或空数组。</span><span class="sxs-lookup"><span data-stu-id="6cee8-145">Return an empty collection or an empty array instead.</span></span>

 <span data-ttu-id="6cee8-146">一般规则是应将 null 和空（0项）集合或数组视为相同。</span><span class="sxs-lookup"><span data-stu-id="6cee8-146">The general rule is that null and empty (0 item) collections or arrays should be treated the same.</span></span>

### <a name="snapshots-versus-live-collections"></a><span data-ttu-id="6cee8-147">快照与活动集合</span><span class="sxs-lookup"><span data-stu-id="6cee8-147">Snapshots Versus Live Collections</span></span>
 <span data-ttu-id="6cee8-148">表示某个时间点的状态的集合称为快照集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-148">Collections representing a state at some point in time are called snapshot collections.</span></span> <span data-ttu-id="6cee8-149">例如，包含从数据库查询返回的行的集合将为快照。</span><span class="sxs-lookup"><span data-stu-id="6cee8-149">For example, a collection containing rows returned from a database query would be a snapshot.</span></span> <span data-ttu-id="6cee8-150">始终表示当前状态的集合称为活动集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-150">Collections that always represent the current state are called live collections.</span></span> <span data-ttu-id="6cee8-151">例如，项的集合 `ComboBox` 为活动集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-151">For example, a collection of `ComboBox` items is a live collection.</span></span>

 <span data-ttu-id="6cee8-152">❌不要从属性返回快照集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-152">❌ DO NOT return snapshot collections from properties.</span></span> <span data-ttu-id="6cee8-153">属性应返回活动集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-153">Properties should return live collections.</span></span>

 <span data-ttu-id="6cee8-154">属性 getter 应为非常轻量的操作。</span><span class="sxs-lookup"><span data-stu-id="6cee8-154">Property getters should be very lightweight operations.</span></span> <span data-ttu-id="6cee8-155">返回快照需要在 O （n）操作中创建内部集合的副本。</span><span class="sxs-lookup"><span data-stu-id="6cee8-155">Returning a snapshot requires creating a copy of an internal collection in an O(n) operation.</span></span>

 <span data-ttu-id="6cee8-156">✔️使用快照集合或活 `IEnumerable<T>` （或其子类型）来表示易失性的集合（即，在未显式修改集合的情况下可以更改）。</span><span class="sxs-lookup"><span data-stu-id="6cee8-156">✔️ DO use either a snapshot collection or a live `IEnumerable<T>` (or its subtype) to represent collections that are volatile (i.e., that can change without explicitly modifying the collection).</span></span>

 <span data-ttu-id="6cee8-157">通常，表示共享资源（例如目录中的文件）的所有集合都是可变的。</span><span class="sxs-lookup"><span data-stu-id="6cee8-157">In general, all collections representing a shared resource (e.g., files in a directory) are volatile.</span></span> <span data-ttu-id="6cee8-158">此类集合非常困难，或者无法实现为活动集合，除非实现只是一个只进枚举器。</span><span class="sxs-lookup"><span data-stu-id="6cee8-158">Such collections are very difficult or impossible to implement as live collections unless the implementation is simply a forward-only enumerator.</span></span>

## <a name="choosing-between-arrays-and-collections"></a><span data-ttu-id="6cee8-159">在数组和集合之间进行选择</span><span class="sxs-lookup"><span data-stu-id="6cee8-159">Choosing Between Arrays and Collections</span></span>
 <span data-ttu-id="6cee8-160">✔️是否比数组更倾向于集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-160">✔️ DO prefer collections over arrays.</span></span>

 <span data-ttu-id="6cee8-161">集合可以更好地控制内容、随时间推移而变化，并且更易于使用。</span><span class="sxs-lookup"><span data-stu-id="6cee8-161">Collections provide more control over contents, can evolve over time, and are more usable.</span></span> <span data-ttu-id="6cee8-162">此外，不建议对只读方案使用数组，因为克隆数组的成本是不高的。</span><span class="sxs-lookup"><span data-stu-id="6cee8-162">In addition, using arrays for read-only scenarios is discouraged because the cost of cloning the array is prohibitive.</span></span> <span data-ttu-id="6cee8-163">可用性研究表明，某些开发人员更喜欢使用基于集合的 Api。</span><span class="sxs-lookup"><span data-stu-id="6cee8-163">Usability studies have shown that some developers feel more comfortable using collection-based APIs.</span></span>

 <span data-ttu-id="6cee8-164">但是，如果要开发低级别 Api，则最好使用数组进行读写方案。</span><span class="sxs-lookup"><span data-stu-id="6cee8-164">However, if you are developing low-level APIs, it might be better to use arrays for read-write scenarios.</span></span> <span data-ttu-id="6cee8-165">数组的内存占用量较小，有助于减少工作集，并且对数组中的元素的访问速度更快，因为它已由运行时进行优化。</span><span class="sxs-lookup"><span data-stu-id="6cee8-165">Arrays have a smaller memory footprint, which helps reduce the working set, and access to elements in an array is faster because it is optimized by the runtime.</span></span>

 <span data-ttu-id="6cee8-166">✔️考虑在低级别 Api 中使用数组，以最大程度地减少内存占用和最大化性能。</span><span class="sxs-lookup"><span data-stu-id="6cee8-166">✔️ CONSIDER using arrays in low-level APIs to minimize memory consumption and maximize performance.</span></span>

 <span data-ttu-id="6cee8-167">✔️使用字节数组而不是字节集合。</span><span class="sxs-lookup"><span data-stu-id="6cee8-167">✔️ DO use byte arrays instead of collections of bytes.</span></span>

 <span data-ttu-id="6cee8-168">❌如果属性在每次调用属性 getter 时必须返回一个新数组（例如，内部数组的副本），请不要使用属性的数组。</span><span class="sxs-lookup"><span data-stu-id="6cee8-168">❌ DO NOT use arrays for properties if the property would have to return a new array (e.g., a copy of an internal array) every time the property getter is called.</span></span>

## <a name="implementing-custom-collections"></a><span data-ttu-id="6cee8-169">实现自定义集合</span><span class="sxs-lookup"><span data-stu-id="6cee8-169">Implementing Custom Collections</span></span>
 <span data-ttu-id="6cee8-170">✔️考虑 `Collection<T>` `ReadOnlyCollection<T>` `KeyedCollection<TKey,TItem>` 在设计新集合时从、或继承。</span><span class="sxs-lookup"><span data-stu-id="6cee8-170">✔️ CONSIDER inheriting from `Collection<T>`, `ReadOnlyCollection<T>`, or `KeyedCollection<TKey,TItem>` when designing new collections.</span></span>

 <span data-ttu-id="6cee8-171">✔️ `IEnumerable<T>` 在设计新集合时实现。</span><span class="sxs-lookup"><span data-stu-id="6cee8-171">✔️ DO implement `IEnumerable<T>` when designing new collections.</span></span> <span data-ttu-id="6cee8-172">请考虑实现甚至 `ICollection<T>` `IList<T>` 有意义的地方。</span><span class="sxs-lookup"><span data-stu-id="6cee8-172">Consider implementing `ICollection<T>` or even `IList<T>` where it makes sense.</span></span>

 <span data-ttu-id="6cee8-173">实现此类自定义集合时，请尽可能地遵循和建立的 API 模式 `Collection<T>` `ReadOnlyCollection<T>` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-173">When implementing such custom collection, follow the API pattern established by `Collection<T>` and `ReadOnlyCollection<T>` as closely as possible.</span></span> <span data-ttu-id="6cee8-174">也就是说，显式实现相同的成员，将这些参数命名为这两个集合，将它们命名为，依此类推。</span><span class="sxs-lookup"><span data-stu-id="6cee8-174">That is, implement the same members explicitly, name the parameters like these two collections name them, and so on.</span></span>

 <span data-ttu-id="6cee8-175">✔️ `IList` `ICollection` 如果集合经常传递到采用这些接口作为输入的 api，则可考虑实现非泛型集合接口（和）。</span><span class="sxs-lookup"><span data-stu-id="6cee8-175">✔️ CONSIDER implementing nongeneric collection interfaces (`IList` and `ICollection`) if the collection will often be passed to APIs taking these interfaces as input.</span></span>

 <span data-ttu-id="6cee8-176">❌避免在具有与集合概念无关的复杂 Api 的类型上实现集合接口。</span><span class="sxs-lookup"><span data-stu-id="6cee8-176">❌ AVOID implementing collection interfaces on types with complex APIs unrelated to the concept of a collection.</span></span>

 <span data-ttu-id="6cee8-177">❌不要从非泛型基集合（如）继承 `CollectionBase` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-177">❌ DO NOT inherit from nongeneric base collections such as `CollectionBase`.</span></span> <span data-ttu-id="6cee8-178">请改用 `Collection<T>` 、 `ReadOnlyCollection<T>` 和 `KeyedCollection<TKey,TItem>` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-178">Use `Collection<T>`, `ReadOnlyCollection<T>`, and `KeyedCollection<TKey,TItem>` instead.</span></span>

### <a name="naming-custom-collections"></a><span data-ttu-id="6cee8-179">命名自定义集合</span><span class="sxs-lookup"><span data-stu-id="6cee8-179">Naming Custom Collections</span></span>
 <span data-ttu-id="6cee8-180">创建集合（实现的类型 `IEnumerable` ）主要有两个原因：（1）创建具有特定结构的操作的新数据结构，以及与现有数据结构（例如、、、）不同的性能特征， <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.LinkedList%601> <xref:System.Collections.Generic.Stack%601> 并创建专用集合来保存一组特定的项（例如， <xref:System.Collections.Specialized.StringCollection> ）。</span><span class="sxs-lookup"><span data-stu-id="6cee8-180">Collections (types that implement `IEnumerable`) are created mainly for two reasons: (1) to create a new data structure with structure-specific operations and often different performance characteristics than existing data structures (e.g.,  <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>), and (2) to create a specialized collection for holding a specific set of items (e.g.,  <xref:System.Collections.Specialized.StringCollection>).</span></span> <span data-ttu-id="6cee8-181">数据结构通常用于应用程序和库的内部实现。</span><span class="sxs-lookup"><span data-stu-id="6cee8-181">Data structures are most often used in the internal implementation of applications and libraries.</span></span> <span data-ttu-id="6cee8-182">专用集合主要是在 Api 中公开（作为属性和参数类型）。</span><span class="sxs-lookup"><span data-stu-id="6cee8-182">Specialized collections are mainly to be exposed in APIs (as property and parameter types).</span></span>

 <span data-ttu-id="6cee8-183">✔️在实现或的抽象名称中使用 "Dictionary" 后缀 `IDictionary` `IDictionary<TKey,TValue>` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-183">✔️ DO use the "Dictionary" suffix in names of abstractions implementing `IDictionary` or `IDictionary<TKey,TValue>`.</span></span>

 <span data-ttu-id="6cee8-184">✔️在实现的类型（或其任何子代）的名称中使用 "Collection" 后缀 `IEnumerable` ，并表示项列表。</span><span class="sxs-lookup"><span data-stu-id="6cee8-184">✔️ DO use the "Collection" suffix in names of types implementing `IEnumerable` (or any of its descendants) and representing a list of items.</span></span>

 <span data-ttu-id="6cee8-185">✔️为自定义数据结构使用适当的数据结构名称。</span><span class="sxs-lookup"><span data-stu-id="6cee8-185">✔️ DO use the appropriate data structure name for custom data structures.</span></span>

 <span data-ttu-id="6cee8-186">❌避免在集合抽象化的名称中使用任何后缀来暗指特定实现，如 "LinkedList" 或 "哈希表"。</span><span class="sxs-lookup"><span data-stu-id="6cee8-186">❌ AVOID using any suffixes implying particular implementation, such as "LinkedList" or "Hashtable," in names of collection abstractions.</span></span>

 <span data-ttu-id="6cee8-187">✔️考虑为集合名称加上项类型的名称。</span><span class="sxs-lookup"><span data-stu-id="6cee8-187">✔️ CONSIDER prefixing collection names with the name of the item type.</span></span> <span data-ttu-id="6cee8-188">例如，存储类型 `Address` （实现）的项的集合 `IEnumerable<Address>` 应命名为 `AddressCollection` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-188">For example, a collection storing items of type `Address` (implementing `IEnumerable<Address>`) should be named `AddressCollection`.</span></span> <span data-ttu-id="6cee8-189">如果项类型为接口，则可以省略项类型的 "I" 前缀。</span><span class="sxs-lookup"><span data-stu-id="6cee8-189">If the item type is an interface, the "I" prefix of the item type can be omitted.</span></span> <span data-ttu-id="6cee8-190">因此， <xref:System.IDisposable> 可以调用项的集合 `DisposableCollection` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-190">Thus, a collection of <xref:System.IDisposable> items can be called `DisposableCollection`.</span></span>

 <span data-ttu-id="6cee8-191">如果可在框架中添加或已存在相应的可写集合，则✔️考虑在只读集合的名称中使用 "ReadOnly" 前缀。</span><span class="sxs-lookup"><span data-stu-id="6cee8-191">✔️ CONSIDER using the "ReadOnly" prefix in names of read-only collections if a corresponding writeable collection might be added or already exists in the framework.</span></span>

 <span data-ttu-id="6cee8-192">例如，应调用字符串的只读集合 `ReadOnlyStringCollection` 。</span><span class="sxs-lookup"><span data-stu-id="6cee8-192">For example, a read-only collection of strings should be called `ReadOnlyStringCollection`.</span></span>

 <span data-ttu-id="6cee8-193">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="6cee8-193">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6cee8-194">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="6cee8-194">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6cee8-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6cee8-195">See also</span></span>

- [<span data-ttu-id="6cee8-196">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="6cee8-196">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="6cee8-197">使用准则</span><span class="sxs-lookup"><span data-stu-id="6cee8-197">Usage Guidelines</span></span>](usage-guidelines.md)
