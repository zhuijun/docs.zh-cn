---
title: 工厂模型概述
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 7cee3966ab3a37d2dbc6dd0ea9ab26b485ef63fd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156389"
---
# <a name="factory-model-overview"></a><span data-ttu-id="38a0c-102">工厂模型概述</span><span class="sxs-lookup"><span data-stu-id="38a0c-102">Factory Model Overview</span></span>

<span data-ttu-id="38a0c-103">ADO.NET 2.0 在 <xref:System.Data.Common> 命名空间中引入了新基类。</span><span class="sxs-lookup"><span data-stu-id="38a0c-103">ADO.NET 2.0 introduced new base classes in the <xref:System.Data.Common> namespace.</span></span> <span data-ttu-id="38a0c-104">基类为抽象类，这意味着它们不能直接实例化。</span><span class="sxs-lookup"><span data-stu-id="38a0c-104">The base classes are abstract, which means that they can't be directly instantiated.</span></span> <span data-ttu-id="38a0c-105">这些基类包括 <xref:System.Data.Common.DbConnection>、<xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbDataAdapter>，它们由 .NET Framework 数据提供程序（如 <xref:System.Data.SqlClient> 和 <xref:System.Data.OleDb>）共享。</span><span class="sxs-lookup"><span data-stu-id="38a0c-105">They include <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, and <xref:System.Data.Common.DbDataAdapter> and are shared by the .NET Framework data providers, such as <xref:System.Data.SqlClient> and <xref:System.Data.OleDb>.</span></span> <span data-ttu-id="38a0c-106">添加基类简化了向 .NET Framework 数据提供程序添加功能的过程，不再需要创建新接口。</span><span class="sxs-lookup"><span data-stu-id="38a0c-106">The addition of base classes simplifies adding functionality to the .NET Framework data providers without having to create new interfaces.</span></span>  
  
 <span data-ttu-id="38a0c-107">ADO.NET 2.0 中还引入了一些抽象基类，使开发人员能够编写不依赖于特定数据提供程序的一般数据访问代码。</span><span class="sxs-lookup"><span data-stu-id="38a0c-107">ADO.NET 2.0 also introduced abstract base classes, which enable a developer to write generic data access code that does not depend on a specific data provider.</span></span>  
  
## <a name="the-factory-design-pattern"></a><span data-ttu-id="38a0c-108">工厂设计模式</span><span class="sxs-lookup"><span data-stu-id="38a0c-108">The Factory Design Pattern</span></span>  

 <span data-ttu-id="38a0c-109">编写独立于提供程序的代码的编程模型基于“工厂”设计模式的使用，此模式使用单个 API 跨多个提供程序访问数据库。</span><span class="sxs-lookup"><span data-stu-id="38a0c-109">The programming model for writing provider-independent code is based on the use of the "factory" design pattern, which uses a single API to access databases across multiple providers.</span></span> <span data-ttu-id="38a0c-110">此模式的命名非常恰当，因为它需单独使用专用的对象来创建其他对象，与实际的工厂非常类似。</span><span class="sxs-lookup"><span data-stu-id="38a0c-110">This pattern is aptly named, as it calls for the use of a specialized object solely to create other objects, much like a real-world factory.</span></span> <span data-ttu-id="38a0c-111">有关工厂设计模式的更详细说明，请参阅 [在 ASP.NET 2.0 和 ADO.NET 2.0 中编写通用数据访问代码](/previous-versions/dotnet/articles/ms971499(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="38a0c-111">For a more detailed description of the factory design pattern, see [Writing Generic Data Access Code in ASP.NET 2.0 and ADO.NET 2.0](/previous-versions/dotnet/articles/ms971499(v=msdn.10)).</span></span>
  
 <span data-ttu-id="38a0c-112">从 ADO.NET 2.0 开始，<xref:System.Data.Common.DbProviderFactories> 类提供 `static`（或 Visual Basic 中的 `Shared`）方法以用于创建 <xref:System.Data.Common.DbProviderFactory> 实例。</span><span class="sxs-lookup"><span data-stu-id="38a0c-112">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbProviderFactories> class provides `static` (or `Shared` in Visual Basic) methods for creating a <xref:System.Data.Common.DbProviderFactory> instance.</span></span> <span data-ttu-id="38a0c-113">该实例随后会基于提供程序信息和运行时提供的连接字符串返回正确的强类型对象。</span><span class="sxs-lookup"><span data-stu-id="38a0c-113">The instance then returns a correct strongly typed object based on provider information and the connection string supplied at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a0c-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="38a0c-114">See also</span></span>

- [<span data-ttu-id="38a0c-115">获取 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="38a0c-115">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="38a0c-116">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="38a0c-116">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="38a0c-117">使用 DbDataAdapter 修改数据</span><span class="sxs-lookup"><span data-stu-id="38a0c-117">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="38a0c-118">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="38a0c-118">ADO.NET Overview</span></span>](ado-net-overview.md)
