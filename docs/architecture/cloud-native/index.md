---
title: 为 Azure 构建云本机 .NET 应用程序
description: 构建利用 Azure 的容器、微服务和无服务器功能的云本机应用程序的指南。
author: ardalis
ms.date: 05/13/2020
ms.openlocfilehash: b315f097b1584bd93f694c10f36ee7524d7e020a
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144378"
---
# <a name="architecting-cloud-native-net-applications-for-azure"></a><span data-ttu-id="fa9dc-103">为 Azure 构建云本机 .NET 应用程序</span><span class="sxs-lookup"><span data-stu-id="fa9dc-103">Architecting Cloud Native .NET Applications for Azure</span></span>

![封面图像](./media/cover.png)

<span data-ttu-id="fa9dc-105">**版本 v.1.0**</span><span class="sxs-lookup"><span data-stu-id="fa9dc-105">**EDITION v.1.0**</span></span>

<span data-ttu-id="fa9dc-106">发布者</span><span class="sxs-lookup"><span data-stu-id="fa9dc-106">PUBLISHED BY</span></span>

<span data-ttu-id="fa9dc-107">Microsoft 开发人员部门、.NET 和 Visual Studio 产品团队</span><span class="sxs-lookup"><span data-stu-id="fa9dc-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="fa9dc-108">Microsoft Corporation 的一个部门</span><span class="sxs-lookup"><span data-stu-id="fa9dc-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="fa9dc-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="fa9dc-109">One Microsoft Way</span></span>

<span data-ttu-id="fa9dc-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="fa9dc-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="fa9dc-111">版权所有 &copy; 2020 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="fa9dc-111">Copyright &copy; 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="fa9dc-112">保留所有权利。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-112">All rights reserved.</span></span> <span data-ttu-id="fa9dc-113">未经发布者书面许可，不得以任何形式或任何方式复制或传播本书中的任何内容。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="fa9dc-114">本书“按原样”提供，表达作者的观点和看法。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="fa9dc-115">本书中表达的观点、看法和信息（包括 URL 和其他 Internet 网站引用）如有更改，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="fa9dc-116">本书中提及的一些示例仅用于说明，纯属虚构。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="fa9dc-117">不存在任何实际关联或联系，请勿妄加推断。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="fa9dc-118">Microsoft 和 <https://www.microsoft.com> 上“商标”网页列出的商标是 Microsoft 集团公司的商标。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-118">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="fa9dc-119">Mac 和 macOS 是 Apple Inc. 的商标</span><span class="sxs-lookup"><span data-stu-id="fa9dc-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="fa9dc-120">Docker 的鲸鱼徽标是 Docker Inc. 的注册商标经许可方可使用。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="fa9dc-121">所有其他标记和徽标均为其各自所有者的财产。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="fa9dc-122">作者：</span><span class="sxs-lookup"><span data-stu-id="fa9dc-122">Authors:</span></span>

