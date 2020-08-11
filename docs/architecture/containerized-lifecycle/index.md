---
title: 使用 Microsoft 平台和工具的容器化 Docker 应用程序的生命周期
description: 在基本层面概要了解使用 Docker 和 Microsoft 平台及工具开发和部署容器化应用程序的过程。
ms.date: 07/30/2020
ms.openlocfilehash: d8055315b25f73d7b0b355026ab6b2c4767f9d89
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915158"
---
# <a name="containerized-docker-application-lifecycle-with-microsoft-platform-and-tools"></a><span data-ttu-id="b55bc-103">使用 Microsoft 平台和工具的容器化 Docker 应用程序的生命周期</span><span class="sxs-lookup"><span data-stu-id="b55bc-103">Containerized Docker Application Lifecycle with Microsoft Platform and Tools</span></span>

![封面](./media/devops-book-cover-large-we.png)

<span data-ttu-id="b55bc-105">**版本 v3.1** - 已更新到 ASP.NET Core v3.1</span><span class="sxs-lookup"><span data-stu-id="b55bc-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="b55bc-106">本指南在整体上概述了使用 Microsoft 平台和工具通过 Docker 开发和部署容器化的 ASP.NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="b55bc-106">This guide is a general overview for developing and deploying containerized ASP.NET Core applications with Docker, using the Microsoft platform and tools.</span></span> <span data-ttu-id="b55bc-107">本指南大致介绍了 Azure DevOps（用于实现 CI/CD 管道）以及 Azure 容器注册表 (ACR) 和 Azure Kubernetes 服务 AKS（用于部署）。</span><span class="sxs-lookup"><span data-stu-id="b55bc-107">The guide includes a high-level introduction to Azure DevOps, for implementing CI/CD pipelines, as well as Azure Container Registry (ACR), and Azure Kubernetes Services AKS for deployment.</span></span>

