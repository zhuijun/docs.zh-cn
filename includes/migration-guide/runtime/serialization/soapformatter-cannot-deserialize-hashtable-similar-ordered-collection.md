---
ms.openlocfilehash: 5a3370e71488e4f9d8d933b504d1d771c78e0385
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619864"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a><span data-ttu-id="829f4-101">SoapFormatter 无法反序列化哈希表和类似有序的集合对象</span><span class="sxs-lookup"><span data-stu-id="829f4-101">SoapFormatter cannot deserialize Hashtable and similar ordered collection objects</span></span>

#### <a name="details"></a><span data-ttu-id="829f4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="829f4-102">Details</span></span>

<span data-ttu-id="829f4-103"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> 不保证在一个 .NET Framework 版本下进行序列化的对象能够在其他版本下成功反序列化。</span><span class="sxs-lookup"><span data-stu-id="829f4-103">The <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> does not guarantee that objects serialized under one .NET Framework version will successfully deserialize under a different version.</span></span> <span data-ttu-id="829f4-104">具体而言，某些有序集合（例如 <xref:System.Collections.Hashtable?displayProperty=fullName>）已在 4.0 和 4.5 中添加了成员，如果这些类型的对象在 .NET Framework 4.5 中进行了序列化，它们在 .NET Framework 4.0 中将无法反序列化。</span><span class="sxs-lookup"><span data-stu-id="829f4-104">Specifically, some ordered collections (like <xref:System.Collections.Hashtable?displayProperty=fullName>) added members between 4.0 and 4.5 such that objects of these types cannot deserialize with .NET Framework 4.0 if they were serialized with .NET Framework 4.5.</span></span> <span data-ttu-id="829f4-105">请注意，如果序列化的数据在同一 .NET Framework 版本中进行序列化和反序列化，将不会发生任何问题。</span><span class="sxs-lookup"><span data-stu-id="829f4-105">Note that if the serialized data is both serialized and deserialized with the same .NET Framework version, no issue will occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="829f4-106">建议</span><span class="sxs-lookup"><span data-stu-id="829f4-106">Suggestion</span></span>

<span data-ttu-id="829f4-107">应使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> 序列化或 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> 替换 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> 序列化以适应 .NET Framework 的更改。</span><span class="sxs-lookup"><span data-stu-id="829f4-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> serialization should be replaced with <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serialization or <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> to be resilient to .NET Framework changes.</span></span>

| <span data-ttu-id="829f4-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="829f4-108">Name</span></span>    | <span data-ttu-id="829f4-109">“值”</span><span class="sxs-lookup"><span data-stu-id="829f4-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="829f4-110">范围</span><span class="sxs-lookup"><span data-stu-id="829f4-110">Scope</span></span>   |<span data-ttu-id="829f4-111">次要</span><span class="sxs-lookup"><span data-stu-id="829f4-111">Minor</span></span>|
|<span data-ttu-id="829f4-112">Version</span><span class="sxs-lookup"><span data-stu-id="829f4-112">Version</span></span>|<span data-ttu-id="829f4-113">4.5</span><span class="sxs-lookup"><span data-stu-id="829f4-113">4.5</span></span>|
|<span data-ttu-id="829f4-114">类型</span><span class="sxs-lookup"><span data-stu-id="829f4-114">Type</span></span>|<span data-ttu-id="829f4-115">运行时</span><span class="sxs-lookup"><span data-stu-id="829f4-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="829f4-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="829f4-116">Affected APIs</span></span>

-<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
