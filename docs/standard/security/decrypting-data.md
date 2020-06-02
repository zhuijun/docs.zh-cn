---
title: 解密数据
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 844561c0d207106a183243f5f2b3e0cea3e70422
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288363"
---
# <a name="decrypting-data"></a><span data-ttu-id="50058-102">解密数据</span><span class="sxs-lookup"><span data-stu-id="50058-102">Decrypting Data</span></span>

<span data-ttu-id="50058-103">解密是加密的反向操作。</span><span class="sxs-lookup"><span data-stu-id="50058-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="50058-104">对于私钥加密，必须知道用于加密数据的密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="50058-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="50058-105">对于公钥加密，必须知道公钥（如果使用了私钥来加密数据）或私钥（如果使用了公钥来加密数据）。</span><span class="sxs-lookup"><span data-stu-id="50058-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="50058-106">对称解密</span><span class="sxs-lookup"><span data-stu-id="50058-106">Symmetric Decryption</span></span>

<span data-ttu-id="50058-107">解密用对称算法加密的数据类似于用对称算法加密数据的过程。</span><span class="sxs-lookup"><span data-stu-id="50058-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="50058-108">若要对从任何托管流对象中读取的数据进行解密，应将 <xref:System.Security.Cryptography.CryptoStream> 与 .NET Framework 提供的对称加密类一起使用。</span><span class="sxs-lookup"><span data-stu-id="50058-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="50058-109">下面的示例演示如何创建 <xref:System.Security.Cryptography.RijndaelManaged> 类的新实例，并使用该实例对 <xref:System.Security.Cryptography.CryptoStream> 对象执行解密。</span><span class="sxs-lookup"><span data-stu-id="50058-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="50058-110">此示例首先创建 **RijndaelManaged** 类的一个新实例。</span><span class="sxs-lookup"><span data-stu-id="50058-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="50058-111">接下来，它创建一个 **CryptoStream** 对象并将其初始化为称作 `myStream`的托管流的值。</span><span class="sxs-lookup"><span data-stu-id="50058-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="50058-112">随后，将用于加密的同一个密钥和 IV 传递给 **RijndaelManaged** 类的 **CreateDecryptor** 方法，然后将该方法传递给 **CryptoStream** 构造函数。</span><span class="sxs-lookup"><span data-stu-id="50058-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="50058-113">最后，将 **CryptoStreamMode.Read** 枚举传递给 **CryptoStream** 构造函数，以指定对流的读取访问权限。</span><span class="sxs-lookup"><span data-stu-id="50058-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

<span data-ttu-id="50058-114">下面的示例显示创建流、解密流、从流中读取和关闭流的整个过程。</span><span class="sxs-lookup"><span data-stu-id="50058-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="50058-115">创建一个 <xref:System.Net.Sockets.TcpListener> 对象，它在建立到侦听对象的连接时初始化一个网络流。</span><span class="sxs-lookup"><span data-stu-id="50058-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="50058-116">然后，使用 **CryptoStream** 类和 **RijndaelManaged** 类解密该网络流。</span><span class="sxs-lookup"><span data-stu-id="50058-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="50058-117">此示例假定已成功传输或已预先商定密钥和 IV。</span><span class="sxs-lookup"><span data-stu-id="50058-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="50058-118">它不会显示加密和传输这些值所需的代码。</span><span class="sxs-lookup"><span data-stu-id="50058-118">It does not show the code needed to encrypt and transfer these values.</span></span>

