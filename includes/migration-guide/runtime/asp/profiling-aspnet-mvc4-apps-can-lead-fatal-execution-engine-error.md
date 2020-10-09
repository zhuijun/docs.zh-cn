---
ms.openlocfilehash: 8b70df0fb2072fd5243d9e46a4a20c22cc7fd677
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607782"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="5a7f2-101">分析 ASP.NET MVC4 应用可能导致严重的执行引擎错误</span><span class="sxs-lookup"><span data-stu-id="5a7f2-101">Profiling ASP.NET MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="5a7f2-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="5a7f2-102">Details</span></span>

<span data-ttu-id="5a7f2-103">使用 NGEN /Profile 程序集的探查器可能会在启动时使已配置的 ASP.NET MVC4 应用程序出故障，引发“严重的执行引擎异常”</span><span class="sxs-lookup"><span data-stu-id="5a7f2-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5a7f2-104">建议</span><span class="sxs-lookup"><span data-stu-id="5a7f2-104">Suggestion</span></span>

<span data-ttu-id="5a7f2-105">此问题已在 .NET Framework 4.5.2 中解决。</span><span class="sxs-lookup"><span data-stu-id="5a7f2-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="5a7f2-106">或者，探查器可通过在其事件掩码中指定 <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> 来避免此问题。</span><span class="sxs-lookup"><span data-stu-id="5a7f2-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="5a7f2-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="5a7f2-107">Name</span></span>    | <span data-ttu-id="5a7f2-108">“值”</span><span class="sxs-lookup"><span data-stu-id="5a7f2-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5a7f2-109">范围</span><span class="sxs-lookup"><span data-stu-id="5a7f2-109">Scope</span></span>   |<span data-ttu-id="5a7f2-110">边缘</span><span class="sxs-lookup"><span data-stu-id="5a7f2-110">Edge</span></span>|
|<span data-ttu-id="5a7f2-111">Version</span><span class="sxs-lookup"><span data-stu-id="5a7f2-111">Version</span></span>|<span data-ttu-id="5a7f2-112">4.5</span><span class="sxs-lookup"><span data-stu-id="5a7f2-112">4.5</span></span>|
|<span data-ttu-id="5a7f2-113">类型</span><span class="sxs-lookup"><span data-stu-id="5a7f2-113">Type</span></span>|<span data-ttu-id="5a7f2-114">运行时</span><span class="sxs-lookup"><span data-stu-id="5a7f2-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5a7f2-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="5a7f2-115">Affected APIs</span></span>

<span data-ttu-id="5a7f2-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="5a7f2-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
