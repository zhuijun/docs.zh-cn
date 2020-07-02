---
ms.openlocfilehash: 0f87f9e9b87860da97ce96e18104b44ec4327c91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621054"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="78523-101">WCF PipeConnection.GetHashAlgorithm 现在使用 SHA256</span><span class="sxs-lookup"><span data-stu-id="78523-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="78523-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="78523-102">Details</span></span>

<span data-ttu-id="78523-103">从 .NET Framework 4.7.1 开始，Windows Communication Foundation 使用 SHA256 哈希为命名管道生成随机名称。</span><span class="sxs-lookup"><span data-stu-id="78523-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="78523-104">在 .NET Framework 4.7 和更早版本中，它使用 SHA1 哈希。</span><span class="sxs-lookup"><span data-stu-id="78523-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="78523-105">建议</span><span class="sxs-lookup"><span data-stu-id="78523-105">Suggestion</span></span>

<span data-ttu-id="78523-106">如果在 .NET Framework 4.7.1 或更高版本中遇到此更改的兼容性问题，则可以通过将以下行添加到 app.config 文件的 <code>&lt;runtime&gt;</code> 部分选择弃用此更改：</span><span class="sxs-lookup"><span data-stu-id="78523-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="78523-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="78523-107">Name</span></span>    | <span data-ttu-id="78523-108">值</span><span class="sxs-lookup"><span data-stu-id="78523-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="78523-109">范围</span><span class="sxs-lookup"><span data-stu-id="78523-109">Scope</span></span>   |<span data-ttu-id="78523-110">次要</span><span class="sxs-lookup"><span data-stu-id="78523-110">Minor</span></span>|
|<span data-ttu-id="78523-111">Version</span><span class="sxs-lookup"><span data-stu-id="78523-111">Version</span></span>|<span data-ttu-id="78523-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="78523-112">4.7.1</span></span>|
|<span data-ttu-id="78523-113">类型</span><span class="sxs-lookup"><span data-stu-id="78523-113">Type</span></span>|<span data-ttu-id="78523-114">运行时</span><span class="sxs-lookup"><span data-stu-id="78523-114">Runtime</span></span>|
