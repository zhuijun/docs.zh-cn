---
title: 如何：启用数据服务结果分页（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 1c8bb8fe757c35f6096b139da6ca939b1ce1c283
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150617"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="cf10e-102">如何：启用数据服务结果分页（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="cf10e-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>

<span data-ttu-id="cf10e-103">WCF 数据服务使你能够限制数据服务查询返回的实体数。</span><span class="sxs-lookup"><span data-stu-id="cf10e-103">WCF Data Services enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="cf10e-104">页限制在初始化服务时调用的方法中定义，并可为每个实体集单独设置页限制。</span><span class="sxs-lookup"><span data-stu-id="cf10e-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="cf10e-105">启用分页后，源中的最后一项包含指向下一页数据的链接。</span><span class="sxs-lookup"><span data-stu-id="cf10e-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="cf10e-106">有关详细信息，请参阅 [配置数据服务](configuring-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cf10e-106">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="cf10e-107">本主题介绍如何修改数据服务以启用返回的 `Customers` 和 `Orders` 实体集的分页。</span><span class="sxs-lookup"><span data-stu-id="cf10e-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="cf10e-108">本主题中的示例使用 Northwind 示例数据服务。</span><span class="sxs-lookup"><span data-stu-id="cf10e-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="cf10e-109">此服务是在完成 [WCF 数据服务快速入门](quickstart-wcf-data-services.md)时创建的。</span><span class="sxs-lookup"><span data-stu-id="cf10e-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="cf10e-110">如何启用返回的 Customers 和 Orders 实体集的分页</span><span class="sxs-lookup"><span data-stu-id="cf10e-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="cf10e-111">在数据服务的代码中，用下列代码替换 `InitializeService` 函数中的占位符代码：</span><span class="sxs-lookup"><span data-stu-id="cf10e-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="cf10e-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="cf10e-112">See also</span></span>

- [<span data-ttu-id="cf10e-113">加载延迟的内容</span><span class="sxs-lookup"><span data-stu-id="cf10e-113">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="cf10e-114">如何：加载分页结果</span><span class="sxs-lookup"><span data-stu-id="cf10e-114">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