<span data-ttu-id="b55bc-108">关于开发的大致详细信息，可参阅 [.NET 微服务：适用于容器化 .NET 应用程序的体系结构](https://docs.microsoft.com/dotnet/architecture/microservices/) 及其相关的参考应用程序 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)。</span><span class="sxs-lookup"><span data-stu-id="b55bc-108">For low-level, development-related details you can see the [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/) guide and it related reference application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers).</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="b55bc-109">向我们发送反馈！</span><span class="sxs-lookup"><span data-stu-id="b55bc-109">Send us your feedback!</span></span>

<span data-ttu-id="b55bc-110">本指南旨在帮助用户了解 .NET 中容器化应用程序和微服务的体系结构。</span><span class="sxs-lookup"><span data-stu-id="b55bc-110">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="b55bc-111">本指南和相关的参考应用程序会不断更新，欢迎你提供宝贵意见！</span><span class="sxs-lookup"><span data-stu-id="b55bc-111">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="b55bc-112">如有关于本指南的改进建议，请在 <https://aka.ms/ebookfeedback> 提交反馈。</span><span class="sxs-lookup"><span data-stu-id="b55bc-112">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="b55bc-113">信用</span><span class="sxs-lookup"><span data-stu-id="b55bc-113">Credits</span></span>

<span data-ttu-id="b55bc-114">作者:</span><span class="sxs-lookup"><span data-stu-id="b55bc-114">Author:</span></span>

> <span data-ttu-id="b55bc-115">**Cesar de la Torre**，Microsoft Corp .NET 产品团队的高级项目经理。</span><span class="sxs-lookup"><span data-stu-id="b55bc-115">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>

<span data-ttu-id="b55bc-116">策划编辑：</span><span class="sxs-lookup"><span data-stu-id="b55bc-116">Acquisitions Editor:</span></span>

> <span data-ttu-id="b55bc-117">Janine Patrick</span><span class="sxs-lookup"><span data-stu-id="b55bc-117">**Janine Patrick**</span></span>

<span data-ttu-id="b55bc-118">开发编辑：</span><span class="sxs-lookup"><span data-stu-id="b55bc-118">Developmental Editor:</span></span>

> <span data-ttu-id="b55bc-119">Bob Russell，Microsoft 的解决方案专业人员</span><span class="sxs-lookup"><span data-stu-id="b55bc-119">**Bob Russell**, Solutions Professional at Microsoft</span></span>
>
> [<span data-ttu-id="b55bc-120">Octal Publishing, Inc.</span><span class="sxs-lookup"><span data-stu-id="b55bc-120">**Octal Publishing, Inc.**</span></span>](http://www.octalpub.com/)

<span data-ttu-id="b55bc-121">生产编辑：</span><span class="sxs-lookup"><span data-stu-id="b55bc-121">Editorial Production:</span></span>

> [<span data-ttu-id="b55bc-122">Dianne Russell</span><span class="sxs-lookup"><span data-stu-id="b55bc-122">Dianne Russell</span></span>](http://www.octalpub.com/)
>
> <span data-ttu-id="b55bc-123">Octal Publishing, Inc.</span><span class="sxs-lookup"><span data-stu-id="b55bc-123">**Octal Publishing, Inc.**</span></span>

<span data-ttu-id="b55bc-124">文字加工编辑：</span><span class="sxs-lookup"><span data-stu-id="b55bc-124">Copyeditor:</span></span>

> <span data-ttu-id="b55bc-125">Bob Russell，Microsoft 的解决方案专业人员</span><span class="sxs-lookup"><span data-stu-id="b55bc-125">**Bob Russell**, Solutions Professional at Microsoft</span></span>

<span data-ttu-id="b55bc-126">参与者和审阅者：</span><span class="sxs-lookup"><span data-stu-id="b55bc-126">Participants and reviewers:</span></span>

> <span data-ttu-id="b55bc-127">Microsoft .NET 团队高级项目经理 Nish Anil </span><span class="sxs-lookup"><span data-stu-id="b55bc-127">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="b55bc-128">**Miguel Veloso**，Plain Concepts 的软件开发工程师</span><span class="sxs-lookup"><span data-stu-id="b55bc-128">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="b55bc-129">Sumit Ghosh，Neudesic 的首席顾问</span><span class="sxs-lookup"><span data-stu-id="b55bc-129">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="b55bc-130">Copyright</span><span class="sxs-lookup"><span data-stu-id="b55bc-130">Copyright</span></span>

<span data-ttu-id="b55bc-131">发布者</span><span class="sxs-lookup"><span data-stu-id="b55bc-131">PUBLISHED BY</span></span>

<span data-ttu-id="b55bc-132">Microsoft 开发人员部门、.NET 和 Visual Studio 产品团队</span><span class="sxs-lookup"><span data-stu-id="b55bc-132">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="b55bc-133">Microsoft Corporation 的一个部门</span><span class="sxs-lookup"><span data-stu-id="b55bc-133">A division of Microsoft Corporation</span></span>

<span data-ttu-id="b55bc-134">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="b55bc-134">One Microsoft Way</span></span>

<span data-ttu-id="b55bc-135">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="b55bc-135">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="b55bc-136">版权所有 &copy; 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="b55bc-136">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="b55bc-137">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="b55bc-137">All rights reserved.</span></span> <span data-ttu-id="b55bc-138">未经发布者书面许可，不得以任何形式或任何方式复制或传播本书中的任何内容。</span><span class="sxs-lookup"><span data-stu-id="b55bc-138">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="b55bc-139">本书“按原样”提供，表达作者的观点和看法。</span><span class="sxs-lookup"><span data-stu-id="b55bc-139">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="b55bc-140">本书中表达的观点、看法和信息（包括 URL 和其他 Internet 网站引用）如有更改，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="b55bc-140">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="b55bc-141">本书中提及的一些示例仅用于说明，纯属虚构。</span><span class="sxs-lookup"><span data-stu-id="b55bc-141">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="b55bc-142">不存在任何实际关联或联系，请勿妄加推断。</span><span class="sxs-lookup"><span data-stu-id="b55bc-142">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="b55bc-143">Microsoft 和 <https://www.microsoft.com> 上“商标”网页列出的商标是 Microsoft 集团公司的商标。</span><span class="sxs-lookup"><span data-stu-id="b55bc-143">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="b55bc-144">Mac 和 macOS 是 Apple Inc. 的商标</span><span class="sxs-lookup"><span data-stu-id="b55bc-144">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="b55bc-145">Docker 的鲸鱼徽标是 Docker Inc. 的注册商标经许可方可使用。</span><span class="sxs-lookup"><span data-stu-id="b55bc-145">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="b55bc-146">所有其他标记和徽标均为其各自所有者的财产。</span><span class="sxs-lookup"><span data-stu-id="b55bc-146">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="b55bc-147">下一页</span><span class="sxs-lookup"><span data-stu-id="b55bc-147">Next</span></span>](introduction-to-containers-and-docker.md)
