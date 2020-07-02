---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619839"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="405cc-101">在 4.0 行为中缺少了目标框架名字对象结果</span><span class="sxs-lookup"><span data-stu-id="405cc-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="405cc-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="405cc-102">Details</span></span>

<span data-ttu-id="405cc-103">未在程序集级别应用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 的应用程序将通过使用 .NET Framework 4.0 的语义 (quirks) 自动运行。</span><span class="sxs-lookup"><span data-stu-id="405cc-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="405cc-104">为了确保高质量，建议所有二进制文件均通过 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 显式属性化，以指示用于生成它们的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="405cc-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="405cc-105">请注意，在项目文件中使用目标框架名字对象将使 MSBuild 自动应用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="405cc-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="405cc-106">建议</span><span class="sxs-lookup"><span data-stu-id="405cc-106">Suggestion</span></span>

<span data-ttu-id="405cc-107">应通过以下方法提供 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>：将该属性直接添加到程序集，或者在[项目文件中或通过 Visual Studio 的项目属性 GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/) 指定目标框架。</span><span class="sxs-lookup"><span data-stu-id="405cc-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="405cc-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="405cc-108">Name</span></span>    | <span data-ttu-id="405cc-109">“值”</span><span class="sxs-lookup"><span data-stu-id="405cc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="405cc-110">范围</span><span class="sxs-lookup"><span data-stu-id="405cc-110">Scope</span></span>   |<span data-ttu-id="405cc-111">主要</span><span class="sxs-lookup"><span data-stu-id="405cc-111">Major</span></span>|
|<span data-ttu-id="405cc-112">Version</span><span class="sxs-lookup"><span data-stu-id="405cc-112">Version</span></span>|<span data-ttu-id="405cc-113">4.5</span><span class="sxs-lookup"><span data-stu-id="405cc-113">4.5</span></span>|
|<span data-ttu-id="405cc-114">类型</span><span class="sxs-lookup"><span data-stu-id="405cc-114">Type</span></span>|<span data-ttu-id="405cc-115">运行时</span><span class="sxs-lookup"><span data-stu-id="405cc-115">Runtime</span></span>|
