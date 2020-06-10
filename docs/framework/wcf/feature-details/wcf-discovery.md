---
title: WCF Discovery
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 63c6589cb2ecff9f0a5e7c8bb61b454f6516c98c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600174"
---
# <a name="wcf-discovery"></a><span data-ttu-id="c0048-102">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="c0048-102">WCF Discovery</span></span>
<span data-ttu-id="c0048-103">Windows Communication Foundation （WCF）提供了支持，使得服务在运行时可通过使用 WS 发现协议以互操作方式发现。</span><span class="sxs-lookup"><span data-stu-id="c0048-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="c0048-104">WCF 服务可以使用多播消息或发现代理服务器向网络公布其可用性。</span><span class="sxs-lookup"><span data-stu-id="c0048-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="c0048-105">客户端应用程序可以搜索网络或发现代理服务器来查找满足一组条件的服务。</span><span class="sxs-lookup"><span data-stu-id="c0048-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="c0048-106">本节中的主题分别概述和详细介绍了此功能的编程模型。</span><span class="sxs-lookup"><span data-stu-id="c0048-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0048-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="c0048-107">In This Section</span></span>  
 [<span data-ttu-id="c0048-108">WCF Discovery 概述</span><span class="sxs-lookup"><span data-stu-id="c0048-108">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="c0048-109">概述 WCF 提供的 WS 发现支持。</span><span class="sxs-lookup"><span data-stu-id="c0048-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="c0048-110">WCF Discovery 对象模型</span><span class="sxs-lookup"><span data-stu-id="c0048-110">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="c0048-111">描述对象模型中的类和 WS-Discovery 支持的扩展性。</span><span class="sxs-lookup"><span data-stu-id="c0048-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="c0048-112">如何：以编程方式向 WCF 服务和客户端添加可发现性</span><span class="sxs-lookup"><span data-stu-id="c0048-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="c0048-113">演示如何使 Windows Communication Foundation （WCF）服务可发现。</span><span class="sxs-lookup"><span data-stu-id="c0048-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="c0048-114">实现发现代理</span><span class="sxs-lookup"><span data-stu-id="c0048-114">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="c0048-115">描述一些必需步骤，这些步骤用于实现发现代理、注册到发现代理的可检测服务以及使用发现代理查找可检测服务的客户端。</span><span class="sxs-lookup"><span data-stu-id="c0048-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="c0048-116">发现版本控制</span><span class="sxs-lookup"><span data-stu-id="c0048-116">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="c0048-117">简要概述了一些新发现功能的原型实现，</span><span class="sxs-lookup"><span data-stu-id="c0048-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="c0048-118">还概述了如何选择要使用的发现版本。</span><span class="sxs-lookup"><span data-stu-id="c0048-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="c0048-119">在配置文件中配置发现</span><span class="sxs-lookup"><span data-stu-id="c0048-119">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="c0048-120">演示如何在配置中配置 Discovery。</span><span class="sxs-lookup"><span data-stu-id="c0048-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="c0048-121">使用 Discovery 客户端通道</span><span class="sxs-lookup"><span data-stu-id="c0048-121">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="c0048-122">演示如何在编写 WCF 客户端应用程序时使用发现客户端通道。</span><span class="sxs-lookup"><span data-stu-id="c0048-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
