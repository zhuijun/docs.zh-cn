---
ms.openlocfilehash: dfdb62e8dd6db67d4fd12aba93928f4615e3f284
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614412"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a><span data-ttu-id="4cdb6-101">TabControl SelectionChanged 事件和 SelectedContent 属性</span><span class="sxs-lookup"><span data-stu-id="4cdb6-101">TabControl SelectionChanged event and SelectedContent property</span></span>

#### <a name="details"></a><span data-ttu-id="4cdb6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4cdb6-102">Details</span></span>

<span data-ttu-id="4cdb6-103">从 .NET Framework 4.7.1 开始，当选择发生变化时，<xref:System.Windows.Controls.TabControl> 在引发 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件之前更新其 <xref:System.Windows.Controls.TabControl.SelectedContent> 属性的值。而在 .NET Framework 4.7 和更早版本中，在事件发生之后才更新到 SelectedContent。</span><span class="sxs-lookup"><span data-stu-id="4cdb6-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.TabControl> updates the value of its <xref:System.Windows.Controls.TabControl.SelectedContent> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.In the .NET Framework 4.7 and earlier versions, the update to SelectedContent happened after the event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4cdb6-104">建议</span><span class="sxs-lookup"><span data-stu-id="4cdb6-104">Suggestion</span></span>

<span data-ttu-id="4cdb6-105">对于面向 .NET Framework 4.7.1 或更高版本的应用，可以在应用程序配置文件的 `<runtime>` 部分添加以下内容，从而选择弃用此更改并启用旧版行为：</span><span class="sxs-lookup"><span data-stu-id="4cdb6-105">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="4cdb6-106">对于面向 .NET Framework 4.7 或更早版本，但在 .NET Framework 4.7.1 或更高版本上运行的应用，可以在应用程序配置文件的 `<runtime>` 部分中添加以下代码行，从而启用新的行为：</span><span class="sxs-lookup"><span data-stu-id="4cdb6-106">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="4cdb6-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="4cdb6-107">Name</span></span>    | <span data-ttu-id="4cdb6-108">“值”</span><span class="sxs-lookup"><span data-stu-id="4cdb6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4cdb6-109">范围</span><span class="sxs-lookup"><span data-stu-id="4cdb6-109">Scope</span></span>   | <span data-ttu-id="4cdb6-110">次要</span><span class="sxs-lookup"><span data-stu-id="4cdb6-110">Minor</span></span>       |
| <span data-ttu-id="4cdb6-111">Version</span><span class="sxs-lookup"><span data-stu-id="4cdb6-111">Version</span></span> | <span data-ttu-id="4cdb6-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="4cdb6-112">4.7.1</span></span>       |
| <span data-ttu-id="4cdb6-113">类型</span><span class="sxs-lookup"><span data-stu-id="4cdb6-113">Type</span></span>    | <span data-ttu-id="4cdb6-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="4cdb6-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4cdb6-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="4cdb6-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
