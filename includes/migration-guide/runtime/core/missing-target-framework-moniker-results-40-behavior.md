---
ms.openlocfilehash: 49740d3b1890d72935e6e329a4f4be836ed70b25
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496944"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="5c9b9-101">在 4.0 行为中缺少了目标框架名字对象结果</span><span class="sxs-lookup"><span data-stu-id="5c9b9-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="5c9b9-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="5c9b9-102">Details</span></span>

<span data-ttu-id="5c9b9-103">未在程序集级别应用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 的应用程序将通过使用 .NET Framework 4.0 的语义 (quirks) 自动运行。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="5c9b9-104">为了确保高质量，建议所有二进制文件均通过 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 显式属性化，以指示用于生成它们的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="5c9b9-105">请注意，在项目文件中使用目标框架名字对象将使 MSBuild 自动应用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5c9b9-106">建议</span><span class="sxs-lookup"><span data-stu-id="5c9b9-106">Suggestion</span></span>

<span data-ttu-id="5c9b9-107">应通过以下方法提供 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>：将该属性直接添加到程序集，或者在[项目文件中或通过 Visual Studio 的项目属性 GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/) 指定目标框架。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="5c9b9-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="5c9b9-108">Name</span></span>    | <span data-ttu-id="5c9b9-109">“值”</span><span class="sxs-lookup"><span data-stu-id="5c9b9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5c9b9-110">范围</span><span class="sxs-lookup"><span data-stu-id="5c9b9-110">Scope</span></span>   |<span data-ttu-id="5c9b9-111">主要</span><span class="sxs-lookup"><span data-stu-id="5c9b9-111">Major</span></span>|
|<span data-ttu-id="5c9b9-112">Version</span><span class="sxs-lookup"><span data-stu-id="5c9b9-112">Version</span></span>|<span data-ttu-id="5c9b9-113">4.5</span><span class="sxs-lookup"><span data-stu-id="5c9b9-113">4.5</span></span>|
|<span data-ttu-id="5c9b9-114">类型</span><span class="sxs-lookup"><span data-stu-id="5c9b9-114">Type</span></span>|<span data-ttu-id="5c9b9-115">运行时</span><span class="sxs-lookup"><span data-stu-id="5c9b9-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5c9b9-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="5c9b9-116">Affected APIs</span></span>

<span data-ttu-id="5c9b9-117">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
