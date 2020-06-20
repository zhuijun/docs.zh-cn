---
title: 程序集绑定重定向安全权限
description: 了解 .NET 中的应用程序配置文件中显式程序集绑定重定向所需的安全权限。
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: a8596bcac4efb0aea07efcfde6726d8bbf148c24
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105094"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="3d8f8-103">程序集绑定重定向安全权限</span><span class="sxs-lookup"><span data-stu-id="3d8f8-103">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="3d8f8-104">应用程序配置文件中的显式程序集绑定重定向需要安全权限。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-104">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="3d8f8-105">这适用于对 .NET Framework 程序集和来自第三方的程序集的重定向。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-105">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="3d8f8-106">通过在上设置标志来授予权限 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-106">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="3d8f8-107">默认情况下，托管程序集没有权限。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-107">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="3d8f8-108">此安全权限将授予受信任区域（本地计算机）和 Intranet 区域中运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-108">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="3d8f8-109">严格禁止在 Internet 区域中运行的应用程序执行程序集绑定重定向。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-109">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="3d8f8-110">如果程序集重定向是在由组件发行者控制的发行者策略文件中执行，或者在管理员控制的计算机配置文件中执行，则不需要该权限。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-110">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="3d8f8-111">但是，若要使应用程序使用 [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) 应用程序配置文件中的元素显式忽略发行者策略，则需要权限。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-111">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="3d8f8-112">下表显示了**BindingRedirects**标志的默认安全设置。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-112">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="3d8f8-113">Zone</span><span class="sxs-lookup"><span data-stu-id="3d8f8-113">Zone</span></span>|<span data-ttu-id="3d8f8-114">BindingRedirects 标志设置</span><span class="sxs-lookup"><span data-stu-id="3d8f8-114">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="3d8f8-115">受信任区域（本地计算机）</span><span class="sxs-lookup"><span data-stu-id="3d8f8-115">Trusted Zone (local machine)</span></span>|<span data-ttu-id="3d8f8-116">**ON**</span><span class="sxs-lookup"><span data-stu-id="3d8f8-116">**ON**</span></span>|  
|<span data-ttu-id="3d8f8-117">Intranet 区域</span><span class="sxs-lookup"><span data-stu-id="3d8f8-117">Intranet Zone</span></span>|<span data-ttu-id="3d8f8-118">**ON**</span><span class="sxs-lookup"><span data-stu-id="3d8f8-118">**ON**</span></span>|  
|<span data-ttu-id="3d8f8-119">Internet 区域</span><span class="sxs-lookup"><span data-stu-id="3d8f8-119">Internet Zone</span></span>|<span data-ttu-id="3d8f8-120">**OFF**</span><span class="sxs-lookup"><span data-stu-id="3d8f8-120">**OFF**</span></span>|  
|<span data-ttu-id="3d8f8-121">不受信任区域</span><span class="sxs-lookup"><span data-stu-id="3d8f8-121">Untrusted zones</span></span>|<span data-ttu-id="3d8f8-122">**OFF**</span><span class="sxs-lookup"><span data-stu-id="3d8f8-122">**OFF**</span></span>|  
  
 <span data-ttu-id="3d8f8-123">管理员可以更改这些安全设置，以支持或限制给定计算机上的特定方案。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-123">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="3d8f8-124">没有用于更改**BindingRedirects**标志设置的默认值的工具;管理员必须手动编辑用户计算机上的 Security.config 文件。</span><span class="sxs-lookup"><span data-stu-id="3d8f8-124">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d8f8-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d8f8-125">See also</span></span>

- <span data-ttu-id="3d8f8-126">[发行者策略文件和并行 (Side-by-Side) 执行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3d8f8-126">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="3d8f8-127">如何：启用和禁用自动绑定重定向</span><span class="sxs-lookup"><span data-stu-id="3d8f8-127">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="3d8f8-128">并行执行</span><span class="sxs-lookup"><span data-stu-id="3d8f8-128">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
