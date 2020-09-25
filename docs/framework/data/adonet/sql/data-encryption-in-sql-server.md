---
title: SQL Server 中的数据加密
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: d0bda11f1a2933d096aa91d2be79d3af35172284
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169526"
---
# <a name="data-encryption-in-sql-server"></a><span data-ttu-id="5660f-102">SQL Server 中的数据加密</span><span class="sxs-lookup"><span data-stu-id="5660f-102">Data Encryption in SQL Server</span></span>

<span data-ttu-id="5660f-103">SQL Server 提供了使用证书、非对称密钥或对称密钥对数据进行加密和解密的功能。</span><span class="sxs-lookup"><span data-stu-id="5660f-103">SQL Server provides functions to encrypt and decrypt data using a certificate, asymmetric key, or symmetric key.</span></span> <span data-ttu-id="5660f-104">它在一个内部证书存储中管理所有这些证书或密钥。</span><span class="sxs-lookup"><span data-stu-id="5660f-104">It manages all of these in an internal certificate store.</span></span> <span data-ttu-id="5660f-105">该存储使用加密层次结构，可在层次结构中的上一层级别保护证书和密钥。</span><span class="sxs-lookup"><span data-stu-id="5660f-105">The store uses an encryption hierarchy that secures certificates and keys at one level with the layer above it in the hierarchy.</span></span> <span data-ttu-id="5660f-106">SQL Server 的此功能区域称为“机密存储”。</span><span class="sxs-lookup"><span data-stu-id="5660f-106">This feature area of SQL Server is called Secret Storage.</span></span>  
  
 <span data-ttu-id="5660f-107">加密功能支持的最快加密模式是对称密钥加密。</span><span class="sxs-lookup"><span data-stu-id="5660f-107">The fastest mode of encryption supported by the encryption functions is symmetric key encryption.</span></span> <span data-ttu-id="5660f-108">此模式适用于处理大量数据。</span><span class="sxs-lookup"><span data-stu-id="5660f-108">This mode is suitable for handling large volumes of data.</span></span> <span data-ttu-id="5660f-109">可以通过证书、密码或其他对称密钥加密对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5660f-109">The symmetric keys can be encrypted by certificates, passwords or other symmetric keys.</span></span>  
  
## <a name="keys-and-algorithms"></a><span data-ttu-id="5660f-110">密钥和算法</span><span class="sxs-lookup"><span data-stu-id="5660f-110">Keys and Algorithms</span></span>  

 <span data-ttu-id="5660f-111">SQL Server 支持多种对称密钥加密算法，包括 DES、Triple DES、RC2、RC4、128 位 RC4、DESX、128 位 AES、192 位 AES 和 256 位 AES。</span><span class="sxs-lookup"><span data-stu-id="5660f-111">SQL Server supports several symmetric key encryption algorithms, including DES, Triple DES, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192-bit AES, and 256-bit AES.</span></span> <span data-ttu-id="5660f-112">这些算法使用 Windows 加密 API 实现。</span><span class="sxs-lookup"><span data-stu-id="5660f-112">The algorithms are implemented using the Windows Crypto API.</span></span>  
  
 <span data-ttu-id="5660f-113">在数据库连接范围内，SQL Server 可以保留多个开放式对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5660f-113">Within the scope of a database connection, SQL Server can maintain multiple open symmetric keys.</span></span> <span data-ttu-id="5660f-114">开放式密钥从存储中进行检索，并可用于解密数据。</span><span class="sxs-lookup"><span data-stu-id="5660f-114">An open key is retrieved from the store and is available for decrypting data.</span></span> <span data-ttu-id="5660f-115">解密一段数据时，不需要指定要使用的对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5660f-115">When a piece of data is decrypted, there is no need to specify the symmetric key to use.</span></span> <span data-ttu-id="5660f-116">每个加密的值均包含用于加密该值的密钥的密钥标识符（密钥 GUID）。</span><span class="sxs-lookup"><span data-stu-id="5660f-116">Each encrypted value contains the key identifier (key GUID) of the key used to encrypt it.</span></span> <span data-ttu-id="5660f-117">如果已解密正确的密钥并且该密钥已开放，则引擎会将加密的字节流匹配到开放式对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5660f-117">The engine matches the encrypted byte stream to an open symmetric key, if the correct key has been decrypted and is open.</span></span> <span data-ttu-id="5660f-118">然后使用此密钥执行解密并返回数据。</span><span class="sxs-lookup"><span data-stu-id="5660f-118">This key is then used to perform decryption and return the data.</span></span> <span data-ttu-id="5660f-119">如果正确的密钥未开放，则返回 NULL。</span><span class="sxs-lookup"><span data-stu-id="5660f-119">If the correct key is not open, NULL is returned.</span></span>  
  
 <span data-ttu-id="5660f-120">有关演示如何处理数据库中的加密数据的示例，请参阅 [对数据列进行加密](/sql/relational-databases/security/encryption/encrypt-a-column-of-data)。</span><span class="sxs-lookup"><span data-stu-id="5660f-120">For an example that shows how to work with encrypted data in a database, see [Encrypt a Column of Data](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).</span></span>
  
