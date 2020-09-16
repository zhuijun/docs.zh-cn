---
title: 在 SQL Server 中对存储过程签名
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 3f33af0238781407dd845a823ff28d87af48feb2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558545"
---
# <a name="signing-stored-procedures-in-sql-server"></a><span data-ttu-id="fd553-102">在 SQL Server 中对存储过程签名</span><span class="sxs-lookup"><span data-stu-id="fd553-102">Signing Stored Procedures in SQL Server</span></span>

<span data-ttu-id="fd553-103">数字签名是用签名人的私钥加密的数据摘要。</span><span class="sxs-lookup"><span data-stu-id="fd553-103">A digital signature is a data digest encrypted with the private key of the signer.</span></span> <span data-ttu-id="fd553-104">该私钥可确保数字签名对于其持有者或所有者是唯一的。</span><span class="sxs-lookup"><span data-stu-id="fd553-104">The private key ensures that the digital signature is unique to its bearer or owner.</span></span> <span data-ttu-id="fd553-105">你可以对存储过程、函数 (（内联表值函数) 、触发器和程序集除外）进行签名。</span><span class="sxs-lookup"><span data-stu-id="fd553-105">You can sign stored procedures, functions (except for inline table-valued functions), triggers, and assemblies.</span></span>

<span data-ttu-id="fd553-106">您可以使用证书或非对称密钥为存储过程签名。</span><span class="sxs-lookup"><span data-stu-id="fd553-106">You can sign a stored procedure with a certificate or an asymmetric key.</span></span> <span data-ttu-id="fd553-107">这适用于以下情况：无法通过所有权链接继承权限，或所有权链中断，例如动态 SQL。</span><span class="sxs-lookup"><span data-stu-id="fd553-107">This is designed for scenarios when permissions cannot be inherited through ownership chaining or when the ownership chain is broken, such as dynamic SQL.</span></span> <span data-ttu-id="fd553-108">然后，你可以创建一个映射到该证书的用户，并为该存储过程需要访问的对象授予证书用户权限。</span><span class="sxs-lookup"><span data-stu-id="fd553-108">You can then create a user mapped to the certificate, granting the certificate user permissions on the objects the stored procedure needs to access.</span></span>

<span data-ttu-id="fd553-109">您还可以创建一个映射到同一个证书的登录名，然后向该登录名授予任何必需的服务器级权限，或者将该登录名添加到一个或多个固定服务器角色中。</span><span class="sxs-lookup"><span data-stu-id="fd553-109">You can also create a login mapped to the same certificate, and then grant any necessary server-level permissions to that login, or add the login to one or more of the fixed server roles.</span></span> <span data-ttu-id="fd553-110">这是为了避免 `TRUSTWORTHY` 在需要更高级别权限的情况下启用数据库设置。</span><span class="sxs-lookup"><span data-stu-id="fd553-110">This is designed to avoid enabling the `TRUSTWORTHY` database setting for scenarios in which higher level permissions are needed.</span></span>

<span data-ttu-id="fd553-111">执行存储过程时，SQL Server 会将证书用户和/或登录的权限与调用方的权限进行组合。</span><span class="sxs-lookup"><span data-stu-id="fd553-111">When the stored procedure is executed, SQL Server combines the permissions of the certificate user and/or login with those of the caller.</span></span> <span data-ttu-id="fd553-112">与 `EXECUTE AS` 子句不同，它不会更改过程的执行上下文。</span><span class="sxs-lookup"><span data-stu-id="fd553-112">Unlike the `EXECUTE AS` clause, it does not change the execution context of the procedure.</span></span> <span data-ttu-id="fd553-113">返回登录名和用户名的内置函数会返回调用方的名称，而不是证书用户的名称。</span><span class="sxs-lookup"><span data-stu-id="fd553-113">Built-in functions that return login and user names return the name of the caller, not the certificate user name.</span></span>

## <a name="creating-certificates"></a><span data-ttu-id="fd553-114">创建证书</span><span class="sxs-lookup"><span data-stu-id="fd553-114">Creating Certificates</span></span>

