---
title: 加密数据
description: 了解如何在 .NET 中使用对称算法或非对称算法加密数据。
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 8a8b5988a13ab571284b08c7aaece3542467aa71
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556964"
---
# <a name="encrypting-data"></a><span data-ttu-id="9fdf5-103">加密数据</span><span class="sxs-lookup"><span data-stu-id="9fdf5-103">Encrypting Data</span></span>

<span data-ttu-id="9fdf5-104">对称加密和非对称加密是使用不同的进程执行的。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-104">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="9fdf5-105">对称加密是对流执行的，因此适用于加密大量数据。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-105">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="9fdf5-106">非对称加密是对少数字节执行的，因此仅适用于加密少量数据。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-106">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="9fdf5-107">对称加密</span><span class="sxs-lookup"><span data-stu-id="9fdf5-107">Symmetric Encryption</span></span>  

<span data-ttu-id="9fdf5-108">托管对称加密类与名为 <xref:System.Security.Cryptography.CryptoStream> 的特殊流类一起使用，后者用于加密读入流中的数据。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-108">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="9fdf5-109">使用托管流类（ **CryptoStream**类）初始化一个类，该类实现 <xref:System.Security.Cryptography.ICryptoTransform> 接口 (从实现加密算法的类创建) ，以及 <xref:System.Security.Cryptography.CryptoStreamMode> 描述允许**CryptoStream**的访问类型的枚举。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-109">The **CryptoStream** class is initialized with a managed stream class, a class that implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="9fdf5-110">可以**CryptoStream**使用从类派生的任何类 <xref:System.IO.Stream> （包括 <xref:System.IO.FileStream> 、和）初始化 CryptoStream 类 <xref:System.IO.MemoryStream> <xref:System.Net.Sockets.NetworkStream> 。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-110">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="9fdf5-111">使用这些类，可以对多个流对象执行对称加密。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-111">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
<span data-ttu-id="9fdf5-112">下面的示例演示如何创建算法的默认实现类的新实例 <xref:System.Security.Cryptography.Aes> 。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-112">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="9fdf5-113">实例用于对**CryptoStream**类执行加密。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-113">The instance is used to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="9fdf5-114">在此示例中，使用名为 **的流对象初始化** CryptoStream `myStream` ，该流对象可以是任何类型的托管流。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-114">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="9fdf5-115">**Aes**类中的**CreateEncryptor**方法传递用于加密的密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-115">The **CreateEncryptor** method from the **Aes** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="9fdf5-116">在此例中，使用了由 `aes` 生成的默认密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-116">In this case, the default key and IV generated from `aes` are used.</span></span>
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
<span data-ttu-id="9fdf5-117">执行此代码后，将使用 AES 算法对写入到**CryptoStream**对象的任何数据进行加密。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-117">After this code is executed, any data written to the **CryptoStream** object is encrypted using the AES algorithm.</span></span>  
  
<span data-ttu-id="9fdf5-118">下面的示例演示创建流、加密流、写入流和关闭流的整个过程。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-118">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="9fdf5-119">此示例创建使用**CryptoStream**类和**Aes**类加密的文件流。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-119">This example creates a file stream that is encrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="9fdf5-120">使用 <xref:System.IO.StreamWriter> 类将消息写入到加密流。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-120">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

<span data-ttu-id="9fdf5-121">代码使用 AES 对称算法加密流，并将 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="9fdf5-121">The code encrypts the stream using the AES symmetric algorithm, and writes "Hello World!"</span></span> <span data-ttu-id="9fdf5-122">写入流。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-122">to the stream.</span></span> <span data-ttu-id="9fdf5-123">如果代码成功，它将创建一个名为*TestData.txt*的加密文件，并在控制台中显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="9fdf5-123">If the code is successful, it creates an encrypted file named *TestData.txt* and displays the following text to the console:</span></span>  
  
```console  
The text was encrypted.  
```  

<span data-ttu-id="9fdf5-124">您可以使用对称解密示例对[数据](decrypting-data.md)进行解密。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-124">You can decrypt the file by using the symmetric decryption example in [Decrypting Data](decrypting-data.md).</span></span> <span data-ttu-id="9fdf5-125">该示例和此示例指定了相同的密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-125">That example and this example specify the same key and IV.</span></span>

<span data-ttu-id="9fdf5-126">但是，如果引发异常，则代码会在控制台中显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="9fdf5-126">However, if an exception is raised, the code displays the following text to the console:</span></span>  
  
```console  
The encryption failed.  
```

## <a name="asymmetric-encryption"></a><span data-ttu-id="9fdf5-127">非对称加密</span><span class="sxs-lookup"><span data-stu-id="9fdf5-127">Asymmetric Encryption</span></span>

<span data-ttu-id="9fdf5-128">非对称算法通常用于加密少量数据，例如加密对称密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="9fdf5-129">通常情况下，单独执行的非对称加密使用另一方生成的公共密钥。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="9fdf5-130"><xref:System.Security.Cryptography.RSA>该类由 .net 提供，用于实现此目的。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-130">The <xref:System.Security.Cryptography.RSA> class is provided by .NET for this purpose.</span></span>  
  
<span data-ttu-id="9fdf5-131">下面的示例使用公钥信息加密对称密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="9fdf5-132">初始化了代表第三方公钥的两个字节数组。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="9fdf5-133"><xref:System.Security.Cryptography.RSAParameters> 对象初始化为这些值。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="9fdf5-134">接下来，使用方法将**RSAParameters**对象与它) 表示的公钥 (一起导入到**RSA**实例中 <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSA** instance using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9fdf5-135">最后，通过类创建私钥和 IV <xref:System.Security.Cryptography.Aes> 进行加密。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-135">Finally, the private key and IV created by an <xref:System.Security.Cryptography.Aes> class are encrypted.</span></span> <span data-ttu-id="9fdf5-136">此示例要求系统安装 128 位加密。</span><span class="sxs-lookup"><span data-stu-id="9fdf5-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
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
        //Initialize the byte arrays to the public key information.  
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="9fdf5-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="9fdf5-137">See also</span></span>

- [<span data-ttu-id="9fdf5-138">生成加密和解密的密钥</span><span class="sxs-lookup"><span data-stu-id="9fdf5-138">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="9fdf5-139">解密数据</span><span class="sxs-lookup"><span data-stu-id="9fdf5-139">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="9fdf5-140">加密服务</span><span class="sxs-lookup"><span data-stu-id="9fdf5-140">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="9fdf5-141">跨平台加密</span><span class="sxs-lookup"><span data-stu-id="9fdf5-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="9fdf5-142">使用填充对 CBC 模式对称解密的漏洞进行计时</span><span class="sxs-lookup"><span data-stu-id="9fdf5-142">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="9fdf5-143">ASP.NET Core 数据保护</span><span class="sxs-lookup"><span data-stu-id="9fdf5-143">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
