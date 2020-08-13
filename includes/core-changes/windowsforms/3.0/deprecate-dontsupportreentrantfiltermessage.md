---
ms.openlocfilehash: 95aa243a5790d4201c7871e617dbe4ccafb7c1a1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556136"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="53ace-101">不支持 DontSupportReentrantFilterMessage 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="53ace-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="53ace-102">已在 .NET Framework 4.6.1 中引入 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 兼容性开关，但它在 .NET Core 和 .NET 5.0 及更高版本上的 Windows 窗体中尚不受支持。</span><span class="sxs-lookup"><span data-stu-id="53ace-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core and .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="53ace-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="53ace-103">Change description</span></span>

<span data-ttu-id="53ace-104">自 .NET Framework 4.6.1 起，`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 兼容性开关可处理通过自定义 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 实现调用 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 消息时可能引发的 <xref:System.IndexOutOfRangeException> 异常。</span><span class="sxs-lookup"><span data-stu-id="53ace-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="53ace-105">有关详细信息，请参阅[缓解：自定义 IMessageFilter.PreFilterMessage 实现](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。</span><span class="sxs-lookup"><span data-stu-id="53ace-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="53ace-106">.NET Core 和 .NET 5.0 及更高版本中尚不支持 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 开关。</span><span class="sxs-lookup"><span data-stu-id="53ace-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="53ace-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="53ace-107">Version introduced</span></span>

<span data-ttu-id="53ace-108">3.0</span><span class="sxs-lookup"><span data-stu-id="53ace-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="53ace-109">建议操作</span><span class="sxs-lookup"><span data-stu-id="53ace-109">Recommended action</span></span>

<span data-ttu-id="53ace-110">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="53ace-110">Remove the switch.</span></span> <span data-ttu-id="53ace-111">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="53ace-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="53ace-112">类别</span><span class="sxs-lookup"><span data-stu-id="53ace-112">Category</span></span>

<span data-ttu-id="53ace-113">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="53ace-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="53ace-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="53ace-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
