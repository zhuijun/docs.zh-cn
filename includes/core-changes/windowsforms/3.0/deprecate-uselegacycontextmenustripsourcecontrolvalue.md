---
ms.openlocfilehash: df6169289fb96df5f7daf8bd58ccaeebc33ad87c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556134"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="2be89-101">不支持 UseLegacyContextMenuStripSourceControlValue 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="2be89-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="2be89-102">已在 .NET Framework 4.7.2 中引入 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 兼容性开关，但它在 .NET Core 或 .NET 5.0 及更高版本上的 Windows 窗体中尚不受支持。</span><span class="sxs-lookup"><span data-stu-id="2be89-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2be89-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="2be89-103">Change description</span></span>

<span data-ttu-id="2be89-104">自 .NET Framework 4.7.2 起，开发人员可使用 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 兼容性开关选择退出 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 属性的新行为 - 新行为是返回对源控件的引用。</span><span class="sxs-lookup"><span data-stu-id="2be89-104">Starting with .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="2be89-105">该属性之前的行为是返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="2be89-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="2be89-106">有关详细信息，请参阅 [\<AppContextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="2be89-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="2be89-107">.NET Core 和 .NET 5.0 及更高版本中尚不支持 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 开关。</span><span class="sxs-lookup"><span data-stu-id="2be89-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2be89-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="2be89-108">Version introduced</span></span>

<span data-ttu-id="2be89-109">3.0</span><span class="sxs-lookup"><span data-stu-id="2be89-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2be89-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="2be89-110">Recommended action</span></span>

<span data-ttu-id="2be89-111">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="2be89-111">Remove the switch.</span></span> <span data-ttu-id="2be89-112">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="2be89-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="2be89-113">类别</span><span class="sxs-lookup"><span data-stu-id="2be89-113">Category</span></span>

<span data-ttu-id="2be89-114">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="2be89-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2be89-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2be89-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
