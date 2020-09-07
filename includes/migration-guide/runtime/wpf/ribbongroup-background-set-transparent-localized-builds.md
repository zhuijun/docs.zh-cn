---
ms.openlocfilehash: d6405573e476ce18513938b500041adefbeeef1b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497087"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="2ed3e-101">本地化版本中的 RibbonGroup 背景设置为透明</span><span class="sxs-lookup"><span data-stu-id="2ed3e-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="2ed3e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="2ed3e-102">Details</span></span>

<span data-ttu-id="2ed3e-103">始终用透明画笔绘制本地化版本上的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 背景，导致 UI 体验不佳。</span><span class="sxs-lookup"><span data-stu-id="2ed3e-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="2ed3e-104">.NET Framework 4.7 WPF 修复中通过更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 本地化资源修复了此问题，因而又确保会选中正确的画笔。</span><span class="sxs-lookup"><span data-stu-id="2ed3e-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2ed3e-105">建议</span><span class="sxs-lookup"><span data-stu-id="2ed3e-105">Suggestion</span></span>

<span data-ttu-id="2ed3e-106">升级到 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="2ed3e-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="2ed3e-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="2ed3e-107">Name</span></span>    | <span data-ttu-id="2ed3e-108">值</span><span class="sxs-lookup"><span data-stu-id="2ed3e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2ed3e-109">范围</span><span class="sxs-lookup"><span data-stu-id="2ed3e-109">Scope</span></span>   |<span data-ttu-id="2ed3e-110">边缘</span><span class="sxs-lookup"><span data-stu-id="2ed3e-110">Edge</span></span>|
|<span data-ttu-id="2ed3e-111">Version</span><span class="sxs-lookup"><span data-stu-id="2ed3e-111">Version</span></span>|<span data-ttu-id="2ed3e-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="2ed3e-112">4.6.2</span></span>|
|<span data-ttu-id="2ed3e-113">类型</span><span class="sxs-lookup"><span data-stu-id="2ed3e-113">Type</span></span>|<span data-ttu-id="2ed3e-114">运行时</span><span class="sxs-lookup"><span data-stu-id="2ed3e-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2ed3e-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2ed3e-115">Affected APIs</span></span>

<span data-ttu-id="2ed3e-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="2ed3e-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
