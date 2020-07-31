---
title: 缓解：X509CertificateClaimSet.FindClaims 方法
description: 了解 X509CertificateClaimSet.FindClaims 方法自面向 .NET Framework 4.6.1 的应用起有何变化。
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 304d8fb5adc27b33f2410faaaf8662e0ff9be66d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475315"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="c7f3b-103">缓解：X509CertificateClaimSet.FindClaims 方法</span><span class="sxs-lookup"><span data-stu-id="c7f3b-103">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="c7f3b-104">从面向 .NET Framework 4.6.1 的应用开始，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法尝试将 `claimType` 参数与其 SAN 字段中的所有 DNS 条目进行匹配。</span><span class="sxs-lookup"><span data-stu-id="c7f3b-104">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c7f3b-105">影响</span><span class="sxs-lookup"><span data-stu-id="c7f3b-105">Impact</span></span>  
 <span data-ttu-id="c7f3b-106">此更改仅影响面向从 .NET Framework 4.6.1 开始的 .NET Framework 版本的应用。</span><span class="sxs-lookup"><span data-stu-id="c7f3b-106">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="c7f3b-107">对于面向 .NET Framework 先前版本的应用，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> 方法尝试仅将 `claimType` 参数与最后一个 DNS 条目进行匹配。</span><span class="sxs-lookup"><span data-stu-id="c7f3b-107">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c7f3b-108">缓解</span><span class="sxs-lookup"><span data-stu-id="c7f3b-108">Mitigation</span></span>  
 <span data-ttu-id="c7f3b-109">如果此更改不可取，则面向从 .NET Framework 4.6.1 开始的 .NET Framework 版本的应用可通过将以下配置设置添加到应用配置文件的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 部分，来选择放弃更改：</span><span class="sxs-lookup"><span data-stu-id="c7f3b-109">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="c7f3b-110">此外，面向 .NET Framework 以前版本但在 .NET Framework 4.6.1 和更高版本下运行的应用可通过将以下配置设置添加到应用配置文件的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 部分，来选择实现此行为：</span><span class="sxs-lookup"><span data-stu-id="c7f3b-110">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7f3b-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c7f3b-111">See also</span></span>

- [<span data-ttu-id="c7f3b-112">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="c7f3b-112">Application compatibility</span></span>](application-compatibility.md)
