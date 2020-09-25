---
title: SQL Server 中的服务器和数据库角色
description: 了解固定服务器和固定数据库角色，这些角色具有分配给它们的固定权限集。 SQL Server 使用基于角色的安全性。
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: 3babf6b249da6e67a6a48bcad647e4674650c348
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177327"
---
# <a name="server-and-database-roles-in-sql-server"></a><span data-ttu-id="9d718-104">SQL Server 中的服务器和数据库角色</span><span class="sxs-lookup"><span data-stu-id="9d718-104">Server and Database Roles in SQL Server</span></span>

<span data-ttu-id="9d718-105">所有版本的 SQL Server 均使用基于角色的安全，它允许您为角色、用户组而不是各个用户分配权限。</span><span class="sxs-lookup"><span data-stu-id="9d718-105">All versions of SQL Server use role-based security, which allows you to assign permissions to a role, or group of users, instead of to individual users.</span></span> <span data-ttu-id="9d718-106">固定服务器和固定数据库角色具有分配给它们的一组固定的权限。</span><span class="sxs-lookup"><span data-stu-id="9d718-106">Fixed server and fixed database roles have a fixed set of permissions assigned to them.</span></span>  
  
## <a name="fixed-server-roles"></a><span data-ttu-id="9d718-107">固定服务器角色</span><span class="sxs-lookup"><span data-stu-id="9d718-107">Fixed Server Roles</span></span>  

 <span data-ttu-id="9d718-108">固定服务器角色具有一组固定的权限，并且适用于整个服务器范围。</span><span class="sxs-lookup"><span data-stu-id="9d718-108">Fixed server roles have a fixed set of permissions and server-wide scope.</span></span> <span data-ttu-id="9d718-109">它们专门用于管理 SQL Server，且不能更改分配给它们的权限。</span><span class="sxs-lookup"><span data-stu-id="9d718-109">They are intended for use in administering SQL Server and the permissions assigned to them cannot be changed.</span></span> <span data-ttu-id="9d718-110">可以在数据库中不存在用户帐户的情况下向固定服务器角色分配登录。</span><span class="sxs-lookup"><span data-stu-id="9d718-110">Logins can be assigned to fixed server roles without having a user account in a database.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9d718-111">`sysadmin` 固定服务器角色包含所有其他角色并且具有无限范围。</span><span class="sxs-lookup"><span data-stu-id="9d718-111">The `sysadmin` fixed server role encompasses all other roles and has unlimited scope.</span></span> <span data-ttu-id="9d718-112">请不要将这些主体添加到此角色，除非它们是高度信任的。</span><span class="sxs-lookup"><span data-stu-id="9d718-112">Do not add principals to this role unless they are highly trusted.</span></span> <span data-ttu-id="9d718-113">`sysadmin` 角色成员对所有服务器数据库和资源有不可撤消的管理特权。</span><span class="sxs-lookup"><span data-stu-id="9d718-113">`sysadmin` role members have irrevocable administrative privileges on all server databases and resources.</span></span>  
  
 <span data-ttu-id="9d718-114">将用户添加到固定服务器角色时，请仔细选择。</span><span class="sxs-lookup"><span data-stu-id="9d718-114">Be selective when you add users to fixed server roles.</span></span> <span data-ttu-id="9d718-115">例如，`bulkadmin` 角色允许用户将任意本地文件的内容插入表中，这样可能会损坏数据的完整性。</span><span class="sxs-lookup"><span data-stu-id="9d718-115">For example, the `bulkadmin` role allows users to insert the contents of any local file into a table, which could jeopardize data integrity.</span></span> <span data-ttu-id="9d718-116">有关固定服务器角色和权限的完整列表，请参阅 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="9d718-116">See SQL Server Books Online for the complete list of fixed server roles and permissions.</span></span>  
  
## <a name="fixed-database-roles"></a><span data-ttu-id="9d718-117">固定数据库角色</span><span class="sxs-lookup"><span data-stu-id="9d718-117">Fixed Database Roles</span></span>  

 <span data-ttu-id="9d718-118">固定数据库角色具有一组预定义的权限，这些权限旨在允许您轻松管理权限组。</span><span class="sxs-lookup"><span data-stu-id="9d718-118">Fixed database roles have a pre-defined set of permissions that are designed to allow you to easily manage groups of permissions.</span></span> <span data-ttu-id="9d718-119">`db_owner` 角色的成员可对数据库执行所有配置和维护活动。</span><span class="sxs-lookup"><span data-stu-id="9d718-119">Members of the `db_owner` role can perform all configuration and maintenance activities on the database.</span></span>  
  
 <span data-ttu-id="9d718-120">有关 SQL Server 预定义角色的更多信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="9d718-120">For more information about SQL Server predefined roles, see the following resources.</span></span>  
  
