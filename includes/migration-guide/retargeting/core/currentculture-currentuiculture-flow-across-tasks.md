---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614334"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a><span data-ttu-id="924f0-101">CurrentCulture 和 CurrentUICulture 在任务之间流动</span><span class="sxs-lookup"><span data-stu-id="924f0-101">CurrentCulture and CurrentUICulture flow across tasks</span></span>

#### <a name="details"></a><span data-ttu-id="924f0-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="924f0-102">Details</span></span>

<span data-ttu-id="924f0-103">从 .NET Framework 4.6 开始，<xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> 存储在线程的 <xref:System.Threading.ExecutionContext?displayProperty=fullName> 中，可跨异步操作流动。这意味着对 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> 的更改将反映在稍后以异步方式运行的任务中。</span><span class="sxs-lookup"><span data-stu-id="924f0-103">Beginning in the .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> are stored in the thread's <xref:System.Threading.ExecutionContext?displayProperty=fullName>, which flows across asynchronous operations.This means that changes to <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> will be reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="924f0-104">这与旧版 .NET Framework 的行为不同（旧版会在所有异步任务中重置 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>）。</span><span class="sxs-lookup"><span data-stu-id="924f0-104">This is different from the behavior of previous .NET Framework versions (which would reset <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> in all asynchronous tasks).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="924f0-105">建议</span><span class="sxs-lookup"><span data-stu-id="924f0-105">Suggestion</span></span>

<span data-ttu-id="924f0-106">受此更改影响的应用可通过将所需的 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> 显式设置为异步任务中的首个操作来暂时解决此问题。</span><span class="sxs-lookup"><span data-stu-id="924f0-106">Apps affected by this change may work around it by explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> as the first operation in an async Task.</span></span> <span data-ttu-id="924f0-107">或者，可通过设置以下兼容性开关选择使用旧行为（不流动 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>）：</span><span class="sxs-lookup"><span data-stu-id="924f0-107">Alternatively, the old behavior (of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) may be opted into by setting the following compatibility switch:</span></span>

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

<span data-ttu-id="924f0-108">.NET Framework 4.6.2 中的 WPF 已修复此问题。</span><span class="sxs-lookup"><span data-stu-id="924f0-108">This issue has been fixed by WPF in .NET Framework 4.6.2.</span></span> <span data-ttu-id="924f0-109">.NET Frameworks 4.6、4.6.1 中也通过 [KB 3139549](https://support.microsoft.com/kb/3139549) 修复了此问题。</span><span class="sxs-lookup"><span data-stu-id="924f0-109">It has also been fixed in .NET Frameworks 4.6, 4.6.1 through [KB 3139549](https://support.microsoft.com/kb/3139549).</span></span> <span data-ttu-id="924f0-110">面向 .NET Framework 4.6 或更高版本的应用程序将自动在 WPF 应用程序中获取正确行为 - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> 将在调度程序操作中保留。</span><span class="sxs-lookup"><span data-stu-id="924f0-110">Applications targeting .NET Framework 4.6 or later will automatically get the right behavior in WPF applications - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) would be preserved across Dispatcher operations.</span></span>

| <span data-ttu-id="924f0-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="924f0-111">Name</span></span>    | <span data-ttu-id="924f0-112">“值”</span><span class="sxs-lookup"><span data-stu-id="924f0-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="924f0-113">范围</span><span class="sxs-lookup"><span data-stu-id="924f0-113">Scope</span></span>   | <span data-ttu-id="924f0-114">次要</span><span class="sxs-lookup"><span data-stu-id="924f0-114">Minor</span></span>       |
| <span data-ttu-id="924f0-115">Version</span><span class="sxs-lookup"><span data-stu-id="924f0-115">Version</span></span> | <span data-ttu-id="924f0-116">4.6</span><span class="sxs-lookup"><span data-stu-id="924f0-116">4.6</span></span>         |
| <span data-ttu-id="924f0-117">类型</span><span class="sxs-lookup"><span data-stu-id="924f0-117">Type</span></span>    | <span data-ttu-id="924f0-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="924f0-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="924f0-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="924f0-119">Affected APIs</span></span>

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
