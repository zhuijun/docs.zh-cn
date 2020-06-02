---
title: 异常引发
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 6bbc6e8fa11759afbd3a1fb2d785f476a6c178ad
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289806"
---
# <a name="exception-throwing"></a><span data-ttu-id="db24a-102">异常引发</span><span class="sxs-lookup"><span data-stu-id="db24a-102">Exception Throwing</span></span>
<span data-ttu-id="db24a-103">本部分中所述的异常引发准则需要一个良好的定义来表示执行失败。</span><span class="sxs-lookup"><span data-stu-id="db24a-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="db24a-104">每当成员无法执行其设计时（成员名称所指的内容），将发生执行失败。</span><span class="sxs-lookup"><span data-stu-id="db24a-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="db24a-105">例如，如果该 `OpenFile` 方法无法向调用方返回打开的文件句柄，则会将其视为执行失败。</span><span class="sxs-lookup"><span data-stu-id="db24a-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="db24a-106">大多数开发人员对使用错误（例如除以零或空引用）的使用异常感到非常熟悉。</span><span class="sxs-lookup"><span data-stu-id="db24a-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="db24a-107">在框架中，异常用于所有错误情况，包括执行错误。</span><span class="sxs-lookup"><span data-stu-id="db24a-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="db24a-108">❌不返回错误代码。</span><span class="sxs-lookup"><span data-stu-id="db24a-108">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="db24a-109">异常是在框架中报告错误的主要方法。</span><span class="sxs-lookup"><span data-stu-id="db24a-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="db24a-110">✔️通过引发异常来报告执行失败。</span><span class="sxs-lookup"><span data-stu-id="db24a-110">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="db24a-111">✔️考虑通过调用 `System.Environment.FailFast` （.NET Framework 2.0 功能）终止进程，而不是在代码遇到不安全的情况下引发异常，以便进行进一步的执行。</span><span class="sxs-lookup"><span data-stu-id="db24a-111">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="db24a-112">❌如果可能，请不要为正常控制流使用异常。</span><span class="sxs-lookup"><span data-stu-id="db24a-112">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="db24a-113">除了可能出现争用条件的系统故障和操作，框架设计器还应设计 Api，使用户能够编写不引发异常的代码。</span><span class="sxs-lookup"><span data-stu-id="db24a-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="db24a-114">例如，你可以提供一种在调用成员之前检查前置条件的方法，以便用户可以编写不引发异常的代码。</span><span class="sxs-lookup"><span data-stu-id="db24a-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="db24a-115">用于检查另一个成员的前置条件的成员通常称为测试人员，实际执行该工作的成员称为 doer。</span><span class="sxs-lookup"><span data-stu-id="db24a-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="db24a-116">在某些情况下，Doer 模式可能会产生不可接受的性能开销。</span><span class="sxs-lookup"><span data-stu-id="db24a-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="db24a-117">在这种情况下，应考虑所谓的试用分析模式（有关详细信息，请参阅[异常和性能](exceptions-and-performance.md)）。</span><span class="sxs-lookup"><span data-stu-id="db24a-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="db24a-118">✔️考虑引发异常的性能影响。</span><span class="sxs-lookup"><span data-stu-id="db24a-118">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="db24a-119">每秒以上100的引发率可能会显著影响大多数应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="db24a-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="db24a-120">✔️会记录公共可调用成员引发的所有异常，因为违反了成员协定（而不是系统失败），并将它们视为协定的一部分。</span><span class="sxs-lookup"><span data-stu-id="db24a-120">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="db24a-121">作为协定一部分的异常不应从一个版本更改为下一个版本（即，异常类型不应更改，且不应添加新异常）。</span><span class="sxs-lookup"><span data-stu-id="db24a-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="db24a-122">❌不具有可引发的公共成员或不基于某个选项的公共成员。</span><span class="sxs-lookup"><span data-stu-id="db24a-122">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="db24a-123">❌不具有返回异常作为返回值或参数的公共成员 `out` 。</span><span class="sxs-lookup"><span data-stu-id="db24a-123">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="db24a-124">从公共 Api 返回异常，而不是引发异常，这会破坏基于异常的错误报告的许多好处。</span><span class="sxs-lookup"><span data-stu-id="db24a-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="db24a-125">✔️考虑使用异常生成器方法。</span><span class="sxs-lookup"><span data-stu-id="db24a-125">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="db24a-126">通常会从不同的位置引发相同的异常。</span><span class="sxs-lookup"><span data-stu-id="db24a-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="db24a-127">若要避免代码膨胀，请使用创建异常并初始化其属性的帮助器方法。</span><span class="sxs-lookup"><span data-stu-id="db24a-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="db24a-128">而且，引发异常的成员不能内联。</span><span class="sxs-lookup"><span data-stu-id="db24a-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="db24a-129">在生成器中移动 throw 语句可能会允许该成员内联。</span><span class="sxs-lookup"><span data-stu-id="db24a-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="db24a-130">❌不引发异常筛选器块中的异常。</span><span class="sxs-lookup"><span data-stu-id="db24a-130">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="db24a-131">当异常筛选器引发异常时，CLR 将捕获该异常，并且筛选器将返回 false。</span><span class="sxs-lookup"><span data-stu-id="db24a-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="db24a-132">此行为与执行和显式返回 false 的筛选器不区分，因此很难进行调试。</span><span class="sxs-lookup"><span data-stu-id="db24a-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="db24a-133">❌避免从 finally 块显式引发异常。</span><span class="sxs-lookup"><span data-stu-id="db24a-133">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="db24a-134">调用引发的方法可接受隐式引发的异常。</span><span class="sxs-lookup"><span data-stu-id="db24a-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="db24a-135">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="db24a-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="db24a-136">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="db24a-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="db24a-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db24a-137">See also</span></span>

- [<span data-ttu-id="db24a-138">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="db24a-138">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="db24a-139">异常设计准则</span><span class="sxs-lookup"><span data-stu-id="db24a-139">Design Guidelines for Exceptions</span></span>](exceptions.md)
