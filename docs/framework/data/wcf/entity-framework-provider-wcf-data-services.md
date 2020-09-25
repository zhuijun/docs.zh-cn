---
title: 实体框架提供程序（WCF 数据服务）
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: cb7bd7e793f73fc34057150ee5217dba6653237e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172640"
---
# <a name="entity-framework-provider-wcf-data-services"></a><span data-ttu-id="cc65e-102">实体框架提供程序（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="cc65e-102">Entity Framework Provider (WCF Data Services)</span></span>

<span data-ttu-id="cc65e-103">与 WCF 数据服务一样，ADO.NET 实体框架基于实体数据模型，这是一种实体关系模型。</span><span class="sxs-lookup"><span data-stu-id="cc65e-103">Like WCF Data Services, the ADO.NET Entity Framework is based on the Entity Data Model, which is a type of entity-relationship model.</span></span> <span data-ttu-id="cc65e-104">实体框架将操作转换为其对实体数据模型（称为 *概念模型*）的实现，以对数据源执行等效操作。</span><span class="sxs-lookup"><span data-stu-id="cc65e-104">The Entity Framework translates operations against its implementation of the Entity Data Model, which is called the *conceptual model*, into equivalent operations against a data source.</span></span> <span data-ttu-id="cc65e-105">这使实体框架成为基于关系数据的数据服务的理想提供程序，任何具有支持实体框架的数据访问接口的数据库均可与 WCF 数据服务结合使用。</span><span class="sxs-lookup"><span data-stu-id="cc65e-105">This makes the Entity Framework an ideal provider for data services that are based on relational data, and any database that has a data provider that supports the Entity Framework can be used with WCF Data Services.</span></span> <span data-ttu-id="cc65e-106">有关当前支持实体框架的数据源的列表，请参阅 [实体框架提供程序](/ef/ef6/fundamentals/providers/)。</span><span class="sxs-lookup"><span data-stu-id="cc65e-106">For a list of the data sources that currently support the Entity Framework, see [Entity Framework Providers](/ef/ef6/fundamentals/providers/).</span></span>
  
 <span data-ttu-id="cc65e-107">在概念模型中，实体容器是服务的根。</span><span class="sxs-lookup"><span data-stu-id="cc65e-107">In a conceptual model, the entity container is the root of the service.</span></span> <span data-ttu-id="cc65e-108">必须先在实体框架中定义一个概念模型，数据服务才能公开数据。</span><span class="sxs-lookup"><span data-stu-id="cc65e-108">You must define a conceptual model in the Entity Framework before the data can be exposed by a data service.</span></span> <span data-ttu-id="cc65e-109">有关详细信息，请参阅 [如何：使用 ADO.NET 实体框架数据源创建数据服务](create-a-data-service-using-an-adonet-ef-data-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="cc65e-109">For more information, see [How to: Create a Data Service Using an ADO.NET Entity Framework Data Source](create-a-data-service-using-an-adonet-ef-data-wcf.md).</span></span>  
  
 <span data-ttu-id="cc65e-110">通过使你能够为实体定义并发标记，WCF 数据服务支持开放式并发模型。</span><span class="sxs-lookup"><span data-stu-id="cc65e-110">WCF Data Services supports the optimistic concurrency model by enabling you to define a concurrency token for an entity.</span></span> <span data-ttu-id="cc65e-111">这样一个包含一个或多个实体属性的并发标记由数据服务用来确定，正在请求、更新或删除的数据中是否发生了更改。</span><span class="sxs-lookup"><span data-stu-id="cc65e-111">This concurrency token, which includes one or more properties of the entity, is used by the data service to determine whether a change has occurred in the data that is being requested, updated, or deleted.</span></span> <span data-ttu-id="cc65e-112">如果从请求的 eTag 中获取的标记值与实体的当前值不相同，则数据服务将引发异常。</span><span class="sxs-lookup"><span data-stu-id="cc65e-112">When token values obtained from the eTag in the request differ from the current values of the entity, an exception is raised by the data service.</span></span> <span data-ttu-id="cc65e-113">若要指示某个属性是并发标记的一部分，必须 `ConcurrencyMode="Fixed"` 在由实体框架提供程序定义的数据模型中应用该属性。</span><span class="sxs-lookup"><span data-stu-id="cc65e-113">To indicate that a property is part of the concurrency token, you must apply the attribute `ConcurrencyMode="Fixed"` in the data model defined by the Entity Framework provider.</span></span> <span data-ttu-id="cc65e-114">并发标记不能包含键属性或导航属性。</span><span class="sxs-lookup"><span data-stu-id="cc65e-114">The concurrency token cannot include a key property or a navigation property.</span></span> <span data-ttu-id="cc65e-115">有关详细信息，请参阅 [更新数据服务](updating-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cc65e-115">For more information, see [Updating the Data Service](updating-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="cc65e-116">若要详细了解实体框架，请参阅 [实体框架概述](../adonet/ef/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cc65e-116">To learn more about the Entity Framework, see [Entity Framework Overview](../adonet/ef/overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc65e-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="cc65e-117">See also</span></span>

- [<span data-ttu-id="cc65e-118">数据服务提供程序</span><span class="sxs-lookup"><span data-stu-id="cc65e-118">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="cc65e-119">反射提供程序</span><span class="sxs-lookup"><span data-stu-id="cc65e-119">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
- [<span data-ttu-id="cc65e-120">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="cc65e-120">Entity Data Model</span></span>](../adonet/entity-data-model.md)
