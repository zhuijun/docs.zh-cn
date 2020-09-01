---
description: C# 编译器选项
title: C# 编译器选项
ms.date: 07/20/2015
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: bcb246055ecb553bbefad2a0d5c95bf6a083ee6f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125522"
---
# <a name="c-compiler-options"></a><span data-ttu-id="2055e-103">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="2055e-103">C# Compiler Options</span></span>

<span data-ttu-id="2055e-104">编译器生成可执行 (.exe) 文件、动态链接库 (.dll) 或者代码模块 (.netmodule)。</span><span class="sxs-lookup"><span data-stu-id="2055e-104">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="2055e-105">每个编译器选项均有两种形式： **-option** 和 **/option**。</span><span class="sxs-lookup"><span data-stu-id="2055e-105">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="2055e-106">此文档仅介绍 **-option** 形式。</span><span class="sxs-lookup"><span data-stu-id="2055e-106">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="2055e-107">在 Visual Studio 中，可在 web.config 文件中设置编译器选项。</span><span class="sxs-lookup"><span data-stu-id="2055e-107">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="2055e-108">有关详细信息，请参阅 [\<compiler> 元素](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)。</span><span class="sxs-lookup"><span data-stu-id="2055e-108">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2055e-109">在本节中</span><span class="sxs-lookup"><span data-stu-id="2055e-109">In this section</span></span>

- <span data-ttu-id="2055e-110">[使用 csc.exe 的命令行生成](command-line-building-with-csc-exe.md) 有关从命令行生成 Visual C# 应用程序的信息。</span><span class="sxs-lookup"><span data-stu-id="2055e-110">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="2055e-111">[如何为 Visual Studio 命令行设置环境变量](how-to-set-environment-variables-for-the-visual-studio-command-line.md) 提供运行 vsvars32.bat\*\* 以启用命令行生成的步骤。</span><span class="sxs-lookup"><span data-stu-id="2055e-111">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *vsvars32.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="2055e-112">[按类别列出的 C# 编译器选项](listed-by-category.md) 编译器选项的分类列表。</span><span class="sxs-lookup"><span data-stu-id="2055e-112">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="2055e-113">[按字母顺序列出的 C# 编译器选项](listed-alphabetically.md) 编译器选项按字母顺序列出的列表。</span><span class="sxs-lookup"><span data-stu-id="2055e-113">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="2055e-114">相关章节</span><span class="sxs-lookup"><span data-stu-id="2055e-114">Related sections</span></span>

- <span data-ttu-id="2055e-115">[生成页，项目设计器](/visualstudio/ide/reference/build-page-project-designer-csharp) 介绍了如何设置属性来控制项目的编译、生成和调试方式。</span><span class="sxs-lookup"><span data-stu-id="2055e-115">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="2055e-116">介绍了 Visual C# 项目的自定义生成步骤。</span><span class="sxs-lookup"><span data-stu-id="2055e-116">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="2055e-117">[默认和自定义生成](/visualstudio/ide/compiling-and-building-in-visual-studio) 有关生成类型和配置的信息。</span><span class="sxs-lookup"><span data-stu-id="2055e-117">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="2055e-118">[准备和管理生成](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) 介绍了 Visual Studio 开发环境中的生成过程。</span><span class="sxs-lookup"><span data-stu-id="2055e-118">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
