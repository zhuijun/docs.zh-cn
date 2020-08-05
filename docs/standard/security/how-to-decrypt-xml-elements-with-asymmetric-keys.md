---
title: 如何：用非对称密钥对 XML 元素进行解密
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: 4a06628ddde0920133bfd74568786fbca6d5cf09
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556769"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="2741b-102">如何：用非对称密钥对 XML 元素进行解密</span><span class="sxs-lookup"><span data-stu-id="2741b-102">How to: Decrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="2741b-103">可以使用 <xref:System.Security.Cryptography.Xml> 命名空间中的类对 XML 文档内的元素进行加密和解密。</span><span class="sxs-lookup"><span data-stu-id="2741b-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="2741b-104">XML 加密是交换或存储加密的 XML 数据的一种标准方式，使用后就无需担心数据被轻易读取。</span><span class="sxs-lookup"><span data-stu-id="2741b-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="2741b-105">有关 XML 加密标准的详细信息，请参阅万维网联合会 (W3C) 推荐[XML 签名语法和处理](https://www.w3.org/TR/xmldsig-core/)。</span><span class="sxs-lookup"><span data-stu-id="2741b-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  

> [!NOTE]
> <span data-ttu-id="2741b-106">本文中的代码适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="2741b-106">The code in this article applies to Windows.</span></span>

<span data-ttu-id="2741b-107">此过程中的示例对使用[如何：用非对称密钥加密 XML 元素](how-to-encrypt-xml-elements-with-asymmetric-keys.md)中所述的方法进行加密的 XML 元素进行解密。</span><span class="sxs-lookup"><span data-stu-id="2741b-107">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="2741b-108">它将查找 <`EncryptedData`> 元素，对元素进行解密，然后将元素替换为原始纯文本 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="2741b-108">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="2741b-109">此示例使用两个密钥对 XML 元素进行解密。</span><span class="sxs-lookup"><span data-stu-id="2741b-109">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="2741b-110">它从密钥容器中检索以前生成的 RSA 私钥，然后使用 RSA 密钥对存储在 <> 元素的 <> 元素中的会话密钥进行解密 `EncryptedKey` `EncryptedData` 。</span><span class="sxs-lookup"><span data-stu-id="2741b-110">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="2741b-111">然后此示例使用会话密钥对 XML 元素进行解密。</span><span class="sxs-lookup"><span data-stu-id="2741b-111">The example then uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="2741b-112">此示例适用于以下情况：多个应用程序必须共享加密数据，或应用程序必须保存其每次运行之间的加密数据。</span><span class="sxs-lookup"><span data-stu-id="2741b-112">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="2741b-113">用非对称密钥对 XML 元素进行解密</span><span class="sxs-lookup"><span data-stu-id="2741b-113">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="2741b-114">创建 <xref:System.Security.Cryptography.CspParameters> 对象，并指定密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="2741b-114">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="2741b-115">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 对象从容器中检索以前生成的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="2741b-115">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="2741b-116">当将 <xref:System.Security.Cryptography.CspParameters> 对象传递到 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 构造函数中时，将自动从密钥容器中检索到密钥。</span><span class="sxs-lookup"><span data-stu-id="2741b-116">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="2741b-117">创建新 <xref:System.Security.Cryptography.Xml.EncryptedXml> 对象以对文档进行解密。</span><span class="sxs-lookup"><span data-stu-id="2741b-117">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="2741b-118">添加一个密钥/名称映射，以便 RSA 密钥与应该进行解密的文档中的元素相关联。</span><span class="sxs-lookup"><span data-stu-id="2741b-118">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="2741b-119">必须使用与加密文档时所用密钥名称相同的名称。</span><span class="sxs-lookup"><span data-stu-id="2741b-119">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="2741b-120">请注意，此名称独立于用来标识在步骤 1 中指定的密钥容器中的密钥名称。</span><span class="sxs-lookup"><span data-stu-id="2741b-120">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="2741b-121">调用 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法以解密 `EncryptedData`> 元素的 <。</span><span class="sxs-lookup"><span data-stu-id="2741b-121">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="2741b-122">此方法使用 RSA 密钥来解密会话密钥，并自动使用会话密钥来解密 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="2741b-122">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="2741b-123">它还会自动将 <`EncryptedData`> 元素替换为原始纯文本。</span><span class="sxs-lookup"><span data-stu-id="2741b-123">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="2741b-124">保存 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="2741b-124">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="2741b-125">示例</span><span class="sxs-lookup"><span data-stu-id="2741b-125">Example</span></span>

<span data-ttu-id="2741b-126">此示例假定名为 `test.xml` 的文件与已编译程序存在于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="2741b-126">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="2741b-127">它还假定 `test.xml` 包含使用[如何：使用非对称密钥对 XML 元素进行加密](how-to-encrypt-xml-elements-with-asymmetric-keys.md)中描述的方法进行加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="2741b-127">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2741b-128">编译代码</span><span class="sxs-lookup"><span data-stu-id="2741b-128">Compiling the Code</span></span>  
  
- <span data-ttu-id="2741b-129">在面向 .NET Framework 的项目中，包含对的引用 `System.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="2741b-129">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="2741b-130">在面向 .NET Core 或 .NET 5 的项目中，安装 NuGet 包[System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。</span><span class="sxs-lookup"><span data-stu-id="2741b-130">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="2741b-131">包括以下命名空间：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="2741b-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="2741b-132">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="2741b-132">.NET Security</span></span>  

<span data-ttu-id="2741b-133">永远不要以纯文本形式存储对称加密密钥，也不要以纯文本形式在计算机之间传输对称密钥。</span><span class="sxs-lookup"><span data-stu-id="2741b-133">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="2741b-134">此外，绝不存储或传输纯文本形式的非对称密钥的私钥。</span><span class="sxs-lookup"><span data-stu-id="2741b-134">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="2741b-135">有关对称和非对称加密密钥的详细信息，请参阅[生成加密和解密密钥](generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="2741b-135">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="2741b-136">绝不将密钥直接嵌入源代码。</span><span class="sxs-lookup"><span data-stu-id="2741b-136">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="2741b-137">通过使用[Ildasm.exe (IL 拆装器) ](../../framework/tools/ildasm-exe-il-disassembler.md)或在文本编辑器（如记事本）中打开程序集，可以轻松地从程序集中读取嵌入的密钥。</span><span class="sxs-lookup"><span data-stu-id="2741b-137">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="2741b-138">当你使用加密密钥执行操作后，通过将每个字节设置为零或通过调用托管加密类的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法来将它从内存中清除。</span><span class="sxs-lookup"><span data-stu-id="2741b-138">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="2741b-139">加密密钥有时可从内存由调试器读取，或从硬盘读取（如果内存位置分页到磁盘）。</span><span class="sxs-lookup"><span data-stu-id="2741b-139">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2741b-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="2741b-140">See also</span></span>

- [<span data-ttu-id="2741b-141">加密模型</span><span class="sxs-lookup"><span data-stu-id="2741b-141">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="2741b-142">加密服务</span><span class="sxs-lookup"><span data-stu-id="2741b-142">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="2741b-143">跨平台加密</span><span class="sxs-lookup"><span data-stu-id="2741b-143">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="2741b-144">如何：用非对称密钥对 XML 元素进行加密</span><span class="sxs-lookup"><span data-stu-id="2741b-144">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="2741b-145">ASP.NET Core 数据保护</span><span class="sxs-lookup"><span data-stu-id="2741b-145">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
