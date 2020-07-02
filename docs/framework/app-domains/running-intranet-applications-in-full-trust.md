---
title: 在完全信任环境中运行 Intranet 应用程序
description: 在 .NET 3.5 SP1 的完全信任环境中运行 Intranet 应用程序。 应用程序及其库程序集可在网络共享中作为完全信任的程序集运行。
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
ms.openlocfilehash: f4fb3b61e434154b1c7252377c234aeff49f0227
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104596"
---
# <a name="running-intranet-applications-in-full-trust"></a><span data-ttu-id="92aad-104">在完全信任环境中运行 Intranet 应用程序</span><span class="sxs-lookup"><span data-stu-id="92aad-104">Running Intranet Applications in Full Trust</span></span>

<span data-ttu-id="92aad-105">从 .NET Framework 3.5 版 Service Pack 1 (SP1) 开始，应用程序及其库程序集可在网络共享中作为完全信任的程序集运行。</span><span class="sxs-lookup"><span data-stu-id="92aad-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), applications and their library assemblies can be run as full-trust assemblies from a network share.</span></span> <span data-ttu-id="92aad-106"><xref:System.Security.SecurityZone.MyComputer> 区域证据自动添加到从 Intranet 上的共享加载的程序集。</span><span class="sxs-lookup"><span data-stu-id="92aad-106"><xref:System.Security.SecurityZone.MyComputer> zone evidence is automatically added to assemblies that are loaded from a share on the intranet.</span></span> <span data-ttu-id="92aad-107">此证据为这些程序集提供与计算机上程序集所具有的相同授予集（通常为完全信任）。</span><span class="sxs-lookup"><span data-stu-id="92aad-107">This evidence gives those assemblies the same grant set (which is typically full trust) as the assemblies that reside on the computer.</span></span> <span data-ttu-id="92aad-108">此功能不适用于 ClickOnce 应用程序或用于在主机上运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="92aad-108">This functionality does not apply to ClickOnce applications or to applications that are designed to run on a host.</span></span>  
  
## <a name="rules-for-library-assemblies"></a><span data-ttu-id="92aad-109">库程序集的规则</span><span class="sxs-lookup"><span data-stu-id="92aad-109">Rules for Library Assemblies</span></span>  

<span data-ttu-id="92aad-110">以下规则适用于可执行文件在网络共享上加载的程序集：</span><span class="sxs-lookup"><span data-stu-id="92aad-110">The following rules apply to assemblies that are loaded by an executable on a network share:</span></span>  
  
- <span data-ttu-id="92aad-111">库程序集必须与可执行程序集位于同一文件夹。</span><span class="sxs-lookup"><span data-stu-id="92aad-111">Library assemblies must reside in the same folder as the executable assembly.</span></span> <span data-ttu-id="92aad-112">不能为位于子文件夹或通过不同路径引用的程序集提供完全信任的授予集。</span><span class="sxs-lookup"><span data-stu-id="92aad-112">Assemblies that reside in a subfolder or are referenced on a different path are not given the full-trust grant set.</span></span>  
  
- <span data-ttu-id="92aad-113">如果可执行文件延迟加载程序集，则它必须使用启动可执行文件所用的路径。</span><span class="sxs-lookup"><span data-stu-id="92aad-113">If the executable delay-loads an assembly, it must use the same path that was used to start the executable.</span></span> <span data-ttu-id="92aad-114">例如，如果共享 \\\\network-computer\\share 映射到某个驱动器号，并且可执行文件是从该路径运行的，那么由该可执行文件使用网络路径加载的程序集将不会被授予完全信任 。</span><span class="sxs-lookup"><span data-stu-id="92aad-114">For example, if the share \\\\*network-computer*\\*share* is mapped to a drive letter and the executable is run from that path, assemblies that are loaded by the executable by using the network path will not be granted full trust.</span></span> <span data-ttu-id="92aad-115">若要在 <xref:System.Security.SecurityZone.MyComputer> 区域延迟加载程序集，则可执行文件必须使用驱动器号路径。</span><span class="sxs-lookup"><span data-stu-id="92aad-115">To delay-load an assembly in the <xref:System.Security.SecurityZone.MyComputer> zone, the executable must use the drive letter path.</span></span>  
  
## <a name="restoring-the-former-intranet-policy"></a><span data-ttu-id="92aad-116">还原以前的 Intranet 策略</span><span class="sxs-lookup"><span data-stu-id="92aad-116">Restoring the Former Intranet Policy</span></span>  

<span data-ttu-id="92aad-117">在早期版本的 .NET framework 中，可为 <xref:System.Security.SecurityZone.Intranet> 区域证据授予共享程序集。</span><span class="sxs-lookup"><span data-stu-id="92aad-117">In earlier versions of the .NET Framework, shared assemblies were granted <xref:System.Security.SecurityZone.Intranet> zone evidence.</span></span> <span data-ttu-id="92aad-118">必须指定代码访问安全策略才能为共享上的程序集授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="92aad-118">You had to specify code access security policy to grant full trust to an assembly on a share.</span></span>  
  
<span data-ttu-id="92aad-119">这一新行为现在是 Intranet 程序集的默认行为。</span><span class="sxs-lookup"><span data-stu-id="92aad-119">This new behavior is the default for intranet assemblies.</span></span> <span data-ttu-id="92aad-120">通过设置适用于计算机上所有应用程序的注册表项，可以还原到早期提供 <xref:System.Security.SecurityZone.Intranet> 证据的行为。</span><span class="sxs-lookup"><span data-stu-id="92aad-120">You can return to the earlier behavior of providing <xref:System.Security.SecurityZone.Intranet> evidence by setting a registry key that applies to all applications on the computer.</span></span> <span data-ttu-id="92aad-121">此过程在 32 位和 64 位计算机上有所不同：</span><span class="sxs-lookup"><span data-stu-id="92aad-121">This process is different for 32-bit and 64-bit computers:</span></span>  
  
- <span data-ttu-id="92aad-122">对于 32 位计算机，在系统注册表中的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 项下创建子项。</span><span class="sxs-lookup"><span data-stu-id="92aad-122">On 32-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="92aad-123">使用项名称 LegacyMyComputerZone，DWORD 值为 1。</span><span class="sxs-lookup"><span data-stu-id="92aad-123">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span>  
  
- <span data-ttu-id="92aad-124">对于 64 位计算机，在系统注册表中的 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework 项下创建子项。</span><span class="sxs-lookup"><span data-stu-id="92aad-124">On 64-bit computers, create a subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key in the system registry.</span></span> <span data-ttu-id="92aad-125">使用项名称 LegacyMyComputerZone，DWORD 值为 1。</span><span class="sxs-lookup"><span data-stu-id="92aad-125">Use the key name LegacyMyComputerZone with a DWORD value of 1.</span></span> <span data-ttu-id="92aad-126">在 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 项下创建相同的子项。</span><span class="sxs-lookup"><span data-stu-id="92aad-126">Create the same subkey under the HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92aad-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="92aad-127">See also</span></span>

- [<span data-ttu-id="92aad-128">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="92aad-128">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
