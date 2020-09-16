---
title: 如何：启用对数据服务的访问（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 377b031c48ed831cfa5e270426283ed03a55f886
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542302"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="64f8d-102">如何：启用对数据服务的访问（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="64f8d-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="64f8d-103">在 WCF 数据服务中，必须显式授予对数据服务公开的资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="64f8d-103">In WCF Data Services, you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="64f8d-104">这意味着您在创建新的数据服务之后，仍必须显式提供对实体集形式的各个资源的访问。</span><span class="sxs-lookup"><span data-stu-id="64f8d-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="64f8d-105">本主题演示如何启用对 Northwind 数据服务中的五个实体集的读写访问，这些实体集是在完成 [快速入门](quickstart-wcf-data-services.md)时创建的。</span><span class="sxs-lookup"><span data-stu-id="64f8d-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="64f8d-106">由于 <xref:System.Data.Services.EntitySetRights> 枚举是通过使用 <xref:System.FlagsAttribute> 定义的，因此您可以使用逻辑 OR 运算符来为单个实体集指定多个权限。</span><span class="sxs-lookup"><span data-stu-id="64f8d-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64f8d-107">任何可以访问该 ASP.NET 应用程序的客户端也能够访问由数据服务公开的资源。</span><span class="sxs-lookup"><span data-stu-id="64f8d-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="64f8d-108">在生产数据服务中，为防止对资源进行未经授权的访问，还应保护应用程序本身的安全。</span><span class="sxs-lookup"><span data-stu-id="64f8d-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="64f8d-109">有关详细信息，请参阅 [保护 ASP.NET 网站](/previous-versions/aspnet/91f66yxt(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="64f8d-109">For more information, see [Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="64f8d-110">启用对数据服务的访问</span><span class="sxs-lookup"><span data-stu-id="64f8d-110">To enable access to the data service</span></span>  
  
- <span data-ttu-id="64f8d-111">在数据服务的代码中，用下列代码替换 `InitializeService` 函数中的占位符代码：</span><span class="sxs-lookup"><span data-stu-id="64f8d-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="64f8d-112">这使得客户端能够对 `Orders` 和 `Order_Details` 实体集进行读写访问，以及对 `Customers` 实体集进行只读访问。</span><span class="sxs-lookup"><span data-stu-id="64f8d-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f8d-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="64f8d-113">See also</span></span>

- [<span data-ttu-id="64f8d-114">如何：开发在 IIS 上运行的 WCF 数据服务</span><span class="sxs-lookup"><span data-stu-id="64f8d-114">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="64f8d-115">配置数据服务</span><span class="sxs-lookup"><span data-stu-id="64f8d-115">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
