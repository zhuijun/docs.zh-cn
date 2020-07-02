---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619846"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="3dc7a-101">Sql_variant 数据使用 sql_variant 排序规则而不是数据库排序规则</span><span class="sxs-lookup"><span data-stu-id="3dc7a-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="3dc7a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3dc7a-102">Details</span></span>

<span data-ttu-id="3dc7a-103"><code>sql_variant</code> 数据使用 <code>sql_variant</code> 排序规则而不是数据库排序规则。</span><span class="sxs-lookup"><span data-stu-id="3dc7a-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3dc7a-104">建议</span><span class="sxs-lookup"><span data-stu-id="3dc7a-104">Suggestion</span></span>

<span data-ttu-id="3dc7a-105">如果数据库排序规则与 <code>sql_variant</code> 排序规则不同，则此更改将解决可能的数据损坏。</span><span class="sxs-lookup"><span data-stu-id="3dc7a-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="3dc7a-106">依赖损坏的数据的应用程序可能会失败。</span><span class="sxs-lookup"><span data-stu-id="3dc7a-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="3dc7a-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="3dc7a-107">Name</span></span>    | <span data-ttu-id="3dc7a-108">“值”</span><span class="sxs-lookup"><span data-stu-id="3dc7a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3dc7a-109">范围</span><span class="sxs-lookup"><span data-stu-id="3dc7a-109">Scope</span></span>   |<span data-ttu-id="3dc7a-110">透明</span><span class="sxs-lookup"><span data-stu-id="3dc7a-110">Transparent</span></span>|
|<span data-ttu-id="3dc7a-111">Version</span><span class="sxs-lookup"><span data-stu-id="3dc7a-111">Version</span></span>|<span data-ttu-id="3dc7a-112">4.5</span><span class="sxs-lookup"><span data-stu-id="3dc7a-112">4.5</span></span>|
|<span data-ttu-id="3dc7a-113">类型</span><span class="sxs-lookup"><span data-stu-id="3dc7a-113">Type</span></span>|<span data-ttu-id="3dc7a-114">运行时</span><span class="sxs-lookup"><span data-stu-id="3dc7a-114">Runtime</span></span>|
