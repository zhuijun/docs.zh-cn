---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721042"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="8ecd2-101">已考虑 SignedCms.ComputeSignature 的布尔参数</span><span class="sxs-lookup"><span data-stu-id="8ecd2-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="8ecd2-102">在 .NET Core 中，已考虑 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 方法的布尔 `silent` 参数。</span><span class="sxs-lookup"><span data-stu-id="8ecd2-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="8ecd2-103">如果将此参数设置为 `true`，则不会显示 PIN 提示。</span><span class="sxs-lookup"><span data-stu-id="8ecd2-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8ecd2-104">更改描述</span><span class="sxs-lookup"><span data-stu-id="8ecd2-104">Change description</span></span>

<span data-ttu-id="8ecd2-105">在 .NET Framework 中，<xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 方法的 `silent` 参数将被忽略，并且如果提供程序要求，则始终会显示 PIN 提示。</span><span class="sxs-lookup"><span data-stu-id="8ecd2-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="8ecd2-106">在 .NET Core 中，已考虑 `silent` 参数，并且如果将其设置为 `true`，则即使提供程序要求也不会显示 PIN 提示。</span><span class="sxs-lookup"><span data-stu-id="8ecd2-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="8ecd2-107">在 2.1 版的 .NET Core 中引入了对 CMS/PKCS #7 消息的支持。</span><span class="sxs-lookup"><span data-stu-id="8ecd2-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8ecd2-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="8ecd2-108">Version introduced</span></span>

<span data-ttu-id="8ecd2-109">2.1</span><span class="sxs-lookup"><span data-stu-id="8ecd2-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8ecd2-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="8ecd2-110">Recommended action</span></span>

<span data-ttu-id="8ecd2-111">为了确保在需要时显示 PIN 提示，桌面应用程序应调用 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 并将 Boolean 参数设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="8ecd2-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="8ecd2-112">无论是否禁用了静默上下文，所产生的行为都与 .NET Framework 上的行为相同。</span><span class="sxs-lookup"><span data-stu-id="8ecd2-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

#### <a name="category"></a><span data-ttu-id="8ecd2-113">类别</span><span class="sxs-lookup"><span data-stu-id="8ecd2-113">Category</span></span>

<span data-ttu-id="8ecd2-114">密码</span><span class="sxs-lookup"><span data-stu-id="8ecd2-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8ecd2-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="8ecd2-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
