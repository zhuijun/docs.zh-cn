---
ms.openlocfilehash: c1e85941c8c6c31c7d937d0671ad955fa6490783
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614327"
---
### <a name="rsacng-now-correctly-loads-rsa-keys-of-non-standard-key-size"></a><span data-ttu-id="297c1-101">RSACng 现在可正确加载非标准密钥大小的 RSA 密钥</span><span class="sxs-lookup"><span data-stu-id="297c1-101">RSACng now correctly loads RSA keys of non-standard key size</span></span>

#### <a name="details"></a><span data-ttu-id="297c1-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="297c1-102">Details</span></span>

<span data-ttu-id="297c1-103">在 .NET Framework 4.6.2 之前的版本中，使用非标准密钥大小的 RSA 证书的客户无法通过 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> 和 <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> 扩展方法访问这些密钥。</span><span class="sxs-lookup"><span data-stu-id="297c1-103">In .NET Framework versions prior to 4.6.2, customers with non-standard key sizes for RSA certificates are unable to access those keys via the <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> and <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=fullName> extension methods.</span></span>  <span data-ttu-id="297c1-104">引发 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>，并附带“不支持请求的密钥大小”消息。</span><span class="sxs-lookup"><span data-stu-id="297c1-104">A <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> with the message &quot;The requested key size is not supported&quot; is thrown.</span></span> <span data-ttu-id="297c1-105">.NET Framework 4.6.2 中已修复此问题。</span><span class="sxs-lookup"><span data-stu-id="297c1-105">In .NET Framework 4.6.2 this issue has been fixed.</span></span> <span data-ttu-id="297c1-106">同样，<xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> 和 <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> 现在可以处理非标准密钥大小，而不会引发 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="297c1-106">Similarly, <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)> and <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)> now work with non-standard key sizes without throwing a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="297c1-107">建议</span><span class="sxs-lookup"><span data-stu-id="297c1-107">Suggestion</span></span>

<span data-ttu-id="297c1-108">如果处理依赖于先前行为的逻辑时有任何异常 - 使用非标准密钥大小时引发 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>，请考虑删除该逻辑。</span><span class="sxs-lookup"><span data-stu-id="297c1-108">If there is any exception handling logic that relies on the previous behavior where a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> is thrown when non-standard key sizes are used, consider removing the logic.</span></span>

| <span data-ttu-id="297c1-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="297c1-109">Name</span></span>    | <span data-ttu-id="297c1-110">值</span><span class="sxs-lookup"><span data-stu-id="297c1-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="297c1-111">范围</span><span class="sxs-lookup"><span data-stu-id="297c1-111">Scope</span></span>   | <span data-ttu-id="297c1-112">边缘</span><span class="sxs-lookup"><span data-stu-id="297c1-112">Edge</span></span>        |
| <span data-ttu-id="297c1-113">Version</span><span class="sxs-lookup"><span data-stu-id="297c1-113">Version</span></span> | <span data-ttu-id="297c1-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="297c1-114">4.6.2</span></span>       |
| <span data-ttu-id="297c1-115">类型</span><span class="sxs-lookup"><span data-stu-id="297c1-115">Type</span></span>    | <span data-ttu-id="297c1-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="297c1-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="297c1-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="297c1-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.RSA.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACng.ImportParameters(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)?displayProperty=nameWithType>
