---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859274"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="76d51-101">路径冒号检查更严格</span><span class="sxs-lookup"><span data-stu-id="76d51-101">Path colon checks are stricter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="76d51-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="76d51-102">Details</span></span>|<span data-ttu-id="76d51-103">在 .NET Framework 4.6.2 中，为了支持以前不受支持的路径，进行了大量更改（无论是在长度方面还是在格式方面）。</span><span class="sxs-lookup"><span data-stu-id="76d51-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="76d51-104">检查正确的驱动器分隔符（冒号）语法变得更加严格，这样做的副作用是阻止了少量特选路径 API 中的某些 URI 路径，这些曾经是可以容忍的。</span><span class="sxs-lookup"><span data-stu-id="76d51-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>|
|<span data-ttu-id="76d51-105">建议</span><span class="sxs-lookup"><span data-stu-id="76d51-105">Suggestion</span></span>|<span data-ttu-id="76d51-106">如果将 URI 传递给受影响的 API，请首先将该字符串修改为合法路径。</span><span class="sxs-lookup"><span data-stu-id="76d51-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="76d51-107">手动从 URL 中删除该方案（例如，从 URL 中删除 <code>file://</code>）</span><span class="sxs-lookup"><span data-stu-id="76d51-107">Remove the scheme from URLs manually (e.g. remove <code>file://</code> from URLs)</span></span></li><li><span data-ttu-id="76d51-108">将 URI 传递给 <xref:System.Uri> 类并使用 <xref:System.Uri.LocalPath></span><span class="sxs-lookup"><span data-stu-id="76d51-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span></li></ul><span data-ttu-id="76d51-109">或者，通过将 <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext 开关设置为 true 来选择不用新路径规范化。</span><span class="sxs-lookup"><span data-stu-id="76d51-109">Alternatively, you can opt out of the new path normalization by setting the <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext switch to true.</span></span>|
|<span data-ttu-id="76d51-110">范围</span><span class="sxs-lookup"><span data-stu-id="76d51-110">Scope</span></span>|<span data-ttu-id="76d51-111">边缘</span><span class="sxs-lookup"><span data-stu-id="76d51-111">Edge</span></span>|
|<span data-ttu-id="76d51-112">Version</span><span class="sxs-lookup"><span data-stu-id="76d51-112">Version</span></span>|<span data-ttu-id="76d51-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="76d51-113">4.6.2</span></span>|
|<span data-ttu-id="76d51-114">类型</span><span class="sxs-lookup"><span data-stu-id="76d51-114">Type</span></span>|<span data-ttu-id="76d51-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="76d51-115">Retargeting</span></span>|
|<span data-ttu-id="76d51-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="76d51-116">Affected APIs</span></span>|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
