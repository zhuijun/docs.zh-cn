---
ms.openlocfilehash: e0cdcce9b8c7d591925b08635e3354dadaf22b7b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556017"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="7c6df-101">EnvelopedCms 默认为 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="7c6df-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="7c6df-102">`EnvelopedCms` 使用的默认对称加密算法已由 TripleDES 改为 AES-256。</span><span class="sxs-lookup"><span data-stu-id="7c6df-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7c6df-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="7c6df-103">Change description</span></span>

<span data-ttu-id="7c6df-104">在以前的版本中，如果 <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> 用于对数据加密但未通过构造函数重载指定对称加密算法，则使用 TripleDES/3DES/3DEA/DES3-EDE 算法对数据加密。</span><span class="sxs-lookup"><span data-stu-id="7c6df-104">In previous versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data is encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="7c6df-105">从 .NET Core 3.0 开始（通过 [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet 包的 4.6.0 版本），默认算法已改为 AES-256 以实现算法现代化并提高默认选项的安全性。</span><span class="sxs-lookup"><span data-stu-id="7c6df-105">Starting with .NET Core 3.0 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="7c6df-106">如果消息收件人证书具有（非 EC）Diffie-Hellman 公钥，则由于底层平台的限制，加密操作可能会失败并显示 <xref:System.Security.Cryptography.CryptographicException>。</span><span class="sxs-lookup"><span data-stu-id="7c6df-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="7c6df-107">在下面的示例代码中，如果在 .NET Core 2.2 或更早版本上运行，则使用 TripleDES 对数据加密。</span><span class="sxs-lookup"><span data-stu-id="7c6df-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 2.2 or earlier.</span></span> <span data-ttu-id="7c6df-108">如果在.NET Core 3.0 或更高版本上运行，则使用 AES-256 对数据加密。</span><span class="sxs-lookup"><span data-stu-id="7c6df-108">If running on .NET Core 3.0 or later, it's encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="7c6df-109">引入的版本</span><span class="sxs-lookup"><span data-stu-id="7c6df-109">Version introduced</span></span>

<span data-ttu-id="7c6df-110">3.0</span><span class="sxs-lookup"><span data-stu-id="7c6df-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7c6df-111">建议操作</span><span class="sxs-lookup"><span data-stu-id="7c6df-111">Recommended action</span></span>

<span data-ttu-id="7c6df-112">如果该更改有负面影响，则可以通过在包含 <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> 类型参数的 <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> 构造函数中显式指定加密算法标识符来还原 TripleDES 加密，例如：</span><span class="sxs-lookup"><span data-stu-id="7c6df-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="7c6df-113">类别</span><span class="sxs-lookup"><span data-stu-id="7c6df-113">Category</span></span>

<span data-ttu-id="7c6df-114">密码</span><span class="sxs-lookup"><span data-stu-id="7c6df-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7c6df-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="7c6df-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
