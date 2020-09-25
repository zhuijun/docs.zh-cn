---
title: SQL Server 中的应用程序安全性方案
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 2d0e65f61939312bf29111e87c49366cd9e389be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197646"
---
# <a name="application-security-scenarios-in-sql-server"></a><span data-ttu-id="ff100-102">SQL Server 中的应用程序安全性方案</span><span class="sxs-lookup"><span data-stu-id="ff100-102">Application Security Scenarios in SQL Server</span></span>

<span data-ttu-id="ff100-103">创建安全的 SQL Server 客户端应用程序没有唯一正确的方法。</span><span class="sxs-lookup"><span data-stu-id="ff100-103">There is no single correct way to create a secure SQL Server client application.</span></span> <span data-ttu-id="ff100-104">每个应用程序都具有独特的要求、部署环境和用户群体。</span><span class="sxs-lookup"><span data-stu-id="ff100-104">Every application is unique in its requirements, deployment environment, and user population.</span></span> <span data-ttu-id="ff100-105">即便应用程序的最初部署具有合理的安全性，但在一段时间后，安全性可能会降低。</span><span class="sxs-lookup"><span data-stu-id="ff100-105">An application that is reasonably secure when it is initially deployed can become less secure over time.</span></span> <span data-ttu-id="ff100-106">没有办法准确地预测未来可能出现的威胁。</span><span class="sxs-lookup"><span data-stu-id="ff100-106">It is impossible to predict with any accuracy what threats may emerge in the future.</span></span>  
  
 <span data-ttu-id="ff100-107">作为一种产品，SQL Server 已在许多版本的基础上进行了改进，以合并最新的安全功能，使开发人员能够创建安全的数据库应用程序。</span><span class="sxs-lookup"><span data-stu-id="ff100-107">SQL Server, as a product, has evolved over many versions to incorporate the latest security features that enable developers to create secure database applications.</span></span> <span data-ttu-id="ff100-108">但是，安全性并不是与生俱来的，需要不断进行监视和更新。</span><span class="sxs-lookup"><span data-stu-id="ff100-108">However, security doesn't come in the box; it requires continual monitoring and updating.</span></span>  
  
## <a name="common-threats"></a><span data-ttu-id="ff100-109">常见威胁</span><span class="sxs-lookup"><span data-stu-id="ff100-109">Common Threats</span></span>  

 <span data-ttu-id="ff100-110">开发人员需要了解安全威胁、为应对这些威胁而提供的工具以及如何避免自身造成的安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="ff100-110">Developers need to understand security threats, the tools provided to counter them, and how to avoid self-inflicted security holes.</span></span> <span data-ttu-id="ff100-111">最好将安全性视为一条链，其中任何一个链接的中断都会削弱整体实力。</span><span class="sxs-lookup"><span data-stu-id="ff100-111">Security can best be thought of as a chain, where a break in any one link compromises the strength of the whole.</span></span> <span data-ttu-id="ff100-112">下面列出了一些常见的安全威胁，本节中的主题将对此进行详细讨论。</span><span class="sxs-lookup"><span data-stu-id="ff100-112">The following list includes some common security threats that are discussed in more detail in the topics in this section.</span></span>  
  
### <a name="sql-injection"></a><span data-ttu-id="ff100-113">SQL 注入</span><span class="sxs-lookup"><span data-stu-id="ff100-113">SQL Injection</span></span>  

 <span data-ttu-id="ff100-114">SQL 注入是恶意用户输入 Transact-SQL 语句而不是有效输入的过程。</span><span class="sxs-lookup"><span data-stu-id="ff100-114">SQL Injection is the process by which a malicious user enters Transact-SQL statements instead of valid input.</span></span> <span data-ttu-id="ff100-115">如果输入未经验证直接传递到服务器，并且应用程序无意中执行了注入的代码，攻击可能会损坏或破坏数据。</span><span class="sxs-lookup"><span data-stu-id="ff100-115">If the input is passed directly to the server without being validated and if the application inadvertently executes the injected code, then the attack has the potential to damage or destroy data.</span></span> <span data-ttu-id="ff100-116">使用存储过程和参数化命令，避免使用动态 SQL，并限制所有用户的权限，可以防止受到 SQL Server 注入攻击。</span><span class="sxs-lookup"><span data-stu-id="ff100-116">You can thwart SQL Server injection attacks by using stored procedures and parameterized commands, avoiding dynamic SQL, and restricting permissions on all users.</span></span>  
  
