---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617120"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a><span data-ttu-id="ebe79-101">MachineKey.Encode 和 MachineKey.Decode 方法现已过时</span><span class="sxs-lookup"><span data-stu-id="ebe79-101">MachineKey.Encode and MachineKey.Decode methods are now obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="ebe79-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ebe79-102">Details</span></span>

<span data-ttu-id="ebe79-103">这些方法现在已过时。</span><span class="sxs-lookup"><span data-stu-id="ebe79-103">These methods are now obsolete.</span></span> <span data-ttu-id="ebe79-104">调用这些方法的代码编译会产生编译器警告。</span><span class="sxs-lookup"><span data-stu-id="ebe79-104">Compilation of code that calls these methods produces a compiler warning.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ebe79-105">建议</span><span class="sxs-lookup"><span data-stu-id="ebe79-105">Suggestion</span></span>

<span data-ttu-id="ebe79-106">建议的替代项为 <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> 和 <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>。</span><span class="sxs-lookup"><span data-stu-id="ebe79-106">The recommended alternatives are <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> and <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>.</span></span> <span data-ttu-id="ebe79-107">或者，可以禁止显示生成警告，也可以使用较早的编译器避免出现此类警告。</span><span class="sxs-lookup"><span data-stu-id="ebe79-107">Alternatively, the build warnings can be suppressed, or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="ebe79-108">API 仍受支持。</span><span class="sxs-lookup"><span data-stu-id="ebe79-108">The APIs are still supported.</span></span>

| <span data-ttu-id="ebe79-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="ebe79-109">Name</span></span>    | <span data-ttu-id="ebe79-110">“值”</span><span class="sxs-lookup"><span data-stu-id="ebe79-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ebe79-111">范围</span><span class="sxs-lookup"><span data-stu-id="ebe79-111">Scope</span></span>   | <span data-ttu-id="ebe79-112">次要</span><span class="sxs-lookup"><span data-stu-id="ebe79-112">Minor</span></span>       |
| <span data-ttu-id="ebe79-113">Version</span><span class="sxs-lookup"><span data-stu-id="ebe79-113">Version</span></span> | <span data-ttu-id="ebe79-114">4.5</span><span class="sxs-lookup"><span data-stu-id="ebe79-114">4.5</span></span>         |
| <span data-ttu-id="ebe79-115">类型</span><span class="sxs-lookup"><span data-stu-id="ebe79-115">Type</span></span>    | <span data-ttu-id="ebe79-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="ebe79-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ebe79-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ebe79-117">Affected APIs</span></span>

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
