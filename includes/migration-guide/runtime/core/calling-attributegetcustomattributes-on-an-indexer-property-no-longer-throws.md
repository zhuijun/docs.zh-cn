---
ms.openlocfilehash: f61e5670334f4d3674fd0b008d1a476b14c7ba4e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497402"
---
### <a name="calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a><span data-ttu-id="df31f-101">如果多义性可按索引类型进行解析，则在索引器属性上调用 Attribute.GetCustomAttributes 将不再引发 AmbiguousMatchException</span><span class="sxs-lookup"><span data-stu-id="df31f-101">Calling Attribute.GetCustomAttributes on an indexer property no longer throws AmbiguousMatchException if the ambiguity can be resolved by index's type</span></span>

#### <a name="details"></a><span data-ttu-id="df31f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="df31f-102">Details</span></span>

<span data-ttu-id="df31f-103">在 .NET Framework 4.6 之前的版本中，在仅按索引类型划分区别的索引器属性上调用 <code>GetCustomAttribute(s)</code> 将引发 <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="df31f-103">Prior to the .NET Framework 4.6, calling <code>GetCustomAttribute(s)</code> on an indexer property which differed from another property only by the type of the index would result in an <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>.</span></span> <span data-ttu-id="df31f-104">从 .NET Framework 4.6 开始，将正确返回该属性的属性。</span><span class="sxs-lookup"><span data-stu-id="df31f-104">Beginning in the .NET Framework 4.6, the property's attributes will be correctly returned.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="df31f-105">建议</span><span class="sxs-lookup"><span data-stu-id="df31f-105">Suggestion</span></span>

<span data-ttu-id="df31f-106">请注意，GetCustomAttribute 现在将更频繁地运行。</span><span class="sxs-lookup"><span data-stu-id="df31f-106">Be aware that GetCustomAttribute(s) will work more frequently now.</span></span> <span data-ttu-id="df31f-107">如果应用以前依赖于 <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>，现在应改用反射以显式查找多个索引器。</span><span class="sxs-lookup"><span data-stu-id="df31f-107">If an app was previously relying on the <xref:System.Reflection.AmbiguousMatchException?displayProperty=fullName>, reflection should now be used to explicitly look for multiple indexers, instead.</span></span>

| <span data-ttu-id="df31f-108">名称</span><span class="sxs-lookup"><span data-stu-id="df31f-108">Name</span></span>    | <span data-ttu-id="df31f-109">值</span><span class="sxs-lookup"><span data-stu-id="df31f-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df31f-110">范围</span><span class="sxs-lookup"><span data-stu-id="df31f-110">Scope</span></span>   |<span data-ttu-id="df31f-111">边缘</span><span class="sxs-lookup"><span data-stu-id="df31f-111">Edge</span></span>|
|<span data-ttu-id="df31f-112">Version</span><span class="sxs-lookup"><span data-stu-id="df31f-112">Version</span></span>|<span data-ttu-id="df31f-113">4.6</span><span class="sxs-lookup"><span data-stu-id="df31f-113">4.6</span></span>|
|<span data-ttu-id="df31f-114">类型</span><span class="sxs-lookup"><span data-stu-id="df31f-114">Type</span></span>|<span data-ttu-id="df31f-115">运行时</span><span class="sxs-lookup"><span data-stu-id="df31f-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="df31f-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="df31f-116">Affected APIs</span></span>

- <xref:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601(System.Reflection.MemberInfo)?displayProperty=nameWithType>
- <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601(System.Reflection.MemberInfo,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)`
- `M:System.Attribute.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)`
- `M:System.Attribute.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute``1(System.Reflection.MemberInfo)``
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttribute``1(System.Reflection.MemberInfo,System.Boolean)``
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Boolean)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type)`
- `M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes(System.Reflection.MemberInfo,System.Type,System.Boolean)`
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes``1(System.Reflection.MemberInfo)``
- ``M:System.Reflection.CustomAttributeExtensions.GetCustomAttributes``1(System.Reflection.MemberInfo,System.Boolean)``

-->
