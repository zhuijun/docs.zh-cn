---
title: 状态管理
description: 了解用于在 ASP.NET Web 窗体和 Blazor 中管理状态的不同方法。
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: 2ca811f886c6a245ac16c2bd66a68ff16e5bfc44
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267719"
---
# <a name="state-management"></a><span data-ttu-id="227ba-103">状态管理</span><span class="sxs-lookup"><span data-stu-id="227ba-103">State management</span></span>

<span data-ttu-id="227ba-104">状态管理是 Web 窗体应用程序的主要概念，通过视图状态、会话状态、应用程序状态和回发功能得以加速。</span><span class="sxs-lookup"><span data-stu-id="227ba-104">State management is a key concept of Web Forms applications, facilitated through View State, Session State, Application State, and Postback features.</span></span> <span data-ttu-id="227ba-105">框架的这些有状态功能有助于隐藏应用程序所需的状态管理，并使应用程序开发人员能够专注于提供其功能。</span><span class="sxs-lookup"><span data-stu-id="227ba-105">These stateful features of the framework helped to hide the state management required for an application and allow application developers to focus on delivering their functionality.</span></span> <span data-ttu-id="227ba-106">使用 ASP.NET Core 和 Blazor，其中的某些功能已被重新定位，一些功能已完全删除。</span><span class="sxs-lookup"><span data-stu-id="227ba-106">With ASP.NET Core and Blazor, some of these features have been relocated and some have been removed altogether.</span></span> <span data-ttu-id="227ba-107">本章介绍如何维护状态，并提供与 Blazor 中的新功能相同的功能。</span><span class="sxs-lookup"><span data-stu-id="227ba-107">This chapter reviews how to maintain state and deliver the same functionality with the new features in Blazor.</span></span>

## <a name="request-state-management-with-viewstate"></a><span data-ttu-id="227ba-108">通过 ViewState 请求状态管理</span><span class="sxs-lookup"><span data-stu-id="227ba-108">Request state management with ViewState</span></span>

<span data-ttu-id="227ba-109">当讨论 Web 窗体应用程序中的状态管理时，许多开发人员会立即想到视图状态。</span><span class="sxs-lookup"><span data-stu-id="227ba-109">When discussing state management in Web Forms application, many developers will immediately think of ViewState.</span></span> <span data-ttu-id="227ba-110">在 Web 窗体中，视图状态通过在浏览器中来回发送大量编码的文本，来管理 HTTP 请求之间的内容状态。</span><span class="sxs-lookup"><span data-stu-id="227ba-110">In Web Forms, ViewState manages the state of the content between HTTP requests by sending a large encoded block of text back and forth to the browser.</span></span> <span data-ttu-id="227ba-111">使用包含多个元素的页面中的内容可能会占用视图状态字段，这可能会使大小增加到几兆字节。</span><span class="sxs-lookup"><span data-stu-id="227ba-111">The ViewState field could be overwhelmed with content from a page containing many elements, potentially expanding to several megabytes in size.</span></span>

<span data-ttu-id="227ba-112">使用 Blazor Server，应用维护与服务器的持续连接。</span><span class="sxs-lookup"><span data-stu-id="227ba-112">With Blazor Server, the app maintains an ongoing connection with the server.</span></span> <span data-ttu-id="227ba-113">应用程序的状态称为 *线路*，连接被视为处于活动状态时，会保留在服务器内存中。</span><span class="sxs-lookup"><span data-stu-id="227ba-113">The app's state, called a *circuit*, is held in server memory while the connection is considered active.</span></span> <span data-ttu-id="227ba-114">仅当用户离开应用或应用中的特定页面时才会释放状态。</span><span class="sxs-lookup"><span data-stu-id="227ba-114">State will only be disposed when the user navigates away from the app or a particular page in the app.</span></span> <span data-ttu-id="227ba-115">活动组件的所有成员在与服务器的交互之间可用。</span><span class="sxs-lookup"><span data-stu-id="227ba-115">All members of the active components are available between interactions with the server.</span></span>

<span data-ttu-id="227ba-116">此功能有几个优点：</span><span class="sxs-lookup"><span data-stu-id="227ba-116">There are several advantages of this feature:</span></span>

- <span data-ttu-id="227ba-117">组件状态随时可用且不在交互之间重建。</span><span class="sxs-lookup"><span data-stu-id="227ba-117">Component state is readily available and not rebuilt between interactions.</span></span>
- <span data-ttu-id="227ba-118">状态不会传输到浏览器。</span><span class="sxs-lookup"><span data-stu-id="227ba-118">State isn't transmitted to the browser.</span></span>

