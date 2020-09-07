---
ms.openlocfilehash: 68b0c4bb032b9744ef585eaef3d68e31afebee24
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496737"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="fa105-101">对于 System.Drawing，WinForm 的 CheckForOverflowUnderflow 属性现在为 true</span><span class="sxs-lookup"><span data-stu-id="fa105-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="fa105-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="fa105-102">Details</span></span>

<span data-ttu-id="fa105-103">System.Drawing.dll 程序集的 CheckForOverflowUnderflow 设置为 true。</span><span class="sxs-lookup"><span data-stu-id="fa105-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fa105-104">建议</span><span class="sxs-lookup"><span data-stu-id="fa105-104">Suggestion</span></span>

<span data-ttu-id="fa105-105">之前在发生溢出时，结果会在不提示的情况下被截断。</span><span class="sxs-lookup"><span data-stu-id="fa105-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="fa105-106">现在引发了 <xref:System.OverflowException?displayProperty=fullName> 异常。</span><span class="sxs-lookup"><span data-stu-id="fa105-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="fa105-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="fa105-107">Name</span></span>    | <span data-ttu-id="fa105-108">“值”</span><span class="sxs-lookup"><span data-stu-id="fa105-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fa105-109">范围</span><span class="sxs-lookup"><span data-stu-id="fa105-109">Scope</span></span>   |<span data-ttu-id="fa105-110">边缘</span><span class="sxs-lookup"><span data-stu-id="fa105-110">Edge</span></span>|
|<span data-ttu-id="fa105-111">Version</span><span class="sxs-lookup"><span data-stu-id="fa105-111">Version</span></span>|<span data-ttu-id="fa105-112">4.5</span><span class="sxs-lookup"><span data-stu-id="fa105-112">4.5</span></span>|
|<span data-ttu-id="fa105-113">类型</span><span class="sxs-lookup"><span data-stu-id="fa105-113">Type</span></span>|<span data-ttu-id="fa105-114">运行时</span><span class="sxs-lookup"><span data-stu-id="fa105-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fa105-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="fa105-115">Affected APIs</span></span>

<span data-ttu-id="fa105-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="fa105-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
