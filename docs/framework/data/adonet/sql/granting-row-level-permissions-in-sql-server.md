---
title: 在 SQL Server 中授予行级权限
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 0b34eaee4b66a2be82049816f0a98b9f53012303
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554848"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="d7046-102">在 SQL Server 中授予行级权限</span><span class="sxs-lookup"><span data-stu-id="d7046-102">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="d7046-103">在某些情况下，会要求更为细致地控制数据访问，而不仅仅是授予、撤消或拒绝提供的权限。</span><span class="sxs-lookup"><span data-stu-id="d7046-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="d7046-104">例如，医院数据库应用程序可能需要限制各个医生只访问与自己的患者相关的信息。</span><span class="sxs-lookup"><span data-stu-id="d7046-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="d7046-105">在很多环境（包括财务、法律、政府和军事应用程序）中都存在类似的要求。</span><span class="sxs-lookup"><span data-stu-id="d7046-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="d7046-106">为了满足这些情况，SQL Server 2016 提供了 [行级安全](/sql/relational-databases/security/row-level-security) 功能，可以用于简化并集中化安全策略中的行级访问逻辑。</span><span class="sxs-lookup"><span data-stu-id="d7046-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="d7046-107">对于 SQL Server 的早期版本，可以通过使用视图制定行级筛选来实现类似功能。</span><span class="sxs-lookup"><span data-stu-id="d7046-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="d7046-108">实现行级筛选</span><span class="sxs-lookup"><span data-stu-id="d7046-108">Implementing Row-level Filtering</span></span>

<span data-ttu-id="d7046-109">行级筛选适用于在类似以上医院示例中的单个表格中存储信息的应用程序。</span><span class="sxs-lookup"><span data-stu-id="d7046-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="d7046-110">若要实现行级筛选，每行都有一个定义区别性参数（如用户名、标签或其他标识符）的列。</span><span class="sxs-lookup"><span data-stu-id="d7046-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="d7046-111">在表格上创建安全策略或视图，利用该表格可以筛选用户可以访问的行。</span><span class="sxs-lookup"><span data-stu-id="d7046-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="d7046-112">然后创建参数化存储的过程，利用该过程可以控制用户可以执行的查询的类型。</span><span class="sxs-lookup"><span data-stu-id="d7046-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="d7046-113">以下示例介绍了基于用户名或登录名如何配置行级筛选：</span><span class="sxs-lookup"><span data-stu-id="d7046-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="d7046-114">创建表格，同时添加要存储名称的列。</span><span class="sxs-lookup"><span data-stu-id="d7046-114">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="d7046-115">启用行级筛选：</span><span class="sxs-lookup"><span data-stu-id="d7046-115">Enable row-level filtering:</span></span>

  - <span data-ttu-id="d7046-116">如果你使用的是 SQL Server 2016 或更高版本，或使用的是 [Azure SQL 数据库](/azure/sql-database/)，则创建在表格中添加谓词的安全策略，该表格将返回的行限制为符合当前数据库用户（使用 CURRENT_USER() 内置函数）或当前登录名（使用 SUSER_SNAME() 内置函数）的行：</span><span class="sxs-lookup"><span data-stu-id="d7046-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

      ```sql
      CREATE SCHEMA Security
      GO

      CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)
          RETURNS TABLE
          WITH SCHEMABINDING
      AS
          RETURN SELECT 1 AS accessResult
          WHERE @UserName = SUSER_SNAME()
      GO

      CREATE SECURITY POLICY Security.userAccessPolicy
          ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,
          ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable
      GO
      ```

  - <span data-ttu-id="d7046-117">如果你使用的是 2016 之前的 SQL Server 版本，则可以使用视图实现类似功能：</span><span class="sxs-lookup"><span data-stu-id="d7046-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="d7046-118">创建用于选择、插入、更新和删除数据的存储过程。</span><span class="sxs-lookup"><span data-stu-id="d7046-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="d7046-119">如果由安全策略实施筛选，存储过程则应直接在基表上执行这些操作；否则，如果由视图实施筛选，存储过程则应将执行操作改为运行视图。</span><span class="sxs-lookup"><span data-stu-id="d7046-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="d7046-120">安全策略或视图会自动筛选由用户查询返回或修改的行，存储过程会提供更坚固的安全边界，以防止具有直接查询访问的用户成功运行可以推断是否存在筛选的数据的查询。</span><span class="sxs-lookup"><span data-stu-id="d7046-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="d7046-121">对于插入数据的存储过程，使用安全策略或视图中指定的相同函数捕获用户名称，并将该值插入 UserName 列。</span><span class="sxs-lookup"><span data-stu-id="d7046-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="d7046-122">拒绝 `public` 角色在表格（和视图，如果适用）上的所有权限。</span><span class="sxs-lookup"><span data-stu-id="d7046-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="d7046-123">用户将不能从其他数据库角色继承权限，因为筛选器谓词基于用户或登录名，而不基于角色。</span><span class="sxs-lookup"><span data-stu-id="d7046-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="d7046-124">为数据库角色授予对存储过程的 EXECUTE 权限。</span><span class="sxs-lookup"><span data-stu-id="d7046-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="d7046-125">用户只能通过提供的存储过程访问数据。</span><span class="sxs-lookup"><span data-stu-id="d7046-125">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7046-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="d7046-126">See also</span></span>

- [<span data-ttu-id="d7046-127">行级安全性</span><span class="sxs-lookup"><span data-stu-id="d7046-127">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="d7046-128">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="d7046-128">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="d7046-129">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="d7046-129">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="d7046-130">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="d7046-130">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="d7046-131">在 SQL Server 中使用存储过程管理权限</span><span class="sxs-lookup"><span data-stu-id="d7046-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="d7046-132">在 SQL Server 中编写安全动态 SQL</span><span class="sxs-lookup"><span data-stu-id="d7046-132">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="d7046-133">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="d7046-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
