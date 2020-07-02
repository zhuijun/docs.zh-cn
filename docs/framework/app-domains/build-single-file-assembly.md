---
title: 如何：生成 .NET Framework 单文件程序集
description: 了解如何在 .NET 中生成单文件程序集。 单文件程序集可以是面向 .NET 的库 (.dll)，也可以是可执行程序 (.exe) 文件。
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: 482a973631e899b8d4bfc4640eef1ea26173605e
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104928"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="b6e85-104">如何：生成 .NET Framework 单文件程序集</span><span class="sxs-lookup"><span data-stu-id="b6e85-104">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="b6e85-105">单文件程序集（最简单的程序集类型）包含类型信息和实现，以及[程序集清单](../../standard/assembly/manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e85-105">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="b6e85-106">可以使用命令行编译器或 Visual Studio 创建面向 .NET Framework 的单文件程序集。</span><span class="sxs-lookup"><span data-stu-id="b6e85-106">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="b6e85-107">默认情况下，编译器创建扩展名为 .exe 的程序集文件。</span><span class="sxs-lookup"><span data-stu-id="b6e85-107">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="b6e85-108">适用于 C# 和 Visual Basic 的 Visual Studio 只能用于创建单文件程序集。</span><span class="sxs-lookup"><span data-stu-id="b6e85-108">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="b6e85-109">如果要创建多文件程序集，则必须使用命令行编译器或 Visual C++。</span><span class="sxs-lookup"><span data-stu-id="b6e85-109">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="b6e85-110">以下步骤说明如何使用命令行编译器创建单文件程序集。</span><span class="sxs-lookup"><span data-stu-id="b6e85-110">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="b6e85-111">创建扩展名为 .exe 的程序集</span><span class="sxs-lookup"><span data-stu-id="b6e85-111">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="b6e85-112">在命令提示符处，键入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b6e85-112">At the command prompt, type the following command:</span></span>

<span data-ttu-id="b6e85-113">\<*compiler command*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="b6e85-113">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="b6e85-114">在此命令中，“compiler command”是代码模块中所用语言的编译器命令，“module name”是要编译为程序集的代码模块的名称。</span><span class="sxs-lookup"><span data-stu-id="b6e85-114">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="b6e85-115">以下示例从名为 `myCode` 的代码模块创建名为 myCode.exe 的程序集。</span><span class="sxs-lookup"><span data-stu-id="b6e85-115">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="b6e85-116">创建扩展名为 .exe 的程序集并指定输出文件名</span><span class="sxs-lookup"><span data-stu-id="b6e85-116">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="b6e85-117">在命令提示符处，键入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b6e85-117">At the command prompt, type the following command:</span></span>

<span data-ttu-id="b6e85-118">\<*compiler command*> /out:\<*file name*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="b6e85-118">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="b6e85-119">在此命令中，“compiler command”是代码模块中所用语言的编译器命令，“file name”是输出文件名称，而“module name”是要编译为程序集的代码模块的名称。</span><span class="sxs-lookup"><span data-stu-id="b6e85-119">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="b6e85-120">以下示例从名为 `myCode` 的代码模块创建名为 myAssembly.exe 的程序集。</span><span class="sxs-lookup"><span data-stu-id="b6e85-120">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="b6e85-121">创建库程序集</span><span class="sxs-lookup"><span data-stu-id="b6e85-121">Create library assemblies</span></span>
 <span data-ttu-id="b6e85-122">库程序集与类库相似。</span><span class="sxs-lookup"><span data-stu-id="b6e85-122">A library assembly is similar to a class library.</span></span> <span data-ttu-id="b6e85-123">它包含将由其他程序集引用的类型，但没有开始执行的入口点。</span><span class="sxs-lookup"><span data-stu-id="b6e85-123">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="b6e85-124">要创建库程序集，请在命令提示符处键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="b6e85-124">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="b6e85-125">\<*compiler command*> -t:library \<*module name*></span><span class="sxs-lookup"><span data-stu-id="b6e85-125">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="b6e85-126">在此命令中，“compiler command”是代码模块中所用语言的编译器命令，“module name”是要编译为程序集的代码模块的名称。</span><span class="sxs-lookup"><span data-stu-id="b6e85-126">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="b6e85-127">也可以使用其他编译器选项，例如 -out: 选项。</span><span class="sxs-lookup"><span data-stu-id="b6e85-127">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="b6e85-128">以下示例从名为 `myCode` 的代码模块创建名为 myCodeAssembly.dll 的库程序集。</span><span class="sxs-lookup"><span data-stu-id="b6e85-128">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="b6e85-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="b6e85-129">See also</span></span>

- [<span data-ttu-id="b6e85-130">创建程序集</span><span class="sxs-lookup"><span data-stu-id="b6e85-130">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="b6e85-131">多文件程序集</span><span class="sxs-lookup"><span data-stu-id="b6e85-131">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="b6e85-132">如何：生成多文件程序集</span><span class="sxs-lookup"><span data-stu-id="b6e85-132">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="b6e85-133">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="b6e85-133">Program with assemblies</span></span>](../../standard/assembly/index.md)
