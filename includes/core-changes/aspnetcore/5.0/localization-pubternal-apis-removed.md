---
ms.openlocfilehash: 62a5f56bb7fffc453623a2c3202f288a19110158
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539444"
---
### <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="0d9fd-101">本地化：已删除“Pubternal”API</span><span class="sxs-lookup"><span data-stu-id="0d9fd-101">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="0d9fd-102">为更好地维护 ASP.NET Core 的 public API 面，已删除部分 :::no-loc text="\"pubternal\""::: 本地化 API。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-102">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="0d9fd-103">:::no-loc text="\"pubternal\""::: API 具有 `public` 访问修饰符，在指示 [internal](../../../../docs/csharp/language-reference/keywords/internal.md) 意向的命名空间中定义。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-103">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../docs/csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="0d9fd-104">有关讨论，请参阅 [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291)。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-104">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0d9fd-105">引入的版本</span><span class="sxs-lookup"><span data-stu-id="0d9fd-105">Version introduced</span></span>

<span data-ttu-id="0d9fd-106">5.0 预览版 6</span><span class="sxs-lookup"><span data-stu-id="0d9fd-106">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0d9fd-107">旧行为</span><span class="sxs-lookup"><span data-stu-id="0d9fd-107">Old behavior</span></span>

<span data-ttu-id="0d9fd-108">以下 API 是 `public`：</span><span class="sxs-lookup"><span data-stu-id="0d9fd-108">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="0d9fd-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 构造函数重载，接受以下参数类型之一：</span><span class="sxs-lookup"><span data-stu-id="0d9fd-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a><span data-ttu-id="0d9fd-110">新行为</span><span class="sxs-lookup"><span data-stu-id="0d9fd-110">New behavior</span></span>

<span data-ttu-id="0d9fd-111">以下列表概述了更改：</span><span class="sxs-lookup"><span data-stu-id="0d9fd-111">The following list outlines the changes:</span></span>

- <span data-ttu-id="0d9fd-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` 变成了 `Microsoft.Extensions.Localization.AssemblyWrapper`，现在是 `internal`。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="0d9fd-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` 变成了 `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`，现在是 `internal`。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="0d9fd-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 构造函数重载，接受以下参数类型之一，现在是 `internal`：</span><span class="sxs-lookup"><span data-stu-id="0d9fd-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a><span data-ttu-id="0d9fd-115">更改原因</span><span class="sxs-lookup"><span data-stu-id="0d9fd-115">Reason for change</span></span>

<span data-ttu-id="0d9fd-116">[aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882) 中有更多全面的解释，从 `public` API 面中删除了 :::no-loc text="\"pubternal\""::: 类型。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-116">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="0d9fd-117">这些更改可使更多类适应该设计决策。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-117">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="0d9fd-118">上述类用作了团队内部测试的扩展点。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-118">The classes in question were intended as extension points for the team's internal testing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0d9fd-119">建议操作</span><span class="sxs-lookup"><span data-stu-id="0d9fd-119">Recommended action</span></span>

<span data-ttu-id="0d9fd-120">尽管不太可能，但某些应用可能有意或无意地依赖 :::no-loc text="\"pubternal\""::: 类型。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-120">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="0d9fd-121">请参阅[新行为](#new-behavior)部分，确定如何从类型中进行迁移。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-121">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="0d9fd-122">如果你已确定方案，且该方案在此更改之前允许公共 API 但现在不允许，则请在 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) 上提交问题。</span><span class="sxs-lookup"><span data-stu-id="0d9fd-122">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="0d9fd-123">类别</span><span class="sxs-lookup"><span data-stu-id="0d9fd-123">Category</span></span>

<span data-ttu-id="0d9fd-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0d9fd-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0d9fd-125">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0d9fd-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
