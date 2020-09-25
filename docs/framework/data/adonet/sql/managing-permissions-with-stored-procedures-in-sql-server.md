---
title: 在 SQL Server 中使用存储过程管理权限
description: 了解如何通过使用存储过程或用户定义函数实现访问权限来限制对数据和数据库对象的访问。
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: 44f6a0c3ca6b913c8998c4e5ddb60eab2b64e71b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172718"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a><span data-ttu-id="397f7-103">在 SQL Server 中使用存储过程管理权限</span><span class="sxs-lookup"><span data-stu-id="397f7-103">Managing Permissions with Stored Procedures in SQL Server</span></span>

<span data-ttu-id="397f7-104">为数据库创建多道防线的一个方法是使用存储过程或用户定义的函数实现所有数据访问。</span><span class="sxs-lookup"><span data-stu-id="397f7-104">One method of creating multiple lines of defense around your database is to implement all data access using stored procedures or user-defined functions.</span></span> <span data-ttu-id="397f7-105">撤消或拒绝对基础对象（如表）的所有权限，并授予对存储过程的 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="397f7-105">You revoke or deny all permissions to underlying objects, such as tables, and grant EXECUTE permissions on stored procedures.</span></span> <span data-ttu-id="397f7-106">这会为数据和数据库对象有效创建安全外围防线。</span><span class="sxs-lookup"><span data-stu-id="397f7-106">This effectively creates a security perimeter around your data and database objects.</span></span>  
  
## <a name="stored-procedure-benefits"></a><span data-ttu-id="397f7-107">存储过程的优点</span><span class="sxs-lookup"><span data-stu-id="397f7-107">Stored Procedure Benefits</span></span>  

 <span data-ttu-id="397f7-108">存储过程具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="397f7-108">Stored procedures have the following benefits:</span></span>  
  
- <span data-ttu-id="397f7-109">可以包装数据逻辑和业务规则，以便用户可以仅通过开发人员和数据库管理员打算使用的方式访问数据和对象。</span><span class="sxs-lookup"><span data-stu-id="397f7-109">Data logic and business rules can be encapsulated so that users can access data and objects only in ways that developers and database administrators intend.</span></span>  
  
- <span data-ttu-id="397f7-110">验证所有用户输入的参数化存储过程可用于阻止 SQL 注入攻击。</span><span class="sxs-lookup"><span data-stu-id="397f7-110">Parameterized stored procedures that validate all user input can be used to thwart SQL injection attacks.</span></span> <span data-ttu-id="397f7-111">如果使用动态 SQL，请确保将命令参数化，并绝对不能将参数值直接包括在查询字符串中。</span><span class="sxs-lookup"><span data-stu-id="397f7-111">If you use dynamic SQL, be sure to parameterize your commands, and never include parameter values directly into a query string.</span></span>  
  
- <span data-ttu-id="397f7-112">可禁止即席查询和数据修改。</span><span class="sxs-lookup"><span data-stu-id="397f7-112">Ad hoc queries and data modifications can be disallowed.</span></span> <span data-ttu-id="397f7-113">这样将阻止用户恶意或无意中损坏数据或执行查询，以避免降低服务器或网络的性能。</span><span class="sxs-lookup"><span data-stu-id="397f7-113">This prevents users from maliciously or inadvertently destroying data or executing queries that impair performance on the server or the network.</span></span>  
  
- <span data-ttu-id="397f7-114">可以在过程代码中处理错误，而无需将错误直接传递给客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="397f7-114">Errors can be handled in procedure code without being passed directly to client applications.</span></span> <span data-ttu-id="397f7-115">这样可防止返回错误消息，以避免其可能有助于探测攻击。</span><span class="sxs-lookup"><span data-stu-id="397f7-115">This prevents error messages from being returned that could aid in a probing attack.</span></span> <span data-ttu-id="397f7-116">在服务器上记录错误并对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="397f7-116">Log errors and handle them on the server.</span></span>  
  
- <span data-ttu-id="397f7-117">存储过程只能编写一次，可由很多应用程序访问。</span><span class="sxs-lookup"><span data-stu-id="397f7-117">Stored procedures can be written once, and accessed by many applications.</span></span>  
  
