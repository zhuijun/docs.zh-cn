---
title: WCF Web HTTP 编程模型
ms.date: 03/30/2017
helpviewer_keywords:
- web services programming model [WCF]
- POX
- REST
ms.assetid: 2312a8d3-b66e-4623-ba42-978434300c7f
ms.openlocfilehash: dd9cc282750e59e5ccbfec428c7252ab9689395f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589846"
---
# <a name="wcf-web-http-programming-model"></a><span data-ttu-id="7ed07-102">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="7ed07-102">WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="7ed07-103">利用 Windows Communication Foundation （WCF） Web HTTP 编程模型，开发人员可以向非 SOAP 终结点公开 WCF 服务操作。</span><span class="sxs-lookup"><span data-stu-id="7ed07-103">The Windows Communication Foundation (WCF) Web HTTP Programming Model allows developers to expose WCF service operations to non-SOAP endpoints.</span></span> <span data-ttu-id="7ed07-104">本节中的主题详细研究此功能。</span><span class="sxs-lookup"><span data-stu-id="7ed07-104">The topics in this section examine the feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ed07-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="7ed07-105">In This Section</span></span>  
 [<span data-ttu-id="7ed07-106">WCF Web HTTP 编程模型概述</span><span class="sxs-lookup"><span data-stu-id="7ed07-106">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)  
 <span data-ttu-id="7ed07-107">提供 Windows Communication Foundation （WCF） Web HTTP 编程模型的概述。</span><span class="sxs-lookup"><span data-stu-id="7ed07-107">Provides an overview of the Windows Communication Foundation (WCF) Web HTTP Programming Model.</span></span>  
  
 [<span data-ttu-id="7ed07-108">WCF Web HTTP 编程对象模型</span><span class="sxs-lookup"><span data-stu-id="7ed07-108">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)  
 <span data-ttu-id="7ed07-109">讨论 Windows Communication Foundation （WCF） Web HTTP 编程模型及其工作原理。</span><span class="sxs-lookup"><span data-stu-id="7ed07-109">Discusses the Windows Communication Foundation (WCF) Web HTTP Programming Model and how it works.</span></span>  
  
 [<span data-ttu-id="7ed07-110">如何：创建基本 WCF Web HTTP 服务</span><span class="sxs-lookup"><span data-stu-id="7ed07-110">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)  
 <span data-ttu-id="7ed07-111">说明如何编写公开非 SOAP 终结点的基本服务。</span><span class="sxs-lookup"><span data-stu-id="7ed07-111">Describes how to write a basic service that exposes a non-SOAP endpoint.</span></span>  
  
 [<span data-ttu-id="7ed07-112">如何：向 SOAP 和 Web 客户端公开协定</span><span class="sxs-lookup"><span data-stu-id="7ed07-112">How to: Expose a Contract to SOAP and Web Clients</span></span>](how-to-expose-a-contract-to-soap-and-web-clients.md)  
 <span data-ttu-id="7ed07-113">说明如何编写向 SOAP 和非 SOAP 客户端公开同一协定的基本服务。</span><span class="sxs-lookup"><span data-stu-id="7ed07-113">Describes how to write a basic service that exposes the same contract to both SOAP and non-SOAP clients.</span></span>  
  
 [<span data-ttu-id="7ed07-114">UriTemplate 和 UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="7ed07-114">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)  
 <span data-ttu-id="7ed07-115">说明如何使用 <xref:System.UriTemplate> 和 <xref:System.UriTemplateTable> 控制 URI。</span><span class="sxs-lookup"><span data-stu-id="7ed07-115">Describes how to control URIs using <xref:System.UriTemplate> and <xref:System.UriTemplateTable>.</span></span>  
  
 [<span data-ttu-id="7ed07-116">对 WCF Web HTTP 服务的缓存支持</span><span class="sxs-lookup"><span data-stu-id="7ed07-116">Caching Support for WCF Web HTTP Services</span></span>](caching-support-for-wcf-web-http-services.md)  
 <span data-ttu-id="7ed07-117">说明如何指定 WCF Web HTTP 服务的缓存行为。</span><span class="sxs-lookup"><span data-stu-id="7ed07-117">Describes how to specify caching behavior for a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="7ed07-118">WCF Web HTTP 格式设置</span><span class="sxs-lookup"><span data-stu-id="7ed07-118">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)  
 <span data-ttu-id="7ed07-119">说明如何指定 WCF Web HTTP 服务响应的格式。</span><span class="sxs-lookup"><span data-stu-id="7ed07-119">Describes how to specify the format of the response from a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="7ed07-120">WCF Web HTTP 错误处理</span><span class="sxs-lookup"><span data-stu-id="7ed07-120">WCF Web HTTP Error Handling</span></span>](wcf-web-http-error-handling.md)  
 <span data-ttu-id="7ed07-121">说明如何将错误返回 WCF Web 客户端，包括 HTTP 状态代码和用户定义的其他错误数据。</span><span class="sxs-lookup"><span data-stu-id="7ed07-121">Describes how to return errors to WCF Web clients including HTTP status codes and additional user-defined error data.</span></span>  
  
 [<span data-ttu-id="7ed07-122">从 WCF 服务调用 REST 样式服务</span><span class="sxs-lookup"><span data-stu-id="7ed07-122">Calling a REST-style service from a WCF service</span></span>](calling-a-rest-style-service-from-a-wcf-service.md)  
 <span data-ttu-id="7ed07-123">说明如何从 WCF 服务内部来调用 REST 样式服务。</span><span class="sxs-lookup"><span data-stu-id="7ed07-123">Describes how to call a REST-style service from inside a WCF service.</span></span>
