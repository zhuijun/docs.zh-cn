---
title: 如何：用对称密钥对 XML 元素进行加密
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AES algorithm
- cryptography [.NET Framework], symmetric keys
- encryption [.NET Framework], symmetric keys
- symmetric keys
- System.Security.Cryptography.EncryptedXml class
- System.Security.Cryptography.RijndaelManaged class
- XML encryption
- Advanced Encryption Standard algorithm
- Rijndael
ms.assetid: d8461a44-aa2c-4ef4-b3e4-ab7cbaaee1b5
ms.openlocfilehash: 1ad75b7f36130a9f3acad97f724406650a7fdb68
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277318"
---
# <a name="how-to-encrypt-xml-elements-with-symmetric-keys"></a><span data-ttu-id="02553-102">如何：用对称密钥对 XML 元素进行加密</span><span class="sxs-lookup"><span data-stu-id="02553-102">How to: Encrypt XML Elements with Symmetric Keys</span></span>
<span data-ttu-id="02553-103">可以使用 <xref:System.Security.Cryptography.Xml> 命名空间中的类加密 XML 文档内的元素。</span><span class="sxs-lookup"><span data-stu-id="02553-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="02553-104">XML 加密可用于存储或传输敏感 XML，而无需担心数据被轻易读取。</span><span class="sxs-lookup"><span data-stu-id="02553-104">XML Encryption allows you to store or transport sensitive XML, without worrying about the data being easily read.</span></span>  <span data-ttu-id="02553-105">此过程使用高级加密标准（AES）算法（也称为 Rijndael）对 XML 元素进行加密。</span><span class="sxs-lookup"><span data-stu-id="02553-105">This procedure encrypts an XML element using the Advanced Encryption Standard (AES) algorithm, also known as Rijndael.</span></span>  
  
 <span data-ttu-id="02553-106">有关如何解密使用此过程加密的 XML 元素的信息，请参阅[如何：使用对称密钥对 Xml 元素进行解密](how-to-decrypt-xml-elements-with-symmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="02553-106">For information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Symmetric Keys](how-to-decrypt-xml-elements-with-symmetric-keys.md).</span></span>  
  
 <span data-ttu-id="02553-107">当使用对称算法（如 AES）来加密 XML 数据时，必须使用相同的密钥来加密和解密 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="02553-107">When you use a symmetric algorithm like AES to encrypt XML data, you must use the same key to encrypt and decrypt the XML data.</span></span>  <span data-ttu-id="02553-108">此过程中的示例假定加密的 XML 将使用相同的密钥进行解密，且加密方和解密方就要使用的算法和密钥达成了一致。</span><span class="sxs-lookup"><span data-stu-id="02553-108">The example in this procedure assumes that the encrypted XML will be decrypted using the same key, and that the encrypting and decrypting parties agree on the algorithm and key to use.</span></span>  <span data-ttu-id="02553-109">此示例不对加密的 XML 内的 AES 密钥进行存储或加密。</span><span class="sxs-lookup"><span data-stu-id="02553-109">This example does not store or encrypt the AES key within the encrypted XML.</span></span>  
  
 <span data-ttu-id="02553-110">此示例适用于以下情况：单个应用程序需要根据内存中存储的会话密钥加密数据，或根据从密码派生而来的加密型强密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="02553-110">This example is appropriate for situations where a single application needs to encrypt data based on a session key stored in memory, or based on a cryptographically strong key derived from a password.</span></span>  <span data-ttu-id="02553-111">对于两个或多个应用程序需要共享加密的 XML 数据的情况，请考虑使用基于非对称算法或 X.509 证书的加密方案。</span><span class="sxs-lookup"><span data-stu-id="02553-111">For situations where two or more applications need to share encrypted XML data, consider using an encryption scheme based on an asymmetric algorithm or an X.509 certificate.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-a-symmetric-key"></a><span data-ttu-id="02553-112">使用对称密钥加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="02553-112">To encrypt an XML element with a symmetric key</span></span>  
  
