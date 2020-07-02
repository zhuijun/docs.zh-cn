---
ms.openlocfilehash: 8cc4f2ba2923774ef4e4e6861a89a7797ca988e1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621049"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="1a45d-101">SignedXml 和 EncryptedXml 的重大更改</span><span class="sxs-lookup"><span data-stu-id="1a45d-101">SignedXml and EncryptedXml Breaking Changes</span></span>

#### <a name="details"></a><span data-ttu-id="1a45d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1a45d-102">Details</span></span>

<span data-ttu-id="1a45d-103">在 .NET Framework 4.6.2 中，<xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> 和 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> 中的安全修复程序会导致不同的运行时行为。</span><span class="sxs-lookup"><span data-stu-id="1a45d-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> lead to different run-time behaviors.</span></span> <span data-ttu-id="1a45d-104">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="1a45d-104">For example,</span></span><ul><li><span data-ttu-id="1a45d-105">如果文档包含多个具有相同 <code>id</code> 特性的元素，并且签名将其中一个元素作为签名根的目标，则该文档现在将视为无效。</span><span class="sxs-lookup"><span data-stu-id="1a45d-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="1a45d-106">在引用中使用非规范 XPath 转换算法的文档现在视为无效。</span><span class="sxs-lookup"><span data-stu-id="1a45d-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="1a45d-107">在引用中使用非规范 XSLT 转换算法的文档现在视为无效。</span><span class="sxs-lookup"><span data-stu-id="1a45d-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="1a45d-108">任何利用外部资源拆离签名的程序都无法执行此操作。</span><span class="sxs-lookup"><span data-stu-id="1a45d-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="1a45d-109">建议</span><span class="sxs-lookup"><span data-stu-id="1a45d-109">Suggestion</span></span>

<span data-ttu-id="1a45d-110">开发者应该检查 <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> 和 <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> 以及派生自 <xref:System.Security.Cryptography.Xml.Transform> 的类型的使用情况，因为文档接收器可能无法进行处理。</span><span class="sxs-lookup"><span data-stu-id="1a45d-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>

| <span data-ttu-id="1a45d-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="1a45d-111">Name</span></span>    | <span data-ttu-id="1a45d-112">值</span><span class="sxs-lookup"><span data-stu-id="1a45d-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1a45d-113">范围</span><span class="sxs-lookup"><span data-stu-id="1a45d-113">Scope</span></span>   |<span data-ttu-id="1a45d-114">次要</span><span class="sxs-lookup"><span data-stu-id="1a45d-114">Minor</span></span>|
|<span data-ttu-id="1a45d-115">Version</span><span class="sxs-lookup"><span data-stu-id="1a45d-115">Version</span></span>|<span data-ttu-id="1a45d-116">4.6.2</span><span class="sxs-lookup"><span data-stu-id="1a45d-116">4.6.2</span></span>|
|<span data-ttu-id="1a45d-117">类型</span><span class="sxs-lookup"><span data-stu-id="1a45d-117">Type</span></span>|<span data-ttu-id="1a45d-118">运行时</span><span class="sxs-lookup"><span data-stu-id="1a45d-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1a45d-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1a45d-119">Affected APIs</span></span>

-<xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
