---
ms.openlocfilehash: 877f9d99b660c4af843e4d8d525219c1df6c99a9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720913"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="7c6ba-101">.NET Core 3.0 倾向于使用 OpenSSL 1.1.x 而不是 OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="7c6ba-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="7c6ba-102">跨多个 Linux 分发工作的适用于 Linux 的 .NET Core 可同时支持 OpenSSL 1.0.x 和 OpenSSL 1.1.x。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="7c6ba-103">.NET Core 2.1 和 .NET Core 2.2 首先查找 1.0.x，然后回退到 1.1.x；.NET Core 3.0 首先查找 1.1.x。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="7c6ba-104">进行此更改是为了增加对新加密标准的支持。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="7c6ba-105">此更改可能会影响库或应用程序，这些库或应用程序与 .NET Core 中的 OpenSSL 特定互操作类型进行平台互操作。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7c6ba-106">更改描述</span><span class="sxs-lookup"><span data-stu-id="7c6ba-106">Change description</span></span>

<span data-ttu-id="7c6ba-107">在 .NET Core 2.2 及更早版本中，运行时倾向于加载 OpenSSL 1.0.x 而不是加载 1.1.x。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="7c6ba-108">这意味着，与 OpenSSL 互操作的 <xref:System.IntPtr> 和 <xref:System.Runtime.InteropServices.SafeHandle> 类型倾向于与 libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 一起使用。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="7c6ba-109">从 .NET Core 3.0 开始，运行时倾向于加载 OpenSSL 1.1.x 而不是 OpenSSL 1.0.x，因此与 OpenSSL 互操作的 <xref:System.IntPtr> 和 <xref:System.Runtime.InteropServices.SafeHandle> 类型倾向于与 libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 一起使用。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="7c6ba-110">因此，从 .NET Core 2.1 或 .NET Core 2.2 升级时，与 OpenSSL 直接互操作的库和应用程序的指针可能与 .NET Core 公开的值不兼容。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7c6ba-111">引入的版本</span><span class="sxs-lookup"><span data-stu-id="7c6ba-111">Version introduced</span></span>

<span data-ttu-id="7c6ba-112">3.0</span><span class="sxs-lookup"><span data-stu-id="7c6ba-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7c6ba-113">建议操作</span><span class="sxs-lookup"><span data-stu-id="7c6ba-113">Recommended action</span></span>

<span data-ttu-id="7c6ba-114">需要小心使用直接与 OpenSSL 操作的库和应用程序，确保它们使用的 OpenSSL 版本与 .NET Core 运行时相同。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="7c6ba-115">所有将 .NET Core 加密类型中的 <xref:System.IntPtr> 或 <xref:System.Runtime.InteropServices.SafeHandle> 值直接用于 OpenSSL 的库或应用程序都应当将其使用的库的版本与新的 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 属性进行比较，以确保指针兼容。</span><span class="sxs-lookup"><span data-stu-id="7c6ba-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="7c6ba-116">类别</span><span class="sxs-lookup"><span data-stu-id="7c6ba-116">Category</span></span>

<span data-ttu-id="7c6ba-117">密码</span><span class="sxs-lookup"><span data-stu-id="7c6ba-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7c6ba-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="7c6ba-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
