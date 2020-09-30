---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077587"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="e7132-101">Blazor：JSObjectReference 和 JSInProcessObjectReference 类型已更改为 internal</span><span class="sxs-lookup"><span data-stu-id="e7132-101">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="e7132-102">ASP.NET Core 5.0 RC1 中引入的新的 `Microsoft.JSInterop.JSObjectReference` 和 `Microsoft.JSInterop.JSInProcessObjectReference` 类型已被标记为 `internal`。</span><span class="sxs-lookup"><span data-stu-id="e7132-102">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7132-103">引入的版本</span><span class="sxs-lookup"><span data-stu-id="e7132-103">Version introduced</span></span>

<span data-ttu-id="e7132-104">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="e7132-104">5.0 RC2</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e7132-105">旧行为</span><span class="sxs-lookup"><span data-stu-id="e7132-105">Old behavior</span></span>

<span data-ttu-id="e7132-106">可以通过 `IJSRuntime` 从 JavaScript 互操作调用中获取 `JSObjectReference`。</span><span class="sxs-lookup"><span data-stu-id="e7132-106">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="e7132-107">例如：</span><span class="sxs-lookup"><span data-stu-id="e7132-107">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a><span data-ttu-id="e7132-108">新行为</span><span class="sxs-lookup"><span data-stu-id="e7132-108">New behavior</span></span>

<span data-ttu-id="e7132-109">`JSObjectReference` 使用 [internal](../../../../docs/csharp/language-reference/keywords/internal.md) 访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="e7132-109">`JSObjectReference` uses the [internal](../../../../docs/csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="e7132-110">必须改为使用 `public` `IJSObjectReference` 接口。</span><span class="sxs-lookup"><span data-stu-id="e7132-110">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="e7132-111">例如：</span><span class="sxs-lookup"><span data-stu-id="e7132-111">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="e7132-112">`JSInProcessObjectReference` 也被标记为 `internal` 并由 `IJSInProcessObjectReference` 替换。</span><span class="sxs-lookup"><span data-stu-id="e7132-112">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e7132-113">更改原因</span><span class="sxs-lookup"><span data-stu-id="e7132-113">Reason for change</span></span>

<span data-ttu-id="e7132-114">此更改使 JavaScript 互操作功能与 Blazor 中的其他模式更加一致。</span><span class="sxs-lookup"><span data-stu-id="e7132-114">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="e7132-115">`IJSObjectReference` 类似于 `IJSRuntime`，因为它有类似的目的，并且有类似的方法和扩展。</span><span class="sxs-lookup"><span data-stu-id="e7132-115">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7132-116">建议操作</span><span class="sxs-lookup"><span data-stu-id="e7132-116">Recommended action</span></span>

<span data-ttu-id="e7132-117">分别用 `IJSObjectReference` 和 `IJSInProcessObjectReference` 替换出现的 `JSObjectReference` 和 `JSInProcessObjectReference`。</span><span class="sxs-lookup"><span data-stu-id="e7132-117">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

#### <a name="category"></a><span data-ttu-id="e7132-118">类别</span><span class="sxs-lookup"><span data-stu-id="e7132-118">Category</span></span>

<span data-ttu-id="e7132-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e7132-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7132-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e7132-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
