---
title: 在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之间进行选择
description: 了解如何在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 类型之间进行选择，以表示 .NET 中的日期和时间信息。
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
ms.openlocfilehash: 0b89d0fd36af00796105af50f51803c90cce2605
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662805"
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a><span data-ttu-id="996e0-103">在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之间进行选择</span><span class="sxs-lookup"><span data-stu-id="996e0-103">Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>

<span data-ttu-id="996e0-104">使用日期和时间信息的 .NET 应用程序多种多样，并可以多种方式使用此类信息。</span><span class="sxs-lookup"><span data-stu-id="996e0-104">.NET applications that use date and time information are very diverse and can use that information in several ways.</span></span> <span data-ttu-id="996e0-105">日期和时间信息的较常见使用方法包括以下一种或多种：</span><span class="sxs-lookup"><span data-stu-id="996e0-105">The more common uses of date and time information include one or more of the following:</span></span>

- <span data-ttu-id="996e0-106">仅反映日期，而时间信息不重要。</span><span class="sxs-lookup"><span data-stu-id="996e0-106">To reflect a date only, so that time information is not important.</span></span>

- <span data-ttu-id="996e0-107">仅反映时间，而日期信息不重要。</span><span class="sxs-lookup"><span data-stu-id="996e0-107">To reflect a time only, so that date information is not important.</span></span>

- <span data-ttu-id="996e0-108">反映未绑定到特定时间和位置的抽象的日期和时间（例如，国际上大多数连锁店在工作日上午 9:00 开张）。</span><span class="sxs-lookup"><span data-stu-id="996e0-108">To reflect an abstract date and time that is not tied to a specific time and place (for example, most stores in an international chain open on weekdays at 9:00 A.M.).</span></span>

- <span data-ttu-id="996e0-109">若要从 .NET 以外的源中检索日期和时间信息，通常是在简单的数据类型中存储日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="996e0-109">To retrieve date and time information from sources outside of .NET, typically where date and time information is stored in a simple data type.</span></span>

- <span data-ttu-id="996e0-110">唯一、明确地标识单个时间点。</span><span class="sxs-lookup"><span data-stu-id="996e0-110">To uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="996e0-111">某些应用程序仅要求主机系统具有明确的日期和时间；其他程序要求整个系统中均具有明确的日期和时间（即，在意义上，某个系统上序列化的日期可以在世界各地的其他系统上进行反序列化和使用）。</span><span class="sxs-lookup"><span data-stu-id="996e0-111">Some applications require that a date and time be unambiguous only on the host system; others require that it be unambiguous across systems (that is, a date serialized on one system can be meaningfully deserialized and used on another system anywhere in the world).</span></span>

- <span data-ttu-id="996e0-112">保留多个相关时间（例如请求程序的本地时间和服务器接收 Web 请求的时间）。</span><span class="sxs-lookup"><span data-stu-id="996e0-112">To preserve multiple related times (such as the requestor's local time and the server's time of receipt for a Web request).</span></span>

- <span data-ttu-id="996e0-113">执行日期和时间算法，可能致使唯一、明确标识单个时间点。</span><span class="sxs-lookup"><span data-stu-id="996e0-113">To perform date and time arithmetic, possibly with a result that uniquely and unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="996e0-114">.Net 包括 <xref:System.DateTime> 、 <xref:System.DateTimeOffset> 、 <xref:System.TimeSpan> 和 <xref:System.TimeZoneInfo> 类型，所有这些类型都可用于生成处理日期和时间的应用程序。</span><span class="sxs-lookup"><span data-stu-id="996e0-114">.NET includes the <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, and <xref:System.TimeZoneInfo> types, all of which can be used to build applications that work with dates and times.</span></span>

> [!NOTE]
> <span data-ttu-id="996e0-115">本主题不讨论， <xref:System.TimeZone> 因为其功能几乎完全融入在 <xref:System.TimeZoneInfo> 类中。</span><span class="sxs-lookup"><span data-stu-id="996e0-115">This topic doesn't discuss <xref:System.TimeZone> because its functionality is almost entirely incorporated in the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="996e0-116">请尽可能使用类， <xref:System.TimeZoneInfo> 而不使用 <xref:System.TimeZone> 类。</span><span class="sxs-lookup"><span data-stu-id="996e0-116">Whenever possible, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

## <a name="the-datetime-structure"></a><span data-ttu-id="996e0-117">DateTime 结构</span><span class="sxs-lookup"><span data-stu-id="996e0-117">The DateTime structure</span></span>

