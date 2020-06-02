---
title: 如何：用非对称密钥对 XML 元素进行加密
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- AES algorithm
- System.Security.Cryptography.RSACryptoServiceProvider class
- asymmetric keys [.NET Framework]
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- key containers
- Advanced Encryption Standard algorithm
- Rijndael
- encryption [.NET Framework], asymmetric keys
ms.assetid: a164ba4f-e596-4bbe-a9ca-f214fe89ed48
ms.openlocfilehash: 475446f6206676e93ea72d16e01bcf1067c24e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277370"
---
# <a name="how-to-encrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="bbffd-102">如何：用非对称密钥对 XML 元素进行加密</span><span class="sxs-lookup"><span data-stu-id="bbffd-102">How to: Encrypt XML Elements with Asymmetric Keys</span></span>
<span data-ttu-id="bbffd-103">可以使用 <xref:System.Security.Cryptography.Xml> 命名空间中的类加密 XML 文档内的元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt an element within an XML document.</span></span>  <span data-ttu-id="bbffd-104">XML 加密是交换或存储加密的 XML 数据的一种标准方式，使用后就无需担心数据被轻易读取。</span><span class="sxs-lookup"><span data-stu-id="bbffd-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="bbffd-105">有关 XML 加密标准的详细信息，请参阅位于的 XML 加密的万维网联合会（W3C）规范 <https://www.w3.org/TR/xmldsig-core/> 。</span><span class="sxs-lookup"><span data-stu-id="bbffd-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="bbffd-106">可以使用 XML 加密将任何 XML 元素或文档替换为包含加密 XML 数据的 <`EncryptedData`> 元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-106">You can use XML Encryption to replace any XML element or document with an <`EncryptedData`> element that contains the encrypted XML data.</span></span>  <span data-ttu-id="bbffd-107"><`EncryptedData`> 元素还可以包含子元素，这些子元素包含有关加密期间使用的密钥和进程的信息。</span><span class="sxs-lookup"><span data-stu-id="bbffd-107">The <`EncryptedData`> element can also contain sub elements that include information about the keys and processes used during encryption.</span></span>  <span data-ttu-id="bbffd-108">XML 加密允许文档包含多个加密元素，并允许对一个元素进行多次加密。</span><span class="sxs-lookup"><span data-stu-id="bbffd-108">XML Encryption allows a document to contain multiple encrypted elements and allows an element to be encrypted multiple times.</span></span>  <span data-ttu-id="bbffd-109">此过程中的代码示例演示如何创建一个 <`EncryptedData`> 元素以及其他一些子元素，这些子元素可在稍后解密过程中使用。</span><span class="sxs-lookup"><span data-stu-id="bbffd-109">The code example in this procedure shows how to create an <`EncryptedData`> element along with several other sub elements that you can use later during decryption.</span></span>  
  
 <span data-ttu-id="bbffd-110">此示例使用两个密钥对 XML 元素进行加密。</span><span class="sxs-lookup"><span data-stu-id="bbffd-110">This example encrypts an XML element using two keys.</span></span>  <span data-ttu-id="bbffd-111">它生成 RSA 公钥/私钥对，并将密钥对保存到安全的密钥容器中。</span><span class="sxs-lookup"><span data-stu-id="bbffd-111">It generates an RSA public/private key pair and saves the key pair to a secure key container.</span></span>  <span data-ttu-id="bbffd-112">然后，此示例使用高级加密标准 (AES) 算法（也称为 Rijndael 算法）创建单独的会话密钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-112">The example then creates a separate session key using the Advanced Encryption Standard (AES) algorithm, also called the Rijndael algorithm.</span></span>  <span data-ttu-id="bbffd-113">使用 AES 会话密钥对 XML 文档进行加密，再使用 RSA 公钥对 AES 会话密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="bbffd-113">The example uses the AES session key to encrypt the XML document and then uses the RSA public key to encrypt the AES session key.</span></span>  <span data-ttu-id="bbffd-114">最后，该示例会将加密的 AES 会话密钥和加密的 XML 数据保存到新的 <> 元素中的 XML 文档 `EncryptedData` 。</span><span class="sxs-lookup"><span data-stu-id="bbffd-114">Finally, the example saves the encrypted AES session key and the encrypted XML data to the XML document within a new <`EncryptedData`> element.</span></span>  
  
 <span data-ttu-id="bbffd-115">若要解密 XML 元素，可检索密钥容器中的 RSA 私钥，用其来解密会话密钥，然后使用会话密钥来解密文档。</span><span class="sxs-lookup"><span data-stu-id="bbffd-115">To decrypt the XML element, you retrieve the RSA private key from the key container, use it to decrypt the session key, and then use the session key to decrypt the document.</span></span>  <span data-ttu-id="bbffd-116">有关如何解密使用此过程加密的 XML 元素的详细信息，请参阅[如何：使用非对称密钥对 Xml 元素进行解密](how-to-decrypt-xml-elements-with-asymmetric-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="bbffd-116">For more information about how to decrypt an XML element that was encrypted using this procedure, see [How to: Decrypt XML Elements with Asymmetric Keys](how-to-decrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
 <span data-ttu-id="bbffd-117">此示例适用于以下情况：多个应用程序需要共享加密数据，或应用程序需要保存它各次运行之间的加密数据。</span><span class="sxs-lookup"><span data-stu-id="bbffd-117">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-encrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="bbffd-118">使用非对称密钥加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="bbffd-118">To encrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="bbffd-119">创建 <xref:System.Security.Cryptography.CspParameters> 对象，并指定密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="bbffd-119">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="bbffd-120">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类生成对称密钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-120">Generate a symmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="bbffd-121">当将 <xref:System.Security.Cryptography.CspParameters> 对象传递 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类的构造函数时，密钥将自动保存在密钥容器中。</span><span class="sxs-lookup"><span data-stu-id="bbffd-121">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="bbffd-122">该密钥将用于加密 AES 会话密钥，并且稍后可检索该密钥以便对其进行解密。</span><span class="sxs-lookup"><span data-stu-id="bbffd-122">This key will be used to encrypt the AES session key and can be retrieved later to decrypt it.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="bbffd-123">通过从磁盘加载 XML 文件来创建 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="bbffd-123">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="bbffd-124"><xref:System.Xml.XmlDocument> 对象包含要加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-124">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#4)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#4)]  
  
4. <span data-ttu-id="bbffd-125">在 <xref:System.Xml.XmlDocument> 对象中查找指定元素，并创建一个新的 <xref:System.Xml.XmlElement> 对象来表示想要加密的元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-125">Find the specified element in the <xref:System.Xml.XmlDocument> object and create a new <xref:System.Xml.XmlElement> object to represent the element you want to encrypt.</span></span> <span data-ttu-id="bbffd-126">在此示例中，加密了 `"creditcard"` 元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-126">In this example, the `"creditcard"` element is encrypted.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
5. <span data-ttu-id="bbffd-127">使用 <xref:System.Security.Cryptography.RijndaelManaged> 类创建新的会话密钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-127">Create a new session key using the <xref:System.Security.Cryptography.RijndaelManaged> class.</span></span>  <span data-ttu-id="bbffd-128">此密钥将加密 XML 元素，然后其自身将被加密并被放置在 XML 文档中。</span><span class="sxs-lookup"><span data-stu-id="bbffd-128">This key will encrypt the XML element, and then be encrypted itself and placed in the XML document.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
6. <span data-ttu-id="bbffd-129">创建 <xref:System.Security.Cryptography.Xml.EncryptedXml> 类的新实例，并通过它使用会话密钥对指定元素进行加密。</span><span class="sxs-lookup"><span data-stu-id="bbffd-129">Create a new instance of the <xref:System.Security.Cryptography.Xml.EncryptedXml> class and use it to encrypt the specified element using the session key.</span></span>  <span data-ttu-id="bbffd-130"><xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> 方法以加密的字节数组的形式返回加密元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-130">The <xref:System.Security.Cryptography.Xml.EncryptedXml.EncryptData%2A> method returns the encrypted element as an array of encrypted bytes.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
7. <span data-ttu-id="bbffd-131">构造一个 <xref:System.Security.Cryptography.Xml.EncryptedData> 对象并对其填充加密 XML 元素的 URL 标识符。</span><span class="sxs-lookup"><span data-stu-id="bbffd-131">Construct an <xref:System.Security.Cryptography.Xml.EncryptedData> object and populate it with the URL identifier of the encrypted XML element.</span></span>  <span data-ttu-id="bbffd-132">此 URL 标识符可使解密方知道 XML 包含一个加密元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-132">This URL identifier lets a decrypting party know that the XML contains an encrypted element.</span></span>  <span data-ttu-id="bbffd-133">可使用 <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> 字段来指定 URL 标识符。</span><span class="sxs-lookup"><span data-stu-id="bbffd-133">You can use the <xref:System.Security.Cryptography.Xml.EncryptedXml.XmlEncElementUrl> field to specify the URL identifier.</span></span>  <span data-ttu-id="bbffd-134">纯文本 XML 元素将被 `EncryptedData` 此对象封装的 <> 元素替换 <xref:System.Security.Cryptography.Xml.EncryptedData> 。</span><span class="sxs-lookup"><span data-stu-id="bbffd-134">The plaintext XML element will be replaced by an <`EncryptedData`> element encapsulated by this <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
8. <span data-ttu-id="bbffd-135">创建一个 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 对象，将它初始化为用于生成会话密钥的加密算法的 URL 标识符。</span><span class="sxs-lookup"><span data-stu-id="bbffd-135">Create an <xref:System.Security.Cryptography.Xml.EncryptionMethod> object that is initialized to the URL identifier of the cryptographic algorithm used to generate the session key.</span></span>  <span data-ttu-id="bbffd-136">将 <xref:System.Security.Cryptography.Xml.EncryptionMethod> 对象传递给 <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="bbffd-136">Pass the <xref:System.Security.Cryptography.Xml.EncryptionMethod> object to the <xref:System.Security.Cryptography.Xml.EncryptedType.EncryptionMethod%2A> property.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#9)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#9)]  
  
9. <span data-ttu-id="bbffd-137">创建一个 <xref:System.Security.Cryptography.Xml.EncryptedKey> 对象，以便包含加密的会话密钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-137">Create an <xref:System.Security.Cryptography.Xml.EncryptedKey> object to contain the encrypted session key.</span></span>  <span data-ttu-id="bbffd-138">加密会话密钥，将其添加到 <xref:System.Security.Cryptography.Xml.EncryptedKey> 对象，并输入会话密钥名称和密钥标识符 URL。</span><span class="sxs-lookup"><span data-stu-id="bbffd-138">Encrypt the session key, add it to the <xref:System.Security.Cryptography.Xml.EncryptedKey> object, and enter a session key name and key identifier URL.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#10)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#10)]  
  
10. <span data-ttu-id="bbffd-139">创建新的 <xref:System.Security.Cryptography.Xml.DataReference> 对象，它将加密数据映射到特定的会话密钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-139">Create a new <xref:System.Security.Cryptography.Xml.DataReference> object that maps the encrypted data to a particular session key.</span></span>  <span data-ttu-id="bbffd-140">此可选步骤使你能够轻松地指定 XML 文档的多个部件由单个密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="bbffd-140">This optional step allows you to easily specify that multiple parts of an XML document were encrypted by a single key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#11)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#11)]  
  
11. <span data-ttu-id="bbffd-141">将加密的密钥添加到 <xref:System.Security.Cryptography.Xml.EncryptedData> 对象。</span><span class="sxs-lookup"><span data-stu-id="bbffd-141">Add the encrypted key to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#12)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#12)]  
  
12. <span data-ttu-id="bbffd-142">创建新的 <xref:System.Security.Cryptography.Xml.KeyInfo> 对象以指定 RSA 密钥的名称。</span><span class="sxs-lookup"><span data-stu-id="bbffd-142">Create a new <xref:System.Security.Cryptography.Xml.KeyInfo> object to specify the name of the RSA key.</span></span>  <span data-ttu-id="bbffd-143">将其添加到 <xref:System.Security.Cryptography.Xml.EncryptedData> 对象。</span><span class="sxs-lookup"><span data-stu-id="bbffd-143">Add it to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span> <span data-ttu-id="bbffd-144">这有助于解密方确定解密会话密钥时要使用的正确的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-144">This helps the decrypting party identify the correct asymmetric key to use when decrypting the session key.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#13)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#13)]  
  
13. <span data-ttu-id="bbffd-145">将加密的元素数据添加到 <xref:System.Security.Cryptography.Xml.EncryptedData> 对象。</span><span class="sxs-lookup"><span data-stu-id="bbffd-145">Add the encrypted element data to the <xref:System.Security.Cryptography.Xml.EncryptedData> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#14)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#14)]  
  
14. <span data-ttu-id="bbffd-146">将原始 <xref:System.Xml.XmlDocument> 对象中的元素替换为 <xref:System.Security.Cryptography.Xml.EncryptedData> 元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-146">Replace the element from the original <xref:System.Xml.XmlDocument> object with the <xref:System.Security.Cryptography.Xml.EncryptedData> element.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#15)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#15)]  
  
15. <span data-ttu-id="bbffd-147">保存 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="bbffd-147">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#16)]
     [!code-vb[HowToEncryptXMLElementAsymmetric#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="bbffd-148">示例</span><span class="sxs-lookup"><span data-stu-id="bbffd-148">Example</span></span>  
 <span data-ttu-id="bbffd-149">此示例假定名为 `"test.xml"` 的文件与已编译程序存在于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="bbffd-149">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="bbffd-150">它还假定 `"test.xml"` 包含 `"creditcard"` 元素。</span><span class="sxs-lookup"><span data-stu-id="bbffd-150">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="bbffd-151">可以将以下 XML 放在名为 `test.xml` 的文件，并将其用于以下示例。</span><span class="sxs-lookup"><span data-stu-id="bbffd-151">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/cs/sample.cs#1)]
 [!code-vb[HowToEncryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEncryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbffd-152">编译代码</span><span class="sxs-lookup"><span data-stu-id="bbffd-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="bbffd-153">若要编译此示例，需要包含对 `System.Security.dll` 的引用。</span><span class="sxs-lookup"><span data-stu-id="bbffd-153">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="bbffd-154">包括以下命名空间：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="bbffd-154">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bbffd-155">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="bbffd-155">.NET Framework Security</span></span>  
 <span data-ttu-id="bbffd-156">永远不要以纯文本形式存储对称加密密钥，也不要以纯文本形式在计算机之间传输对称密钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-156">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="bbffd-157">此外，绝不存储或传输纯文本形式的非对称密钥的私钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-157">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="bbffd-158">有关对称和非对称加密密钥的详细信息，请参阅[生成加密和解密密钥](generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="bbffd-158">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="bbffd-159">绝不将密钥直接嵌入源代码。</span><span class="sxs-lookup"><span data-stu-id="bbffd-159">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="bbffd-160">使用[Ildasm （IL 拆装器）](../../framework/tools/ildasm-exe-il-disassembler.md)或在文本编辑器（例如记事本）中打开程序集，可以轻松地从程序集中读取嵌入的密钥。</span><span class="sxs-lookup"><span data-stu-id="bbffd-160">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="bbffd-161">当你使用加密密钥执行操作后，通过将每个字节设置为零或通过调用托管加密类的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> 方法来将它从内存中清除。</span><span class="sxs-lookup"><span data-stu-id="bbffd-161">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="bbffd-162">加密密钥有时可从内存由调试器读取，或从硬盘读取（如果内存位置分页到磁盘）。</span><span class="sxs-lookup"><span data-stu-id="bbffd-162">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbffd-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbffd-163">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="bbffd-164">如何：用非对称密钥对 XML 元素进行解密</span><span class="sxs-lookup"><span data-stu-id="bbffd-164">How to: Decrypt XML Elements with Asymmetric Keys</span></span>](how-to-decrypt-xml-elements-with-asymmetric-keys.md)
