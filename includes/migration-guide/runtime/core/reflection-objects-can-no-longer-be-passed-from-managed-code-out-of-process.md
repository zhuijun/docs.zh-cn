---
ms.openlocfilehash: f011f6ebe0fa85a59f3e69c93bba9eddc4c1689b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497807"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="93dd6-101">反射对象可能无法再从托管代码传递至进程外 DCOM 客户端</span><span class="sxs-lookup"><span data-stu-id="93dd6-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="93dd6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="93dd6-102">Details</span></span>

<span data-ttu-id="93dd6-103">反射对象可能无法再从托管代码传道至进程外客户端</span><span class="sxs-lookup"><span data-stu-id="93dd6-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="93dd6-104">以下类型将受影响：</span><span class="sxs-lookup"><span data-stu-id="93dd6-104">The following types are affected:</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <span data-ttu-id="93dd6-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName>（及其派生类型，包括 <xref:System.Reflection.FieldInfo?displayProperty=fullName>、<xref:System.Reflection.MethodInfo?displayProperty=fullName>、<xref:System.Type?displayProperty=fullName> 和 <xref:System.Reflection.TypeInfo?displayProperty=fullName>）</span><span class="sxs-lookup"><span data-stu-id="93dd6-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>

<span data-ttu-id="93dd6-106">调用对象的 <code>IMarshal</code> 会返回 <code>E_NOINTERFACE</code>。</span><span class="sxs-lookup"><span data-stu-id="93dd6-106">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="93dd6-107">建议</span><span class="sxs-lookup"><span data-stu-id="93dd6-107">Suggestion</span></span>

<span data-ttu-id="93dd6-108">更新封送代码，以与非反射对象一起使用。</span><span class="sxs-lookup"><span data-stu-id="93dd6-108">Update marshaling code to work with non-reflection objects.</span></span>

| <span data-ttu-id="93dd6-109">名称</span><span class="sxs-lookup"><span data-stu-id="93dd6-109">Name</span></span>    | <span data-ttu-id="93dd6-110">值</span><span class="sxs-lookup"><span data-stu-id="93dd6-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="93dd6-111">范围</span><span class="sxs-lookup"><span data-stu-id="93dd6-111">Scope</span></span>   |<span data-ttu-id="93dd6-112">次要</span><span class="sxs-lookup"><span data-stu-id="93dd6-112">Minor</span></span>|
|<span data-ttu-id="93dd6-113">Version</span><span class="sxs-lookup"><span data-stu-id="93dd6-113">Version</span></span>|<span data-ttu-id="93dd6-114">4.6</span><span class="sxs-lookup"><span data-stu-id="93dd6-114">4.6</span></span>|
|<span data-ttu-id="93dd6-115">类型</span><span class="sxs-lookup"><span data-stu-id="93dd6-115">Type</span></span>|<span data-ttu-id="93dd6-116">运行时</span><span class="sxs-lookup"><span data-stu-id="93dd6-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="93dd6-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="93dd6-117">Affected APIs</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <xref:System.Reflection.FieldInfo?displayProperty=fullName>
- <xref:System.Reflection.MemberInfo?displayProperty=fullName>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.MethodInfo?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>
- <xref:System.Reflection.TypeInfo?displayProperty=fullName>
- <xref:System.Type?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Reflection.Assembly`
- `T:System.Reflection.FieldInfo`
- `T:System.Reflection.MemberInfo`
- `T:System.Reflection.MethodBody`
- `T:System.Reflection.MethodInfo`
- `T:System.Reflection.Module`
- `T:System.Reflection.ParameterInfo`
- `T:System.Reflection.TypeInfo`
- `T:System.Type`

-->
