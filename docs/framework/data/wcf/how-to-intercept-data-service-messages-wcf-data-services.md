---
title: 如何：截获数据服务消息（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: 8cc8bdcf776befafba967ee2649a6ada789d07c5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194357"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="36ccb-102">如何：截获数据服务消息（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="36ccb-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>

<span data-ttu-id="36ccb-103">使用 WCF 数据服务，可以截获请求消息，以便可以向操作添加自定义逻辑。</span><span class="sxs-lookup"><span data-stu-id="36ccb-103">With WCF Data Services, you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="36ccb-104">若要截获消息，请使用数据服务中的专门特性化的方法。</span><span class="sxs-lookup"><span data-stu-id="36ccb-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="36ccb-105">有关详细信息，请参阅 [拦截](interceptors-wcf-data-services.md)程序。</span><span class="sxs-lookup"><span data-stu-id="36ccb-105">For more information, see [Interceptors](interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="36ccb-106">本主题中的示例使用 Northwind 示例数据服务。</span><span class="sxs-lookup"><span data-stu-id="36ccb-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="36ccb-107">此服务是在完成 [WCF 数据服务快速入门](quickstart-wcf-data-services.md)时创建的。</span><span class="sxs-lookup"><span data-stu-id="36ccb-107">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="36ccb-108">为 Orders 实体集定义查询侦听器</span><span class="sxs-lookup"><span data-stu-id="36ccb-108">To define a query interceptor for the Orders entity set</span></span>  
  
1. <span data-ttu-id="36ccb-109">在 Northwind 数据服务项目中，打开 Northwind.svc 文件。</span><span class="sxs-lookup"><span data-stu-id="36ccb-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="36ccb-110">在 `Northwind` 类的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）。</span><span class="sxs-lookup"><span data-stu-id="36ccb-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. <span data-ttu-id="36ccb-111">在 `Northwind` 类中，定义一个名为 `OnQueryOrders` 的服务操作方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="36ccb-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="36ccb-112">为 Products 实体集定义变更侦听器</span><span class="sxs-lookup"><span data-stu-id="36ccb-112">To define a change interceptor for the Products entity set</span></span>  
  
1. <span data-ttu-id="36ccb-113">在 Northwind 数据服务项目中，打开 Northwind.svc 文件。</span><span class="sxs-lookup"><span data-stu-id="36ccb-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="36ccb-114">在 `Northwind` 类中，定义一个名为 `OnChangeProducts` 的服务操作方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="36ccb-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="36ccb-115">示例</span><span class="sxs-lookup"><span data-stu-id="36ccb-115">Example</span></span>  

 <span data-ttu-id="36ccb-116">下面的示例为 `Orders` 实体集定义一个返回 lambda 表达式的查询侦听器方法。</span><span class="sxs-lookup"><span data-stu-id="36ccb-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="36ccb-117">此表达式包含一个委托，该委托基于具有特定联系人姓名的相关 `Orders` 筛选所请求的 `Customers`。</span><span class="sxs-lookup"><span data-stu-id="36ccb-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="36ccb-118">该姓名反过来又由请求的用户确定。</span><span class="sxs-lookup"><span data-stu-id="36ccb-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="36ccb-119">此示例假定数据服务承载在使用 WCF 的 ASP.NET Web 应用程序中，并且已启用身份验证。</span><span class="sxs-lookup"><span data-stu-id="36ccb-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="36ccb-120"><xref:System.Web.HttpContext> 类用于检索当前请求的原则。</span><span class="sxs-lookup"><span data-stu-id="36ccb-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="36ccb-121">示例</span><span class="sxs-lookup"><span data-stu-id="36ccb-121">Example</span></span>  

 <span data-ttu-id="36ccb-122">下面的示例为 `Products` 实体集定义变更侦听器方法。</span><span class="sxs-lookup"><span data-stu-id="36ccb-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="36ccb-123">此方法验证对该服务的 <xref:System.Data.Services.UpdateOperations.Add> 或 <xref:System.Data.Services.UpdateOperations.Change> 操作的输入，如果对断货的产品进行更改，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="36ccb-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="36ccb-124">此方法还将删除产品操作视为不支持的操作，从而阻止这一操作。</span><span class="sxs-lookup"><span data-stu-id="36ccb-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="36ccb-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="36ccb-125">See also</span></span>

- [<span data-ttu-id="36ccb-126">如何：定义服务操作</span><span class="sxs-lookup"><span data-stu-id="36ccb-126">How to: Define a Service Operation</span></span>](how-to-define-a-service-operation-wcf-data-services.md)
- [<span data-ttu-id="36ccb-127">定义 WCF 数据服务</span><span class="sxs-lookup"><span data-stu-id="36ccb-127">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
