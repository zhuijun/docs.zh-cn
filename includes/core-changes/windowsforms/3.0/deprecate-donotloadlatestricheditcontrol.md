---
ms.openlocfilehash: e10b5168d59edd56ff549a3a1e3a09d023fe5e28
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556132"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a><span data-ttu-id="d05bb-101">不支持 DoNotLoadLatestRichEditControl 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="d05bb-101">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>

<span data-ttu-id="d05bb-102">已在 .NET Framework 4.7.1 中引入 `Switch.System.Windows.Forms.UseLegacyImages` 兼容性开关，但它在 .NET Core 或 .NET 5.0 及更高版本上的 Windows 窗体中尚不受支持。</span><span class="sxs-lookup"><span data-stu-id="d05bb-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d05bb-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="d05bb-103">Change description</span></span>

<span data-ttu-id="d05bb-104">在 .NET Framework 4.6.2 及更低版本中，<xref:System.Windows.Forms.RichTextBox> 控件会实例化 Win32 RichEdit 控件 v3.0；而对于面向 .NET Framework 4.7.1 的应用程序，<xref:System.Windows.Forms.RichTextBox> 控件会实例化 RichEdit v4.1（位于 msftedit.dll 中）。</span><span class="sxs-lookup"><span data-stu-id="d05bb-104">In .NET Framework 4.6.2 and previous versions, the <xref:System.Windows.Forms.RichTextBox> control instantiates the Win32 RichEdit control v3.0, and for applications that target .NET Framework 4.7.1, the  <xref:System.Windows.Forms.RichTextBox> control instantiates RichEdit v4.1 (in *msftedit.dll*).</span></span> <span data-ttu-id="d05bb-105">已引入 `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 兼容性开关，使面向 .NET Framework 4.7.1 及更高版本的应用程序可选择不使用新的 RichEdit v4.1 控件而改用旧的 RichEdit v3 控件。</span><span class="sxs-lookup"><span data-stu-id="d05bb-105">The `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` compatibility switch was introduced to allow applications that target .NET Framework 4.7.1 and later versions to opt out of the new RichEdit v4.1 control and use the old RichEdit v3 control instead.</span></span>

<span data-ttu-id="d05bb-106">.NET Core 和 .NET 5.0 及更高版本中尚不支持 `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` 开关。</span><span class="sxs-lookup"><span data-stu-id="d05bb-106">In .NET Core and .NET 5.0 and later versions, the `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` switch is not supported.</span></span> <span data-ttu-id="d05bb-107">仅支持 <xref:System.Windows.Forms.RichTextBox> 控件的新版本。</span><span class="sxs-lookup"><span data-stu-id="d05bb-107">Only new versions of the <xref:System.Windows.Forms.RichTextBox> control are supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d05bb-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="d05bb-108">Version introduced</span></span>

<span data-ttu-id="d05bb-109">3.0</span><span class="sxs-lookup"><span data-stu-id="d05bb-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d05bb-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="d05bb-110">Recommended action</span></span>

<span data-ttu-id="d05bb-111">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="d05bb-111">Remove the switch.</span></span> <span data-ttu-id="d05bb-112">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="d05bb-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d05bb-113">类别</span><span class="sxs-lookup"><span data-stu-id="d05bb-113">Category</span></span>

<span data-ttu-id="d05bb-114">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="d05bb-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d05bb-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d05bb-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
