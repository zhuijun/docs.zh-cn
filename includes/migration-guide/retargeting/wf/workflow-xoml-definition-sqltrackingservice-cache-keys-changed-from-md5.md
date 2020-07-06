---
ms.openlocfilehash: 7a7ecf052276fe8e62463498b83230d466630c79
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617787"
---
### <a name="workflow-xoml-definition-and-sqltrackingservice-cache-keys-changed-from-md5-to-sha256"></a><span data-ttu-id="8e9a8-101">工作流 XOML 定义和 SqlTrackingService 缓存密钥已从 MD5 更改为 SHA256</span><span class="sxs-lookup"><span data-stu-id="8e9a8-101">Workflow XOML definition and SqlTrackingService cache keys changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="8e9a8-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="8e9a8-102">Details</span></span>

<span data-ttu-id="8e9a8-103">工作流运行时保存 XOML 中定义的工作流定义的缓存。</span><span class="sxs-lookup"><span data-stu-id="8e9a8-103">The Workflow Runtime in keeps a cache of workflow definitions defined in XOML.</span></span> <span data-ttu-id="8e9a8-104">SqlTrackingService 还保留按字符串键入的缓存。</span><span class="sxs-lookup"><span data-stu-id="8e9a8-104">The SqlTrackingService also keeps a cache that is keyed by strings.</span></span> <span data-ttu-id="8e9a8-105">由包含校验和哈希值的值键入这些缓存。</span><span class="sxs-lookup"><span data-stu-id="8e9a8-105">These caches are keyed by values that include checksum hash value.</span></span> <span data-ttu-id="8e9a8-106">在 .NET Framework 4.7.2 和早期版本中，该校验和哈希使用 MD5 算法，这会在启用 FIPS 的系统上导致问题。</span><span class="sxs-lookup"><span data-stu-id="8e9a8-106">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="8e9a8-107">从 .NET Framework 4.8 开始，使用的算法为 SHA256。由于每次工作流运行时和 SqlTrackingService 启动时都会重新计算值，因此进行此更改后不会出现兼容性问题。</span><span class="sxs-lookup"><span data-stu-id="8e9a8-107">Starting with the .NET Framework 4.8, the algorithm used is SHA256.There shouldn't be a compatibility issue with this change because the values are recalculated each time the Workflow Runtime and SqlTrackingService is started.</span></span> <span data-ttu-id="8e9a8-108">但是，我们提供了可以让客户恢复使用旧版哈希算法的例外做法（如有必要）。</span><span class="sxs-lookup"><span data-stu-id="8e9a8-108">However, we have provided quirks to allow customers to revert back to usage of the legacy hashing algorithm, if necessary.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8e9a8-109">建议</span><span class="sxs-lookup"><span data-stu-id="8e9a8-109">Suggestion</span></span>

<span data-ttu-id="8e9a8-110">如果此更改在执行工作流时出现问题，请尝试设置一个或两个 `AppContext` 开关：</span><span class="sxs-lookup"><span data-stu-id="8e9a8-110">If this change presents a problem when executing workflows, try setting one or both of the `AppContext` switches:</span></span>

- <span data-ttu-id="8e9a8-111">将 &quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; 设为 true。</span><span class="sxs-lookup"><span data-stu-id="8e9a8-111">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot; to true.</span></span>
- <span data-ttu-id="8e9a8-112">将 &quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; 设为 true。</span><span class="sxs-lookup"><span data-stu-id="8e9a8-112">&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot; to true.</span></span>
<span data-ttu-id="8e9a8-113">在代码中：</span><span class="sxs-lookup"><span data-stu-id="8e9a8-113">In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey&quot;, true);&#13;&#10;System.AppContext.SetSwitch(&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKey&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="8e9a8-114">或者在配置文件中（这需要在创建 <xref:System.Workflow.Runtime.WorkflowRuntime> 对象的应用程序的配置文件中）：</span><span class="sxs-lookup"><span data-stu-id="8e9a8-114">Or in the configuration file (this needs to be in the config file for the application that is creating the <xref:System.Workflow.Runtime.WorkflowRuntime> object):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForWorkflowDefinitionDispenserCacheKey=true&quot; /&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.Runtime.UseLegacyHashForSqlTrackingCacheKeytrue&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="8e9a8-115">名称</span><span class="sxs-lookup"><span data-stu-id="8e9a8-115">Name</span></span>    | <span data-ttu-id="8e9a8-116">“值”</span><span class="sxs-lookup"><span data-stu-id="8e9a8-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8e9a8-117">范围</span><span class="sxs-lookup"><span data-stu-id="8e9a8-117">Scope</span></span>   | <span data-ttu-id="8e9a8-118">次要</span><span class="sxs-lookup"><span data-stu-id="8e9a8-118">Minor</span></span>       |
| <span data-ttu-id="8e9a8-119">Version</span><span class="sxs-lookup"><span data-stu-id="8e9a8-119">Version</span></span> | <span data-ttu-id="8e9a8-120">4.8</span><span class="sxs-lookup"><span data-stu-id="8e9a8-120">4.8</span></span>         |
| <span data-ttu-id="8e9a8-121">类型</span><span class="sxs-lookup"><span data-stu-id="8e9a8-121">Type</span></span>    | <span data-ttu-id="8e9a8-122">重定目标</span><span class="sxs-lookup"><span data-stu-id="8e9a8-122">Retargeting</span></span> |
