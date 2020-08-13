---
ms.openlocfilehash: d69f619522c7abc3171f1c089e53cc2754899f93
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556131"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="4fb08-101">不支持 UseLegacyImages 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="4fb08-101">UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="4fb08-102">已在 .NET Framework 4.8 中引入 `Switch.System.Windows.Forms.UseLegacyImages` 兼容性开关，但它在 .NET Core 或 .NET 5.0 及更高版本上的 Windows 窗体中尚不受支持。</span><span class="sxs-lookup"><span data-stu-id="4fb08-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4fb08-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="4fb08-103">Change description</span></span>

<span data-ttu-id="4fb08-104">自 .NET Framework 4.8 起，`Switch.System.Windows.Forms.UseLegacyImages` 兼容性开关会处理高 DPI 环境中 ClickOnce 方案内可能出现的图像缩放问题。</span><span class="sxs-lookup"><span data-stu-id="4fb08-104">Starting with .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="4fb08-105">如果设置为 `true`，则用户可通过此开关在缩放比例设置为大于 100% 的高 DPI 显示器上还原旧的图像缩放行为。</span><span class="sxs-lookup"><span data-stu-id="4fb08-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="4fb08-106">有关详细信息，请参阅 GitHub 上的 [.NET Framework 4.8 发行说明](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)。</span><span class="sxs-lookup"><span data-stu-id="4fb08-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="4fb08-107">.NET Core 和 .NET 5.0 及更高版本中尚不支持 `Switch.System.Windows.Forms.UseLegacyImages` 开关。</span><span class="sxs-lookup"><span data-stu-id="4fb08-107">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4fb08-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="4fb08-108">Version introduced</span></span>

<span data-ttu-id="4fb08-109">3.0</span><span class="sxs-lookup"><span data-stu-id="4fb08-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4fb08-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="4fb08-110">Recommended action</span></span>

<span data-ttu-id="4fb08-111">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="4fb08-111">Remove the switch.</span></span> <span data-ttu-id="4fb08-112">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="4fb08-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="4fb08-113">类别</span><span class="sxs-lookup"><span data-stu-id="4fb08-113">Category</span></span>

<span data-ttu-id="4fb08-114">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="4fb08-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4fb08-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="4fb08-115">Affected APIs</span></span>

- <span data-ttu-id="4fb08-116">无</span><span class="sxs-lookup"><span data-stu-id="4fb08-116">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
