---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617785"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a><span data-ttu-id="f0a81-101">托管加密类不会在 FIPS 模式下引发 CryptographyException</span><span class="sxs-lookup"><span data-stu-id="f0a81-101">Managed cryptography classes do not throw a CryptographyException in FIPS mode</span></span>

#### <a name="details"></a><span data-ttu-id="f0a81-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f0a81-102">Details</span></span>

<span data-ttu-id="f0a81-103">在 .NET framework 4.7.2 及更低版本中，当在 FIPS 模式下配置系统加密库时，<xref:System.Security.Cryptography.SHA256Managed> 等托管加密提供程序类会引发 <xref:System.Security.Cryptography.CryptographicException>。</span><span class="sxs-lookup"><span data-stu-id="f0a81-103">In .NET Framework 4.7.2 and earlier versions, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in FIPS mode.</span></span> <span data-ttu-id="f0a81-104">引发这些异常的原因是托管版本未经过 FIPS（联邦信息处理标准）140-2 认证，以及没有阻止根据 FIPS 规则规定未被认可的加密算法。</span><span class="sxs-lookup"><span data-stu-id="f0a81-104">These exceptions are thrown because the managed versions have not undergone FIPS (Federal Information Processing Standards) 140-2 certification, as well as to block cryptographic algorithms that were not considered to be approved based on the FIPS rules.</span></span>  <span data-ttu-id="f0a81-105">由于很少有开发人员将其开发计算机置于 FIPS 模式下，因此这些异常通常仅在生产系统上引发。面向 .NET Framework 4.8 及更高版本的应用程序会自动切换到新的且宽松的策略，以便在这种情况下默认不再引发 <xref:System.Security.Cryptography.CryptographicException>。</span><span class="sxs-lookup"><span data-stu-id="f0a81-105">Because few developers have their development machines in FIPS mode, these exceptions are frequently thrown only on production systems.Applications that target .NET Framework 4.8 and later versions automatically switch to the newer, relaxed policy, so that a <xref:System.Security.Cryptography.CryptographicException> is no longer thrown by default in such cases.</span></span> <span data-ttu-id="f0a81-106">相反，托管加密类会将加密操作重定向到系统加密库。</span><span class="sxs-lookup"><span data-stu-id="f0a81-106">Instead, the managed cryptography classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="f0a81-107">此系统更改可有效地删除开发人员环境和生产环境之间可能令人混淆的差异，并使本机组件和托管组件采用相同的加密策略运行。</span><span class="sxs-lookup"><span data-stu-id="f0a81-107">This policy change effectively removes a potentially confusing difference between developer environments and the production environments and makes native components and managed components operate under the same cryptographic policy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f0a81-108">建议</span><span class="sxs-lookup"><span data-stu-id="f0a81-108">Suggestion</span></span>

<span data-ttu-id="f0a81-109">如果不希望出现这种情况，可以选择退出该行为并还原上述行为，方法是将以下 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 配置设置添加到应用程序配置文件的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分中，以便在 FIPS 模式下引发 <xref:System.Security.Cryptography.CryptographicException>：</span><span class="sxs-lookup"><span data-stu-id="f0a81-109">If this behavior is undesirable, you can opt out of it and restore the previous behavior so that a <xref:System.Security.Cryptography.CryptographicException> is thrown in FIPS mode by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

<span data-ttu-id="f0a81-110">如果应用程序面向 .NET Framework 4.7.2 或更低版本，则也可以通过将以下 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 配置设置添加到应用程序配置文件的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分来选择加入此更改：</span><span class="sxs-lookup"><span data-stu-id="f0a81-110">If your application targets .NET Framework 4.7.2 or earlier, you can also opt in to this change by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| <span data-ttu-id="f0a81-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="f0a81-111">Name</span></span>    | <span data-ttu-id="f0a81-112">“值”</span><span class="sxs-lookup"><span data-stu-id="f0a81-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f0a81-113">范围</span><span class="sxs-lookup"><span data-stu-id="f0a81-113">Scope</span></span>   | <span data-ttu-id="f0a81-114">边缘</span><span class="sxs-lookup"><span data-stu-id="f0a81-114">Edge</span></span>        |
| <span data-ttu-id="f0a81-115">Version</span><span class="sxs-lookup"><span data-stu-id="f0a81-115">Version</span></span> | <span data-ttu-id="f0a81-116">4.8</span><span class="sxs-lookup"><span data-stu-id="f0a81-116">4.8</span></span>         |
| <span data-ttu-id="f0a81-117">类型</span><span class="sxs-lookup"><span data-stu-id="f0a81-117">Type</span></span>    | <span data-ttu-id="f0a81-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="f0a81-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f0a81-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f0a81-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
