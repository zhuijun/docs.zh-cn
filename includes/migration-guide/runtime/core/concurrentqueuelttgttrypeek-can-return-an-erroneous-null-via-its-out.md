---
ms.openlocfilehash: 004e2d1883b631e88ab5e164b1120c3b081b7041
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497576"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="3aac1-101">ConcurrentQueue&lt;T&gt;.TryPeek 可通过 out 参数返回错误的 null</span><span class="sxs-lookup"><span data-stu-id="3aac1-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="3aac1-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3aac1-102">Details</span></span>

<span data-ttu-id="3aac1-103">在某些多线程情况下，<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> 可返回 true，但使用 null 值填充 Out 参数（而非正确的扫视值）。</span><span class="sxs-lookup"><span data-stu-id="3aac1-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3aac1-104">建议</span><span class="sxs-lookup"><span data-stu-id="3aac1-104">Suggestion</span></span>

<span data-ttu-id="3aac1-105">此问题已在 .NET Framework 4.5.1 中解决。</span><span class="sxs-lookup"><span data-stu-id="3aac1-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="3aac1-106">升级到该 Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="3aac1-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="3aac1-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="3aac1-107">Name</span></span>    | <span data-ttu-id="3aac1-108">“值”</span><span class="sxs-lookup"><span data-stu-id="3aac1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3aac1-109">范围</span><span class="sxs-lookup"><span data-stu-id="3aac1-109">Scope</span></span>   |<span data-ttu-id="3aac1-110">主要</span><span class="sxs-lookup"><span data-stu-id="3aac1-110">Major</span></span>|
|<span data-ttu-id="3aac1-111">Version</span><span class="sxs-lookup"><span data-stu-id="3aac1-111">Version</span></span>|<span data-ttu-id="3aac1-112">4.5</span><span class="sxs-lookup"><span data-stu-id="3aac1-112">4.5</span></span>|
|<span data-ttu-id="3aac1-113">类型</span><span class="sxs-lookup"><span data-stu-id="3aac1-113">Type</span></span>|<span data-ttu-id="3aac1-114">运行时</span><span class="sxs-lookup"><span data-stu-id="3aac1-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3aac1-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3aac1-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.ConcurrentQueue`1.TryPeek(`0@)``

-->
