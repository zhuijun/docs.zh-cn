---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619854"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="78035-101">ObjectContext.Translate 和 ObjectContext.ExecuteStoreQuery 现在支持枚举类型</span><span class="sxs-lookup"><span data-stu-id="78035-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="78035-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="78035-102">Details</span></span>

<span data-ttu-id="78035-103">在 .NET Framework 4.0 中，<code>ObjectContext.Translate</code> 和 <code>ObjectContext.ExecuteStoreQuery</code> 方法的泛型参数 <code>T</code> 不能是枚举类型。</span><span class="sxs-lookup"><span data-stu-id="78035-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="78035-104">现在支持这种情况。</span><span class="sxs-lookup"><span data-stu-id="78035-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="78035-105">建议</span><span class="sxs-lookup"><span data-stu-id="78035-105">Suggestion</span></span>

<span data-ttu-id="78035-106">如果在 .NET Framework 4.0 的枚举类型上调用了 Translate 或 ExecuteStoreQuery，则返回“0”。</span><span class="sxs-lookup"><span data-stu-id="78035-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="78035-107">如果需要该行为，调用应替换为常数 0（或其枚举等效项）。</span><span class="sxs-lookup"><span data-stu-id="78035-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="78035-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="78035-108">Name</span></span>    | <span data-ttu-id="78035-109">“值”</span><span class="sxs-lookup"><span data-stu-id="78035-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="78035-110">范围</span><span class="sxs-lookup"><span data-stu-id="78035-110">Scope</span></span>   |<span data-ttu-id="78035-111">边缘</span><span class="sxs-lookup"><span data-stu-id="78035-111">Edge</span></span>|
|<span data-ttu-id="78035-112">Version</span><span class="sxs-lookup"><span data-stu-id="78035-112">Version</span></span>|<span data-ttu-id="78035-113">4.5</span><span class="sxs-lookup"><span data-stu-id="78035-113">4.5</span></span>|
|<span data-ttu-id="78035-114">类型</span><span class="sxs-lookup"><span data-stu-id="78035-114">Type</span></span>|<span data-ttu-id="78035-115">运行时</span><span class="sxs-lookup"><span data-stu-id="78035-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="78035-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="78035-116">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
