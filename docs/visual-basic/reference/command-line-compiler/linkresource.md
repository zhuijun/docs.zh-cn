---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 43ebb61efa26ed11af573e2c4e73a6fd71ac0902
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403195"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="89e59-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89e59-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="89e59-103">创建指向托管资源的链接。</span><span class="sxs-lookup"><span data-stu-id="89e59-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e59-104">语法</span><span class="sxs-lookup"><span data-stu-id="89e59-104">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="89e59-105">or</span><span class="sxs-lookup"><span data-stu-id="89e59-105">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="89e59-106">自变量</span><span class="sxs-lookup"><span data-stu-id="89e59-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="89e59-107">必需。</span><span class="sxs-lookup"><span data-stu-id="89e59-107">Required.</span></span> <span data-ttu-id="89e59-108">要链接到程序集的资源文件。</span><span class="sxs-lookup"><span data-stu-id="89e59-108">The resource file to link to the assembly.</span></span> <span data-ttu-id="89e59-109">如果文件名包含空格，则将名称括在引号内 (" ")。</span><span class="sxs-lookup"><span data-stu-id="89e59-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="89e59-110">可选。</span><span class="sxs-lookup"><span data-stu-id="89e59-110">Optional.</span></span> <span data-ttu-id="89e59-111">资源的逻辑名称。</span><span class="sxs-lookup"><span data-stu-id="89e59-111">The logical name for the resource.</span></span> <span data-ttu-id="89e59-112">用于加载资源的名称。</span><span class="sxs-lookup"><span data-stu-id="89e59-112">The name that is used to load the resource.</span></span> <span data-ttu-id="89e59-113">默认值是文件的名称。</span><span class="sxs-lookup"><span data-stu-id="89e59-113">The default is the name of the file.</span></span> <span data-ttu-id="89e59-114">可以选择在程序集清单中指定文件是公共还是专用的，示例：`-linkres:filename.res,myname.res,public`。</span><span class="sxs-lookup"><span data-stu-id="89e59-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="89e59-115">默认情况下，`filename` 在程序集中是公共的。</span><span class="sxs-lookup"><span data-stu-id="89e59-115">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89e59-116">备注</span><span class="sxs-lookup"><span data-stu-id="89e59-116">Remarks</span></span>  
 <span data-ttu-id="89e59-117">`-linkresource` 选项不会将资源文件嵌入到输出文件中；使用 `-resource` 选项来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="89e59-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="89e59-118">`-linkresource` 选项需要除 `-target:module` 之外的任一 `-target` 选项。</span><span class="sxs-lookup"><span data-stu-id="89e59-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="89e59-119">例如，如果 `filename` 是由 [Resgen.exe（资源文件生成器）](../../../framework/tools/resgen-exe-resource-file-generator.md)创建的或在开发环境中创建的 .NET Framework 资源文件，则可使用 <xref:System.Resources> 命名空间中的成员来访问它。</span><span class="sxs-lookup"><span data-stu-id="89e59-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="89e59-120">（有关详细信息，请参阅 <xref:System.Resources.ResourceManager>。）若要在运行时访问所有其他资源，请使用 <xref:System.Reflection.Assembly> 类中以 `GetManifestResource` 开头的方法。</span><span class="sxs-lookup"><span data-stu-id="89e59-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="89e59-121">文件名可以是任何文件格式。</span><span class="sxs-lookup"><span data-stu-id="89e59-121">The file name can be any file format.</span></span> <span data-ttu-id="89e59-122">例如，你可能希望生成程序集的本机 DLL 部分，从而可将它安装到全局程序集缓存中，并且可从该程序集中的托管代码访问它。</span><span class="sxs-lookup"><span data-stu-id="89e59-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="89e59-123">`-linkresource` 的缩写形式是 `-linkres`。</span><span class="sxs-lookup"><span data-stu-id="89e59-123">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89e59-124">`-linkresource` 选项在Visual Studio 开发环境内无法使用；仅当从命令行编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="89e59-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89e59-125">示例</span><span class="sxs-lookup"><span data-stu-id="89e59-125">Example</span></span>  
 <span data-ttu-id="89e59-126">下面的代码编译 `in.vb` 并链接到资源文件 `rf.resource`。</span><span class="sxs-lookup"><span data-stu-id="89e59-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="89e59-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="89e59-127">See also</span></span>

- [<span data-ttu-id="89e59-128">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="89e59-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="89e59-129">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89e59-129">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="89e59-130">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89e59-130">-resource (Visual Basic)</span></span>](resource.md)
- [<span data-ttu-id="89e59-131">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="89e59-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
