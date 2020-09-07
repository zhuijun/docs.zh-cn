---
ms.openlocfilehash: a133c2ea48df11915f8708029c70549e8a1ccefd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497524"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="a8369-101">当 WPF 窗口超出单个显示屏时，会不经剪辑就呈现该窗口</span><span class="sxs-lookup"><span data-stu-id="a8369-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

#### <a name="details"></a><span data-ttu-id="a8369-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a8369-102">Details</span></span>

<span data-ttu-id="a8369-103">在 Windows 8 及更高版本上运行的 .NET Framework 4.6 中，当一个窗口超出多监视器方案中的单个显示屏时，会不经剪辑就呈现整个窗口。</span><span class="sxs-lookup"><span data-stu-id="a8369-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="a8369-104">这与先前版本的 .NET Framework 不同，以前的版本在 WPF 窗口超出单个显示屏时会剪辑该窗口。</span><span class="sxs-lookup"><span data-stu-id="a8369-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a8369-105">建议</span><span class="sxs-lookup"><span data-stu-id="a8369-105">Suggestion</span></span>

<span data-ttu-id="a8369-106">可以使用应用程序的配置文件中的 <code>&lt;appSettings&gt;</code> 的 <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> 元素，或在应用启动时设置 <code>EnableMultiMonitorDisplayClipping</code> 属性，显式设置此行为（无论剪辑与否）。</span><span class="sxs-lookup"><span data-stu-id="a8369-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>

| <span data-ttu-id="a8369-107">名称</span><span class="sxs-lookup"><span data-stu-id="a8369-107">Name</span></span>    | <span data-ttu-id="a8369-108">值</span><span class="sxs-lookup"><span data-stu-id="a8369-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a8369-109">范围</span><span class="sxs-lookup"><span data-stu-id="a8369-109">Scope</span></span>   |<span data-ttu-id="a8369-110">次要</span><span class="sxs-lookup"><span data-stu-id="a8369-110">Minor</span></span>|
|<span data-ttu-id="a8369-111">Version</span><span class="sxs-lookup"><span data-stu-id="a8369-111">Version</span></span>|<span data-ttu-id="a8369-112">4.6</span><span class="sxs-lookup"><span data-stu-id="a8369-112">4.6</span></span>|
|<span data-ttu-id="a8369-113">类型</span><span class="sxs-lookup"><span data-stu-id="a8369-113">Type</span></span>|<span data-ttu-id="a8369-114">运行时</span><span class="sxs-lookup"><span data-stu-id="a8369-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a8369-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a8369-115">Affected APIs</span></span>

<span data-ttu-id="a8369-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="a8369-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
