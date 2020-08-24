---
title: 创建、改进微服务 API 及协定并进行版本控制
description: 在考虑演变和版本控制的情况下创建微服务 API 和协定，因为需要改变。
ms.date: 09/20/2018
ms.openlocfilehash: 9164bfd12df18a88ac187c8962f0afc80b702881
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557667"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a><span data-ttu-id="016e1-103">创建、改进微服务 API 及协定并进行版本控制</span><span class="sxs-lookup"><span data-stu-id="016e1-103">Creating, evolving, and versioning microservice APIs and contracts</span></span>

<span data-ttu-id="016e1-104">微服务 API 是服务及其客户端之间的协定。</span><span class="sxs-lookup"><span data-stu-id="016e1-104">A microservice API is a contract between the service and its clients.</span></span> <span data-ttu-id="016e1-105">用户将能够独立改进微服务，前提是不破坏其 API 协定，这正是协定之所以重要的原因。</span><span class="sxs-lookup"><span data-stu-id="016e1-105">You'll be able to evolve a microservice independently only if you do not break its API contract, which is why the contract is so important.</span></span> <span data-ttu-id="016e1-106">如果更改协定，会影响客户端应用程序或 API 网关。</span><span class="sxs-lookup"><span data-stu-id="016e1-106">If you change the contract, it will impact your client applications or your API Gateway.</span></span>

<span data-ttu-id="016e1-107">API 定义的本质取决于所使用的协议。</span><span class="sxs-lookup"><span data-stu-id="016e1-107">The nature of the API definition depends on which protocol you're using.</span></span> <span data-ttu-id="016e1-108">例如，如果使用的是消息传送（如 [AMQP](http://www.amqp.org/)）协议，则 API 由消息类型构成。</span><span class="sxs-lookup"><span data-stu-id="016e1-108">For instance, if you're using messaging (like [AMQP](http://www.amqp.org/)), the API consists of the message types.</span></span> <span data-ttu-id="016e1-109">如果使用的是 HTTP 和 RESTful 服务，则 API 由 URL、请求和响应 JSON 格式构成。</span><span class="sxs-lookup"><span data-stu-id="016e1-109">If you're using HTTP and RESTful services, the API consists of the URLs and the request and response JSON formats.</span></span>

<span data-ttu-id="016e1-110">但是，即使关注的是初始协定，服务 API 仍需随时间推移而改变。</span><span class="sxs-lookup"><span data-stu-id="016e1-110">However, even if you're thoughtful about your initial contract, a service API will need to change over time.</span></span> <span data-ttu-id="016e1-111">如果发生这种情况 — 尤其是如果 API 是一个供多个客户端应用程序使用的公共 API，通常不能强制所有客户端升级到新的 API 协定。</span><span class="sxs-lookup"><span data-stu-id="016e1-111">When that happens—and especially if your API is a public API consumed by multiple client applications — you typically can't force all clients to upgrade to your new API contract.</span></span> <span data-ttu-id="016e1-112">通常需要逐渐增加对新版服务的部署，并且同时运行旧版和新版的服务协定。</span><span class="sxs-lookup"><span data-stu-id="016e1-112">You usually need to incrementally deploy new versions of a service in a way that both old and new versions of a service contract are running simultaneously.</span></span> <span data-ttu-id="016e1-113">因此，有必要制定服务版本控制策略。</span><span class="sxs-lookup"><span data-stu-id="016e1-113">Therefore, it's important to have a strategy for your service versioning.</span></span>

<span data-ttu-id="016e1-114">如果 API 改动较小，例如向 API 添加属性或参数，则使用较旧 API 的客户端应切换到服务的新版本。</span><span class="sxs-lookup"><span data-stu-id="016e1-114">When the API changes are small, like if you add attributes or parameters to your API, clients that use an older API should switch and work with the new version of the service.</span></span> <span data-ttu-id="016e1-115">你或许能够为任何缺少的必需属性提供默认值，并且客户端或许能够忽略任何额外响应属性。</span><span class="sxs-lookup"><span data-stu-id="016e1-115">You might be able to provide default values for any missing attributes that are required, and the clients might be able to ignore any extra response attributes.</span></span>

<span data-ttu-id="016e1-116">但是，有时需要对服务 API 作出重大但却不兼容的更改。</span><span class="sxs-lookup"><span data-stu-id="016e1-116">However, sometimes you need to make major and incompatible changes to a service API.</span></span> <span data-ttu-id="016e1-117">因为可能不能强制客户端应用程序或服务立即升级到最新版本，服务必须为旧版 API 提供一段时间的支持。</span><span class="sxs-lookup"><span data-stu-id="016e1-117">Because you might not be able to force client applications or services to upgrade immediately to the new version, a service must support older versions of the API for some period.</span></span> <span data-ttu-id="016e1-118">如果使用基于 HTTP 的机制，如 REST，一种方法是在 URL 中或 HTTP 标头中嵌入 API 版本号。</span><span class="sxs-lookup"><span data-stu-id="016e1-118">If you're using an HTTP-based mechanism such as REST, one approach is to embed the API version number in the URL or into an HTTP header.</span></span> <span data-ttu-id="016e1-119">然后可以决定是在同一服务实例内同时实现两个版本的服务，还是部署不同实例，分别处理两个版本的 API。</span><span class="sxs-lookup"><span data-stu-id="016e1-119">Then you can decide between implementing both versions of the service simultaneously within the same service instance, or deploying different instances that each handle a version of the API.</span></span> <span data-ttu-id="016e1-120">解决此问题的一个好方法是使用[中介器模式](https://en.wikipedia.org/wiki/Mediator_pattern)（例如，[MediatR 库](https://github.com/jbogard/MediatR)），将不同的实现版本分离到独立的处理程序中去。</span><span class="sxs-lookup"><span data-stu-id="016e1-120">A good approach for this is the [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern) (for example, [MediatR library](https://github.com/jbogard/MediatR)) to decouple the different implementation versions into independent handlers.</span></span>

<span data-ttu-id="016e1-121">最后，如果使用的是 REST 体系结构，[超媒体](https://www.infoq.com/articles/mark-baker-hypermedia)是为服务提供版本控制并允许改进 API 的最佳解决方案。</span><span class="sxs-lookup"><span data-stu-id="016e1-121">Finally, if you're using a REST architecture, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) is the best solution for versioning your services and allowing evolvable APIs.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="016e1-122">其他资源</span><span class="sxs-lookup"><span data-stu-id="016e1-122">Additional resources</span></span>

- <span data-ttu-id="016e1-123">**Scott Hanselman.ASP.NET Core RESTful Web API versioning made easy**（简化 ASP.NET Core RESTful Web API 版本控制） </span><span class="sxs-lookup"><span data-stu-id="016e1-123">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="016e1-124">**RESTful Web API 版本控制** </span><span class="sxs-lookup"><span data-stu-id="016e1-124">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="016e1-125">**Roy Fielding。版本控制、超媒体和 REST** </span><span class="sxs-lookup"><span data-stu-id="016e1-125">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
><span data-ttu-id="016e1-126">[上一页](asynchronous-message-based-communication.md)
>[下一页](microservices-addressability-service-registry.md)</span><span class="sxs-lookup"><span data-stu-id="016e1-126">[Previous](asynchronous-message-based-communication.md)
[Next](microservices-addressability-service-registry.md)</span></span>
