---
ms.openlocfilehash: 3fb8807a9b6f0bb0d2bc746f5e89eaa8a81d6aa8
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556137"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a><span data-ttu-id="c2e87-101">不支持 DoNotSupportSelectAllShortcutInMultilineTextBox 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="c2e87-101">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>

<span data-ttu-id="c2e87-102">已在 .NET Framework 4.6.1 中引入 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 兼容性开关，但它在 .NET Core 和 .NET 5.0 及更高版本上的 Windows 窗体中尚不受支持。</span><span class="sxs-lookup"><span data-stu-id="c2e87-102">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c2e87-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="c2e87-103">Change description</span></span>

<span data-ttu-id="c2e87-104">自 .NET Framework 4.6.1 起，在 <xref:System.Windows.Forms.TextBox> 控件中选择 <kbd>Ctrl</kbd> + <kbd>A</kbd> 快捷键会选中所有文本。</span><span class="sxs-lookup"><span data-stu-id="c2e87-104">Starting with .NET Framework 4.6.1, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key in a <xref:System.Windows.Forms.TextBox> control selected all text.</span></span> <span data-ttu-id="c2e87-105">在 .NET Framework 4.6 及更低版本中，如果 [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) 和 <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> 属性都设置为 `true`，则选择 <kbd>Ctrl</kbd> + <kbd>A</kbd> 快捷键没法选中全部文本。</span><span class="sxs-lookup"><span data-stu-id="c2e87-105">In .NET Framework 4.6 and previous versions, selecting the <kbd>Ctrl</kbd> + <kbd>A</kbd> shortcut key failed to select all text if the [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) and <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> properties were both set to `true`.</span></span> <span data-ttu-id="c2e87-106">为保留原始行为，已在 .NET Framework 4.6.1 中引入 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 兼容性开关。</span><span class="sxs-lookup"><span data-stu-id="c2e87-106">The `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` compatibility switch was introduced in .NET Framework 4.6.1 to retain the original behavior.</span></span> <span data-ttu-id="c2e87-107">有关更多信息，请参见<xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c2e87-107">For more information see <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c2e87-108">.NET Core 和 .NET 5.0 及更高版本中尚不支持 `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` 开关。</span><span class="sxs-lookup"><span data-stu-id="c2e87-108">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c2e87-109">引入的版本</span><span class="sxs-lookup"><span data-stu-id="c2e87-109">Version introduced</span></span>

<span data-ttu-id="c2e87-110">3.0</span><span class="sxs-lookup"><span data-stu-id="c2e87-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c2e87-111">建议操作</span><span class="sxs-lookup"><span data-stu-id="c2e87-111">Recommended action</span></span>

<span data-ttu-id="c2e87-112">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="c2e87-112">Remove the switch.</span></span> <span data-ttu-id="c2e87-113">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="c2e87-113">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="c2e87-114">类别</span><span class="sxs-lookup"><span data-stu-id="c2e87-114">Category</span></span>

<span data-ttu-id="c2e87-115">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="c2e87-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c2e87-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c2e87-116">Affected APIs</span></span>

- <span data-ttu-id="c2e87-117">None</span><span class="sxs-lookup"><span data-stu-id="c2e87-117">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
