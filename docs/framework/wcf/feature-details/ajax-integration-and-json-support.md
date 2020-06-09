---
title: AJAX 集成和 JSON 支持
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 3054c3c6faa8dfe621c706d8df031c23d497da0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576507"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="41df1-102">AJAX 集成和 JSON 支持</span><span class="sxs-lookup"><span data-stu-id="41df1-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="41df1-103">Windows Communication Foundation （WCF）对 ASP.NET 异步 JavaScript 和 XML （AJAX）和 JavaScript 对象表示法（JSON）数据格式的支持允许 WCF 服务向 AJAX 客户端公开操作。</span><span class="sxs-lookup"><span data-stu-id="41df1-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="41df1-104">AJAX 客户端是运行 JavaScript 代码并使用 HTTP 请求访问这些 WCF 服务的网页。</span><span class="sxs-lookup"><span data-stu-id="41df1-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="41df1-105">本节中的主题提供有关此支持以及如何实现此支持的信息。</span><span class="sxs-lookup"><span data-stu-id="41df1-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="41df1-106">有关 ASP.NET AJAX 及其与 ASP.NET 2.0 的集成的详细信息，请参阅[ASP.NET Ajax 概述](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="41df1-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41df1-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="41df1-107">In This Section</span></span>  
 [<span data-ttu-id="41df1-108">为 ASP.NET AJAX 创建 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="41df1-108">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="41df1-109">介绍如何通过以下方式向 AJAX 客户端公开 WCF 服务：添加适当的 AJAX 终结点：通过配置，或使用自定义的服务主机工厂生成自动配置 AJAX 终结点的服务主机。</span><span class="sxs-lookup"><span data-stu-id="41df1-109">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="41df1-110">创建不使用 ASP.NET 的 WCF AJAX 服务</span><span class="sxs-lookup"><span data-stu-id="41df1-110">Creating WCF AJAX Services without ASP.NET</span></span>](creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="41df1-111">介绍如何在不使用 ASP.NET 的情况下创建 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="41df1-111">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="41df1-112">对 JSON 和其他数据传输格式的支持</span><span class="sxs-lookup"><span data-stu-id="41df1-112">Support for JSON and Other Data Transfer Formats</span></span>](support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="41df1-113">描述对通常用于与 ASP.NET AJAX 服务进行通信的 JSON 格式（替代 XML）的支持。</span><span class="sxs-lookup"><span data-stu-id="41df1-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="41df1-114">如何：将支持 AJAX 的 ASP.NET Web 服务迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="41df1-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="41df1-115">介绍如何将启用了 AJAX 的 ASP.NET Web 服务迁移到 WCF Web 服务。</span><span class="sxs-lookup"><span data-stu-id="41df1-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41df1-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="41df1-116">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="41df1-117">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="41df1-117">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