1. <span data-ttu-id="02553-113">使用 <xref:System.Security.Cryptography.RijndaelManaged> 类生成对称密钥。</span><span class="sxs-lookup"><span data-stu-id="02553-113">Generate a symmetric key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="02553-114">此密钥将用于加密 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="02553-114">This key will be used to encrypt the XML element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementSymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="02553-115">通过从磁盘加载 XML 文件来创建 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="02553-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="02553-116"><xref:System.Xml.XmlDocument> 对象包含要加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="02553-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementSymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="02553-117">在 <xref:System.Xml.XmlDocument> 对象中查找指定元素，并创建一个新的 <xref:System.Xml.XmlElement> 对象来表示想要加密的元素。</span><span class="sxs-lookup"><span data-stu-id="02553-117">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span>  <span data-ttu-id="02553-118">在此示例中，加密了 `"creditcard"` 元素。</span><span class="sxs-lookup"><span data-stu-id="02553-118">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementSymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="02553-119">创建 <xref:System.Security.Cryptography.Xml.EncryptedXml> 类的新实例，并将其与对称密钥一起使用来加密 <xref:System.Xml.XmlElement>。</span><span class="sxs-lookup"><span data-stu-id="02553-119">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the <xref:System.Xml.XmlElement> with the symmetric key.</span></span>  <span data-ttu-id="02553-120"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> 方法以加密的字节数组的形式返回加密元素。</span><span class="sxs-lookup"><span data-stu-id="02553-120">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementSymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="02553-121">构造一个 <xref:System.Security.Cryptography.Xml.EncryptedData> 对象并对其填充 XML 加密元素的 URL 标识符。</span><span class="sxs-lookup"><span data-stu-id="02553-121">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the XML Encryption element.</span></span>  <span data-ttu-id="02553-122">此 URL 标识符可使解密方知道 XML 包含一个加密元素。</span><span class="sxs-lookup"><span data-stu-id="02553-122">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="02553-123">可使用 <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> 字段来指定 URL 标识符。</span><span class="sxs-lookup"><span data-stu-id="02553-123">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementSymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="02553-124">创建一个 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 对象，将它初始化为用于生成密钥的加密算法的 URL 标识符。</span><span class="sxs-lookup"><span data-stu-id="02553-124">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the key.</span></span>  <span data-ttu-id="02553-125">将 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 对象传递给 <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="02553-125">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementSymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="02553-126">将加密的元素数据添加到 <xref:System.Security.Cryptography.Xml.EncryptedData> 对象。</span><span class="sxs-lookup"><span data-stu-id="02553-126">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementSymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="02553-127">将原始 <xref:System.Xml.XmlDocument> 对象中的元素替换为 <xref:System.Security.Cryptography.Xml.EncryptedData> 元素。</span><span class="sxs-lookup"><span data-stu-id="02553-127">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementSymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="02553-128">示例</span><span class="sxs-lookup"><span data-stu-id="02553-128">Example</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementSymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementSymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="02553-129">编译代码</span><span class="sxs-lookup"><span data-stu-id="02553-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="02553-130">若要编译此示例，需要包含对 `System.Security.dll` 的引用。</span><span class="sxs-lookup"><span data-stu-id="02553-130">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="02553-131">包括以下命名空间：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="02553-131">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="02553-132">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="02553-132">.NET Framework Security</span></span>  
 <span data-ttu-id="02553-133">永远不要以纯文本形式存储加密密钥，也不要以纯文本形式在计算机之间传输密钥。</span><span class="sxs-lookup"><span data-stu-id="02553-133">Never store a cryptographic key in plaintext or transfer a key between machines in plaintext.</span></span>  <span data-ttu-id="02553-134">请转而使用安全的密钥容器来存储加密密钥。</span><span class="sxs-lookup"><span data-stu-id="02553-134">Instead, use a secure key container to store cryptographic keys.</span></span>  
  
 <span data-ttu-id="02553-135">当你使用加密密钥执行操作后，通过将每个字节设置为零或通过调用托管加密类的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法来将它从内存中清除。</span><span class="sxs-lookup"><span data-stu-id="02553-135">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02553-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02553-136">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="02553-137">如何：用对称密钥对 XML 元素进行解密</span><span class="sxs-lookup"><span data-stu-id="02553-137">How to: Decrypt XML Elements with Symmetric Keys</span></span>](how-to-decrypt-xml-elements-with-symmetric-keys.md)
