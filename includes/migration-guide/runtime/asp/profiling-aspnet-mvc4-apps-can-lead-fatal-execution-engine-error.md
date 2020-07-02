---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621939"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="b3994-101">分析 ASP.Net MVC4 应用可能导致严重的执行引擎错误</span><span class="sxs-lookup"><span data-stu-id="b3994-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="b3994-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b3994-102">Details</span></span>

<span data-ttu-id="b3994-103">使用 NGEN /Profile 程序集的探查器可能会在启动时使已配置的 ASP.NET MVC4 应用程序出故障，引发“严重的执行引擎异常”</span><span class="sxs-lookup"><span data-stu-id="b3994-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b3994-104">建议</span><span class="sxs-lookup"><span data-stu-id="b3994-104">Suggestion</span></span>

<span data-ttu-id="b3994-105">此问题已在 .NET Framework 4.5.2 中解决。</span><span class="sxs-lookup"><span data-stu-id="b3994-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="b3994-106">或者，探查器可通过在其事件掩码中指定 <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> 来避免此问题。</span><span class="sxs-lookup"><span data-stu-id="b3994-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="b3994-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="b3994-107">Name</span></span>    | <span data-ttu-id="b3994-108">“值”</span><span class="sxs-lookup"><span data-stu-id="b3994-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b3994-109">范围</span><span class="sxs-lookup"><span data-stu-id="b3994-109">Scope</span></span>   |<span data-ttu-id="b3994-110">边缘</span><span class="sxs-lookup"><span data-stu-id="b3994-110">Edge</span></span>|
|<span data-ttu-id="b3994-111">Version</span><span class="sxs-lookup"><span data-stu-id="b3994-111">Version</span></span>|<span data-ttu-id="b3994-112">4.5</span><span class="sxs-lookup"><span data-stu-id="b3994-112">4.5</span></span>|
|<span data-ttu-id="b3994-113">类型</span><span class="sxs-lookup"><span data-stu-id="b3994-113">Type</span></span>|<span data-ttu-id="b3994-114">运行时</span><span class="sxs-lookup"><span data-stu-id="b3994-114">Runtime</span></span>|