```vb
Imports System.IO
Imports System.Net
Imports System.Net.Sockets
Imports System.Security.Cryptography
Imports System.Threading

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Initialize a TCPListener on port 11000
            'using the current IP address.
            Dim tcpListen As New TcpListener(IPAddress.Any, 11000)

            'Start the listener.
            tcpListen.Start()

            'Check for a connection every five seconds.
            While Not tcpListen.Pending()
                Console.WriteLine("Still listening. Will try in 5 seconds.")

                Thread.Sleep(5000)
            End While

            'Accept the client if one is found.
            Dim tcp As TcpClient = tcpListen.AcceptTcpClient()

            'Create a network stream from the connection.
            Dim netStream As NetworkStream = tcp.GetStream()

            'Create a new instance of the RijndaelManaged class
            'and decrypt the stream.
            Dim rmCrypto As New RijndaelManaged()

            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            netStream.Close()
            tcp.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The Listener Failed.")
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Net;
using System.Net.Sockets;
using System.Security.Cryptography;
using System.Threading;

class Class1
{
   static void Main(string[] args)
   {
      //The key and IV must be the same values that were used
      //to encrypt the stream.
      byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      try
      {
         //Initialize a TCPListener on port 11000
         //using the current IP address.
         TcpListener tcpListen = new TcpListener(IPAddress.Any, 11000);

         //Start the listener.
         tcpListen.Start();

         //Check for a connection every five seconds.
         while(!tcpListen.Pending())
         {
            Console.WriteLine("Still listening. Will try in 5 seconds.");
            Thread.Sleep(5000);
         }

         //Accept the client if one is found.
         TcpClient tcp = tcpListen.AcceptTcpClient();

         //Create a network stream from the connection.
         NetworkStream netStream = tcp.GetStream();

         //Create a new instance of the RijndaelManaged class
         // and decrypt the stream.
         RijndaelManaged rmCrypto = new RijndaelManaged();

         //Create a CryptoStream, pass it the NetworkStream, and decrypt
         //it with the Rijndael class using the key and IV.
         CryptoStream cryptStream = new CryptoStream(netStream,
            rmCrypto.CreateDecryptor(key, iv),
            CryptoStreamMode.Read);

         //Read the stream.
         StreamReader sReader = new StreamReader(cryptStream);

         //Display the message.
         Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

         //Close the streams.
         sReader.Close();
         netStream.Close();
         tcp.Close();
      }
      //Catch any exceptions.
      catch
      {
         Console.WriteLine("The Listener Failed.");
      }
   }
}
```

<span data-ttu-id="50058-119">为使上面的示例正常运行，必须建立一个到侦听器的加密连接。</span><span class="sxs-lookup"><span data-stu-id="50058-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="50058-120">该连接必须使用侦听器中所用的相同的密钥、IV 和算法。</span><span class="sxs-lookup"><span data-stu-id="50058-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="50058-121">如果建立了这样的连接，则会将消息解密并显示到控制台上。</span><span class="sxs-lookup"><span data-stu-id="50058-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="50058-122">不对称解密</span><span class="sxs-lookup"><span data-stu-id="50058-122">Asymmetric Decryption</span></span>

<span data-ttu-id="50058-123">通常，一方（A 方）同时生成公钥和私钥，并将其存储在内存或加密密钥容器中。</span><span class="sxs-lookup"><span data-stu-id="50058-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="50058-124">然后 A 方将公钥发送到另一方（B 方）。</span><span class="sxs-lookup"><span data-stu-id="50058-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="50058-125">使用公钥时，参与方 B 会对数据进行加密，然后将数据发送回 A 方。接收到数据后，A 方使用对应的私钥将其解密。</span><span class="sxs-lookup"><span data-stu-id="50058-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="50058-126">A 方只有使用与 B 方用于加密数据的公钥相对应的私钥，解密才能成功。</span><span class="sxs-lookup"><span data-stu-id="50058-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="50058-127">有关如何将非对称密钥存储在安全加密密钥容器中以及随后如何获取非对称密钥的信息，请参阅 [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md)。</span><span class="sxs-lookup"><span data-stu-id="50058-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="50058-128">下面的示例阐释如何对表示一个对称密钥和 IV 的两个字节数组进行解密。</span><span class="sxs-lookup"><span data-stu-id="50058-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="50058-129">有关如何以可方便地发送到第三方的格式从 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 对象提取非对称公钥的信息，请参阅 [Encrypting Data](encrypting-data.md)的托管流的值。</span><span class="sxs-lookup"><span data-stu-id="50058-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

```vb
'Create a new instance of the RSACryptoServiceProvider class.
Dim rsa As New RSACryptoServiceProvider()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, False)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, False)
```

```csharp
//Create a new instance of the RSACryptoServiceProvider class.
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, false);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , false);
```

## <a name="see-also"></a><span data-ttu-id="50058-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="50058-130">See also</span></span>

- [<span data-ttu-id="50058-131">生成加密和解密的密钥</span><span class="sxs-lookup"><span data-stu-id="50058-131">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="50058-132">加密数据</span><span class="sxs-lookup"><span data-stu-id="50058-132">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="50058-133">加密服务</span><span class="sxs-lookup"><span data-stu-id="50058-133">Cryptographic Services</span></span>](cryptographic-services.md)
