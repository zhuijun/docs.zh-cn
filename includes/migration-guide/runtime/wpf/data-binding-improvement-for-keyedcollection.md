---
ms.openlocfilehash: 8964cd2f69e95e4078001997ad5a5d126ce42d7b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497918"
---
### <a name="data-binding-improvement-for-keyedcollection"></a><span data-ttu-id="1e1ed-101">KeyedCollection 的数据绑定改进</span><span class="sxs-lookup"><span data-stu-id="1e1ed-101">Data Binding improvement for KeyedCollection</span></span>

#### <a name="details"></a><span data-ttu-id="1e1ed-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1e1ed-102">Details</span></span>

<span data-ttu-id="1e1ed-103">修复了源对象使用相同签名（例如，KeyedCollection&lt;int,TItem&gt;）声明自定义索引器时，<xref:System.Windows.Data.Binding> 错误使用 IList 索引器的问题。</span><span class="sxs-lookup"><span data-stu-id="1e1ed-103">Fixed <xref:System.Windows.Data.Binding> incorrect use of IList indexer when the source object declares a custom indexer with the same signature (for example, KeyedCollection&lt;int,TItem&gt;).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1e1ed-104">建议</span><span class="sxs-lookup"><span data-stu-id="1e1ed-104">Suggestion</span></span>

<span data-ttu-id="1e1ed-105">为了使针对较旧版本的应用程序能够从此更改中受益，它必须在 .NET Framework 4.8 或更高版本上运行，并且必须通过将以下 [AppContext 开关](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)添加到应用配置文件的 <code>&lt;runtime&gt;</code> 部分并将其设置为 <code>false</code> 来选择加入更改：</span><span class="sxs-lookup"><span data-stu-id="1e1ed-105">In order for an application that targets an older version to benefit from this change, it must run on the .NET Framework 4.8 or later, and it must opt in to the change by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the <code>&lt;runtime&gt;</code> section of the app config file and setting it to <code>false</code>:</span></span><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.Binding.IListIndexerHidesCustomIndexer=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1e1ed-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="1e1ed-106">Name</span></span>    | <span data-ttu-id="1e1ed-107">“值”</span><span class="sxs-lookup"><span data-stu-id="1e1ed-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1e1ed-108">范围</span><span class="sxs-lookup"><span data-stu-id="1e1ed-108">Scope</span></span>   |<span data-ttu-id="1e1ed-109">主要</span><span class="sxs-lookup"><span data-stu-id="1e1ed-109">Major</span></span>|
|<span data-ttu-id="1e1ed-110">Version</span><span class="sxs-lookup"><span data-stu-id="1e1ed-110">Version</span></span>|<span data-ttu-id="1e1ed-111">4.8</span><span class="sxs-lookup"><span data-stu-id="1e1ed-111">4.8</span></span>|
|<span data-ttu-id="1e1ed-112">类型</span><span class="sxs-lookup"><span data-stu-id="1e1ed-112">Type</span></span>|<span data-ttu-id="1e1ed-113">运行时</span><span class="sxs-lookup"><span data-stu-id="1e1ed-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1e1ed-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1e1ed-114">Affected APIs</span></span>

<span data-ttu-id="1e1ed-115">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="1e1ed-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
