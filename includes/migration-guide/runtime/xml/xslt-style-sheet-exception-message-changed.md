---
ms.openlocfilehash: d33d75b4c2d9bc18844f66f1fcca1e2efc6f1eee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497869"
---
### <a name="xslt-style-sheet-exception-message-changed"></a><span data-ttu-id="22e6e-101">XSLT 样式表异常消息已更改</span><span class="sxs-lookup"><span data-stu-id="22e6e-101">XSLT style sheet exception message changed</span></span>

#### <a name="details"></a><span data-ttu-id="22e6e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="22e6e-102">Details</span></span>

<span data-ttu-id="22e6e-103">在 .NET Framework 4.5 中，XSLT 文件过于复杂时显示的错误消息的文本为“样式表太复杂”。在先前版本中，错误消息为“XSLT 编译错误”。取决于错误消息的文本的应用程序代码将不再有效。</span><span class="sxs-lookup"><span data-stu-id="22e6e-103">In the .NET Framework 4.5, the text of the error message when an XSLT file is too complex is &quot;The style sheet is too complex.&quot; In previous versions, the error message was &quot;XSLT compile error.&quot; Application code that depends on the text of the error message will no longer work.</span></span> <span data-ttu-id="22e6e-104">但是，异常类型保持不变，因此，此更改应该不会造成实际影响。</span><span class="sxs-lookup"><span data-stu-id="22e6e-104">However, the exception types remain the same, so this change should have no real impact.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="22e6e-105">建议</span><span class="sxs-lookup"><span data-stu-id="22e6e-105">Suggestion</span></span>

<span data-ttu-id="22e6e-106">根据此错误条件发出的异常消息更新任何应用代码，以收到新消息，或者（最好是）更新代码以仅依赖于未更改的异常类型 (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>)。</span><span class="sxs-lookup"><span data-stu-id="22e6e-106">Update any app code depending on the exception message from this error condition to expect the new message, or (even better) update the code to depend only on the exception type (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), which has not changed.</span></span>

| <span data-ttu-id="22e6e-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="22e6e-107">Name</span></span>    | <span data-ttu-id="22e6e-108">“值”</span><span class="sxs-lookup"><span data-stu-id="22e6e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="22e6e-109">范围</span><span class="sxs-lookup"><span data-stu-id="22e6e-109">Scope</span></span>   |<span data-ttu-id="22e6e-110">边缘</span><span class="sxs-lookup"><span data-stu-id="22e6e-110">Edge</span></span>|
|<span data-ttu-id="22e6e-111">Version</span><span class="sxs-lookup"><span data-stu-id="22e6e-111">Version</span></span>|<span data-ttu-id="22e6e-112">4.5</span><span class="sxs-lookup"><span data-stu-id="22e6e-112">4.5</span></span>|
|<span data-ttu-id="22e6e-113">类型</span><span class="sxs-lookup"><span data-stu-id="22e6e-113">Type</span></span>|<span data-ttu-id="22e6e-114">运行时</span><span class="sxs-lookup"><span data-stu-id="22e6e-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="22e6e-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="22e6e-115">Affected APIs</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`

-->
