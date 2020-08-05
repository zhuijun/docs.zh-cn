---
title: 解密数据
description: 了解如何使用对称算法或非对称算法解密 .NET 中的数据。
ms.date: 07/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 2ba4c3ba43d688aeb66c67ec3f94f4a503d47892
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556977"
---
# <a name="decrypting-data"></a>解密数据

解密是加密的反向操作。 对于私钥加密，必须知道用于加密数据的密钥和 IV。 对于公钥加密，必须知道公钥（如果使用了私钥来加密数据）或私钥（如果使用了公钥来加密数据）。

## <a name="symmetric-decryption"></a>对称解密

解密用对称算法加密的数据类似于用对称算法加密数据的过程。 <xref:System.Security.Cryptography.CryptoStream>类与 .net 提供的对称加密类一起使用，对从任何托管流对象中读取的数据进行解密。

下面的示例演示如何创建算法的默认实现类的新实例 <xref:System.Security.Cryptography.Aes> 。 实例用于对对象执行解密 <xref:System.Security.Cryptography.CryptoStream> 。 此示例首先创建**Aes**实现类的新实例。 接下来，它创建一个 **CryptoStream** 对象并将其初始化为称作 `myStream`的托管流的值。 接下来，通过**Aes**类向**CreateDecryptor**方法传递用于加密的同一个密钥和 IV，然后将其传递给**CryptoStream**构造函数。

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

下面的示例显示创建流、解密流、从流中读取和关闭流的整个过程。 将创建一个文件流对象，该对象读取名为*TestData.txt*的文件。 然后，使用**CryptoStream**类和**Aes**类对文件流进行解密。 此示例指定在对称加密示例中用于[加密数据](encrypting-data.md)的密钥和 IV 值。 它不会显示加密和传输这些值所需的代码。

```vb
Imports System
Imports System.IO
Imports System.Security.Cryptography

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Create a file stream.
            Dim myStream As FileStream = new FileStream("TestData.txt", FileMode.Open)

            'Create a new instance of the default Aes implementation class
            'and decrypt the stream.
            Dim aes As Aes = Aes.Create()

            'Create an instance of the CryptoStream class, pass it the file stream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            myStream.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The decryption Failed.")
            Throw
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

class Class1
{
    static void Main(string[] args)
    {
        //The key and IV must be the same values that were used
        //to encrypt the stream.
        byte[] key = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        byte[] iv = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        try
        {
            //Create a file stream.
            FileStream myStream = new FileStream("TestData.txt", FileMode.Open);

            //Create a new instance of the default Aes implementation class
            Aes aes = Aes.Create();

            //Create a CryptoStream, pass it the file stream, and decrypt
            //it with the Aes class using the key and IV.
            CryptoStream cryptStream = new CryptoStream(
               myStream,
               aes.CreateDecryptor(key, iv),
               CryptoStreamMode.Read);

            //Read the stream.
            StreamReader sReader = new StreamReader(cryptStream);

            //Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

            //Close the streams.
            sReader.Close();
            myStream.Close();
        }
        //Catch any exceptions.
        catch
        {
            Console.WriteLine("The decryption failed.");
            throw;
        }
    }
}
```

前面的示例使用对称加密示例中用于[加密数据](encrypting-data.md)的相同密钥、IV 和算法。 它对该示例创建的*TestData.txt*文件进行解密，并在控制台上显示原始文本。

## <a name="asymmetric-decryption"></a>不对称解密

通常，一方（A 方）同时生成公钥和私钥，并将其存储在内存或加密密钥容器中。 然后 A 方将公钥发送到另一方（B 方）。 使用公钥时，参与方 B 会对数据进行加密，然后将数据发送回 A 方。接收到数据后，A 方使用对应的私钥将其解密。 A 方只有使用与 B 方用于加密数据的公钥相对应的私钥，解密才能成功。

有关如何将非对称密钥存储在安全加密密钥容器中以及随后如何获取非对称密钥的信息，请参阅 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)。

下面的示例阐释如何对表示一个对称密钥和 IV 的两个字节数组进行解密。 有关如何以可方便地发送到第三方的格式从 <xref:System.Security.Cryptography.RSA> 对象提取非对称公钥的信息，请参阅 [Encrypting Data](encrypting-data.md)的托管流的值。

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a>请参阅

- [生成加密和解密的密钥](generating-keys-for-encryption-and-decryption.md)
- [加密数据](encrypting-data.md)
- [加密服务](cryptographic-services.md)
- [加密模型](cryptography-model.md)
- [跨平台加密](cross-platform-cryptography.md)
- [使用填充对 CBC 模式对称解密的漏洞进行计时](vulnerabilities-cbc-mode.md)
- [ASP.NET Core 数据保护](/aspnet/core/security/data-protection/introduction)
