---
title: 如何：使用数字签名为 XML 文档签名
description: 了解如何用数字签名对 XML 文档进行签名。 使用 .NET 中的 System.Security.Cryptography.Xml 命名空间中的类。
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSA class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: e1457fd659ab63489bd4cfafd7731a4b098a2791
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557068"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="ee166-104">如何：使用数字签名为 XML 文档签名</span><span class="sxs-lookup"><span data-stu-id="ee166-104">How to: Sign XML Documents with Digital Signatures</span></span>

<span data-ttu-id="ee166-105">可以使用 <xref:System.Security.Cryptography.Xml> 命名空间中的类通过数字签名对 XML 文档或部分 XML 文档进行签名。</span><span class="sxs-lookup"><span data-stu-id="ee166-105">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="ee166-106">使用 XML 数字签名 (XMLDSIG)，你可以验证签名后的数据没有被更改。</span><span class="sxs-lookup"><span data-stu-id="ee166-106">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="ee166-107">有关 XMLDSIG 标准的详细信息，请参阅万维网联合会 (W3C) 推荐[XML 签名语法和处理](https://www.w3.org/TR/xmldsig-core/)。</span><span class="sxs-lookup"><span data-stu-id="ee166-107">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee166-108">本文中的代码适用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="ee166-108">The code in this article applies to Windows.</span></span>

<span data-ttu-id="ee166-109">此过程中的代码示例演示了如何对整个 XML 文档进行数字签名，以及如何将签名附加到 <> 元素中的文档 `Signature` 。</span><span class="sxs-lookup"><span data-stu-id="ee166-109">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="ee166-110">该示例创建一个 RSA 签名密钥，并将该密钥添加到安全密钥容器，然后使用该密钥对 XML 文档进行数字签名。</span><span class="sxs-lookup"><span data-stu-id="ee166-110">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="ee166-111">然后可以检索该密码来验证 XML 数字签名，或使用它对另一个 XML 文档进行签名。</span><span class="sxs-lookup"><span data-stu-id="ee166-111">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
<span data-ttu-id="ee166-112">有关如何验证使用此过程创建的 XML 数字签名的信息，请参阅[如何：验证 Xml 文档的数字签名](how-to-verify-the-digital-signatures-of-xml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="ee166-112">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="ee166-113">对 XML 文档进行数字签名</span><span class="sxs-lookup"><span data-stu-id="ee166-113">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="ee166-114">创建 <xref:System.Security.Cryptography.CspParameters> 对象，并指定密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="ee166-114">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="ee166-115">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类生成一个非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="ee166-115">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="ee166-116">当将 <xref:System.Security.Cryptography.CspParameters> 对象传递 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 类的构造函数时，密钥将自动保存在密钥容器中。</span><span class="sxs-lookup"><span data-stu-id="ee166-116">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="ee166-117">此密钥将用于对 XML 文档签名。</span><span class="sxs-lookup"><span data-stu-id="ee166-117">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="ee166-118">通过从磁盘加载 XML 文件来创建 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="ee166-118">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="ee166-119"><xref:System.Xml.XmlDocument> 对象包含要加密的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="ee166-119">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="ee166-120">创建一个新的 <xref:System.Security.Cryptography.Xml.SignedXml> 对象，并向其传递 <xref:System.Xml.XmlDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="ee166-120">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="ee166-121">将签名 RSA 密钥添加到 <xref:System.Security.Cryptography.Xml.SignedXml> 对象。</span><span class="sxs-lookup"><span data-stu-id="ee166-121">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="ee166-122">创建说明签名内容的 <xref:System.Security.Cryptography.Xml.Reference> 对象。</span><span class="sxs-lookup"><span data-stu-id="ee166-122">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="ee166-123">若要对整个文档进行签名，请将 <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> 属性设置为 `""`。</span><span class="sxs-lookup"><span data-stu-id="ee166-123">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="ee166-124">将 <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> 对象添加到 <xref:System.Security.Cryptography.Xml.Reference> 对象中。</span><span class="sxs-lookup"><span data-stu-id="ee166-124">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="ee166-125">变换使验证程序可以使用与签名工具所用的相同方式表示 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="ee166-125">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="ee166-126">可以采用不同的方式表示 XML 数据，因此这一步对于验证至关重要。</span><span class="sxs-lookup"><span data-stu-id="ee166-126">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="ee166-127">将 <xref:System.Security.Cryptography.Xml.Reference> 对象添加到 <xref:System.Security.Cryptography.Xml.SignedXml> 对象中。</span><span class="sxs-lookup"><span data-stu-id="ee166-127">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="ee166-128">通过调用 <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> 方法计算签名。</span><span class="sxs-lookup"><span data-stu-id="ee166-128">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="ee166-129">检索 (<>) 元素的签名的 XML 表示形式 `Signature` ，并将其保存到新的 <xref:System.Xml.XmlElement> 对象。</span><span class="sxs-lookup"><span data-stu-id="ee166-129">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="ee166-130">将元素追加到 <xref:System.Xml.XmlDocument> 对象中。</span><span class="sxs-lookup"><span data-stu-id="ee166-130">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="ee166-131">保存文档。</span><span class="sxs-lookup"><span data-stu-id="ee166-131">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="ee166-132">示例</span><span class="sxs-lookup"><span data-stu-id="ee166-132">Example</span></span>  
 <span data-ttu-id="ee166-133">此示例假定名为 `test.xml` 的文件与已编译程序存在于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="ee166-133">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="ee166-134">可以将以下 XML 放在名为 `test.xml` 的文件，并将其用于以下示例。</span><span class="sxs-lookup"><span data-stu-id="ee166-134">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ee166-135">编译代码</span><span class="sxs-lookup"><span data-stu-id="ee166-135">Compiling the Code</span></span>  
  
- <span data-ttu-id="ee166-136">在面向 .NET Framework 的项目中，包含对的引用 `System.Security.dll` 。</span><span class="sxs-lookup"><span data-stu-id="ee166-136">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="ee166-137">在面向 .NET Core 或 .NET 5 的项目中，安装 NuGet 包[System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)。</span><span class="sxs-lookup"><span data-stu-id="ee166-137">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="ee166-138">包括以下命名空间：<xref:System.Xml>、<xref:System.Security.Cryptography> 和 <xref:System.Security.Cryptography.Xml>。</span><span class="sxs-lookup"><span data-stu-id="ee166-138">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="ee166-139">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="ee166-139">.NET Security</span></span>

<span data-ttu-id="ee166-140">切勿用纯文本存储或传输非对称密钥对的私钥。</span><span class="sxs-lookup"><span data-stu-id="ee166-140">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="ee166-141">有关对称和非对称加密密钥的详细信息，请参阅[生成加密和解密密钥](generating-keys-for-encryption-and-decryption.md)。</span><span class="sxs-lookup"><span data-stu-id="ee166-141">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="ee166-142">切勿将私钥直接嵌入到源代码中。</span><span class="sxs-lookup"><span data-stu-id="ee166-142">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="ee166-143">[Ildasm.exe 使用 (IL 拆装器) ](../../framework/tools/ildasm-exe-il-disassembler.md)或通过在文本编辑器（例如记事本）中打开程序集，可以轻松地从程序集中读取嵌入的密钥。</span><span class="sxs-lookup"><span data-stu-id="ee166-143">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee166-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="ee166-144">See also</span></span>

- [<span data-ttu-id="ee166-145">加密模型</span><span class="sxs-lookup"><span data-stu-id="ee166-145">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="ee166-146">加密服务</span><span class="sxs-lookup"><span data-stu-id="ee166-146">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="ee166-147">跨平台加密</span><span class="sxs-lookup"><span data-stu-id="ee166-147">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="ee166-148">如何：验证 XML 文档的数字签名</span><span class="sxs-lookup"><span data-stu-id="ee166-148">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
- [<span data-ttu-id="ee166-149">ASP.NET Core 数据保护</span><span class="sxs-lookup"><span data-stu-id="ee166-149">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
