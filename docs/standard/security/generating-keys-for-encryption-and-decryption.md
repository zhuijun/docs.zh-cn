---
title: 生成加密和解密的密钥
description: 了解如何创建和管理用于 .NET 中的加密和解密的对称和非对称密钥。
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET], keys
- symmetric keys
- asymmetric keys [.NET]
- cryptography [.NET], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 7ce19dc465fb1fac22545398e0724e6b76dd7098
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556938"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="5be3b-103">生成加密和解密的密钥</span><span class="sxs-lookup"><span data-stu-id="5be3b-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="5be3b-104">创建和管理密钥是加密过程的一个重要部分。</span><span class="sxs-lookup"><span data-stu-id="5be3b-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="5be3b-105">对称算法要求创建密钥和初始化向量 (IV)。</span><span class="sxs-lookup"><span data-stu-id="5be3b-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="5be3b-106">密钥必须对不应解密数据的任何人保密。</span><span class="sxs-lookup"><span data-stu-id="5be3b-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="5be3b-107">IV 并不是一定要保密，但应定期更改。</span><span class="sxs-lookup"><span data-stu-id="5be3b-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="5be3b-108">非对称算法要求创建公钥和私钥。</span><span class="sxs-lookup"><span data-stu-id="5be3b-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="5be3b-109">公钥可以公开给任何人，而私钥必须只有将解密用公钥加密的数据的参与方知道。</span><span class="sxs-lookup"><span data-stu-id="5be3b-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="5be3b-110">本节介绍如何生成和管理对称和非对称算法的密钥。</span><span class="sxs-lookup"><span data-stu-id="5be3b-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="5be3b-111">对称密钥</span><span class="sxs-lookup"><span data-stu-id="5be3b-111">Symmetric Keys</span></span>  
 <span data-ttu-id="5be3b-112">.NET 提供的对称加密类需要一个密钥和新的初始化向量 (IV) 来加密和解密数据。</span><span class="sxs-lookup"><span data-stu-id="5be3b-112">The symmetric encryption classes supplied by .NET require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="5be3b-113">每当使用无参数方法创建一个托管对称加密类的新实例时，都会 `Create()` 自动创建新的密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="5be3b-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless `Create()` method, a new key and IV are automatically created.</span></span> <span data-ttu-id="5be3b-114">获许解密你的数据的任何人都必须具有相同的密钥和 IV 并使用相同的算法。</span><span class="sxs-lookup"><span data-stu-id="5be3b-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="5be3b-115">通常情况下，应为每个会话创建一个新的密钥和 IV，且不应为了在稍后会话中使用而存储该密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="5be3b-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="5be3b-116">为了将对称密钥和 IV 传送给远程方，通常使用不对称加密来加密对称密钥。</span><span class="sxs-lookup"><span data-stu-id="5be3b-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="5be3b-117">通过不安全的网络发送密钥而不对其进行加密会很不安全，这是因为截获密钥和 IV 的任何人都能够解密您的数据。</span><span class="sxs-lookup"><span data-stu-id="5be3b-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span>  
  
 <span data-ttu-id="5be3b-118">下面的示例演示如何创建算法的默认实现类的新实例 <xref:System.Security.Cryptography.Aes> 。</span><span class="sxs-lookup"><span data-stu-id="5be3b-118">The following example shows the creation of a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 <span data-ttu-id="5be3b-119">执行前面的代码后，将生成新的密钥和 IV，并分别置于 **Key** 和 **IV** 属性中。</span><span class="sxs-lookup"><span data-stu-id="5be3b-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="5be3b-120">有时可能需要生成多个密钥。</span><span class="sxs-lookup"><span data-stu-id="5be3b-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="5be3b-121">在这种情况下，你可以创建会实现对称算法的类的新实例，然后通过调用 **GenerateKey** 和 **GenerateIV** 方法来创建新的密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="5be3b-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="5be3b-122">下面的代码示例演示了如何在创建了对称加密类的新实例后创建新的密钥和 IVs。</span><span class="sxs-lookup"><span data-stu-id="5be3b-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
