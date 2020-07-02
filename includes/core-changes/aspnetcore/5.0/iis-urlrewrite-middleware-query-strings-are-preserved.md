---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325242"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="36ead-101">IIS：保留 UrlRewrite 中间件查询字符串</span><span class="sxs-lookup"><span data-stu-id="36ead-101">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="36ead-102">IIS UrlRewrite 中间件缺陷阻止了在重写规则中保留查询字符串。</span><span class="sxs-lookup"><span data-stu-id="36ead-102">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="36ead-103">此缺陷已修复，以与 IIS UrlRewrite 模块的行为保持一致。</span><span class="sxs-lookup"><span data-stu-id="36ead-103">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="36ead-104">有关讨论，请参阅问题 [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972)。</span><span class="sxs-lookup"><span data-stu-id="36ead-104">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="36ead-105">引入的版本</span><span class="sxs-lookup"><span data-stu-id="36ead-105">Version introduced</span></span>

<span data-ttu-id="36ead-106">ASP.NET Core 5.0 预览版 7</span><span class="sxs-lookup"><span data-stu-id="36ead-106">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="36ead-107">旧行为</span><span class="sxs-lookup"><span data-stu-id="36ead-107">Old behavior</span></span>

<span data-ttu-id="36ead-108">考虑以下重写规则：</span><span class="sxs-lookup"><span data-stu-id="36ead-108">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="36ead-109">前面的规则不追加查询字符串。</span><span class="sxs-lookup"><span data-stu-id="36ead-109">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="36ead-110">URI（如 `/about?id=1`）会重定向到 `/contact` 而不是 `/contact?id=1`。</span><span class="sxs-lookup"><span data-stu-id="36ead-110">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="36ead-111">`appendQueryString` 属性也默认为 `true`。</span><span class="sxs-lookup"><span data-stu-id="36ead-111">The `appendQueryString` attribute defaults to `true` as well.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="36ead-112">新行为</span><span class="sxs-lookup"><span data-stu-id="36ead-112">New behavior</span></span>

<span data-ttu-id="36ead-113">保留查询字符串。</span><span class="sxs-lookup"><span data-stu-id="36ead-113">The query string is preserved.</span></span> <span data-ttu-id="36ead-114">[旧行为](#old-behavior)的示例中的 URI 将为 `/contact?id=1`。</span><span class="sxs-lookup"><span data-stu-id="36ead-114">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="36ead-115">更改原因</span><span class="sxs-lookup"><span data-stu-id="36ead-115">Reason for change</span></span>

<span data-ttu-id="36ead-116">旧行为与 IIS UrlRewrite 模块的行为不匹配。</span><span class="sxs-lookup"><span data-stu-id="36ead-116">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="36ead-117">若要支持在中间件与模块之间进行移植，应以保持一致的行为为目标。</span><span class="sxs-lookup"><span data-stu-id="36ead-117">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="36ead-118">建议操作</span><span class="sxs-lookup"><span data-stu-id="36ead-118">Recommended action</span></span>

<span data-ttu-id="36ead-119">如果首选删除查询字符串的行为，请将 `action` 元素设置为 `appendQueryString="false"`。</span><span class="sxs-lookup"><span data-stu-id="36ead-119">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

#### <a name="category"></a><span data-ttu-id="36ead-120">类别</span><span class="sxs-lookup"><span data-stu-id="36ead-120">Category</span></span>

<span data-ttu-id="36ead-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="36ead-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="36ead-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="36ead-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