<span data-ttu-id="996e0-118"><xref:System.DateTime> 值定义特定日期和时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-118">A <xref:System.DateTime> value defines a particular date and time.</span></span> <span data-ttu-id="996e0-119">它包括一个 <xref:System.DateTime.Kind%2A> 属性，该属性提供有关日期和时间所属时区的有限信息。</span><span class="sxs-lookup"><span data-stu-id="996e0-119">It includes a <xref:System.DateTime.Kind%2A> property that provides limited information about the time zone to which that date and time belongs.</span></span> <span data-ttu-id="996e0-120">由 <xref:System.DateTimeKind> 属性返回的 <xref:System.DateTime.Kind%2A> 值指示 <xref:System.DateTime> 值是表示本地时间 (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>)、协调世界时 (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>) 还是未指定的时间 (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="996e0-120">The <xref:System.DateTimeKind> value returned by the <xref:System.DateTime.Kind%2A> property indicates whether the <xref:System.DateTime> value represents the local time (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), Coordinated Universal Time (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), or an unspecified time (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).</span></span>

<span data-ttu-id="996e0-121"><xref:System.DateTime> 结构适用于执行以下操作的应用程序：</span><span class="sxs-lookup"><span data-stu-id="996e0-121">The <xref:System.DateTime> structure is suitable for applications that do the following:</span></span>

- <span data-ttu-id="996e0-122">仅使用日期。</span><span class="sxs-lookup"><span data-stu-id="996e0-122">Work with dates only.</span></span>

- <span data-ttu-id="996e0-123">只使用时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-123">Work with times only.</span></span>

- <span data-ttu-id="996e0-124">使用抽象的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-124">Work with abstract dates and times.</span></span>

- <span data-ttu-id="996e0-125">使用缺少时区信息的日期和时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-125">Work with dates and times for which time zone information is missing.</span></span>

- <span data-ttu-id="996e0-126">只使用 UTC 日期和时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-126">Work with UTC dates and times only.</span></span>

- <span data-ttu-id="996e0-127">从 .NET 外部的源（如 SQL 数据库）中检索日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="996e0-127">Retrieve date and time information from sources outside of .NET, such as SQL databases.</span></span> <span data-ttu-id="996e0-128">通常，这些源按与 <xref:System.DateTime> 结构兼容的简单格式存储日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="996e0-128">Typically, these sources store date and time information in a simple format that is compatible with the <xref:System.DateTime> structure.</span></span>

- <span data-ttu-id="996e0-129">执行日期和时间算法，但不关注常规结果。</span><span class="sxs-lookup"><span data-stu-id="996e0-129">Perform date and time arithmetic, but are concerned with general results.</span></span> <span data-ttu-id="996e0-130">例如，在向特定日期和时间添加六个月的加法运算中，是否将结果调整为夏令时通常并不重要。</span><span class="sxs-lookup"><span data-stu-id="996e0-130">For example, in an addition operation that adds six months to a particular date and time, it is often not important whether the result is adjusted for daylight saving time.</span></span>

<span data-ttu-id="996e0-131">除非特定的 <xref:System.DateTime> 值表示 UTC，否则日期和时间值通常不明确的或其可移植性受限。</span><span class="sxs-lookup"><span data-stu-id="996e0-131">Unless a particular <xref:System.DateTime> value represents UTC, that date and time value is often ambiguous or limited in its portability.</span></span> <span data-ttu-id="996e0-132">例如，如果 <xref:System.DateTime> 值表示本地时间，则在该本地时区内可移植（即，如果在其他系统的相同时区上反序列化此值，它仍然明确标识单个时间点）。</span><span class="sxs-lookup"><span data-stu-id="996e0-132">For example, if a <xref:System.DateTime> value represents the local time, it is portable within that local time zone (that is, if the value is deserialized on another system in the same time zone, that value still unambiguously identifies a single point in time).</span></span> <span data-ttu-id="996e0-133">在本地时区之外， <xref:System.DateTime> 值可以具有多个解释。</span><span class="sxs-lookup"><span data-stu-id="996e0-133">Outside the local time zone, that <xref:System.DateTime> value can have multiple interpretations.</span></span> <span data-ttu-id="996e0-134">如果值的 <xref:System.DateTime.Kind%2A> 属性是 <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，则它的可移植性更低：此时它在相同时区内（可能甚至在首次序列化的同一系统上）是不明确的。</span><span class="sxs-lookup"><span data-stu-id="996e0-134">If the value's <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, it is even less portable: it is now ambiguous within the same time zone and possibly even on the same system on which it was first serialized.</span></span> <span data-ttu-id="996e0-135">仅当 <xref:System.DateTime> 值表示 UTC 时，无论使用此值的系统和时区如何，它都会明确标识单个时间点。</span><span class="sxs-lookup"><span data-stu-id="996e0-135">Only if a <xref:System.DateTime> value represents UTC does that value unambiguously identify a single point in time regardless of the system or time zone in which the value is used.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="996e0-136">在保存或共享 <xref:System.DateTime> 数据时，应使用 UTC 并将 <xref:System.DateTime> 值的 <xref:System.DateTime.Kind%2A> 属性设置为 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="996e0-136">When saving or sharing <xref:System.DateTime> data, UTC should be used and the <xref:System.DateTime> value's <xref:System.DateTime.Kind%2A> property should be set to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="the-datetimeoffset-structure"></a><span data-ttu-id="996e0-137">DateTimeOffset 结构</span><span class="sxs-lookup"><span data-stu-id="996e0-137">The DateTimeOffset structure</span></span>

