---
ms.openlocfilehash: b2fcacdb02c411c4dcb12051bf0c6759faccdea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619866"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="7cf8e-101">默认情况下，禁用 OData URL 中的 Replace 方法</span><span class="sxs-lookup"><span data-stu-id="7cf8e-101">The Replace method in OData URLs is disabled by default</span></span>

#### <a name="details"></a><span data-ttu-id="7cf8e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="7cf8e-102">Details</span></span>

<span data-ttu-id="7cf8e-103">从 .NET Framework 4.5 开始，默认会禁用 OData URL 中的 Replace 方法。</span><span class="sxs-lookup"><span data-stu-id="7cf8e-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="7cf8e-104">在禁用 OData Replace 时（现在是默认设置），任何包含 replace 函数的用户请求（这并不常见）都将失败。</span><span class="sxs-lookup"><span data-stu-id="7cf8e-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7cf8e-105">建议</span><span class="sxs-lookup"><span data-stu-id="7cf8e-105">Suggestion</span></span>

<span data-ttu-id="7cf8e-106">如果需要 replace 方法（这并不常见），可通过配置设置 (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>) 重新启用。</span><span class="sxs-lookup"><span data-stu-id="7cf8e-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span></span> <span data-ttu-id="7cf8e-107">但是，启用的 replace 方法可能会带来安全漏洞，应仅在仔细检查后使用。</span><span class="sxs-lookup"><span data-stu-id="7cf8e-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>

| <span data-ttu-id="7cf8e-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="7cf8e-108">Name</span></span>    | <span data-ttu-id="7cf8e-109">“值”</span><span class="sxs-lookup"><span data-stu-id="7cf8e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7cf8e-110">范围</span><span class="sxs-lookup"><span data-stu-id="7cf8e-110">Scope</span></span>   |<span data-ttu-id="7cf8e-111">边缘</span><span class="sxs-lookup"><span data-stu-id="7cf8e-111">Edge</span></span>|
|<span data-ttu-id="7cf8e-112">Version</span><span class="sxs-lookup"><span data-stu-id="7cf8e-112">Version</span></span>|<span data-ttu-id="7cf8e-113">4.5</span><span class="sxs-lookup"><span data-stu-id="7cf8e-113">4.5</span></span>|
|<span data-ttu-id="7cf8e-114">类型</span><span class="sxs-lookup"><span data-stu-id="7cf8e-114">Type</span></span>|<span data-ttu-id="7cf8e-115">运行时</span><span class="sxs-lookup"><span data-stu-id="7cf8e-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7cf8e-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="7cf8e-116">Affected APIs</span></span>

-<xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