|<span data-ttu-id="9d718-121">资源</span><span class="sxs-lookup"><span data-stu-id="9d718-121">Resource</span></span>|<span data-ttu-id="9d718-122">说明</span><span class="sxs-lookup"><span data-stu-id="9d718-122">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="9d718-123">服务器级角色</span><span class="sxs-lookup"><span data-stu-id="9d718-123">Server-Level Roles</span></span>](/sql/relational-databases/security/authentication-access/server-level-roles)|<span data-ttu-id="9d718-124">描述固定服务器角色以及与 SQL Server 相关联的权限。</span><span class="sxs-lookup"><span data-stu-id="9d718-124">Describes fixed server roles and the permissions associated with them in SQL Server.</span></span>|  
|[<span data-ttu-id="9d718-125">数据库级别的角色</span><span class="sxs-lookup"><span data-stu-id="9d718-125">Database-Level Roles</span></span>](/sql/relational-databases/security/authentication-access/database-level-roles)|<span data-ttu-id="9d718-126">描述固定数据库角色及与其关联的权限</span><span class="sxs-lookup"><span data-stu-id="9d718-126">Describes fixed database roles and the permissions associated with them</span></span>|  
  
## <a name="database-roles-and-users"></a><span data-ttu-id="9d718-127">数据库角色和用户</span><span class="sxs-lookup"><span data-stu-id="9d718-127">Database Roles and Users</span></span>  

 <span data-ttu-id="9d718-128">要使用数据库对象，必须将登录映射到数据库用户帐户。</span><span class="sxs-lookup"><span data-stu-id="9d718-128">Logins must be mapped to database user accounts in order to work with database objects.</span></span> <span data-ttu-id="9d718-129">这样就可以将数据库用户添加到数据库角色，从而继承与这些角色关联的任何权限集。</span><span class="sxs-lookup"><span data-stu-id="9d718-129">Database users can then be added to database roles, inheriting any permission sets associated with those roles.</span></span> <span data-ttu-id="9d718-130">可以授予所有权限。</span><span class="sxs-lookup"><span data-stu-id="9d718-130">All permissions can be granted.</span></span>  
  
 <span data-ttu-id="9d718-131">当为应用程序设计安全性时，还必须考虑 `public` 角色、`dbo` 用户帐户和 `guest` 帐户。</span><span class="sxs-lookup"><span data-stu-id="9d718-131">You must also consider the `public` role, the `dbo` user account, and the `guest` account when you design security for your application.</span></span>  
  
### <a name="the-public-role"></a><span data-ttu-id="9d718-132">公共角色</span><span class="sxs-lookup"><span data-stu-id="9d718-132">The public Role</span></span>  

 <span data-ttu-id="9d718-133">`public` 角色包含在每个数据库中，包括系统数据库。</span><span class="sxs-lookup"><span data-stu-id="9d718-133">The `public` role is contained in every database, which includes system databases.</span></span> <span data-ttu-id="9d718-134">无法删除该角色，也无法向其中添加用户或从中删除用户。</span><span class="sxs-lookup"><span data-stu-id="9d718-134">It cannot be dropped and you cannot add or remove users from it.</span></span> <span data-ttu-id="9d718-135">授予 `public` 角色的权限由所有其他用户和角色继承，因为默认情况下，它们属于 `public` 角色。</span><span class="sxs-lookup"><span data-stu-id="9d718-135">Permissions granted to the `public` role are inherited by all other users and roles because they belong to the `public` role by default.</span></span> <span data-ttu-id="9d718-136">仅为 `public` 角色授予您希望所有用户都具有的权限。</span><span class="sxs-lookup"><span data-stu-id="9d718-136">Grant `public` only the permissions you want all users to have.</span></span>  
  
### <a name="the-dbo-user-account"></a><span data-ttu-id="9d718-137">dbo 用户帐户</span><span class="sxs-lookup"><span data-stu-id="9d718-137">The dbo User Account</span></span>  

 <span data-ttu-id="9d718-138">`dbo` 或数据库所有者是具有在数据库中执行所有活动的默示权限的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="9d718-138">The `dbo`, or database owner, is a user account that has implied permissions to perform all activities in the database.</span></span> <span data-ttu-id="9d718-139">`sysadmin` 固定服务器角色的成员会自动映射到 `dbo`。</span><span class="sxs-lookup"><span data-stu-id="9d718-139">Members of the `sysadmin` fixed server role are automatically mapped to `dbo`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9d718-140">`dbo` 也是架构的名称，如 [SQL Server 中的所有权和用户架构分离](ownership-and-user-schema-separation-in-sql-server.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="9d718-140">`dbo` is also the name of a schema, as discussed in [Ownership and User-Schema Separation in SQL Server](ownership-and-user-schema-separation-in-sql-server.md).</span></span>  
  
 <span data-ttu-id="9d718-141">`dbo` 用户帐户经常与 `db_owner` 固定数据库角色相混淆。</span><span class="sxs-lookup"><span data-stu-id="9d718-141">The `dbo` user account is frequently confused with the `db_owner` fixed database role.</span></span> <span data-ttu-id="9d718-142">`db_owner` 的作用域是一个数据库；`sysadmin` 的作用域是整个服务器。</span><span class="sxs-lookup"><span data-stu-id="9d718-142">The scope of `db_owner` is a database; the scope of `sysadmin` is the whole server.</span></span> <span data-ttu-id="9d718-143">`db_owner` 角色中的成员无法授予 `dbo` 用户特权。</span><span class="sxs-lookup"><span data-stu-id="9d718-143">Membership in the `db_owner` role does not confer `dbo` user privileges.</span></span>  
  