### <a name="elevation-of-privilege"></a><span data-ttu-id="ff100-117">权限提升</span><span class="sxs-lookup"><span data-stu-id="ff100-117">Elevation of Privilege</span></span>  

 <span data-ttu-id="ff100-118">当用户能够获得可信帐户（所有者或管理员）的特权时，就会发生特权提升攻击。</span><span class="sxs-lookup"><span data-stu-id="ff100-118">Elevation of privilege attacks occur when a user is able to assume the privileges of a trusted account, such as an owner or administrator.</span></span> <span data-ttu-id="ff100-119">始终在最低特权的用户帐户下运行，并仅分配所需的权限。</span><span class="sxs-lookup"><span data-stu-id="ff100-119">Always run under least-privileged user accounts and assign only needed permissions.</span></span> <span data-ttu-id="ff100-120">避免使用管理帐户或所有者帐户来执行代码。</span><span class="sxs-lookup"><span data-stu-id="ff100-120">Avoid using administrative or owner accounts for executing code.</span></span> <span data-ttu-id="ff100-121">这可以限制攻击成功后可能发生的破坏程度。</span><span class="sxs-lookup"><span data-stu-id="ff100-121">This limits the amount of damage that can occur if an attack succeeds.</span></span> <span data-ttu-id="ff100-122">执行需要附加权限的任务时，请仅在任务期间使用过程签名或模拟。</span><span class="sxs-lookup"><span data-stu-id="ff100-122">When performing tasks that require additional permissions, use procedure signing or impersonation only for the duration of the task.</span></span> <span data-ttu-id="ff100-123">你可以使用证书为存储过程签名，或使用模拟来临时分配权限。</span><span class="sxs-lookup"><span data-stu-id="ff100-123">You can sign stored procedures with certificates or use impersonation to temporarily assign permissions.</span></span>  
  
### <a name="probing-and-intelligent-observation"></a><span data-ttu-id="ff100-124">探测和智能观测</span><span class="sxs-lookup"><span data-stu-id="ff100-124">Probing and Intelligent Observation</span></span>  

 <span data-ttu-id="ff100-125">探测攻击可以使用应用程序生成的错误消息来搜索安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="ff100-125">A probing attack can use error messages generated by an application to search for security vulnerabilities.</span></span> <span data-ttu-id="ff100-126">在所有过程代码中实现错误处理，以防止向最终用户返回 SQL Server 错误信息。</span><span class="sxs-lookup"><span data-stu-id="ff100-126">Implement error handling in all procedural code to prevent SQL Server error information from being returned to the end user.</span></span>  
  
### <a name="authentication"></a><span data-ttu-id="ff100-127">身份验证</span><span class="sxs-lookup"><span data-stu-id="ff100-127">Authentication</span></span>  

 <span data-ttu-id="ff100-128">如果在运行时构造了基于用户输入的连接字符串，则在使用 SQL Server 登录名时可能会发生连接字符串注入攻击。</span><span class="sxs-lookup"><span data-stu-id="ff100-128">A connection string injection attack can occur when using SQL Server logins if a connection string based on user input is constructed at run time.</span></span> <span data-ttu-id="ff100-129">如果未检查连接字符串中是否有有效的关键字对，则攻击者可以插入其他字符，从而有可能访问服务器上的敏感数据或其他资源。</span><span class="sxs-lookup"><span data-stu-id="ff100-129">If the connection string is not checked for valid keyword pairs, an attacker can insert extra characters, potentially accessing sensitive data or other resources on the server.</span></span> <span data-ttu-id="ff100-130">尽可能使用 Windows 身份验证。</span><span class="sxs-lookup"><span data-stu-id="ff100-130">Use Windows authentication wherever possible.</span></span> <span data-ttu-id="ff100-131">如果必须使用 SQL Server 登录名，请在运行时使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 创建和验证连接字符串。</span><span class="sxs-lookup"><span data-stu-id="ff100-131">If you must use SQL Server logins, use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create and validate connection strings at run time.</span></span>  
  
