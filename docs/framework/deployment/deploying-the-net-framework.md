---
title: 部署 .NET Framework
description: 了解如何为想要随应用程序一起安装 .NET 的开发人员以及想在网络中部署 .NET 的管理员部署 .NET。
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
ms.openlocfilehash: 9e9fef2af56ca278b0e326c15546ca9f849a3253
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622765"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="a7dcb-103">部署 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a7dcb-103">Deploying the .NET Framework</span></span>
<span data-ttu-id="a7dcb-104">本部分 .NET Framework 文档所提供的信息适用于安装应用程序的同时想一并安装 .NET Framework 的开发人员，以及想在网络中部署 .NET Framework 的管理员。</span><span class="sxs-lookup"><span data-stu-id="a7dcb-104">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="a7dcb-105">本文还讨论与部署相关的激活和重启问题，并介绍如何监视 .NET Framework 安装的进度。</span><span class="sxs-lookup"><span data-stu-id="a7dcb-105">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7dcb-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="a7dcb-106">In This Section</span></span>  
 [<span data-ttu-id="a7dcb-107">面向开发人员的部署指南</span><span class="sxs-lookup"><span data-stu-id="a7dcb-107">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)  
 <span data-ttu-id="a7dcb-108">说明开发人员如何在其计算机的应用程序中安装 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="a7dcb-108">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="a7dcb-109">面向管理员的部署指南</span><span class="sxs-lookup"><span data-stu-id="a7dcb-109">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)  
 <span data-ttu-id="a7dcb-110">说明系统管理员如何通过 Microsoft Endpoint Configuration Manager 跨网络部署 .NET Framework 及其系统依赖项。</span><span class="sxs-lookup"><span data-stu-id="a7dcb-110">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>  
  
 [<span data-ttu-id="a7dcb-111">在 .NET Framework 4.5 安装期间减少系统重新启动次数</span><span class="sxs-lookup"><span data-stu-id="a7dcb-111">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)  
 <span data-ttu-id="a7dcb-112">描述在任何可能的情况下可以阻止重启的 Restart Manager，并说明安装 .NET Framework 的应用程序如何利用它。</span><span class="sxs-lookup"><span data-stu-id="a7dcb-112">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="a7dcb-113">如何：获取 .NET Framework 4.5 安装程序的进度</span><span class="sxs-lookup"><span data-stu-id="a7dcb-113">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="a7dcb-114">描述如何在没有提示的情况下启动和跟踪 .NET Framework 安装进度，同时显示你自己的安装进度视图。</span><span class="sxs-lookup"><span data-stu-id="a7dcb-114">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="a7dcb-115">.NET Framework 初始化错误：管理用户体验</span><span class="sxs-lookup"><span data-stu-id="a7dcb-115">.NET Framework Initialization Errors: Managing the User Experience</span></span>](initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="a7dcb-116">介绍当 .NET Framework 应用程序所需的 CLR 版本无效或用户电脑上未安装该版本时会发生什么情况，如何解决这些错误以及如何控制向用户显示的错误消息。</span><span class="sxs-lookup"><span data-stu-id="a7dcb-116">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="a7dcb-117">如何：调试 CLR 激活问题</span><span class="sxs-lookup"><span data-stu-id="a7dcb-117">How to: Debug CLR Activation Issues</span></span>](how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="a7dcb-118">介绍如何查看和调试 CLR 激活日志，解决使用正确版本的 CLR 运行应用程序时可能遇到的问题。</span><span class="sxs-lookup"><span data-stu-id="a7dcb-118">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7dcb-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="a7dcb-119">See also</span></span>

- [<span data-ttu-id="a7dcb-120">开发指南</span><span class="sxs-lookup"><span data-stu-id="a7dcb-120">Development Guide</span></span>](../development-guide.md)
