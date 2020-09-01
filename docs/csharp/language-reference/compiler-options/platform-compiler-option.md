---
description: -platform（C# 编译器选项）
title: -platform（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: e2e4fc37418243ff6998d19165250b895c0a4fa1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124859"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="1d1c8-103">-platform（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="1d1c8-103">-platform (C# Compiler Options)</span></span>

<span data-ttu-id="1d1c8-104">指定公共语言运行时 (CLR) 的哪个版本可以运行程序集。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-104">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>

## <a name="syntax"></a><span data-ttu-id="1d1c8-105">语法</span><span class="sxs-lookup"><span data-stu-id="1d1c8-105">Syntax</span></span>

```console
-platform:string
```

## <a name="parameters"></a><span data-ttu-id="1d1c8-106">参数</span><span class="sxs-lookup"><span data-stu-id="1d1c8-106">Parameters</span></span>

`string` \
<span data-ttu-id="1d1c8-107">anycpu（默认值）、anycpu32bitpreferred、ARM、x64、x86 或 Itanium。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-107">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d1c8-108">备注</span><span class="sxs-lookup"><span data-stu-id="1d1c8-108">Remarks</span></span>

- <span data-ttu-id="1d1c8-109">anycpu（默认值）将程序集编译成可在任意平台上运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-109">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="1d1c8-110">您的应用程序将尽可能作为 64 位进程运行；当只有 32 位模式可用时，才会回退到 32 位。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-110">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>

- <span data-ttu-id="1d1c8-111">anycpu32bitpreferred 将程序集编译成可在任意平台上运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-111">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="1d1c8-112">在同时支持 64 位和 32 位应用程序的系统上，您的应用程序将以32 位模式运行。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-112">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="1d1c8-113">可以仅为针对 .NET Framework 4.5 的项目指定此选项。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-113">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>

- <span data-ttu-id="1d1c8-114">ARM 将程序集编译成可以在具有高级 RISC 计算机 (ARM) 处理器的计算机上运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-114">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>

- <span data-ttu-id="1d1c8-115">ARM64\*\*\*\* 编译程序集以在由 64 位 CLR 在具有支持 A64 指令集的高级 RISC 计算机 (ARM) 处理器的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-115">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>

- <span data-ttu-id="1d1c8-116">x64 将程序集编译成可由支持 AMD64 或 EM64T 指令集的计算机上的 64 位 CLR 运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-116">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>

- <span data-ttu-id="1d1c8-117">x86 将程序集编译成可由 32 位、x86 可兼容 CLR 运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-117">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>

- <span data-ttu-id="1d1c8-118">Itanium 将程序集编译成可由配有 Itanium 处理器的计算机上的 64 位 CLR 运行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-118">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>

<span data-ttu-id="1d1c8-119">在 64 位 Windows 操作系统上：</span><span class="sxs-lookup"><span data-stu-id="1d1c8-119">On a 64-bit Windows operating system:</span></span>

- <span data-ttu-id="1d1c8-120">用 -platform:x86 编译的程序集将在 WOW64 下运行的 32 位 CLR 上执行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-120">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>

- <span data-ttu-id="1d1c8-121">用 -platform:anycpu 编译的 DLL 将在加载它的进程所在的同一 CLR 上执行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-121">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>

- <span data-ttu-id="1d1c8-122">用 -platform:anycpu 编译的可执行文件将在 64 位 CLR 上执行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-122">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>

- <span data-ttu-id="1d1c8-123">用 -platform:anycpu32bitpreferred 编译的可执行文件将在 32 位 CLR 上执行\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-123">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>

<span data-ttu-id="1d1c8-124">anycpu32bitpreferred 设置只对可执行 (.exe) 文件有效，并且需要 .NET Framework 4.5\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-124">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>

<span data-ttu-id="1d1c8-125">有关开发 Windows 64 位操作系统上运行的应用程序的详细信息，请参阅 [64 位应用程序](../../../framework/64-bit-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-125">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1d1c8-126">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="1d1c8-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="1d1c8-127">打开项目的“属性” \*\*\*\* 页。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-127">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="1d1c8-128">单击“生成”\*\*\*\* 属性页。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-128">Click the **Build** property page.</span></span>

3. <span data-ttu-id="1d1c8-129">修改“目标平台”属性，对于针对 .NET Framework 4.5 的项目，选择或清除“首选 32 位”复选框\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-129">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>

> [!NOTE]
> <span data-ttu-id="1d1c8-130">`-platform` 在 Visual C# Express 的开发环境中不可用。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-130">`-platform` is not available in the development environment in Visual C# Express.</span></span>

<span data-ttu-id="1d1c8-131">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-131">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>

## <a name="example"></a><span data-ttu-id="1d1c8-132">示例</span><span class="sxs-lookup"><span data-stu-id="1d1c8-132">Example</span></span>

<span data-ttu-id="1d1c8-133">下面的示例演示如何使用 -platform 选项来指定只有 64 位 Windows 操作系统上的 64 位 CLR 才能运行应用程序\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1d1c8-133">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a><span data-ttu-id="1d1c8-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d1c8-134">See also</span></span>

- [<span data-ttu-id="1d1c8-135">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="1d1c8-135">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="1d1c8-136">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="1d1c8-136">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
