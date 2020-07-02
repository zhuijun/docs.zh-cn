---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619847"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a><span data-ttu-id="cb832-101">在执行后一个步骤时才能在调试器中看到空联合器值</span><span class="sxs-lookup"><span data-stu-id="cb832-101">Null coalescer values are not visible in debugger until one step later</span></span>

#### <a name="details"></a><span data-ttu-id="cb832-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cb832-102">Details</span></span>

<span data-ttu-id="cb832-103">在 64 位版本的 Framework 上运行时，.NET Framework 4.5 中的 bug 导致在执行分配操作后无法立即在调试器中看到通过空联合操作设置的值。</span><span class="sxs-lookup"><span data-stu-id="cb832-103">A bug in the .NET Framework 4.5 causes values set via a null coalescing operation to not be visible in the debugger immediately after the assignment operation is executed when running on the 64-bit version of the Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cb832-104">建议</span><span class="sxs-lookup"><span data-stu-id="cb832-104">Suggestion</span></span>

<span data-ttu-id="cb832-105">在调试器中多单步执行一次将正确更新本地/字段的值。</span><span class="sxs-lookup"><span data-stu-id="cb832-105">Stepping one additional time in the debugger will cause the local/field's value to be correctly updated.</span></span> <span data-ttu-id="cb832-106">另外，此问题已在 .NET Framework 4.6 中解决；因此升级到该版本的 Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="cb832-106">Also, this issue has been fixed in the .NET Framework 4.6; upgrading to that version of the Framework should solve the issue.</span></span>

| <span data-ttu-id="cb832-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="cb832-107">Name</span></span>    | <span data-ttu-id="cb832-108">“值”</span><span class="sxs-lookup"><span data-stu-id="cb832-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cb832-109">范围</span><span class="sxs-lookup"><span data-stu-id="cb832-109">Scope</span></span>   |<span data-ttu-id="cb832-110">边缘</span><span class="sxs-lookup"><span data-stu-id="cb832-110">Edge</span></span>|
|<span data-ttu-id="cb832-111">Version</span><span class="sxs-lookup"><span data-stu-id="cb832-111">Version</span></span>|<span data-ttu-id="cb832-112">4.5</span><span class="sxs-lookup"><span data-stu-id="cb832-112">4.5</span></span>|
|<span data-ttu-id="cb832-113">类型</span><span class="sxs-lookup"><span data-stu-id="cb832-113">Type</span></span>|<span data-ttu-id="cb832-114">运行时</span><span class="sxs-lookup"><span data-stu-id="cb832-114">Runtime</span></span>|
