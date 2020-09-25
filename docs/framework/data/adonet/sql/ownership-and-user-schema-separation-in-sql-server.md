---
title: SQL Server 中的所有权和用户架构分离
description: 了解用户架构分离如何允许灵活管理 SQL Server 数据库对象权限。 将对象分组到不同的命名空间中。
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: e92799237a90c502aa4000d8d4027df522aa0d87
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183138"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="28f6b-104">SQL Server 中的所有权和用户架构分离</span><span class="sxs-lookup"><span data-stu-id="28f6b-104">Ownership and User-Schema Separation in SQL Server</span></span>

<span data-ttu-id="28f6b-105">SQL Server 安全性的核心概念是对象的所有者具有管理这些对象的不可撤消的权限。</span><span class="sxs-lookup"><span data-stu-id="28f6b-105">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="28f6b-106">您不能取消对象所有者的特权，并且如果用户在数据库中拥有对象，您也不能将用户从数据库中删除。</span><span class="sxs-lookup"><span data-stu-id="28f6b-106">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="28f6b-107">用户架构分离</span><span class="sxs-lookup"><span data-stu-id="28f6b-107">User-Schema Separation</span></span>  

 <span data-ttu-id="28f6b-108">通过用户架构分离，可实现管理数据库对象权限的更大灵活性。</span><span class="sxs-lookup"><span data-stu-id="28f6b-108">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="28f6b-109">*架构*是数据库对象的命名容器，使你能够将对象分组到不同的命名空间中。</span><span class="sxs-lookup"><span data-stu-id="28f6b-109">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="28f6b-110">例如，AdventureWorks 示例数据库包含 Production、Sales 和 HumanResources 的架构。</span><span class="sxs-lookup"><span data-stu-id="28f6b-110">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="28f6b-111">用于引用对象的由四部分组成的命名语法指定架构名称。</span><span class="sxs-lookup"><span data-stu-id="28f6b-111">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```text
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="28f6b-112">架构所有者和权限</span><span class="sxs-lookup"><span data-stu-id="28f6b-112">Schema Owners and Permissions</span></span>  

 <span data-ttu-id="28f6b-113">任何数据库主体都可以拥有架构，并且一个主体可拥有多个架构。</span><span class="sxs-lookup"><span data-stu-id="28f6b-113">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="28f6b-114">您可以对架构应用安全规则，安全规则将由架构中的所有对象继承。</span><span class="sxs-lookup"><span data-stu-id="28f6b-114">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="28f6b-115">如果设置了对架构的访问权限，则当新对象添加到架构时，新对象会自动应用这些权限。</span><span class="sxs-lookup"><span data-stu-id="28f6b-115">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="28f6b-116">可以为用户分配一个默认的架构，且多个数据库用户可以共享同一架构。</span><span class="sxs-lookup"><span data-stu-id="28f6b-116">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="28f6b-117">默认情况下，当开发人员在架构中创建对象时，该对象由拥有架构的安全主体而不是开发人员拥有。</span><span class="sxs-lookup"><span data-stu-id="28f6b-117">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="28f6b-118">可以使用 ALTER AUTHORIZATION Transact-SQL 语句转移对象所有权。</span><span class="sxs-lookup"><span data-stu-id="28f6b-118">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="28f6b-119">虽因架构会增大管理权限的复杂度而不建议使用，但架构仍然可以包含由不同用户拥有的对象并可具有比分配给架构的权限更加细化的权限。</span><span class="sxs-lookup"><span data-stu-id="28f6b-119">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="28f6b-120">对象可以在架构之间移动，架构所有权也可以在主体之间转移。</span><span class="sxs-lookup"><span data-stu-id="28f6b-120">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="28f6b-121">可以在不影响架构的情况下删除数据库用户。</span><span class="sxs-lookup"><span data-stu-id="28f6b-121">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="28f6b-122">内置架构</span><span class="sxs-lookup"><span data-stu-id="28f6b-122">Built-In Schemas</span></span>  

 <span data-ttu-id="28f6b-123">SQL Server 随附了十个预定义的架构，它们与内置数据库用户和角色具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="28f6b-123">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="28f6b-124">这些架构主要用于向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="28f6b-124">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="28f6b-125">如果您不需要与固定数据库角色具有相同名称的架构，则可以删除它们。</span><span class="sxs-lookup"><span data-stu-id="28f6b-125">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="28f6b-126">您不能删除下列架构：</span><span class="sxs-lookup"><span data-stu-id="28f6b-126">You cannot drop the following schemas:</span></span>  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="28f6b-127">如果从模型数据库中删除这些架构，它们将不会显示在新数据库中。</span><span class="sxs-lookup"><span data-stu-id="28f6b-127">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28f6b-128">`sys` 和 `INFORMATION_SCHEMA` 架构是为系统对象而保留的。</span><span class="sxs-lookup"><span data-stu-id="28f6b-128">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="28f6b-129">您不能在这些架构中创建对象，而且不能删除它们。</span><span class="sxs-lookup"><span data-stu-id="28f6b-129">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="28f6b-130">dbo 架构</span><span class="sxs-lookup"><span data-stu-id="28f6b-130">The dbo Schema</span></span>  

 <span data-ttu-id="28f6b-131">`dbo` 是新创建的数据库的默认架构。</span><span class="sxs-lookup"><span data-stu-id="28f6b-131">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="28f6b-132">`dbo` 架构由 `dbo` 用户帐户拥有。</span><span class="sxs-lookup"><span data-stu-id="28f6b-132">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="28f6b-133">默认情况下，使用 CREATE USER Transact-SQL 命令创建的用户的默认架构为 `dbo`。</span><span class="sxs-lookup"><span data-stu-id="28f6b-133">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="28f6b-134">分配了 `dbo` 架构的用户不继承 `dbo` 用户帐户的权限。</span><span class="sxs-lookup"><span data-stu-id="28f6b-134">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="28f6b-135">用户不从架构继承权限；架构权限由架构中包含的数据库对象继承。</span><span class="sxs-lookup"><span data-stu-id="28f6b-135">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28f6b-136">当使用部分名称来引用数据库对象时，SQL Server 首先在用户的默认架构中查找。</span><span class="sxs-lookup"><span data-stu-id="28f6b-136">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="28f6b-137">如果在此处未找到该对象，则 SQL Server 其次将在 `dbo` 架构中查找。</span><span class="sxs-lookup"><span data-stu-id="28f6b-137">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="28f6b-138">如果对象不在 `dbo` 架构中，则会返回一个错误。</span><span class="sxs-lookup"><span data-stu-id="28f6b-138">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="28f6b-139">外部资源</span><span class="sxs-lookup"><span data-stu-id="28f6b-139">External Resources</span></span>  

 <span data-ttu-id="28f6b-140">有关对象所有权和架构的更多信息，请参见下列资源。</span><span class="sxs-lookup"><span data-stu-id="28f6b-140">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="28f6b-141">资源</span><span class="sxs-lookup"><span data-stu-id="28f6b-141">Resource</span></span>|<span data-ttu-id="28f6b-142">说明</span><span class="sxs-lookup"><span data-stu-id="28f6b-142">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="28f6b-143">[用户架构分离](/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="28f6b-143">[User-Schema Separation](/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span></span>|<span data-ttu-id="28f6b-144">描述用户架构分离引发的变化，</span><span class="sxs-lookup"><span data-stu-id="28f6b-144">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="28f6b-145">包括新行为及其对所有权、目录视图和权限的影响。</span><span class="sxs-lookup"><span data-stu-id="28f6b-145">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28f6b-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="28f6b-146">See also</span></span>

- [<span data-ttu-id="28f6b-147">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="28f6b-147">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="28f6b-148">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="28f6b-148">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="28f6b-149">SQL Server 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="28f6b-149">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)
- [<span data-ttu-id="28f6b-150">SQL Server 中的服务器和数据库角色</span><span class="sxs-lookup"><span data-stu-id="28f6b-150">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)
- [<span data-ttu-id="28f6b-151">SQL Server 中的授权和权限</span><span class="sxs-lookup"><span data-stu-id="28f6b-151">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)
- [<span data-ttu-id="28f6b-152">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="28f6b-152">ADO.NET Overview</span></span>](../ado-net-overview.md)
