---
title: 如何：使用 X.509 证书解密 XML 元素
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- System.Security.Cryptography.X509Certificate2 class
- decryption
- X.509 certificates
- certificates, X.509 certificates
ms.assetid: bd015722-d88d-408d-8ca8-e4e475c441ed
ms.openlocfilehash: 32a6d95b96bb20571c14c16cc70b944fa3e4032b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277383"
---
# <a name="how-to-decrypt-xml-elements-with-x509-certificates"></a><span data-ttu-id="c926c-102">如何：使用 X.509 证书解密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="c926c-102">How to: Decrypt XML Elements with X.509 Certificates</span></span>
<span data-ttu-id="c926c-103">可以使用 <xref:System.Security.Cryptography.Xml> 命名空间中的类对 XML 文档内的元素进行加密和解密。</span><span class="sxs-lookup"><span data-stu-id="c926c-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="c926c-104">XML 加密是交换或存储加密的 XML 数据的一种标准方式，使用后就无需担心数据被轻易读取。</span><span class="sxs-lookup"><span data-stu-id="c926c-104">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="c926c-105">有关 XML 加密标准的详细信息，请参阅位于的 XML 加密的万维网联合会（W3C）规范 <https://www.w3.org/TR/xmldsig-core/> 。</span><span class="sxs-lookup"><span data-stu-id="c926c-105">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) specification for XML Encryption located at <https://www.w3.org/TR/xmldsig-core/>.</span></span>  
  
 <span data-ttu-id="c926c-106">此示例对使用中所述的方法进行加密的 XML 元素进行解密： how [to：使用 X.509 证书对 XML 元素进行加密](how-to-encrypt-xml-elements-with-x-509-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="c926c-106">This example decrypts an XML element that was encrypted using the methods described in: [How to: Encrypt XML Elements with X.509 Certificates](how-to-encrypt-xml-elements-with-x-509-certificates.md).</span></span>  <span data-ttu-id="c926c-107">它将查找 <`EncryptedData`> 元素，对元素进行解密，然后将元素替换为原始纯文本 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="c926c-107">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
 <span data-ttu-id="c926c-108">此过程中的代码示例将使用当前用户帐户的本地证书存储中的 X.509 证书来解密 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="c926c-108">The code example in this procedure decrypts an XML element using an X.509 certificate from the local certificate store of the current user account.</span></span>  <span data-ttu-id="c926c-109">该示例使用 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法自动检索 x.509 证书，并对存储在 `EncryptedKey` <> 元素的 <> 元素中的会话密钥进行解密 `EncryptedData` 。</span><span class="sxs-lookup"><span data-stu-id="c926c-109">The example uses the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to automatically retrieve the X.509 certificate and decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="c926c-110">然后，<xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法将自动使用会话密钥对 XML 元素进行解密。</span><span class="sxs-lookup"><span data-stu-id="c926c-110">The <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method then automatically uses the session key to decrypt the XML element.</span></span>  
  
 <span data-ttu-id="c926c-111">此示例适用于以下情况：多个应用程序需要共享加密数据，或应用程序需要保存它各次运行之间的加密数据。</span><span class="sxs-lookup"><span data-stu-id="c926c-111">This example is appropriate for situations where multiple applications need to share encrypted data or where an application needs to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-x509-certificate"></a><span data-ttu-id="c926c-112">用 X.509 证书解密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="c926c-112">To decrypt an XML element with an X.509 certificate</span></span>  
  
1. <span data-ttu-id="c926c-113">通过从磁盘加载 XML 文件来创建 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="c926c-113">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="c926c-114"><xref:System.Xml.XmlDocument> 对象包含要解密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="c926c-114">The <xref:System.Xml.XmlDocument> object contains the XML element to decrypt.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementX509#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#2)]  
  
2. <span data-ttu-id="c926c-115">通过将 <xref:System.Xml.XmlDocument> 对象传递给构造函数，创建一个新的 <xref:System.Security.Cryptography.Xml.EncryptedXml> 对象。</span><span class="sxs-lookup"><span data-stu-id="c926c-115">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object by passing the <xref:System.Xml.XmlDocument> object to the constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementX509#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#3)]  
  
3. <span data-ttu-id="c926c-116">使用 <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> 方法解密 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="c926c-116">Decrypt the XML document using the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#4)]
     [!code-vb[HowToDecryptXMLElementX509#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#4)]  
  
4. <span data-ttu-id="c926c-117">保存 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="c926c-117">Save the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementX509#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementX509#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="c926c-118">示例</span><span class="sxs-lookup"><span data-stu-id="c926c-118">Example</span></span>  
 <span data-ttu-id="c926c-119">此示例假定名为 `"test.xml"` 的文件与已编译程序存在于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="c926c-119">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="c926c-120">它还假定 `"test.xml"` 包含 `"creditcard"` 元素。</span><span class="sxs-lookup"><span data-stu-id="c926c-120">It also assumes that `"test.xml"` contains a `"creditcard"` element.</span></span>  <span data-ttu-id="c926c-121">可以将以下 XML 放在名为 `test.xml` 的文件，并将其用于以下示例。</span><span class="sxs-lookup"><span data-stu-id="c926c-121">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToDecryptXMLElementX509#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementX509/cs/sample.cs#1)]
 [!code-vb[HowToDecryptXMLElementX509#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementX509/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c926c-122">编译代码</span><span class="sxs-lookup"><span data-stu-id="c926c-122">Compiling the Code</span></span>  
  
- <span data-ttu-id="c926c-123">若要编译此示例，需要包含对 `System.Security.dll` 的引用。</span><span class="sxs-lookup"><span data-stu-id="c926c-123">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="c926c-124">包括以下命名空间：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="c926c-124">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c926c-125">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="c926c-125">.NET Framework Security</span></span>  
 <span data-ttu-id="c926c-126">此示例中使用的 X.509 证书仅用于测试目的。</span><span class="sxs-lookup"><span data-stu-id="c926c-126">The X.509 certificate used in this example is for test purposes only.</span></span>  <span data-ttu-id="c926c-127">应用程序应使用由受信任的证书颁发机构生成的 X.509 证书，或使用由 Microsoft Windows 证书服务器生成的证书。</span><span class="sxs-lookup"><span data-stu-id="c926c-127">Applications should use an X.509 certificate generated by a trusted certificate authority or use a certificate generated by the Microsoft Windows Certificate Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c926c-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c926c-128">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="c926c-129">如何：使用 X.509 证书加密 XML 元素</span><span class="sxs-lookup"><span data-stu-id="c926c-129">How to: Encrypt XML Elements with X.509 Certificates</span></span>](how-to-encrypt-xml-elements-with-x-509-certificates.md)
