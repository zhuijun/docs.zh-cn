---
ms.openlocfilehash: ccba3cf98a1ca9e199d9a48f00e254bf34b93f72
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497612"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a><span data-ttu-id="3413c-101">BinaryFormatter 可能无法从 LoadFrom 上下文找到类型</span><span class="sxs-lookup"><span data-stu-id="3413c-101">BinaryFormatter can fail to find type from LoadFrom context</span></span>

#### <a name="details"></a><span data-ttu-id="3413c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3413c-102">Details</span></span>

<span data-ttu-id="3413c-103">自 .NET Framework 4.5 起，大量 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 更改可能在使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> 反序列化 LoadFrom 上下文中负载的类型时导致反序列化出现差异。</span><span class="sxs-lookup"><span data-stu-id="3413c-103">As of .NET Framework 4.5, a number of <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> changes may cause differences in deserialization when using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> to deserialize types that had been loaded in the LoadFrom context.</span></span> <span data-ttu-id="3413c-104">这些更改由新的方式引起，<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 现在加载了一种类型，可以在 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> 稍后尝试反序列化为该类型时，导致其他行为。</span><span class="sxs-lookup"><span data-stu-id="3413c-104">These changes are due to the new ways <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> now loads a type which causes different behavior when a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> attempts to deserialize to that type later on.</span></span> <span data-ttu-id="3413c-105">默认序列化活页夹虽然在某些情况下可以基于 XmlSerializer 旧行为工作，但它不会自动搜索 LoadFrom 上下文。</span><span class="sxs-lookup"><span data-stu-id="3413c-105">The default serialization binder does not automatically search the LoadFrom context, although it may have worked in some circumstances based on the old behavior of XmlSerializer.</span></span> <span data-ttu-id="3413c-106">由于这些更改，当从其他上下文加载的程序集加载类型时，可能引发 <xref:System.IO.FileNotFoundException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="3413c-106">Due to the changes, when a type is being loaded from an assembly loaded in a different context, a <xref:System.IO.FileNotFoundException?displayProperty=fullName> may be thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3413c-107">建议</span><span class="sxs-lookup"><span data-stu-id="3413c-107">Suggestion</span></span>

<span data-ttu-id="3413c-108">如果显示此异常，则 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> 的 <code>Binder</code> 属性可以设为将查找正确类型的自定义活页夹。</span><span class="sxs-lookup"><span data-stu-id="3413c-108">If this exception is seen, the <code>Binder</code> property of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> can be set to a custom binder that will find the correct type.</span></span><pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre><span data-ttu-id="3413c-109">然后自定义活页夹：</span><span class="sxs-lookup"><span data-stu-id="3413c-109">And then the custom binder:</span></span><pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="3413c-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="3413c-110">Name</span></span>    | <span data-ttu-id="3413c-111">“值”</span><span class="sxs-lookup"><span data-stu-id="3413c-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3413c-112">范围</span><span class="sxs-lookup"><span data-stu-id="3413c-112">Scope</span></span>   |<span data-ttu-id="3413c-113">边缘</span><span class="sxs-lookup"><span data-stu-id="3413c-113">Edge</span></span>|
|<span data-ttu-id="3413c-114">Version</span><span class="sxs-lookup"><span data-stu-id="3413c-114">Version</span></span>|<span data-ttu-id="3413c-115">4.5</span><span class="sxs-lookup"><span data-stu-id="3413c-115">4.5</span></span>|
|<span data-ttu-id="3413c-116">类型</span><span class="sxs-lookup"><span data-stu-id="3413c-116">Type</span></span>|<span data-ttu-id="3413c-117">运行时</span><span class="sxs-lookup"><span data-stu-id="3413c-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3413c-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3413c-118">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)`

-->
