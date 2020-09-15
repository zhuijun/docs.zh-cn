---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617790"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="c89b4-101">将 SelectionTextBrush 公共属性添加到 TextBox/PasswordBox 非装饰器选择功能</span><span class="sxs-lookup"><span data-stu-id="c89b4-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

#### <a name="details"></a><span data-ttu-id="c89b4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c89b4-102">Details</span></span>

<span data-ttu-id="c89b4-103">在使用 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.PasswordBox> 的[基于非装饰器的文本选择功能](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md)的 WPF 应用程序中，开发人员现在可以设置新添加的 SelectionTextBrush 属性，以便更改所选文本的呈现。</span><span class="sxs-lookup"><span data-stu-id="c89b4-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="c89b4-104">默认情况下，通过 <xref:System.Windows.SystemColors.HighlightTextBrushKey> 更改此颜色。</span><span class="sxs-lookup"><span data-stu-id="c89b4-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="c89b4-105">如果未启用基于非修饰器的文本选择功能，则此属性不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="c89b4-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c89b4-106">建议</span><span class="sxs-lookup"><span data-stu-id="c89b4-106">Suggestion</span></span>

<span data-ttu-id="c89b4-107">启用基于非装饰器的文本选择功能后，可以使用 <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> 属性更改所选文本的外观。</span><span class="sxs-lookup"><span data-stu-id="c89b4-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="c89b4-108">可以使用 XAML 实现此操作：</span><span class="sxs-lookup"><span data-stu-id="c89b4-108">This can be achieved using XAML:</span></span>

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c89b4-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="c89b4-109">Name</span></span>    | <span data-ttu-id="c89b4-110">“值”</span><span class="sxs-lookup"><span data-stu-id="c89b4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c89b4-111">范围</span><span class="sxs-lookup"><span data-stu-id="c89b4-111">Scope</span></span>   | <span data-ttu-id="c89b4-112">主要</span><span class="sxs-lookup"><span data-stu-id="c89b4-112">Major</span></span>       |
| <span data-ttu-id="c89b4-113">Version</span><span class="sxs-lookup"><span data-stu-id="c89b4-113">Version</span></span> | <span data-ttu-id="c89b4-114">4.8</span><span class="sxs-lookup"><span data-stu-id="c89b4-114">4.8</span></span>         |
| <span data-ttu-id="c89b4-115">类型</span><span class="sxs-lookup"><span data-stu-id="c89b4-115">Type</span></span>    | <span data-ttu-id="c89b4-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="c89b4-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c89b4-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c89b4-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [<span data-ttu-id="c89b4-118">System.Windows.Controls.TextBox</span><span class="sxs-lookup"><span data-stu-id="c89b4-118">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)
- [<span data-ttu-id="c89b4-119">System.Windows.Controls.PasswordBox</span><span class="sxs-lookup"><span data-stu-id="c89b4-119">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)
