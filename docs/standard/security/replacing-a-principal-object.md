---
title: 替换 Principal 对象
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET], replacing principal objects
- security [.NET], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
ms.openlocfilehash: fced91aef991bc228e65128d5e8d69e6a46588e5
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557094"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="40c5e-102">替换 Principal 对象</span><span class="sxs-lookup"><span data-stu-id="40c5e-102">Replacing a Principal Object</span></span>

<span data-ttu-id="40c5e-103">提供身份验证服务的应用程序必须能够为给定的线程替换 **主体** 对象 (<xref:System.Security.Principal.IPrincipal>)。</span><span class="sxs-lookup"><span data-stu-id="40c5e-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="40c5e-104">此外，安全系统必须帮助保护这种替换 **主体** 对象的能力，因为恶意附加的不正确的 **主体** 会通过声明一个不真实的身份或角色危及应用程序的安全。</span><span class="sxs-lookup"><span data-stu-id="40c5e-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="40c5e-105">因此，必须向需要能够替换 **主体** 对象的应用程序授予 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> 对象，以进行主体控制。</span><span class="sxs-lookup"><span data-stu-id="40c5e-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="40c5e-106">（请注意，对于执行基于角色的安全检查或创建 **主体** 对象，此权限不是必需的。）</span><span class="sxs-lookup"><span data-stu-id="40c5e-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
<span data-ttu-id="40c5e-107">可通过执行以下任务替换当前 **主体** 对象：</span><span class="sxs-lookup"><span data-stu-id="40c5e-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="40c5e-108">创建替换的 **主体** 对象和关联的 **标识** 对象。</span><span class="sxs-lookup"><span data-stu-id="40c5e-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="40c5e-109">将新的 **主体** 附加到调用上下文。</span><span class="sxs-lookup"><span data-stu-id="40c5e-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40c5e-110">示例</span><span class="sxs-lookup"><span data-stu-id="40c5e-110">Example</span></span>

<span data-ttu-id="40c5e-111">下面的示例演示如何创建一般主体对象并用该对象来设置线程的主体。</span><span class="sxs-lookup"><span data-stu-id="40c5e-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="40c5e-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="40c5e-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="40c5e-113">主体和标识对象</span><span class="sxs-lookup"><span data-stu-id="40c5e-113">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="40c5e-114">ASP.NET Core 安全性</span><span class="sxs-lookup"><span data-stu-id="40c5e-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)
