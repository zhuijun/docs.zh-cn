---
title: 在 SQL Server 中编写安全的动态 SQL
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: c598427a17ceb289f75fab481a55016f0efe5624
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147445"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a><span data-ttu-id="e271a-102">在 SQL Server 中编写安全的动态 SQL</span><span class="sxs-lookup"><span data-stu-id="e271a-102">Writing Secure Dynamic SQL in SQL Server</span></span>

<span data-ttu-id="e271a-103">SQL 注入是恶意用户输入 Transact-SQL 语句而不是有效输入的过程。</span><span class="sxs-lookup"><span data-stu-id="e271a-103">SQL Injection is the process by which a malicious user enters Transact-SQL statements instead of valid input.</span></span> <span data-ttu-id="e271a-104">如果输入未经验证直接传递到服务器，并且应用程序无意中执行了注入的代码，则攻击可能会损坏或破坏数据。</span><span class="sxs-lookup"><span data-stu-id="e271a-104">If the input is passed directly to the server without being validated and if the application inadvertently executes the injected code, the attack has the potential to damage or destroy data.</span></span>  
  
 <span data-ttu-id="e271a-105">构成 SQL 语句的任何过程都应进行注入漏洞审阅，因为 SQL Server 将执行其接收到的所有语法有效的查询。</span><span class="sxs-lookup"><span data-stu-id="e271a-105">Any procedure that constructs SQL statements should be reviewed for injection vulnerabilities because SQL Server will execute all syntactically valid queries that it receives.</span></span> <span data-ttu-id="e271a-106">一个有经验的、坚定的攻击者甚至可以操作参数化数据。</span><span class="sxs-lookup"><span data-stu-id="e271a-106">Even parameterized data can be manipulated by a skilled and determined attacker.</span></span> <span data-ttu-id="e271a-107">如果使用动态 SQL，请确保参数化命令，并且切勿直接将参数值包含在查询字符串中。</span><span class="sxs-lookup"><span data-stu-id="e271a-107">If you use dynamic SQL, be sure to parameterize your commands, and never include parameter values directly into the query string.</span></span>  
  
## <a name="anatomy-of-a-sql-injection-attack"></a><span data-ttu-id="e271a-108">SQL 注入攻击剖析</span><span class="sxs-lookup"><span data-stu-id="e271a-108">Anatomy of a SQL Injection Attack</span></span>  

 <span data-ttu-id="e271a-109">注入过程的工作方式是提前终止文本字符串，然后追加一个新的命令。</span><span class="sxs-lookup"><span data-stu-id="e271a-109">The injection process works by prematurely terminating a text string and appending a new command.</span></span> <span data-ttu-id="e271a-110">由于插入的命令可能在执行前追加其他字符串，因此攻击者将用注释标记“--”来终止注入的字符串。</span><span class="sxs-lookup"><span data-stu-id="e271a-110">Because the inserted command may have additional strings appended to it before it is executed, the malefactor terminates the injected string with a comment mark "--".</span></span> <span data-ttu-id="e271a-111">执行时，此后的文本将被忽略。</span><span class="sxs-lookup"><span data-stu-id="e271a-111">Subsequent text is ignored at execution time.</span></span> <span data-ttu-id="e271a-112">可以使用分号 (;) 分隔符插入多个命令。</span><span class="sxs-lookup"><span data-stu-id="e271a-112">Multiple commands can be inserted using a semicolon (;) delimiter.</span></span>  
  
 <span data-ttu-id="e271a-113">只要注入的 SQL 代码语法正确，便无法采用编程方式来检测篡改。</span><span class="sxs-lookup"><span data-stu-id="e271a-113">As long as injected SQL code is syntactically correct, tampering cannot be detected programmatically.</span></span> <span data-ttu-id="e271a-114">因此，必须验证所有用户输入，并仔细检查在您所用的服务器中执行构造 SQL 命令的代码。</span><span class="sxs-lookup"><span data-stu-id="e271a-114">Therefore, you must validate all user input and carefully review code that executes constructed SQL commands in the server that you are using.</span></span> <span data-ttu-id="e271a-115">绝不串联未验证的用户输入。</span><span class="sxs-lookup"><span data-stu-id="e271a-115">Never concatenate user input that is not validated.</span></span> <span data-ttu-id="e271a-116">字符串串联是脚本注入的主要输入点。</span><span class="sxs-lookup"><span data-stu-id="e271a-116">String concatenation is the primary point of entry for script injection.</span></span>  
  
 <span data-ttu-id="e271a-117">下面是一些有用的指导原则：</span><span class="sxs-lookup"><span data-stu-id="e271a-117">Here are some helpful guidelines:</span></span>  
  
