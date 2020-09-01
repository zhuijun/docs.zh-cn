---
description: '@（C# 编译器选项）'
title: '@（C# 编译器选项）'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 89a057cba6e0d23c15fc9b652e5bfbc89b6ecbaa
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128642"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="ab200-103">@（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="ab200-103">@ (C# Compiler Options)</span></span>
<span data-ttu-id="ab200-104">通过 @ 选项，可以指定包含编译器选项和要编译的源代码文件的文件。</span><span class="sxs-lookup"><span data-stu-id="ab200-104">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab200-105">语法</span><span class="sxs-lookup"><span data-stu-id="ab200-105">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ab200-106">自变量</span><span class="sxs-lookup"><span data-stu-id="ab200-106">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="ab200-107">列出了编译器选项或要编译的源代码文件的文件。</span><span class="sxs-lookup"><span data-stu-id="ab200-107">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab200-108">备注</span><span class="sxs-lookup"><span data-stu-id="ab200-108">Remarks</span></span>  
 <span data-ttu-id="ab200-109">编译器选项和源代码文件将由编译器处理，如同在命令行被指定一样。</span><span class="sxs-lookup"><span data-stu-id="ab200-109">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="ab200-110">若要在一次编译中指定多个响应文件，请指定多个响应文件选项。</span><span class="sxs-lookup"><span data-stu-id="ab200-110">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="ab200-111">例如：</span><span class="sxs-lookup"><span data-stu-id="ab200-111">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="ab200-112">在响应文件中，多个编译器选项和源代码文件可以出现在同一行中。</span><span class="sxs-lookup"><span data-stu-id="ab200-112">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="ab200-113">单个编译器选项的指定必须出现在同一行中（不能跨行）。</span><span class="sxs-lookup"><span data-stu-id="ab200-113">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="ab200-114">响应文件的注释可以 # 符号开始。</span><span class="sxs-lookup"><span data-stu-id="ab200-114">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="ab200-115">从响应文件内指定编译器选项就如同在命令行发出这些命令。</span><span class="sxs-lookup"><span data-stu-id="ab200-115">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="ab200-116">有关详细信息，请参阅[从命令行生成](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="ab200-116">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="ab200-117">编译器在遇到命令选项时会进行处理。</span><span class="sxs-lookup"><span data-stu-id="ab200-117">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="ab200-118">因此，命令行参数可以重写先前在响应文件中列出的选项。</span><span class="sxs-lookup"><span data-stu-id="ab200-118">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="ab200-119">反之，响应文件中的选项也将重写先前在命令行或其他响应文件中列出的选项。</span><span class="sxs-lookup"><span data-stu-id="ab200-119">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="ab200-120">C# 提供 csc.rsp 文件，该文件与 csc.exe 文件位于同一目录。</span><span class="sxs-lookup"><span data-stu-id="ab200-120">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="ab200-121">有关 csc.rsp 的详细信息，请参阅 [-noconfig](./noconfig-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="ab200-121">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="ab200-122">不能在 Visual Studio 开发环境中设置此编译器选项，也不能以编程方式对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="ab200-122">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab200-123">示例</span><span class="sxs-lookup"><span data-stu-id="ab200-123">Example</span></span>  
 <span data-ttu-id="ab200-124">以下几行来自示例响应文件：</span><span class="sxs-lookup"><span data-stu-id="ab200-124">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab200-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab200-125">See also</span></span>

- [<span data-ttu-id="ab200-126">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="ab200-126">C# Compiler Options</span></span>](./index.md)
