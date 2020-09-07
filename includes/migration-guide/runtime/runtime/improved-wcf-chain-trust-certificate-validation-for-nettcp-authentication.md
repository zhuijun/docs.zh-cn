---
ms.openlocfilehash: c8f017084fc1ec1eca636ef0178a40559e15b2c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497189"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a><span data-ttu-id="55e37-101">改进了 Net.Tcp 证书身份验证的 WCF 链信任证书验证</span><span class="sxs-lookup"><span data-stu-id="55e37-101">Improved WCF chain trust certificate validation for Net.Tcp certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="55e37-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="55e37-102">Details</span></span>

<span data-ttu-id="55e37-103">.NET Framework 4.7.2 改进了通过 WCF 对传输安全性使用证书身份验证时的链信任证书验证。</span><span class="sxs-lookup"><span data-stu-id="55e37-103">.NET Framework 4.7.2 improves chain trust certificate validation when using certificate authentication with transport security with WCF.</span></span> <span data-ttu-id="55e37-104">由于此改进，用于对服务器进行身份验证的客户端证书必须为客户端身份验证进行配置。</span><span class="sxs-lookup"><span data-stu-id="55e37-104">With this improvement, client certificates that are used to authenticate to a server must be configured for client authentication.</span></span>  <span data-ttu-id="55e37-105">同样，用于对服务器进行身份验证的服务器证书必须为服务器身份验证进行配置。</span><span class="sxs-lookup"><span data-stu-id="55e37-105">Similarly server certificates that are for the authenticating a server must be configured for server authentication.</span></span> <span data-ttu-id="55e37-106">由于此更改，如果禁用根证书，证书链验证将失败。</span><span class="sxs-lookup"><span data-stu-id="55e37-106">With this change, if the root certificate is disabled, the certificate chain validation fails.</span></span> <span data-ttu-id="55e37-107">相同的更改还通过 Windows 安全汇总应用于 .NET Framework 3.5 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="55e37-107">The same change was also made to .NET Framework 3.5 and later versions via Windows security roll-up.</span></span> <span data-ttu-id="55e37-108">可在[此处](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7)了解详细信息。此更改默认开启，可通过配置设置关闭。</span><span class="sxs-lookup"><span data-stu-id="55e37-108">You can find more information [here](https://support.microsoft.com/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7).This change is on by default and can be turned off by a configuration setting.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="55e37-109">建议</span><span class="sxs-lookup"><span data-stu-id="55e37-109">Suggestion</span></span>

<ul><li><span data-ttu-id="55e37-110">验证服务器和客户端证书是否具有所需的 EKU OID。</span><span class="sxs-lookup"><span data-stu-id="55e37-110">Validate if your server and client certification has the required EKU OID.</span></span> <span data-ttu-id="55e37-111">如果没有，请更新证书。</span><span class="sxs-lookup"><span data-stu-id="55e37-111">If not, update your certification.</span></span></li><li><span data-ttu-id="55e37-112">验证根证书是否无效。</span><span class="sxs-lookup"><span data-stu-id="55e37-112">Validate if your root certificate is invalid.</span></span> <span data-ttu-id="55e37-113">如果是这样，请更新根证书。</span><span class="sxs-lookup"><span data-stu-id="55e37-113">If so, update the root certificate.</span></span></li><li><span data-ttu-id="55e37-114">如何选择退出更改：如果不能更新证书，可以暂时使用以下配置设置来躲开重大更改。但是，选择弃用更改将导致系统易遭受安全性问题。</span><span class="sxs-lookup"><span data-stu-id="55e37-114">How to opt out of the change: If you can't update the certificate, you can work around the breaking change temporarily with the following configration setting,  However, opting out of the change will leave your system vulnerable to the security issue.</span></span></li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="55e37-115">“属性”</span><span class="sxs-lookup"><span data-stu-id="55e37-115">Name</span></span>    | <span data-ttu-id="55e37-116">“值”</span><span class="sxs-lookup"><span data-stu-id="55e37-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="55e37-117">范围</span><span class="sxs-lookup"><span data-stu-id="55e37-117">Scope</span></span>   |<span data-ttu-id="55e37-118">次要</span><span class="sxs-lookup"><span data-stu-id="55e37-118">Minor</span></span>|
|<span data-ttu-id="55e37-119">版本</span><span class="sxs-lookup"><span data-stu-id="55e37-119">Version</span></span>|<span data-ttu-id="55e37-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="55e37-120">4.7.2</span></span>|
|<span data-ttu-id="55e37-121">类型</span><span class="sxs-lookup"><span data-stu-id="55e37-121">Type</span></span>|<span data-ttu-id="55e37-122">运行时</span><span class="sxs-lookup"><span data-stu-id="55e37-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="55e37-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="55e37-123">Affected APIs</span></span>

<span data-ttu-id="55e37-124">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="55e37-124">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
