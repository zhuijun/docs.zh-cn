---
ms.openlocfilehash: 760c9ce2427bc1f5e9276e66ecb6d2cf2ed83c16
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738810"
---
### <a name="parameter-names-changed-in-rc1"></a><span data-ttu-id="bd301-101">RC1 中的参数名称已更改</span><span class="sxs-lookup"><span data-stu-id="bd301-101">Parameter names changed in RC1</span></span>

<span data-ttu-id="bd301-102">某些引用程序集参数名称已更改以匹配实现程序集中的参数名称。</span><span class="sxs-lookup"><span data-stu-id="bd301-102">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bd301-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="bd301-103">Change description</span></span>

<span data-ttu-id="bd301-104">在以前的 .NET 5.0 预览版和 RC 版本中，某些[引用程序集](../../../../docs/standard/assembly/reference-assemblies.md)参数名称与实现程序集中的对应参数不同。</span><span class="sxs-lookup"><span data-stu-id="bd301-104">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../docs/standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="bd301-105">使用命名参数和反射时，这可能会导致出现问题。</span><span class="sxs-lookup"><span data-stu-id="bd301-105">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="bd301-106">在 .NET 5.0 RC2 中，这些不匹配的参数名称在引用程序集中已更新，以与实现程序集中的相应参数名完全匹配。</span><span class="sxs-lookup"><span data-stu-id="bd301-106">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="bd301-107">下表显示了更改的 API 和参数名称。</span><span class="sxs-lookup"><span data-stu-id="bd301-107">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="bd301-108">API</span><span class="sxs-lookup"><span data-stu-id="bd301-108">API</span></span> | <span data-ttu-id="bd301-109">旧参数名称</span><span class="sxs-lookup"><span data-stu-id="bd301-109">Old parameter name</span></span> | <span data-ttu-id="bd301-110">新参数名称</span><span class="sxs-lookup"><span data-stu-id="bd301-110">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

#### <a name="reason-for-change"></a><span data-ttu-id="bd301-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="bd301-111">Reason for change</span></span>

<span data-ttu-id="bd301-112">更改参数名称以保持一致性，避免在使用命名参数和反射时出现故障。</span><span class="sxs-lookup"><span data-stu-id="bd301-112">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bd301-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="bd301-113">Version introduced</span></span>

<span data-ttu-id="bd301-114">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="bd301-114">5.0 RC2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bd301-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="bd301-115">Recommended action</span></span>

<span data-ttu-id="bd301-116">如果由于参数名称更改而遇到编译器错误，请相应地更新参数名称。</span><span class="sxs-lookup"><span data-stu-id="bd301-116">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

#### <a name="category"></a><span data-ttu-id="bd301-117">类别</span><span class="sxs-lookup"><span data-stu-id="bd301-117">Category</span></span>

<span data-ttu-id="bd301-118">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="bd301-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bd301-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="bd301-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
