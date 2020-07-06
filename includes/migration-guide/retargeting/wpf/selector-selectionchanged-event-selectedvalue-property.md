---
ms.openlocfilehash: 0ef39d67cd4335658658f5772b5bce49d827cad0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614410"
---
### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a><span data-ttu-id="85530-101">选择器 SelectionChanged 事件和 SelectedValue 属性</span><span class="sxs-lookup"><span data-stu-id="85530-101">Selector SelectionChanged event and SelectedValue property</span></span>

#### <a name="details"></a><span data-ttu-id="85530-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="85530-102">Details</span></span>

<span data-ttu-id="85530-103">自 .NET Framework 4.7.1 起，在引发 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件之前，<xref:System.Windows.Controls.Primitives.Selector> 始终在选择更改时更新其 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 属性值。</span><span class="sxs-lookup"><span data-stu-id="85530-103">Starting with the .NET Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> always updates the value of its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.</span></span> <span data-ttu-id="85530-104">这使得 SelectedValue 属性与其他选择属性（<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> 和 <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>）一致，这些选择属性在引发事件之前更新。</span><span class="sxs-lookup"><span data-stu-id="85530-104">This makes the SelectedValue property consistent with the other selection properties (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> and <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), which are updated before raising the event.</span></span><p/><span data-ttu-id="85530-105">在 .NET Framework 4.7 和更早版本中，大多数情况下会在事件之前更新 SelectedValue，但如果选择更改是由 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 属性更改引起的，则在事件之后进行更新。</span><span class="sxs-lookup"><span data-stu-id="85530-105">In the .NET Framework 4.7 and earlier versions, the update to SelectedValue happened before the event in most cases, but it happened after the event if the selection change was caused by changing the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="85530-106">建议</span><span class="sxs-lookup"><span data-stu-id="85530-106">Suggestion</span></span>

<span data-ttu-id="85530-107">对于面向 .NET Framework 4.7.1 或更高版本的应用，可以在应用程序配置文件的 `<runtime>` 部分添加以下内容，从而选择弃用此更改并启用旧版行为：</span><span class="sxs-lookup"><span data-stu-id="85530-107">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the `<runtime>` section of the application configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="85530-108">对于面向 .NET Framework 4.7 或更早版本，但在 .NET Framework 4.7.1 或更高版本上运行的应用，可以在应用程序配置文件的 `<runtime>` 部分中添加以下代码行，从而启用新的行为：</span><span class="sxs-lookup"><span data-stu-id="85530-108">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the `<runtime>` section of the application .configuration file:</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="85530-109">名称</span><span class="sxs-lookup"><span data-stu-id="85530-109">Name</span></span>    | <span data-ttu-id="85530-110">“值”</span><span class="sxs-lookup"><span data-stu-id="85530-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85530-111">范围</span><span class="sxs-lookup"><span data-stu-id="85530-111">Scope</span></span>   | <span data-ttu-id="85530-112">次要</span><span class="sxs-lookup"><span data-stu-id="85530-112">Minor</span></span>       |
| <span data-ttu-id="85530-113">Version</span><span class="sxs-lookup"><span data-stu-id="85530-113">Version</span></span> | <span data-ttu-id="85530-114">4.7.1</span><span class="sxs-lookup"><span data-stu-id="85530-114">4.7.1</span></span>       |
| <span data-ttu-id="85530-115">类型</span><span class="sxs-lookup"><span data-stu-id="85530-115">Type</span></span>    | <span data-ttu-id="85530-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="85530-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="85530-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="85530-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType>
