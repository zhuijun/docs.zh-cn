---
title: Windows 应用商店应用的网络隔离
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 0f9288b53b969838cac64c24d3c9861a0f841aca
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558454"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="e5f69-102">Windows 应用商店应用的网络隔离</span><span class="sxs-lookup"><span data-stu-id="e5f69-102">Network Isolation for Windows Store Apps</span></span>

<span data-ttu-id="e5f69-103"><xref:System.Net>、<xref:System.Net.Http> 和 <xref:System.Net.Http.Headers> 命名空间中的类可用于开发 Windows 应用商店应用或桌面应用。</span><span class="sxs-lookup"><span data-stu-id="e5f69-103">Classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="e5f69-104">在 Windows 应用商店应用中使用时，这些命名空间中的类会受到网络隔离（Windows 8 使用的应用程序安全模型的一部分）的影响。</span><span class="sxs-lookup"><span data-stu-id="e5f69-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by Windows 8.</span></span> <span data-ttu-id="e5f69-105">必须在应用清单中为 Windows 应用商店应用启用适当的网络功能，以便系统允许网络访问。</span><span class="sxs-lookup"><span data-stu-id="e5f69-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="e5f69-106">网络隔离的核对清单</span><span class="sxs-lookup"><span data-stu-id="e5f69-106">Checklist for Network Isolation</span></span>  

<span data-ttu-id="e5f69-107">使用此清单以确保为 Windows 应用商店应用配置了网络隔离。</span><span class="sxs-lookup"><span data-stu-id="e5f69-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1. <span data-ttu-id="e5f69-108">确定应用所需网络访问请求的方向。</span><span class="sxs-lookup"><span data-stu-id="e5f69-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="e5f69-109">这可以是出站客户端发起的请求或入站主动提供的请求，也可以是这两种网络请求类型的组合。</span><span class="sxs-lookup"><span data-stu-id="e5f69-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2. <span data-ttu-id="e5f69-110">确定该应用将与之通信的网络资源类型。</span><span class="sxs-lookup"><span data-stu-id="e5f69-110">Determine the type of network resources that the app will communicate with.</span></span> <span data-ttu-id="e5f69-111">应用可能需要与家庭或工作网络上受信任的资源进行通信。</span><span class="sxs-lookup"><span data-stu-id="e5f69-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="e5f69-112">应用可能需要与 Internet 上的资源进行通信。</span><span class="sxs-lookup"><span data-stu-id="e5f69-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="e5f69-113">应用可能需要访问两种类型的网络资源。</span><span class="sxs-lookup"><span data-stu-id="e5f69-113">An app might need access to both types of network resources.</span></span>  
  
3. <span data-ttu-id="e5f69-114">在应用程序清单中配置最低要求的网络隔离功能。</span><span class="sxs-lookup"><span data-stu-id="e5f69-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4. <span data-ttu-id="e5f69-115">部署并运行应用，使用为故障排除提供的网络隔离工具进行测试。</span><span class="sxs-lookup"><span data-stu-id="e5f69-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
<span data-ttu-id="e5f69-116">有关如何配置用于网络隔离故障排除的网络功能和隔离工具的详细信息，请参阅 Windows 8.x 应用商店开发人员文档中的[如何配置网络隔离功能](/previous-versions/windows/apps/hh770532(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="e5f69-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](/previous-versions/windows/apps/hh770532(v=win.10)) in the Windows 8.x Store developer documentation.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e5f69-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5f69-117">See also</span></span>

- <span data-ttu-id="e5f69-118">[连接到 Web 服务](/previous-versions/windows/apps/hh761504(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="e5f69-118">[Connecting to a web service](/previous-versions/windows/apps/hh761504(v=win.10))</span></span>
- <span data-ttu-id="e5f69-119">[网络隔离指南和核对清单](/previous-versions/windows/apps/hh770532(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="e5f69-119">[Guidelines and checklist for network isolation](/previous-versions/windows/apps/hh770532(v=win.10))</span></span>
- <span data-ttu-id="e5f69-120">[快速入门：使用 HttpClient 进行连接](/previous-versions/windows/apps/hh781239(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="e5f69-120">[Quickstart: Connecting using HttpClient](/previous-versions/windows/apps/hh781239(v=win.10))</span></span>
- <span data-ttu-id="e5f69-121">[如何使用 HttpClient 处理程序](/previous-versions/windows/apps/hh781241(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="e5f69-121">[How to use HttpClient handlers](/previous-versions/windows/apps/hh781241(v=win.10))</span></span>
- <span data-ttu-id="e5f69-122">[如何确保 HttpClient 连接安全](/previous-versions/windows/apps/hh781240(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="e5f69-122">[How to secure HttpClient connections](/previous-versions/windows/apps/hh781240(v=win.10))</span></span>
- [<span data-ttu-id="e5f69-123">HttpClient 示例</span><span class="sxs-lookup"><span data-stu-id="e5f69-123">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