## <a name="external-resources"></a><span data-ttu-id="5660f-121">外部资源</span><span class="sxs-lookup"><span data-stu-id="5660f-121">External Resources</span></span>  

 <span data-ttu-id="5660f-122">有关数据加密的更多信息，请参见以下资源。</span><span class="sxs-lookup"><span data-stu-id="5660f-122">For more information on data encryption, see the following resources.</span></span>  
  
|<span data-ttu-id="5660f-123">资源</span><span class="sxs-lookup"><span data-stu-id="5660f-123">Resource</span></span>|<span data-ttu-id="5660f-124">说明</span><span class="sxs-lookup"><span data-stu-id="5660f-124">Description</span></span>|  
|-|-|  
|[<span data-ttu-id="5660f-125">SQL Server 加密</span><span class="sxs-lookup"><span data-stu-id="5660f-125">SQL Server Encryption</span></span>](/sql/relational-databases/security/encryption/sql-server-encryption)|<span data-ttu-id="5660f-126">概述了 SQL Server 中的加密。</span><span class="sxs-lookup"><span data-stu-id="5660f-126">Provides an overview of encryption in SQL Server.</span></span> <span data-ttu-id="5660f-127">本主题包括指向其他文章的链接。</span><span class="sxs-lookup"><span data-stu-id="5660f-127">This topic includes links to additional articles.</span></span>|  
|[<span data-ttu-id="5660f-128">加密层次结构</span><span class="sxs-lookup"><span data-stu-id="5660f-128">Encryption Hierarchy</span></span>](/sql/relational-databases/security/encryption/encryption-hierarchy)|<span data-ttu-id="5660f-129">概述了 SQL Server 中的加密。</span><span class="sxs-lookup"><span data-stu-id="5660f-129">Provides an overview of encryption in SQL Server.</span></span> <span data-ttu-id="5660f-130">本主题提供指向其他文章的链接。</span><span class="sxs-lookup"><span data-stu-id="5660f-130">This topic provides links to additional articles.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5660f-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="5660f-131">See also</span></span>

- [<span data-ttu-id="5660f-132">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="5660f-132">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="5660f-133">SQL Server 中的应用程序安全方案</span><span class="sxs-lookup"><span data-stu-id="5660f-133">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="5660f-134">SQL Server 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="5660f-134">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)
- [<span data-ttu-id="5660f-135">SQL Server 中的服务器和数据库角色</span><span class="sxs-lookup"><span data-stu-id="5660f-135">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)
- [<span data-ttu-id="5660f-136">SQL Server 中的所有权和用户架构分离</span><span class="sxs-lookup"><span data-stu-id="5660f-136">Ownership and User-Schema Separation in SQL Server</span></span>](ownership-and-user-schema-separation-in-sql-server.md)
- [<span data-ttu-id="5660f-137">SQL Server 中的授权和权限</span><span class="sxs-lookup"><span data-stu-id="5660f-137">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)
- [<span data-ttu-id="5660f-138">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="5660f-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
