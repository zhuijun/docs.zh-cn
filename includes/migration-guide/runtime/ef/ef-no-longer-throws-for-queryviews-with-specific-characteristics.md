---
ms.openlocfilehash: ceae6b85c14862b1b1183d01def0dda723ee0c2b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497517"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="2e2c9-101">EF 将不再引发有特定特征的 QueryViews</span><span class="sxs-lookup"><span data-stu-id="2e2c9-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="2e2c9-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="2e2c9-102">Details</span></span>

<span data-ttu-id="2e2c9-103">当应用执行涉及到带有 0..1 导航属性（此属性尝试将相关实体包含为查询的一部分）的查询时，Entity Framework 将不再引发 <xref:System.StackOverflowException?displayProperty=fullName> 异常。</span><span class="sxs-lookup"><span data-stu-id="2e2c9-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="2e2c9-104">例如，通过调用 <code>.Include(e =&gt; e.RelatedNavProp)</code>。</span><span class="sxs-lookup"><span data-stu-id="2e2c9-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2e2c9-105">建议</span><span class="sxs-lookup"><span data-stu-id="2e2c9-105">Suggestion</span></span>

<span data-ttu-id="2e2c9-106">在运行调用 .Include 的查询时，此更改仅影响使用带有 1-0..1 关系的 QueryViews 的代码。</span><span class="sxs-lookup"><span data-stu-id="2e2c9-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="2e2c9-107">它可以改善可靠性，并且应该几乎对所有应用透明。</span><span class="sxs-lookup"><span data-stu-id="2e2c9-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="2e2c9-108">但是，如果它导致意外的行为，你可以通过将以下项添加到应用配置文件的 <code>&lt;appSettings&gt;</code> 部分来禁用它：</span><span class="sxs-lookup"><span data-stu-id="2e2c9-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2e2c9-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="2e2c9-109">Name</span></span>    | <span data-ttu-id="2e2c9-110">“值”</span><span class="sxs-lookup"><span data-stu-id="2e2c9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2e2c9-111">范围</span><span class="sxs-lookup"><span data-stu-id="2e2c9-111">Scope</span></span>   |<span data-ttu-id="2e2c9-112">边缘</span><span class="sxs-lookup"><span data-stu-id="2e2c9-112">Edge</span></span>|
|<span data-ttu-id="2e2c9-113">Version</span><span class="sxs-lookup"><span data-stu-id="2e2c9-113">Version</span></span>|<span data-ttu-id="2e2c9-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="2e2c9-114">4.5.2</span></span>|
|<span data-ttu-id="2e2c9-115">类型</span><span class="sxs-lookup"><span data-stu-id="2e2c9-115">Type</span></span>|<span data-ttu-id="2e2c9-116">运行时</span><span class="sxs-lookup"><span data-stu-id="2e2c9-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2e2c9-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2e2c9-117">Affected APIs</span></span>

<span data-ttu-id="2e2c9-118">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="2e2c9-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
