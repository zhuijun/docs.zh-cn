---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621052"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="b414d-101">WCF MsmqSecureHashAlgorithm 现在的默认值为 SHA256</span><span class="sxs-lookup"><span data-stu-id="b414d-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="b414d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b414d-102">Details</span></span>

<span data-ttu-id="b414d-103">自 .NET Framework 4.7.1 起，Msmq 消息 WCF 中的默认消息签名算法为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="b414d-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="b414d-104">在 .NET Framework 4.7 和更低版本中，默认消息签名算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="b414d-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b414d-105">建议</span><span class="sxs-lookup"><span data-stu-id="b414d-105">Suggestion</span></span>

<span data-ttu-id="b414d-106">如果在 .NET Framework 4.7.1 或更高版本中遇到此更改的兼容性问题，则可以通过将以下行添加到 app.config 文件的 <code>&lt;runtime&gt;</code> 部分选择退出更改：</span><span class="sxs-lookup"><span data-stu-id="b414d-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="b414d-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="b414d-107">Name</span></span>    | <span data-ttu-id="b414d-108">值</span><span class="sxs-lookup"><span data-stu-id="b414d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b414d-109">范围</span><span class="sxs-lookup"><span data-stu-id="b414d-109">Scope</span></span>   |<span data-ttu-id="b414d-110">次要</span><span class="sxs-lookup"><span data-stu-id="b414d-110">Minor</span></span>|
|<span data-ttu-id="b414d-111">Version</span><span class="sxs-lookup"><span data-stu-id="b414d-111">Version</span></span>|<span data-ttu-id="b414d-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="b414d-112">4.7.1</span></span>|
|<span data-ttu-id="b414d-113">类型</span><span class="sxs-lookup"><span data-stu-id="b414d-113">Type</span></span>|<span data-ttu-id="b414d-114">运行时</span><span class="sxs-lookup"><span data-stu-id="b414d-114">Runtime</span></span>|
