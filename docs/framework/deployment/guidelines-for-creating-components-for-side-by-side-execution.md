---
title: 并行执行的组件的创建指南
description: 查看有关创建并行执行的组件的指南。 例如，将类型标识绑定到某个文件版本，或使用可识别版本的存储。
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: f0d25984f2444d29d9fc0edb3add23b6adc04c62
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622635"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a><span data-ttu-id="4d786-104">并行执行的组件的创建指南</span><span class="sxs-lookup"><span data-stu-id="4d786-104">Guidelines for Creating Components for Side-by-Side Execution</span></span>
<span data-ttu-id="4d786-105">创建适用于并行执行的托管应用程序或组件时，请遵循下列一般性准则：</span><span class="sxs-lookup"><span data-stu-id="4d786-105">Follow these general guidelines to create managed applications or components designed for side-by-side execution:</span></span>  
  
- <span data-ttu-id="4d786-106">将类型标识绑定到文件的特定版本。</span><span class="sxs-lookup"><span data-stu-id="4d786-106">Bind type identity to a particular version of a file.</span></span>  
  
     <span data-ttu-id="4d786-107">通过使用具有强名称的程序集，公共语言运行时将类型标识绑定到文件的特定版本。</span><span class="sxs-lookup"><span data-stu-id="4d786-107">The common language runtime binds type identity to a particular file version by using strong-named assemblies.</span></span> <span data-ttu-id="4d786-108">若要创建适用于并行执行的应用程序或组件，你必须为所有的程序集提供强名称。</span><span class="sxs-lookup"><span data-stu-id="4d786-108">To create an application or component for side-by-side execution, you must give all assemblies a strong name.</span></span> <span data-ttu-id="4d786-109">这样可以创建精确的类型标识，并确保任何类型解析都定向到正确的文件。</span><span class="sxs-lookup"><span data-stu-id="4d786-109">This creates precise type identity and ensures that any type resolution is directed to the correct file.</span></span> <span data-ttu-id="4d786-110">具有强名称的程序集包含版本、区域性和发行者信息，运行时使用这些信息来正确地定位文件，从而满足绑定请求。</span><span class="sxs-lookup"><span data-stu-id="4d786-110">A strong-named assembly contains version, culture, and publisher information that the runtime uses to locate the correct file to fulfill a binding request.</span></span>  
  
- <span data-ttu-id="4d786-111">使用可以区别版本的存储。</span><span class="sxs-lookup"><span data-stu-id="4d786-111">Use version-aware storage.</span></span>  
  
     <span data-ttu-id="4d786-112">运行时使用全局程序集缓存提供可以区别版本的存储。</span><span class="sxs-lookup"><span data-stu-id="4d786-112">The runtime uses the global assembly cache to provide version-aware storage.</span></span> <span data-ttu-id="4d786-113">全局程序集缓存是一个可以区别版本的目录结构，安装在使用 .NET Framework 的每台计算机上。</span><span class="sxs-lookup"><span data-stu-id="4d786-113">The global assembly cache is a version-aware directory structure installed on every computer that uses the .NET Framework.</span></span> <span data-ttu-id="4d786-114">安装在全局程序集缓存中的程序集不会在安装该程序集的新版本时被覆盖。</span><span class="sxs-lookup"><span data-stu-id="4d786-114">Assemblies installed in the global assembly cache are not overwritten when a new version of that assembly is installed.</span></span>  
  
- <span data-ttu-id="4d786-115">创建隔离运行的应用程序或组件。</span><span class="sxs-lookup"><span data-stu-id="4d786-115">Create an application or component that runs in isolation.</span></span>  
  
     <span data-ttu-id="4d786-116">隔离运行的应用程序或组件必须管理资源，以避免该应用程序或组件的两个实例在同时运行时发生冲突。</span><span class="sxs-lookup"><span data-stu-id="4d786-116">An application or component that runs in isolation must manage resources to avoid conflicts when two instances of the application or component are running simultaneously.</span></span> <span data-ttu-id="4d786-117">应用程序或组件还必须使用版本特定的文件结构。</span><span class="sxs-lookup"><span data-stu-id="4d786-117">The application or component must also use a version-specific file structure.</span></span>  
  
