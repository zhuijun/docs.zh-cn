---
title: 加密数据
description: 了解如何在 .NET 中加密数据。 可以在数据流上使用对称加密，也可以对少量字节使用非对称加密。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 6cebdecd461f28f8228ebb8440dbff218dc211db
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662519"
---
# <a name="encrypting-data"></a><span data-ttu-id="853f7-104">加密数据</span><span class="sxs-lookup"><span data-stu-id="853f7-104">Encrypting Data</span></span>
<span data-ttu-id="853f7-105">对称加密和非对称加密是使用不同的进程执行的。</span><span class="sxs-lookup"><span data-stu-id="853f7-105">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="853f7-106">对称加密是对流执行的，因此适用于加密大量数据。</span><span class="sxs-lookup"><span data-stu-id="853f7-106">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="853f7-107">非对称加密是对少数字节执行的，因此仅适用于加密少量数据。</span><span class="sxs-lookup"><span data-stu-id="853f7-107">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="853f7-108">对称加密</span><span class="sxs-lookup"><span data-stu-id="853f7-108">Symmetric Encryption</span></span>  
 <span data-ttu-id="853f7-109">托管对称加密类与名为 <xref:System.Security.Cryptography.CryptoStream> 的特殊流类一起使用，后者用于加密读入流中的数据。</span><span class="sxs-lookup"><span data-stu-id="853f7-109">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="853f7-110">使用托管流类、实现 **接口（从实现加密算法的类创建）的类以及用于描述对** CryptoStream <xref:System.Security.Cryptography.ICryptoTransform> 授予的访问权限的类型的 <xref:System.Security.Cryptography.CryptoStreamMode> 枚举，来初始化 **CryptoStream**类。</span><span class="sxs-lookup"><span data-stu-id="853f7-110">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="853f7-111">可以**CryptoStream**使用从类派生的任何类 <xref:System.IO.Stream> （包括 <xref:System.IO.FileStream> 、和）初始化 CryptoStream 类 <xref:System.IO.MemoryStream> <xref:System.Net.Sockets.NetworkStream> 。</span><span class="sxs-lookup"><span data-stu-id="853f7-111">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="853f7-112">使用这些类，可以对多个流对象执行对称加密。</span><span class="sxs-lookup"><span data-stu-id="853f7-112">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="853f7-113">下面的示例演示如何创建 <xref:System.Security.Cryptography.RijndaelManaged> 类的新实例（该类可实现 Rijndael 加密算法），并用它对 **CryptoStream** 类进行加密。</span><span class="sxs-lookup"><span data-stu-id="853f7-113">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="853f7-114">在此示例中，使用名为 **的流对象初始化** CryptoStream `myStream` ，该流对象可以是任何类型的托管流。</span><span class="sxs-lookup"><span data-stu-id="853f7-114">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="853f7-115">向 **RijndaelManaged** 类中的 **CreateEncryptor** 方法传递用于加密的密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="853f7-115">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="853f7-116">在此例中，使用了由 `rmCrypto` 生成的默认密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="853f7-116">In this case, the default key and IV generated from `rmCrypto` are used.</span></span> <span data-ttu-id="853f7-117">最后传递 **CryptoStreamMode.Write** ，指定对流的写入权限。</span><span class="sxs-lookup"><span data-stu-id="853f7-117">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="853f7-118">执行此代码后，使用 Rijndael 算法对写入到 **CryptoStream** 对象的任何数据进行加密。</span><span class="sxs-lookup"><span data-stu-id="853f7-118">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="853f7-119">下面的示例演示创建流、加密流、写入流和关闭流的整个过程。</span><span class="sxs-lookup"><span data-stu-id="853f7-119">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="853f7-120">此示例创建使用 **CryptoStream** 类和 **RijndaelManaged** 类加密的网络流。</span><span class="sxs-lookup"><span data-stu-id="853f7-120">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="853f7-121">使用 <xref:System.IO.StreamWriter> 类将消息写入到加密流。</span><span class="sxs-lookup"><span data-stu-id="853f7-121">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="853f7-122">此示例还可用于写入文件。</span><span class="sxs-lookup"><span data-stu-id="853f7-122">You can also use this example to write to a file.</span></span> <span data-ttu-id="853f7-123">若要执行该操作，请删除 <xref:System.Net.Sockets.TcpClient> 引用，并将 <xref:System.Net.Sockets.NetworkStream> 替换为 <xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="853f7-123">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the
      'listening process.
      Dim tcp As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.
      Dim netStream As NetworkStream = tcp.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim rmCrypto As New RijndaelManaged()  
  
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt
      'it with the Rijndael class.  
      Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the
      'network stream.  
      Dim sWriter As New StreamWriter(cryptStream)  
  
      'Write to the stream.  
      sWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      sWriter.Close()  
      cryptStream.Close()  
      netStream.Close()  
      tcp.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the
         //listening process.
         TcpClient tcp = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt
         //it with the Rijndael class.  
         CryptoStream cryptStream = new CryptoStream(netStream,
         rmCrypto.CreateEncryptor(key, iv),
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the
         //network stream.  
         StreamWriter sWriter = new StreamWriter(cryptStream);  
  
         //Write to the stream.  
         sWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         sWriter.Close();  
         cryptStream.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 <span data-ttu-id="853f7-124">要使以上示例成功执行， <xref:System.Net.Sockets.TcpClient> 类中必须具有用于侦听指定 IP 地址和端口号的进程。</span><span class="sxs-lookup"><span data-stu-id="853f7-124">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="853f7-125">如果存在侦听进程，则代码将连接到该侦听进程，使用 Rijndael 对称算法加密流，并将“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="853f7-125">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="853f7-126">写入流。</span><span class="sxs-lookup"><span data-stu-id="853f7-126">to the stream.</span></span> <span data-ttu-id="853f7-127">如果代码成功运行，则它会向控制台显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="853f7-127">If the code is successful, it displays the following text to the console:</span></span>  
  
```console  
The message was sent.  
```  
  
 <span data-ttu-id="853f7-128">但是，如果找不到任何侦听进程或引发异常，则代码将向控制台显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="853f7-128">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```console  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="853f7-129">非对称加密</span><span class="sxs-lookup"><span data-stu-id="853f7-129">Asymmetric Encryption</span></span>  
 <span data-ttu-id="853f7-130">非对称算法通常用于加密少量数据，例如加密对称密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="853f7-130">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="853f7-131">通常情况下，单独执行的非对称加密使用另一方生成的公共密钥。</span><span class="sxs-lookup"><span data-stu-id="853f7-131">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="853f7-132">.NET Framework 出于此目的提供了 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类。</span><span class="sxs-lookup"><span data-stu-id="853f7-132">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="853f7-133">下面的示例使用公钥信息加密对称密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="853f7-133">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="853f7-134">初始化了代表第三方公钥的两个字节数组。</span><span class="sxs-lookup"><span data-stu-id="853f7-134">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="853f7-135"><xref:System.Security.Cryptography.RSAParameters> 对象初始化为这些值。</span><span class="sxs-lookup"><span data-stu-id="853f7-135">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="853f7-136">然后，使用 **方法将** RSAParameters **对象（以及它所代表的公钥）导入** RSACryptoServiceProvider <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="853f7-136">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="853f7-137">最后，对 <xref:System.Security.Cryptography.RijndaelManaged> 类创建私钥和 IV 进行加密。</span><span class="sxs-lookup"><span data-stu-id="853f7-137">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="853f7-138">此示例要求系统安装 128 位加密。</span><span class="sxs-lookup"><span data-stu-id="853f7-138">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim publicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte  
        Dim encryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim rsa As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()  
  
        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = publicKey  
        rsaKeyInfo.Exponent = exponent  
  
        'Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(RM.Key, False)  
        encryptedSymmetricIV = rsa.Encrypt(RM.IV, False)  
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
      byte[] publicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] encryptedSymmetricKey;  
      byte[] encryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters rsaKeyInfo = new RSAParameters();  
  
      //Set rsaKeyInfo to the public key values.
      rsaKeyInfo.Modulus = publicKey;  
      rsaKeyInfo.Exponent = exponent;  
  
      //Import key parameters into RSA.  
      rsa.ImportParameters(rsaKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged rm = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      encryptedSymmetricKey = rsa.Encrypt(rm.Key, false);  
      encryptedSymmetricIV = rsa.Encrypt(rm.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="853f7-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="853f7-139">See also</span></span>

- [<span data-ttu-id="853f7-140">生成加密和解密的密钥</span><span class="sxs-lookup"><span data-stu-id="853f7-140">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="853f7-141">解密数据</span><span class="sxs-lookup"><span data-stu-id="853f7-141">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="853f7-142">加密服务</span><span class="sxs-lookup"><span data-stu-id="853f7-142">Cryptographic Services</span></span>](cryptographic-services.md)
