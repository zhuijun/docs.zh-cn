---
ms.openlocfilehash: c967a5b09b5e9ffeee7bff046f0c96469bc7fb02
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615604"
---
### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a><span data-ttu-id="c97d2-101">ClickOnce 支持面向 4.0 的应用上的 SHA-256</span><span class="sxs-lookup"><span data-stu-id="c97d2-101">ClickOnce supports SHA-256 on 4.0-targeted apps</span></span>

#### <a name="details"></a><span data-ttu-id="c97d2-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c97d2-102">Details</span></span>

<span data-ttu-id="c97d2-103">以前，如果 ClickOnce 应用具有使用 SHA-256 签名的证书，即使应用面向 4.0 版本，也需要 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="c97d2-103">Previously, a ClickOnce app with a certificate signed with SHA-256 would require .NET Framework 4.5 or later to be present, even if the app targeted 4.0.</span></span> <span data-ttu-id="c97d2-104">现在，即使使用 SHA-256 签名，面向 .NET Framework 4.0 的 ClickOnce 应用也可在 .NET Framework 4.0 上运行。</span><span class="sxs-lookup"><span data-stu-id="c97d2-104">Now, .NET Framework 4.0-targeted ClickOnce apps can run on .NET Framework 4.0, even if signed with SHA-256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c97d2-105">建议</span><span class="sxs-lookup"><span data-stu-id="c97d2-105">Suggestion</span></span>

<span data-ttu-id="c97d2-106">此更改删除了该依赖项，允许将 SHA-256 证书用于为面向 .NET Framework 4 或更早版本的 ClickOnce 应用签名。</span><span class="sxs-lookup"><span data-stu-id="c97d2-106">This change removes that dependency and allows SHA-256 certificates to be used to sign ClickOnce apps that target .NET Framework 4 and earlier versions.</span></span>

| <span data-ttu-id="c97d2-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="c97d2-107">Name</span></span>    | <span data-ttu-id="c97d2-108">“值”</span><span class="sxs-lookup"><span data-stu-id="c97d2-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c97d2-109">范围</span><span class="sxs-lookup"><span data-stu-id="c97d2-109">Scope</span></span>   | <span data-ttu-id="c97d2-110">次要</span><span class="sxs-lookup"><span data-stu-id="c97d2-110">Minor</span></span>       |
| <span data-ttu-id="c97d2-111">Version</span><span class="sxs-lookup"><span data-stu-id="c97d2-111">Version</span></span> | <span data-ttu-id="c97d2-112">4.6</span><span class="sxs-lookup"><span data-stu-id="c97d2-112">4.6</span></span>         |
| <span data-ttu-id="c97d2-113">类型</span><span class="sxs-lookup"><span data-stu-id="c97d2-113">Type</span></span>    | <span data-ttu-id="c97d2-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="c97d2-114">Retargeting</span></span> |
