---
title: 危险权限和策略管理
description: 请参阅 .NET 中各种危险权限的链接。 这些权限只能提供给可信代码，并且仅在必要时才提供。
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: 1d3fb53775a4d88f9372b582189a38e18376761a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855811"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="fa8a0-104">危险权限和策略管理</span><span class="sxs-lookup"><span data-stu-id="fa8a0-104">Dangerous Permissions and Policy Administration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="fa8a0-105">.NET Framework 为其提供权限的多个受保护的操作可能允许绕过安全系统。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-105">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="fa8a0-106">应仅对可信的代码，并且仅在必要的时候授予这些危险的权限。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-106">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="fa8a0-107">如果它被授予这些权限，通常会对恶意代码没有任何防范。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-107">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa8a0-108">在 .NET Framework 4 中，对 .NET Framework 安全模型和术语进行了重大更改。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-108">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="fa8a0-109">有关这些更改的详细信息，请参阅[安全更改](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-109">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="fa8a0-110">下表介绍了危险权限。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-110">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="fa8a0-111">权限</span><span class="sxs-lookup"><span data-stu-id="fa8a0-111">Permission</span></span>|<span data-ttu-id="fa8a0-112">潜在的风险</span><span class="sxs-lookup"><span data-stu-id="fa8a0-112">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="fa8a0-113">允许托管代码调用到非托管代码中，常常是很危险的。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-113">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="fa8a0-114">如果没有验证，代码可以执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-114">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="fa8a0-115">无效证据可以欺骗安全策略。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-115">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="fa8a0-116">修改安全策略的功能可以禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-116">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="fa8a0-117">序列化的使用可以避开可访问性机制。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-117">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="fa8a0-118">有关详细信息，请参阅 [安全和序列化](security-and-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-118">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="fa8a0-119">设置当前主体的功能可以欺骗基于角色的安全性。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-119">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="fa8a0-120">由于与线程关联的安全状态，因此对线程进行操作很危险。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-120">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="fa8a0-121">可以使用私有成员来攻克可访问性机制。</span><span class="sxs-lookup"><span data-stu-id="fa8a0-121">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa8a0-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa8a0-122">See also</span></span>

- [<span data-ttu-id="fa8a0-123">安全编码准则</span><span class="sxs-lookup"><span data-stu-id="fa8a0-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
