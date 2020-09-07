---
ms.openlocfilehash: 75c7385bceec2595683d1c0d97a7df9264e3bf0b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497035"
---
### <a name="xmlserializer-fails-while-serializing-a-type-that-hides-an-accessible-member-with-an-inaccessible-one"></a><span data-ttu-id="20230-101">当所序列化的类型使用不可访问成员来隐藏可访问的成员时，XmlSerializer 失败</span><span class="sxs-lookup"><span data-stu-id="20230-101">XmlSerializer fails while serializing a type that hides an accessible member with an inaccessible one</span></span>

#### <a name="details"></a><span data-ttu-id="20230-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="20230-102">Details</span></span>

<span data-ttu-id="20230-103">在序列化派生类型时，如果该类型包含不可访问的字段或属性，即（通过“new”关键字）隐藏之前基类型上可访问的同名字段或属性（例如，public），则 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 可能会失败。</span><span class="sxs-lookup"><span data-stu-id="20230-103">When serializing a derived type, the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> can fail if the type contains an inaccessible field or property that hides (via the 'new' keyword) a field or property of the same name that was previously accessible (public, for example) on the base type.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="20230-104">建议</span><span class="sxs-lookup"><span data-stu-id="20230-104">Suggestion</span></span>

<span data-ttu-id="20230-105">通过将新的隐藏成员设为可访问 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>（例如，将其标记为 public），可以解决此问题。或者，以下 config 设置将还原为 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 行为，也可解决此问题：</span><span class="sxs-lookup"><span data-stu-id="20230-105">This problem can be solved by making the new, hiding member accessible to the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> (by marking it public, for example).Alternatively, the following config setting will revert to 4.0 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> behavior, which will fix the problem:</span></span><pre><code class="lang-xml">&lt;system.xml.serialization&gt;&#13;&#10;&lt;xmlSerializer useLegacySerializerGeneration=&quot;true&quot; /&gt;&#13;&#10;&lt;/system.xml.serialization&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="20230-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="20230-106">Name</span></span>    | <span data-ttu-id="20230-107">“值”</span><span class="sxs-lookup"><span data-stu-id="20230-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="20230-108">范围</span><span class="sxs-lookup"><span data-stu-id="20230-108">Scope</span></span>   |<span data-ttu-id="20230-109">次要</span><span class="sxs-lookup"><span data-stu-id="20230-109">Minor</span></span>|
|<span data-ttu-id="20230-110">Version</span><span class="sxs-lookup"><span data-stu-id="20230-110">Version</span></span>|<span data-ttu-id="20230-111">4.5</span><span class="sxs-lookup"><span data-stu-id="20230-111">4.5</span></span>|
|<span data-ttu-id="20230-112">类型</span><span class="sxs-lookup"><span data-stu-id="20230-112">Type</span></span>|<span data-ttu-id="20230-113">运行时</span><span class="sxs-lookup"><span data-stu-id="20230-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="20230-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="20230-114">Affected APIs</span></span>

- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Object,System.Xml.Serialization.XmlSerializationWriter)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.Stream,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.IO.TextWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String)`
- `M:System.Xml.Serialization.XmlSerializer.Serialize(System.Xml.XmlWriter,System.Object,System.Xml.Serialization.XmlSerializerNamespaces,System.String,System.String)`

-->
