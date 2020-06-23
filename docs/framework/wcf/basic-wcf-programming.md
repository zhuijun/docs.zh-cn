---
title: 基本 WCF 编程
description: 请参阅以下文章，开发从基本编程生命周期到故障排除的 Windows Communication Foundation 应用程序。
ms.date: 03/30/2017
helpviewer_keywords:
- basic programming [WCF]
- WCF [WCF], basic programming
- WCF [WCF], programming
- Windows Communication Foundation [WCF], basic programming
- Windows Communication Foundation [WCF], programming
ms.assetid: 3ae3d498-f43c-4ecc-8cc0-6cbe36b62593
ms.openlocfilehash: 6f4de39494902dcffcb25f75a6ff9f57b28547ff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245513"
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="fa2c2-103">基本 WCF 编程</span><span class="sxs-lookup"><span data-stu-id="fa2c2-103">Basic WCF programming</span></span>

<span data-ttu-id="fa2c2-104">本部分介绍了创建 Windows Communication Foundation （WCF）应用程序的基础知识。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-104">This section presents the fundamentals for creating Windows Communication Foundation (WCF) applications.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fa2c2-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="fa2c2-105">In this section</span></span>

 <span data-ttu-id="fa2c2-106">[基本编程生命周期](basic-programming-lifecycle.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c2-106">[Basic Programming Lifecycle](basic-programming-lifecycle.md)</span></span>\
 <span data-ttu-id="fa2c2-107">介绍设计、生成和部署 WCF 服务和客户端应用程序的生命周期。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-107">Describes the lifecycle of designing, building, and deploying WCF service and client applications.</span></span>

 <span data-ttu-id="fa2c2-108">[设计和实现服务](designing-and-implementing-services.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c2-108">[Designing and Implementing Services](designing-and-implementing-services.md)</span></span>\
 <span data-ttu-id="fa2c2-109">描述如何设计和实现服务协定、选择消息交换模式、指定错误协定，以及服务的其他基本方面。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-109">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>

 <span data-ttu-id="fa2c2-110">[配置服务](configuring-services.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c2-110">[Configuring Services](configuring-services.md)</span></span>\
 <span data-ttu-id="fa2c2-111">介绍如何配置 WCF 服务以支持协定要求，自定义本地运行时行为，并指示发布服务的地址。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-111">Describes how to configure a WCF service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>

 <span data-ttu-id="fa2c2-112">[托管服务](hosting-services.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c2-112">[Hosting Services](hosting-services.md)</span></span>\
 <span data-ttu-id="fa2c2-113">描述应用程序中宿主服务的基础知识。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-113">Describes the basics of hosting services in an application.</span></span>

 <span data-ttu-id="fa2c2-114">[构建客户端](building-clients.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c2-114">[Building Clients](building-clients.md)</span></span>\
 <span data-ttu-id="fa2c2-115">描述如何从服务中获取元数据，将其转换为 WCF 客户端代码，处理安全问题，以及生成、配置和托管 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-115">Describes how to obtain metadata from services, convert that into WCF client code, handle security issues, and build, configure, and host a WCF client.</span></span>

 <span data-ttu-id="fa2c2-116">[扩展性简介](introduction-to-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c2-116">[Introduction to Extensibility](introduction-to-extensibility.md)</span></span>\
 <span data-ttu-id="fa2c2-117">介绍如何扩展 WCF 以创建自定义解决方案。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-117">Describes how to extend WCF to create custom solutions.</span></span>

 <span data-ttu-id="fa2c2-118">[WCF 疑难解答快速入门](wcf-troubleshooting-quickstart.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c2-118">[WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md)</span></span>\
 <span data-ttu-id="fa2c2-119">描述一些发生的最常见问题、相应的解决办法以及在哪里可找到有关这些问题的更多信息。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-119">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>

 <span data-ttu-id="fa2c2-120">[WCF 和 ASP.NET Web API](wcf-and-aspnet-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="fa2c2-120">[WCF and ASP.NET Web API](wcf-and-aspnet-web-api.md)</span></span>\
 <span data-ttu-id="fa2c2-121">讨论这两种技术、它们如何相关以及何时使用。</span><span class="sxs-lookup"><span data-stu-id="fa2c2-121">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>

## <a name="reference"></a><span data-ttu-id="fa2c2-122">参考</span><span class="sxs-lookup"><span data-stu-id="fa2c2-122">Reference</span></span>

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Description>

## <a name="related-sections"></a><span data-ttu-id="fa2c2-123">相关章节</span><span class="sxs-lookup"><span data-stu-id="fa2c2-123">Related sections</span></span>

- [<span data-ttu-id="fa2c2-124">概念性概述</span><span class="sxs-lookup"><span data-stu-id="fa2c2-124">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="fa2c2-125">入门教程</span><span class="sxs-lookup"><span data-stu-id="fa2c2-125">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="fa2c2-126">指南与最佳做法</span><span class="sxs-lookup"><span data-stu-id="fa2c2-126">Guidelines and Best Practices</span></span>](guidelines-and-best-practices.md)
- [<span data-ttu-id="fa2c2-127">Windows Communication Foundation 工具</span><span class="sxs-lookup"><span data-stu-id="fa2c2-127">Windows Communication Foundation Tools</span></span>](tools.md)
- [<span data-ttu-id="fa2c2-128">Windows Communication Foundation (WCF) 示例</span><span class="sxs-lookup"><span data-stu-id="fa2c2-128">Windows Communication Foundation (WCF) samples</span></span>](./samples/index.md)
- [<span data-ttu-id="fa2c2-129">入门</span><span class="sxs-lookup"><span data-stu-id="fa2c2-129">Getting Started</span></span>](./samples/getting-started-sample.md)
- [<span data-ttu-id="fa2c2-130">使用内联代码的 IIS 承载</span><span class="sxs-lookup"><span data-stu-id="fa2c2-130">IIS Hosting Using Inline Code</span></span>](./samples/iis-hosting-using-inline-code.md)
- [<span data-ttu-id="fa2c2-131">自承载</span><span class="sxs-lookup"><span data-stu-id="fa2c2-131">Self-Host</span></span>](./samples/self-host.md)