- <span data-ttu-id="e271a-118">切勿直接从用户输入构建 Transact-SQL 语句；使用存储过程来验证用户输入。</span><span class="sxs-lookup"><span data-stu-id="e271a-118">Never build Transact-SQL statements directly from user input; use stored procedures to validate user input.</span></span>  
  
- <span data-ttu-id="e271a-119">通过测试类型、长度、格式和范围来验证用户输入。</span><span class="sxs-lookup"><span data-stu-id="e271a-119">Validate user input by testing type, length, format, and range.</span></span> <span data-ttu-id="e271a-120">使用 Transact-SQL QUOTENAME() 函数转义系统名称，或使用 REPLACE() 函数转义字符串中的任何字符。</span><span class="sxs-lookup"><span data-stu-id="e271a-120">Use the Transact-SQL QUOTENAME() function to escape system names or the REPLACE() function to escape any character in a string.</span></span>  
  
- <span data-ttu-id="e271a-121">在应用程序的每一层中实施多层验证。</span><span class="sxs-lookup"><span data-stu-id="e271a-121">Implement multiple layers of validation in each tier of your application.</span></span>  
  
- <span data-ttu-id="e271a-122">测试输入的大小和数据类型，强制执行适当的限制。</span><span class="sxs-lookup"><span data-stu-id="e271a-122">Test the size and data type of input and enforce appropriate limits.</span></span> <span data-ttu-id="e271a-123">这有助于防止有意造成的缓冲区溢出。</span><span class="sxs-lookup"><span data-stu-id="e271a-123">This can help prevent deliberate buffer overruns.</span></span>  
  
- <span data-ttu-id="e271a-124">测试字符串变量的内容，只接受所需的值。</span><span class="sxs-lookup"><span data-stu-id="e271a-124">Test the content of string variables and accept only expected values.</span></span> <span data-ttu-id="e271a-125">拒绝包含二进制数据、转义序列和注释字符的输入内容。</span><span class="sxs-lookup"><span data-stu-id="e271a-125">Reject entries that contain binary data, escape sequences, and comment characters.</span></span>  
  
- <span data-ttu-id="e271a-126">使用 XML 文档时，根据数据的架构对输入的所有数据进行验证。</span><span class="sxs-lookup"><span data-stu-id="e271a-126">When you are working with XML documents, validate all data against its schema as it is entered.</span></span>  
  
- <span data-ttu-id="e271a-127">在多层环境中，所有数据都应该在验证之后才允许进入可信区域。</span><span class="sxs-lookup"><span data-stu-id="e271a-127">In multi-tiered environments, all data should be validated before admission to the trusted zone.</span></span>  
  
- <span data-ttu-id="e271a-128">不接受以下来自可构造文件名的字段中的字符串：AUX、CLOCK$、COM1 到 COM8、CON、CONFIG$、LPT1 到 LPT8、NUL 和 PRN。</span><span class="sxs-lookup"><span data-stu-id="e271a-128">Do not accept the following strings in fields from which file names can be constructed: AUX, CLOCK$, COM1 through COM8, CON, CONFIG$, LPT1 through LPT8, NUL, and PRN.</span></span>  
  
- <span data-ttu-id="e271a-129">将 <xref:System.Data.SqlClient.SqlParameter> 对象与存储过程和命令一起使用以提供类型检查和长度验证。</span><span class="sxs-lookup"><span data-stu-id="e271a-129">Use <xref:System.Data.SqlClient.SqlParameter> objects with stored procedures and commands to provide type checking and length validation.</span></span>  
  
