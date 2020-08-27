---
ms.openlocfilehash: cf51d5f6b3eee7189fd9613b3d780a829d197a04
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557994"
---
### <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="3322d-101">System.Security.Cryptography.Oid 在功能上仅用于初始化</span><span class="sxs-lookup"><span data-stu-id="3322d-101">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="3322d-102">用于表示 ASN.1 对象标识符值及其易记名称的 <xref:System.Security.Cryptography.Oid?displayProperty=fullName> 类以前是完全可变的。</span><span class="sxs-lookup"><span data-stu-id="3322d-102">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="3322d-103">此可变性经常被忽视或意外出现。</span><span class="sxs-lookup"><span data-stu-id="3322d-103">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="3322d-104">现在，当你在分配值后尝试更改该值时，属性资源库会引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="3322d-104">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3322d-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="3322d-105">Change description</span></span>

<span data-ttu-id="3322d-106">在以前的版本中，<xref:System.Security.Cryptography.Oid> 上的属性资源库可用于更改 <xref:System.Security.Cryptography.Oid.FriendlyName> 和 <xref:System.Security.Cryptography.Oid.Value> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="3322d-106">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="3322d-107">在 .NET 5.0 和更高版本中，属性资源库仅可用于初始化值。</span><span class="sxs-lookup"><span data-stu-id="3322d-107">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="3322d-108">属性具有值后，无论是从构造函数还是以前版本调用属性资源库，属性资源库始终引发 <xref:System.PlatformNotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="3322d-108">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3322d-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="3322d-109">Reason for change</span></span>

<span data-ttu-id="3322d-110">通过此更改，可将 <xref:System.Security.Cryptography.Oid> 对象作为公共 API 中的返回值的一部分重用，以减少对象分配配置文件。</span><span class="sxs-lookup"><span data-stu-id="3322d-110">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="3322d-111">当 <xref:System.Security.Cryptography.Oid> 值用作输入时，则无需创建临时的“防御”副本。</span><span class="sxs-lookup"><span data-stu-id="3322d-111">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3322d-112">引入的版本</span><span class="sxs-lookup"><span data-stu-id="3322d-112">Version introduced</span></span>

<span data-ttu-id="3322d-113">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="3322d-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3322d-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="3322d-114">Recommended action</span></span>

<span data-ttu-id="3322d-115">除了用于对象初始化之外，请避免使用 <xref:System.Security.Cryptography.Oid> 属性资源库。</span><span class="sxs-lookup"><span data-stu-id="3322d-115">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="3322d-116">若要表示新值，请使用新的实例，而不是更改现有对象上的值。</span><span class="sxs-lookup"><span data-stu-id="3322d-116">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

#### <a name="category"></a><span data-ttu-id="3322d-117">类别</span><span class="sxs-lookup"><span data-stu-id="3322d-117">Category</span></span>

<span data-ttu-id="3322d-118">密码</span><span class="sxs-lookup"><span data-stu-id="3322d-118">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3322d-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3322d-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

-->
