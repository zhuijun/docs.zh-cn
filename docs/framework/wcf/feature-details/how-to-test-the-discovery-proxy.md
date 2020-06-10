---
title: 如何：测试发现代理
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 78921d0a26f1116c87c2931b1472a161d6fed145
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592809"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="f1330-102">如何：测试发现代理</span><span class="sxs-lookup"><span data-stu-id="f1330-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="f1330-103">本主题是演示如何实现发现代理的四个主题中的第四个。</span><span class="sxs-lookup"><span data-stu-id="f1330-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="f1330-104">在上一主题中，[如何：实现使用发现代理查找服务的客户端应用](client-app-discovery-proxy-to-find-a-service.md)程序，实现了使用发现代理查找服务然后调用服务的 WCF 客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1330-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="f1330-105">本主题说明如何验证发现代理、服务以及客户端应用程序是否按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="f1330-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="f1330-106">运行发现代理</span><span class="sxs-lookup"><span data-stu-id="f1330-106">Run the Discovery Proxy</span></span>  
  
1. <span data-ttu-id="f1330-107">以管理员身份打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="f1330-107">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="f1330-108">您可能会看到显示如下内容的对话框：Windows 防火墙已经阻止此程序的部分功能。</span><span class="sxs-lookup"><span data-stu-id="f1330-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="f1330-109">如果看到此消息，请单击 "**解除阻止**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f1330-109">If you see this message, click the **Unblock** button.</span></span>  
  
3. <span data-ttu-id="f1330-110">在命令提示中，运行发现代理 DiscoveryProxy.exe。</span><span class="sxs-lookup"><span data-stu-id="f1330-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4. <span data-ttu-id="f1330-111">应用程序应显示以下文本：`Proxy started. Hit Enter to exit`。</span><span class="sxs-lookup"><span data-stu-id="f1330-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="f1330-112">运行可检测服务</span><span class="sxs-lookup"><span data-stu-id="f1330-112">Run the Discoverable Service</span></span>  
  
1. <span data-ttu-id="f1330-113">以管理员身份打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="f1330-113">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="f1330-114">在命令提示中，运行 Service.exe 可检测服务。</span><span class="sxs-lookup"><span data-stu-id="f1330-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3. <span data-ttu-id="f1330-115">DiscoveryProxy 应显示以下文本： `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` 。</span><span class="sxs-lookup"><span data-stu-id="f1330-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="f1330-116">运行客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="f1330-116">Run the Client Application</span></span>  
  
1. <span data-ttu-id="f1330-117">打开命令提示。</span><span class="sxs-lookup"><span data-stu-id="f1330-117">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="f1330-118">在命令提示中，运行 client.exe 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1330-118">Within the command prompt, run the client.exe application.</span></span>  
  
3. <span data-ttu-id="f1330-119">几秒钟后，客户端应用程序显示以下文本：Connecting to [Service-Endpoint]。</span><span class="sxs-lookup"><span data-stu-id="f1330-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4. <span data-ttu-id="f1330-120">然后，service.exe 应显示以下文本：Greeting request received, I will respond.</span><span class="sxs-lookup"><span data-stu-id="f1330-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5. <span data-ttu-id="f1330-121">然后，client.exe 应显示以下文本：Hello Client!</span><span class="sxs-lookup"><span data-stu-id="f1330-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="f1330-122">关闭应用程序</span><span class="sxs-lookup"><span data-stu-id="f1330-122">Shut Down the Applications</span></span>  
  
1. <span data-ttu-id="f1330-123">关闭客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1330-123">Shut down the client application.</span></span>  
  
2. <span data-ttu-id="f1330-124">关闭服务。</span><span class="sxs-lookup"><span data-stu-id="f1330-124">Shut down the service.</span></span> <span data-ttu-id="f1330-125">此时，发现代理显示以下文本：`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`。</span><span class="sxs-lookup"><span data-stu-id="f1330-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3. <span data-ttu-id="f1330-126">关闭发现代理。</span><span class="sxs-lookup"><span data-stu-id="f1330-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1330-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1330-127">See also</span></span>

- [<span data-ttu-id="f1330-128">WCF Discovery 概述</span><span class="sxs-lookup"><span data-stu-id="f1330-128">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="f1330-129">如何：实现发现代理</span><span class="sxs-lookup"><span data-stu-id="f1330-129">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="f1330-130">如何：实现向发现代理注册的可发现的服务</span><span class="sxs-lookup"><span data-stu-id="f1330-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="f1330-131">如何：实现使用发现代理查找服务的客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="f1330-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
