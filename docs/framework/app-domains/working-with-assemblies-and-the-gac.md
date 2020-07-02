---
title: 使用程序集和全局程序集缓存
description: 使用 .NET 中的程序集和全局程序集缓存 (GAC)。 查看建议在 GAC 中安装程序集的原因。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
ms.openlocfilehash: 16cfd9faf02d5b58acad1cc0cf19be61c9814d35
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105155"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a><span data-ttu-id="45485-104">使用程序集和全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="45485-104">Working with Assemblies and the Global Assembly Cache</span></span>

<span data-ttu-id="45485-105">如果需要在几个应用程序间共享程序集，可将其安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="45485-105">If you intend to share an assembly among several applications, you can install it into the global assembly cache.</span></span> <span data-ttu-id="45485-106">安装了公共语言运行时的每台计算机均具有此计算机范围的代码缓存。</span><span class="sxs-lookup"><span data-stu-id="45485-106">Each computer where the common language runtime is installed has this machine-wide code cache.</span></span> <span data-ttu-id="45485-107">全局程序集缓存中存储专门指定给由计算机中若干应用程序共享的程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-107">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span> <span data-ttu-id="45485-108">程序集必须具有强名称才可安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="45485-108">An assembly must have a strong name to be installed in the global assembly cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45485-109">全局程序集缓存中放置的程序集必须具有相同的程序集名称和文件名（不包括文件扩展名）。</span><span class="sxs-lookup"><span data-stu-id="45485-109">Assemblies placed in the global assembly cache must have the same assembly name and file name (not including the file name extension).</span></span> <span data-ttu-id="45485-110">例如，程序集名称为 myAssembly 的程序集必须具有名为 myAssembly.exe 或 myAssembly.dll 的文件。</span><span class="sxs-lookup"><span data-stu-id="45485-110">For example, an assembly with the assembly name of myAssembly must have a file name of either myAssembly.exe or myAssembly.dll.</span></span>  
  
<span data-ttu-id="45485-111">只能在需要时才通过将程序集安装到全局程序集缓存中来共享程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-111">You should share assemblies by installing them into the global assembly cache only when necessary.</span></span> <span data-ttu-id="45485-112">一般原则是：程序集依赖项保持专用，并在应用程序目录中定位程序集，除非明确要求共享程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-112">As a general guideline, keep assembly dependencies private and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="45485-113">另外，无需为了使程序集可以访问 COM 互操作或非托管代码而将程序集安装到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="45485-113">In addition, you do not have to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
<span data-ttu-id="45485-114">建议将程序集安装到全局程序集缓存中的原因有以下几点：</span><span class="sxs-lookup"><span data-stu-id="45485-114">There are several reasons why you might want to install an assembly into the global assembly cache:</span></span>  
  
- <span data-ttu-id="45485-115">共享位置。</span><span class="sxs-lookup"><span data-stu-id="45485-115">Shared location.</span></span>  
  
     <span data-ttu-id="45485-116">应该由应用程序使用的程序集可以置于全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="45485-116">Assemblies that should be used by applications can be put in the global assembly cache.</span></span> <span data-ttu-id="45485-117">例如，如果所有应用程序都应使用位于全局程序集缓存中的程序集，则可将版本策略语句添加到 Machine.config 文件中，此文件将引用重新定向到程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-117">For example, if all applications should use an assembly located in the global assembly cache, a version policy statement can be added to the Machine.config file that redirects references to the assembly.</span></span>  
  
- <span data-ttu-id="45485-118">文件安全。</span><span class="sxs-lookup"><span data-stu-id="45485-118">File security.</span></span>  
  
     <span data-ttu-id="45485-119">管理员通常使用访问控制列表 (ACL) 来保护 systemroot 目录，从而控制写入和执行访问。</span><span class="sxs-lookup"><span data-stu-id="45485-119">Administrators often protect the systemroot directory using an Access Control List (ACL) to control write and execute access.</span></span> <span data-ttu-id="45485-120">由于全局程序集缓存安装在 systemroot 目录中，因此它将继承该目录的 ACL。</span><span class="sxs-lookup"><span data-stu-id="45485-120">Because the global assembly cache is installed in the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="45485-121">建议只允许具有“管理员”权限的用户从全局程序集缓存中删除文件。</span><span class="sxs-lookup"><span data-stu-id="45485-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
- <span data-ttu-id="45485-122">并行版本。</span><span class="sxs-lookup"><span data-stu-id="45485-122">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="45485-123">可在全局程序集缓存中维护名称相同但版本信息不同的程序集的多个副本。</span><span class="sxs-lookup"><span data-stu-id="45485-123">Multiple copies of assemblies with the same name but different version information can be maintained in the global assembly cache.</span></span>  
  
