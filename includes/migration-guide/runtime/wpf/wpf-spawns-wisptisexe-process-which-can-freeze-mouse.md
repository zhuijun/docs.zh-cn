---
ms.openlocfilehash: e0f72d19a884087b1f0f6ebd1b6baea75bc37af4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619901"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a><span data-ttu-id="41094-101">WPF 生成可冻结鼠标的 wisptis.exe 进程</span><span class="sxs-lookup"><span data-stu-id="41094-101">WPF spawns a wisptis.exe process which can freeze the mouse</span></span>

#### <a name="details"></a><span data-ttu-id="41094-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="41094-102">Details</span></span>

<span data-ttu-id="41094-103">4\.5.2 中引入了一个问题，导致生成可冻结鼠标输入的 <code>wisptis.exe</code>。</span><span class="sxs-lookup"><span data-stu-id="41094-103">An issue was introduced in 4.5.2 that causes <code>wisptis.exe</code> to be spawned that can freeze mouse input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="41094-104">建议</span><span class="sxs-lookup"><span data-stu-id="41094-104">Suggestion</span></span>

<span data-ttu-id="41094-105">.NET Framework 4.5.2 的服务版本（修补程序汇总 3026376）中提供了此问题的修补程序，也可通过升级到 .NET Framework 4.6 解决此问题</span><span class="sxs-lookup"><span data-stu-id="41094-105">A fix for this issue is available in a servicing release of the .NET Framework 4.5.2 (hotfix rollup 3026376), or by upgrading to the .NET Framework 4.6</span></span>

| <span data-ttu-id="41094-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="41094-106">Name</span></span>    | <span data-ttu-id="41094-107">“值”</span><span class="sxs-lookup"><span data-stu-id="41094-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="41094-108">范围</span><span class="sxs-lookup"><span data-stu-id="41094-108">Scope</span></span>   |<span data-ttu-id="41094-109">主要</span><span class="sxs-lookup"><span data-stu-id="41094-109">Major</span></span>|
|<span data-ttu-id="41094-110">Version</span><span class="sxs-lookup"><span data-stu-id="41094-110">Version</span></span>|<span data-ttu-id="41094-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="41094-111">4.5.2</span></span>|
|<span data-ttu-id="41094-112">类型</span><span class="sxs-lookup"><span data-stu-id="41094-112">Type</span></span>|<span data-ttu-id="41094-113">运行时</span><span class="sxs-lookup"><span data-stu-id="41094-113">Runtime</span></span>|
