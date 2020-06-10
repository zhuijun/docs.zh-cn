---
title: 实现发现代理
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 382df95fef2108d338e4ea327da9185c856eca5a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579236"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="1f7d5-102">实现发现代理</span><span class="sxs-lookup"><span data-stu-id="1f7d5-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="1f7d5-103">本节说明实现发现代理所需执行的步骤。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="1f7d5-104">发现代理是包含服务存储库的独立服务。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="1f7d5-105">客户端可以查询发现代理，以便查找该代理已知的可检测服务。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="1f7d5-106">使用服务填充代理的方式由实施者决定。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="1f7d5-107">例如，发现代理可以连接到现有服务存储库并使该信息可供检测，管理员可以使用管理 API 向代理添加可检测服务，或者发现代理也可以使用公告功能更新其内部缓存。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="1f7d5-108">WCF 实现提供可使您轻松生成代理的基类。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="1f7d5-109">可以利用这些 API 在现有存储库之上生成发现代理。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="1f7d5-110">此处实现的发现代理与任何其他 WCF 服务类似，您还可以在其中使发现代理可发现，并使客户端定位其终结点。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f7d5-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="1f7d5-111">In This Section</span></span>  
 [<span data-ttu-id="1f7d5-112">如何：实现发现代理</span><span class="sxs-lookup"><span data-stu-id="1f7d5-112">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="1f7d5-113">说明如何实现发现代理。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="1f7d5-114">如何：实现向发现代理注册的可发现的服务</span><span class="sxs-lookup"><span data-stu-id="1f7d5-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="1f7d5-115">介绍如何实现使用发现代理注册的可发现的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="1f7d5-116">如何：实现使用发现代理查找服务的客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="1f7d5-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="1f7d5-117">描述如何实现使用发现代理搜索服务的 WCF 客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="1f7d5-118">如何：测试发现代理</span><span class="sxs-lookup"><span data-stu-id="1f7d5-118">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="1f7d5-119">说明如何测试前面三个主题中编写的代码。</span><span class="sxs-lookup"><span data-stu-id="1f7d5-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f7d5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f7d5-120">See also</span></span>

- [<span data-ttu-id="1f7d5-121">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="1f7d5-121">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="1f7d5-122">如何：以编程方式向 WCF 服务和客户端添加可发现性</span><span class="sxs-lookup"><span data-stu-id="1f7d5-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
