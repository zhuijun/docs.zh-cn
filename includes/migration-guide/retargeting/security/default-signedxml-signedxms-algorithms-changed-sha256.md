---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614379"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a><span data-ttu-id="d5089-101">默认的 SignedXML 和 SignedXMS 算法已更改为 SHA256</span><span class="sxs-lookup"><span data-stu-id="d5089-101">Default SignedXML and SignedXMS algorithms changed to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="d5089-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d5089-102">Details</span></span>

<span data-ttu-id="d5089-103">在 .NET Framework 4.7 及早期版本中，SignedXML 和 SignedCMS 默认为 SHA1 以执行某些操作。从 .NET Framework 4.7.1 开始，默认情况下启用 SHA256 来执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="d5089-103">In the .NET Framework 4.7 and earlier, SignedXML and SignedCMS default to SHA1 for some operations.Starting with the .NET Framework 4.7.1, SHA256 is enabled by default for these operations.</span></span> <span data-ttu-id="d5089-104">此更改是必需的，因为 SHA1 不再是安全的。</span><span class="sxs-lookup"><span data-stu-id="d5089-104">This change is necessary because SHA1 is no longer considered to be secure.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d5089-105">建议</span><span class="sxs-lookup"><span data-stu-id="d5089-105">Suggestion</span></span>

<span data-ttu-id="d5089-106">有两个新的上下文切换值，用于控制默认情况下使用 SHA1（不安全）还是 SHA256：</span><span class="sxs-lookup"><span data-stu-id="d5089-106">There are two new context switch values to control whether SHA1 (insecure) or SHA256 is used by default:</span></span>

- <span data-ttu-id="d5089-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span><span class="sxs-lookup"><span data-stu-id="d5089-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span></span>
- <span data-ttu-id="d5089-108">Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms 对于面向 .NET Framework 4.7.1 及更高版本的应用程序，如果不希望使用 SHA256，则可通过将以下配置开关添加到应用配置文件的[运行时](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)部分，将默认值还原为 SHA1：</span><span class="sxs-lookup"><span data-stu-id="d5089-108">Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms For applications that target the .NET Framework 4.7.1 and later versions, if the use of SHA256 is undesirable, you can restore the default to SHA1 by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

<span data-ttu-id="d5089-109">对于面向 .NET Framework 4.7 及更高版本的应用程序，可通过将以下配置开关添加到应用配置文件的[运行时](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)部分，来选择使用此更改：</span><span class="sxs-lookup"><span data-stu-id="d5089-109">For applications that target the .NET Framework 4.7 and earlier versions, you can opt into this change by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| <span data-ttu-id="d5089-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="d5089-110">Name</span></span>    | <span data-ttu-id="d5089-111">“值”</span><span class="sxs-lookup"><span data-stu-id="d5089-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d5089-112">范围</span><span class="sxs-lookup"><span data-stu-id="d5089-112">Scope</span></span>   | <span data-ttu-id="d5089-113">次要</span><span class="sxs-lookup"><span data-stu-id="d5089-113">Minor</span></span>       |
| <span data-ttu-id="d5089-114">Version</span><span class="sxs-lookup"><span data-stu-id="d5089-114">Version</span></span> | <span data-ttu-id="d5089-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="d5089-115">4.7.1</span></span>       |
| <span data-ttu-id="d5089-116">类型</span><span class="sxs-lookup"><span data-stu-id="d5089-116">Type</span></span>    | <span data-ttu-id="d5089-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="d5089-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d5089-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d5089-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
