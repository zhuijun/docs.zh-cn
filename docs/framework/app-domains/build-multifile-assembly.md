---
title: 如何：生成多文件程序集
description: 查看示例代码理解过程中的每个步骤，了解如何在 .NET 中生成（创建）多文件程序集。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: a4c298284950ba2989bb73e6d3383b3c4024e6e7
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104946"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="7b9de-103">如何：生成多文件程序集</span><span class="sxs-lookup"><span data-stu-id="7b9de-103">How to: Build a multifile assembly</span></span>

<span data-ttu-id="7b9de-104">本文章介绍如何创建多文件程序集，并提供用于说明过程中每个步骤的代码。</span><span class="sxs-lookup"><span data-stu-id="7b9de-104">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="7b9de-105">适用于 C# 和 Visual Basic 的 Visual Studio IDE 只能用于创建单文件程序集。</span><span class="sxs-lookup"><span data-stu-id="7b9de-105">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="7b9de-106">如果要创建多文件程序集，则必须使用命令行编译器或带有 Visual C++ 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7b9de-106">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="7b9de-107">多文件程序集仅由 .NET Framework 支持。</span><span class="sxs-lookup"><span data-stu-id="7b9de-107">Multifile assemblies are supported by .NET Framework only.</span></span>

## <a name="create-a-multifile-assembly"></a><span data-ttu-id="7b9de-108">创建多文件程序集</span><span class="sxs-lookup"><span data-stu-id="7b9de-108">Create a multifile assembly</span></span>

1. <span data-ttu-id="7b9de-109">将包含程序集中其他模块引用的命名空间的所有文件编译成代码模块。</span><span class="sxs-lookup"><span data-stu-id="7b9de-109">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="7b9de-110">代码模块的默认扩展名为 .netmodule。</span><span class="sxs-lookup"><span data-stu-id="7b9de-110">The default extension for code modules is *.netmodule*.</span></span>

   <span data-ttu-id="7b9de-111">例如，假定 `Stringer` 文件具有一个名为 `myStringer` 的命名空间，其中包括一个名为 `Stringer` 的类。</span><span class="sxs-lookup"><span data-stu-id="7b9de-111">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="7b9de-112">`Stringer` 类包含名为 `StringerMethod` 的方法，此方法将单独一行写入控制台。</span><span class="sxs-lookup"><span data-stu-id="7b9de-112">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. <span data-ttu-id="7b9de-113">使用下面的命令编译此代码：</span><span class="sxs-lookup"><span data-stu-id="7b9de-113">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   <span data-ttu-id="7b9de-114">使用 **/t:** 编译器选项指定 *module* 参数，表明文件应作为模块（而不是作为程序集）编译。</span><span class="sxs-lookup"><span data-stu-id="7b9de-114">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="7b9de-115">编译器生成一个名为 Stringer.netmodule 的模块，可将其添加到程序集中。</span><span class="sxs-lookup"><span data-stu-id="7b9de-115">The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.</span></span>

