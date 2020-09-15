---
ms.openlocfilehash: 9e70bcd95393a7ff24de43577d26869ce674067b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614416"
---
### <a name="wpf-focusvisual-for-radiobutton-and-checkbox-now-displays-correctly-when-the-controls-have-no-content"></a><span data-ttu-id="d3436-101">RadioButton 和 CheckBox 的 WPF FocusVisual 现可在控件无内容时正确显示</span><span class="sxs-lookup"><span data-stu-id="d3436-101">WPF FocusVisual for RadioButton and CheckBox Now Displays Correctly When The Controls Have No Content</span></span>

#### <a name="details"></a><span data-ttu-id="d3436-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d3436-102">Details</span></span>

<span data-ttu-id="d3436-103">在 .NET Framework 4.7.1 和更早版本中，WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> 不一致且在经典和高对比度主题中具有不正确的焦点视觉对象。</span><span class="sxs-lookup"><span data-stu-id="d3436-103">In the .NET Framework 4.7.1 and earlier versions, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="d3436-104">控件没有内容集时会出现这些问题。</span><span class="sxs-lookup"><span data-stu-id="d3436-104">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="d3436-105">这会使得主题间的转换变得混乱且难以看到焦点视觉对象。</span><span class="sxs-lookup"><span data-stu-id="d3436-105">This can make the transition between themes confusing and the focus visual hard to see.</span></span> <span data-ttu-id="d3436-106">现在，在 .NET Framework 4.7.2 中，主题间的这些视觉对象更加一致，并且在经典和高对比度主题中更轻松可见。</span><span class="sxs-lookup"><span data-stu-id="d3436-106">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d3436-107">建议</span><span class="sxs-lookup"><span data-stu-id="d3436-107">Suggestion</span></span>

<span data-ttu-id="d3436-108">如果开发人员面向 .NET Framework 4.7.2，但要还原到 .NET 4.7.1 行为，则需要设置以下 AppContext 标记。</span><span class="sxs-lookup"><span data-stu-id="d3436-108">A developer targeting .NET Framework 4.7.2 that wants to revert to the behavior in .NET 4.7.1 will need to set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="d3436-109">如果开发人员面向 .NET 4.7.2 以下的框架版本，但想要利用此更改，则必须设置以下 AppContext 标记。请注意，必须正确设置所有标记，并且安装的 .NET Framework 版本必须是 4.7.2 或更高版本。WPF 应用程序需选择启用所有的早期辅助功能改进，才能获取最新改进。</span><span class="sxs-lookup"><span data-stu-id="d3436-109">A developer who wants to utilize this change while targeting a framework version below .NET 4.7.2 must set the following AppContext flags.Note that all the flags must be set appropriately and the installed version of the .NET Framework must be 4.7.2 or greater.WPF applications are required to opt in to all earlier accessibility improvements to get the latest improvements.</span></span> <span data-ttu-id="d3436-110">若要执行此操作，请确保将“Switch.UseLegacyAccessibilityFeatures”和“Switch.UseLegacyAccessibilityFeatures.2”这两个 AppContext 开关设置为 false。</span><span class="sxs-lookup"><span data-stu-id="d3436-110">To do this, ensure that both the AppContext switches 'Switch.UseLegacyAccessibilityFeatures' and 'Switch.UseLegacyAccessibilityFeatures.2' are set to false.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="d3436-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="d3436-111">Name</span></span>    | <span data-ttu-id="d3436-112">“值”</span><span class="sxs-lookup"><span data-stu-id="d3436-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d3436-113">范围</span><span class="sxs-lookup"><span data-stu-id="d3436-113">Scope</span></span>   | <span data-ttu-id="d3436-114">边缘</span><span class="sxs-lookup"><span data-stu-id="d3436-114">Edge</span></span>        |
| <span data-ttu-id="d3436-115">Version</span><span class="sxs-lookup"><span data-stu-id="d3436-115">Version</span></span> | <span data-ttu-id="d3436-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="d3436-116">4.7.2</span></span>       |
| <span data-ttu-id="d3436-117">类型</span><span class="sxs-lookup"><span data-stu-id="d3436-117">Type</span></span>    | <span data-ttu-id="d3436-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="d3436-118">Retargeting</span></span> |
