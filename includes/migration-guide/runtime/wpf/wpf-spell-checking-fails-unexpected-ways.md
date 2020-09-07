---
ms.openlocfilehash: d4e60f2a59980263916718ebcc71cc359952c031
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496951"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="d6b09-101">WPF 拼写检查以一种意想不到的方式失败</span><span class="sxs-lookup"><span data-stu-id="d6b09-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="d6b09-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d6b09-102">Details</span></span>

<span data-ttu-id="d6b09-103">这包括 WPF 拼写检查器的诸多问题：</span><span class="sxs-lookup"><span data-stu-id="d6b09-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="d6b09-104">WPF 拼写检查器有时会引发 <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d6b09-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="d6b09-105">当使用“以不同用户身份运行”启动应用程序时，WPF 拼写检查器会无法使用 <xref:System.UnauthorizedAccessException></span><span class="sxs-lookup"><span data-stu-id="d6b09-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="d6b09-106">WPF 拼写检查器在组合词（如德语中的“Hausnummer”）中错误地标出了拼写错误。</span><span class="sxs-lookup"><span data-stu-id="d6b09-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="d6b09-107">建议</span><span class="sxs-lookup"><span data-stu-id="d6b09-107">Suggestion</span></span>

<span data-ttu-id="d6b09-108">问题 #1 - 此问题已在 .NET Framework 4.6.2 中解决 问题 #2 - 当使用“以不同用户身份运行”启动应用程序时，不再支持 WPF 拼写检查器。</span><span class="sxs-lookup"><span data-stu-id="d6b09-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="d6b09-109">从 .NET Framework 4.6.2 开始，以此方式启动的应用程序将不再意外出现故障 - 而是静默禁用 WPF 拼写检查器。</span><span class="sxs-lookup"><span data-stu-id="d6b09-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="d6b09-110">问题 #3 - 此问题已在 .NET Framework 4.6.2 中解决。</span><span class="sxs-lookup"><span data-stu-id="d6b09-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="d6b09-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="d6b09-111">Name</span></span>    | <span data-ttu-id="d6b09-112">“值”</span><span class="sxs-lookup"><span data-stu-id="d6b09-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d6b09-113">范围</span><span class="sxs-lookup"><span data-stu-id="d6b09-113">Scope</span></span>   |<span data-ttu-id="d6b09-114">边缘</span><span class="sxs-lookup"><span data-stu-id="d6b09-114">Edge</span></span>|
|<span data-ttu-id="d6b09-115">Version</span><span class="sxs-lookup"><span data-stu-id="d6b09-115">Version</span></span>|<span data-ttu-id="d6b09-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="d6b09-116">4.6.1</span></span>|
|<span data-ttu-id="d6b09-117">类型</span><span class="sxs-lookup"><span data-stu-id="d6b09-117">Type</span></span>|<span data-ttu-id="d6b09-118">运行时</span><span class="sxs-lookup"><span data-stu-id="d6b09-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d6b09-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d6b09-119">Affected APIs</span></span>

<span data-ttu-id="d6b09-120">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="d6b09-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