3. <span data-ttu-id="7b9de-116">编译所有其他模块，使用必要的编译器选项来表明代码中引用的其他模块。</span><span class="sxs-lookup"><span data-stu-id="7b9de-116">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="7b9de-117">此步骤使用 /addmodule 编译器选项。</span><span class="sxs-lookup"><span data-stu-id="7b9de-117">This step uses the **/addmodule** compiler option.</span></span>

   <span data-ttu-id="7b9de-118">在下面的示例中，名为 Client 的代码模块具有一个入口点 `Main` 方法，此方法引用创建于步骤 1 的 Stringer.dll 模块中的方法 。</span><span class="sxs-lookup"><span data-stu-id="7b9de-118">In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.</span></span>

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. <span data-ttu-id="7b9de-119">使用下面的命令编译此代码：</span><span class="sxs-lookup"><span data-stu-id="7b9de-119">Use the following command to compile this code:</span></span>

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   <span data-ttu-id="7b9de-120">指定 /t:module 选项，因为此模块将在以后的步骤中添加到程序集。</span><span class="sxs-lookup"><span data-stu-id="7b9de-120">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="7b9de-121">Client 中的代码会引用 Stringer.netmodule 中的代码创建的命名空间，因此请指定 /addmodule 选项 。</span><span class="sxs-lookup"><span data-stu-id="7b9de-121">Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*.</span></span> <span data-ttu-id="7b9de-122">编译器生成一个名为 Client.netmodule 的模块，其中包含对另一个模块 Stringer.netmodule 的引用 。</span><span class="sxs-lookup"><span data-stu-id="7b9de-122">The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7b9de-123">C# 和 Visual Basic 编译器支持使用以下两种不同语法直接创建多文件程序集。</span><span class="sxs-lookup"><span data-stu-id="7b9de-123">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
   >
   > <span data-ttu-id="7b9de-124">两次编译创建出一个双文件程序集：</span><span class="sxs-lookup"><span data-stu-id="7b9de-124">Two compilations create a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > <span data-ttu-id="7b9de-125">一次编译创建出一个双文件程序集：</span><span class="sxs-lookup"><span data-stu-id="7b9de-125">One compilation creates a two-file assembly:</span></span>
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. <span data-ttu-id="7b9de-126">使用[程序集链接器 (Al.exe)](../tools/al-exe-assembly-linker.md) 来创建包含程序集清单的输出文件。</span><span class="sxs-lookup"><span data-stu-id="7b9de-126">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="7b9de-127">此文件包含作为程序集组成部分的所有模块或资源的参考信息。</span><span class="sxs-lookup"><span data-stu-id="7b9de-127">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="7b9de-128">在命令提示符处，键入下列命令：</span><span class="sxs-lookup"><span data-stu-id="7b9de-128">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="7b9de-129">al \<*module name*> \<*module name*> …</span><span class="sxs-lookup"><span data-stu-id="7b9de-129">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="7b9de-130">/main:\<*method name*> /out:\<*file name*> /target:\<*assembly file type*>  </span><span class="sxs-lookup"><span data-stu-id="7b9de-130">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="7b9de-131">在此命令中，“module name”参数指定程序集要包含的各模块的名称。</span><span class="sxs-lookup"><span data-stu-id="7b9de-131">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="7b9de-132">/main: 选项指定作为程序集入口点的方法名称。</span><span class="sxs-lookup"><span data-stu-id="7b9de-132">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="7b9de-133">/out: 选项指定输出文件的名称，它包含程序集元数据。</span><span class="sxs-lookup"><span data-stu-id="7b9de-133">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="7b9de-134">/target: 选项指定程序集是控制台应用程序可执行文件 (.exe)、Windows 可执行文件 (.win) 或库文件 (.lib)  。</span><span class="sxs-lookup"><span data-stu-id="7b9de-134">The **/target:** option specifies that the assembly is a console application executable (*.exe*) file, a Windows executable (*.win*) file, or a library (*.lib*) file.</span></span>

    <span data-ttu-id="7b9de-135">在下面的示例中，Al.exe 创建一个程序集，该程序集是一个名为 myAssembly.exe 的控制台应用程序可执行文件 。</span><span class="sxs-lookup"><span data-stu-id="7b9de-135">In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*.</span></span> <span data-ttu-id="7b9de-136">该应用程序由名为 Client.netmodule 和 Stringer.netmodule 的两个模块以及名为 myAssembly.exe（其中只包含程序集元数据）的可执行文件组成  。</span><span class="sxs-lookup"><span data-stu-id="7b9de-136">The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata.</span></span> <span data-ttu-id="7b9de-137">程序集的入口点是位于 Client.dll 的 `MainClientApp` 类中的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="7b9de-137">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.</span></span>

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="7b9de-138">可以使用 [MSIL 反汇编程序 (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) 来检查程序集的内容，或者确定文件是程序集还是模块。</span><span class="sxs-lookup"><span data-stu-id="7b9de-138">You can use the [MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b9de-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="7b9de-139">See also</span></span>

- [<span data-ttu-id="7b9de-140">创建程序集</span><span class="sxs-lookup"><span data-stu-id="7b9de-140">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="7b9de-141">如何：查看程序集内容</span><span class="sxs-lookup"><span data-stu-id="7b9de-141">How to: View assembly contents</span></span>](../../standard/assembly/view-contents.md)
- [<span data-ttu-id="7b9de-142">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="7b9de-142">How the runtime locates assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="7b9de-143">多文件程序集</span><span class="sxs-lookup"><span data-stu-id="7b9de-143">Multifile assemblies</span></span>](multifile-assemblies.md)
