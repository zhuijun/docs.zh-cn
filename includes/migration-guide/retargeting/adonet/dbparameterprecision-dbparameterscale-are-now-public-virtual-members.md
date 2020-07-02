---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616028"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="af3f5-101">DbParameter.Precision 和 DbParameter.Scale 现在是公共虚拟成员</span><span class="sxs-lookup"><span data-stu-id="af3f5-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

#### <a name="details"></a><span data-ttu-id="af3f5-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="af3f5-102">Details</span></span>

<span data-ttu-id="af3f5-103">实现 <xref:System.Data.Common.DbParameter.Precision> 和 <xref:System.Data.Common.DbParameter.Scale> 将实现为公共虚拟属性。</span><span class="sxs-lookup"><span data-stu-id="af3f5-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="af3f5-104">它们替换相应的显示接口实现、<xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> 和 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>。</span><span class="sxs-lookup"><span data-stu-id="af3f5-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="af3f5-105">建议</span><span class="sxs-lookup"><span data-stu-id="af3f5-105">Suggestion</span></span>

<span data-ttu-id="af3f5-106">在重新生成 ADO.NET 数据库提供程序时，这些差异要求将“override”关键字应用到 Precision 和 Scale 属性。</span><span class="sxs-lookup"><span data-stu-id="af3f5-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="af3f5-107">仅在重新生成组件时才需要这样做；现有二进制文件将继续运行。</span><span class="sxs-lookup"><span data-stu-id="af3f5-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>

| <span data-ttu-id="af3f5-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="af3f5-108">Name</span></span>    | <span data-ttu-id="af3f5-109">“值”</span><span class="sxs-lookup"><span data-stu-id="af3f5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="af3f5-110">范围</span><span class="sxs-lookup"><span data-stu-id="af3f5-110">Scope</span></span>   | <span data-ttu-id="af3f5-111">次要</span><span class="sxs-lookup"><span data-stu-id="af3f5-111">Minor</span></span>       |
| <span data-ttu-id="af3f5-112">Version</span><span class="sxs-lookup"><span data-stu-id="af3f5-112">Version</span></span> | <span data-ttu-id="af3f5-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="af3f5-113">4.5.1</span></span>       |
| <span data-ttu-id="af3f5-114">类型</span><span class="sxs-lookup"><span data-stu-id="af3f5-114">Type</span></span>    | <span data-ttu-id="af3f5-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="af3f5-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="af3f5-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="af3f5-116">Affected APIs</span></span>

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
