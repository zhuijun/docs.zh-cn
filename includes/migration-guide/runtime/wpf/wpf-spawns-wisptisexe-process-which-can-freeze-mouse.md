---
ms.openlocfilehash: c3114277445daaae988b41782721c443c1e780d1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496314"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a><span data-ttu-id="1cbf0-101">WPF 生成可冻结鼠标的 wisptis.exe 进程</span><span class="sxs-lookup"><span data-stu-id="1cbf0-101">WPF spawns a wisptis.exe process which can freeze the mouse</span></span>

#### <a name="details"></a><span data-ttu-id="1cbf0-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1cbf0-102">Details</span></span>

<span data-ttu-id="1cbf0-103">4\.5.2 中引入了一个问题，导致生成可冻结鼠标输入的 <code>wisptis.exe</code>。</span><span class="sxs-lookup"><span data-stu-id="1cbf0-103">An issue was introduced in 4.5.2 that causes <code>wisptis.exe</code> to be spawned that can freeze mouse input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1cbf0-104">建议</span><span class="sxs-lookup"><span data-stu-id="1cbf0-104">Suggestion</span></span>

<span data-ttu-id="1cbf0-105">.NET Framework 4.5.2 的服务版本（修补程序汇总 3026376）中提供了此问题的修补程序，也可通过升级到 .NET Framework 4.6 解决此问题</span><span class="sxs-lookup"><span data-stu-id="1cbf0-105">A fix for this issue is available in a servicing release of the .NET Framework 4.5.2 (hotfix rollup 3026376), or by upgrading to the .NET Framework 4.6</span></span>

| <span data-ttu-id="1cbf0-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="1cbf0-106">Name</span></span>    | <span data-ttu-id="1cbf0-107">“值”</span><span class="sxs-lookup"><span data-stu-id="1cbf0-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1cbf0-108">范围</span><span class="sxs-lookup"><span data-stu-id="1cbf0-108">Scope</span></span>   |<span data-ttu-id="1cbf0-109">主要</span><span class="sxs-lookup"><span data-stu-id="1cbf0-109">Major</span></span>|
|<span data-ttu-id="1cbf0-110">Version</span><span class="sxs-lookup"><span data-stu-id="1cbf0-110">Version</span></span>|<span data-ttu-id="1cbf0-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="1cbf0-111">4.5.2</span></span>|
|<span data-ttu-id="1cbf0-112">类型</span><span class="sxs-lookup"><span data-stu-id="1cbf0-112">Type</span></span>|<span data-ttu-id="1cbf0-113">运行时</span><span class="sxs-lookup"><span data-stu-id="1cbf0-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1cbf0-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1cbf0-114">Affected APIs</span></span>

<span data-ttu-id="1cbf0-115">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="1cbf0-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
