---
title: 生成加密和解密的密钥
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 992ac30310d138e04b8408497c5e49166a356ab4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291534"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="6fc75-102">生成加密和解密的密钥</span><span class="sxs-lookup"><span data-stu-id="6fc75-102">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="6fc75-103">创建和管理密钥是加密过程的一个重要部分。</span><span class="sxs-lookup"><span data-stu-id="6fc75-103">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="6fc75-104">对称算法要求创建密钥和初始化向量 (IV)。</span><span class="sxs-lookup"><span data-stu-id="6fc75-104">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="6fc75-105">密钥必须对不应解密数据的任何人保密。</span><span class="sxs-lookup"><span data-stu-id="6fc75-105">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="6fc75-106">IV 并不是一定要保密，但应定期更改。</span><span class="sxs-lookup"><span data-stu-id="6fc75-106">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="6fc75-107">非对称算法要求创建公钥和私钥。</span><span class="sxs-lookup"><span data-stu-id="6fc75-107">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="6fc75-108">公钥可以公开给任何人，而私钥必须只有将解密用公钥加密的数据的参与方知道。</span><span class="sxs-lookup"><span data-stu-id="6fc75-108">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="6fc75-109">本节介绍如何生成和管理对称和非对称算法的密钥。</span><span class="sxs-lookup"><span data-stu-id="6fc75-109">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="6fc75-110">对称密钥</span><span class="sxs-lookup"><span data-stu-id="6fc75-110">Symmetric Keys</span></span>  
 <span data-ttu-id="6fc75-111">.NET Framework 所提供的对称加密类需要一个密钥和新的初始化向量 (IV) 来加密和解密数据。</span><span class="sxs-lookup"><span data-stu-id="6fc75-111">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="6fc75-112">每当使用无参数构造函数创建一个托管对称加密类的新实例时，都会自动创建新的密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="6fc75-112">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="6fc75-113">获许解密你的数据的任何人都必须具有相同的密钥和 IV 并使用相同的算法。</span><span class="sxs-lookup"><span data-stu-id="6fc75-113">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="6fc75-114">通常情况下，应为每个会话创建一个新的密钥和 IV，且不应为了在稍后会话中使用而存储该密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="6fc75-114">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="6fc75-115">为了将对称密钥和 IV 传送给远程方，通常使用不对称加密来加密对称密钥。</span><span class="sxs-lookup"><span data-stu-id="6fc75-115">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="6fc75-116">通过不安全的网络发送密钥而不对其进行加密会很不安全，这是因为截获密钥和 IV 的任何人都能够解密您的数据。</span><span class="sxs-lookup"><span data-stu-id="6fc75-116">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="6fc75-117">有关使用加密交换数据的详细信息，请参阅 [创建加密方案](creating-a-cryptographic-scheme.md)。</span><span class="sxs-lookup"><span data-stu-id="6fc75-117">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="6fc75-118">下列示例演示如何创建 <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> 类的新实例，该类会实现 TripleDES 算法。</span><span class="sxs-lookup"><span data-stu-id="6fc75-118">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="6fc75-119">执行前面的代码后，将生成新的密钥和 IV，并分别置于 **Key** 和 **IV** 属性中。</span><span class="sxs-lookup"><span data-stu-id="6fc75-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="6fc75-120">有时可能需要生成多个密钥。</span><span class="sxs-lookup"><span data-stu-id="6fc75-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="6fc75-121">在这种情况下，你可以创建会实现对称算法的类的新实例，然后通过调用 **GenerateKey** 和 **GenerateIV** 方法来创建新的密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="6fc75-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="6fc75-122">下面的代码示例演示了如何在创建了对称加密类的新实例后创建新的密钥和 IVs。</span><span class="sxs-lookup"><span data-stu-id="6fc75-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 <span data-ttu-id="6fc75-123">执行前面的代码后，在创建 **TripleDESCryptoServiceProvider** 的新实例时会生成一个密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="6fc75-123">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="6fc75-124">调用 **GenerateKey** 和 **GenerateIV** 方法时会创建另一个密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="6fc75-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="6fc75-125">非对称密钥</span><span class="sxs-lookup"><span data-stu-id="6fc75-125">Asymmetric Keys</span></span>  
 <span data-ttu-id="6fc75-126">.NET Framework 为非对称加密提供了 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 和 <xref:System.Security.Cryptography.DSACryptoServiceProvider> 类。</span><span class="sxs-lookup"><span data-stu-id="6fc75-126">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="6fc75-127">使用无参数构造函数创建新的实例时，这些类会创建一个公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="6fc75-127">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="6fc75-128">可以存储非对称密钥以用于多个会话，也可以生成它以仅用于一个会话。</span><span class="sxs-lookup"><span data-stu-id="6fc75-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="6fc75-129">虽然公钥可以普遍可用，但私钥应受到严密保护。</span><span class="sxs-lookup"><span data-stu-id="6fc75-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="6fc75-130">每次创建非对称算法类的新实例时，都将生成一个公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="6fc75-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="6fc75-131">在创建类的新实例后，可以使用以下两种方法之一来提取密钥信息：</span><span class="sxs-lookup"><span data-stu-id="6fc75-131">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="6fc75-132"><xref:System.Security.Cryptography.RSA.ToXmlString%2A> 方法，它会返回密钥信息的的 XML 表示形式。</span><span class="sxs-lookup"><span data-stu-id="6fc75-132">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="6fc75-133"><xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> 方法，它返回存储密钥信息的 <xref:System.Security.Cryptography.RSAParameters> 结构。</span><span class="sxs-lookup"><span data-stu-id="6fc75-133">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="6fc75-134">这两种方法接受一个布尔值，该值指示是只返回公钥信息还是同时返回公钥和私钥信息。</span><span class="sxs-lookup"><span data-stu-id="6fc75-134">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="6fc75-135">通过使用 **方法，** RSACryptoServiceProvider **类可以初始化为** RSAParameters <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> 结构的值。</span><span class="sxs-lookup"><span data-stu-id="6fc75-135">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="6fc75-136">非对称私钥永远不应以原义或纯文本形式存储在本地计算机上。</span><span class="sxs-lookup"><span data-stu-id="6fc75-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="6fc75-137">如果需要存储私钥，则应使用密钥容器。</span><span class="sxs-lookup"><span data-stu-id="6fc75-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="6fc75-138">有关如何在密钥容器中存储私钥的详细信息，请参阅 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)。</span><span class="sxs-lookup"><span data-stu-id="6fc75-138">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="6fc75-139">下列代码示例通过创建公钥/私钥对来创建 **RSACryptoServiceProvider** 类的新实例，并将公钥信息保存到 **RSAParameters** 结构。</span><span class="sxs-lookup"><span data-stu-id="6fc75-139">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="6fc75-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6fc75-140">See also</span></span>

- [<span data-ttu-id="6fc75-141">加密数据</span><span class="sxs-lookup"><span data-stu-id="6fc75-141">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="6fc75-142">解密数据</span><span class="sxs-lookup"><span data-stu-id="6fc75-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="6fc75-143">加密服务</span><span class="sxs-lookup"><span data-stu-id="6fc75-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="6fc75-144">如何：将非对称密钥存储在密钥容器中</span><span class="sxs-lookup"><span data-stu-id="6fc75-144">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