- <span data-ttu-id="e271a-130">在客户端代码中使用 <xref:System.Text.RegularExpressions.Regex> 表达式来筛选无效字符。</span><span class="sxs-lookup"><span data-stu-id="e271a-130">Use <xref:System.Text.RegularExpressions.Regex> expressions in client code to filter invalid characters.</span></span>  
  
## <a name="dynamic-sql-strategies"></a><span data-ttu-id="e271a-131">动态 SQL 策略</span><span class="sxs-lookup"><span data-stu-id="e271a-131">Dynamic SQL Strategies</span></span>  

 <span data-ttu-id="e271a-132">在过程代码中执行动态创建的 SQL 语句会中断所有权链，从而导致 SQL Server 针对动态 SQL 访问的对象检查调用方的权限。</span><span class="sxs-lookup"><span data-stu-id="e271a-132">Executing dynamically created SQL statements in your procedural code breaks the ownership chain, causing SQL Server to check the permissions of the caller against the objects being accessed by the dynamic SQL.</span></span>  
  
 <span data-ttu-id="e271a-133">SQL Server 提供一些方法，用于向用户授予使用存储过程和可执行动态 SQL 的用户定义函数来访问数据的权限。</span><span class="sxs-lookup"><span data-stu-id="e271a-133">SQL Server has methods for granting users access to data using stored procedures and user-defined functions that execute dynamic SQL.</span></span>  
  
- <span data-ttu-id="e271a-134">如[在 SQL Server 中使用模拟自定义权限](customizing-permissions-with-impersonation-in-sql-server.md)中所述，将模拟用于 Transact-SQL EXECUTE AS 子句。</span><span class="sxs-lookup"><span data-stu-id="e271a-134">Using impersonation with the Transact-SQL EXECUTE AS clause, as described in [Customizing Permissions with Impersonation in SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).</span></span>  
  
