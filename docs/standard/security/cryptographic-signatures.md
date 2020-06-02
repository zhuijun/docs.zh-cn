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
# <a name="cryptographic-signatures"></a>加密签名

加密数字签名使用公钥算法提供数据完整性。 如果使用数字签名对数据进行签名，则其他人可验证该签名，并且可证明这些数据确实是你发出的，并且在你签名之后未被更改。 有关数字签名的详细信息，请参阅 [Cryptographic Services](cryptographic-services.md)。

本主题说明如何使用 <xref:System.Security.Cryptography?displayProperty=nameWithType> 命名空间中的类来生成和验证数字签名。

## <a name="generating-signatures"></a>生成签名

数字签名通常应用于表示较大数据的哈希值。 下面的示例将数字签名应用于哈希值。 首先，创建 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类的新实例以生成公钥/私钥对。 然后，将 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 传递到 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 类的新实例。 这将私钥传输给了实际执行数字签名的 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>。 必须先指定要使用的哈希算法。然后才可以对哈希代码进行签名。 本示例使用 SHA1 算法。 最后，调用 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> 方法以执行签名。

由于与 SHA1 冲突，Microsoft 建议使用 SHA256 或更高版本。

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

### <a name="signing-xml-files"></a>对 XML 文件进行签名

.NET Framework 提供可实现 XML 签名的 <xref:System.Security.Cryptography.Xml> 命名空间。 当想要验证 XML 是否源自某个源时，对 XML 进行签名就变得非常重要。 例如，如果你正在利用使用 XML 的股票报价服务，则如果已对 XML 签名，你就可以验证该 XML 的源。

此命名空间中的类遵循来自万维网联合会的 [XML 签名语法和处理建议](https://www.w3.org/TR/xmldsig-core/) 。

## <a name="verifying-signatures"></a>验证签名

若要验证数据是否是由特定方进行签名的，则必须具有以下信息：

- 对数据进行签名的一方的公钥。

- 数字签名。

- 已签名的数据。

- 签名方使用的哈希算法。

若要验证由 <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> 类签署的签名，请使用 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 类。 必须向 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 类提供签名者的公钥。 将需要模数和指数的值以指定公钥。 （生成公钥/私钥对的参与方应提供这些值。）首先创建一个 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 对象以保存将验证签名的公钥，然后将 <xref:System.Security.Cryptography.RSAParameters> 结构初始化为指定公钥的模数和指数值。

下面的代码显示 <xref:System.Security.Cryptography.RSAParameters> 结构的创建。 `Modulus` 属性设置为名为 `modulusData` 的字节数组的值， `Exponent` 属性设置为名为 `exponentData`的字节数组的值。

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

创建 <xref:System.Security.Cryptography.RSAParameters> 对象后，可将 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类的新实例初始化为 <xref:System.Security.Cryptography.RSAParameters>中指定的值。 然后将 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 传递到 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> 的构造函数以传输密钥。

下面的示例阐释此过程。 在本示例中， `hashValue` 和 `signedHashValue` 是由远程方提供的字节数组。 远程方已使用 SHA1 算法对 `hashValue` 进行了签名，从而生成了数字签名 `signedHashValue`。 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>方法验证数字签名是否有效，以及是否已用于对进行签名 `hashValue` 。

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

如果签名有效，则此代码段将显示“`The signature is valid`”，如果无效，则显示“`The signature is not valid`”。

## <a name="see-also"></a>另请参阅

- [加密服务](cryptographic-services.md)
