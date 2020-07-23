---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441540"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="e35f2-101">授权：终结点路由中的资源为 HttpContext</span><span class="sxs-lookup"><span data-stu-id="e35f2-101">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="e35f2-102">在 ASP.NET Core 3.1 中使用终结点路由时，用于授权的资源是终结点。</span><span class="sxs-lookup"><span data-stu-id="e35f2-102">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="e35f2-103">此方法不足以获取对路由数据 (<xref:Microsoft.AspNetCore.Routing.RouteData>) 的访问权限。</span><span class="sxs-lookup"><span data-stu-id="e35f2-103">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="e35f2-104">以前在 MVC 中，已传入 <xref:Microsoft.AspNetCore.Http.HttpContext> 资源，这允许访问终结点 (<xref:Microsoft.AspNetCore.Http.Endpoint>) 和路由数据。</span><span class="sxs-lookup"><span data-stu-id="e35f2-104">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="e35f2-105">此更改可确保传递给授权的资源始终是 `HttpContext`。</span><span class="sxs-lookup"><span data-stu-id="e35f2-105">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e35f2-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="e35f2-106">Version introduced</span></span>

<span data-ttu-id="e35f2-107">5.0 预览版 7</span><span class="sxs-lookup"><span data-stu-id="e35f2-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e35f2-108">旧行为</span><span class="sxs-lookup"><span data-stu-id="e35f2-108">Old behavior</span></span>

<span data-ttu-id="e35f2-109">使用终结点路由和授权中间件 (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) 或 [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) 属性时，传递给授权的资源是匹配的终结点。</span><span class="sxs-lookup"><span data-stu-id="e35f2-109">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e35f2-110">新行为</span><span class="sxs-lookup"><span data-stu-id="e35f2-110">New behavior</span></span>

<span data-ttu-id="e35f2-111">终结点路由将 `HttpContext` 传递给授权。</span><span class="sxs-lookup"><span data-stu-id="e35f2-111">Endpoint routing passes the `HttpContext` to authorization.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e35f2-112">更改原因</span><span class="sxs-lookup"><span data-stu-id="e35f2-112">Reason for change</span></span>

<span data-ttu-id="e35f2-113">可以从 `HttpContext` 访问终结点。</span><span class="sxs-lookup"><span data-stu-id="e35f2-113">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="e35f2-114">但是，无法从终结点访问路由数据等内容。</span><span class="sxs-lookup"><span data-stu-id="e35f2-114">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="e35f2-115">非终结点路由导致了功能丢失。</span><span class="sxs-lookup"><span data-stu-id="e35f2-115">There was a loss in functionality from non-endpoint routing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e35f2-116">建议操作</span><span class="sxs-lookup"><span data-stu-id="e35f2-116">Recommended action</span></span>

<span data-ttu-id="e35f2-117">如果应用使用终结点资源，请对 `HttpContext` 调用 <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> 以继续访问终结点。</span><span class="sxs-lookup"><span data-stu-id="e35f2-117">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="e35f2-118">在 ASP.NET Core 5.0 预览版 8 及更高版本中，可以通过 <xref:System.AppContext.SetSwitch%2A> 还原到旧行为。</span><span class="sxs-lookup"><span data-stu-id="e35f2-118">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="e35f2-119">例如：</span><span class="sxs-lookup"><span data-stu-id="e35f2-119">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a><span data-ttu-id="e35f2-120">类别</span><span class="sxs-lookup"><span data-stu-id="e35f2-120">Category</span></span>

<span data-ttu-id="e35f2-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e35f2-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e35f2-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e35f2-122">Affected APIs</span></span>

<span data-ttu-id="e35f2-123">None</span><span class="sxs-lookup"><span data-stu-id="e35f2-123">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
