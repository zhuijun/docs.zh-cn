---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616030"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a><span data-ttu-id="d3bbe-101">不支持对具有非公共资源库的属性的双向数据绑定</span><span class="sxs-lookup"><span data-stu-id="d3bbe-101">Two-way data-binding to a property with a non-public setter is not supported</span></span>

#### <a name="details"></a><span data-ttu-id="d3bbe-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d3bbe-102">Details</span></span>

<span data-ttu-id="d3bbe-103">尝试将数据绑定到没有公共资源库的方案从未受支持。</span><span class="sxs-lookup"><span data-stu-id="d3bbe-103">Attempting to data bind to a property without a public setter has never been a supported scenario.</span></span> <span data-ttu-id="d3bbe-104">从 .NET Framework 4.5.1 开始，此方案将引发 <xref:System.InvalidOperationException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="d3bbe-104">Beginning in the .NET Framework 4.5.1, this scenario will throw an <xref:System.InvalidOperationException?displayProperty=fullName>.</span></span> <span data-ttu-id="d3bbe-105">请注意，仅专门面向 .NET Framework 4.5.1 的应用会引发此新异常。</span><span class="sxs-lookup"><span data-stu-id="d3bbe-105">Note that this new exception will only be thrown for apps that specifically target the .NET Framework 4.5.1.</span></span> <span data-ttu-id="d3bbe-106">如果应用面向 .NET Framework 4.5，将允许该调用。</span><span class="sxs-lookup"><span data-stu-id="d3bbe-106">If an app targets the .NET Framework 4.5, the call will be allowed.</span></span> <span data-ttu-id="d3bbe-107">如果应用不面向特定 .NET Framework 版本，绑定将视为单向绑定。</span><span class="sxs-lookup"><span data-stu-id="d3bbe-107">If the app does not target a particular .NET Framework version, the binding will be treated as one-way.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d3bbe-108">建议</span><span class="sxs-lookup"><span data-stu-id="d3bbe-108">Suggestion</span></span>

<span data-ttu-id="d3bbe-109">应更新应用以使用单向绑定，或公开公布属性的资源库。</span><span class="sxs-lookup"><span data-stu-id="d3bbe-109">The app should be updated to either use one-way binding, or expose the property's setter publicly.</span></span> <span data-ttu-id="d3bbe-110">或者，面向 .NET Framework 4.5 将使应用展示旧行为。</span><span class="sxs-lookup"><span data-stu-id="d3bbe-110">Alternatively, targeting the .NET Framework 4.5 will cause the app to exhibit the old behavior.</span></span>

| <span data-ttu-id="d3bbe-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="d3bbe-111">Name</span></span>    | <span data-ttu-id="d3bbe-112">“值”</span><span class="sxs-lookup"><span data-stu-id="d3bbe-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d3bbe-113">范围</span><span class="sxs-lookup"><span data-stu-id="d3bbe-113">Scope</span></span>   | <span data-ttu-id="d3bbe-114">次要</span><span class="sxs-lookup"><span data-stu-id="d3bbe-114">Minor</span></span>       |
| <span data-ttu-id="d3bbe-115">Version</span><span class="sxs-lookup"><span data-stu-id="d3bbe-115">Version</span></span> | <span data-ttu-id="d3bbe-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d3bbe-116">4.5.1</span></span>       |
| <span data-ttu-id="d3bbe-117">类型</span><span class="sxs-lookup"><span data-stu-id="d3bbe-117">Type</span></span>    | <span data-ttu-id="d3bbe-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="d3bbe-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d3bbe-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d3bbe-119">Affected APIs</span></span>

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
