---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619827"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="b012d-101">使用 Regex.CompileToAssembly 进行编译的程序集在 4.0 和 4.5 之间中断</span><span class="sxs-lookup"><span data-stu-id="b012d-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="b012d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b012d-102">Details</span></span>

<span data-ttu-id="b012d-103">如果已编译的正则表达式的程序集使用 .NET Framework 4.5 生成但却面向 .NET Framework 4，则在安装了 .NET Framework 4 的系统上尝试使用该程序集的正则表达式之一时，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="b012d-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b012d-104">建议</span><span class="sxs-lookup"><span data-stu-id="b012d-104">Suggestion</span></span>

<span data-ttu-id="b012d-105">若要解决此问题，可执行下列操作之一：</span><span class="sxs-lookup"><span data-stu-id="b012d-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="b012d-106">使用 .NET Framework 4 生成包含正则表达式的程序集。</span><span class="sxs-lookup"><span data-stu-id="b012d-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="b012d-107">使用已解释的正则表达式。</span><span class="sxs-lookup"><span data-stu-id="b012d-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="b012d-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="b012d-108">Name</span></span>    | <span data-ttu-id="b012d-109">“值”</span><span class="sxs-lookup"><span data-stu-id="b012d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b012d-110">范围</span><span class="sxs-lookup"><span data-stu-id="b012d-110">Scope</span></span>   |<span data-ttu-id="b012d-111">次要</span><span class="sxs-lookup"><span data-stu-id="b012d-111">Minor</span></span>|
|<span data-ttu-id="b012d-112">Version</span><span class="sxs-lookup"><span data-stu-id="b012d-112">Version</span></span>|<span data-ttu-id="b012d-113">4.5</span><span class="sxs-lookup"><span data-stu-id="b012d-113">4.5</span></span>|
|<span data-ttu-id="b012d-114">类型</span><span class="sxs-lookup"><span data-stu-id="b012d-114">Type</span></span>|<span data-ttu-id="b012d-115">运行时</span><span class="sxs-lookup"><span data-stu-id="b012d-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b012d-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b012d-116">Affected APIs</span></span>

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