<span data-ttu-id="fd553-115">使用证书或非对称密钥对存储过程进行签名时，将使用私钥创建一个由存储过程代码的加密哈希和执行方式用户组成的数据摘要。</span><span class="sxs-lookup"><span data-stu-id="fd553-115">When you sign a stored procedure with a certificate or asymmetric key, a data digest consisting of the encrypted hash of the stored procedure code, along with the execute-as user, is created using the private key.</span></span> <span data-ttu-id="fd553-116">在运行时，数据摘要将使用公钥解密并与存储过程的哈希值进行比较。</span><span class="sxs-lookup"><span data-stu-id="fd553-116">At run time, the data digest is decrypted with the public key and compared with the hash value of the stored procedure.</span></span> <span data-ttu-id="fd553-117">更改 execute as 用户会使哈希值失效，使数字签名不再匹配。</span><span class="sxs-lookup"><span data-stu-id="fd553-117">Changing the execute-as user invalidates the hash value so that the digital signature no longer matches.</span></span> <span data-ttu-id="fd553-118">修改存储过程将完全删除该签名，这会阻止无权访问私钥的用户更改存储过程代码。</span><span class="sxs-lookup"><span data-stu-id="fd553-118">Modifying the stored procedure drops the signature entirely, which prevents someone who does not have access to the private key from changing the stored procedure code.</span></span> <span data-ttu-id="fd553-119">在这两种情况下，每次更改代码或执行方式用户时，都必须对过程进行重新签名。</span><span class="sxs-lookup"><span data-stu-id="fd553-119">In either case, you must re-sign the procedure each time you change the code or the execute-as user.</span></span>

<span data-ttu-id="fd553-120">对模块进行签名涉及两个必需步骤：</span><span class="sxs-lookup"><span data-stu-id="fd553-120">There are two required steps involved in signing a module:</span></span>

1. <span data-ttu-id="fd553-121">使用 Transact-SQL `CREATE CERTIFICATE [certificateName]` 语句创建一个证书。</span><span class="sxs-lookup"><span data-stu-id="fd553-121">Create a certificate using the Transact-SQL `CREATE CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="fd553-122">此语句具有多个用于设置开始日期、结束日期和密码的选项。</span><span class="sxs-lookup"><span data-stu-id="fd553-122">This statement has several options for setting a start and end date and a password.</span></span> <span data-ttu-id="fd553-123">默认的到期日期为一年。</span><span class="sxs-lookup"><span data-stu-id="fd553-123">The default expiration date is one year.</span></span>

1. <span data-ttu-id="fd553-124">使用 Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` 语句通过证书为过程签名。</span><span class="sxs-lookup"><span data-stu-id="fd553-124">Sign the procedure with the certificate using the Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` statement.</span></span>

<span data-ttu-id="fd553-125">模块签名后，需要创建一个或多个主体，以便保存应该与证书关联的附加权限。</span><span class="sxs-lookup"><span data-stu-id="fd553-125">Once the module has been signed, one or more principals needs to be created in order to hold the additional permissions that should be associated with the certificate.</span></span>

<span data-ttu-id="fd553-126">如果模块需要其他数据库级别权限：</span><span class="sxs-lookup"><span data-stu-id="fd553-126">If the module needs additional database-level permissions:</span></span>

1. <span data-ttu-id="fd553-127">使用 Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` 语句创建与该证书关联的数据库用户。</span><span class="sxs-lookup"><span data-stu-id="fd553-127">Create a database user associated with that certificate using the Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="fd553-128">此用户仅存在于数据库中，并且不与登录名相关联，除非还使用同一证书创建了登录名。</span><span class="sxs-lookup"><span data-stu-id="fd553-128">This user exists in the database only and is not associated with a login unless a login has also been created from that same certificate.</span></span>

1. <span data-ttu-id="fd553-129">向证书用户授予所需的数据库级别权限。</span><span class="sxs-lookup"><span data-stu-id="fd553-129">Grant the certificate user the required database-level permissions.</span></span>

<span data-ttu-id="fd553-130">如果模块需要其他服务器级别权限：</span><span class="sxs-lookup"><span data-stu-id="fd553-130">If the module needs additional server-level permissions:</span></span>

