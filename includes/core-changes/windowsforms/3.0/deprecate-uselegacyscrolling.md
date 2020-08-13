---
ms.openlocfilehash: ee4a27dde9f1e7756401e3d8b709514082f5d3b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556135"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="a3452-101">不支持 DomainUpDown.UseLegacyScrolling 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="a3452-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="a3452-102">已在 .NET Framework 4.7.1 中引入 `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 兼容性开关，但它在 .NET Core 或 .NET 5.0 及更高版本上的 Windows 窗体中尚不受支持。</span><span class="sxs-lookup"><span data-stu-id="a3452-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a3452-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="a3452-103">Change description</span></span>

<span data-ttu-id="a3452-104">自 .NET Framework 4.7.1 起，开发人员可使用 `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 兼容性开关选择不执行独立 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作。</span><span class="sxs-lookup"><span data-stu-id="a3452-104">Starting with .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="a3452-105">该开关会还原旧行为，也就是说如果存在上下文文本，则忽略 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>而且开发人员需要先在控件上执行 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 操作，然后才能执行 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作。</span><span class="sxs-lookup"><span data-stu-id="a3452-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="a3452-106">有关详细信息，请参阅 [\<AppContextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。</span><span class="sxs-lookup"><span data-stu-id="a3452-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="a3452-107">.NET Core 和 .NET 5.0 及更高版本中尚不支持 `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 开关。</span><span class="sxs-lookup"><span data-stu-id="a3452-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a3452-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="a3452-108">Version introduced</span></span>

<span data-ttu-id="a3452-109">3.0</span><span class="sxs-lookup"><span data-stu-id="a3452-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a3452-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="a3452-110">Recommended action</span></span>

<span data-ttu-id="a3452-111">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="a3452-111">Remove the switch.</span></span> <span data-ttu-id="a3452-112">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="a3452-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="a3452-113">类别</span><span class="sxs-lookup"><span data-stu-id="a3452-113">Category</span></span>

<span data-ttu-id="a3452-114">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="a3452-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a3452-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a3452-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
