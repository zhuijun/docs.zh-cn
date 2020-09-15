---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616026"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a><span data-ttu-id="90182-101">SignedXml.GetPublicKey 在 net462（或 lightup）上返回 RSACng 而不重定向更改</span><span class="sxs-lookup"><span data-stu-id="90182-101">SignedXml.GetPublicKey returns RSACng on net462 (or lightup) without retargeting change</span></span>

#### <a name="details"></a><span data-ttu-id="90182-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="90182-102">Details</span></span>

<span data-ttu-id="90182-103">从 .NET Framework 4.6.2 开始，<xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> 方法所返回对象的具体类型从 CryptoServiceProvider 实现更改为 Cng 实现（不奇怪）。</span><span class="sxs-lookup"><span data-stu-id="90182-103">Starting with the .NET Framework 4.6.2, the concrete type of the object returned by the <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> method changed (without a quirk) from a CryptoServiceProvider implementation to a Cng implementation.</span></span> <span data-ttu-id="90182-104">这是因为实现已从使用 `certificate.PublicKey.Key` 更改为使用内部 `certificate.GetAnyPublicKey`（将转到 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>）。</span><span class="sxs-lookup"><span data-stu-id="90182-104">This is because the implementation changed from using `certificate.PublicKey.Key` to using the internal `certificate.GetAnyPublicKey` which forwards to <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="90182-105">建议</span><span class="sxs-lookup"><span data-stu-id="90182-105">Suggestion</span></span>

<span data-ttu-id="90182-106">从在 .NET Framework 4.7.1 上运行的应用开始，可通过将以下配置开关添加到应用配置文件的[运行时](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)部分，使用 .NET Framework 4.6.1 和早期版本中默认使用的 CryptoServiceProvider 实现：</span><span class="sxs-lookup"><span data-stu-id="90182-106">Starting with apps running on the .NET Framework 4.7.1, you can use the CryptoServiceProvider implementation used by default in the .NET Framework 4.6.1 and earlier versions by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| <span data-ttu-id="90182-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="90182-107">Name</span></span>    | <span data-ttu-id="90182-108">“值”</span><span class="sxs-lookup"><span data-stu-id="90182-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="90182-109">范围</span><span class="sxs-lookup"><span data-stu-id="90182-109">Scope</span></span>   | <span data-ttu-id="90182-110">边缘</span><span class="sxs-lookup"><span data-stu-id="90182-110">Edge</span></span>        |
| <span data-ttu-id="90182-111">Version</span><span class="sxs-lookup"><span data-stu-id="90182-111">Version</span></span> | <span data-ttu-id="90182-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="90182-112">4.6.2</span></span>       |
| <span data-ttu-id="90182-113">类型</span><span class="sxs-lookup"><span data-stu-id="90182-113">Type</span></span>    | <span data-ttu-id="90182-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="90182-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="90182-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="90182-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