<span data-ttu-id="227ba-119">但是，内存中组件状态持久性存在一些缺点需要注意：</span><span class="sxs-lookup"><span data-stu-id="227ba-119">However, there are some disadvantages to in-memory component state persistence to be aware of:</span></span>

- <span data-ttu-id="227ba-120">如果服务器在请求之间重启，则状态将丢失。</span><span class="sxs-lookup"><span data-stu-id="227ba-120">If the server restarts between request, state is lost.</span></span>
- <span data-ttu-id="227ba-121">应用程序 web 服务器负载平衡解决方案必须包含粘滞会话，以确保来自同一浏览器的所有请求都返回到相同的服务器。</span><span class="sxs-lookup"><span data-stu-id="227ba-121">Your application web server load-balancing solution must include sticky sessions to ensure that all requests from the same browser return to the same server.</span></span> <span data-ttu-id="227ba-122">如果请求发送到其他服务器，则状态将丢失。</span><span class="sxs-lookup"><span data-stu-id="227ba-122">If a request goes to a different server, state will be lost.</span></span>
- <span data-ttu-id="227ba-123">服务器上组件状态的持久性可能导致 web 服务器上的内存压力。</span><span class="sxs-lookup"><span data-stu-id="227ba-123">Persistence of component state on the server can lead to memory pressure on the web server.</span></span>

<span data-ttu-id="227ba-124">出于上述原因，请不要仅依赖于组件在服务器内存中的状态。</span><span class="sxs-lookup"><span data-stu-id="227ba-124">For the preceding reasons, don't rely on just the state of the component to reside in-memory on the server.</span></span> <span data-ttu-id="227ba-125">应用程序还应包括请求之间的数据的一些支持数据存储。</span><span class="sxs-lookup"><span data-stu-id="227ba-125">Your application should also include some backing data store for data between requests.</span></span> <span data-ttu-id="227ba-126">此策略的一些简单示例：</span><span class="sxs-lookup"><span data-stu-id="227ba-126">Some simple examples of this strategy:</span></span>

- <span data-ttu-id="227ba-127">在购物车应用程序中，将添加到购物车中的新项的内容保存到数据库记录中。</span><span class="sxs-lookup"><span data-stu-id="227ba-127">In a shopping cart application, persist the content of new items added to the cart in a database record.</span></span> <span data-ttu-id="227ba-128">如果服务器上的状态丢失，可以从数据库记录中重建该状态。</span><span class="sxs-lookup"><span data-stu-id="227ba-128">If the state on the server is lost, you can reconstitute it from the database records.</span></span>
- <span data-ttu-id="227ba-129">在多部分 web 窗体中，用户希望应用程序记住每个请求之间的值。</span><span class="sxs-lookup"><span data-stu-id="227ba-129">In a multi-part web form, your users will expect your application to remember values between each request.</span></span> <span data-ttu-id="227ba-130">将用户的每个发布的数据写入数据存储区，以便在多部分窗体完成时，可以将这些数据提取并组合到最终的窗体响应结构。</span><span class="sxs-lookup"><span data-stu-id="227ba-130">Write the data between each of your user's posts to a data store so that they can be fetched and assembled into the final form response structure when the multi-part form is completed.</span></span>

<span data-ttu-id="227ba-131">有关在 Blazor 应用中管理状态的更多详细信息，请参阅 [ASP.NET Core Blazor 状态管理](/aspnet/core/blazor/state-management)。</span><span class="sxs-lookup"><span data-stu-id="227ba-131">For additional details on managing state in Blazor apps, see [ASP.NET Core Blazor state management](/aspnet/core/blazor/state-management).</span></span>

## <a name="maintain-state-with-session"></a><span data-ttu-id="227ba-132">通过会话维护状态</span><span class="sxs-lookup"><span data-stu-id="227ba-132">Maintain state with Session</span></span>

<span data-ttu-id="227ba-133">Web 窗体开发人员可以通过字典对象维护有关当前正在进行的用户的信息 <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="227ba-133">Web Forms developers could maintain information about the currently acting user with the <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> dictionary object.</span></span> <span data-ttu-id="227ba-134">向添加具有字符串键的对象非常简单 `Session` ，并且该对象稍后会在用户与应用程序交互的过程中可用。</span><span class="sxs-lookup"><span data-stu-id="227ba-134">It's easy enough to add an object with a string key to the `Session`, and that object would be available at a later time during the user's interactions with the application.</span></span> <span data-ttu-id="227ba-135">在尝试消除与 HTTP 的管理交互的过程中， `Session` 对象使其易于维护。</span><span class="sxs-lookup"><span data-stu-id="227ba-135">In an attempt to eliminate managing interacting with HTTP, the `Session` object made it easy to maintain state.</span></span>

