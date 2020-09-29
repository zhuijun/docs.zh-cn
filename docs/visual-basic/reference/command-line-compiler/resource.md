---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 726f3dd179aedb39b578c8580c9632182af2d5e0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085121"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="5acc0-102">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5acc0-102">-resource (Visual Basic)</span></span>

<span data-ttu-id="5acc0-103">将托管资源嵌入程序集。</span><span class="sxs-lookup"><span data-stu-id="5acc0-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5acc0-104">语法</span><span class="sxs-lookup"><span data-stu-id="5acc0-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="5acc0-105">or</span><span class="sxs-lookup"><span data-stu-id="5acc0-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5acc0-106">自变量</span><span class="sxs-lookup"><span data-stu-id="5acc0-106">Arguments</span></span>  
  
|<span data-ttu-id="5acc0-107">术语</span><span class="sxs-lookup"><span data-stu-id="5acc0-107">Term</span></span>|<span data-ttu-id="5acc0-108">定义</span><span class="sxs-lookup"><span data-stu-id="5acc0-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="5acc0-109">必需。</span><span class="sxs-lookup"><span data-stu-id="5acc0-109">Required.</span></span> <span data-ttu-id="5acc0-110">要嵌入到输出文件中的资源文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5acc0-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="5acc0-111">默认情况下，`filename` 在程序集中是公共的。</span><span class="sxs-lookup"><span data-stu-id="5acc0-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="5acc0-112">如果文件名包含空格，则将名称括在引号 (" ") 内。</span><span class="sxs-lookup"><span data-stu-id="5acc0-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="5acc0-113">可选。</span><span class="sxs-lookup"><span data-stu-id="5acc0-113">Optional.</span></span> <span data-ttu-id="5acc0-114">资源的逻辑名称；用于加载资源的名称。</span><span class="sxs-lookup"><span data-stu-id="5acc0-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="5acc0-115">默认值是文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5acc0-115">The default is the name of the file.</span></span> <span data-ttu-id="5acc0-116">可以选择在程序集清单中指定资源是公共还是专用的，如下所示：`-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="5acc0-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5acc0-117">备注</span><span class="sxs-lookup"><span data-stu-id="5acc0-117">Remarks</span></span>  

 <span data-ttu-id="5acc0-118">使用 `-linkresource` 将资源链接到程序集，而不将资源文件置于输出文件中。</span><span class="sxs-lookup"><span data-stu-id="5acc0-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="5acc0-119">例如，如果 `filename` [是由资源文件生成器 (Resgen.exe)](../../../framework/tools/resgen-exe-resource-file-generator.md) 创建的或在开发环境中创建的 .NET Framework 资源文件，则可使用 <xref:System.Resources> 命名空间中的成员来访问它（有关详细信息，请参阅 <xref:System.Resources.ResourceManager>）。</span><span class="sxs-lookup"><span data-stu-id="5acc0-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="5acc0-120">若要在运行时访问所有其他资源，请使用以下方法之一：<xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、<xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 或 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>。</span><span class="sxs-lookup"><span data-stu-id="5acc0-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="5acc0-121">`-resource` 的缩写形式是 `-res`。</span><span class="sxs-lookup"><span data-stu-id="5acc0-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="5acc0-122">有关如何在 Visual Studio IDE 中设置 `-resource` 的信息，请参阅[管理应用程序资源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="5acc0-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5acc0-123">示例</span><span class="sxs-lookup"><span data-stu-id="5acc0-123">Example</span></span>  

 <span data-ttu-id="5acc0-124">下面的代码编译 `In.vb` 并附加资源文件 `Rf.resource`。</span><span class="sxs-lookup"><span data-stu-id="5acc0-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5acc0-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="5acc0-125">See also</span></span>

- [<span data-ttu-id="5acc0-126">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="5acc0-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="5acc0-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="5acc0-127">-win32resource</span></span>](win32resource.md)
- [<span data-ttu-id="5acc0-128">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5acc0-128">-linkresource (Visual Basic)</span></span>](linkresource.md)
- [<span data-ttu-id="5acc0-129">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5acc0-129">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="5acc0-130">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="5acc0-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
