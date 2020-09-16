---
title: 保证应用程序的安全
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: af184f64b43c2d3dc39f8c0add08940d3b002c24
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550750"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="597d1-102">保护 ADO.NET 应用程序</span><span class="sxs-lookup"><span data-stu-id="597d1-102">Securing ADO.NET applications</span></span>

<span data-ttu-id="597d1-103">编写安全 ADO.NET 应用程序不仅仅是避免常见的编码缺陷（如不验证用户输入）。</span><span class="sxs-lookup"><span data-stu-id="597d1-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="597d1-104">访问数据的应用程序具有许多潜在的故障点，攻击者可以利用它们检索、操纵或破坏敏感数据。</span><span class="sxs-lookup"><span data-stu-id="597d1-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="597d1-105">因此，了解安全性的各个方面（从应用程序设计阶段期间的威胁建模过程到应用程序的最终部署和不断的维护）非常重要。</span><span class="sxs-lookup"><span data-stu-id="597d1-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
<span data-ttu-id="597d1-106">.NET Framework 提供了很多有用的类、服务和工具，以用于保证数据库应用程序的安全和对其进行管理。</span><span class="sxs-lookup"><span data-stu-id="597d1-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="597d1-107">公共语言运行库 (CLR) 提供了供代码在其中运行的类型安全环境，以及用于进一步限制托管代码权限的代码访问安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="597d1-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="597d1-108">遵循安全数据访问编码惯例可降低由潜在攻击者造成的损坏。</span><span class="sxs-lookup"><span data-stu-id="597d1-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
<span data-ttu-id="597d1-109">编写安全代码不会阻止在使用非托管资源（如数据库）时自己造成的安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="597d1-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="597d1-110">多数服务器数据库（如 SQL Server）拥有其各自的安全系统，正确实现这些安全系统可增强安全性。</span><span class="sxs-lookup"><span data-stu-id="597d1-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="597d1-111">但是，即使是具有可靠安全系统的数据源，如果未适当配置，也可能受到攻击。</span><span class="sxs-lookup"><span data-stu-id="597d1-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="597d1-112">在本节中</span><span class="sxs-lookup"><span data-stu-id="597d1-112">In this section</span></span>

 [<span data-ttu-id="597d1-113">安全性概述</span><span class="sxs-lookup"><span data-stu-id="597d1-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="597d1-114">提供对设计安全 ADO.NET 应用程序的建议。</span><span class="sxs-lookup"><span data-stu-id="597d1-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="597d1-115">安全数据访问</span><span class="sxs-lookup"><span data-stu-id="597d1-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="597d1-116">描述如何使用受保护数据源中的数据。</span><span class="sxs-lookup"><span data-stu-id="597d1-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="597d1-117">保证客户端应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="597d1-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="597d1-118">描述客户端应用程序的安全注意事项。</span><span class="sxs-lookup"><span data-stu-id="597d1-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="597d1-119">代码访问安全性和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="597d1-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="597d1-120">描述 CAS 如何帮助保护 ADO.NET 代码，</span><span class="sxs-lookup"><span data-stu-id="597d1-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="597d1-121">还讨论如何使用部分信任。</span><span class="sxs-lookup"><span data-stu-id="597d1-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="597d1-122">隐私和数据安全性</span><span class="sxs-lookup"><span data-stu-id="597d1-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="597d1-123">描述 ADO.NET 应用程序的加密选项。</span><span class="sxs-lookup"><span data-stu-id="597d1-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="597d1-124">相关章节</span><span class="sxs-lookup"><span data-stu-id="597d1-124">Related sections</span></span>

 [<span data-ttu-id="597d1-125">数据集和 DataTable 安全指南</span><span class="sxs-lookup"><span data-stu-id="597d1-125">DataSet and DataTable security guidance</span></span>](dataset-datatable-dataview/security-guidance.md)  
 <span data-ttu-id="597d1-126">提供和的安全 <xref:System.Data.DataSet> 指南 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="597d1-126">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="597d1-127">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="597d1-127">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="597d1-128">描述从开发人员角度来讲的 SQL Server 安全功能。</span><span class="sxs-lookup"><span data-stu-id="597d1-128">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="597d1-129">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="597d1-129">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="597d1-130">描述实体框架应用程序的安全性。</span><span class="sxs-lookup"><span data-stu-id="597d1-130">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="597d1-131">安全性</span><span class="sxs-lookup"><span data-stu-id="597d1-131">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="597d1-132">包含一些链接，这些链接指向介绍 .NET 中的所有安全方面的文章。</span><span class="sxs-lookup"><span data-stu-id="597d1-132">Contains links to articles describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="597d1-133">[安全性工具](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="597d1-133">[Security Tools](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="597d1-134">用于保证安全策略的安全和对其进行管理的 .NET Framework 工具。</span><span class="sxs-lookup"><span data-stu-id="597d1-134">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="597d1-135">[创建安全应用程序的资源](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="597d1-135">[Resources for Creating Secure Applications](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="597d1-136">提供指向用于创建安全应用程序的文章的链接。</span><span class="sxs-lookup"><span data-stu-id="597d1-136">Provides links to articles for creating secure applications.</span></span>  
  
 [<span data-ttu-id="597d1-137">安全参考书目</span><span class="sxs-lookup"><span data-stu-id="597d1-137">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="597d1-138">提供联机和印刷资料中提供的外部资源的链接。</span><span class="sxs-lookup"><span data-stu-id="597d1-138">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597d1-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="597d1-139">See also</span></span>

- [<span data-ttu-id="597d1-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="597d1-140">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="597d1-141">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="597d1-141">ADO.NET Overview</span></span>](ado-net-overview.md)