<span data-ttu-id="996e0-138"><xref:System.DateTimeOffset> 结构表示日期和时间值，以及指示此值与 UTC 的差异程度的偏移量。</span><span class="sxs-lookup"><span data-stu-id="996e0-138">The <xref:System.DateTimeOffset> structure represents a date and time value, together with an offset that indicates how much that value differs from UTC.</span></span> <span data-ttu-id="996e0-139">因此，此值始终明确地标识单个时间点。</span><span class="sxs-lookup"><span data-stu-id="996e0-139">Thus, the value always unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="996e0-140"><xref:System.DateTimeOffset> 类型包括 <xref:System.DateTime> 类型的所有功能以及时区感知功能。</span><span class="sxs-lookup"><span data-stu-id="996e0-140">The <xref:System.DateTimeOffset> type includes all of the functionality of the <xref:System.DateTime> type along with time zone awareness.</span></span> <span data-ttu-id="996e0-141">这使它适用于执行以下操作的应用程序：</span><span class="sxs-lookup"><span data-stu-id="996e0-141">This makes it suitable for applications that do the following:</span></span>

- <span data-ttu-id="996e0-142">唯一、明确地标识单个时间点。</span><span class="sxs-lookup"><span data-stu-id="996e0-142">Uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="996e0-143"><xref:System.DateTimeOffset> 类型可用于明确定义“现在”的含义、记录事务时间、记录系统或应用程序事件时间以及记录创建和修改时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-143">The <xref:System.DateTimeOffset> type can be used to unambiguously define the meaning of "now", to log transaction times, to log the times of system or application events, and to record file creation and modification times.</span></span>

- <span data-ttu-id="996e0-144">执行常规日期和时间算法。</span><span class="sxs-lookup"><span data-stu-id="996e0-144">Perform general date and time arithmetic.</span></span>

- <span data-ttu-id="996e0-145">保留多个相关时间，只要这些时间存储为两个单独的值或结构中的两个成员。</span><span class="sxs-lookup"><span data-stu-id="996e0-145">Preserve multiple related times, as long as those times are stored as two separate values or as two members of a structure.</span></span>

> [!NOTE]
> <span data-ttu-id="996e0-146"><xref:System.DateTimeOffset> 值的使用频率比 <xref:System.DateTime> 值的更高。</span><span class="sxs-lookup"><span data-stu-id="996e0-146">These uses for <xref:System.DateTimeOffset> values are much more common than those for <xref:System.DateTime> values.</span></span> <span data-ttu-id="996e0-147">因此，在应用程序开发中应考虑使用 <xref:System.DateTimeOffset> 作为默认日期和时间类型。</span><span class="sxs-lookup"><span data-stu-id="996e0-147">As a result, <xref:System.DateTimeOffset> should be considered the default date and time type for application development.</span></span>

<span data-ttu-id="996e0-148"><xref:System.DateTimeOffset> 值不限于特定时区，而可以来自各个时区。</span><span class="sxs-lookup"><span data-stu-id="996e0-148">A <xref:System.DateTimeOffset> value is not tied to a particular time zone, but can originate from any of a variety of time zones.</span></span> <span data-ttu-id="996e0-149">为了说明这一点，以下示例列出了 <xref:System.DateTimeOffset> 值（包括本地太平洋标准时间）可属于的时区。</span><span class="sxs-lookup"><span data-stu-id="996e0-149">To illustrate this, the following example lists the time zones to which a number of <xref:System.DateTimeOffset> values (including a local Pacific Standard Time) can belong.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

