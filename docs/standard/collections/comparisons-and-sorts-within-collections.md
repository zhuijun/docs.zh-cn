---
title: 集合内的比较和排序
ms.date: 04/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
ms.openlocfilehash: 8e4530063f14211688e5ef2d2ec4ed7e4834cdf1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212962"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="9fd2a-102">集合内的比较和排序</span><span class="sxs-lookup"><span data-stu-id="9fd2a-102">Comparisons and sorts within collections</span></span>

<span data-ttu-id="9fd2a-103"><xref:System.Collections> 类在管理集合所涉及的几乎所有进程中执行比较，无论是搜索待删除的元素或返回键值对的值。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>

<span data-ttu-id="9fd2a-104">集合通常使用相等比较器和/或排序比较器。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="9fd2a-105">有两个构造用于比较。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-105">Two constructs are used for comparisons.</span></span>

<a name="BKMK_Checkingforequality"></a>
## <a name="check-for-equality"></a><span data-ttu-id="9fd2a-106">检查是否相等</span><span class="sxs-lookup"><span data-stu-id="9fd2a-106">Check for equality</span></span>

<span data-ttu-id="9fd2a-107">诸如 `Contains`、 <xref:System.Collections.IList.IndexOf%2A>、 <xref:System.Collections.Generic.List%601.LastIndexOf%2A>和 `Remove` 的方法将相等比较器用于集合元素。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="9fd2a-108">如果集合是泛型的，则按照以下原则比较项是否相等：</span><span class="sxs-lookup"><span data-stu-id="9fd2a-108">If the collection is generic, then items are compared for equality according to the following guidelines:</span></span>

- <span data-ttu-id="9fd2a-109">如果类型 T 实现 <xref:System.IEquatable%601> 泛型接口，则相等比较器是该接口的 <xref:System.IEquatable%601.Equals%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>

- <span data-ttu-id="9fd2a-110">如果类型 T 未实现 <xref:System.IEquatable%601>，则使用 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>

<span data-ttu-id="9fd2a-111">此外，字典集合的某些构造函数重载接受 <xref:System.Collections.Generic.IEqualityComparer%601> 实现，用于比较键是否相等。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-111">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="9fd2a-112">有关示例，请参见 <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> 构造函数。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> constructor.</span></span>

<a name="BKMK_Determiningsortorder"></a>
## <a name="determine-sort-order"></a><span data-ttu-id="9fd2a-113">确定排序顺序</span><span class="sxs-lookup"><span data-stu-id="9fd2a-113">Determine sort order</span></span>

<span data-ttu-id="9fd2a-114">`BinarySearch` 和 `Sort` 等方法将排序比较器用于集合元素。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="9fd2a-115">可在集合的元素间进行比较，或在元素或指定值之间进行比较。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="9fd2a-116">对于比较对象，有 `default comparer` 和 `explicit comparer`的概念。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>

<span data-ttu-id="9fd2a-117">默认比较器依赖至少一个正在被比较的对象来实现 **IComparable** 接口。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="9fd2a-118">在用作列表集合的值或字典集合的键的所有类上实现 **IComparable** 不失为一个好办法。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="9fd2a-119">对泛型集合而言，等同性比较是根据以下内容确定的：</span><span class="sxs-lookup"><span data-stu-id="9fd2a-119">For a generic collection, equality comparison is determined according to the following:</span></span>

- <span data-ttu-id="9fd2a-120">如果类型 T 实现 <xref:System.IComparable%601?displayProperty=nameWithType> 泛型接口，则默认比较器是该接口的 <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>

- <span data-ttu-id="9fd2a-121">如果类型 T 实现非泛型 <xref:System.IComparable?displayProperty=nameWithType> 接口，则默认比较器是该接口的 <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>

- <span data-ttu-id="9fd2a-122">如果类型 T 未实现任何接口，则没有默认比较器，必须显式提供一个比较器或比较委托。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-122">If type T doesn't implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>

<span data-ttu-id="9fd2a-123">为了提供显式比较，某些方法接受 **IComparer** 实现作为参数。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="9fd2a-124">例如， <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 方法接受 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 实现。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>

<span data-ttu-id="9fd2a-125">系统当前的区域性设置可影响集合中的比较和排序。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="9fd2a-126">默认情况下， **Collections** 类中的比较和排序是区分区域性的。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="9fd2a-127">若要忽略区域性设置并因此获得一致的比较和排序结果，请使用具有接受 <xref:System.Globalization.CultureInfo.InvariantCulture%2A> 的成员重载的 <xref:System.Globalization.CultureInfo>。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="9fd2a-128">有关详细信息，请参阅 “[在集合中执行不区分区域性的字符串操作](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)” 和 “[在数组中执行不区分区域性的字符串操作](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)”。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>

<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a><span data-ttu-id="9fd2a-129">等同性和排序示例</span><span class="sxs-lookup"><span data-stu-id="9fd2a-129">Equality and sort example</span></span>

<span data-ttu-id="9fd2a-130">以下代码展示了 <xref:System.IEquatable%601> 和 <xref:System.IComparable%601> 在简单的业务对象上的实现。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="9fd2a-131">此外，如果对象被存储在列表中并已排序，那么你会发现调用 <xref:System.Collections.Generic.List%601.Sort> 方法会导致 `Part` 类型使用默认比较器，并通过使用匿名方法实现 <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="9fd2a-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>

[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
[!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9fd2a-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="9fd2a-132">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
