---
ms.openlocfilehash: 3d94023fc508a56304587121c6cf1444c87b0d52
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721306"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="cabf9-101">RSAOpenSsl 密钥生成的最小大小已增加</span><span class="sxs-lookup"><span data-stu-id="cabf9-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="cabf9-102">在 Linux 上生成新 RSA 密钥的最小大小已从 384 位提高到 512 位。</span><span class="sxs-lookup"><span data-stu-id="cabf9-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cabf9-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="cabf9-103">Change description</span></span>

<span data-ttu-id="cabf9-104">自 .NET Core 3.0 起，Linux 上 <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType><xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A> 和 <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> 中 RSA 实例上的 `LegalKeySizes` 属性报告的最低合法密钥大小已从 384 增加到 512。</span><span class="sxs-lookup"><span data-stu-id="cabf9-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="cabf9-105">因此，在 .NET Core 2.2 及更早版本中，方法调用（如 `RSA.Create(384)`）会成功。</span><span class="sxs-lookup"><span data-stu-id="cabf9-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="cabf9-106">在 .NET Core 3.0 及更高版本中，方法调用 `RSA.Create(384)` 会引发异常，指示大小太小。</span><span class="sxs-lookup"><span data-stu-id="cabf9-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="cabf9-107">此更改是因为在 Linux 上执行加密操作的 OpenSSL 在版本 1.0.2 与 1.1.0 之间提高了其最小值。</span><span class="sxs-lookup"><span data-stu-id="cabf9-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="cabf9-108">.NET Core 3.0 倾向于使用 OpenSSL 1.1.x 而不是 1.0.x，并提高了最小报告版本来反映这一新的更高的依赖项限制。</span><span class="sxs-lookup"><span data-stu-id="cabf9-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cabf9-109">引入的版本</span><span class="sxs-lookup"><span data-stu-id="cabf9-109">Version introduced</span></span>

<span data-ttu-id="cabf9-110">3.0</span><span class="sxs-lookup"><span data-stu-id="cabf9-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cabf9-111">建议操作</span><span class="sxs-lookup"><span data-stu-id="cabf9-111">Recommended action</span></span>

<span data-ttu-id="cabf9-112">如果调用任何受影响的 API，请确保所有生成的密钥的大小不小于提供程序的最小值。</span><span class="sxs-lookup"><span data-stu-id="cabf9-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="cabf9-113">384 位 RSA 已被视为不安全（512 位 RSA 也是如此）。</span><span class="sxs-lookup"><span data-stu-id="cabf9-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="cabf9-114">新式建议（例如 [NIST 特别出版物 800-57 第 1 部分修订版 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)）建议将 2048 位作为新生成的密钥的最小大小。</span><span class="sxs-lookup"><span data-stu-id="cabf9-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="cabf9-115">类别</span><span class="sxs-lookup"><span data-stu-id="cabf9-115">Category</span></span>

<span data-ttu-id="cabf9-116">密码</span><span class="sxs-lookup"><span data-stu-id="cabf9-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cabf9-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="cabf9-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
#### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