- <span data-ttu-id="45485-124">其他搜索位置。</span><span class="sxs-lookup"><span data-stu-id="45485-124">Additional search location.</span></span>  
  
     <span data-ttu-id="45485-125">在探测或使用配置文件中的基本代码信息之前，公共语言运行时会先检查全局程序集缓存中符合程序集请求的程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-125">The common language runtime checks the global assembly cache for an assembly that matches the assembly request before probing or using the codebase information in a configuration file.</span></span>  
  
 <span data-ttu-id="45485-126">请注意，在有些情况下，很明显不需要将程序集安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="45485-126">Note that there are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="45485-127">如果将组成应用程序的某个程序集置于全局程序集缓存中，就无法再通过使用 XCOPY 复制应用程序目录来复制或安装应用程序。</span><span class="sxs-lookup"><span data-stu-id="45485-127">If you place one of the assemblies that make up an application into the global assembly cache, you can no longer replicate or install the application by using XCOPY to copy the application directory.</span></span> <span data-ttu-id="45485-128">在这种情况下，还必须将程序集移到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="45485-128">In this case, you must also move the assembly into the global assembly cache.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45485-129">本节内容</span><span class="sxs-lookup"><span data-stu-id="45485-129">In This Section</span></span>  
[<span data-ttu-id="45485-130">如何：将程序集安装到全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="45485-130">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)  
<span data-ttu-id="45485-131">描述将程序集安装到全局程序集缓存的方法。</span><span class="sxs-lookup"><span data-stu-id="45485-131">Describes the ways to install an assembly into the global assembly cache.</span></span>  
  
[<span data-ttu-id="45485-132">如何：查看全局程序集缓存的内容</span><span class="sxs-lookup"><span data-stu-id="45485-132">How to: View the Contents of the Global Assembly Cache</span></span>](how-to-view-the-contents-of-the-gac.md)  
<span data-ttu-id="45485-133">说明如何使用 [Gacutil.exe（全局程序集缓存工具）](../tools/gacutil-exe-gac-tool.md)来查看全局程序集缓存的内容。</span><span class="sxs-lookup"><span data-stu-id="45485-133">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
[<span data-ttu-id="45485-134">如何：从全局程序集缓存中删除程序集</span><span class="sxs-lookup"><span data-stu-id="45485-134">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)  
<span data-ttu-id="45485-135">说明如何使用 [Gacutil.exe（全局程序集缓存工具）](../tools/gacutil-exe-gac-tool.md)从全局程序集缓存中删除程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-135">Explains how to use the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to remove an assembly from the global assembly cache.</span></span>  
  
[<span data-ttu-id="45485-136">将服务组件和全局程序集缓存结合使用</span><span class="sxs-lookup"><span data-stu-id="45485-136">Using Serviced Components with the Global Assembly Cache</span></span>](use-serviced-components-with-the-gac.md)  
<span data-ttu-id="45485-137">说明服务组件（托管 COM+ 组件）应置于全局程序集缓存中的原因。</span><span class="sxs-lookup"><span data-stu-id="45485-137">Explains why serviced components (managed COM+ components) should be placed in the global assembly cache.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="45485-138">相关章节</span><span class="sxs-lookup"><span data-stu-id="45485-138">Related Sections</span></span>  

[<span data-ttu-id="45485-139">创建程序集</span><span class="sxs-lookup"><span data-stu-id="45485-139">Creating Assemblies</span></span>](../../standard/assembly/create.md)  
<span data-ttu-id="45485-140">概述创建程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-140">Provides an overview of creating assemblies.</span></span>  
  
[<span data-ttu-id="45485-141">全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="45485-141">Global Assembly Cache</span></span>](gac.md)  
<span data-ttu-id="45485-142">描述全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="45485-142">Describes the global assembly cache.</span></span>  
  
[<span data-ttu-id="45485-143">如何：查看程序集内容</span><span class="sxs-lookup"><span data-stu-id="45485-143">How to: View Assembly Contents</span></span>](../../standard/assembly/view-contents.md)  
<span data-ttu-id="45485-144">说明如何使用 [Ildasm.exe（IL 反汇编程序）](../tools/ildasm-exe-il-disassembler.md)来查看程序集中的 Microsoft 中间语言 (MSIL) 信息。</span><span class="sxs-lookup"><span data-stu-id="45485-144">Explains how to use the [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in an assembly.</span></span>  
  
[<span data-ttu-id="45485-145">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="45485-145">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)  
<span data-ttu-id="45485-146">描述公共语言运行时如何查找并加载构成应用程序的程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-146">Describes how the common language runtime locates and loads the assemblies that make up your application.</span></span>  
  
[<span data-ttu-id="45485-147">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="45485-147">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="45485-148">描述托管应用程序的构造块 - 程序集。</span><span class="sxs-lookup"><span data-stu-id="45485-148">Describes assemblies, the building blocks of managed applications.</span></span>
