---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614330"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a><span data-ttu-id="dfea7-101">AesCryptoServiceProvider 解密器提供了可重用的转换</span><span class="sxs-lookup"><span data-stu-id="dfea7-101">AesCryptoServiceProvider decryptor provides a reusable transform</span></span>

#### <a name="details"></a><span data-ttu-id="dfea7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="dfea7-102">Details</span></span>

<span data-ttu-id="dfea7-103">从面向 .NET Framework 4.6.2 的应用起，<xref:System.Security.Cryptography.AesCryptoServiceProvider> 解密器提供了可重用的转换。</span><span class="sxs-lookup"><span data-stu-id="dfea7-103">Starting with apps that target the .NET Framework 4.6.2, the <xref:System.Security.Cryptography.AesCryptoServiceProvider> decryptor provides a reusable transform.</span></span> <span data-ttu-id="dfea7-104">调用 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> 后，此转换将重新初始化并且可以重用。</span><span class="sxs-lookup"><span data-stu-id="dfea7-104">After a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, the transform is reinitialized and can be reused.</span></span> <span data-ttu-id="dfea7-105">对于面向旧版 .NET Framework 的应用，在调用 <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> 后尝试通过调用 <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> 重用解密器会引发 <xref:System.Security.Cryptography.CryptographicException> 或导致数据损坏。</span><span class="sxs-lookup"><span data-stu-id="dfea7-105">For apps that target earlier versions of the .NET Framework, attempting to reuse the decryptor by calling <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> after a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> throws a <xref:System.Security.Cryptography.CryptographicException> or produces corrupted data.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dfea7-106">建议</span><span class="sxs-lookup"><span data-stu-id="dfea7-106">Suggestion</span></span>

<span data-ttu-id="dfea7-107">此更改的影响应该很小，因为这是预期的行为。对于依赖旧行为的应用程序，可通过将以下配置设置添加到应用程序配置文件的 `<runtime>` 部分中，从而选择不用此更改：</span><span class="sxs-lookup"><span data-stu-id="dfea7-107">The impact of this change should be minimal, since this is the expected behavior.Applications that depend on the previous behavior can opt out of it using it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

<span data-ttu-id="dfea7-108">此外，对于面向旧版 .NET framework，但在 .NET Framework 4.6.2 及更高版本下运行的应用程序，可通过将以下配置设置添加到应用程序配置文件的 `<runtime>` 部分，从而选择应用此更改：</span><span class="sxs-lookup"><span data-stu-id="dfea7-108">In addition, applications that target a previous version of the .NET Framework but are running under a version of the .NET Framework starting with .NET Framework 4.6.2 can opt in to it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| <span data-ttu-id="dfea7-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="dfea7-109">Name</span></span>    | <span data-ttu-id="dfea7-110">值</span><span class="sxs-lookup"><span data-stu-id="dfea7-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dfea7-111">范围</span><span class="sxs-lookup"><span data-stu-id="dfea7-111">Scope</span></span>   | <span data-ttu-id="dfea7-112">次要</span><span class="sxs-lookup"><span data-stu-id="dfea7-112">Minor</span></span>       |
| <span data-ttu-id="dfea7-113">Version</span><span class="sxs-lookup"><span data-stu-id="dfea7-113">Version</span></span> | <span data-ttu-id="dfea7-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="dfea7-114">4.6.2</span></span>       |
| <span data-ttu-id="dfea7-115">类型</span><span class="sxs-lookup"><span data-stu-id="dfea7-115">Type</span></span>    | <span data-ttu-id="dfea7-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="dfea7-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="dfea7-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="dfea7-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
