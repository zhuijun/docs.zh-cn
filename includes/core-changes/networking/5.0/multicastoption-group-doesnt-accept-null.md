---
ms.openlocfilehash: 88a0b7e04c7015ca3fa5abd8a6897dafcbe41c49
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557955"
---
### <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="a5d30-101">MulticastOption.Group 不接受 null 值</span><span class="sxs-lookup"><span data-stu-id="a5d30-101">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="a5d30-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 不再接受 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="a5d30-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="a5d30-103">如果将属性设置为 `null`，则会引发 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="a5d30-103">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a5d30-104">引入的版本</span><span class="sxs-lookup"><span data-stu-id="a5d30-104">Version introduced</span></span>

<span data-ttu-id="a5d30-105">5.0</span><span class="sxs-lookup"><span data-stu-id="a5d30-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="a5d30-106">更改描述</span><span class="sxs-lookup"><span data-stu-id="a5d30-106">Change description</span></span>

<span data-ttu-id="a5d30-107">在早期版本的 .NET 中，可以将 <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 属性设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="a5d30-107">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="a5d30-108">如果 <xref:System.Net.Sockets.MulticastOption> 稍后传递给 <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>，则运行时将引发 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="a5d30-108">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="a5d30-109">在 .NET 5.0 和更高版本中，如果将属性设置为 `null`，则会引发 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="a5d30-109">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a5d30-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="a5d30-110">Reason for change</span></span>

<span data-ttu-id="a5d30-111">为了与框架设计准则保持一致，属性已更新为在值为 `null` 时引发 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="a5d30-111">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a5d30-112">建议操作</span><span class="sxs-lookup"><span data-stu-id="a5d30-112">Recommended action</span></span>

<span data-ttu-id="a5d30-113">请确保未将 <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="a5d30-113">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

#### <a name="category"></a><span data-ttu-id="a5d30-114">类别</span><span class="sxs-lookup"><span data-stu-id="a5d30-114">Category</span></span>

<span data-ttu-id="a5d30-115">网络</span><span class="sxs-lookup"><span data-stu-id="a5d30-115">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a5d30-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a5d30-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

-->
