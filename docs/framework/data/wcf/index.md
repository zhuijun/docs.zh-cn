---
title: WCF 数据服务 4.5
description: 了解 WCF 数据服务，它是一个 .NET Framework 组件，它支持使用 REST 语义公开和使用数据的服务。
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: ca6b196e8c910f97ead6d1df5b6c0dd6c49c68a4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247748"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="504f5-103">WCF 数据服务 4.5</span><span class="sxs-lookup"><span data-stu-id="504f5-103">WCF Data Services 4.5</span></span>

<span data-ttu-id="504f5-104">WCF 数据服务（以前称为 "ADO.NET Data Services"）是 .NET Framework 的一个组件，它使你能够使用[具象状态传输（REST）](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)的语义创建使用 Open Data Protocol （OData）在 Web 或 intranet 上公开和使用数据的服务。</span><span class="sxs-lookup"><span data-stu-id="504f5-104">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="504f5-105">OData 将数据公开为可通过 URI 进行寻址的资源。</span><span class="sxs-lookup"><span data-stu-id="504f5-105">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="504f5-106">通过使用标准 HTTP 谓词 GET、PUT、POST 和 DELETE 访问和更改数据。</span><span class="sxs-lookup"><span data-stu-id="504f5-106">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="504f5-107">OData 使用[实体数据模型](../adonet/entity-data-model.md)的实体关系约定将资源公开为通过关联相关的实体集。</span><span class="sxs-lookup"><span data-stu-id="504f5-107">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="504f5-108">WCF 数据服务使用 OData 协议对资源进行寻址和更新。</span><span class="sxs-lookup"><span data-stu-id="504f5-108">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="504f5-109">通过这种方式，你可以从支持 OData 的任何客户端访问这些服务。</span><span class="sxs-lookup"><span data-stu-id="504f5-109">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="504f5-110">OData 使你可以通过使用众所周知的传输格式请求数据并将数据写入资源： Atom，一组用于以 XML 格式交换和更新数据的标准，以及 JavaScript 对象表示法（JSON），这是在 AJAX 应用程序中广泛使用的基于文本的数据交换格式。</span><span class="sxs-lookup"><span data-stu-id="504f5-110">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="504f5-111">WCF 数据服务可以将源自各种源的数据作为 OData 源公开。</span><span class="sxs-lookup"><span data-stu-id="504f5-111">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="504f5-112">Visual Studio 工具通过使用 ADO.NET 实体框架数据模型，使你可以更轻松地创建基于 OData 的服务。</span><span class="sxs-lookup"><span data-stu-id="504f5-112">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="504f5-113">还可以基于公共语言运行时（CLR）类，甚至是后期绑定或未类型化的数据来创建 OData 源。</span><span class="sxs-lookup"><span data-stu-id="504f5-113">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="504f5-114">WCF 数据服务还包括一组客户端库，一个用于一般 .NET Framework 客户端应用程序，另一个专用于基于 Silverlight 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="504f5-114">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="504f5-115">在从 .NET Framework 和 Silverlight 之类的环境访问 OData 源时，这些客户端库提供了基于对象的编程模型。</span><span class="sxs-lookup"><span data-stu-id="504f5-115">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="504f5-116">从何处开始？</span><span class="sxs-lookup"><span data-stu-id="504f5-116">Where Should I Start?</span></span>

<span data-ttu-id="504f5-117">根据你的兴趣，请考虑以下主题之一中的 WCF 数据服务入门。</span><span class="sxs-lookup"><span data-stu-id="504f5-117">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="504f5-118">我希望直接开始使用...</span><span class="sxs-lookup"><span data-stu-id="504f5-118">I want to jump right in...</span></span>

