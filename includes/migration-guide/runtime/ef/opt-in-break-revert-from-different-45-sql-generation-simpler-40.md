---
ms.openlocfilehash: 346fb6ecd43f7f93529e45f169c79b7acacc9c1f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496450"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="e2a7d-101">选择中断以从不同的 4.5 SQL 生成还原到更简单的 4.0 SQL 生成</span><span class="sxs-lookup"><span data-stu-id="e2a7d-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

#### <a name="details"></a><span data-ttu-id="e2a7d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e2a7d-102">Details</span></span>

<span data-ttu-id="e2a7d-103">生成 JOIN 语句并包含对限制操作的调用（无需先使用 OrderBy）的查询现在可以生成更简单的 SQL。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="e2a7d-104">升级到 .NET Framework 4.5 后，这些查询生成了比以前版本更复杂的 SQL。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e2a7d-105">建议</span><span class="sxs-lookup"><span data-stu-id="e2a7d-105">Suggestion</span></span>

<span data-ttu-id="e2a7d-106">在默认情况下，禁用此功能。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-106">This feature is disabled by default.</span></span> <span data-ttu-id="e2a7d-107">如果实体框架生成可导致性能降低的额外 JOIN 语句，则可以通过将以下项添加到应用程序配置 (app.config) 文件的 <code>&lt;appSettings&gt;</code> 部分来启用此功能：</span><span class="sxs-lookup"><span data-stu-id="e2a7d-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e2a7d-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="e2a7d-108">Name</span></span>    | <span data-ttu-id="e2a7d-109">“值”</span><span class="sxs-lookup"><span data-stu-id="e2a7d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e2a7d-110">范围</span><span class="sxs-lookup"><span data-stu-id="e2a7d-110">Scope</span></span>   |<span data-ttu-id="e2a7d-111">透明</span><span class="sxs-lookup"><span data-stu-id="e2a7d-111">Transparent</span></span>|
|<span data-ttu-id="e2a7d-112">Version</span><span class="sxs-lookup"><span data-stu-id="e2a7d-112">Version</span></span>|<span data-ttu-id="e2a7d-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="e2a7d-113">4.5.2</span></span>|
|<span data-ttu-id="e2a7d-114">类型</span><span class="sxs-lookup"><span data-stu-id="e2a7d-114">Type</span></span>|<span data-ttu-id="e2a7d-115">运行时</span><span class="sxs-lookup"><span data-stu-id="e2a7d-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e2a7d-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e2a7d-116">Affected APIs</span></span>

<span data-ttu-id="e2a7d-117">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="e2a7d-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
