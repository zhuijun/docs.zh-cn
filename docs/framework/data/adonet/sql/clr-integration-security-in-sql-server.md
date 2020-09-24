---
title: SQL Server 中的 CLR 集成安全性
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: e5d15b4e5ac36f7ecddf45179c65a60995a1a578
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147770"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="6fde6-102">SQL Server 中的 CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="6fde6-102">CLR Integration Security in SQL Server</span></span>

<span data-ttu-id="6fde6-103">Microsoft SQL Server 提供 .NET Framework 的公共语言运行时 (CLR) 组件集成。</span><span class="sxs-lookup"><span data-stu-id="6fde6-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="6fde6-104">通过 CLR 集成，您可以使用任何 .NET Framework 语言（如 Microsoft Visual Basic .NET 或 Microsoft Visual C#）编写存储过程、触发器、用户定义的类型、用户定义的函数、用户定义的聚合以及流式表值函数。</span><span class="sxs-lookup"><span data-stu-id="6fde6-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="6fde6-105">CLR 支持一种用于托管代码的安全模型，称为代码访问安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="6fde6-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="6fde6-106">在此模型中，将根据元数据中代码提供的证据向程序集授予权限。</span><span class="sxs-lookup"><span data-stu-id="6fde6-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="6fde6-107">SQL Server 将 SQL Server 的基于用户的安全模型与 CLR 的基于代码启用的安全模型相集成。</span><span class="sxs-lookup"><span data-stu-id="6fde6-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="6fde6-108">外部资源</span><span class="sxs-lookup"><span data-stu-id="6fde6-108">External Resources</span></span>  

 <span data-ttu-id="6fde6-109">有关 CLR 与 SQL Server 集成的更多信息，请参见下列资源。</span><span class="sxs-lookup"><span data-stu-id="6fde6-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="6fde6-110">资源</span><span class="sxs-lookup"><span data-stu-id="6fde6-110">Resource</span></span>|<span data-ttu-id="6fde6-111">说明</span><span class="sxs-lookup"><span data-stu-id="6fde6-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="6fde6-112">代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="6fde6-112">Code Access Security</span></span>](../../../misc/code-access-security.md)|<span data-ttu-id="6fde6-113">包含描述 .NET Framework 中 CAS 的主题。</span><span class="sxs-lookup"><span data-stu-id="6fde6-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="6fde6-114">CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="6fde6-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="6fde6-115">讨论在 SQL Server 内部执行的托管代码的安全模型。</span><span class="sxs-lookup"><span data-stu-id="6fde6-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fde6-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="6fde6-116">See also</span></span>

- [<span data-ttu-id="6fde6-117">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="6fde6-117">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="6fde6-118">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="6fde6-118">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="6fde6-119">SQL Server 公共语言运行时集成</span><span class="sxs-lookup"><span data-stu-id="6fde6-119">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="6fde6-120">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="6fde6-120">ADO.NET Overview</span></span>](../ado-net-overview.md)
