---
title: 示例编译命令行
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 496627d3b77b0382ae7d15c8225a6fbd41f1db73
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403117"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="b454e-102">示例编译命令行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b454e-102">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="b454e-103">作为从 Visual Studio 中编译 Visual Basic 程序的替代方法，可以从命令行进行编译，以生成可执行 (.exe) 文件或动态链接库 (.dll) 文件。</span><span class="sxs-lookup"><span data-stu-id="b454e-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="b454e-104">Visual Basic 命令行编译器支持一组完整的选项，这些选项控制输入和输出文件、程序集以及调试和预处理器选项。</span><span class="sxs-lookup"><span data-stu-id="b454e-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="b454e-105">每个选项都以两种可互换形式提供：`-option` 和 `/option`。</span><span class="sxs-lookup"><span data-stu-id="b454e-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="b454e-106">此文档仅显示 `-option` 形式。</span><span class="sxs-lookup"><span data-stu-id="b454e-106">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="b454e-107">下表列出可以进行修改以供自己使用的一些示例命令行。</span><span class="sxs-lookup"><span data-stu-id="b454e-107">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="b454e-108">功能</span><span class="sxs-lookup"><span data-stu-id="b454e-108">To</span></span>|<span data-ttu-id="b454e-109">使用</span><span class="sxs-lookup"><span data-stu-id="b454e-109">Use</span></span>|
|--------|---------|
|<span data-ttu-id="b454e-110">编译 File.vb 并创建 File.exe</span><span class="sxs-lookup"><span data-stu-id="b454e-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="b454e-111">编译 File.vb 并创建 File.dll</span><span class="sxs-lookup"><span data-stu-id="b454e-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="b454e-112">编译 File.vb 并创建 My.exe</span><span class="sxs-lookup"><span data-stu-id="b454e-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="b454e-113">编译 File.vb 并创建库和名为 File.dll 的引用程序集</span><span class="sxs-lookup"><span data-stu-id="b454e-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="b454e-114">编译当前目录中的所有 Visual Basic 文件（打开了优化并定义了 `DEBUG` 符号），生成 File2.exe</span><span class="sxs-lookup"><span data-stu-id="b454e-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="b454e-115">编译当前目录中的所有 Visual Basic 文件，生成 File2.dll 的调试版本而不显示徽标或警告</span><span class="sxs-lookup"><span data-stu-id="b454e-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="b454e-116">将当前目录中的所有 Visual Basic 文件编译为 Something.dll</span><span class="sxs-lookup"><span data-stu-id="b454e-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="b454e-117">使用 Visual Studio IDE 生成项目时，可以在输出窗口中显示有关关联 vbc  命令及其编译器选项的信息。</span><span class="sxs-lookup"><span data-stu-id="b454e-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="b454e-118">若要显示此信息，请打开[“选项”对话框、“项目和解决方案”、“生成和运行”](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然后将“MSBuild 项目生成输出详细信息”  设置为“普通”  或更高级别的详细程度。</span><span class="sxs-lookup"><span data-stu-id="b454e-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="b454e-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="b454e-119">See also</span></span>

- [<span data-ttu-id="b454e-120">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="b454e-120">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b454e-121">条件编译</span><span class="sxs-lookup"><span data-stu-id="b454e-121">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