- [<span data-ttu-id="504f5-119">快速入门</span><span class="sxs-lookup"><span data-stu-id="504f5-119">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="504f5-120">入门</span><span class="sxs-lookup"><span data-stu-id="504f5-120">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="504f5-121">只显示一些代码 .。。</span><span class="sxs-lookup"><span data-stu-id="504f5-121">Just show me some code...</span></span>

- [<span data-ttu-id="504f5-122">快速入门</span><span class="sxs-lookup"><span data-stu-id="504f5-122">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="504f5-123">如何：执行数据服务查询</span><span class="sxs-lookup"><span data-stu-id="504f5-123">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="504f5-124">如何：将数据绑定到 Windows Presentation Foundation 元素</span><span class="sxs-lookup"><span data-stu-id="504f5-124">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="504f5-125">我想了解有关 OData 的详细信息 .。。</span><span class="sxs-lookup"><span data-stu-id="504f5-125">I want to know more about OData...</span></span>

- [<span data-ttu-id="504f5-126">白皮书： OData 简介</span><span class="sxs-lookup"><span data-stu-id="504f5-126">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="504f5-127">Open Data Protocol 网站</span><span class="sxs-lookup"><span data-stu-id="504f5-127">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="504f5-128">OData：SDK</span><span class="sxs-lookup"><span data-stu-id="504f5-128">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="504f5-129">我想要查看端到端示例 .。。</span><span class="sxs-lookup"><span data-stu-id="504f5-129">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="504f5-130">[WCF 数据服务快速入门](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="504f5-130">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="504f5-131">OData SDK-示例代码</span><span class="sxs-lookup"><span data-stu-id="504f5-131">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="504f5-132">它如何与 Visual Studio 集成？</span><span class="sxs-lookup"><span data-stu-id="504f5-132">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="504f5-133">生成数据服务客户端库</span><span class="sxs-lookup"><span data-stu-id="504f5-133">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="504f5-134">创建数据服务</span><span class="sxs-lookup"><span data-stu-id="504f5-134">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="504f5-135">实体框架提供程序</span><span class="sxs-lookup"><span data-stu-id="504f5-135">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="504f5-136">它的作用是什么？</span><span class="sxs-lookup"><span data-stu-id="504f5-136">What can I do with it?</span></span>

- [<span data-ttu-id="504f5-137">概述</span><span class="sxs-lookup"><span data-stu-id="504f5-137">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="504f5-138">应用程序方案</span><span class="sxs-lookup"><span data-stu-id="504f5-138">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="504f5-139">我想要使用 LINQ .。。</span><span class="sxs-lookup"><span data-stu-id="504f5-139">I want to use LINQ...</span></span>

- [<span data-ttu-id="504f5-140">查询数据服务</span><span class="sxs-lookup"><span data-stu-id="504f5-140">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="504f5-141">LINQ 注意事项</span><span class="sxs-lookup"><span data-stu-id="504f5-141">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="504f5-142">如何：执行数据服务查询</span><span class="sxs-lookup"><span data-stu-id="504f5-142">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="504f5-143">我仍然需要了解更多信息 .。。</span><span class="sxs-lookup"><span data-stu-id="504f5-143">I still need some more information...</span></span>

- <span data-ttu-id="504f5-144">[WCF Data Services Team Blog](https://docs.microsoft.com/archive/blogs/astoriateam/)（WCF Data Services 团队博客）</span><span class="sxs-lookup"><span data-stu-id="504f5-144">[WCF Data Services Team Blog](https://docs.microsoft.com/archive/blogs/astoriateam/)</span></span>

- [<span data-ttu-id="504f5-145">资源</span><span class="sxs-lookup"><span data-stu-id="504f5-145">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="504f5-146">本节内容</span><span class="sxs-lookup"><span data-stu-id="504f5-146">In This Section</span></span>

[<span data-ttu-id="504f5-147">概述</span><span class="sxs-lookup"><span data-stu-id="504f5-147">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="504f5-148">概述 WCF 数据服务中可用的特性和功能。</span><span class="sxs-lookup"><span data-stu-id="504f5-148">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="504f5-149">[WCF 数据服务5.0 的新增功能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="504f5-149">[What's New in WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="504f5-150">介绍 WCF 数据服务的新功能，并支持新的 OData 功能。</span><span class="sxs-lookup"><span data-stu-id="504f5-150">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="504f5-151">入门</span><span class="sxs-lookup"><span data-stu-id="504f5-151">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="504f5-152">介绍如何使用 WCF 数据服务公开和使用 OData 源。</span><span class="sxs-lookup"><span data-stu-id="504f5-152">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="504f5-153">定义 WCF 数据服务</span><span class="sxs-lookup"><span data-stu-id="504f5-153">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="504f5-154">介绍如何创建和配置公开 OData 源的数据服务。</span><span class="sxs-lookup"><span data-stu-id="504f5-154">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="504f5-155">WCF 数据服务客户端库</span><span class="sxs-lookup"><span data-stu-id="504f5-155">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="504f5-156">介绍如何使用客户端库从 .NET Framework 客户端应用程序中使用 OData 源。</span><span class="sxs-lookup"><span data-stu-id="504f5-156">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="504f5-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="504f5-157">See also</span></span>

- <span data-ttu-id="504f5-158">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)（表述性状态转移 (REST)）</span><span class="sxs-lookup"><span data-stu-id="504f5-158">[Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)</span></span>
