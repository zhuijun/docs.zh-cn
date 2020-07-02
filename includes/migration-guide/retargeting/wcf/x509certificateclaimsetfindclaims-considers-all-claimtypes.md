---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614355"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="cbd77-101">X509CertificateClaimSet.FindClaims 考虑到所有 claimTypes</span><span class="sxs-lookup"><span data-stu-id="cbd77-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

#### <a name="details"></a><span data-ttu-id="cbd77-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cbd77-102">Details</span></span>

<span data-ttu-id="cbd77-103">在面向 .NET Framework 4.6.1 的应用中，如果从 SAN 字段拥有多个 DNS 条目的证书初始化 X509 声明集，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> 方法会尝试将 claimType 自变量与所有 DNS 条目进行匹配。对于面向以前版本的 .NET Framework 的应用，<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> 方法会尝试仅将 claimType 自变量与最后一个 DNS 条目进行匹配。</span><span class="sxs-lookup"><span data-stu-id="cbd77-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument only with the last DNS entry.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cbd77-104">建议</span><span class="sxs-lookup"><span data-stu-id="cbd77-104">Suggestion</span></span>

<span data-ttu-id="cbd77-105">此更改仅影响面向 .NET Framework 4.6.1 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="cbd77-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="cbd77-106">在 [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) 兼容性开关中，可能会禁用此更改（如果面向 4.6.1 之前的版本，将启用此更改）。</span><span class="sxs-lookup"><span data-stu-id="cbd77-106">This change may be disabled (or enabled if targeting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="cbd77-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="cbd77-107">Name</span></span>    | <span data-ttu-id="cbd77-108">“值”</span><span class="sxs-lookup"><span data-stu-id="cbd77-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cbd77-109">范围</span><span class="sxs-lookup"><span data-stu-id="cbd77-109">Scope</span></span>   | <span data-ttu-id="cbd77-110">次要</span><span class="sxs-lookup"><span data-stu-id="cbd77-110">Minor</span></span>       |
| <span data-ttu-id="cbd77-111">Version</span><span class="sxs-lookup"><span data-stu-id="cbd77-111">Version</span></span> | <span data-ttu-id="cbd77-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="cbd77-112">4.6.1</span></span>       |
| <span data-ttu-id="cbd77-113">类型</span><span class="sxs-lookup"><span data-stu-id="cbd77-113">Type</span></span>    | <span data-ttu-id="cbd77-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="cbd77-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cbd77-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="cbd77-115">Affected APIs</span></span>

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
