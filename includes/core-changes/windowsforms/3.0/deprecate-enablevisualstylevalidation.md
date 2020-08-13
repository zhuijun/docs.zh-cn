---
ms.openlocfilehash: 196a26bd235e5e2556baa7fac979b3316ff81e1f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556130"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="de8d9-101">不支持 EnableVisualStyleValidation 兼容性开关</span><span class="sxs-lookup"><span data-stu-id="de8d9-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="de8d9-102">.NET Core 或 .NET 5.0 及更高版本上的 Windows 窗体不支持 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 兼容性开关。</span><span class="sxs-lookup"><span data-stu-id="de8d9-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="de8d9-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="de8d9-103">Change description</span></span>

<span data-ttu-id="de8d9-104">在 .NET Framework 中，`Switch.System.Windows.Forms.EnableVisualStyleValidation` 兼容性开关使得应用程序可选择不验证以数值格式提供的视觉样式。</span><span class="sxs-lookup"><span data-stu-id="de8d9-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="de8d9-105">.NET Core 和 .NET 5.0 及更高版本中尚不支持 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 开关。</span><span class="sxs-lookup"><span data-stu-id="de8d9-105">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="de8d9-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="de8d9-106">Version introduced</span></span>

<span data-ttu-id="de8d9-107">3.0</span><span class="sxs-lookup"><span data-stu-id="de8d9-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="de8d9-108">建议操作</span><span class="sxs-lookup"><span data-stu-id="de8d9-108">Recommended action</span></span>

<span data-ttu-id="de8d9-109">删除此开关。</span><span class="sxs-lookup"><span data-stu-id="de8d9-109">Remove the switch.</span></span> <span data-ttu-id="de8d9-110">此开关不受支持，且未提供替代功能。</span><span class="sxs-lookup"><span data-stu-id="de8d9-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="de8d9-111">类别</span><span class="sxs-lookup"><span data-stu-id="de8d9-111">Category</span></span>

<span data-ttu-id="de8d9-112">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="de8d9-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="de8d9-113">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="de8d9-113">Affected APIs</span></span>

- <span data-ttu-id="de8d9-114">无</span><span class="sxs-lookup"><span data-stu-id="de8d9-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
