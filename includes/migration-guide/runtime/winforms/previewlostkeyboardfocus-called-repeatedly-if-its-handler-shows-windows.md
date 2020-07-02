---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619877"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a><span data-ttu-id="60563-101">如果 PreviewLostKeyboardFocus 的处理程序显示 Windows 窗体消息框，将重复调用它</span><span class="sxs-lookup"><span data-stu-id="60563-101">PreviewLostKeyboardFocus is called repeatedly if its handler shows a Windows Forms message box</span></span>

#### <a name="details"></a><span data-ttu-id="60563-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="60563-102">Details</span></span>

<span data-ttu-id="60563-103">从 .NET Framework 4.5 开始，在消息框关闭时，从 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> 处理程序中调用 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 将重新触发该处理程序，从而可能会导致消息框无限循环出现。</span><span class="sxs-lookup"><span data-stu-id="60563-103">Beginning in the .NET Framework 4.5, calling <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> from a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> handler will cause the handler to re-fire when the message box is closed, potentially resulting in an infinite loop of message boxes.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="60563-104">建议</span><span class="sxs-lookup"><span data-stu-id="60563-104">Suggestion</span></span>

<span data-ttu-id="60563-105">有两种选项可以解决此问题：</span><span class="sxs-lookup"><span data-stu-id="60563-105">There are two options to work around this issue:</span></span><ol><li><span data-ttu-id="60563-106">调用 <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType>（而非 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>）可避免此问题出现。</span><span class="sxs-lookup"><span data-stu-id="60563-106">It may be avoided by calling <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> instead of <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</span></span></li><li><span data-ttu-id="60563-107">在 <xref:System.Windows.UIElement.LostKeyboardFocus> 事件处理程序中显示消息框可避免此问题出现（这与 <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> 事件处理程序的情况不同）。</span><span class="sxs-lookup"><span data-stu-id="60563-107">It may be avoided by showing the message box from a <xref:System.Windows.UIElement.LostKeyboardFocus> event handler (as opposed to a <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> event handler).</span></span></li></ol>

| <span data-ttu-id="60563-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="60563-108">Name</span></span>    | <span data-ttu-id="60563-109">“值”</span><span class="sxs-lookup"><span data-stu-id="60563-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="60563-110">范围</span><span class="sxs-lookup"><span data-stu-id="60563-110">Scope</span></span>   |<span data-ttu-id="60563-111">边缘</span><span class="sxs-lookup"><span data-stu-id="60563-111">Edge</span></span>|
|<span data-ttu-id="60563-112">Version</span><span class="sxs-lookup"><span data-stu-id="60563-112">Version</span></span>|<span data-ttu-id="60563-113">4.5</span><span class="sxs-lookup"><span data-stu-id="60563-113">4.5</span></span>|
|<span data-ttu-id="60563-114">类型</span><span class="sxs-lookup"><span data-stu-id="60563-114">Type</span></span>|<span data-ttu-id="60563-115">运行时</span><span class="sxs-lookup"><span data-stu-id="60563-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="60563-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="60563-116">Affected APIs</span></span>

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|
