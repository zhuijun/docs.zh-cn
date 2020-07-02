---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614350"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="673b8-101">路径冒号检查更严格</span><span class="sxs-lookup"><span data-stu-id="673b8-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="673b8-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="673b8-102">Details</span></span>

<span data-ttu-id="673b8-103">在 .NET Framework 4.6.2 中，为了支持以前不受支持的路径，进行了大量更改（无论是在长度方面还是在格式方面）。</span><span class="sxs-lookup"><span data-stu-id="673b8-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="673b8-104">检查正确的驱动器分隔符（冒号）语法变得更加严格，这样做的副作用是阻止了少量特选路径 API 中的某些 URI 路径，这些曾经是可以容忍的。</span><span class="sxs-lookup"><span data-stu-id="673b8-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="673b8-105">建议</span><span class="sxs-lookup"><span data-stu-id="673b8-105">Suggestion</span></span>

<span data-ttu-id="673b8-106">如果将 URI 传递给受影响的 API，请首先将该字符串修改为合法路径。</span><span class="sxs-lookup"><span data-stu-id="673b8-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="673b8-107">手动从 URL 中删除该方案（例如，从 URL 中删除 `file://`）</span><span class="sxs-lookup"><span data-stu-id="673b8-107">Remove the scheme from URLs manually (e.g. remove `file://` from URLs)</span></span>

- <span data-ttu-id="673b8-108">将 URI 传递给 <xref:System.Uri> 类并使用 <xref:System.Uri.LocalPath></span><span class="sxs-lookup"><span data-stu-id="673b8-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span>

<span data-ttu-id="673b8-109">或者，通过将 `Switch.System.IO.UseLegacyPathHandling` AppContext 开关设置为 true 来选择不用新路径规范化。</span><span class="sxs-lookup"><span data-stu-id="673b8-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to true.</span></span>

| <span data-ttu-id="673b8-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="673b8-110">Name</span></span>    | <span data-ttu-id="673b8-111">值</span><span class="sxs-lookup"><span data-stu-id="673b8-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="673b8-112">范围</span><span class="sxs-lookup"><span data-stu-id="673b8-112">Scope</span></span>   | <span data-ttu-id="673b8-113">边缘</span><span class="sxs-lookup"><span data-stu-id="673b8-113">Edge</span></span>        |
| <span data-ttu-id="673b8-114">Version</span><span class="sxs-lookup"><span data-stu-id="673b8-114">Version</span></span> | <span data-ttu-id="673b8-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="673b8-115">4.6.2</span></span>       |
| <span data-ttu-id="673b8-116">类型</span><span class="sxs-lookup"><span data-stu-id="673b8-116">Type</span></span>    | <span data-ttu-id="673b8-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="673b8-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="673b8-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="673b8-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