### <a name="the-guest-user-account"></a><span data-ttu-id="9d718-144">guest 用户帐户</span><span class="sxs-lookup"><span data-stu-id="9d718-144">The guest User Account</span></span>  

 <span data-ttu-id="9d718-145">用户经过身份验证并允许登录 SQL Server 的实例后，用户需要访问的每个数据库中必须存在一个单独的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="9d718-145">After a user has been authenticated and allowed to log in to an instance of SQL Server, a separate user account must exist in each database the user has to access.</span></span> <span data-ttu-id="9d718-146">要求每个数据库中具有用户帐户会阻止用户连接到 SQL Server 的实例，并且会阻止用户访问服务器上的所有数据库。</span><span class="sxs-lookup"><span data-stu-id="9d718-146">Requiring a user account in each database prevents users from connecting to an instance of SQL Server and accessing all the databases on a server.</span></span> <span data-ttu-id="9d718-147">通过允许没有数据库用户帐户的登录访问数据库，可在数据库中包含 `guest` 用户帐户时避开此需求。</span><span class="sxs-lookup"><span data-stu-id="9d718-147">The existence of a `guest` user account in the database circumvents this requirement by allowing a login without a database user account to access a database.</span></span>  
  
 <span data-ttu-id="9d718-148">在所有版本的 SQL Server 中，`guest` 帐户均为内置帐户。</span><span class="sxs-lookup"><span data-stu-id="9d718-148">The `guest` account is a built-in account in all versions of SQL Server.</span></span> <span data-ttu-id="9d718-149">默认情况下，它在新的数据库中是禁用的。</span><span class="sxs-lookup"><span data-stu-id="9d718-149">By default, it is disabled in new databases.</span></span> <span data-ttu-id="9d718-150">如果启用此帐户，则可以通过撤消其 CONNECT 权限（方法是执行 Transact-SQL REVOKE CONNECT FROM GUEST 语句）来禁用此帐户。</span><span class="sxs-lookup"><span data-stu-id="9d718-150">If it is enabled, you can disable it by revoking its CONNECT permission by executing the Transact-SQL REVOKE CONNECT FROM GUEST statement.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9d718-151">避免使用 `guest` 帐户；没有其自己的数据库权限的所有登录都会获取授予此帐户的数据库权限。</span><span class="sxs-lookup"><span data-stu-id="9d718-151">Avoid using the `guest` account; all logins without their own database permissions obtain the database permissions granted to this account.</span></span> <span data-ttu-id="9d718-152">如果必须使用 `guest` 帐户，请为其授予最小权限。</span><span class="sxs-lookup"><span data-stu-id="9d718-152">If you must use the `guest` account, grant it minimum permissions.</span></span>  
  
 <span data-ttu-id="9d718-153">有关 SQL Server 登录名、用户和角色的更多信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="9d718-153">For more information about SQL Server logins, users and roles, see the following resources.</span></span>  
  
|<span data-ttu-id="9d718-154">资源</span><span class="sxs-lookup"><span data-stu-id="9d718-154">Resource</span></span>|<span data-ttu-id="9d718-155">说明</span><span class="sxs-lookup"><span data-stu-id="9d718-155">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="9d718-156">数据库引擎权限入门</span><span class="sxs-lookup"><span data-stu-id="9d718-156">Getting Started with Database Engine Permissions</span></span>](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|<span data-ttu-id="9d718-157">包含指向描述主体、角色、凭据、安全对象和权限的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="9d718-157">Contains links to topics that describe principals, roles, credentials, securables and permissions.</span></span>|  
|[<span data-ttu-id="9d718-158">主体</span><span class="sxs-lookup"><span data-stu-id="9d718-158">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="9d718-159">描述主体并包含指向描述服务器和数据库角色的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="9d718-159">Describes principals and contains links to topics that describe server and database roles.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d718-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="9d718-160">See also</span></span>

- [<span data-ttu-id="9d718-161">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="9d718-161">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="9d718-162">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="9d718-162">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="9d718-163">SQL Server 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="9d718-163">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)
- [<span data-ttu-id="9d718-164">SQL Server 中的所有权和用户架构分离</span><span class="sxs-lookup"><span data-stu-id="9d718-164">Ownership and User-Schema Separation in SQL Server</span></span>](ownership-and-user-schema-separation-in-sql-server.md)
- [<span data-ttu-id="9d718-165">SQL Server 中的授权和权限</span><span class="sxs-lookup"><span data-stu-id="9d718-165">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)
- [<span data-ttu-id="9d718-166">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="9d718-166">ADO.NET Overview</span></span>](../ado-net-overview.md)
