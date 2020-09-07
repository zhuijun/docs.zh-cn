---
ms.openlocfilehash: 9baca45de1c8994f610815e84fdee8ba3930eb04
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496327"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="93d94-101">WCF MsmqSecureHashAlgorithm 现在的默认值为 SHA256</span><span class="sxs-lookup"><span data-stu-id="93d94-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="93d94-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="93d94-102">Details</span></span>

<span data-ttu-id="93d94-103">自 .NET Framework 4.7.1 起，Msmq 消息 WCF 中的默认消息签名算法为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="93d94-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="93d94-104">在 .NET Framework 4.7 和更低版本中，默认消息签名算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="93d94-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="93d94-105">建议</span><span class="sxs-lookup"><span data-stu-id="93d94-105">Suggestion</span></span>

<span data-ttu-id="93d94-106">如果在 .NET Framework 4.7.1 或更高版本中遇到此更改的兼容性问题，则可以通过将以下行添加到 app.config 文件的 <code>&lt;runtime&gt;</code> 部分选择退出更改：</span><span class="sxs-lookup"><span data-stu-id="93d94-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="93d94-107">名称</span><span class="sxs-lookup"><span data-stu-id="93d94-107">Name</span></span>    | <span data-ttu-id="93d94-108">值</span><span class="sxs-lookup"><span data-stu-id="93d94-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="93d94-109">范围</span><span class="sxs-lookup"><span data-stu-id="93d94-109">Scope</span></span>   |<span data-ttu-id="93d94-110">次要</span><span class="sxs-lookup"><span data-stu-id="93d94-110">Minor</span></span>|
|<span data-ttu-id="93d94-111">Version</span><span class="sxs-lookup"><span data-stu-id="93d94-111">Version</span></span>|<span data-ttu-id="93d94-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="93d94-112">4.7.1</span></span>|
|<span data-ttu-id="93d94-113">类型</span><span class="sxs-lookup"><span data-stu-id="93d94-113">Type</span></span>|<span data-ttu-id="93d94-114">运行时</span><span class="sxs-lookup"><span data-stu-id="93d94-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="93d94-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="93d94-115">Affected APIs</span></span>

<span data-ttu-id="93d94-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="93d94-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
