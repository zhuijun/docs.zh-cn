---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 9fb9287f9472d4b33eff4cb601aff5eed370b2c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065562"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="a5950-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="a5950-102">-moduleassemblyname</span></span>

<span data-ttu-id="a5950-103">指定此模块所属程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="a5950-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5950-104">语法</span><span class="sxs-lookup"><span data-stu-id="a5950-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5950-105">自变量</span><span class="sxs-lookup"><span data-stu-id="a5950-105">Arguments</span></span>  
  
|<span data-ttu-id="a5950-106">术语</span><span class="sxs-lookup"><span data-stu-id="a5950-106">Term</span></span>|<span data-ttu-id="a5950-107">定义</span><span class="sxs-lookup"><span data-stu-id="a5950-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="a5950-108">此模块所属程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="a5950-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5950-109">备注</span><span class="sxs-lookup"><span data-stu-id="a5950-109">Remarks</span></span>  

 <span data-ttu-id="a5950-110">仅当指定了 `-target:module` 选项时，编译器才处理 `-moduleassemblyname` 选项。</span><span class="sxs-lookup"><span data-stu-id="a5950-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="a5950-111">这将导致编译器创建模块。</span><span class="sxs-lookup"><span data-stu-id="a5950-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="a5950-112">编译器创建的模块仅对使用 `-moduleassemblyname` 选项指定的程序集有效。</span><span class="sxs-lookup"><span data-stu-id="a5950-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="a5950-113">如果将模块放在不同的程序集中，则会发生运行时错误。</span><span class="sxs-lookup"><span data-stu-id="a5950-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="a5950-114">仅当满足以下条件时，才需要 `-moduleassemblyname` 选项：</span><span class="sxs-lookup"><span data-stu-id="a5950-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="a5950-115">模块中的数据类型需要访问所引用程序集中的 `Friend` 类型。</span><span class="sxs-lookup"><span data-stu-id="a5950-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="a5950-116">引用的程序集已获得友元程序集访问权限，可访问将在其中生成模块的程序集。</span><span class="sxs-lookup"><span data-stu-id="a5950-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="a5950-117">有关创建模块的详细信息，请参阅 [-target (Visual Basic)](target.md)。</span><span class="sxs-lookup"><span data-stu-id="a5950-117">For more information about creating a module, see [-target (Visual Basic)](target.md).</span></span> <span data-ttu-id="a5950-118">有关友元程序集的详细信息，请参阅[友元程序集](../../../standard/assembly/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="a5950-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5950-119">`-moduleassemblyname` 选项在 Visual Studio 开发环境内无法使用；仅当从命令提示符编译时才可用。</span><span class="sxs-lookup"><span data-stu-id="a5950-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5950-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="a5950-120">See also</span></span>

- [<span data-ttu-id="a5950-121">如何：生成单文件程序集</span><span class="sxs-lookup"><span data-stu-id="a5950-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="a5950-122">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="a5950-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a5950-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5950-123">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="a5950-124">-main</span><span class="sxs-lookup"><span data-stu-id="a5950-124">-main</span></span>](main.md)
- [<span data-ttu-id="a5950-125">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5950-125">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="a5950-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="a5950-126">-addmodule</span></span>](addmodule.md)
- [<span data-ttu-id="a5950-127">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="a5950-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="a5950-128">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="a5950-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="a5950-129">友元程序集</span><span class="sxs-lookup"><span data-stu-id="a5950-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
