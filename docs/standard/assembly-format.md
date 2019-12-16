---
title: ".NET 程序集文件格式"
description: "了解 .NET 程序集文件格式，使用它描述和包含 .NET 应用和库。"
keywords: ".NET、.NET Core"
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.translationtype: HT
ms.sourcegitcommit: 75642ff3beb4462faa9068db76c89f3cb5f75ab8
ms.openlocfilehash: 47e895274f6d400639878e0bd5c700e04b554ce5
ms.contentlocale: zh-cn
ms.lasthandoff: 08/21/2017

---

# <a name="net-assembly-file-format"></a><span data-ttu-id="299b3-104">.NET 程序集文件格式</span><span class="sxs-lookup"><span data-stu-id="299b3-104">.NET Assembly File Format</span></span>

<span data-ttu-id="299b3-105">.NET 定义用于充分描述和包含 .NET 程序的二进制文件格式 -“程序集”。</span><span class="sxs-lookup"><span data-stu-id="299b3-105">.NET defines a binary file format - "assembly" - that is used to fully-describe and contain .NET programs.</span></span> <span data-ttu-id="299b3-106">程序集用于程序本身以及所有依赖库。</span><span class="sxs-lookup"><span data-stu-id="299b3-106">Assemblies are used for the programs themselves as well as any dependent libraries.</span></span> <span data-ttu-id="299b3-107">一个 .NET 程序可作为多个程序集中的其中一个运行，除了相应的 .NET 实现外，无需其他项目。</span><span class="sxs-lookup"><span data-stu-id="299b3-107">A .NET program can be executed as one of more assemblies, with no other required artifacts, beyond the appropriate .NET implementation.</span></span> <span data-ttu-id="299b3-108">本机依赖项（包括操作系统 API）是一个需要单独考虑的问题，虽然有时会使用 .NET 程序集格式来描述它，但并未将它包含在此格式内（例如，WinRT）。</span><span class="sxs-lookup"><span data-stu-id="299b3-108">Native dependencies, including operating system APIs, are a separate concern and are not contained within the .NET assembly format, although are sometimes described with this format (for example, WinRT).</span></span>

> <span data-ttu-id="299b3-109">每个 CLI 组件都带有特定于该组件、用于声明、实现和引用的元数据。</span><span class="sxs-lookup"><span data-stu-id="299b3-109">Each CLI component carries the metadata for declarations, implementations, and references specific to that component.</span></span> <span data-ttu-id="299b3-110">因此，特定于组件的元数据被称为组件元数据，并且自 ECMA 335 I.9.1 生成的组件被认为是自描述组件和程序集。</span><span class="sxs-lookup"><span data-stu-id="299b3-110">Therefore, the component-specific metadata is referred to as component metadata, and the resulting component is said to be self-describing – from ECMA 335 I.9.1, Components and assemblies.</span></span>

<span data-ttu-id="299b3-111">该格式完全被指定并标准化为 ECMA 335。</span><span class="sxs-lookup"><span data-stu-id="299b3-111">The format is fully specified and standardized as ECMA 335.</span></span> <span data-ttu-id="299b3-112">所有 .NET 编译器和运行时都使用此格式。</span><span class="sxs-lookup"><span data-stu-id="299b3-112">All .NET compilers and runtimes use this format.</span></span> <span data-ttu-id="299b3-113">已编入文档、偶尔更新的二进制格式的出现对于互操作性而言是一个主要优势（也可以说是需求）。</span><span class="sxs-lookup"><span data-stu-id="299b3-113">The presence of a documented and infrequently updated binary format has been a major benefit (arguably a requirement) for interoperatibility.</span></span> <span data-ttu-id="299b3-114">该格式上一次进行实质更新是在 2005 年 (.NET 2.0)，目的是为了容纳泛型和处理器体系结构。</span><span class="sxs-lookup"><span data-stu-id="299b3-114">The format was last updated in a substantive way in 2005 (.NET 2.0) to accommodate generics and processor architecture.</span></span>