<span data-ttu-id="227ba-136">.NET Framework 对象的签名与 `Session` ASP.NET Core `Session` 对象不同。</span><span class="sxs-lookup"><span data-stu-id="227ba-136">The signature of the .NET Framework `Session` object isn't the same as the ASP.NET Core `Session` object.</span></span> <span data-ttu-id="227ba-137">在决定迁移和使用新的会话状态功能之前，请考虑 [新 ASP.NET Core 会话的文档](/dotnet/api/microsoft.aspnetcore.http.isession) 。</span><span class="sxs-lookup"><span data-stu-id="227ba-137">Consider [the documentation for the new ASP.NET Core Session](/dotnet/api/microsoft.aspnetcore.http.isession) before deciding to migrate and use the new session state feature.</span></span>

<span data-ttu-id="227ba-138">会话在 ASP.NET Core 和 Blazor 服务器中可用，但不建议将其用于适当地将数据存储在数据存储库中。</span><span class="sxs-lookup"><span data-stu-id="227ba-138">Session is available in ASP.NET Core and Blazor Server, but is discouraged from use in favor of storing data in a data repository appropriately.</span></span> <span data-ttu-id="227ba-139">如果由于隐私问题，访问者拒绝在应用程序中使用 HTTP cookie，则会话状态也不起作用。</span><span class="sxs-lookup"><span data-stu-id="227ba-139">Session state is also not functional if visitors decline the use HTTP cookies in your application due to privacy concerns.</span></span>