<span data-ttu-id="996e0-150">输出显示，此示例中的每个日期和时间值至少可以属于三个不同时区。</span><span class="sxs-lookup"><span data-stu-id="996e0-150">The output shows that each date and time value in this example can belong to at least three different time zones.</span></span> <span data-ttu-id="996e0-151">2007 年 6 月 10 日的 <xref:System.DateTimeOffset> 值显示，如果日期和时间值表示夏令时，则其相对于 UTC 的偏移量甚至不一定对应于原始时区的基本 UTC 偏移量或其显示名称中找到的相对于 UTC 的偏移量。</span><span class="sxs-lookup"><span data-stu-id="996e0-151">The <xref:System.DateTimeOffset> value of 6/10/2007 shows that if a date and time value represents a daylight saving time, its offset from UTC does not even necessarily correspond to the originating time zone's base UTC offset or to the offset from UTC found in its display name.</span></span> <span data-ttu-id="996e0-152">这意味着，因为单个 <xref:System.DateTimeOffset> 值与其时区并非紧密耦合的，因此它无法反映到/从夏令时的时区转换。</span><span class="sxs-lookup"><span data-stu-id="996e0-152">This means that, because a single <xref:System.DateTimeOffset> value is not tightly coupled with its time zone, it cannot reflect a time zone's transition to and from daylight saving time.</span></span> <span data-ttu-id="996e0-153">这在使用日期和时间运算操纵 <xref:System.DateTimeOffset> 值时特别容易出现问题。</span><span class="sxs-lookup"><span data-stu-id="996e0-153">This can be particularly problematic when date and time arithmetic is used to manipulate a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="996e0-154">有关如何以考虑时区调整规则的方式执行日期和时间算术运算的讨论，请参阅[执行日期和时间算术运算](performing-arithmetic-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="996e0-154">For a discussion of how to perform date and time arithmetic in a way that takes account of a time zone's adjustment rules, see [Performing arithmetic operations with dates and times](performing-arithmetic-operations.md).</span></span>

## <a name="the-timespan-structure"></a><span data-ttu-id="996e0-155">TimeSpan 结构</span><span class="sxs-lookup"><span data-stu-id="996e0-155">The TimeSpan structure</span></span>

<span data-ttu-id="996e0-156"><xref:System.TimeSpan> 结构表示时间间隔。</span><span class="sxs-lookup"><span data-stu-id="996e0-156">The <xref:System.TimeSpan> structure represents a time interval.</span></span> <span data-ttu-id="996e0-157">它的两个典型用途是：</span><span class="sxs-lookup"><span data-stu-id="996e0-157">Its two typical uses are:</span></span>

- <span data-ttu-id="996e0-158">反映两个日期和时间值之间的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="996e0-158">Reflecting the time interval between two date and time values.</span></span> <span data-ttu-id="996e0-159">例如，两个 <xref:System.DateTime> 值相减将返回 <xref:System.TimeSpan> 值。</span><span class="sxs-lookup"><span data-stu-id="996e0-159">For example, subtracting one <xref:System.DateTime> value from another returns a <xref:System.TimeSpan> value.</span></span>

- <span data-ttu-id="996e0-160">测量运行时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-160">Measuring elapsed time.</span></span> <span data-ttu-id="996e0-161">例如， <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> 属性返回一个 <xref:System.TimeSpan> 值，该值反映自调用 <xref:System.Diagnostics.Stopwatch> 开始测量运行时间的其中一个方法以来经过的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="996e0-161">For example, the <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> property returns a <xref:System.TimeSpan> value that reflects the time interval that has elapsed since the call to one of the <xref:System.Diagnostics.Stopwatch> methods that begins to measure elapsed time.</span></span>

<span data-ttu-id="996e0-162">值 <xref:System.TimeSpan> 还可用于替换值（ <xref:System.DateTime> 当该值反映不引用特定日期的时间）。</span><span class="sxs-lookup"><span data-stu-id="996e0-162">A <xref:System.TimeSpan> value can also be used as a replacement for a <xref:System.DateTime> value when that value reflects a time without reference to a particular day.</span></span> <span data-ttu-id="996e0-163">此用法与 <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> 和 <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> 属性类似，后者返回一个 <xref:System.TimeSpan> 值，该值表示不引用日期的时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-163">This usage is similar to the <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> properties, which return a <xref:System.TimeSpan> value that represents the time without reference to a date.</span></span> <span data-ttu-id="996e0-164">例如， <xref:System.TimeSpan> 结构可用于反映商店每天的开张或打烊时间，还可用来表示任何常规事件发生的时间。</span><span class="sxs-lookup"><span data-stu-id="996e0-164">For example, the <xref:System.TimeSpan> structure can be used to reflect a store's daily opening or closing time, or it can be used to represent the time at which any regular event occurs.</span></span>

<span data-ttu-id="996e0-165">以下示例定义了 `StoreInfo` 结构，其中包含表示商店开张或打烊时间的 <xref:System.TimeSpan> 对象，以及表示商店所在时区的 <xref:System.TimeZoneInfo> 对象。</span><span class="sxs-lookup"><span data-stu-id="996e0-165">The following example defines a `StoreInfo` structure that includes <xref:System.TimeSpan> objects for store opening and closing times, as well as a <xref:System.TimeZoneInfo> object that represents the store's time zone.</span></span> <span data-ttu-id="996e0-166">此结构还包含两个方法（`IsOpenNow` 和 `IsOpenAt`），用于指示假定用户处于本地时区时其所指定的时间商店是否开张。</span><span class="sxs-lookup"><span data-stu-id="996e0-166">The structure also includes two methods, `IsOpenNow` and `IsOpenAt`, that indicates whether the store is open at a time specified by the user, who is assumed to be in the local time zone.</span></span>

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

<span data-ttu-id="996e0-167">随后， `StoreInfo` 结构可由客户端代码按如下方式使用。</span><span class="sxs-lookup"><span data-stu-id="996e0-167">The `StoreInfo` structure can then be used by client code like the following.</span></span>

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a><span data-ttu-id="996e0-168">TimeZoneInfo 类</span><span class="sxs-lookup"><span data-stu-id="996e0-168">The TimeZoneInfo class</span></span>

<span data-ttu-id="996e0-169"><xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone.</span><span class="sxs-lookup"><span data-stu-id="996e0-169">The <xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone.</span></span> <span data-ttu-id="996e0-170">借助 <xref:System.TimeZoneInfo> 类，即可处理日期和时间，以使任何日期和时间值均明确标识单个时间点。</span><span class="sxs-lookup"><span data-stu-id="996e0-170">The <xref:System.TimeZoneInfo> class makes it possible to work with dates and times so that any date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="996e0-171"><xref:System.TimeZoneInfo> 类也可扩展。</span><span class="sxs-lookup"><span data-stu-id="996e0-171">The <xref:System.TimeZoneInfo> class is also extensible.</span></span> <span data-ttu-id="996e0-172">虽然它依赖于为 Windows 系统提供且在注册表中定义的时区信息，但仍然支持创建自定义时区。</span><span class="sxs-lookup"><span data-stu-id="996e0-172">Although it depends on time zone information provided for Windows systems and defined in the registry, it supports the creation of custom time zones.</span></span> <span data-ttu-id="996e0-173">它还支持时区信息的序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="996e0-173">It also supports the serialization and deserialization of time zone information.</span></span>

<span data-ttu-id="996e0-174">在某些情况下，可能需要进一步的开发工作才可以充分利用 <xref:System.TimeZoneInfo> 类。</span><span class="sxs-lookup"><span data-stu-id="996e0-174">In some cases, taking full advantage of the <xref:System.TimeZoneInfo> class may require further development work.</span></span> <span data-ttu-id="996e0-175">如果日期和时间值不与其所属的时区紧密耦合，则需要进一步的工作。</span><span class="sxs-lookup"><span data-stu-id="996e0-175">If date and time values are not tightly coupled with the time zones to which they belong, further work is required.</span></span> <span data-ttu-id="996e0-176">除非您的应用程序提供某种机制来将日期和时间与其关联的时区链接在一起，否则特定日期和时间值很容易与其时区无关。</span><span class="sxs-lookup"><span data-stu-id="996e0-176">Unless your application provides some mechanism for linking a date and time with its associated time zone, it's easy for a particular date and time value to become disassociated from its time zone.</span></span> <span data-ttu-id="996e0-177">链接此信息的一种方法是，定义一个同时包含日期和时间值及其关联时区对象的类或结构。</span><span class="sxs-lookup"><span data-stu-id="996e0-177">One method of linking this information is to define a class or structure that contains both the date and time value and its associated time zone object.</span></span>

<span data-ttu-id="996e0-178">仅当日期和时间对象实例化时其值所属的时区已知，才可使用 .NET 中的时区支持。</span><span class="sxs-lookup"><span data-stu-id="996e0-178">Taking advantage of time zone support in .NET is possible only if the time zone to which a date and time value belongs is known when that date and time object is instantiated.</span></span> <span data-ttu-id="996e0-179">这通情况并非如此，尤其是在 Web 或网络应用程序中。</span><span class="sxs-lookup"><span data-stu-id="996e0-179">This is often not the case, particularly in Web or network applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="996e0-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="996e0-180">See also</span></span>

- [<span data-ttu-id="996e0-181">日期、时间和时区</span><span class="sxs-lookup"><span data-stu-id="996e0-181">Dates, times, and time zones</span></span>](index.md)
