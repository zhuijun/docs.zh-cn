---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617122"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="ab2f4-101">Entity Framework 版本必须与 .NET Framework 版本匹配</span><span class="sxs-lookup"><span data-stu-id="ab2f4-101">Entity Framework version must match the .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="ab2f4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ab2f4-102">Details</span></span>

<span data-ttu-id="ab2f4-103">Entity Framework (EF) 版本应与 .NET Framework 版本匹配。</span><span class="sxs-lookup"><span data-stu-id="ab2f4-103">The Entity Framework (EF) version should be matched with the .NET Framework version.</span></span> <span data-ttu-id="ab2f4-104">Entity Framework 5 推荐用于 .NET Framework 4.5。</span><span class="sxs-lookup"><span data-stu-id="ab2f4-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="ab2f4-105">在与 <xref:System.ComponentModel.DataAnnotations> 相关的 .NET Framework 4.5 项目中，存在一些已知的 EF 4.x 问题。</span><span class="sxs-lookup"><span data-stu-id="ab2f4-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="ab2f4-106">在 .NET Framework 4.5 中，它们被移动到了另一程序集，因此确定要使用的注释时会出现问题。</span><span class="sxs-lookup"><span data-stu-id="ab2f4-106">In .NET Framework 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ab2f4-107">建议</span><span class="sxs-lookup"><span data-stu-id="ab2f4-107">Suggestion</span></span>

<span data-ttu-id="ab2f4-108">对于 .NET Framework 4.5 升级到 Entity Framework 5</span><span class="sxs-lookup"><span data-stu-id="ab2f4-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>

| <span data-ttu-id="ab2f4-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="ab2f4-109">Name</span></span>    | <span data-ttu-id="ab2f4-110">“值”</span><span class="sxs-lookup"><span data-stu-id="ab2f4-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ab2f4-111">范围</span><span class="sxs-lookup"><span data-stu-id="ab2f4-111">Scope</span></span>   | <span data-ttu-id="ab2f4-112">主要</span><span class="sxs-lookup"><span data-stu-id="ab2f4-112">Major</span></span>       |
| <span data-ttu-id="ab2f4-113">Version</span><span class="sxs-lookup"><span data-stu-id="ab2f4-113">Version</span></span> | <span data-ttu-id="ab2f4-114">4.5</span><span class="sxs-lookup"><span data-stu-id="ab2f4-114">4.5</span></span>         |
| <span data-ttu-id="ab2f4-115">类型</span><span class="sxs-lookup"><span data-stu-id="ab2f4-115">Type</span></span>    | <span data-ttu-id="ab2f4-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="ab2f4-116">Retargeting</span></span> |
