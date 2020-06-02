---
title: 加密签名
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: 9e69578ceffeeacb73cf059f5b577fe7c137b599
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288389"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="a9a52-102">加密签名</span><span class="sxs-lookup"><span data-stu-id="a9a52-102">Cryptographic Signatures</span></span>

<span data-ttu-id="a9a52-103">加密数字签名使用公钥算法提供数据完整性。</span><span class="sxs-lookup"><span data-stu-id="a9a52-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="a9a52-104">如果使用数字签名对数据进行签名，则其他人可验证该签名，并且可证明这些数据确实是你发出的，并且在你签名之后未被更改。</span><span class="sxs-lookup"><span data-stu-id="a9a52-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="a9a52-105">有关数字签名的详细信息，请参阅 [Cryptographic Services](cryptographic-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a52-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="a9a52-106">本主题说明如何使用 <xref:System.Security.Cryptography?displayProperty=nameWithType> 命名空间中的类来生成和验证数字签名。</span><span class="sxs-lookup"><span data-stu-id="a9a52-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="a9a52-107">生成签名</span><span class="sxs-lookup"><span data-stu-id="a9a52-107">Generating Signatures</span></span>

<span data-ttu-id="a9a52-108">数字签名通常应用于表示较大数据的哈希值。</span><span class="sxs-lookup"><span data-stu-id="a9a52-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="a9a52-109">下面的示例将数字签名应用于哈希值。</span><span class="sxs-lookup"><span data-stu-id="a9a52-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="a9a52-110">首先，创建 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类的新实例以生成公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="a9a52-110">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="a9a52-111">然后，将 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 传递到 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 类的新实例。</span><span class="sxs-lookup"><span data-stu-id="a9a52-111">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="a9a52-112">这将私钥传输给了实际执行数字签名的 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>。</span><span class="sxs-lookup"><span data-stu-id="a9a52-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="a9a52-113">必须先指定要使用的哈希算法。然后才可以对哈希代码进行签名。</span><span class="sxs-lookup"><span data-stu-id="a9a52-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="a9a52-114">本示例使用 SHA1 算法。</span><span class="sxs-lookup"><span data-stu-id="a9a52-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="a9a52-115">最后，调用 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> 方法以执行签名。</span><span class="sxs-lookup"><span data-stu-id="a9a52-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="a9a52-116">由于与 SHA1 冲突，Microsoft 建议使用 SHA256 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="a9a52-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As New RSACryptoServiceProvider()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSACryptoServiceProvider to transfer the private key.
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
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSACryptoServiceProvider to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

### <a name="signing-xml-files"></a><span data-ttu-id="a9a52-117">对 XML 文件进行签名</span><span class="sxs-lookup"><span data-stu-id="a9a52-117">Signing XML Files</span></span>

<span data-ttu-id="a9a52-118">.NET Framework 提供可实现 XML 签名的 <xref:System.Security.Cryptography.Xml> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="a9a52-118">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="a9a52-119">当想要验证 XML 是否源自某个源时，对 XML 进行签名就变得非常重要。</span><span class="sxs-lookup"><span data-stu-id="a9a52-119">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="a9a52-120">例如，如果你正在利用使用 XML 的股票报价服务，则如果已对 XML 签名，你就可以验证该 XML 的源。</span><span class="sxs-lookup"><span data-stu-id="a9a52-120">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="a9a52-121">此命名空间中的类遵循来自万维网联合会的 [XML 签名语法和处理建议](https://www.w3.org/TR/xmldsig-core/) 。</span><span class="sxs-lookup"><span data-stu-id="a9a52-121">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

## <a name="verifying-signatures"></a><span data-ttu-id="a9a52-122">验证签名</span><span class="sxs-lookup"><span data-stu-id="a9a52-122">Verifying Signatures</span></span>

<span data-ttu-id="a9a52-123">若要验证数据是否是由特定方进行签名的，则必须具有以下信息：</span><span class="sxs-lookup"><span data-stu-id="a9a52-123">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="a9a52-124">对数据进行签名的一方的公钥。</span><span class="sxs-lookup"><span data-stu-id="a9a52-124">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="a9a52-125">数字签名。</span><span class="sxs-lookup"><span data-stu-id="a9a52-125">The digital signature.</span></span>

- <span data-ttu-id="a9a52-126">已签名的数据。</span><span class="sxs-lookup"><span data-stu-id="a9a52-126">The data that was signed.</span></span>

- <span data-ttu-id="a9a52-127">签名方使用的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="a9a52-127">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="a9a52-128">若要验证由 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 类签署的签名，请使用 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 类。</span><span class="sxs-lookup"><span data-stu-id="a9a52-128">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="a9a52-129">必须向 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 类提供签名者的公钥。</span><span class="sxs-lookup"><span data-stu-id="a9a52-129">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="a9a52-130">将需要模数和指数的值以指定公钥。</span><span class="sxs-lookup"><span data-stu-id="a9a52-130">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="a9a52-131">（生成公钥/私钥对的参与方应提供这些值。）首先创建一个 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 对象以保存将验证签名的公钥，然后将 <xref:System.Security.Cryptography.RSAParameters> 结构初始化为指定公钥的模数和指数值。</span><span class="sxs-lookup"><span data-stu-id="a9a52-131">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="a9a52-132">下面的代码显示 <xref:System.Security.Cryptography.RSAParameters> 结构的创建。</span><span class="sxs-lookup"><span data-stu-id="a9a52-132">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="a9a52-133">`Modulus` 属性设置为名为 `modulusData` 的字节数组的值， `Exponent` 属性设置为名为 `exponentData`的字节数组的值。</span><span class="sxs-lookup"><span data-stu-id="a9a52-133">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="a9a52-134">创建 <xref:System.Security.Cryptography.RSAParameters> 对象后，可将 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类的新实例初始化为 <xref:System.Security.Cryptography.RSAParameters>中指定的值。</span><span class="sxs-lookup"><span data-stu-id="a9a52-134">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="a9a52-135">然后将 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 传递到 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 的构造函数以传输密钥。</span><span class="sxs-lookup"><span data-stu-id="a9a52-135">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="a9a52-136">下面的示例阐释此过程。</span><span class="sxs-lookup"><span data-stu-id="a9a52-136">The following example illustrates this process.</span></span> <span data-ttu-id="a9a52-137">在本示例中， `hashValue` 和 `signedHashValue` 是由远程方提供的字节数组。</span><span class="sxs-lookup"><span data-stu-id="a9a52-137">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="a9a52-138">远程方已使用 SHA1 算法对 `hashValue` 进行了签名，从而生成了数字签名 `signedHashValue`。</span><span class="sxs-lookup"><span data-stu-id="a9a52-138">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="a9a52-139"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>方法验证数字签名是否有效，以及是否已用于对进行签名 `hashValue` 。</span><span class="sxs-lookup"><span data-stu-id="a9a52-139">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

```vb
Dim rsa As New RSACryptoServiceProvider()
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
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();
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

<span data-ttu-id="a9a52-140">如果签名有效，则此代码段将显示“`The signature is valid`”，如果无效，则显示“`The signature is not valid`”。</span><span class="sxs-lookup"><span data-stu-id="a9a52-140">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9a52-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9a52-141">See also</span></span>

- [<span data-ttu-id="a9a52-142">加密服务</span><span class="sxs-lookup"><span data-stu-id="a9a52-142">Cryptographic Services</span></span>](cryptographic-services.md)