aes.GenerateIV()  
aes.GenerateKey()  
```  
  
```csharp  
Aes aes = Aes.Create();  
aes.GenerateIV();  
aes.GenerateKey();  
```  
  
 <span data-ttu-id="5be3b-123">执行前面的代码时，在新的**Aes**实例发出时，将生成一个密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="5be3b-123">When the preceding code is executed, a key and IV are generated when the new instance of **Aes** is made.</span></span> <span data-ttu-id="5be3b-124">调用 **GenerateKey** 和 **GenerateIV** 方法时会创建另一个密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="5be3b-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>
  
## <a name="asymmetric-keys"></a><span data-ttu-id="5be3b-125">非对称密钥</span><span class="sxs-lookup"><span data-stu-id="5be3b-125">Asymmetric Keys</span></span>

 <span data-ttu-id="5be3b-126">.NET <xref:System.Security.Cryptography.RSA> 为非对称加密提供了类。</span><span class="sxs-lookup"><span data-stu-id="5be3b-126">.NET provides the <xref:System.Security.Cryptography.RSA> class for asymmetric encryption.</span></span> <span data-ttu-id="5be3b-127">使用无参数 `Create()` 方法创建新的实例时，此类将创建一个公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="5be3b-127">This class creates a public/private key pair when you use the parameterless `Create()` method to create a new instance.</span></span> <span data-ttu-id="5be3b-128">可以存储非对称密钥以用于多个会话，也可以生成它以仅用于一个会话。</span><span class="sxs-lookup"><span data-stu-id="5be3b-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="5be3b-129">虽然公钥可以普遍可用，但私钥应受到严密保护。</span><span class="sxs-lookup"><span data-stu-id="5be3b-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="5be3b-130">每次创建非对称算法类的新实例时，都将生成一个公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="5be3b-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="5be3b-131">创建类的新实例后，可以使用方法提取密钥信息 <xref:System.Security.Cryptography.RSA.ExportParameters%2A> ，该方法将返回 <xref:System.Security.Cryptography.RSAParameters> 存储密钥信息的结构。</span><span class="sxs-lookup"><span data-stu-id="5be3b-131">After a new instance of the class is created, the key information can be extracted using the <xref:System.Security.Cryptography.RSA.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span> <span data-ttu-id="5be3b-132">方法接受一个布尔值，该值指示是只返回公钥信息还是同时返回公钥和私钥信息。</span><span class="sxs-lookup"><span data-stu-id="5be3b-132">The method accepts a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span>

<span data-ttu-id="5be3b-133">还有其他方法可让你提取关键信息，例如：</span><span class="sxs-lookup"><span data-stu-id="5be3b-133">There are also other methods that let you extract key information, such as:</span></span>

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

<span data-ttu-id="5be3b-134">可以通过使用方法，将**RSA**实例初始化为**RSAParameters**结构的值 <xref:System.Security.Cryptography.RSA.ImportParameters%2A> 。</span><span class="sxs-lookup"><span data-stu-id="5be3b-134">An **RSA** instance can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A> method.</span></span> <span data-ttu-id="5be3b-135">或使用方法创建一个新的实例 <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5be3b-135">Or create a new instance by using the <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5be3b-136">非对称私钥永远不应以原义或纯文本形式存储在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="5be3b-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="5be3b-137">如果需要存储私钥，则应使用密钥容器。</span><span class="sxs-lookup"><span data-stu-id="5be3b-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="5be3b-138">有关如何在密钥容器中存储私钥的详细信息，请参阅[如何：将非对称密钥存储在密钥容器中](how-to-store-asymmetric-keys-in-a-key-container.md)。</span><span class="sxs-lookup"><span data-stu-id="5be3b-138">For more information about how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="5be3b-139">下面的代码示例创建**RSA**类的新实例，创建公钥/私钥对，并将公钥信息保存到**RSAParameters**结构。</span><span class="sxs-lookup"><span data-stu-id="5be3b-139">The following code example creates a new instance of the **RSA** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSA = RSA.Create()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSA rsa = RSA.Create();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="5be3b-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="5be3b-140">See also</span></span>

- [<span data-ttu-id="5be3b-141">加密数据</span><span class="sxs-lookup"><span data-stu-id="5be3b-141">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="5be3b-142">解密数据</span><span class="sxs-lookup"><span data-stu-id="5be3b-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="5be3b-143">加密服务</span><span class="sxs-lookup"><span data-stu-id="5be3b-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="5be3b-144">如何：将非对称密钥存储在密钥容器中</span><span class="sxs-lookup"><span data-stu-id="5be3b-144">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
- [<span data-ttu-id="5be3b-145">跨平台加密</span><span class="sxs-lookup"><span data-stu-id="5be3b-145">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="5be3b-146">ASP.NET Core 数据保护</span><span class="sxs-lookup"><span data-stu-id="5be3b-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
