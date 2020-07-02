---
title: 全局程序集缓存
description: 了解全局程序集缓存，即安装了 .NET 公共语言运行时的计算机范围的代码缓存。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
ms.openlocfilehash: 7f08bb4cf279924b12432f259dae8ce5a8474285
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104912"
---
# <a name="global-assembly-cache"></a><span data-ttu-id="ac5f8-103">全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="ac5f8-103">Global Assembly Cache</span></span>
<span data-ttu-id="ac5f8-104">安装了公共语言运行时的每台计算机均具有计算机范围的代码缓存，称为全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-104">Each computer where the Common Language Runtime is installed has a machine-wide code cache called the Global Assembly Cache.</span></span> <span data-ttu-id="ac5f8-105">全局程序集缓存中存储专门指定给由计算机中若干应用程序共享的程序集。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-105">The Global Assembly Cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="ac5f8-106">只能在需要时才通过将程序集安装到全局程序集缓存中来共享程序集。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-106">You should share assemblies by installing them into the Global Assembly Cache only when you need to.</span></span> <span data-ttu-id="ac5f8-107">一般原则是：程序集依赖项保持专用，并将程序集放在应用程序目录中，除非明确要求共享该程序集。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-107">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="ac5f8-108">另外，无需为了使 COM 互操作或非托管代码可以访问程序集而将程序集安装到全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-108">In addition, it is not necessary to install assemblies into the Global Assembly Cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac5f8-109">在有些情况下，很明显不需要将程序集安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-109">There are scenarios where you explicitly do not want to install an assembly into the Global Assembly Cache.</span></span> <span data-ttu-id="ac5f8-110">将组成应用程序的某个程序集置于全局程序集缓存中之后，无法再通过使用 xcopy 命令复制应用程序目录来复制或安装应用程序。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-110">If you place one of the assemblies that make up an application in the Global Assembly Cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="ac5f8-111">必须同时移动全局程序集缓存中的程序集。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-111">You must move the assembly in the Global Assembly Cache as well.</span></span>  
  
 <span data-ttu-id="ac5f8-112">可以通过两种方法将程序集部署到全局程序集缓存：</span><span class="sxs-lookup"><span data-stu-id="ac5f8-112">There are two ways to deploy an assembly into the Global Assembly Cache:</span></span>  
  
- <span data-ttu-id="ac5f8-113">使用专用于全局程序集缓存的安装程序。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-113">Use an installer designed to work with the Global Assembly Cache.</span></span> <span data-ttu-id="ac5f8-114">这是将程序集安装到全局程序集缓存中的首选项。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-114">This is the preferred option for installing assemblies into the Global Assembly Cache.</span></span>  
  
- <span data-ttu-id="ac5f8-115">使用 Windows SDK 提供的名为[全局程序集缓存工具 (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 的开发人员工具。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-115">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md), provided by the Windows SDK.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ac5f8-116">在部署方案中，使用 Windows Installer 将程序集安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-116">In deployment scenarios, use Windows Installer to install assemblies into the Global Assembly Cache.</span></span> <span data-ttu-id="ac5f8-117">仅在开发方案中使用全局程序集缓存工具，因为它不提供 Windows Installer 所能提供的程序集引用计数等功能。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-117">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="ac5f8-118">从 .NET Framework 4 开始，全局程序集缓存的默认位置为 %windir%\Microsoft.NET\assembly。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-118">Starting with the .NET Framework 4, the default location for the Global Assembly Cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="ac5f8-119">在 .NET Framework 的早期版本中，默认位置为 %windir%\assembly。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-119">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="ac5f8-120">管理员通常使用访问控制列表 (ACL) 来保护 systemroot 目录，从而控制写入和执行访问。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-120">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="ac5f8-121">由于全局程序集缓存安装在 systemroot 目录的子目录中，因此它将继承该目录的 ACL。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-121">Because the Global Assembly Cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="ac5f8-122">建议只允许具有“管理员”权限的用户从全局程序集缓存中删除文件。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-122">It is recommended that only users with Administrator privileges be allowed to delete files from the Global Assembly Cache.</span></span>  
  
 <span data-ttu-id="ac5f8-123">部署在全局程序集缓存中的程序集必须使用强名称。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-123">Assemblies deployed in the Global Assembly Cache must have a strong name.</span></span> <span data-ttu-id="ac5f8-124">将程序集添加到全局程序集缓存时，可对组成该程序集的所有文件执行完整性检查。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-124">When an assembly is added to the Global Assembly Cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="ac5f8-125">缓存通过执行这些完整性检查来确保该程序集未被篡改，例如，文件已更改，但清单没有反映出此更改。</span><span class="sxs-lookup"><span data-stu-id="ac5f8-125">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5f8-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="ac5f8-126">See also</span></span>

- [<span data-ttu-id="ac5f8-127">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="ac5f8-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="ac5f8-128">使用程序集和全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="ac5f8-128">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="ac5f8-129">具有强名称的程序集</span><span class="sxs-lookup"><span data-stu-id="ac5f8-129">Strong-Named Assemblies</span></span>](../../standard/assembly/strong-named.md)