## <a name="application-and-component-isolation"></a><span data-ttu-id="4d786-118">应用程序和组件的隔离</span><span class="sxs-lookup"><span data-stu-id="4d786-118">Application and Component Isolation</span></span>  
 <span data-ttu-id="4d786-119">对于并行执行的应用程序或组件，设计成功的关键是隔离。</span><span class="sxs-lookup"><span data-stu-id="4d786-119">One key to successfully designing an application or component for side-by-side execution is isolation.</span></span> <span data-ttu-id="4d786-120">应用程序或组件必须以隔离方式管理所有的资源，尤其是文件 I/O。</span><span class="sxs-lookup"><span data-stu-id="4d786-120">The application or component must manage all resources, particularly file I/O, in an isolated manner.</span></span> <span data-ttu-id="4d786-121">请遵循以下准则，确保你的应用程序或组件以隔离方式运行：</span><span class="sxs-lookup"><span data-stu-id="4d786-121">Follow these guidelines to make sure your application or component runs in isolation:</span></span>  
  
- <span data-ttu-id="4d786-122">按照版本特定的方式，写入注册表。</span><span class="sxs-lookup"><span data-stu-id="4d786-122">Write to the registry in a version-specific way.</span></span> <span data-ttu-id="4d786-123">将指示版本的值存储在配置单元或项中，同时，不要在组件的不同版本间共享信息或状态。</span><span class="sxs-lookup"><span data-stu-id="4d786-123">Store values in hives or keys that indicate the version, and do not share information or state across versions of a component.</span></span> <span data-ttu-id="4d786-124">这就防止了同时运行的两个应用程序或组件覆盖信息。</span><span class="sxs-lookup"><span data-stu-id="4d786-124">This prevents two applications or components running at the same time from overwriting information.</span></span>  
  
- <span data-ttu-id="4d786-125">使命名的内核对象成为版本特定的内核对象，以避免发生争用条件。</span><span class="sxs-lookup"><span data-stu-id="4d786-125">Make named kernel objects version-specific so that a race condition does not occur.</span></span> <span data-ttu-id="4d786-126">例如，当来自同一应用程序的两个版本的两个信号灯互相等待时，就发生了争用条件。</span><span class="sxs-lookup"><span data-stu-id="4d786-126">For example, a race condition occurs when two semaphores from two versions of the same application wait on each other.</span></span>  
  
- <span data-ttu-id="4d786-127">使文件名和目录名可以区别版本。</span><span class="sxs-lookup"><span data-stu-id="4d786-127">Make file and directory names version-aware.</span></span> <span data-ttu-id="4d786-128">这意味着文件结构应该依赖于版本信息。</span><span class="sxs-lookup"><span data-stu-id="4d786-128">This means that file structures should rely on version information.</span></span>  
  
- <span data-ttu-id="4d786-129">按照版本特定的方式，创建用户帐户和组。</span><span class="sxs-lookup"><span data-stu-id="4d786-129">Create user accounts and groups in a version-specific manner.</span></span> <span data-ttu-id="4d786-130">应用程序创建的用户帐户和组应该由版本识别。</span><span class="sxs-lookup"><span data-stu-id="4d786-130">User accounts and groups created by an application should be identified by version.</span></span> <span data-ttu-id="4d786-131">不要在应用程序的不同版本间共享用户帐户和组。</span><span class="sxs-lookup"><span data-stu-id="4d786-131">Do not share user accounts and groups between versions of an application.</span></span>  
  
## <a name="installing-and-uninstalling-versions"></a><span data-ttu-id="4d786-132">安装或卸载版本</span><span class="sxs-lookup"><span data-stu-id="4d786-132">Installing and Uninstalling Versions</span></span>  
 <span data-ttu-id="4d786-133">在设计并行执行的应用程序时，请遵循以下关于安装和卸载版本的准则：</span><span class="sxs-lookup"><span data-stu-id="4d786-133">When designing an application for side-by-side execution, follow these guidelines concerning installing and uninstalling versions:</span></span>  
  
