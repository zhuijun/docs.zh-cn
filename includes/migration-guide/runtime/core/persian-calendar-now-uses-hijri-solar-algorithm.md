---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621122"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="4be41-101">波斯日历现在使用回历太阳算法</span><span class="sxs-lookup"><span data-stu-id="4be41-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="4be41-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4be41-102">Details</span></span>

<span data-ttu-id="4be41-103">自 .NET Framework 4.6 起，<xref:System.Globalization.PersianCalendar?displayProperty=fullName> 类使用回历太阳算法。</span><span class="sxs-lookup"><span data-stu-id="4be41-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="4be41-104">自 .NET Framework 4.6 起，对于早于 1800 年或晚于 2023 年（公历）的日期，在 <xref:System.Globalization.PersianCalendar?displayProperty=fullName> 和其他日历之间转换日期所得结果可能略微不同。此外，<xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> 现在为 <code>March 22, 0622</code>，而不是 <code>March 21, 0622</code>。</span><span class="sxs-lookup"><span data-stu-id="4be41-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4be41-105">建议</span><span class="sxs-lookup"><span data-stu-id="4be41-105">Suggestion</span></span>

<span data-ttu-id="4be41-106">请注意，在 .NET Framework 4.6 中使用 PersianCalendar 时，某些较早或较晚的日期可能略微不同。</span><span class="sxs-lookup"><span data-stu-id="4be41-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="4be41-107">另外，当在不同 .NET Framework 版本上运行的进程之间序列化日期时，请勿将它们存储为 PersianCalendar 日期字符串（因为这些值可能不相同）。</span><span class="sxs-lookup"><span data-stu-id="4be41-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="4be41-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="4be41-108">Name</span></span>    | <span data-ttu-id="4be41-109">值</span><span class="sxs-lookup"><span data-stu-id="4be41-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4be41-110">范围</span><span class="sxs-lookup"><span data-stu-id="4be41-110">Scope</span></span>   |<span data-ttu-id="4be41-111">次要</span><span class="sxs-lookup"><span data-stu-id="4be41-111">Minor</span></span>|
|<span data-ttu-id="4be41-112">Version</span><span class="sxs-lookup"><span data-stu-id="4be41-112">Version</span></span>|<span data-ttu-id="4be41-113">4.6</span><span class="sxs-lookup"><span data-stu-id="4be41-113">4.6</span></span>|
|<span data-ttu-id="4be41-114">类型</span><span class="sxs-lookup"><span data-stu-id="4be41-114">Type</span></span>|<span data-ttu-id="4be41-115">运行时</span><span class="sxs-lookup"><span data-stu-id="4be41-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4be41-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="4be41-116">Affected APIs</span></span>

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
