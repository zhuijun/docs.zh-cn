---
title: 程序集绑定重定向安全权限
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921376"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="11612-102">程序集绑定重定向安全权限</span><span class="sxs-lookup"><span data-stu-id="11612-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="11612-103">应用程序配置文件中的显式程序集绑定重定向需要安全权限。</span><span class="sxs-lookup"><span data-stu-id="11612-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="11612-104">这适用于对 .NET Framework 程序集和来自第三方的程序集的重定向。</span><span class="sxs-lookup"><span data-stu-id="11612-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="11612-105">通过在上设置标志来授予权限 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="11612-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="11612-106">默认情况下，托管程序集没有权限。</span><span class="sxs-lookup"><span data-stu-id="11612-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="11612-107">此安全权限将授予受信任区域（本地计算机）和 Intranet 区域中运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="11612-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="11612-108">严格禁止在 Internet 区域中运行的应用程序执行程序集绑定重定向。</span><span class="sxs-lookup"><span data-stu-id="11612-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="11612-109">如果程序集重定向是在由组件发行者控制的发行者策略文件中执行，或者在管理员控制的计算机配置文件中执行，则不需要该权限。</span><span class="sxs-lookup"><span data-stu-id="11612-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="11612-110">但是，若要使应用程序使用 [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) 应用程序配置文件中的元素显式忽略发行者策略，则需要权限。</span><span class="sxs-lookup"><span data-stu-id="11612-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="11612-111">下表显示了**BindingRedirects**标志的默认安全设置。</span><span class="sxs-lookup"><span data-stu-id="11612-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="11612-112">Zone</span><span class="sxs-lookup"><span data-stu-id="11612-112">Zone</span></span>|<span data-ttu-id="11612-113">BindingRedirects 标志设置</span><span class="sxs-lookup"><span data-stu-id="11612-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="11612-114">受信任区域（本地计算机）</span><span class="sxs-lookup"><span data-stu-id="11612-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="11612-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="11612-115">**ON**</span></span>|  
|<span data-ttu-id="11612-116">Intranet 区域</span><span class="sxs-lookup"><span data-stu-id="11612-116">Intranet Zone</span></span>|<span data-ttu-id="11612-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="11612-117">**ON**</span></span>|  
|<span data-ttu-id="11612-118">Internet 区域</span><span class="sxs-lookup"><span data-stu-id="11612-118">Internet Zone</span></span>|<span data-ttu-id="11612-119">**OFF**</span><span class="sxs-lookup"><span data-stu-id="11612-119">**OFF**</span></span>|  
|<span data-ttu-id="11612-120">不受信任区域</span><span class="sxs-lookup"><span data-stu-id="11612-120">Untrusted zones</span></span>|<span data-ttu-id="11612-121">**OFF**</span><span class="sxs-lookup"><span data-stu-id="11612-121">**OFF**</span></span>|  
  
 <span data-ttu-id="11612-122">管理员可以更改这些安全设置，以支持或限制给定计算机上的特定方案。</span><span class="sxs-lookup"><span data-stu-id="11612-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="11612-123">没有用于更改**BindingRedirects**标志设置的默认值的工具;管理员必须手动编辑用户计算机上的安全配置文件。</span><span class="sxs-lookup"><span data-stu-id="11612-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11612-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11612-124">See also</span></span>

- <span data-ttu-id="11612-125">[发行者策略文件和并行 (Side-by-Side) 执行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="11612-125">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="11612-126">如何：启用和禁用自动绑定重定向</span><span class="sxs-lookup"><span data-stu-id="11612-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="11612-127">并行执行</span><span class="sxs-lookup"><span data-stu-id="11612-127">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
