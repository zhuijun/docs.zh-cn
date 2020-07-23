---
title: 免注册 COM 互操作
description: 使用免注册 COM 互操作，在不使用 Windows 注册表来存储程序集信息的情况下激活组件。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
ms.openlocfilehash: c6a4dfc54152ade6136e4292bbd1c4522553d491
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281597"
---
# <a name="registration-free-com-interop"></a><span data-ttu-id="73c87-103">免注册 COM 互操作</span><span class="sxs-lookup"><span data-stu-id="73c87-103">Registration-Free COM Interop</span></span>
<span data-ttu-id="73c87-104">免注册 COM 互操作在不使用 Windows 注册表来存储程序集信息的情况下激活组件。</span><span class="sxs-lookup"><span data-stu-id="73c87-104">Registration-free COM interop activates a component without using the Windows registry to store assembly information.</span></span> <span data-ttu-id="73c87-105">不是在部署过程中在计算机上注册组件，而是在设计时创建包含有关绑定和激活信息的 Win32 样式清单文件。</span><span class="sxs-lookup"><span data-stu-id="73c87-105">Instead of registering a component on a computer during deployment, you create Win32-style manifest files at design time that contain information about binding and activation.</span></span> <span data-ttu-id="73c87-106">正是这些清单文件（而不是注册表项）指导对象的激活。</span><span class="sxs-lookup"><span data-stu-id="73c87-106">These manifest files, rather than registry keys, direct the activation of an object.</span></span>  
  
 <span data-ttu-id="73c87-107">不在部署期间注册程序集而使用免注册激活具有两大优势：</span><span class="sxs-lookup"><span data-stu-id="73c87-107">Using registration-free activation for your assemblies instead of registering them during deployment offers two advantages:</span></span>  
  
- <span data-ttu-id="73c87-108">计算机上安装了多个 DLL 版本时，你可以控制要激活的版本。</span><span class="sxs-lookup"><span data-stu-id="73c87-108">You can control which DLL version is activated when more than one version is installed on a computer.</span></span>  
  
- <span data-ttu-id="73c87-109">最终用户可以使用 XCOPY 或 FTP 将应用程序复制到计算机上适当的目录。</span><span class="sxs-lookup"><span data-stu-id="73c87-109">End users can use XCOPY or FTP to copy your application to an appropriate directory on their computer.</span></span> <span data-ttu-id="73c87-110">然后即可从该目录运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="73c87-110">The application can then be run from that directory.</span></span>  
  
 <span data-ttu-id="73c87-111">本节介绍免注册 COM 互操作所需的两种清单类型：应用程序清单和组件清单。</span><span class="sxs-lookup"><span data-stu-id="73c87-111">This section describes the two types of manifests needed for registration-free COM interop: application and component manifests.</span></span> <span data-ttu-id="73c87-112">这些清单是 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="73c87-112">These manifests are XML files.</span></span> <span data-ttu-id="73c87-113">应用程序清单由应用程序开发人员创建，包含描述程序集和程序集依赖项的元数据。</span><span class="sxs-lookup"><span data-stu-id="73c87-113">An application manifest, which is created by an application developer, contains metadata that describes assemblies and assembly dependencies.</span></span> <span data-ttu-id="73c87-114">组件清单由组件开发人员创建，包含 Windows 注册表中的其他信息。</span><span class="sxs-lookup"><span data-stu-id="73c87-114">A component manifest, created by a component developer, contains information otherwise located in the Windows registry.</span></span>  
  
### <a name="requirements-for-registration-free-com-interop"></a><span data-ttu-id="73c87-115">免注册 COM 互操作的需求</span><span class="sxs-lookup"><span data-stu-id="73c87-115">Requirements for registration-free COM interop</span></span>  
  
