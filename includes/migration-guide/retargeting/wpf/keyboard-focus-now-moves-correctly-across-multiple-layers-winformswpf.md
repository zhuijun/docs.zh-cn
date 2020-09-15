---
ms.openlocfilehash: a82b720fd4e771481ea1142a88a095443afa0d5b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614411"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a><span data-ttu-id="8f107-101">现在，键盘焦点可在 WinForms/WPF 承载的多个层之间正确移动</span><span class="sxs-lookup"><span data-stu-id="8f107-101">Keyboard focus now moves correctly across multiple layers of WinForms/WPF hosting</span></span>

#### <a name="details"></a><span data-ttu-id="8f107-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="8f107-102">Details</span></span>

<span data-ttu-id="8f107-103">请考虑 WPF 应用程序，其承载的 WinForms 控件会反过来承载 WPF 控件。</span><span class="sxs-lookup"><span data-stu-id="8f107-103">Consider a WPF application hosting a WinForms control which in turn hosts WPF controls.</span></span> <span data-ttu-id="8f107-104">如果该层的第一个或最后一个控件是 WPF `System.Windows.Forms.Integration.ElementHost`，那么用户可能不能按 Tab 离开 WinForms 层。</span><span class="sxs-lookup"><span data-stu-id="8f107-104">Users may not be able to tab out of the WinForms layer if the first or last control in that layer is the WPF `System.Windows.Forms.Integration.ElementHost`.</span></span> <span data-ttu-id="8f107-105">此更改修复了这个问题，现在，用户能按 Tab 离开 WinForms layer.Automated 应用程序。这些应用程序依赖于绝不转义 WinForms 层的焦点可能不再按预期工作。</span><span class="sxs-lookup"><span data-stu-id="8f107-105">This change fixes this issue, and users are now able to tab out of the WinForms layer.Automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8f107-106">建议</span><span class="sxs-lookup"><span data-stu-id="8f107-106">Suggestion</span></span>

<span data-ttu-id="8f107-107">如果开发人员想要利用此更改，但面向 .NET 4.7.2 以下的框架版本，他可将下列一组 AppContext 标记设置为 false，从而启用更改。</span><span class="sxs-lookup"><span data-stu-id="8f107-107">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 can set the following set of AppContext flags to false for the change to be enabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="8f107-108">WPF 应用程序必须选择启用所有早期的可访问性改进，才能使用之后的改进。</span><span class="sxs-lookup"><span data-stu-id="8f107-108">WPF applications must opt in to all early accessibility improvements to get the later improvements.</span></span> <span data-ttu-id="8f107-109">换言之，必须同时设置 `Switch.UseLegacyAccessibilityFeatures` 和 `Switch.UseLegacyAccessibilityFeatures.2` 开关。如果开发人员需要以前的功能，且面向 .NET 4.7.2 或更高版本，他可将以下 AppContext 标记设置为 false，从而禁用更改。</span><span class="sxs-lookup"><span data-stu-id="8f107-109">In other words, both the `Switch.UseLegacyAccessibilityFeatures` and the `Switch.UseLegacyAccessibilityFeatures.2` switches must be setA developer who requires the previous functionality while targeting .NET 4.7.2 or greater can set the following AppContext flag to true for the change to be disabled.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="8f107-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="8f107-110">Name</span></span>    | <span data-ttu-id="8f107-111">“值”</span><span class="sxs-lookup"><span data-stu-id="8f107-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8f107-112">范围</span><span class="sxs-lookup"><span data-stu-id="8f107-112">Scope</span></span>   | <span data-ttu-id="8f107-113">边缘</span><span class="sxs-lookup"><span data-stu-id="8f107-113">Edge</span></span>        |
| <span data-ttu-id="8f107-114">Version</span><span class="sxs-lookup"><span data-stu-id="8f107-114">Version</span></span> | <span data-ttu-id="8f107-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="8f107-115">4.7.2</span></span>       |
| <span data-ttu-id="8f107-116">类型</span><span class="sxs-lookup"><span data-stu-id="8f107-116">Type</span></span>    | <span data-ttu-id="8f107-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="8f107-117">Retargeting</span></span> |
