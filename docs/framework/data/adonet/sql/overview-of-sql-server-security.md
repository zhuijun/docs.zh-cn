---
title: SQL Server 安全性概述
description: 了解 SQL Server 安全体系结构，以了解哪些特性和功能应对已知的威胁，并预测将来的威胁。
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: ba396774e760a550246d0f0507984d3f7212204b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172653"
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="26a9a-103">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="26a9a-103">Overview of SQL Server Security</span></span>

<span data-ttu-id="26a9a-104">具有重叠安全层的全面防御策略是抵御安全威胁的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="26a9a-104">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="26a9a-105">SQL Server 提供的安全体系结构旨在允许数据库管理员和开发人员创建安全的数据库应用程序并抵御威胁。</span><span class="sxs-lookup"><span data-stu-id="26a9a-105">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="26a9a-106">通过引入新功能，SQL Server 的每个版本都在先前的 SQL Server 版本基础上得到改善。</span><span class="sxs-lookup"><span data-stu-id="26a9a-106">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="26a9a-107">但是，安全性并不是现成的。</span><span class="sxs-lookup"><span data-stu-id="26a9a-107">However, security does not ship in the box.</span></span> <span data-ttu-id="26a9a-108">每个应用程序都具有其独特的安全要求。</span><span class="sxs-lookup"><span data-stu-id="26a9a-108">Each application is unique in its security requirements.</span></span> <span data-ttu-id="26a9a-109">开发人员需要了解哪些功能组合最适合抵御已知的威胁，并需要预见未来可能出现的威胁。</span><span class="sxs-lookup"><span data-stu-id="26a9a-109">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="26a9a-110">SQL Server 实例包含以服务器为首的实体的分层集合。</span><span class="sxs-lookup"><span data-stu-id="26a9a-110">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="26a9a-111">每个服务器均包含多个数据库，而每个数据库均包含可保护对象的集合。</span><span class="sxs-lookup"><span data-stu-id="26a9a-111">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="26a9a-112">每个 SQL Server 安全对象都有可以授予主体的关联 *权限* ，该 *主体*是授予访问 SQL Server 的个人、组或进程。</span><span class="sxs-lookup"><span data-stu-id="26a9a-112">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="26a9a-113">SQL Server 安全框架通过 *身份验证* 和 *授权*管理对安全实体的访问。</span><span class="sxs-lookup"><span data-stu-id="26a9a-113">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
- <span data-ttu-id="26a9a-114">身份验证是指通过提交服务器评估的凭据以登录到主体请求访问的 SQL Server 的过程。</span><span class="sxs-lookup"><span data-stu-id="26a9a-114">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="26a9a-115">身份验证可以确定接受身份验证的用户或进程的标识。</span><span class="sxs-lookup"><span data-stu-id="26a9a-115">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
- <span data-ttu-id="26a9a-116">授权是确定主体可以访问哪些安全对象资源以及哪些操作允许用于这些资源的过程。</span><span class="sxs-lookup"><span data-stu-id="26a9a-116">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="26a9a-117">本节中的主题介绍 SQL Server 安全基础知识，并提供到相关版本 SQL Server 联机丛书中完整文档的链接。</span><span class="sxs-lookup"><span data-stu-id="26a9a-117">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26a9a-118">本节内容</span><span class="sxs-lookup"><span data-stu-id="26a9a-118">In This Section</span></span>  

 [<span data-ttu-id="26a9a-119">SQL Server 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="26a9a-119">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)  
 <span data-ttu-id="26a9a-120">介绍了 SQL Server 登录和身份验证，并收录了其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="26a9a-120">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="26a9a-121">SQL Server 中的服务器和数据库角色</span><span class="sxs-lookup"><span data-stu-id="26a9a-121">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="26a9a-122">说明固定服务器和数据库角色、自定义数据库角色和内置帐户，并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="26a9a-122">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="26a9a-123">SQL Server 中的所有权和用户架构分离</span><span class="sxs-lookup"><span data-stu-id="26a9a-123">Ownership and User-Schema Separation in SQL Server</span></span>](ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="26a9a-124">说明对象所属权和用户架构分离，并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="26a9a-124">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="26a9a-125">SQL Server 中的授权和权限</span><span class="sxs-lookup"><span data-stu-id="26a9a-125">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="26a9a-126">说明使用最低特权原则授予权限并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="26a9a-126">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="26a9a-127">SQL Server 中的数据加密</span><span class="sxs-lookup"><span data-stu-id="26a9a-127">Data Encryption in SQL Server</span></span>](data-encryption-in-sql-server.md)  
 <span data-ttu-id="26a9a-128">说明 SQL Server 中的数据加密选项并提供到其他资源的链接。</span><span class="sxs-lookup"><span data-stu-id="26a9a-128">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="26a9a-129">SQL Server 中的 CLR 集成安全性</span><span class="sxs-lookup"><span data-stu-id="26a9a-129">CLR Integration Security in SQL Server</span></span>](clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="26a9a-130">提供到 CLR 集成安全资源的链接。</span><span class="sxs-lookup"><span data-stu-id="26a9a-130">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a9a-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="26a9a-131">See also</span></span>

- [<span data-ttu-id="26a9a-132">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="26a9a-132">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="26a9a-133">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="26a9a-133">SQL Server Security</span></span>](sql-server-security.md)
- [<span data-ttu-id="26a9a-134">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="26a9a-134">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="26a9a-135">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="26a9a-135">ADO.NET Overview</span></span>](../ado-net-overview.md)