> <span data-ttu-id="fa9dc-123">Rob Vettor，Microsoft 首席云系统架构师/IP 架构师 ([thinkingincloudnative.com](https://thinkingincloudnative.com/about/))</span><span class="sxs-lookup"><span data-stu-id="fa9dc-123">**Rob Vettor**, Principal Cloud System Architect/IP Architect - [thinkingincloudnative.com](https://thinkingincloudnative.com/about/), Microsoft</span></span>
>
> <span data-ttu-id="fa9dc-124">Steve "ardalis" Smith，[Ardalis.com](https://ardalis.com) 软件设计师及培训师</span><span class="sxs-lookup"><span data-stu-id="fa9dc-124">**Steve "ardalis" Smith**, Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="fa9dc-125">参与者和审阅者：</span><span class="sxs-lookup"><span data-stu-id="fa9dc-125">Participants and Reviewers:</span></span>

> <span data-ttu-id="fa9dc-126">**Cesar De Torre**，Microsoft .NET 团队首席项目经理</span><span class="sxs-lookup"><span data-stu-id="fa9dc-126">**Cesar De la Torre**, Principal Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="fa9dc-127">Nish Anil，Microsoft .NET 团队高级项目经理</span><span class="sxs-lookup"><span data-stu-id="fa9dc-127">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="fa9dc-128">Jeremy Likness，Microsoft .NET 团队高级项目经理</span><span class="sxs-lookup"><span data-stu-id="fa9dc-128">**Jeremy Likness**, Senior Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="fa9dc-129">Cecil Phillip，Microsoft 高级云大使</span><span class="sxs-lookup"><span data-stu-id="fa9dc-129">**Cecil Phillip**, Senior Cloud Advocate, Microsoft</span></span>

<span data-ttu-id="fa9dc-130">编辑：</span><span class="sxs-lookup"><span data-stu-id="fa9dc-130">Editors:</span></span>

> <span data-ttu-id="fa9dc-131">Maira Wenzel，Microsoft .NET 团队高级项目经理</span><span class="sxs-lookup"><span data-stu-id="fa9dc-131">**Maira Wenzel**, Program Manager, .NET team, Microsoft</span></span>

## <a name="version"></a><span data-ttu-id="fa9dc-132">Version</span><span class="sxs-lookup"><span data-stu-id="fa9dc-132">Version</span></span>

<span data-ttu-id="fa9dc-133">本指南的编写涵盖 .NET Core 3.1 版本以及与 .NET Core 3.1 同期的同一“批”技术（即 Azure 和其他第三方技术）的许多其他更新。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-133">This guide has been written to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="fa9dc-134">本指南的目标读者</span><span class="sxs-lookup"><span data-stu-id="fa9dc-134">Who should use this guide</span></span>

<span data-ttu-id="fa9dc-135">本指南的受众主要是对学习如何构建为云设计的应用程序感兴趣的开发人员、开发主管和架构师。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-135">The audience for this guide is mainly developers, development leads, and architects who are interested in learning how to build applications designed for the cloud.</span></span>

<span data-ttu-id="fa9dc-136">次级受众是计划选择是否使用云本机方法构建其应用程序的技术决策者。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-136">A secondary audience is technical decision-makers who plan to choose whether to build their applications using a cloud-native approach.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="fa9dc-137">如何使用本指南</span><span class="sxs-lookup"><span data-stu-id="fa9dc-137">How you can use this guide</span></span>

<span data-ttu-id="fa9dc-138">本指南首先定义云本机，并介绍使用云本机原则和技术构建的参考应用程序。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-138">This guide begins by defining cloud native and introducing a reference application built using cloud-native principles and technologies.</span></span> <span data-ttu-id="fa9dc-139">除了前两章，本书内容分成特定章节，集中讨论大多数云本机应用程序的共通主题。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-139">Beyond these first two chapters, the rest of the book is broken up into specific chapters focused on topics common to most cloud-native applications.</span></span> <span data-ttu-id="fa9dc-140">可以跳转到以下任何章节，了解相关云本机方法：</span><span class="sxs-lookup"><span data-stu-id="fa9dc-140">You can jump to any of these chapters to learn about cloud-native approaches to:</span></span>

- <span data-ttu-id="fa9dc-141">数据和数据访问</span><span class="sxs-lookup"><span data-stu-id="fa9dc-141">Data and data access</span></span>
- <span data-ttu-id="fa9dc-142">通信模式</span><span class="sxs-lookup"><span data-stu-id="fa9dc-142">Communication patterns</span></span>
- <span data-ttu-id="fa9dc-143">缩放和可伸缩性</span><span class="sxs-lookup"><span data-stu-id="fa9dc-143">Scaling and scalability</span></span>
- <span data-ttu-id="fa9dc-144">应用程序复原能力</span><span class="sxs-lookup"><span data-stu-id="fa9dc-144">Application resiliency</span></span>
- <span data-ttu-id="fa9dc-145">监视和运行状况</span><span class="sxs-lookup"><span data-stu-id="fa9dc-145">Monitoring and health</span></span>
- <span data-ttu-id="fa9dc-146">标识和安全性</span><span class="sxs-lookup"><span data-stu-id="fa9dc-146">Identity and security</span></span>
- <span data-ttu-id="fa9dc-147">DevOps</span><span class="sxs-lookup"><span data-stu-id="fa9dc-147">DevOps</span></span>

<span data-ttu-id="fa9dc-148">本指南有 PDF 格式和在线版本。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-148">This guide is available both in PDF form and online.</span></span> <span data-ttu-id="fa9dc-149">欢迎随时将此文档或其在线版本的链接转发给你的团队，以确保对这些主题有共同的理解。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-149">Feel free to forward this document or links to its online version to your team to help ensure common understanding of these topics.</span></span> <span data-ttu-id="fa9dc-150">这些主题中的大多数都得益于对基本原则和模式的一致理解，以及与这些主题相关的决策所涉及的权衡。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-150">Most of these topics benefit from a consistent understanding of the underlying principles and patterns, as well as the trade-offs involved in decisions related to these topics.</span></span> <span data-ttu-id="fa9dc-151">本文档的目标是为团队及其领导提供所需的信息，使其能够为应用程序的体系结构、开发和托管作出明智的决策。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-151">Our goal with this document is to equip teams and their leaders with the information they need to make well-informed decisions for their applications' architecture, development, and hosting.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="fa9dc-152">提供你的反馈</span><span class="sxs-lookup"><span data-stu-id="fa9dc-152">Send your feedback</span></span>

<span data-ttu-id="fa9dc-153">我们正在不断完善本书和相关示例，欢迎你提供反馈！</span><span class="sxs-lookup"><span data-stu-id="fa9dc-153">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="fa9dc-154">如果对如何改进本书有任何建议，请使用 [GitHub 问题](https://github.com/dotnet/docs/issues)上任何页面底部的反馈部分进行反馈。</span><span class="sxs-lookup"><span data-stu-id="fa9dc-154">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="fa9dc-155">下一页</span><span class="sxs-lookup"><span data-stu-id="fa9dc-155">Next</span></span>](introduction.md)
