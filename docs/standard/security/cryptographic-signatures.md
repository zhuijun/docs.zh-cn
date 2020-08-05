---
title: 加密签名
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET], signatures
- security [.NET], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: ce2be1d509da4e399bf87e1c8df7ba061fc2707c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557003"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="6a032-102">加密签名</span><span class="sxs-lookup"><span data-stu-id="6a032-102">Cryptographic Signatures</span></span>

<span data-ttu-id="6a032-103">加密数字签名使用公钥算法提供数据完整性。</span><span class="sxs-lookup"><span data-stu-id="6a032-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="6a032-104">如果使用数字签名对数据进行签名，则其他人可验证该签名，并且可证明这些数据确实是你发出的，并且在你签名之后未被更改。</span><span class="sxs-lookup"><span data-stu-id="6a032-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="6a032-105">有关数字签名的详细信息，请参阅 [Cryptographic Services](cryptographic-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6a032-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="6a032-106">本主题说明如何使用 <xref:System.Security.Cryptography> 命名空间中的类来生成和验证数字签名。</span><span class="sxs-lookup"><span data-stu-id="6a032-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="6a032-107">生成签名</span><span class="sxs-lookup"><span data-stu-id="6a032-107">Generating Signatures</span></span>

<span data-ttu-id="6a032-108">数字签名通常应用于表示较大数据的哈希值。</span><span class="sxs-lookup"><span data-stu-id="6a032-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="6a032-109">下面的示例将数字签名应用于哈希值。</span><span class="sxs-lookup"><span data-stu-id="6a032-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="6a032-110">首先，创建 <xref:System.Security.Cryptography.RSA> 类的新实例以生成公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="6a032-110">First, a new instance of the <xref:System.Security.Cryptography.RSA> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="6a032-111">然后，将 <xref:System.Security.Cryptography.RSA> 传递到 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 类的新实例。</span><span class="sxs-lookup"><span data-stu-id="6a032-111">Next, the <xref:System.Security.Cryptography.RSA> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="6a032-112">这将私钥传输给了实际执行数字签名的 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>。</span><span class="sxs-lookup"><span data-stu-id="6a032-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="6a032-113">必须先指定要使用的哈希算法。然后才可以对哈希代码进行签名。</span><span class="sxs-lookup"><span data-stu-id="6a032-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="6a032-114">本示例使用 SHA1 算法。</span><span class="sxs-lookup"><span data-stu-id="6a032-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="6a032-115">最后，调用 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> 方法以执行签名。</span><span class="sxs-lookup"><span data-stu-id="6a032-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="6a032-116">由于 SHA1 出现冲突，我们建议 SHA256 或更好。</span><span class="sxs-lookup"><span data-stu-id="6a032-116">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As RSA = RSA.Create()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSA instance to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
    End Sub
End Module
```

```csharp
using System;
using System.Security.Cryptography;

class Class1
{
   static void Main()
   {
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSA rsa = RSA.Create();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSA instance to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

## <a name="verifying-signatures"></a><span data-ttu-id="6a032-117">验证签名</span><span class="sxs-lookup"><span data-stu-id="6a032-117">Verifying Signatures</span></span>

<span data-ttu-id="6a032-118">若要验证数据是否是由特定方进行签名的，则必须具有以下信息：</span><span class="sxs-lookup"><span data-stu-id="6a032-118">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="6a032-119">对数据进行签名的一方的公钥。</span><span class="sxs-lookup"><span data-stu-id="6a032-119">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="6a032-120">数字签名。</span><span class="sxs-lookup"><span data-stu-id="6a032-120">The digital signature.</span></span>

- <span data-ttu-id="6a032-121">已签名的数据。</span><span class="sxs-lookup"><span data-stu-id="6a032-121">The data that was signed.</span></span>

- <span data-ttu-id="6a032-122">签名方使用的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="6a032-122">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="6a032-123">若要验证由 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 类签署的签名，请使用 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 类。</span><span class="sxs-lookup"><span data-stu-id="6a032-123">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="6a032-124">必须向 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 类提供签名者的公钥。</span><span class="sxs-lookup"><span data-stu-id="6a032-124">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="6a032-125">对于 RSA，你将需要模数和指数的值以指定公钥。</span><span class="sxs-lookup"><span data-stu-id="6a032-125">For RSA, you will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="6a032-126"> (生成公钥/私钥对的参与方应提供这些值。 ) 首先创建一个 <xref:System.Security.Cryptography.RSA> 对象以保存将验证签名的公钥，然后将 <xref:System.Security.Cryptography.RSAParameters> 结构初始化为指定公钥的模数和指数值。</span><span class="sxs-lookup"><span data-stu-id="6a032-126">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSA> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="6a032-127">下面的代码显示 <xref:System.Security.Cryptography.RSAParameters> 结构的创建。</span><span class="sxs-lookup"><span data-stu-id="6a032-127">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="6a032-128">`Modulus` 属性设置为名为 `modulusData` 的字节数组的值， `Exponent` 属性设置为名为 `exponentData`的字节数组的值。</span><span class="sxs-lookup"><span data-stu-id="6a032-128">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

<span data-ttu-id="6a032-129">创建 <xref:System.Security.Cryptography.RSAParameters> 对象后，可以将实现类的新实例初始化 <xref:System.Security.Cryptography.RSA> 为中指定的值 <xref:System.Security.Cryptography.RSAParameters> 。</span><span class="sxs-lookup"><span data-stu-id="6a032-129">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSA> implementation class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="6a032-130"><xref:System.Security.Cryptography.RSA>实例依次传递到的构造函数 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 以传输密钥。</span><span class="sxs-lookup"><span data-stu-id="6a032-130">The <xref:System.Security.Cryptography.RSA> instance is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="6a032-131">下面的示例阐释此过程。</span><span class="sxs-lookup"><span data-stu-id="6a032-131">The following example illustrates this process.</span></span> <span data-ttu-id="6a032-132">在本示例中， `hashValue` 和 `signedHashValue` 是由远程方提供的字节数组。</span><span class="sxs-lookup"><span data-stu-id="6a032-132">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="6a032-133">远程方已使用 SHA1 算法对 `hashValue` 进行了签名，从而生成了数字签名 `signedHashValue`。</span><span class="sxs-lookup"><span data-stu-id="6a032-133">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="6a032-134"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>方法验证数字签名是否有效，以及是否已用于对进行签名 `hashValue` 。</span><span class="sxs-lookup"><span data-stu-id="6a032-134">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

<span data-ttu-id="6a032-135">由于 SHA1 出现冲突，我们建议 SHA256 或更好。</span><span class="sxs-lookup"><span data-stu-id="6a032-135">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>  <span data-ttu-id="6a032-136">但是，如果使用 SHA1 来创建签名，则必须使用 SHA1 来验证签名。</span><span class="sxs-lookup"><span data-stu-id="6a032-136">However, if SHA1 was used to create the signature, you have to use SHA1 to verify the signature.</span></span>

```vb
Dim rsa As RSA = RSA.Create()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSA rsa = RSA.Create();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

<span data-ttu-id="6a032-137">如果签名有效，则此代码段将显示“`The signature is valid`”，如果无效，则显示“`The signature is not valid`”。</span><span class="sxs-lookup"><span data-stu-id="6a032-137">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a032-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a032-138">See also</span></span>

- [<span data-ttu-id="6a032-139">加密服务</span><span class="sxs-lookup"><span data-stu-id="6a032-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="6a032-140">加密模型</span><span class="sxs-lookup"><span data-stu-id="6a032-140">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="6a032-141">跨平台加密</span><span class="sxs-lookup"><span data-stu-id="6a032-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="6a032-142">ASP.NET Core 数据保护</span><span class="sxs-lookup"><span data-stu-id="6a032-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
