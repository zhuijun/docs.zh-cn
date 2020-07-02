---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614354"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="11916-101">与 TransportWithMessageCredential 安全模式绑定的 WCF</span><span class="sxs-lookup"><span data-stu-id="11916-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

#### <a name="details"></a><span data-ttu-id="11916-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="11916-102">Details</span></span>

<span data-ttu-id="11916-103">从 .NET Framework 4.6.1 开始，可将使用 TransportWithMessageCredential 安全模式的 WCF 绑定设置为接收带有非对称安全密钥的未签名&quot;to&quot;标头的消息。默认情况下，.NET Framework 4.6.1 中将继续拒绝未签名&quot;to&quot;标头。</span><span class="sxs-lookup"><span data-stu-id="11916-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET Framework 4.6.1.</span></span> <span data-ttu-id="11916-104">仅当应用程序使用 Switch.System.ServiceModel.AllowUnsignedToHeader 配置开关选择启用此新操作模式时，才会接受它们。</span><span class="sxs-lookup"><span data-stu-id="11916-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="11916-105">建议</span><span class="sxs-lookup"><span data-stu-id="11916-105">Suggestion</span></span>

<span data-ttu-id="11916-106">由于这是一项可以选择使用的功能，因此它不应影响现有应用的行为。</span><span class="sxs-lookup"><span data-stu-id="11916-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span><br/><span data-ttu-id="11916-107">要控制是否使用新行为，请使用以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="11916-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| <span data-ttu-id="11916-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="11916-108">Name</span></span>    | <span data-ttu-id="11916-109">“值”</span><span class="sxs-lookup"><span data-stu-id="11916-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="11916-110">范围</span><span class="sxs-lookup"><span data-stu-id="11916-110">Scope</span></span>   | <span data-ttu-id="11916-111">透明</span><span class="sxs-lookup"><span data-stu-id="11916-111">Transparent</span></span> |
| <span data-ttu-id="11916-112">Version</span><span class="sxs-lookup"><span data-stu-id="11916-112">Version</span></span> | <span data-ttu-id="11916-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="11916-113">4.6.1</span></span>       |
| <span data-ttu-id="11916-114">类型</span><span class="sxs-lookup"><span data-stu-id="11916-114">Type</span></span>    | <span data-ttu-id="11916-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="11916-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="11916-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="11916-116">Affected APIs</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
