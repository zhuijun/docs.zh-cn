---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621936"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a><span data-ttu-id="04499-101">修复了 ListBox 包含重复值类型时的挂起问题</span><span class="sxs-lookup"><span data-stu-id="04499-101">Fixed a hang when ListBox contains duplicate value-types</span></span>

#### <a name="details"></a><span data-ttu-id="04499-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="04499-102">Details</span></span>

<span data-ttu-id="04499-103">修复了项集合包含重复的值类型对象时，虚拟化 <xref:System.Windows.Controls.ItemsControl> 可能在滚动期间挂起的问题。</span><span class="sxs-lookup"><span data-stu-id="04499-103">Fixed a problem where a virtualizing<xref:System.Windows.Controls.ItemsControl> can hang during scrolling when its Items collection contains duplicate value-typed objects.</span></span>

| <span data-ttu-id="04499-104">“属性”</span><span class="sxs-lookup"><span data-stu-id="04499-104">Name</span></span>    | <span data-ttu-id="04499-105">“值”</span><span class="sxs-lookup"><span data-stu-id="04499-105">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="04499-106">范围</span><span class="sxs-lookup"><span data-stu-id="04499-106">Scope</span></span>   |<span data-ttu-id="04499-107">主要</span><span class="sxs-lookup"><span data-stu-id="04499-107">Major</span></span>|
|<span data-ttu-id="04499-108">Version</span><span class="sxs-lookup"><span data-stu-id="04499-108">Version</span></span>|<span data-ttu-id="04499-109">4.8</span><span class="sxs-lookup"><span data-stu-id="04499-109">4.8</span></span>|
|<span data-ttu-id="04499-110">类型</span><span class="sxs-lookup"><span data-stu-id="04499-110">Type</span></span>|<span data-ttu-id="04499-111">运行时</span><span class="sxs-lookup"><span data-stu-id="04499-111">Runtime</span></span>|
