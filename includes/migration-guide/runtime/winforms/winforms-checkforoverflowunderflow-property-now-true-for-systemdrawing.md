---
ms.openlocfilehash: 4cd06fd02fadbaa9f74e40f850e688ee883454ed
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619886"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="73d94-101">对于 System.Drawing，WinForm 的 CheckForOverflowUnderflow 属性现在为 true</span><span class="sxs-lookup"><span data-stu-id="73d94-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

#### <a name="details"></a><span data-ttu-id="73d94-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="73d94-102">Details</span></span>

<span data-ttu-id="73d94-103">System.Drawing.dll 程序集的 CheckForOverflowUnderflow 设置为 true。</span><span class="sxs-lookup"><span data-stu-id="73d94-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="73d94-104">建议</span><span class="sxs-lookup"><span data-stu-id="73d94-104">Suggestion</span></span>

<span data-ttu-id="73d94-105">之前在发生溢出时，结果会在不提示的情况下被截断。</span><span class="sxs-lookup"><span data-stu-id="73d94-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="73d94-106">现在引发了 <xref:System.OverflowException?displayProperty=fullName> 异常。</span><span class="sxs-lookup"><span data-stu-id="73d94-106">Now an <xref:System.OverflowException?displayProperty=fullName> exception is thrown.</span></span>

| <span data-ttu-id="73d94-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="73d94-107">Name</span></span>    | <span data-ttu-id="73d94-108">“值”</span><span class="sxs-lookup"><span data-stu-id="73d94-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="73d94-109">范围</span><span class="sxs-lookup"><span data-stu-id="73d94-109">Scope</span></span>   |<span data-ttu-id="73d94-110">边缘</span><span class="sxs-lookup"><span data-stu-id="73d94-110">Edge</span></span>|
|<span data-ttu-id="73d94-111">Version</span><span class="sxs-lookup"><span data-stu-id="73d94-111">Version</span></span>|<span data-ttu-id="73d94-112">4.5</span><span class="sxs-lookup"><span data-stu-id="73d94-112">4.5</span></span>|
|<span data-ttu-id="73d94-113">类型</span><span class="sxs-lookup"><span data-stu-id="73d94-113">Type</span></span>|<span data-ttu-id="73d94-114">运行时</span><span class="sxs-lookup"><span data-stu-id="73d94-114">Runtime</span></span>|