<span data-ttu-id="299b3-115">格式为 CPU 和 OS 不可知。</span><span class="sxs-lookup"><span data-stu-id="299b3-115">The format is CPU- and OS-agnostic.</span></span> <span data-ttu-id="299b3-116">它被用作针对许多芯片和 CPU 的 .NET 实现的一部分。</span><span class="sxs-lookup"><span data-stu-id="299b3-116">It has been used as part of .NET implementations that target many chips and CPUs.</span></span> <span data-ttu-id="299b3-117">虽然格式本身继承了 Windows，但它可用于所有操作系统。</span><span class="sxs-lookup"><span data-stu-id="299b3-117">While the format itself has Windows heritage, it is implementable on any operating system.</span></span> <span data-ttu-id="299b3-118">对于 OS 互操作性，这可以说是一项最重大的选择，因为大部分值存储在 Little-endian 格式中。</span><span class="sxs-lookup"><span data-stu-id="299b3-118">It’s arguably most significant choice for OS interoperability is that most values are stored in little-endian format.</span></span> <span data-ttu-id="299b3-119">它与计算机的指针大小没有特定关联（例如，32 位、64 位）。</span><span class="sxs-lookup"><span data-stu-id="299b3-119">It doesn’t have a specific affinity to machine pointer size (for example, 32-bit, 64-bit).</span></span>

<span data-ttu-id="299b3-120">.NET 程序集格式也详细介绍了给定程序和库的结构。</span><span class="sxs-lookup"><span data-stu-id="299b3-120">The .NET assembly format is also very descriptive about the structure of a given program or library.</span></span> <span data-ttu-id="299b3-121">专门介绍了程序集的内部组件：定义的程序集引用和类型及其内部结构。</span><span class="sxs-lookup"><span data-stu-id="299b3-121">It describes the internal components of an assembly, specifically: assembly references and types defined and their internal structure.</span></span> <span data-ttu-id="299b3-122">工具或 API 可读取和处理此信息以进行显示或做出程序化决策。</span><span class="sxs-lookup"><span data-stu-id="299b3-122">Tools or APIs can read and process this information for display or to make programmatic decisions.</span></span>

## <a name="format"></a><span data-ttu-id="299b3-123">格式</span><span class="sxs-lookup"><span data-stu-id="299b3-123">Format</span></span>

<span data-ttu-id="299b3-124">.NET 二进制格式以 Windows [PE 文件](http://en.wikipedia.org/wiki/Portable_Executable)格式为基础。</span><span class="sxs-lookup"><span data-stu-id="299b3-124">The .NET binary format is based on the Windows [PE file](http://en.wikipedia.org/wiki/Portable_Executable) format.</span></span> <span data-ttu-id="299b3-125">实际上，.NET 类库符合 Windows PE，咋看之下会显示为 Windows 动态链接库 (DLL) 或应用程序可执行文件 (EXE)。</span><span class="sxs-lookup"><span data-stu-id="299b3-125">In fact, .NET class libraries are conformant Windows PEs, and appear on first glance to be Windows dynamic link libraries (DLLs) or application executables (EXEs).</span></span> <span data-ttu-id="299b3-126">此特性在 Windows 上十分有用，它们可以伪装成本地可执行二进制文件，并获得相同的处理方式（例如，OS 加载，PE 工具）。</span><span class="sxs-lookup"><span data-stu-id="299b3-126">This is a very useful characteristic on Windows, where they can masquerade as native executable binaries and get some of the same treatment (for example, OS load, PE tools).</span></span>

![程序集头](./media/assembly-format/assembly-headers.png)

<span data-ttu-id="299b3-128">来自 ECMA 335 II.25.1 的程序集头，运行时文件格式结构。</span><span class="sxs-lookup"><span data-stu-id="299b3-128">Assembly Headers from ECMA 335 II.25.1, Structure of the runtime file format.</span></span>

## <a name="processing-the-assemblies"></a><span data-ttu-id="299b3-129">处理程序集</span><span class="sxs-lookup"><span data-stu-id="299b3-129">Processing the Assemblies</span></span>

<span data-ttu-id="299b3-130">可以编写工具或 API 来处理程序集。</span><span class="sxs-lookup"><span data-stu-id="299b3-130">It is possible to write tools or APIs to process assemblies.</span></span> <span data-ttu-id="299b3-131">程序集信息能够在运行时做出程序化决策、重新编写程序集、在编辑器中提供 API IntelliSense 以及生成文档。</span><span class="sxs-lookup"><span data-stu-id="299b3-131">Assembly information enables making programmatic decisions at runtime, re-writing assemblies, providing API IntelliSense in an editor and generating documentation.</span></span> <span data-ttu-id="299b3-132"><xref:System.Reflection?displayProperty=fullName> 和 [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) 是常用于此目的的典型工具。</span><span class="sxs-lookup"><span data-stu-id="299b3-132"><xref:System.Reflection?displayProperty=fullName> and [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) are good examples of tools that are frequently used for this purpose.</span></span>
