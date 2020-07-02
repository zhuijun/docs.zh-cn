---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614378"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="d3ae5-101">现在，WCF 消息安全性能够使用 TLS1.1 和 TLS1.2</span><span class="sxs-lookup"><span data-stu-id="d3ae5-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

#### <a name="details"></a><span data-ttu-id="d3ae5-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d3ae5-102">Details</span></span>

<span data-ttu-id="d3ae5-103">从 .NET Framework 4.7 开始，除 SSL3.0 和 TLS1.0 之外，客户还可通过应用程序配置设置在 WCF 消息安全性中配置 TLS1.1 或 TLS1.2。</span><span class="sxs-lookup"><span data-stu-id="d3ae5-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d3ae5-104">建议</span><span class="sxs-lookup"><span data-stu-id="d3ae5-104">Suggestion</span></span>

<span data-ttu-id="d3ae5-105">在 .NET Framework 4.7 中，默认情况下禁用 WCF 消息安全性中对 TLS1.1 和 TLS1.2 的支持。</span><span class="sxs-lookup"><span data-stu-id="d3ae5-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="d3ae5-106">可通过将以下行添加到 app.config 或 web.config 文件的 `<runtime>` 部分来启用支持：</span><span class="sxs-lookup"><span data-stu-id="d3ae5-106">You can enable it by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| <span data-ttu-id="d3ae5-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="d3ae5-107">Name</span></span>    | <span data-ttu-id="d3ae5-108">值</span><span class="sxs-lookup"><span data-stu-id="d3ae5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d3ae5-109">范围</span><span class="sxs-lookup"><span data-stu-id="d3ae5-109">Scope</span></span>   | <span data-ttu-id="d3ae5-110">边缘</span><span class="sxs-lookup"><span data-stu-id="d3ae5-110">Edge</span></span>        |
| <span data-ttu-id="d3ae5-111">Version</span><span class="sxs-lookup"><span data-stu-id="d3ae5-111">Version</span></span> | <span data-ttu-id="d3ae5-112">4.7</span><span class="sxs-lookup"><span data-stu-id="d3ae5-112">4.7</span></span>         |
| <span data-ttu-id="d3ae5-113">类型</span><span class="sxs-lookup"><span data-stu-id="d3ae5-113">Type</span></span>    | <span data-ttu-id="d3ae5-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="d3ae5-114">Retargeting</span></span> |
