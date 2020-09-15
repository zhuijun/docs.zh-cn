---
ms.openlocfilehash: 3300a74b81fc9eeba670ee0ceb2c2615fd3925bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617126"
---
### <a name="listlttgtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="664a3-101">List&lt;T&gt;.ForEach 在修改列表项时可能会引发异常</span><span class="sxs-lookup"><span data-stu-id="664a3-101">List&lt;T&gt;.ForEach can throw exception when modifying list item</span></span>

#### <a name="details"></a><span data-ttu-id="664a3-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="664a3-102">Details</span></span>

<span data-ttu-id="664a3-103">从 .NET Framework 4.5 开始，如果修改了调用集合中的元素，<xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> 枚举器将引发 <xref:System.InvalidOperationException?displayProperty=fullName> 异常。</span><span class="sxs-lookup"><span data-stu-id="664a3-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=fullName> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="664a3-104">该操作在以前不会引发异常，但可能会导致争用条件。</span><span class="sxs-lookup"><span data-stu-id="664a3-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="664a3-105">建议</span><span class="sxs-lookup"><span data-stu-id="664a3-105">Suggestion</span></span>

<span data-ttu-id="664a3-106">理想情况下，应修复代码以便在枚举列表元素时不会修改列表，因为这始终不是安全操作。</span><span class="sxs-lookup"><span data-stu-id="664a3-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="664a3-107">但是，若要还原到以前的行为，应用可面向 .NET Framework 4.0。</span><span class="sxs-lookup"><span data-stu-id="664a3-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>

| <span data-ttu-id="664a3-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="664a3-108">Name</span></span>    | <span data-ttu-id="664a3-109">“值”</span><span class="sxs-lookup"><span data-stu-id="664a3-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="664a3-110">范围</span><span class="sxs-lookup"><span data-stu-id="664a3-110">Scope</span></span>   | <span data-ttu-id="664a3-111">边缘</span><span class="sxs-lookup"><span data-stu-id="664a3-111">Edge</span></span>        |
| <span data-ttu-id="664a3-112">Version</span><span class="sxs-lookup"><span data-stu-id="664a3-112">Version</span></span> | <span data-ttu-id="664a3-113">4.5</span><span class="sxs-lookup"><span data-stu-id="664a3-113">4.5</span></span>         |
| <span data-ttu-id="664a3-114">类型</span><span class="sxs-lookup"><span data-stu-id="664a3-114">Type</span></span>    | <span data-ttu-id="664a3-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="664a3-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="664a3-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="664a3-116">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType>