1. <span data-ttu-id="fd553-131">将证书复制到 `master` 数据库。</span><span class="sxs-lookup"><span data-stu-id="fd553-131">Copy the certificate to the `master` database.</span></span>

1. <span data-ttu-id="fd553-132">使用 Transact-sql 语句创建与该证书关联的登录名 `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` 。</span><span class="sxs-lookup"><span data-stu-id="fd553-132">Create a login associated with that certificate using the Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` statement.</span></span>

1. <span data-ttu-id="fd553-133">向证书登录名授予必需的服务器级权限。</span><span class="sxs-lookup"><span data-stu-id="fd553-133">Grant the certificate login the required server-level permissions.</span></span>

> [!NOTE]
> <span data-ttu-id="fd553-134">证书不能向用户授予已经使用 DENY 语句撤消的权限。</span><span class="sxs-lookup"><span data-stu-id="fd553-134">A certificate cannot grant permissions to a user that has had permissions revoked using the DENY statement.</span></span> <span data-ttu-id="fd553-135">DENY 始终优先于 GRANT，以防止调用方继承授予给证书用户的权限。</span><span class="sxs-lookup"><span data-stu-id="fd553-135">DENY always takes precedence over GRANT, preventing the caller from inheriting permissions granted to the certificate user.</span></span>

## <a name="external-resources"></a><span data-ttu-id="fd553-136">外部资源</span><span class="sxs-lookup"><span data-stu-id="fd553-136">External Resources</span></span>

<span data-ttu-id="fd553-137">有关详细信息，请参阅以下资源。</span><span class="sxs-lookup"><span data-stu-id="fd553-137">For more information, see the following resources.</span></span>

|<span data-ttu-id="fd553-138">资源</span><span class="sxs-lookup"><span data-stu-id="fd553-138">Resource</span></span>|<span data-ttu-id="fd553-139">说明</span><span class="sxs-lookup"><span data-stu-id="fd553-139">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="fd553-140">[Module Signing（模块签名）](/previous-versions/sql/sql-server-2008/ms345102(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="fd553-140">[Module Signing](/previous-versions/sql/sql-server-2008/ms345102(v=sql.100))</span></span>|<span data-ttu-id="fd553-141">介绍模块签名，并提供示例方案和相关 Transact-sql 文章的链接。</span><span class="sxs-lookup"><span data-stu-id="fd553-141">Describes module signing, providing a sample scenario and links to the relevant Transact-SQL articles.</span></span>|
|[<span data-ttu-id="fd553-142">使用证书为存储过程签名</span><span class="sxs-lookup"><span data-stu-id="fd553-142">Signing Stored Procedures with a Certificate</span></span>](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)|<span data-ttu-id="fd553-143">提供有关使用证书为存储过程签名的教程。</span><span class="sxs-lookup"><span data-stu-id="fd553-143">Provides a tutorial for signing a stored procedure with a certificate.</span></span>|

## <a name="see-also"></a><span data-ttu-id="fd553-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="fd553-144">See also</span></span>

- [<span data-ttu-id="fd553-145">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="fd553-145">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="fd553-146">SQL Server 安全性概述</span><span class="sxs-lookup"><span data-stu-id="fd553-146">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="fd553-147">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="fd553-147">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="fd553-148">在 SQL Server 中使用存储过程管理权限</span><span class="sxs-lookup"><span data-stu-id="fd553-148">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="fd553-149">在 SQL Server 中编写安全动态 SQL</span><span class="sxs-lookup"><span data-stu-id="fd553-149">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="fd553-150">在 SQL Server 中使用模拟自定义权限</span><span class="sxs-lookup"><span data-stu-id="fd553-150">Customizing Permissions with Impersonation in SQL Server</span></span>](customizing-permissions-with-impersonation-in-sql-server.md)
- [<span data-ttu-id="fd553-151">使用存储过程修改数据</span><span class="sxs-lookup"><span data-stu-id="fd553-151">Modifying Data with Stored Procedures</span></span>](../modifying-data-with-stored-procedures.md)
- [<span data-ttu-id="fd553-152">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="fd553-152">ADO.NET Overview</span></span>](../ado-net-overview.md)
