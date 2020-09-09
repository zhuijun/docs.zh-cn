---
ms.openlocfilehash: 6af63c0a58a3273aa98fa70f22e3637b481806b4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496218"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="6a3f0-101">路径冒号检查更严格</span><span class="sxs-lookup"><span data-stu-id="6a3f0-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="6a3f0-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="6a3f0-102">Details</span></span>

<span data-ttu-id="6a3f0-103">在 .NET Framework 4.6.2 中，为了支持以前不受支持的路径，进行了大量更改（无论是在长度方面还是在格式方面）。</span><span class="sxs-lookup"><span data-stu-id="6a3f0-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="6a3f0-104">检查正确的驱动器分隔符（冒号）语法变得更加严格，这样做的副作用是阻止了少量特选路径 API 中的某些 URI 路径，而这些之前已被容忍的。</span><span class="sxs-lookup"><span data-stu-id="6a3f0-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they were previously tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6a3f0-105">建议</span><span class="sxs-lookup"><span data-stu-id="6a3f0-105">Suggestion</span></span>

<span data-ttu-id="6a3f0-106">如果将 URI 传递给受影响的 API，请首先将该字符串修改为合法路径。</span><span class="sxs-lookup"><span data-stu-id="6a3f0-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span>

- <span data-ttu-id="6a3f0-107">手动从 URL 中删除该方案（例如从 URL 中删除 `file://`）。</span><span class="sxs-lookup"><span data-stu-id="6a3f0-107">Remove the scheme from URLs manually (for example, remove `file://` from URLs).</span></span>

- <span data-ttu-id="6a3f0-108">将 URI 传递给 <xref:System.Uri> 类并使用 <xref:System.Uri.LocalPath>。</span><span class="sxs-lookup"><span data-stu-id="6a3f0-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath>.</span></span>

<span data-ttu-id="6a3f0-109">或者，通过将 `Switch.System.IO.UseLegacyPathHandling` AppContext 开关设置为 `true` 来选择不用新路径规范化。</span><span class="sxs-lookup"><span data-stu-id="6a3f0-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to `true`.</span></span>

| <span data-ttu-id="6a3f0-110">名称</span><span class="sxs-lookup"><span data-stu-id="6a3f0-110">Name</span></span>    | <span data-ttu-id="6a3f0-111">值</span><span class="sxs-lookup"><span data-stu-id="6a3f0-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6a3f0-112">范围</span><span class="sxs-lookup"><span data-stu-id="6a3f0-112">Scope</span></span>   | <span data-ttu-id="6a3f0-113">边缘</span><span class="sxs-lookup"><span data-stu-id="6a3f0-113">Edge</span></span>        |
| <span data-ttu-id="6a3f0-114">Version</span><span class="sxs-lookup"><span data-stu-id="6a3f0-114">Version</span></span> | <span data-ttu-id="6a3f0-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="6a3f0-115">4.6.2</span></span>       |
| <span data-ttu-id="6a3f0-116">类型</span><span class="sxs-lookup"><span data-stu-id="6a3f0-116">Type</span></span>    | <span data-ttu-id="6a3f0-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="6a3f0-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6a3f0-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="6a3f0-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
