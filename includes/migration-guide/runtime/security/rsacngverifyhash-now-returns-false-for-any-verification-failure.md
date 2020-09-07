---
ms.openlocfilehash: b7b16e39fa5df9732fa769f2bcd3696dff3b2a49
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497815"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="438fc-101">RSACng.VerifyHash 现在为任意验证失败返回 False</span><span class="sxs-lookup"><span data-stu-id="438fc-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

#### <a name="details"></a><span data-ttu-id="438fc-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="438fc-102">Details</span></span>

<span data-ttu-id="438fc-103">自 .NET Framework 4.6.2 起，如果签名本身格式不正确，则此方法返回 False  。</span><span class="sxs-lookup"><span data-stu-id="438fc-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="438fc-104">现在为任意验证失败返回 false。在 .NET Framework 4.6 和 4.6.1 中，如果签名格式错误，则此方法引发 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="438fc-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> if the signature itself is badly formatted.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="438fc-105">建议</span><span class="sxs-lookup"><span data-stu-id="438fc-105">Suggestion</span></span>

<span data-ttu-id="438fc-106">如果验证失败且此方法返回 False，应改为执行依赖处理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> 而实现执行的任意代码。</span><span class="sxs-lookup"><span data-stu-id="438fc-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> should instead execute if validation fails and the method returns **False**.</span></span>

| <span data-ttu-id="438fc-107">名称</span><span class="sxs-lookup"><span data-stu-id="438fc-107">Name</span></span>    | <span data-ttu-id="438fc-108">值</span><span class="sxs-lookup"><span data-stu-id="438fc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="438fc-109">范围</span><span class="sxs-lookup"><span data-stu-id="438fc-109">Scope</span></span>   |<span data-ttu-id="438fc-110">次要</span><span class="sxs-lookup"><span data-stu-id="438fc-110">Minor</span></span>|
|<span data-ttu-id="438fc-111">Version</span><span class="sxs-lookup"><span data-stu-id="438fc-111">Version</span></span>|<span data-ttu-id="438fc-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="438fc-112">4.6.2</span></span>|
|<span data-ttu-id="438fc-113">类型</span><span class="sxs-lookup"><span data-stu-id="438fc-113">Type</span></span>|<span data-ttu-id="438fc-114">运行时</span><span class="sxs-lookup"><span data-stu-id="438fc-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="438fc-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="438fc-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
