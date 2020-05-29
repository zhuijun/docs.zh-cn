---
title: 使用 ASP.NET Core 和 Azure 构建新式 Web 应用程序
description: 本指南提供了使用 ASP.NET Core 和 Azure 生成单片式 Web 应用的端到端指导。
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 8eebe9a8e530b244f4596adef1b5e6dd23e305bd
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144534"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="26a53-103">使用 ASP.NET Core 和 Azure 构建新式 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="26a53-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![《架构新式 Web 应用程序》指南的书籍封面图像。](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="26a53-105">**版本 v3.1** - 已更新到 ASP.NET Core v3.1</span><span class="sxs-lookup"><span data-stu-id="26a53-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="26a53-106">发布者</span><span class="sxs-lookup"><span data-stu-id="26a53-106">PUBLISHED BY</span></span>

<span data-ttu-id="26a53-107">Microsoft 开发人员部门、.NET 和 Visual Studio 产品团队</span><span class="sxs-lookup"><span data-stu-id="26a53-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="26a53-108">Microsoft Corporation 的一个部门</span><span class="sxs-lookup"><span data-stu-id="26a53-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="26a53-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="26a53-109">One Microsoft Way</span></span>

<span data-ttu-id="26a53-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="26a53-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="26a53-111">版权所有 © 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="26a53-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="26a53-112">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="26a53-112">All rights reserved.</span></span> <span data-ttu-id="26a53-113">未经发布者书面许可，不得以任何形式或任何方式复制或传播本书中的任何内容。</span><span class="sxs-lookup"><span data-stu-id="26a53-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="26a53-114">本书“按原样”提供，表达作者的观点和看法。</span><span class="sxs-lookup"><span data-stu-id="26a53-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="26a53-115">本书中表达的观点、看法和信息（包括 URL 和其他 Internet 网站引用）如有更改，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="26a53-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="26a53-116">本书中提及的一些示例仅用于说明，纯属虚构。</span><span class="sxs-lookup"><span data-stu-id="26a53-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="26a53-117">不存在任何实际关联或联系，请勿妄加推断。</span><span class="sxs-lookup"><span data-stu-id="26a53-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="26a53-118">Microsoft 和 <https://www.microsoft.com> 上“商标”网页列出的商标是 Microsoft 集团公司的商标。</span><span class="sxs-lookup"><span data-stu-id="26a53-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="26a53-119">Mac 和 macOS 是 Apple Inc. 的商标</span><span class="sxs-lookup"><span data-stu-id="26a53-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="26a53-120">Docker 的鲸鱼徽标是 Docker Inc. 的注册商标经许可方可使用。</span><span class="sxs-lookup"><span data-stu-id="26a53-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="26a53-121">所有其他标记和徽标均为其各自所有者的财产。</span><span class="sxs-lookup"><span data-stu-id="26a53-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="26a53-122">作者:</span><span class="sxs-lookup"><span data-stu-id="26a53-122">Author:</span></span>

> <span data-ttu-id="26a53-123">**Steve "ardalis" Smith** - 软件设计师及培训师 - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="26a53-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="26a53-124">编辑：</span><span class="sxs-lookup"><span data-stu-id="26a53-124">Editors:</span></span>

> <span data-ttu-id="26a53-125">Maira Wenzel </span><span class="sxs-lookup"><span data-stu-id="26a53-125">**Maira Wenzel**</span></span>

## <a name="action-links"></a><span data-ttu-id="26a53-126">操作链接</span><span class="sxs-lookup"><span data-stu-id="26a53-126">Action links</span></span>

- <span data-ttu-id="26a53-127">此电子书还提供 PDF 格式（仅限英文）[下载](https://aka.ms/webappebook)</span><span class="sxs-lookup"><span data-stu-id="26a53-127">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/webappebook)</span></span>

- <span data-ttu-id="26a53-128">克隆参考应用程序 [GitHub 上的 eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) 或为其创建分支</span><span class="sxs-lookup"><span data-stu-id="26a53-128">Clone/Fork the reference application [eShopOnWeb on GitHub](https://github.com/dotnet-architecture/eShopOnWeb)</span></span>

## <a name="introduction"></a><span data-ttu-id="26a53-129">介绍</span><span class="sxs-lookup"><span data-stu-id="26a53-129">Introduction</span></span>

<span data-ttu-id="26a53-130">相比传统 .NET 开发，.NET Core 和 ASP.NET Core 具有一系列优势。</span><span class="sxs-lookup"><span data-stu-id="26a53-130">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="26a53-131">如果以下所有方面或一些方面对于你的应用程序成功至关重要，应将 .NET Core 用于服务器应用程序：</span><span class="sxs-lookup"><span data-stu-id="26a53-131">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="26a53-132">跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="26a53-132">Cross-platform support.</span></span>

- <span data-ttu-id="26a53-133">微服务的使用。</span><span class="sxs-lookup"><span data-stu-id="26a53-133">Use of microservices.</span></span>

- <span data-ttu-id="26a53-134">Docker 容器的使用。</span><span class="sxs-lookup"><span data-stu-id="26a53-134">Use of Docker containers.</span></span>

- <span data-ttu-id="26a53-135">高性能和可伸缩性需求。</span><span class="sxs-lookup"><span data-stu-id="26a53-135">High performance and scalability requirements.</span></span>

- <span data-ttu-id="26a53-136">在同一服务器上通过应用程序对 .NET 版本进行并行版本控制。</span><span class="sxs-lookup"><span data-stu-id="26a53-136">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="26a53-137">传统 .NET 应用程序虽然支持许多以上要求，但是 ASP.NET Core 和 .NET Core 已经过优化，可为以上方案提供完善的支持。</span><span class="sxs-lookup"><span data-stu-id="26a53-137">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="26a53-138">越来越多的组织选择使用 Microsoft Azure 等服务，在云中托管 web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="26a53-138">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="26a53-139">如果以下方面对你的应用程序或组织至关重要，应该考虑在云中托管应用程序：</span><span class="sxs-lookup"><span data-stu-id="26a53-139">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="26a53-140">减少对数据中心的成本投入（硬件、软件、空间、实用工具、服务器管理等）</span><span class="sxs-lookup"><span data-stu-id="26a53-140">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="26a53-141">灵活的定价（基于使用情况付费，无需为空闲容量付费）。</span><span class="sxs-lookup"><span data-stu-id="26a53-141">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="26a53-142">高可靠性。</span><span class="sxs-lookup"><span data-stu-id="26a53-142">Extreme reliability.</span></span>

- <span data-ttu-id="26a53-143">改善应用移动性；可轻松更改部署应用的位置和方式。</span><span class="sxs-lookup"><span data-stu-id="26a53-143">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="26a53-144">灵活的容量；基于实际需要增加或减少。</span><span class="sxs-lookup"><span data-stu-id="26a53-144">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="26a53-145">使用 Azure 中托管的 ASP.NET Core 生成 Web 应用，与传统替代方法相比，这能提供许多竞争优势。</span><span class="sxs-lookup"><span data-stu-id="26a53-145">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="26a53-146">ASP.NET Core 针对新式 web 应用程序开发做法和云托管方案进行了优化。</span><span class="sxs-lookup"><span data-stu-id="26a53-146">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="26a53-147">本指南介绍如何构建 ASP.NET Core 应用程序以充分利用这些功能。</span><span class="sxs-lookup"><span data-stu-id="26a53-147">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="26a53-148">目标</span><span class="sxs-lookup"><span data-stu-id="26a53-148">Purpose</span></span>

<span data-ttu-id="26a53-149">本指南提供了使用 ASP.NET Core 和 Azure 构建单片 Web 应用程序的端到端指导  。</span><span class="sxs-lookup"><span data-stu-id="26a53-149">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="26a53-150">在此上下文中，“单片”是指这一事实，即这些应用程序会作为单个单元部署，而不是作为交互服务和应用程序的集合。</span><span class="sxs-lookup"><span data-stu-id="26a53-150">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="26a53-151">本指南是[“ _.NET 微服务 - 容器化 .NET 应用程序体系结构_”](../microservices/index.md)的补充，该文章更侧重于介绍 Docker、微服务和部署容器以托管企业应用程序。</span><span class="sxs-lookup"><span data-stu-id="26a53-151">This guide is complementary to ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md), which focuses more on Docker, microservices, and deployment of containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="26a53-152">.NET 微服务。</span><span class="sxs-lookup"><span data-stu-id="26a53-152">.NET Microservices.</span></span> <span data-ttu-id="26a53-153">适用于容器化 .NET 应用程序的体系结构</span><span class="sxs-lookup"><span data-stu-id="26a53-153">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="26a53-154">电子书 </span><span class="sxs-lookup"><span data-stu-id="26a53-154">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="26a53-155">示例应用程序 </span><span class="sxs-lookup"><span data-stu-id="26a53-155">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="26a53-156">本指南的目标读者</span><span class="sxs-lookup"><span data-stu-id="26a53-156">Who should use this guide</span></span>

<span data-ttu-id="26a53-157">本指南的受众主要是对使用云中的 Microsoft 技术和服务生成新式 web 应用程序感兴趣的开发者、开发潜在顾客和架构师。</span><span class="sxs-lookup"><span data-stu-id="26a53-157">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="26a53-158">次要受众是技术决策者，他们已经熟悉 ASP.NET 或 Azure，并想要了解是否需要为新项目或现有项目升级到 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="26a53-158">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="26a53-159">如何使用本指南</span><span class="sxs-lookup"><span data-stu-id="26a53-159">How you can use this guide</span></span>

<span data-ttu-id="26a53-160">本指南已精简为较小的文档，侧重介绍如何使用新式 .NET 技术和 Azure 生成 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="26a53-160">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Azure.</span></span> <span data-ttu-id="26a53-161">可通读本指南，了解有关此类应用程序及其技术注意事项的基本信息。</span><span class="sxs-lookup"><span data-stu-id="26a53-161">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="26a53-162">本指南及其示例应用程序还可作为操作起点或参考。</span><span class="sxs-lookup"><span data-stu-id="26a53-162">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="26a53-163">可将相关示例应用程序作为你自己的应用程序的模板，或者了解如何组织应用程序的组件部件。</span><span class="sxs-lookup"><span data-stu-id="26a53-163">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="26a53-164">在对自己的应用程序进行选择权衡时，请参考指南的原则、体系结构的范围以及技术选项和决策注意事项。</span><span class="sxs-lookup"><span data-stu-id="26a53-164">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="26a53-165">请将本指南转发到团队中，这有助于确保对这些注意事项和机会的共同理解。</span><span class="sxs-lookup"><span data-stu-id="26a53-165">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="26a53-166">确保每个人使用共同的术语和基础原则工作，这有助于构建模式和做法的一致应用。</span><span class="sxs-lookup"><span data-stu-id="26a53-166">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="26a53-167">reference</span><span class="sxs-lookup"><span data-stu-id="26a53-167">References</span></span>

- <span data-ttu-id="26a53-168">**为服务器应用选择 .NET Core 或 .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="26a53-168">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="26a53-169">下一篇</span><span class="sxs-lookup"><span data-stu-id="26a53-169">Next</span></span>](modern-web-applications-characteristics.md)
