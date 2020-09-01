---
description: 如何为 Visual Studio 命令行设置环境变量
title: 如何为 Visual Studio 命令行设置环境变量
ms.date: 12/20/2019
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: b985c85e2fddce459ed68b3d07ba7d54a8b2d0a7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125600"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="819a6-103">如何为 Visual Studio 命令行设置环境变量</span><span class="sxs-lookup"><span data-stu-id="819a6-103">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="819a6-104">VsDevCmd.bat 文件设置适当的环境变量来生成命令行。</span><span class="sxs-lookup"><span data-stu-id="819a6-104">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="819a6-105">Visual Studio 2015 及更早版本基于相同目的使用 VSVARS32.bat，而不是 VsDevCmd.bat。</span><span class="sxs-lookup"><span data-stu-id="819a6-105">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="819a6-106">此文件保存在 \Program Files\Microsoft Visual Studio\\Version\*\* \Common7\Tools 或 Program Files (x86)\Microsoft Visual Studio\\Version\*\* \Common7\Tools。</span><span class="sxs-lookup"><span data-stu-id="819a6-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="819a6-107">如果安装了 Visual Studio 当前版本的计算机上还安装有 Visual Studio 的早期版本，则不可在同一命令提示符窗口中运行不同版本的 VsDevCmd.bat 和 VSVARS32.BAT。</span><span class="sxs-lookup"><span data-stu-id="819a6-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="819a6-108">转而应在其自身的窗口中运行各版本的命令。</span><span class="sxs-lookup"><span data-stu-id="819a6-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="819a6-109">若要运行 VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="819a6-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="819a6-110">从“开始”\*\*\*\* 菜单，打开“VS 2019 开发人员命令提示”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="819a6-110">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="819a6-111">该提示位于“Visual Studio 2019”\*\*\*\* 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="819a6-111">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="819a6-112">更改为安装目录的 \Program Files\Microsoft Visual Studio\\Version\\Offering\Common7\Tools 或 \Program Files (x86)\Microsoft Visual Studio\\Version\\Offering\Common7\Tools 子目录。</span><span class="sxs-lookup"><span data-stu-id="819a6-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="819a6-113">（Version \*\* 为 2019\*\*，即当前版本。</span><span class="sxs-lookup"><span data-stu-id="819a6-113">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="819a6-114">Offering\*\* 是 Enterprise**、Professional** 或 Community\*\*。）</span><span class="sxs-lookup"><span data-stu-id="819a6-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="819a6-115">通过键入“VsDevCmd”\*\*\*\* 运行 VsDevCmd.bat。</span><span class="sxs-lookup"><span data-stu-id="819a6-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="819a6-116">VsDevCmd.bat 可能因计算机而异。</span><span class="sxs-lookup"><span data-stu-id="819a6-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="819a6-117">请勿使用其他计算机上的 VsDevCmd.bat 替换缺失或损坏的 VsDevCmd.bat 文件。</span><span class="sxs-lookup"><span data-stu-id="819a6-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="819a6-118">而是应重新运行安装程序以替换丢失的文件。</span><span class="sxs-lookup"><span data-stu-id="819a6-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="819a6-119">适用于 VsDevCmd.BAT 的选项</span><span class="sxs-lookup"><span data-stu-id="819a6-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="819a6-120">若要查看适用于 VsDevCmd.BAT 的选项，请运行以下包含 `-help` 选项的命令：</span><span class="sxs-lookup"><span data-stu-id="819a6-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="819a6-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="819a6-121">See also</span></span>

- [<span data-ttu-id="819a6-122">在命令行上使用 csc.exe 生成</span><span class="sxs-lookup"><span data-stu-id="819a6-122">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