- <span data-ttu-id="397f7-118">客户端应用程序不需要知道有关基础数据结构的任何信息。</span><span class="sxs-lookup"><span data-stu-id="397f7-118">Client applications do not need to know anything about the underlying data structures.</span></span> <span data-ttu-id="397f7-119">只要更改不影响参数列表或返回的数据类型，就可以更改存储过程代码，而无需在客户端应用程序中进行更改。</span><span class="sxs-lookup"><span data-stu-id="397f7-119">Stored procedure code can be changed without requiring changes in client applications as long as the changes do not affect parameter lists or returned data types.</span></span>  
  
- <span data-ttu-id="397f7-120">存储过程可通过将多个操作组合到一个过程调用中来减少网络通讯。</span><span class="sxs-lookup"><span data-stu-id="397f7-120">Stored procedures can reduce network traffic by combining multiple operations into one procedure call.</span></span>  
  
## <a name="stored-procedure-execution"></a><span data-ttu-id="397f7-121">存储过程的执行</span><span class="sxs-lookup"><span data-stu-id="397f7-121">Stored Procedure Execution</span></span>  

 <span data-ttu-id="397f7-122">存储过程利用所有权链接来提供对数据的访问，这样，用户就不必拥有访问数据库对象的显式权限。</span><span class="sxs-lookup"><span data-stu-id="397f7-122">Stored procedures take advantage of ownership chaining to provide access to data so that users do not need to have explicit permission to access database objects.</span></span> <span data-ttu-id="397f7-123">如果按顺序相互访问的对象由同一个用户所拥有，就会存在所有权链接。</span><span class="sxs-lookup"><span data-stu-id="397f7-123">An ownership chain exists when objects that access each other sequentially are owned by the same user.</span></span> <span data-ttu-id="397f7-124">例如，存储过程可以调用其他存储过程，或者存储过程可访问多个表。</span><span class="sxs-lookup"><span data-stu-id="397f7-124">For example, a stored procedure can call other stored procedures, or a stored procedure can access multiple tables.</span></span> <span data-ttu-id="397f7-125">如果执行链中的所有对象的所有者相同，则 SQL Server 只检查调用方的 EXECUTE 权限，而不检查调用方对其他对象的权限。</span><span class="sxs-lookup"><span data-stu-id="397f7-125">If all objects in the chain of execution have the same owner, then SQL Server only checks the EXECUTE permission for the caller, not the caller's permissions on other objects.</span></span> <span data-ttu-id="397f7-126">因此，只需对存储过程授予 EXECUTE 权限；可以撤消或拒绝对基础表的所有权限。</span><span class="sxs-lookup"><span data-stu-id="397f7-126">Therefore you need to grant only EXECUTE permissions on stored procedures; you can revoke or deny all permissions on the underlying tables.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="397f7-127">最佳实践</span><span class="sxs-lookup"><span data-stu-id="397f7-127">Best Practices</span></span>  

 <span data-ttu-id="397f7-128">仅编写存储过程不足以保证应用程序的安全，</span><span class="sxs-lookup"><span data-stu-id="397f7-128">Simply writing stored procedures isn't enough to adequately secure your application.</span></span> <span data-ttu-id="397f7-129">还应当考虑以下潜在的安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="397f7-129">You should also consider the following potential security holes.</span></span>  
  
- <span data-ttu-id="397f7-130">为您希望其能够访问数据的数据库角色授予对存储过程的 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="397f7-130">Grant EXECUTE permissions on the stored procedures for database roles you want to be able to access the data.</span></span>  
  
- <span data-ttu-id="397f7-131">撤消或拒绝数据库中所有角色和用户（包括 `public` 角色）对基础表的所有权限。</span><span class="sxs-lookup"><span data-stu-id="397f7-131">Revoke or deny all permissions to the underlying tables for all roles and users in the database, including the `public` role.</span></span> <span data-ttu-id="397f7-132">所有用户会从公共角色中继承权限。</span><span class="sxs-lookup"><span data-stu-id="397f7-132">All users inherit permissions from public.</span></span> <span data-ttu-id="397f7-133">因此，拒绝对 `public` 的权限表示只有所有者和 `sysadmin` 成员具有访问权；所有其他用户将无法从其他角色的成员资格继承权限。</span><span class="sxs-lookup"><span data-stu-id="397f7-133">Therefore denying permissions to `public` means that only owners and `sysadmin` members have access; all other users will be unable to inherit permissions from membership in other roles.</span></span>  
  
