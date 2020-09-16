---
title: Hosting2
ms.date: 03/30/2017
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
ms.openlocfilehash: 0a502093ff40f1a702f5d4d9046d4627eae39e01
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555778"
---
# <a name="hosting"></a><span data-ttu-id="0cc6c-102">Hosting</span><span class="sxs-lookup"><span data-stu-id="0cc6c-102">Hosting</span></span>
<span data-ttu-id="0cc6c-103">本节中的主题介绍服务承载。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-103">The topics in the section describe service hosting.</span></span> <span data-ttu-id="0cc6c-104">可以通过 Internet Information Services (IIS) 、Windows 进程激活服务 (为) 、Windows Server AppFabric、Windows 服务或托管的应用程序来承载服务，此选项通常称为 " *自承载*"。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-104">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="0cc6c-105">值得注意的是，从不受信任的主机运行服务或任何扩展会危害安全。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-105">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0cc6c-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="0cc6c-106">In This Section</span></span>  
 [<span data-ttu-id="0cc6c-107">在 Internet 信息服务中承载</span><span class="sxs-lookup"><span data-stu-id="0cc6c-107">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)  
 <span data-ttu-id="0cc6c-108">描述如何在 Internet Information Services 或 [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10))中承载 WCF) 服务 Windows Communication Foundation (。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-108">Describes how a Windows Communication Foundation (WCF) service is hosted in Internet Information Services or [Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)).</span></span>  
  
 [<span data-ttu-id="0cc6c-109">在 Windows 进程激活服务中承载</span><span class="sxs-lookup"><span data-stu-id="0cc6c-109">Hosting in Windows Process Activation Service</span></span>](hosting-in-windows-process-activation-service.md)  
 <span data-ttu-id="0cc6c-110">描述 Windows 进程激活服务如何承载 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-110">Describes how a WCF service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="0cc6c-111">在 Windows 服务应用程序中承载</span><span class="sxs-lookup"><span data-stu-id="0cc6c-111">Hosting in a Windows Service Application</span></span>](hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="0cc6c-112">描述 WCF 服务如何由 Windows 服务托管。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-112">Describes how a WCF service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="0cc6c-113">在托管应用程序中承载</span><span class="sxs-lookup"><span data-stu-id="0cc6c-113">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)  
 <span data-ttu-id="0cc6c-114">介绍如何在托管应用程序中托管 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-114">Describes how a WCF service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="0cc6c-115">IIS 和 WAS 中的基于配置的激活</span><span class="sxs-lookup"><span data-stu-id="0cc6c-115">Configuration-Based Activation in IIS and WAS</span></span>](configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="0cc6c-116">介绍如何在 IIS 下承载 WCF 服务，或者不使用 .svc 文件承载 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-116">Describes how a WCF service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="0cc6c-117">支持多个 IIS 站点绑定</span><span class="sxs-lookup"><span data-stu-id="0cc6c-117">Supporting Multiple IIS Site Bindings</span></span>](supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="0cc6c-118">描述如何使用同一 URI 方案在一个网站上为一个服务指定多个基址。</span><span class="sxs-lookup"><span data-stu-id="0cc6c-118">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc6c-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="0cc6c-119">See also</span></span>

- [<span data-ttu-id="0cc6c-120">承载服务</span><span class="sxs-lookup"><span data-stu-id="0cc6c-120">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="0cc6c-121">[Windows Server App Fabric 承载功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0cc6c-121">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