### <a name="passwords"></a><span data-ttu-id="ff100-132">密码</span><span class="sxs-lookup"><span data-stu-id="ff100-132">Passwords</span></span>  

 <span data-ttu-id="ff100-133">许多攻击成功是因为入侵者能够获取或猜出特权用户的密码。</span><span class="sxs-lookup"><span data-stu-id="ff100-133">Many attacks succeed because an intruder was able to obtain or guess a password for a privileged user.</span></span> <span data-ttu-id="ff100-134">密码是抵御入侵者的第一道防线，因此设置强密码对于系统安全是绝对必要的。</span><span class="sxs-lookup"><span data-stu-id="ff100-134">Passwords are your first line of defense against intruders, so setting strong passwords is essential to the security of your system.</span></span> <span data-ttu-id="ff100-135">创建并强制实施用于混合模式身份验证的密码策略。</span><span class="sxs-lookup"><span data-stu-id="ff100-135">Create and enforce password policies for mixed mode authentication.</span></span>  
  
 <span data-ttu-id="ff100-136">即使使用 Windows 身份验证，也请始终为 `sa` 帐户分配一个强密码。</span><span class="sxs-lookup"><span data-stu-id="ff100-136">Always assign a strong password to the `sa` account, even when using Windows Authentication.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff100-137">本节内容</span><span class="sxs-lookup"><span data-stu-id="ff100-137">In This Section</span></span>  

 [<span data-ttu-id="ff100-138">在 SQL Server 中使用存储过程管理权限</span><span class="sxs-lookup"><span data-stu-id="ff100-138">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)  
 <span data-ttu-id="ff100-139">描述如何使用存储过程来管理权限和控制数据访问。</span><span class="sxs-lookup"><span data-stu-id="ff100-139">Describes how to use stored procedures to manage permissions and control data access.</span></span> <span data-ttu-id="ff100-140">使用存储过程是应对许多安全威胁的一种有效方法。</span><span class="sxs-lookup"><span data-stu-id="ff100-140">Using stored procedures is an effective way to respond to many security threats.</span></span>  
  
 [<span data-ttu-id="ff100-141">在 SQL Server 中编写安全动态 SQL</span><span class="sxs-lookup"><span data-stu-id="ff100-141">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)  
 <span data-ttu-id="ff100-142">介绍使用存储过程编写安全动态 SQL 的技术。</span><span class="sxs-lookup"><span data-stu-id="ff100-142">Describes techniques for writing secure dynamic SQL using stored procedures.</span></span>  
  
 [<span data-ttu-id="ff100-143">SQL Server 中的签名存储过程</span><span class="sxs-lookup"><span data-stu-id="ff100-143">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)  
 <span data-ttu-id="ff100-144">描述如何使用证书为存储过程签名，以使用户可以使用其无直接访问权限的数据。</span><span class="sxs-lookup"><span data-stu-id="ff100-144">Describes how to sign a stored procedure with a certificate to enable users to work with data they do not have direct access to.</span></span> <span data-ttu-id="ff100-145">这就使存储过程可执行调用方无直接执行权限的操作。</span><span class="sxs-lookup"><span data-stu-id="ff100-145">This enables stored procedures to perform operations that the caller does not have permissions to perform directly.</span></span>  
  
 [<span data-ttu-id="ff100-146">在 SQL Server 中使用模拟自定义权限</span><span class="sxs-lookup"><span data-stu-id="ff100-146">Customizing Permissions with Impersonation in SQL Server</span></span>](customizing-permissions-with-impersonation-in-sql-server.md)  
 <span data-ttu-id="ff100-147">描述如何使用 EXECUTE AS 子句来模拟另一用户。</span><span class="sxs-lookup"><span data-stu-id="ff100-147">Describes how to use the EXECUTE AS clause to impersonate another user.</span></span> <span data-ttu-id="ff100-148">模拟将执行上下文从调用方切换到指定用户。</span><span class="sxs-lookup"><span data-stu-id="ff100-148">Impersonation switches the execution context from the caller to the specified user.</span></span>  
  
 [<span data-ttu-id="ff100-149">在 SQL Server 中授予行级权限</span><span class="sxs-lookup"><span data-stu-id="ff100-149">Granting Row-Level Permissions in SQL Server</span></span>](granting-row-level-permissions-in-sql-server.md)  
 <span data-ttu-id="ff100-150">描述如何实现行级权限以限制数据访问。</span><span class="sxs-lookup"><span data-stu-id="ff100-150">Describes how to implement row-level permissions to restrict data access.</span></span>  
  
 [<span data-ttu-id="ff100-151">在 SQL Server 中创建应用程序角色</span><span class="sxs-lookup"><span data-stu-id="ff100-151">Creating Application Roles in SQL Server</span></span>](creating-application-roles-in-sql-server.md)  
 <span data-ttu-id="ff100-152">描述应用程序角色的功能。</span><span class="sxs-lookup"><span data-stu-id="ff100-152">Describes features and functionality of application roles.</span></span>  
  
 [<span data-ttu-id="ff100-153">在 SQL Server 中启用跨数据库访问</span><span class="sxs-lookup"><span data-stu-id="ff100-153">Enabling Cross-Database Access in SQL Server</span></span>](enabling-cross-database-access-in-sql-server.md)  
 <span data-ttu-id="ff100-154">描述如何在不损害安全性的情况启用跨数据库访问。</span><span class="sxs-lookup"><span data-stu-id="ff100-154">Describes how to enable cross-database access without jeopardizing security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff100-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="ff100-155">See also</span></span>

- [<span data-ttu-id="ff100-156">SQL Server 安全性</span><span class="sxs-lookup"><span data-stu-id="ff100-156">SQL Server Security</span></span>](sql-server-security.md)
- [<span data-ttu-id="ff100-157">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="ff100-157">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="ff100-158">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="ff100-158">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="ff100-159">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="ff100-159">ADO.NET Overview</span></span>](../ado-net-overview.md)
