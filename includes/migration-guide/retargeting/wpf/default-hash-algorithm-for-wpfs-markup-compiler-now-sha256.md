---
ms.openlocfilehash: 4303b177ffe01328965c909a5a3809414fcead91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614409"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a><span data-ttu-id="00885-101">现在 WPF 标记编译器的默认哈希算法为 SHA256</span><span class="sxs-lookup"><span data-stu-id="00885-101">The default hash algorithm for WPF's Markup Compiler is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="00885-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="00885-102">Details</span></span>

<span data-ttu-id="00885-103">WPF 标记编译器为 XAML 标记文件提供编译服务。</span><span class="sxs-lookup"><span data-stu-id="00885-103">The WPF MarkupCompiler provides compilation services for XAML markup files.</span></span>  <span data-ttu-id="00885-104">在 .NET Framework 4.7.1 及更早版本中，用于校验和的默认哈希算法为 SHA1。</span><span class="sxs-lookup"><span data-stu-id="00885-104">In the .NET Framework 4.7.1 and earlier versions, the default hash algorithm used for checksums was SHA1.</span></span> <span data-ttu-id="00885-105">由于 SHA1 最近出现安全问题，从 .NET Framework 4.7.2 起，此默认算法已更改为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="00885-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.2.</span></span>  <span data-ttu-id="00885-106">此更改会影响编译期间标记文件的所有校验和生成。</span><span class="sxs-lookup"><span data-stu-id="00885-106">This change affects all checksum generation for markup files during compilation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="00885-107">建议</span><span class="sxs-lookup"><span data-stu-id="00885-107">Suggestion</span></span>

<span data-ttu-id="00885-108">如果开发人员面向 .NET Framework 4.7.2 或更高版本且想要还原到 SHA1 哈希行为，则必须设置以下 AppContext 标记。</span><span class="sxs-lookup"><span data-stu-id="00885-108">A developer who targets .NET Framework 4.7.2 or greater and wants to revert to SHA1 hashing behavior must set the following AppContext flag.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="00885-109">如果开发人员面向 .NET 4.7.2 更低版本且想要利用 SHA256 哈希，则必须设置以下 AppContext 标记。</span><span class="sxs-lookup"><span data-stu-id="00885-109">A developer who wants to utilize SHA256 hashing while targeting a framework version below .NET 4.7.2 must set the below AppContext flag.</span></span>  <span data-ttu-id="00885-110">请注意，安装的 .NET Framework 必须是 4.7.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="00885-110">Note that the installed version of the .NET Framework must be 4.7.2 or greater.</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="00885-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="00885-111">Name</span></span>    | <span data-ttu-id="00885-112">“值”</span><span class="sxs-lookup"><span data-stu-id="00885-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="00885-113">范围</span><span class="sxs-lookup"><span data-stu-id="00885-113">Scope</span></span>   | <span data-ttu-id="00885-114">透明</span><span class="sxs-lookup"><span data-stu-id="00885-114">Transparent</span></span> |
| <span data-ttu-id="00885-115">Version</span><span class="sxs-lookup"><span data-stu-id="00885-115">Version</span></span> | <span data-ttu-id="00885-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="00885-116">4.7.2</span></span>       |
| <span data-ttu-id="00885-117">类型</span><span class="sxs-lookup"><span data-stu-id="00885-117">Type</span></span>    | <span data-ttu-id="00885-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="00885-118">Retargeting</span></span> |