<span data-ttu-id="227ba-140">[ASP.NET Core 一文中的会话和状态管理](/aspnet/core/fundamentals/app-state#session-state)中提供了 ASP.NET Core 和会话状态的配置。</span><span class="sxs-lookup"><span data-stu-id="227ba-140">Configuration for ASP.NET Core and Session state is available in the [Session and state management in ASP.NET Core article](/aspnet/core/fundamentals/app-state#session-state).</span></span>

## <a name="application-state"></a><span data-ttu-id="227ba-141">应用程序状态</span><span class="sxs-lookup"><span data-stu-id="227ba-141">Application state</span></span>

<span data-ttu-id="227ba-142">`Application`Web 窗体框架中的对象为与应用程序范围的配置和状态交互提供了大规模的跨请求存储库。</span><span class="sxs-lookup"><span data-stu-id="227ba-142">The `Application` object in the Web Forms framework provides a massive, cross-request repository for interacting with application-scope configuration and state.</span></span> <span data-ttu-id="227ba-143">应用程序状态是存储各种应用程序配置属性的理想位置，这些属性将由所有请求引用，而不考虑发出请求的用户。</span><span class="sxs-lookup"><span data-stu-id="227ba-143">Application state was an ideal place to store various application configuration properties that would be referenced by all requests, regardless of the user making the request.</span></span> <span data-ttu-id="227ba-144">对象的问题在于 `Application` ，数据不会在多个服务器之间保持不变。</span><span class="sxs-lookup"><span data-stu-id="227ba-144">The problem with the `Application` object was that data didn't persist across multiple servers.</span></span> <span data-ttu-id="227ba-145">重新启动之间丢失了应用程序对象的状态。</span><span class="sxs-lookup"><span data-stu-id="227ba-145">The state of the application object was lost between restarts.</span></span>

<span data-ttu-id="227ba-146">对于 `Session` ，建议将数据移动到可能由多个服务器实例访问的持久性后备存储。</span><span class="sxs-lookup"><span data-stu-id="227ba-146">As with `Session`, it's recommended that data move to a persistent backing store that could be accessed by multiple server instances.</span></span> <span data-ttu-id="227ba-147">如果有要跨请求和用户访问的易失性数据，可以轻松地将其存储在可注入到需要此信息或交互的组件中的单一服务。</span><span class="sxs-lookup"><span data-stu-id="227ba-147">If there is volatile data that you would like to be able to access across requests and users, you could easily store it in a singleton service that can be injected into components that require this information or interaction.</span></span>

<span data-ttu-id="227ba-148">用于维护应用程序状态及其消耗的对象结构可能与以下实现类似：</span><span class="sxs-lookup"><span data-stu-id="227ba-148">The construction of an object to maintain application state and its consumption could resemble the following implementation:</span></span>

```csharp
public class MyApplicationState
{
    public int VisitorCounter { get; private set; } = 0;

    public void IncrementCounter() => VisitorCounter += 1;
}
```

```csharp
app.AddSingleton<MyApplicationState>();
```

```razor
@inject MyApplicationState AppState

<label>Total Visitors: @AppState.VisitorCounter</label>
```

<span data-ttu-id="227ba-149">`MyApplicationState`对象只在服务器上创建一次，并获取值并将其 `VisitorCounter` 输出到组件的标签中。</span><span class="sxs-lookup"><span data-stu-id="227ba-149">The `MyApplicationState` object is created only once on the server, and the value `VisitorCounter` is fetched and output in the component's label.</span></span> <span data-ttu-id="227ba-150">`VisitorCounter`应保留该值，并从后备数据存储中检索该值以实现持久性和可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="227ba-150">The `VisitorCounter` value should be persisted and retrieved from a backing data store for durability and scalability.</span></span>

## <a name="in-the-browser"></a><span data-ttu-id="227ba-151">在浏览器中</span><span class="sxs-lookup"><span data-stu-id="227ba-151">In the browser</span></span>

<span data-ttu-id="227ba-152">还可以在用户的设备上将应用程序数据存储在客户端，以便以后使用。</span><span class="sxs-lookup"><span data-stu-id="227ba-152">Application data can also be stored client-side on the user's device so that is available later.</span></span> <span data-ttu-id="227ba-153">可以通过两种浏览器功能在用户浏览器的不同范围内保留数据：</span><span class="sxs-lookup"><span data-stu-id="227ba-153">There are two browser features that allow for persistence of data in different scopes of the user's browser:</span></span>

- <span data-ttu-id="227ba-154">`localStorage` -范围限定为用户的整个浏览器。</span><span class="sxs-lookup"><span data-stu-id="227ba-154">`localStorage` - scoped to the user's entire browser.</span></span> <span data-ttu-id="227ba-155">如果重新加载页面，浏览器将关闭并重新打开，或者使用相同的 URL 打开其他选项卡，则浏览器会提供相同的选项卡 `localStorage`</span><span class="sxs-lookup"><span data-stu-id="227ba-155">If the page is reloaded, the browser is closed and reopened, or another tab is opened with the same URL then the same `localStorage` is provided by the browser</span></span>
- <span data-ttu-id="227ba-156">`sessionStorage` -范围是用户的当前浏览器选项卡。如果重新加载该选项卡，则状态将保持不变。</span><span class="sxs-lookup"><span data-stu-id="227ba-156">`sessionStorage` - scoped to the user's current browser tab. If the tab is reloaded, the state persists.</span></span> <span data-ttu-id="227ba-157">但是，如果用户为应用程序打开了另一个选项卡或关闭并重新打开浏览器，则状态将丢失。</span><span class="sxs-lookup"><span data-stu-id="227ba-157">However, if the user opens another tab to your application or closes and reopens the browser the state is lost.</span></span>

<span data-ttu-id="227ba-158">您可以编写一些自定义 JavaScript 代码来与这些功能进行交互，也可以使用多个 NuGet 包来提供此功能。</span><span class="sxs-lookup"><span data-stu-id="227ba-158">You can write some custom JavaScript code to interact with these features, or there are a number of NuGet packages that you can use that provide this functionality.</span></span> <span data-ttu-id="227ba-159">此类包之一为 [AspNetCore. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage)。</span><span class="sxs-lookup"><span data-stu-id="227ba-159">One such package is [Microsoft.AspNetCore.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage).</span></span>

<span data-ttu-id="227ba-160">有关利用此包与和交互的说明 `localStorage` `sessionStorage` ，请参阅 [Blazor 状态管理](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) 一文。</span><span class="sxs-lookup"><span data-stu-id="227ba-160">For instructions on utilizing this package to interact with `localStorage` and `sessionStorage`, see the [Blazor State Management](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) article.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="227ba-161">[上一页](pages-routing-layouts.md)
>[下一页](forms-validation.md)</span><span class="sxs-lookup"><span data-stu-id="227ba-161">[Previous](pages-routing-layouts.md)
[Next](forms-validation.md)</span></span>
