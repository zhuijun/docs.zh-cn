---
title: 如何：使用数字签名为 XML 文档签名
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: 81fa5e4c503f26dc13758090f845fd8387287084
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277175"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="e1d24-102">如何：使用数字签名为 XML 文档签名</span><span class="sxs-lookup"><span data-stu-id="e1d24-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="e1d24-103">可以使用 <xref:System.Security.Cryptography.Xml> 命名空间中的类通过数字签名对 XML 文档或部分 XML 文档进行签名。</span><span class="sxs-lookup"><span data-stu-id="e1d24-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="e1d24-104">使用 XML 数字签名 (XMLDSIG)，你可以验证签名后的数据没有被更改。</span><span class="sxs-lookup"><span data-stu-id="e1d24-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="e1d24-105">有关 XMLDSIG 标准的详细信息，请参阅万维网联合会（W3C）建议[XML 签名语法和处理](https://www.w3.org/TR/xmldsig-core/)。</span><span class="sxs-lookup"><span data-stu-id="e1d24-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="e1d24-106">此过程中的代码示例演示了如何对整个 XML 文档进行数字签名，以及如何将签名附加到 <> 元素中的文档 `Signature` 。</span><span class="sxs-lookup"><span data-stu-id="e1d24-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="e1d24-107">该示例创建一个 RSA 签名密钥，并将该密钥添加到安全密钥容器，然后使用该密钥对 XML 文档进行数字签名。</span><span class="sxs-lookup"><span data-stu-id="e1d24-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="e1d24-108">然后可以检索该密码来验证 XML 数字签名，或使用它对另一个 XML 文档进行签名。</span><span class="sxs-lookup"><span data-stu-id="e1d24-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="e1d24-109">有关如何验证使用此过程创建的 XML 数字签名的信息，请参阅[如何：验证 Xml 文档的数字签名](how-to-verify-the-digital-signatures-of-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="e1d24-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="e1d24-110">对 XML 文档进行数字签名</span><span class="sxs-lookup"><span data-stu-id="e1d24-110">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="e1d24-111">创建 <xref:System.Security.Cryptography.CspParameters> 对象，并指定密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="e1d24-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="e1d24-112">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类生成一个非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="e1d24-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="e1d24-113">当将 <xref:System.Security.Cryptography.CspParameters> 对象传递 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类的构造函数时，密钥将自动保存在密钥容器中。</span><span class="sxs-lookup"><span data-stu-id="e1d24-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="e1d24-114">此密钥将用于对 XML 文档签名。</span><span class="sxs-lookup"><span data-stu-id="e1d24-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="e1d24-115">通过从磁盘加载 XML 文件来创建 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="e1d24-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="e1d24-116"><xref:System.Xml.XmlDocument> 对象包含要加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="e1d24-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="e1d24-117">创建一个新的 <xref:System.Security.Cryptography.Xml.SignedXml> 对象，并向其传递 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="e1d24-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="e1d24-118">将签名 RSA 密钥添加到 <xref:System.Security.Cryptography.Xml.SignedXml> 对象。</span><span class="sxs-lookup"><span data-stu-id="e1d24-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="e1d24-119">创建说明签名内容的 <xref:System.Security.Cryptography.Xml.Reference> 对象。</span><span class="sxs-lookup"><span data-stu-id="e1d24-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="e1d24-120">若要对整个文档进行签名，请将 <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> 属性设置为 `""`。</span><span class="sxs-lookup"><span data-stu-id="e1d24-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="e1d24-121">将 <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> 对象添加到 <xref:System.Security.Cryptography.Xml.Reference> 对象中。</span><span class="sxs-lookup"><span data-stu-id="e1d24-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="e1d24-122">变换使验证程序可以使用与签名工具所用的相同方式表示 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="e1d24-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="e1d24-123">可以采用不同的方式表示 XML 数据，因此这一步对于验证至关重要。</span><span class="sxs-lookup"><span data-stu-id="e1d24-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="e1d24-124">将 <xref:System.Security.Cryptography.Xml.Reference> 对象添加到 <xref:System.Security.Cryptography.Xml.SignedXml> 对象中。</span><span class="sxs-lookup"><span data-stu-id="e1d24-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="e1d24-125">通过调用 <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> 方法计算签名。</span><span class="sxs-lookup"><span data-stu-id="e1d24-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="e1d24-126">检索签名（<> 元素）的 XML 表示形式 `Signature` ，并将其保存到新的 <xref:System.Xml.XmlElement> 对象。</span><span class="sxs-lookup"><span data-stu-id="e1d24-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="e1d24-127">将元素追加到 <xref:System.Xml.XmlDocument> 对象中。</span><span class="sxs-lookup"><span data-stu-id="e1d24-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="e1d24-128">保存文档。</span><span class="sxs-lookup"><span data-stu-id="e1d24-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="e1d24-129">示例</span><span class="sxs-lookup"><span data-stu-id="e1d24-129">Example</span></span>  
 <span data-ttu-id="e1d24-130">此示例假定名为 `test.xml` 的文件与已编译程序存在于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="e1d24-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="e1d24-131">可以将以下 XML 放在名为 `test.xml` 的文件，并将其用于以下示例。</span><span class="sxs-lookup"><span data-stu-id="e1d24-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1d24-132">编译代码</span><span class="sxs-lookup"><span data-stu-id="e1d24-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="e1d24-133">若要编译此示例，需要包含对 `System.Security.dll` 的引用。</span><span class="sxs-lookup"><span data-stu-id="e1d24-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="e1d24-134">包括以下命名空间：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="e1d24-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e1d24-135">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="e1d24-135">.NET Framework Security</span></span>  
 <span data-ttu-id="e1d24-136">切勿用纯文本存储或传输非对称密钥对的私钥。</span><span class="sxs-lookup"><span data-stu-id="e1d24-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="e1d24-137">有关对称和非对称加密密钥的详细信息，请参阅[生成加密和解密密钥](generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="e1d24-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="e1d24-138">切勿将私钥直接嵌入到源代码中。</span><span class="sxs-lookup"><span data-stu-id="e1d24-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="e1d24-139">使用[Ildasm （IL 拆装器）](../../framework/tools/ildasm-exe-il-disassembler.md)或在文本编辑器（例如记事本）中打开程序集，可以轻松地从程序集中读取嵌入的密钥。</span><span class="sxs-lookup"><span data-stu-id="e1d24-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d24-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e1d24-140">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="e1d24-141">如何：验证 XML 文档的数字签名</span><span class="sxs-lookup"><span data-stu-id="e1d24-141">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
