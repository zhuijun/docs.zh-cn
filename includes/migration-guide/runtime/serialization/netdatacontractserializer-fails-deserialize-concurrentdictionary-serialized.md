---
ms.openlocfilehash: eef5633ec8566f6d5216b7dca4387766cacb600d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619865"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a><span data-ttu-id="70e21-101">NetDataContractSerializer 无法反序列化使用其他 .NET 版本序列化的 ConcurrentDictionary</span><span class="sxs-lookup"><span data-stu-id="70e21-101">NetDataContractSerializer fails to deserialize a ConcurrentDictionary serialized with a different .NET version</span></span>

#### <a name="details"></a><span data-ttu-id="70e21-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="70e21-102">Details</span></span>

<span data-ttu-id="70e21-103">根据设计，只有在序列化和反序列化端共享相同的 CLR 类型时，才能使用 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="70e21-103">By design, the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="70e21-104">因此，无法保证使用某个版本的 .NET Framework 序列化的对象可以由其他版本反序列化。<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="70e21-104">Therefore, it is not guaranteed that an object serialized with one version of the .NET Framework can be deserialized by a different version.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span></span> <span data-ttu-id="70e21-105">是一种类型，已知该类型如果使用 .NET Framework 4.5 或更早版本序列化并使用 .NET Framework 4.5.1 或更早版本反序列化，则无法正确反序列化。</span><span class="sxs-lookup"><span data-stu-id="70e21-105">is a type that is known to not to deserialize correctly if serialized with the .NET Framework 4.5 or earlier and deserialized with the .NET Framework 4.5.1 or later.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="70e21-106">建议</span><span class="sxs-lookup"><span data-stu-id="70e21-106">Suggestion</span></span>

<span data-ttu-id="70e21-107">针对这个问题有很多可行的解决方法：</span><span class="sxs-lookup"><span data-stu-id="70e21-107">There are a number of possible work-arounds for this issue:</span></span><ul><li><span data-ttu-id="70e21-108">升级序列化计算机以使用 .NET Framework 4.5.1。</span><span class="sxs-lookup"><span data-stu-id="70e21-108">Upgrade the serializing computer to use the .NET Framework 4.5.1, as well.</span></span></li><li><span data-ttu-id="70e21-109">使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> 而不是 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>，因为这并不指望在序列化端和反序列化端具有完全相同的 CLR 类型。</span><span class="sxs-lookup"><span data-stu-id="70e21-109">Use <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> instead of <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> as this does not expect the exact same CLR types at both serializing and deserializing ends.</span></span></li><li><span data-ttu-id="70e21-110">使用 <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> 而不是 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>，因为它不会显示出特定的 4.5-&gt;4.5.1 中断。</span><span class="sxs-lookup"><span data-stu-id="70e21-110">Use <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> instead of <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> since it does not exhibit this particular 4.5-&gt;4.5.1 break.</span></span></li></ul>

| <span data-ttu-id="70e21-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="70e21-111">Name</span></span>    | <span data-ttu-id="70e21-112">“值”</span><span class="sxs-lookup"><span data-stu-id="70e21-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="70e21-113">范围</span><span class="sxs-lookup"><span data-stu-id="70e21-113">Scope</span></span>   |<span data-ttu-id="70e21-114">次要</span><span class="sxs-lookup"><span data-stu-id="70e21-114">Minor</span></span>|
|<span data-ttu-id="70e21-115">Version</span><span class="sxs-lookup"><span data-stu-id="70e21-115">Version</span></span>|<span data-ttu-id="70e21-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="70e21-116">4.5.1</span></span>|
|<span data-ttu-id="70e21-117">类型</span><span class="sxs-lookup"><span data-stu-id="70e21-117">Type</span></span>|<span data-ttu-id="70e21-118">运行时</span><span class="sxs-lookup"><span data-stu-id="70e21-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="70e21-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="70e21-119">Affected APIs</span></span>

-<xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|
