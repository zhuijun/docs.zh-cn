---
ms.openlocfilehash: fdec6671cbf2dae0d72dfaec07f162058b38cf9d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619909"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a><span data-ttu-id="4ce83-101">XmlTextReader DTD 实体扩展限制为 10,000,000 个字符</span><span class="sxs-lookup"><span data-stu-id="4ce83-101">XmlTextReader DTD entity expansion is limited to 10,000,000 characters</span></span>

#### <a name="details"></a><span data-ttu-id="4ce83-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4ce83-102">Details</span></span>

<span data-ttu-id="4ce83-103">DTD 实体扩展现在限制为 10,000,000 个字符。</span><span class="sxs-lookup"><span data-stu-id="4ce83-103">DTD entity expansion is now limited to 10,000,000 characters.</span></span> <span data-ttu-id="4ce83-104">加载不带 DTD 实体扩展或带有限的 DTD 实体扩展的 XML 文件不受影响。</span><span class="sxs-lookup"><span data-stu-id="4ce83-104">Loading XML files without DTD entity expansion or with limited DTD entity expansion is unaffected.</span></span> <span data-ttu-id="4ce83-105">包含了扩展到 10,000,000 个字符以上的 DTD 实体的文件将无法加载，且会立即引发异常。</span><span class="sxs-lookup"><span data-stu-id="4ce83-105">Files with DTD entities that expand to more than 10,000,000 characters fail to load, and now throw an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4ce83-106">建议</span><span class="sxs-lookup"><span data-stu-id="4ce83-106">Suggestion</span></span>

<span data-ttu-id="4ce83-107">如果 DTD 实体扩展的限制低于 10,000,000，该值可使用 <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> 属性重写。</span><span class="sxs-lookup"><span data-stu-id="4ce83-107">If the limit of DTD entity expansion is too low 10,000,000, the value can be overridden with the <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities> property.</span></span> <span data-ttu-id="4ce83-108">可以将具有适当 <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> 值的 <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> 传递给采用 <xref:System.Xml.XmlReaderSettings?displayProperty=fullName>（例如 <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>）的 <code>XmlReader.Create</code></span><span class="sxs-lookup"><span data-stu-id="4ce83-108">An <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> with the proper <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName> value can be passed to <code>XmlReader.Create</code> that takes <xref:System.Xml.XmlReaderSettings?displayProperty=fullName> (ie. <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)</span></span>

| <span data-ttu-id="4ce83-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="4ce83-109">Name</span></span>    | <span data-ttu-id="4ce83-110">“值”</span><span class="sxs-lookup"><span data-stu-id="4ce83-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4ce83-111">范围</span><span class="sxs-lookup"><span data-stu-id="4ce83-111">Scope</span></span>   |<span data-ttu-id="4ce83-112">边缘</span><span class="sxs-lookup"><span data-stu-id="4ce83-112">Edge</span></span>|
|<span data-ttu-id="4ce83-113">Version</span><span class="sxs-lookup"><span data-stu-id="4ce83-113">Version</span></span>|<span data-ttu-id="4ce83-114">4.5</span><span class="sxs-lookup"><span data-stu-id="4ce83-114">4.5</span></span>|
|<span data-ttu-id="4ce83-115">类型</span><span class="sxs-lookup"><span data-stu-id="4ce83-115">Type</span></span>|<span data-ttu-id="4ce83-116">运行时</span><span class="sxs-lookup"><span data-stu-id="4ce83-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4ce83-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="4ce83-117">Affected APIs</span></span>

-<xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)></li></ul>|