- <span data-ttu-id="e271a-135">使用证书对存储过程签名，如[在 SQL Server 中对存储过程签名](signing-stored-procedures-in-sql-server.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="e271a-135">Signing stored procedures with certificates, as described in [Signing Stored Procedures in SQL Server](signing-stored-procedures-in-sql-server.md).</span></span>  
  
### <a name="execute-as"></a><span data-ttu-id="e271a-136">EXECUTE AS</span><span class="sxs-lookup"><span data-stu-id="e271a-136">EXECUTE AS</span></span>  

 <span data-ttu-id="e271a-137">EXECUTE AS 子句会将调用方的权限替换为 EXECUTE AS 子句中指定的用户的权限。</span><span class="sxs-lookup"><span data-stu-id="e271a-137">The EXECUTE AS clause replaces the permissions of the caller with that of the user specified in the EXECUTE AS clause.</span></span> <span data-ttu-id="e271a-138">嵌套存储过程或触发器会在代理用户的安全上下文下执行。</span><span class="sxs-lookup"><span data-stu-id="e271a-138">Nested stored procedures or triggers execute under the security context of the proxy user.</span></span> <span data-ttu-id="e271a-139">这可能会破坏依赖行级安全性或需要审核的应用程序。</span><span class="sxs-lookup"><span data-stu-id="e271a-139">This can break applications that rely on row-level security or require auditing.</span></span> <span data-ttu-id="e271a-140">某些返回用户标识的函数会返回 EXECUTE AS 子句中指定的用户，而不是原始调用方。</span><span class="sxs-lookup"><span data-stu-id="e271a-140">Some functions that return the identity of the user return the user specified in the EXECUTE AS clause, not the original caller.</span></span> <span data-ttu-id="e271a-141">仅在执行过程后或发出 REVERT 语句时，执行上下文才会还原为原始调用方。</span><span class="sxs-lookup"><span data-stu-id="e271a-141">Execution context is reverted to the original caller only after execution of the procedure or when a REVERT statement is issued.</span></span>  
  
### <a name="certificate-signing"></a><span data-ttu-id="e271a-142">证书签名</span><span class="sxs-lookup"><span data-stu-id="e271a-142">Certificate Signing</span></span>  

 <span data-ttu-id="e271a-143">执行已使用证书签名的存储过程时，授予证书用户的权限将与调用方的权限合并。</span><span class="sxs-lookup"><span data-stu-id="e271a-143">When a stored procedure that has been signed with a certificate executes, the permissions granted to the certificate user are merged with those of the caller.</span></span> <span data-ttu-id="e271a-144">执行上下文保持不变；证书用户不会模拟调用方。</span><span class="sxs-lookup"><span data-stu-id="e271a-144">The execution context remains the same; the certificate user does not impersonate the caller.</span></span> <span data-ttu-id="e271a-145">对存储过程进行签名需要执行几个步骤。</span><span class="sxs-lookup"><span data-stu-id="e271a-145">Signing stored procedures requires several steps to implement.</span></span> <span data-ttu-id="e271a-146">每次修改过程时，都必须重新签名。</span><span class="sxs-lookup"><span data-stu-id="e271a-146">Each time the procedure is modified, it must be re-signed.</span></span>  
  
### <a name="cross-database-access"></a><span data-ttu-id="e271a-147">跨数据库访问</span><span class="sxs-lookup"><span data-stu-id="e271a-147">Cross Database Access</span></span>  

 <span data-ttu-id="e271a-148">在执行动态创建的 SQL 语句的情况下，跨数据库所有权链不起作用。</span><span class="sxs-lookup"><span data-stu-id="e271a-148">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed.</span></span> <span data-ttu-id="e271a-149">在 SQL Server 中，可以通过创建一个可访问另一个数据库中数据的存储过程并用两个数据库中都存在的证书为此过程签名来解决这个问题。</span><span class="sxs-lookup"><span data-stu-id="e271a-149">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="e271a-150">这样，用户就可以访问该过程使用的数据库资源，而无需授予他们数据库访问或权限。</span><span class="sxs-lookup"><span data-stu-id="e271a-150">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e271a-151">外部资源</span><span class="sxs-lookup"><span data-stu-id="e271a-151">External Resources</span></span>  

 <span data-ttu-id="e271a-152">有关详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="e271a-152">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="e271a-153">资源</span><span class="sxs-lookup"><span data-stu-id="e271a-153">Resource</span></span>|<span data-ttu-id="e271a-154">说明</span><span class="sxs-lookup"><span data-stu-id="e271a-154">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e271a-155">SQL Server 联机丛书中的[存储过程](/sql/relational-databases/stored-procedures/stored-procedures-database-engine)和 [SQL 注入](/sql/relational-databases/security/sql-injection)</span><span class="sxs-lookup"><span data-stu-id="e271a-155">[Stored Procedures](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) and [SQL Injection](/sql/relational-databases/security/sql-injection) in SQL Server Books Online</span></span>|<span data-ttu-id="e271a-156">上述主题描述了如何创建存储过程以及 SQL 注入的工作原理。</span><span class="sxs-lookup"><span data-stu-id="e271a-156">Topics describe how to create stored procedures and how SQL Injection works.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e271a-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="e271a-157">See also</span></span>

- [<span data-ttu-id="e271a-158">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="e271a-158">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="e271a-159">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="e271a-159">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="e271a-160">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="e271a-160">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="e271a-161">在 SQL Server 中使用存储过程管理权限</span><span class="sxs-lookup"><span data-stu-id="e271a-161">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="e271a-162">SQL Server 中的签名存储过程</span><span class="sxs-lookup"><span data-stu-id="e271a-162">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="e271a-163">在 SQL Server 中使用模拟自定义权限</span><span class="sxs-lookup"><span data-stu-id="e271a-163">Customizing Permissions with Impersonation in SQL Server</span></span>](customizing-permissions-with-impersonation-in-sql-server.md)
- [<span data-ttu-id="e271a-164">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="e271a-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
