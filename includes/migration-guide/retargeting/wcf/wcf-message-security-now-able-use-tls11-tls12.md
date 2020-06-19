---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859067"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="01285-101">现在，WCF 消息安全性能够使用 TLS1.1 和 TLS1.2</span><span class="sxs-lookup"><span data-stu-id="01285-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="01285-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="01285-102">Details</span></span>|<span data-ttu-id="01285-103">从 .NET Framework 4.7 开始，除 SSL3.0 和 TLS1.0 之外，客户还可通过应用程序配置设置在 WCF 消息安全性中配置 TLS1.1 或 TLS1.2。</span><span class="sxs-lookup"><span data-stu-id="01285-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="01285-104">建议</span><span class="sxs-lookup"><span data-stu-id="01285-104">Suggestion</span></span>|<span data-ttu-id="01285-105">在 .NET Framework 4.7 中，默认情况下禁用 WCF 消息安全性中对 TLS1.1 和 TLS1.2 的支持。</span><span class="sxs-lookup"><span data-stu-id="01285-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="01285-106">可通过将以下行添加到 app.config 或 web.config 文件的 <code>&lt;runtime&gt;</code> 部分来启用支持：</span><span class="sxs-lookup"><span data-stu-id="01285-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="01285-107">范围</span><span class="sxs-lookup"><span data-stu-id="01285-107">Scope</span></span>|<span data-ttu-id="01285-108">边缘</span><span class="sxs-lookup"><span data-stu-id="01285-108">Edge</span></span>|
|<span data-ttu-id="01285-109">Version</span><span class="sxs-lookup"><span data-stu-id="01285-109">Version</span></span>|<span data-ttu-id="01285-110">4.7</span><span class="sxs-lookup"><span data-stu-id="01285-110">4.7</span></span>|
|<span data-ttu-id="01285-111">类型</span><span class="sxs-lookup"><span data-stu-id="01285-111">Type</span></span>|<span data-ttu-id="01285-112">重定目标</span><span class="sxs-lookup"><span data-stu-id="01285-112">Retargeting</span></span>|
