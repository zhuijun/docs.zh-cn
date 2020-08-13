---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556133"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="eece3-101">不支持 AllowUpdateChildControlIndexForTabControls 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="eece3-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="eece3-102">`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 兼容性开关在 .NET Framework 4.6 及更高版本上的 Windows 窗体中受支持，但在自 .NET Core 或 .NET 5.0 及更高版本中不受支持。</span><span class="sxs-lookup"><span data-stu-id="eece3-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eece3-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="eece3-103">Change description</span></span>

<span data-ttu-id="eece3-104">在 .NET Framework 4.6 及更高版本中，选中选项卡会对其控件集合重新排序。</span><span class="sxs-lookup"><span data-stu-id="eece3-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="eece3-105">借助 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 兼容性开关，应用程序可在不需要此类重新排序时跳过此行为。</span><span class="sxs-lookup"><span data-stu-id="eece3-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="eece3-106">.NET Core 和 .NET 5.0 及更高版本中尚不支持 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 开关。</span><span class="sxs-lookup"><span data-stu-id="eece3-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eece3-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="eece3-107">Version introduced</span></span>

<span data-ttu-id="eece3-108">3.0</span><span class="sxs-lookup"><span data-stu-id="eece3-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eece3-109">建议操作</span><span class="sxs-lookup"><span data-stu-id="eece3-109">Recommended action</span></span>

<span data-ttu-id="eece3-110">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="eece3-110">Remove the switch.</span></span> <span data-ttu-id="eece3-111">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="eece3-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="eece3-112">类别</span><span class="sxs-lookup"><span data-stu-id="eece3-112">Category</span></span>

<span data-ttu-id="eece3-113">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="eece3-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eece3-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="eece3-114">Affected APIs</span></span>

- <span data-ttu-id="eece3-115">无</span><span class="sxs-lookup"><span data-stu-id="eece3-115">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
