---
ms.openlocfilehash: fb339fb35cdcbba4f1c860fae9c17162c4cff596
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496801"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="2e013-101">Sql_variant 数据使用 sql_variant 排序规则而不是数据库排序规则</span><span class="sxs-lookup"><span data-stu-id="2e013-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="2e013-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="2e013-102">Details</span></span>

<span data-ttu-id="2e013-103"><code>sql_variant</code> 数据使用 <code>sql_variant</code> 排序规则而不是数据库排序规则。</span><span class="sxs-lookup"><span data-stu-id="2e013-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2e013-104">建议</span><span class="sxs-lookup"><span data-stu-id="2e013-104">Suggestion</span></span>

<span data-ttu-id="2e013-105">如果数据库排序规则与 <code>sql_variant</code> 排序规则不同，则此更改将解决可能的数据损坏。</span><span class="sxs-lookup"><span data-stu-id="2e013-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="2e013-106">依赖损坏的数据的应用程序可能会失败。</span><span class="sxs-lookup"><span data-stu-id="2e013-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="2e013-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="2e013-107">Name</span></span>    | <span data-ttu-id="2e013-108">“值”</span><span class="sxs-lookup"><span data-stu-id="2e013-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2e013-109">范围</span><span class="sxs-lookup"><span data-stu-id="2e013-109">Scope</span></span>   |<span data-ttu-id="2e013-110">透明</span><span class="sxs-lookup"><span data-stu-id="2e013-110">Transparent</span></span>|
|<span data-ttu-id="2e013-111">Version</span><span class="sxs-lookup"><span data-stu-id="2e013-111">Version</span></span>|<span data-ttu-id="2e013-112">4.5</span><span class="sxs-lookup"><span data-stu-id="2e013-112">4.5</span></span>|
|<span data-ttu-id="2e013-113">类型</span><span class="sxs-lookup"><span data-stu-id="2e013-113">Type</span></span>|<span data-ttu-id="2e013-114">运行时</span><span class="sxs-lookup"><span data-stu-id="2e013-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2e013-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2e013-115">Affected APIs</span></span>

<span data-ttu-id="2e013-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="2e013-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
