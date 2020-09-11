---
description: -linkresource (C# 编译器选项)
title: -linkresource (C# 编译器选项)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: cd1150f3fa0dd0eca4e9352ce3809e73a15126c7
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466100"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="63fe3-103">-linkresource (C# 编译器选项)</span><span class="sxs-lookup"><span data-stu-id="63fe3-103">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="63fe3-104">在输出文件中创建指向 .NET 资源的链接。</span><span class="sxs-lookup"><span data-stu-id="63fe3-104">Creates a link to a .NET resource in the output file.</span></span> <span data-ttu-id="63fe3-105">不会在输出文件中添加资源文件。</span><span class="sxs-lookup"><span data-stu-id="63fe3-105">The resource file is not added to the output file.</span></span> <span data-ttu-id="63fe3-106">这不同于会在输出文件中嵌入资源文件的 [-resource](./resource-compiler-option.md) 选项。</span><span class="sxs-lookup"><span data-stu-id="63fe3-106">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63fe3-107">语法</span><span class="sxs-lookup"><span data-stu-id="63fe3-107">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="63fe3-108">自变量</span><span class="sxs-lookup"><span data-stu-id="63fe3-108">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="63fe3-109">希望从程序集链接到的 .NET 资源文件。</span><span class="sxs-lookup"><span data-stu-id="63fe3-109">The .NET resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="63fe3-110">`identifier`（可选）</span><span class="sxs-lookup"><span data-stu-id="63fe3-110">`identifier` (optional)</span></span>  
 <span data-ttu-id="63fe3-111">资源的逻辑名称；用于加载资源的名称。</span><span class="sxs-lookup"><span data-stu-id="63fe3-111">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="63fe3-112">默认值是文件的名称。</span><span class="sxs-lookup"><span data-stu-id="63fe3-112">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="63fe3-113">`accessibility-modifier`（可选）</span><span class="sxs-lookup"><span data-stu-id="63fe3-113">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="63fe3-114">资源的可访问性：public 或 private。</span><span class="sxs-lookup"><span data-stu-id="63fe3-114">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="63fe3-115">默认值为 public。</span><span class="sxs-lookup"><span data-stu-id="63fe3-115">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63fe3-116">备注</span><span class="sxs-lookup"><span data-stu-id="63fe3-116">Remarks</span></span>  
 <span data-ttu-id="63fe3-117">默认情况下，如果使用 C# 编译器创建链接资源，则这些资源在程序集中是公有的。</span><span class="sxs-lookup"><span data-stu-id="63fe3-117">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="63fe3-118">若要使资源变为私有，请将 `private` 指定为可访问性修饰符。</span><span class="sxs-lookup"><span data-stu-id="63fe3-118">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="63fe3-119">不允许使用 `public` 或 `private` 以外的任何其他修饰符。</span><span class="sxs-lookup"><span data-stu-id="63fe3-119">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="63fe3-120">-linkresource 需要某个 [-target](./target-compiler-option.md) 选项（-target:module 除外）\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63fe3-120">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="63fe3-121">例如，如果 `filename` 是由 [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) 创建的或在开发环境中创建的 .NET 资源文件，则可使用 <xref:System.Resources> 命名空间中的成员来访问它。</span><span class="sxs-lookup"><span data-stu-id="63fe3-121">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="63fe3-122">有关详细信息，请参阅 <xref:System.Resources.ResourceManager?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="63fe3-122">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="63fe3-123">对于所有其他资源，请使用 <xref:System.Reflection.Assembly> 类中的 `GetManifestResource` 方法在运行时访问资源。</span><span class="sxs-lookup"><span data-stu-id="63fe3-123">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="63fe3-124">`filename` 中指定的文件可为任何格式。</span><span class="sxs-lookup"><span data-stu-id="63fe3-124">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="63fe3-125">例如，你可能希望生成程序集的本机 DLL 部分，从而可将它安装到全局程序集缓存中，并且可从该程序集中的托管代码访问它。</span><span class="sxs-lookup"><span data-stu-id="63fe3-125">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="63fe3-126">以下示例中的第二个示例演示了如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="63fe3-126">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="63fe3-127">可在程序集链接器中执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="63fe3-127">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="63fe3-128">以下示例中的第三个示例演示了如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="63fe3-128">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="63fe3-129">有关详细信息，请参阅 [Al.exe（程序集链接器）](../../../framework/tools/al-exe-assembly-linker.md)和[使用程序集和全局程序集缓存](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="63fe3-129">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="63fe3-130">-linkres 是 -linkresource 的缩写形式\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="63fe3-130">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="63fe3-131">此编译器选项在 Visual Studio 中不可用，并且无法以编程方式更改。</span><span class="sxs-lookup"><span data-stu-id="63fe3-131">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63fe3-132">示例</span><span class="sxs-lookup"><span data-stu-id="63fe3-132">Example</span></span>  
 <span data-ttu-id="63fe3-133">编译 `in.cs` 并链接到资源文件 `rf.resource`：</span><span class="sxs-lookup"><span data-stu-id="63fe3-133">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="63fe3-134">示例</span><span class="sxs-lookup"><span data-stu-id="63fe3-134">Example</span></span>  
 <span data-ttu-id="63fe3-135">将 `A.cs` 编译为 DLL，链接到本机 DLL N.dll，并将输出文件放在全局程序集缓存 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="63fe3-135">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="63fe3-136">在此示例中，A.dll 和 N.dll 都存在于 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="63fe3-136">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="63fe3-137">示例</span><span class="sxs-lookup"><span data-stu-id="63fe3-137">Example</span></span>  
 <span data-ttu-id="63fe3-138">此示例执行的操作与上一示例相同，但使用程序集链接器选项执行。</span><span class="sxs-lookup"><span data-stu-id="63fe3-138">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="63fe3-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="63fe3-139">See also</span></span>

- [<span data-ttu-id="63fe3-140">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="63fe3-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="63fe3-141">Al.exe（程序集链接器）</span><span class="sxs-lookup"><span data-stu-id="63fe3-141">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="63fe3-142">使用程序集和全局程序集缓存</span><span class="sxs-lookup"><span data-stu-id="63fe3-142">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="63fe3-143">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="63fe3-143">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
