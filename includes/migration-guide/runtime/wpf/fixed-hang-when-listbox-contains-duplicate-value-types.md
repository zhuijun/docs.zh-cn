---
ms.openlocfilehash: 7637c2d96aef93b4cf8f2314c1dd1edba51d553c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497151"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a><span data-ttu-id="27f7e-101">修复了 ListBox 包含重复值类型时的挂起问题</span><span class="sxs-lookup"><span data-stu-id="27f7e-101">Fixed a hang when ListBox contains duplicate value-types</span></span>

#### <a name="details"></a><span data-ttu-id="27f7e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="27f7e-102">Details</span></span>

<span data-ttu-id="27f7e-103">修复了项集合包含重复的值类型对象时，虚拟化 <xref:System.Windows.Controls.ItemsControl> 可能在滚动期间挂起的问题。</span><span class="sxs-lookup"><span data-stu-id="27f7e-103">Fixed a problem where a virtualizing<xref:System.Windows.Controls.ItemsControl> can hang during scrolling when its Items collection contains duplicate value-typed objects.</span></span>

| <span data-ttu-id="27f7e-104">“属性”</span><span class="sxs-lookup"><span data-stu-id="27f7e-104">Name</span></span>    | <span data-ttu-id="27f7e-105">“值”</span><span class="sxs-lookup"><span data-stu-id="27f7e-105">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="27f7e-106">范围</span><span class="sxs-lookup"><span data-stu-id="27f7e-106">Scope</span></span>   |<span data-ttu-id="27f7e-107">主要</span><span class="sxs-lookup"><span data-stu-id="27f7e-107">Major</span></span>|
|<span data-ttu-id="27f7e-108">Version</span><span class="sxs-lookup"><span data-stu-id="27f7e-108">Version</span></span>|<span data-ttu-id="27f7e-109">4.8</span><span class="sxs-lookup"><span data-stu-id="27f7e-109">4.8</span></span>|
|<span data-ttu-id="27f7e-110">类型</span><span class="sxs-lookup"><span data-stu-id="27f7e-110">Type</span></span>|<span data-ttu-id="27f7e-111">运行时</span><span class="sxs-lookup"><span data-stu-id="27f7e-111">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="27f7e-112">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="27f7e-112">Affected APIs</span></span>

<span data-ttu-id="27f7e-113">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="27f7e-113">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