1. <span data-ttu-id="73c87-116">对免注册 COM 互操作的支持根据库程序集的类型而略有差异；具体而言，因该程序集是非托管的（COM 并行）还是托管的（基于 NET）而异。</span><span class="sxs-lookup"><span data-stu-id="73c87-116">Support for registration-free COM interop varies slightly depending on the type of library assembly; specifically, whether the assembly is unmanaged (COM side-by-side) or managed (.NET-based).</span></span> <span data-ttu-id="73c87-117">下表显示每个程序集类型对操作系统和 .NET Framework 版本的要求。</span><span class="sxs-lookup"><span data-stu-id="73c87-117">The following table shows the operating system and .NET Framework version requirements for each assembly type.</span></span>  
  
    |<span data-ttu-id="73c87-118">程序集类型</span><span class="sxs-lookup"><span data-stu-id="73c87-118">Assembly type</span></span>|<span data-ttu-id="73c87-119">操作系统</span><span class="sxs-lookup"><span data-stu-id="73c87-119">Operating system</span></span>|<span data-ttu-id="73c87-120">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="73c87-120">.NET Framework version</span></span>|  
    |-------------------|----------------------|----------------------------|  
    |<span data-ttu-id="73c87-121">COM 并行</span><span class="sxs-lookup"><span data-stu-id="73c87-121">COM side-by-side</span></span>|<span data-ttu-id="73c87-122">Microsoft Windows XP</span><span class="sxs-lookup"><span data-stu-id="73c87-122">Microsoft Windows XP</span></span>|<span data-ttu-id="73c87-123">不要求。</span><span class="sxs-lookup"><span data-stu-id="73c87-123">Not required.</span></span>|  
    |<span data-ttu-id="73c87-124">基于 .NET</span><span class="sxs-lookup"><span data-stu-id="73c87-124">.NET-based</span></span>|<span data-ttu-id="73c87-125">带有 SP2 的 Windows XP</span><span class="sxs-lookup"><span data-stu-id="73c87-125">Windows XP with SP2</span></span>|<span data-ttu-id="73c87-126">NET Framework 1.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="73c87-126">NET Framework version 1.1 or later.</span></span>|  
  
     <span data-ttu-id="73c87-127">Windows Server 2003 系列还支持基于 .NET 的程序集采用免注册 COM 互操作。</span><span class="sxs-lookup"><span data-stu-id="73c87-127">The Windows Server 2003 family also supports registration-free COM interop for .NET-based assemblies.</span></span>  
  
     <span data-ttu-id="73c87-128">要使基于 .NET 的类与 COM 的免注册激活兼容，类必须具有无参数构造函数，并且必须是公共类。</span><span class="sxs-lookup"><span data-stu-id="73c87-128">For a .NET-based class to be compatible with registry-free activation from COM, the class must have a parameterless constructor and must be public.</span></span>  
  
### <a name="configuring-com-components-for-registration-free-activation"></a><span data-ttu-id="73c87-129">将 COM 组件配置为免注册激活</span><span class="sxs-lookup"><span data-stu-id="73c87-129">Configuring COM components for registration-free activation</span></span>  
  
1. <span data-ttu-id="73c87-130">要使 COM 组件参与免注册激活，必需将其作为并行程序集进行部署。</span><span class="sxs-lookup"><span data-stu-id="73c87-130">For a COM component to participate in registration-free activation, it must be deployed as a side-by-side assembly.</span></span> <span data-ttu-id="73c87-131">并行程序集是非托管程序集。</span><span class="sxs-lookup"><span data-stu-id="73c87-131">Side-by-side assemblies are unmanaged assemblies.</span></span>  <span data-ttu-id="73c87-132">有关详细信息，请参阅[使用并行程序集](/windows/desktop/SbsCs/using-side-by-side-assemblies)。</span><span class="sxs-lookup"><span data-stu-id="73c87-132">For more information, see [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies).</span></span>  
  
     <span data-ttu-id="73c87-133">要使用 COM 并行程序集，基于 .NET 的应用程序的开发人员必须提供一个包含绑定和激活信息的应用程序清单。</span><span class="sxs-lookup"><span data-stu-id="73c87-133">To use COM side-by-side assemblies, a .NET-based application developer must provide an application manifest, which contains the binding and activation information.</span></span> <span data-ttu-id="73c87-134">Windows XP 操作系统内置对非托管并行程序集的支持。</span><span class="sxs-lookup"><span data-stu-id="73c87-134">Support for unmanaged side-by-side assemblies is built into the Windows XP operating system.</span></span> <span data-ttu-id="73c87-135">当要激活的组件不在注册表中时，操作系统支持的 COM 运行时将扫描应用程序清单以查找激活信息。</span><span class="sxs-lookup"><span data-stu-id="73c87-135">The COM runtime, supported by the operating system, scans an application manifest for activation information when the component being activated is not in the registry.</span></span>  
  
     <span data-ttu-id="73c87-136">Windows XP 上安装的 COM 组件可以选择进行免注册激活。</span><span class="sxs-lookup"><span data-stu-id="73c87-136">Registration-free activation is optional for COM components installed on Windows XP.</span></span> <span data-ttu-id="73c87-137">有关向应用程序添加并行程序集的详细说明，请参阅[使用并行程序集](/windows/desktop/SbsCs/using-side-by-side-assemblies)。</span><span class="sxs-lookup"><span data-stu-id="73c87-137">For detailed instructions on adding a side-by-side assembly to an application, see [Using Side-by-side Assemblies](/windows/desktop/SbsCs/using-side-by-side-assemblies).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="73c87-138">并行执行是一项 .NET Framework 功能，它使得多个版本的运行时，以及使用同一个运行时版本的多个版本的应用程序和组件，能够在同一台计算机上同时运行。</span><span class="sxs-lookup"><span data-stu-id="73c87-138">Side-by-side execution is a .NET Framework feature that enables multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, to run on the same computer at the same time.</span></span> <span data-ttu-id="73c87-139">并行执行和并行程序集是提供并行功能的两种不同机制。</span><span class="sxs-lookup"><span data-stu-id="73c87-139">Side-by-side execution and side-by-side assemblies are different mechanisms for providing side-by-side functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c87-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="73c87-140">See also</span></span>

- [<span data-ttu-id="73c87-141">如何：配置基于 .NET Framework 的 COM 组件以进行免注册激活</span><span class="sxs-lookup"><span data-stu-id="73c87-141">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)
