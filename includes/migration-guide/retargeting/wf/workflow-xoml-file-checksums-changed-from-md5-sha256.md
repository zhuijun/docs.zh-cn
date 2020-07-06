---
ms.openlocfilehash: 2aa424ff5e3308b730c22cb865993d4100f193cc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617788"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="34439-101">工作流 XOML 文件校验和已从 MD5 更改为 SHA256</span><span class="sxs-lookup"><span data-stu-id="34439-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="34439-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="34439-102">Details</span></span>

<span data-ttu-id="34439-103">为了支持使用 Visual Studio 调试基于 XOML 的工作流，当生成包含 XOML 文件的工作流项目时，系统会将 XOML 文件内容的校验和作为 <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> 值包含在生成的代码中。</span><span class="sxs-lookup"><span data-stu-id="34439-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="34439-104">在 .NET Framework 4.7.2 和早期版本中，该校验和哈希使用 MD5 算法，这会在启用 FIPS 的系统上导致问题。</span><span class="sxs-lookup"><span data-stu-id="34439-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="34439-105">从 .NET Framework 4.8 开始，采用的算法为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="34439-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="34439-106">为了与 WorkflowMarkupSourceAttribute.MD5Digest 兼容，只使用生成的校验和的前 16 个字节。这可能会导致调试过程中出现问题。</span><span class="sxs-lookup"><span data-stu-id="34439-106">To be compatibile with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="34439-107">可能需要重新生成项目。</span><span class="sxs-lookup"><span data-stu-id="34439-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="34439-108">建议</span><span class="sxs-lookup"><span data-stu-id="34439-108">Suggestion</span></span>

<span data-ttu-id="34439-109">如果重新生成项目没有解决问题，请尝试在代码中将 `AppContext` 开关 &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; 设置为 true：</span><span class="sxs-lookup"><span data-stu-id="34439-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="34439-110">或者在配置文件中设置（需要位于正在使用的 MSBuild.exe 的 MSBuild.exe.config 中）：</span><span class="sxs-lookup"><span data-stu-id="34439-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="34439-111">名称</span><span class="sxs-lookup"><span data-stu-id="34439-111">Name</span></span>    | <span data-ttu-id="34439-112">“值”</span><span class="sxs-lookup"><span data-stu-id="34439-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="34439-113">范围</span><span class="sxs-lookup"><span data-stu-id="34439-113">Scope</span></span>   | <span data-ttu-id="34439-114">次要</span><span class="sxs-lookup"><span data-stu-id="34439-114">Minor</span></span>       |
| <span data-ttu-id="34439-115">Version</span><span class="sxs-lookup"><span data-stu-id="34439-115">Version</span></span> | <span data-ttu-id="34439-116">4.8</span><span class="sxs-lookup"><span data-stu-id="34439-116">4.8</span></span>         |
| <span data-ttu-id="34439-117">类型</span><span class="sxs-lookup"><span data-stu-id="34439-117">Type</span></span>    | <span data-ttu-id="34439-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="34439-118">Retargeting</span></span> |
