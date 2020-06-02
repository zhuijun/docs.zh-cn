---
title: 异常和性能
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: a558547f0e6770e7e76ca31f760d6e2f55c712db
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289780"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="11650-102">异常和性能</span><span class="sxs-lookup"><span data-stu-id="11650-102">Exceptions and Performance</span></span>
<span data-ttu-id="11650-103">与异常相关的一个常见问题是，如果异常用于经常失败的代码，则实现的性能不可接受。</span><span class="sxs-lookup"><span data-stu-id="11650-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="11650-104">这是一个重要的考虑因素。</span><span class="sxs-lookup"><span data-stu-id="11650-104">This is a valid concern.</span></span> <span data-ttu-id="11650-105">当成员引发异常时，其性能可以是较慢的顺序。</span><span class="sxs-lookup"><span data-stu-id="11650-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="11650-106">但是，可以获得良好的性能，同时严格遵守禁止使用错误代码的异常指导原则。</span><span class="sxs-lookup"><span data-stu-id="11650-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="11650-107">本节中所述的两种模式提供了执行此操作的方法。</span><span class="sxs-lookup"><span data-stu-id="11650-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="11650-108">❌不要使用错误代码，原因是异常可能会对性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="11650-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="11650-109">若要提高性能，可以使用以下两节中所述的 Doer 模式或 Try 分析模式。</span><span class="sxs-lookup"><span data-stu-id="11650-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="11650-110">测试人员-Doer 模式</span><span class="sxs-lookup"><span data-stu-id="11650-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="11650-111">有时异常引发成员的性能可以通过将成员分为两个来改进。</span><span class="sxs-lookup"><span data-stu-id="11650-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="11650-112">让我们看看 <xref:System.Collections.Generic.ICollection%601.Add%2A> 接口的方法 <xref:System.Collections.Generic.ICollection%601> 。</span><span class="sxs-lookup"><span data-stu-id="11650-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="11650-113">如果集合是只读的，则该方法将 `Add` 引发。</span><span class="sxs-lookup"><span data-stu-id="11650-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="11650-114">这可能会导致方法调用经常失败的情况下出现性能问题。</span><span class="sxs-lookup"><span data-stu-id="11650-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="11650-115">缓解此问题的一种方法是在尝试添加值之前测试集合是否可写。</span><span class="sxs-lookup"><span data-stu-id="11650-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="11650-116">用于测试条件的成员（在我们的示例中为属性 `IsReadOnly` ）称为 "测试人员"。</span><span class="sxs-lookup"><span data-stu-id="11650-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="11650-117">用于执行可能引发的操作的成员（我们的 `Add` 示例中的方法）称为 doer。</span><span class="sxs-lookup"><span data-stu-id="11650-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="11650-118">✔️考虑在常见方案中可能会引发异常的成员的 Doer 模式，以避免与异常相关的性能问题。</span><span class="sxs-lookup"><span data-stu-id="11650-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="11650-119">Try-Parse 模式</span><span class="sxs-lookup"><span data-stu-id="11650-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="11650-120">对于性能非常敏感的 Api，应使用上一节中所述的更快的模式，而不是使用 Doer 模式。</span><span class="sxs-lookup"><span data-stu-id="11650-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="11650-121">模式调用以调整成员名称，从而使定义完善的测试用例成为成员语义的一部分。</span><span class="sxs-lookup"><span data-stu-id="11650-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="11650-122">例如， <xref:System.DateTime> 定义在对 <xref:System.DateTime.Parse%2A> 字符串进行分析失败时引发异常的方法。</span><span class="sxs-lookup"><span data-stu-id="11650-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="11650-123">它还定义了一个 <xref:System.DateTime.TryParse%2A> 尝试进行分析的相应方法，但如果分析不成功，则返回 false，并使用参数返回成功分析的结果 `out` 。</span><span class="sxs-lookup"><span data-stu-id="11650-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="11650-124">使用此模式时，务必按严格的条款定义尝试功能。</span><span class="sxs-lookup"><span data-stu-id="11650-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="11650-125">如果成员由于任何原因而失败，而不是明确定义的尝试，则成员仍必须引发相应的异常。</span><span class="sxs-lookup"><span data-stu-id="11650-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="11650-126">✔️考虑在常见方案中可能会引发异常的成员的试验分析模式，以避免与异常相关的性能问题。</span><span class="sxs-lookup"><span data-stu-id="11650-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="11650-127">✔️对实现此模式的方法使用前缀 "Try" 和 Boolean 返回类型。</span><span class="sxs-lookup"><span data-stu-id="11650-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="11650-128">✔️使用 Try Parse 模式为每个成员提供异常引发成员。</span><span class="sxs-lookup"><span data-stu-id="11650-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="11650-129">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="11650-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="11650-130">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="11650-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="11650-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11650-131">See also</span></span>

- [<span data-ttu-id="11650-132">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="11650-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="11650-133">异常设计准则</span><span class="sxs-lookup"><span data-stu-id="11650-133">Design Guidelines for Exceptions</span></span>](exceptions.md)
