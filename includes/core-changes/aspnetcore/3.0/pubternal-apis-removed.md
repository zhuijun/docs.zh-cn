---
ms.openlocfilehash: b1fb9647091cecb80b9c2f04ec9b6bb156eb39ba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84466821"
---
### <a name="pubternal-apis-removed"></a><span data-ttu-id="654ec-101">已删除“Pubternal”API</span><span class="sxs-lookup"><span data-stu-id="654ec-101">"Pubternal" APIs removed</span></span>

<span data-ttu-id="654ec-102">为了更好地维护 ASP.NET Core 面向公众的 API，`*.Internal` 命名空间中的大多数类型（称为 :::no-loc text="\"pubternal\""::: API）已成为真正的内部类型。</span><span class="sxs-lookup"><span data-stu-id="654ec-102">To better maintain the public API surface of ASP.NET Core, most of the types in `*.Internal` namespaces (referred to as :::no-loc text="\"pubternal\""::: APIs) have become truly internal.</span></span> <span data-ttu-id="654ec-103">这些命名空间中的成员永远不会作为面向公众的 API 得到支持。</span><span class="sxs-lookup"><span data-stu-id="654ec-103">Members in these namespaces were never meant to be supported as public-facing APIs.</span></span> <span data-ttu-id="654ec-104">API 可能在次要版本中中断（这种情况经常会发生）。</span><span class="sxs-lookup"><span data-stu-id="654ec-104">The APIs could break in minor releases and often did.</span></span> <span data-ttu-id="654ec-105">在更新到 ASP.NET Core 3.0 时，依赖于这些 API 的代码会中断。</span><span class="sxs-lookup"><span data-stu-id="654ec-105">Code that depends on these APIs breaks when updating to ASP.NET Core 3.0.</span></span>

<span data-ttu-id="654ec-106">有关详细信息，请参阅 [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) 和 [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312)。</span><span class="sxs-lookup"><span data-stu-id="654ec-106">For more information, see [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) and [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="654ec-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="654ec-107">Version introduced</span></span>

<span data-ttu-id="654ec-108">3.0</span><span class="sxs-lookup"><span data-stu-id="654ec-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="654ec-109">旧行为</span><span class="sxs-lookup"><span data-stu-id="654ec-109">Old behavior</span></span>

<span data-ttu-id="654ec-110">受影响的 API 使用 `public` 访问修饰符进行标记，并存在于 `*.Internal` 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="654ec-110">The affected APIs are marked with the `public` access modifier and exist in `*.Internal` namespaces.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="654ec-111">新行为</span><span class="sxs-lookup"><span data-stu-id="654ec-111">New behavior</span></span>

<span data-ttu-id="654ec-112">受影响的 API 使用 [internal](/dotnet/csharp/language-reference/keywords/internal) 访问修饰符进行标记，不能再供该程序集外部的代码使用。</span><span class="sxs-lookup"><span data-stu-id="654ec-112">The affected APIs are marked with the [internal](/dotnet/csharp/language-reference/keywords/internal) access modifier and can no longer be used by code outside that assembly.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="654ec-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="654ec-113">Reason for change</span></span>

<span data-ttu-id="654ec-114">对于这些 :::no-loc text="\"pubternal\""::: API，指导原则是：</span><span class="sxs-lookup"><span data-stu-id="654ec-114">The guidance for these :::no-loc text="\"pubternal\""::: APIs was that they:</span></span>

* <span data-ttu-id="654ec-115">它们可能会更改，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="654ec-115">Could change without notice.</span></span>
* <span data-ttu-id="654ec-116">它们不遵从 .NET 策略来防止中断性变更。</span><span class="sxs-lookup"><span data-stu-id="654ec-116">Weren't subject to .NET policies to prevent breaking changes.</span></span>

<span data-ttu-id="654ec-117">保留这些 API `public` （即使保留在 `*.Internal` 命名空间中）会对客户造成混淆。</span><span class="sxs-lookup"><span data-stu-id="654ec-117">Leaving the APIs `public` (even in the `*.Internal` namespaces) was confusing to customers.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="654ec-118">建议操作</span><span class="sxs-lookup"><span data-stu-id="654ec-118">Recommended action</span></span>

<span data-ttu-id="654ec-119">停止使用这些 :::no-loc text="\"pubternal\""::: API。</span><span class="sxs-lookup"><span data-stu-id="654ec-119">Stop using these :::no-loc text="\"pubternal\""::: APIs.</span></span> <span data-ttu-id="654ec-120">如果对其他 API 有任何疑问，请在 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) 存储库中提问。</span><span class="sxs-lookup"><span data-stu-id="654ec-120">If you have questions about alternate APIs, open an issue in the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) repository.</span></span>

<span data-ttu-id="654ec-121">例如，请考虑 ASP.NET Core 2.2 项目中的以下 HTTP 请求缓冲代码。</span><span class="sxs-lookup"><span data-stu-id="654ec-121">For example, consider the following HTTP request buffering code in an ASP.NET Core 2.2 project.</span></span> <span data-ttu-id="654ec-122">`EnableRewind` 扩展方法存在于 `Microsoft.AspNetCore.Http.Internal` 命名空间中。</span><span class="sxs-lookup"><span data-stu-id="654ec-122">The `EnableRewind` extension method exists in the `Microsoft.AspNetCore.Http.Internal` namespace.</span></span>

```csharp
HttpContext.Request.EnableRewind();
```

<span data-ttu-id="654ec-123">在 ASP.NET Core 3.0 项目中，将 `EnableRewind` 调用替换为对 `EnableBuffering` 扩展方法的调用。</span><span class="sxs-lookup"><span data-stu-id="654ec-123">In an ASP.NET Core 3.0 project, replace the `EnableRewind` call with a call to the `EnableBuffering` extension method.</span></span> <span data-ttu-id="654ec-124">请求缓冲功能的工作方式与过去相同。</span><span class="sxs-lookup"><span data-stu-id="654ec-124">The request buffering feature works as it did in the past.</span></span> <span data-ttu-id="654ec-125">`EnableBuffering` 立即调用 `internal` API。</span><span class="sxs-lookup"><span data-stu-id="654ec-125">`EnableBuffering` calls the now `internal` API.</span></span>

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a><span data-ttu-id="654ec-126">类别</span><span class="sxs-lookup"><span data-stu-id="654ec-126">Category</span></span>

<span data-ttu-id="654ec-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="654ec-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="654ec-128">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="654ec-128">Affected APIs</span></span>

<span data-ttu-id="654ec-129">名称中具有 `Internal` 段的 `Microsoft.AspNetCore.*` 和 `Microsoft.Extensions.*` 命名空间中的所有 API。</span><span class="sxs-lookup"><span data-stu-id="654ec-129">All APIs in the `Microsoft.AspNetCore.*` and `Microsoft.Extensions.*` namespaces that have an `Internal` segment in the namespace name.</span></span> <span data-ttu-id="654ec-130">例如：</span><span class="sxs-lookup"><span data-stu-id="654ec-130">For example:</span></span>

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->