- <span data-ttu-id="4d786-134">请不要从注册表中删除在 .NET Framework 的其他版本下运行的其他应用程序可能需要的信息。</span><span class="sxs-lookup"><span data-stu-id="4d786-134">Do not delete information from the registry that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
- <span data-ttu-id="4d786-135">请不要在注册表中替换在 .NET Framework 的其他版本下运行的其他应用程序可能需要的信息。</span><span class="sxs-lookup"><span data-stu-id="4d786-135">Do not replace information in the registry that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
- <span data-ttu-id="4d786-136">请不要注销在 .NET Framework 的其他版本下运行的其他应用程序可能需要的 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="4d786-136">Do not unregister COM components that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
- <span data-ttu-id="4d786-137">对于已注册的 COM 服务器，请不要更改 InprocServer32 或其他注册表项。</span><span class="sxs-lookup"><span data-stu-id="4d786-137">Do not change **InprocServer32** or other registry entries for a COM server that was already registered.</span></span>  
  
- <span data-ttu-id="4d786-138">请不要删除在 .NET Framework 的其他版本下运行的其他应用程序可能需要的用户帐户或组。</span><span class="sxs-lookup"><span data-stu-id="4d786-138">Do not delete user accounts or groups that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
- <span data-ttu-id="4d786-139">请不要向注册表中添加任何包含未版本化路径的内容。</span><span class="sxs-lookup"><span data-stu-id="4d786-139">Do not add anything to the registry that contains an unversioned path.</span></span>  
  
## <a name="file-version-number-and-assembly-version-number"></a><span data-ttu-id="4d786-140">文件版本号和程序集版本号</span><span class="sxs-lookup"><span data-stu-id="4d786-140">File Version Number and Assembly Version Number</span></span>  
 <span data-ttu-id="4d786-141">文件版本是运行时不使用的 Win32 版本资源。</span><span class="sxs-lookup"><span data-stu-id="4d786-141">File version is a Win32 version resource that is not used by the runtime.</span></span> <span data-ttu-id="4d786-142">通常情况下，即使是对于就地更新，也应更新文件版本。</span><span class="sxs-lookup"><span data-stu-id="4d786-142">In general, you update the file version even for an in-place update.</span></span> <span data-ttu-id="4d786-143">两个相同的文件可以有不同的文件版本信息，而两个不同的文件也可以有相同的文件版本信息。</span><span class="sxs-lookup"><span data-stu-id="4d786-143">Two identical files can have different file version information, and two different files can have the same file version information.</span></span>  
  
 <span data-ttu-id="4d786-144">运行时使用程序集版本进行程序集绑定。</span><span class="sxs-lookup"><span data-stu-id="4d786-144">The assembly version is used by the runtime for assembly binding.</span></span> <span data-ttu-id="4d786-145">若两个相同的程序集版本号不同，则运行时将它们视为两个不同的程序集。</span><span class="sxs-lookup"><span data-stu-id="4d786-145">Two identical assemblies with different version numbers are treated as two different assemblies by the runtime.</span></span>  
  
 <span data-ttu-id="4d786-146">仅当文件版本号更新时，[全局程序集缓存工具 (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 才允许用户替换程序集。</span><span class="sxs-lookup"><span data-stu-id="4d786-146">The [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) allows you to replace an assembly when only the file version number is newer.</span></span> <span data-ttu-id="4d786-147">安装程序在安装时通常不会覆盖程序集，除非该程序集版本号较大。</span><span class="sxs-lookup"><span data-stu-id="4d786-147">The installer generally does not install over an assembly unless the assembly version number is greater.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d786-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="4d786-148">See also</span></span>

- [<span data-ttu-id="4d786-149">并行执行</span><span class="sxs-lookup"><span data-stu-id="4d786-149">Side-by-Side Execution</span></span>](side-by-side-execution.md)
- [<span data-ttu-id="4d786-150">如何：启用和禁用自动绑定重定向</span><span class="sxs-lookup"><span data-stu-id="4d786-150">How to: Enable and Disable Automatic Binding Redirection</span></span>](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
