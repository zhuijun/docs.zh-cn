---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621146"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="7e6ec-101">反射对象可能无法再从托管代码传递至进程外 DCOM 客户端</span><span class="sxs-lookup"><span data-stu-id="7e6ec-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="7e6ec-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="7e6ec-102">Details</span></span>

<span data-ttu-id="7e6ec-103">反射对象可能无法再从托管代码传道至进程外客户端</span><span class="sxs-lookup"><span data-stu-id="7e6ec-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="7e6ec-104">以下类型将受影响：</span><span class="sxs-lookup"><span data-stu-id="7e6ec-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><span data-ttu-id="7e6ec-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName>（及其派生类型，包括 <xref:System.Reflection.FieldInfo?displayProperty=fullName>、<xref:System.Reflection.MethodInfo?displayProperty=fullName>、<xref:System.Type?displayProperty=fullName> 和 <xref:System.Reflection.TypeInfo?displayProperty=fullName>）</span><span class="sxs-lookup"><span data-stu-id="7e6ec-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><span data-ttu-id="7e6ec-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="7e6ec-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span></span></li></ul><span data-ttu-id="7e6ec-107">调用对象的 <code>IMarshal</code> 会返回 <code>E_NOINTERFACE</code>。</span><span class="sxs-lookup"><span data-stu-id="7e6ec-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7e6ec-108">建议</span><span class="sxs-lookup"><span data-stu-id="7e6ec-108">Suggestion</span></span>

<span data-ttu-id="7e6ec-109">更新封送代码，以与非反射对象一起使用</span><span class="sxs-lookup"><span data-stu-id="7e6ec-109">Update marshaling code to work with non-reflection objects</span></span>

| <span data-ttu-id="7e6ec-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="7e6ec-110">Name</span></span>    | <span data-ttu-id="7e6ec-111">值</span><span class="sxs-lookup"><span data-stu-id="7e6ec-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7e6ec-112">范围</span><span class="sxs-lookup"><span data-stu-id="7e6ec-112">Scope</span></span>   |<span data-ttu-id="7e6ec-113">次要</span><span class="sxs-lookup"><span data-stu-id="7e6ec-113">Minor</span></span>|
|<span data-ttu-id="7e6ec-114">Version</span><span class="sxs-lookup"><span data-stu-id="7e6ec-114">Version</span></span>|<span data-ttu-id="7e6ec-115">4.6</span><span class="sxs-lookup"><span data-stu-id="7e6ec-115">4.6</span></span>|
|<span data-ttu-id="7e6ec-116">类型</span><span class="sxs-lookup"><span data-stu-id="7e6ec-116">Type</span></span>|<span data-ttu-id="7e6ec-117">运行时</span><span class="sxs-lookup"><span data-stu-id="7e6ec-117">Runtime</span></span>|
