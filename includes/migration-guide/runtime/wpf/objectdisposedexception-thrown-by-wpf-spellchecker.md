---
ms.openlocfilehash: 3244913e06a744dafc4440f824ebe6bed25b8dd1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497071"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="9574c-101">WPF 拼写检查器引发的 ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="9574c-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="9574c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9574c-102">Details</span></span>

<span data-ttu-id="9574c-103">应用程序关闭，拼写检查器引发 <xref:System.ObjectDisposedException?displayProperty=fullName>，在这期间，WPF 应用程序有时会出现故障。</span><span class="sxs-lookup"><span data-stu-id="9574c-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="9574c-104">.NET Framework 4.7 WPF 中已通过妥善处理异常解决了此问题，因此确保了应用程序不再受到不良影响。</span><span class="sxs-lookup"><span data-stu-id="9574c-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="9574c-105">应注意，在调试器控制下运行的应用程序中会继续观察到偶尔引发的最可能异常。</span><span class="sxs-lookup"><span data-stu-id="9574c-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9574c-106">建议</span><span class="sxs-lookup"><span data-stu-id="9574c-106">Suggestion</span></span>

<span data-ttu-id="9574c-107">升级到 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9574c-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="9574c-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="9574c-108">Name</span></span>    | <span data-ttu-id="9574c-109">“值”</span><span class="sxs-lookup"><span data-stu-id="9574c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9574c-110">范围</span><span class="sxs-lookup"><span data-stu-id="9574c-110">Scope</span></span>   |<span data-ttu-id="9574c-111">边缘</span><span class="sxs-lookup"><span data-stu-id="9574c-111">Edge</span></span>|
|<span data-ttu-id="9574c-112">Version</span><span class="sxs-lookup"><span data-stu-id="9574c-112">Version</span></span>|<span data-ttu-id="9574c-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="9574c-113">4.6.1</span></span>|
|<span data-ttu-id="9574c-114">类型</span><span class="sxs-lookup"><span data-stu-id="9574c-114">Type</span></span>|<span data-ttu-id="9574c-115">运行时</span><span class="sxs-lookup"><span data-stu-id="9574c-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="9574c-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9574c-116">Affected APIs</span></span>

<span data-ttu-id="9574c-117">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="9574c-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