- <span data-ttu-id="397f7-134">请不要将用户或角色添加到 `sysadmin` 或 `db_owner` 角色。</span><span class="sxs-lookup"><span data-stu-id="397f7-134">Do not add users or roles to the `sysadmin` or `db_owner` roles.</span></span> <span data-ttu-id="397f7-135">系统管理员和数据库所有者可访问所有数据库对象。</span><span class="sxs-lookup"><span data-stu-id="397f7-135">System administrators and database owners can access all database objects.</span></span>  
  
- <span data-ttu-id="397f7-136">禁用 `guest` 帐户。</span><span class="sxs-lookup"><span data-stu-id="397f7-136">Disable the `guest` account.</span></span> <span data-ttu-id="397f7-137">这样将阻止匿名用户连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="397f7-137">This will prevent anonymous users from connecting to the database.</span></span> <span data-ttu-id="397f7-138">默认情况下，会在新数据库中禁用来宾帐户。</span><span class="sxs-lookup"><span data-stu-id="397f7-138">The guest account is disabled by default in new databases.</span></span>  
  
- <span data-ttu-id="397f7-139">实现错误处理和记录错误。</span><span class="sxs-lookup"><span data-stu-id="397f7-139">Implement error handling and log errors.</span></span>  
  
- <span data-ttu-id="397f7-140">创建用于验证所有用户输入的参数化存储过程。</span><span class="sxs-lookup"><span data-stu-id="397f7-140">Create parameterized stored procedures that validate all user input.</span></span> <span data-ttu-id="397f7-141">将所有用户输入视为不受信任。</span><span class="sxs-lookup"><span data-stu-id="397f7-141">Treat all user input as untrusted.</span></span>  
  
- <span data-ttu-id="397f7-142">除非绝对必要，否则应避免使用动态 SQL。</span><span class="sxs-lookup"><span data-stu-id="397f7-142">Avoid dynamic SQL unless absolutely necessary.</span></span> <span data-ttu-id="397f7-143">使用 Transact-SQL QUOTENAME() 函数可分隔字符串值，并对输入字符串中的任何分隔符进行转义。</span><span class="sxs-lookup"><span data-stu-id="397f7-143">Use the Transact-SQL QUOTENAME() function to delimit a string value and escape any occurrence of the delimiter in the input string.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="397f7-144">外部资源</span><span class="sxs-lookup"><span data-stu-id="397f7-144">External Resources</span></span>  

 <span data-ttu-id="397f7-145">有关详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="397f7-145">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="397f7-146">资源</span><span class="sxs-lookup"><span data-stu-id="397f7-146">Resource</span></span>|<span data-ttu-id="397f7-147">说明</span><span class="sxs-lookup"><span data-stu-id="397f7-147">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="397f7-148">[存储过程](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) 和 [SQL 注入](/sql/relational-databases/security/sql-injection)</span><span class="sxs-lookup"><span data-stu-id="397f7-148">[Stored Procedures](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) and [SQL Injection](/sql/relational-databases/security/sql-injection)</span></span>|<span data-ttu-id="397f7-149">本文介绍如何创建存储过程和 SQL 注入的工作方式。</span><span class="sxs-lookup"><span data-stu-id="397f7-149">Articles describe how to create stored procedures and how SQL Injection works.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="397f7-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="397f7-150">See also</span></span>

- [<span data-ttu-id="397f7-151">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="397f7-151">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="397f7-152">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="397f7-152">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="397f7-153">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="397f7-153">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="397f7-154">在 SQL Server 中编写安全动态 SQL</span><span class="sxs-lookup"><span data-stu-id="397f7-154">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="397f7-155">SQL Server 中的签名存储过程</span><span class="sxs-lookup"><span data-stu-id="397f7-155">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="397f7-156">在 SQL Server 中使用模拟自定义权限</span><span class="sxs-lookup"><span data-stu-id="397f7-156">Customizing Permissions with Impersonation in SQL Server</span></span>](customizing-permissions-with-impersonation-in-sql-server.md)
- [<span data-ttu-id="397f7-157">使用存储过程修改数据</span><span class="sxs-lookup"><span data-stu-id="397f7-157">Modifying Data with Stored Procedures</span></span>](../modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="397f7-158">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="397f7-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
