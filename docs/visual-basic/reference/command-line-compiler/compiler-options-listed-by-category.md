---
title: 按类别列出的编译器选项
ms.date: 04/12/2018
helpviewer_keywords:
- Visual Basic compiler, options
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
ms.openlocfilehash: 77a130b684d26cf7e4b9df9382348a371a60bc5d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072036"
---
# <a name="visual-basic-compiler-options-listed-by-category"></a><span data-ttu-id="4a01b-102">按类别列出的 Visual Basic 编译器选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-102">Visual Basic compiler options listed by category</span></span>

<span data-ttu-id="4a01b-103">Visual Basic 命令行编译器用作一种替代方法，用于在 Visual Studio 集成开发环境 (IDE) 中编译程序。</span><span class="sxs-lookup"><span data-stu-id="4a01b-103">The Visual Basic command-line compiler is provided as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="4a01b-104">以下是按功能分类排序的 Visual Basic 命令行编译器选项的列表。</span><span class="sxs-lookup"><span data-stu-id="4a01b-104">The following is a list of the Visual Basic command-line compiler options sorted by functional category.</span></span>  

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]
  
## <a name="compiler-output"></a><span data-ttu-id="4a01b-105">编译器输出</span><span class="sxs-lookup"><span data-stu-id="4a01b-105">Compiler output</span></span>  
  
|<span data-ttu-id="4a01b-106">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-106">Option</span></span>|<span data-ttu-id="4a01b-107">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-107">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-108">-nologo</span><span class="sxs-lookup"><span data-stu-id="4a01b-108">-nologo</span></span>](nologo.md)|<span data-ttu-id="4a01b-109">禁止显示编译器横幅信息。</span><span class="sxs-lookup"><span data-stu-id="4a01b-109">Suppresses compiler banner information.</span></span>|  
|[<span data-ttu-id="4a01b-110">-utf8output</span><span class="sxs-lookup"><span data-stu-id="4a01b-110">-utf8output</span></span>](utf8output.md)|<span data-ttu-id="4a01b-111">显示使用 UTF-8 编码的编译器输出。</span><span class="sxs-lookup"><span data-stu-id="4a01b-111">Displays compiler output using UTF-8 encoding.</span></span>|  
|[<span data-ttu-id="4a01b-112">-verbose</span><span class="sxs-lookup"><span data-stu-id="4a01b-112">-verbose</span></span>](verbose.md)|<span data-ttu-id="4a01b-113">在编译期间输出其他信息。</span><span class="sxs-lookup"><span data-stu-id="4a01b-113">Outputs extra information during compilation.</span></span>|  
|`-modulename:<string>`|<span data-ttu-id="4a01b-114">指定源模块的名称</span><span class="sxs-lookup"><span data-stu-id="4a01b-114">Specify the name of the source module</span></span>|  
|[<span data-ttu-id="4a01b-115">/preferreduilang</span><span class="sxs-lookup"><span data-stu-id="4a01b-115">-preferreduilang</span></span>](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|<span data-ttu-id="4a01b-116">指定编译器输出的语言。</span><span class="sxs-lookup"><span data-stu-id="4a01b-116">Specify a language for compiler output.</span></span>|
  
## <a name="optimization"></a><span data-ttu-id="4a01b-117">优化</span><span class="sxs-lookup"><span data-stu-id="4a01b-117">Optimization</span></span>  
  
|<span data-ttu-id="4a01b-118">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-118">Option</span></span>|<span data-ttu-id="4a01b-119">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-119">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-120">-filealign</span><span class="sxs-lookup"><span data-stu-id="4a01b-120">-filealign</span></span>](filealign.md)|<span data-ttu-id="4a01b-121">指定输出文件各节的对齐位置。</span><span class="sxs-lookup"><span data-stu-id="4a01b-121">Specifies where to align the sections of the output file.</span></span>|  
|[<span data-ttu-id="4a01b-122">-optimize</span><span class="sxs-lookup"><span data-stu-id="4a01b-122">-optimize</span></span>](optimize.md)|<span data-ttu-id="4a01b-123">启用/禁用优化。</span><span class="sxs-lookup"><span data-stu-id="4a01b-123">Enables/disables optimizations.</span></span>|  
  
## <a name="output-files"></a><span data-ttu-id="4a01b-124">输出文件</span><span class="sxs-lookup"><span data-stu-id="4a01b-124">Output files</span></span>  
  
|<span data-ttu-id="4a01b-125">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-125">Option</span></span>|<span data-ttu-id="4a01b-126">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-126">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-127">-doc</span><span class="sxs-lookup"><span data-stu-id="4a01b-127">-doc</span></span>](doc.md)|<span data-ttu-id="4a01b-128">处理 XML 文件的文档注释。</span><span class="sxs-lookup"><span data-stu-id="4a01b-128">Process documentation comments to an XML file.</span></span>|  
|[<span data-ttu-id="4a01b-129">-deterministic</span><span class="sxs-lookup"><span data-stu-id="4a01b-129">-deterministic</span></span>](deterministic.md)|<span data-ttu-id="4a01b-130">如果输入相同，则会导致编译器输出的程序集其二进制内容在整个编译中相同。</span><span class="sxs-lookup"><span data-stu-id="4a01b-130">Causes the compiler to output an assembly whose binary content is identical across compilations if inputs are identical.</span></span>|
|[<span data-ttu-id="4a01b-131">-netcf</span><span class="sxs-lookup"><span data-stu-id="4a01b-131">-netcf</span></span>](netcf.md)|<span data-ttu-id="4a01b-132">将编译器设置为以 .NET Compact Framework 为目标。</span><span class="sxs-lookup"><span data-stu-id="4a01b-132">Sets the compiler to target the .NET Compact Framework.</span></span>|  
|[<span data-ttu-id="4a01b-133">-out</span><span class="sxs-lookup"><span data-stu-id="4a01b-133">-out</span></span>](out.md)|<span data-ttu-id="4a01b-134">指定输出目录。</span><span class="sxs-lookup"><span data-stu-id="4a01b-134">Specifies an output file.</span></span>|  
|[<span data-ttu-id="4a01b-135">/refonly</span><span class="sxs-lookup"><span data-stu-id="4a01b-135">-refonly</span></span>](refonly-compiler-option.md)|<span data-ttu-id="4a01b-136">仅输出引用程序集。</span><span class="sxs-lookup"><span data-stu-id="4a01b-136">Outputs only a reference assembly.</span></span>|
|[<span data-ttu-id="4a01b-137">/refout</span><span class="sxs-lookup"><span data-stu-id="4a01b-137">-refout</span></span>](refout-compiler-option.md)|<span data-ttu-id="4a01b-138">指定引用程序集的输出路径。</span><span class="sxs-lookup"><span data-stu-id="4a01b-138">Specifies the output path of a reference assembly.</span></span>|
|[<span data-ttu-id="4a01b-139">-target</span><span class="sxs-lookup"><span data-stu-id="4a01b-139">-target</span></span>](target.md)|<span data-ttu-id="4a01b-140">指定输出的格式。</span><span class="sxs-lookup"><span data-stu-id="4a01b-140">Specifies the format of the output.</span></span>|  
  
## <a name="net-assemblies"></a><span data-ttu-id="4a01b-141">.NET 程序集</span><span class="sxs-lookup"><span data-stu-id="4a01b-141">.NET assemblies</span></span>  
  
|<span data-ttu-id="4a01b-142">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-142">Option</span></span>|<span data-ttu-id="4a01b-143">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-143">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-144">-addmodule</span><span class="sxs-lookup"><span data-stu-id="4a01b-144">-addmodule</span></span>](addmodule.md)|<span data-ttu-id="4a01b-145">使编译器让指定文件中的所有类型信息可供当前正在编译的项目使用。</span><span class="sxs-lookup"><span data-stu-id="4a01b-145">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>|  
|[<span data-ttu-id="4a01b-146">-delaysign</span><span class="sxs-lookup"><span data-stu-id="4a01b-146">-delaysign</span></span>](delaysign.md)|<span data-ttu-id="4a01b-147">指定程序集是完全签名的还是部分签名的。</span><span class="sxs-lookup"><span data-stu-id="4a01b-147">Specifies whether the assembly will be fully or partially signed.</span></span>|  
|[<span data-ttu-id="4a01b-148">-imports</span><span class="sxs-lookup"><span data-stu-id="4a01b-148">-imports</span></span>](imports.md)|<span data-ttu-id="4a01b-149">从指定的程序集导入命名空间。</span><span class="sxs-lookup"><span data-stu-id="4a01b-149">Imports a namespace from a specified assembly.</span></span>|  
|[<span data-ttu-id="4a01b-150">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="4a01b-150">-keycontainer</span></span>](keycontainer.md)|<span data-ttu-id="4a01b-151">指定密钥对的密钥容器名称从而为程序集赋予强名称。</span><span class="sxs-lookup"><span data-stu-id="4a01b-151">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>|  
|[<span data-ttu-id="4a01b-152">-keyfile</span><span class="sxs-lookup"><span data-stu-id="4a01b-152">-keyfile</span></span>](keyfile.md)|<span data-ttu-id="4a01b-153">指定包含密钥或密钥对的文件从而为程序集赋予强名称。</span><span class="sxs-lookup"><span data-stu-id="4a01b-153">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>|  
|[<span data-ttu-id="4a01b-154">-libpath</span><span class="sxs-lookup"><span data-stu-id="4a01b-154">-libpath</span></span>](libpath.md)|<span data-ttu-id="4a01b-155">指定通过 [-reference](reference.md) 选项引用的程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="4a01b-155">Specifies the location of assemblies referenced by the [-reference](reference.md) option.</span></span>|  
|[<span data-ttu-id="4a01b-156">-reference</span><span class="sxs-lookup"><span data-stu-id="4a01b-156">-reference</span></span>](reference.md)|<span data-ttu-id="4a01b-157">从程序集导入元数据。</span><span class="sxs-lookup"><span data-stu-id="4a01b-157">Imports metadata from an assembly.</span></span>|  
|[<span data-ttu-id="4a01b-158">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="4a01b-158">-moduleassemblyname</span></span>](moduleassemblyname.md)|<span data-ttu-id="4a01b-159">指定模块所属程序集的名称。</span><span class="sxs-lookup"><span data-stu-id="4a01b-159">Specifies the name of the assembly that a module will be a part of.</span></span>|  
|`-analyzer`|<span data-ttu-id="4a01b-160">从此程序集（缩写形式：-a）运行分析器</span><span class="sxs-lookup"><span data-stu-id="4a01b-160">Run the analyzers from this assembly (Short form: -a)</span></span>|  
|`-additionalfile`|<span data-ttu-id="4a01b-161">命名其他文件，这些文件不会直接影响代码生成，但可能由分析器用于生成错误或警告。</span><span class="sxs-lookup"><span data-stu-id="4a01b-161">Names additional files that don't directly affect code generation but may be used by analyzers for producing errors or warnings.</span></span>|  
  
## <a name="debuggingerror-checking"></a><span data-ttu-id="4a01b-162">调试/错误检查</span><span class="sxs-lookup"><span data-stu-id="4a01b-162">Debugging/error checking</span></span>  
  
|<span data-ttu-id="4a01b-163">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-163">Option</span></span>|<span data-ttu-id="4a01b-164">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-164">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-165">-bugreport</span><span class="sxs-lookup"><span data-stu-id="4a01b-165">-bugreport</span></span>](bugreport.md)|<span data-ttu-id="4a01b-166">创建一个文件，其中包含可以轻松报告 bug 的信息。</span><span class="sxs-lookup"><span data-stu-id="4a01b-166">Creates a file that contains information that makes it easy to report a bug.</span></span>|  
|[<span data-ttu-id="4a01b-167">-debug</span><span class="sxs-lookup"><span data-stu-id="4a01b-167">-debug</span></span>](debug.md)|<span data-ttu-id="4a01b-168">生成调试信息。</span><span class="sxs-lookup"><span data-stu-id="4a01b-168">Produces debugging information.</span></span>|  
|[<span data-ttu-id="4a01b-169">-nowarn</span><span class="sxs-lookup"><span data-stu-id="4a01b-169">-nowarn</span></span>](nowarn.md)|<span data-ttu-id="4a01b-170">禁止编译器生成警告的能力。</span><span class="sxs-lookup"><span data-stu-id="4a01b-170">Suppresses the compiler's ability to generate warnings.</span></span>|  
|[<span data-ttu-id="4a01b-171">-quiet</span><span class="sxs-lookup"><span data-stu-id="4a01b-171">-quiet</span></span>](quiet.md)|<span data-ttu-id="4a01b-172">阻止编译器显示与语法相关的错误和警告的代码。</span><span class="sxs-lookup"><span data-stu-id="4a01b-172">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>|  
|[<span data-ttu-id="4a01b-173">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="4a01b-173">-removeintchecks</span></span>](removeintchecks.md)|<span data-ttu-id="4a01b-174">禁用整数溢出检查。</span><span class="sxs-lookup"><span data-stu-id="4a01b-174">Disables integer overflow checking.</span></span>|  
|[<span data-ttu-id="4a01b-175">-warnaserror</span><span class="sxs-lookup"><span data-stu-id="4a01b-175">-warnaserror</span></span>](warnaserror.md)|<span data-ttu-id="4a01b-176">将警告提升为错误。</span><span class="sxs-lookup"><span data-stu-id="4a01b-176">Promotes warnings to errors.</span></span>|  
|`-ruleset:<file>`|<span data-ttu-id="4a01b-177">指定可禁用特定诊断的规则集文件。</span><span class="sxs-lookup"><span data-stu-id="4a01b-177">Specify a ruleset file that disables specific diagnostics.</span></span>|  
  
## <a name="help"></a><span data-ttu-id="4a01b-178">帮助</span><span class="sxs-lookup"><span data-stu-id="4a01b-178">Help</span></span>  
  
|<span data-ttu-id="4a01b-179">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-179">Option</span></span>|<span data-ttu-id="4a01b-180">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-180">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-181">-?</span><span class="sxs-lookup"><span data-stu-id="4a01b-181">-?</span></span>](help.md)|<span data-ttu-id="4a01b-182">显示编译器选项。</span><span class="sxs-lookup"><span data-stu-id="4a01b-182">Displays the compiler options.</span></span> <span data-ttu-id="4a01b-183">此命令等同于指定 `-help` 选项。</span><span class="sxs-lookup"><span data-stu-id="4a01b-183">This command is the same as specifying the `-help` option.</span></span> <span data-ttu-id="4a01b-184">未进行编译。</span><span class="sxs-lookup"><span data-stu-id="4a01b-184">No compilation occurs.</span></span>|  
|[<span data-ttu-id="4a01b-185">-help</span><span class="sxs-lookup"><span data-stu-id="4a01b-185">-help</span></span>](help.md)|<span data-ttu-id="4a01b-186">显示编译器选项。</span><span class="sxs-lookup"><span data-stu-id="4a01b-186">Displays the compiler options.</span></span> <span data-ttu-id="4a01b-187">此命令等同于指定 `-?` 选项。</span><span class="sxs-lookup"><span data-stu-id="4a01b-187">This command is the same as specifying the `-?` option.</span></span> <span data-ttu-id="4a01b-188">未进行编译。</span><span class="sxs-lookup"><span data-stu-id="4a01b-188">No compilation occurs.</span></span>|  
  
## <a name="language"></a><span data-ttu-id="4a01b-189">语言</span><span class="sxs-lookup"><span data-stu-id="4a01b-189">Language</span></span>  
  
|<span data-ttu-id="4a01b-190">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-190">Option</span></span>|<span data-ttu-id="4a01b-191">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-191">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-192">-langversion</span><span class="sxs-lookup"><span data-stu-id="4a01b-192">-langversion</span></span>](langversion.md)|<span data-ttu-id="4a01b-193">指定语言版本：9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0。</span><span class="sxs-lookup"><span data-stu-id="4a01b-193">Specify language version: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0.</span></span>|  
|[<span data-ttu-id="4a01b-194">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="4a01b-194">-optionexplicit</span></span>](optionexplicit.md)|<span data-ttu-id="4a01b-195">强制执行显式声明变量。</span><span class="sxs-lookup"><span data-stu-id="4a01b-195">Enforces explicit declaration of variables.</span></span>|  
|[<span data-ttu-id="4a01b-196">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="4a01b-196">-optionstrict</span></span>](optionstrict.md)|<span data-ttu-id="4a01b-197">执行严格的类语义。</span><span class="sxs-lookup"><span data-stu-id="4a01b-197">Enforces strict type semantics.</span></span>|  
|[<span data-ttu-id="4a01b-198">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="4a01b-198">-optioncompare</span></span>](optioncompare.md)|<span data-ttu-id="4a01b-199">指定字符串比较是否应为二进制，或是否应使用特定于区域设置的文本语义。</span><span class="sxs-lookup"><span data-stu-id="4a01b-199">Specifies whether string comparisons should be binary or use locale-specific text semantics.</span></span>|  
|[<span data-ttu-id="4a01b-200">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="4a01b-200">-optioninfer</span></span>](optioninfer.md)|<span data-ttu-id="4a01b-201">允许在变量声明中使用局部类型推理。</span><span class="sxs-lookup"><span data-stu-id="4a01b-201">Enables the use of local type inference in variable declarations.</span></span>|  
  
## <a name="preprocessor"></a><span data-ttu-id="4a01b-202">预处理器</span><span class="sxs-lookup"><span data-stu-id="4a01b-202">Preprocessor</span></span>  
  
|<span data-ttu-id="4a01b-203">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-203">Option</span></span>|<span data-ttu-id="4a01b-204">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-204">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-205">-define</span><span class="sxs-lookup"><span data-stu-id="4a01b-205">-define</span></span>](define.md)|<span data-ttu-id="4a01b-206">定义条件编译的符号。</span><span class="sxs-lookup"><span data-stu-id="4a01b-206">Defines symbols for conditional compilation.</span></span>|  
  
## <a name="resources"></a><span data-ttu-id="4a01b-207">资源</span><span class="sxs-lookup"><span data-stu-id="4a01b-207">Resources</span></span>  
  
|<span data-ttu-id="4a01b-208">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-208">Option</span></span>|<span data-ttu-id="4a01b-209">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-209">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-210">-linkresource</span><span class="sxs-lookup"><span data-stu-id="4a01b-210">-linkresource</span></span>](linkresource.md)|<span data-ttu-id="4a01b-211">创建指向托管资源的链接。</span><span class="sxs-lookup"><span data-stu-id="4a01b-211">Creates a link to a managed resource.</span></span>|  
|[<span data-ttu-id="4a01b-212">-resource</span><span class="sxs-lookup"><span data-stu-id="4a01b-212">-resource</span></span>](resource.md)|<span data-ttu-id="4a01b-213">将托管资源嵌入程序集。</span><span class="sxs-lookup"><span data-stu-id="4a01b-213">Embeds a managed resource in an assembly.</span></span>|  
|[<span data-ttu-id="4a01b-214">-win32icon</span><span class="sxs-lookup"><span data-stu-id="4a01b-214">-win32icon</span></span>](win32icon.md)|<span data-ttu-id="4a01b-215">将 .ico 文件插入到输出文件。</span><span class="sxs-lookup"><span data-stu-id="4a01b-215">Inserts an .ico file into the output file.</span></span>|  
|[<span data-ttu-id="4a01b-216">-win32resource</span><span class="sxs-lookup"><span data-stu-id="4a01b-216">-win32resource</span></span>](win32resource.md)|<span data-ttu-id="4a01b-217">将 Win32 资源插入到输出文件。</span><span class="sxs-lookup"><span data-stu-id="4a01b-217">Inserts a Win32 resource into the output file.</span></span>|  
  
## <a name="miscellaneous"></a><span data-ttu-id="4a01b-218">杂项</span><span class="sxs-lookup"><span data-stu-id="4a01b-218">Miscellaneous</span></span>  
  
|<span data-ttu-id="4a01b-219">选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-219">Option</span></span>|<span data-ttu-id="4a01b-220">目标</span><span class="sxs-lookup"><span data-stu-id="4a01b-220">Purpose</span></span>|  
|---|---|  
|[<span data-ttu-id="4a01b-221">@（指定响应文件）</span><span class="sxs-lookup"><span data-stu-id="4a01b-221">@ (Specify Response File)</span></span>](specify-response-file.md)|<span data-ttu-id="4a01b-222">指定响应文件。</span><span class="sxs-lookup"><span data-stu-id="4a01b-222">Specifies a response file.</span></span>|  
|[<span data-ttu-id="4a01b-223">-baseaddress</span><span class="sxs-lookup"><span data-stu-id="4a01b-223">-baseaddress</span></span>](baseaddress.md)|<span data-ttu-id="4a01b-224">指定的 DLL 的基址。</span><span class="sxs-lookup"><span data-stu-id="4a01b-224">Specifies the base address of a DLL.</span></span>|  
|[<span data-ttu-id="4a01b-225">-codepage</span><span class="sxs-lookup"><span data-stu-id="4a01b-225">-codepage</span></span>](codepage.md)|<span data-ttu-id="4a01b-226">指定要用于编译中所有源代码文件的代码页。</span><span class="sxs-lookup"><span data-stu-id="4a01b-226">Specifies the code page to use for all source code files in the compilation.</span></span>|  
|[<span data-ttu-id="4a01b-227">-errorreport</span><span class="sxs-lookup"><span data-stu-id="4a01b-227">-errorreport</span></span>](errorreport.md)|<span data-ttu-id="4a01b-228">指定 Visual Basic 编译器应报告内部编译器错误的方式。</span><span class="sxs-lookup"><span data-stu-id="4a01b-228">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>|  
|[<span data-ttu-id="4a01b-229">-highentropyva</span><span class="sxs-lookup"><span data-stu-id="4a01b-229">-highentropyva</span></span>](highentropyva.md)|<span data-ttu-id="4a01b-230">向 Windows 内核提供下列信息：特定的可执行文件是否支持高熵地址空间布局随机化 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="4a01b-230">Tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>|  
|[<span data-ttu-id="4a01b-231">-main</span><span class="sxs-lookup"><span data-stu-id="4a01b-231">-main</span></span>](main.md)|<span data-ttu-id="4a01b-232">指定包含启动时要使用的 `Sub Main` 过程的类。</span><span class="sxs-lookup"><span data-stu-id="4a01b-232">Specifies the class that contains the `Sub Main` procedure to use at startup.</span></span>|  
|[<span data-ttu-id="4a01b-233">-noconfig</span><span class="sxs-lookup"><span data-stu-id="4a01b-233">-noconfig</span></span>](noconfig.md)|<span data-ttu-id="4a01b-234">不要使用 Vbc.rsp 进行编译</span><span class="sxs-lookup"><span data-stu-id="4a01b-234">Do not compile with Vbc.rsp</span></span>|  
|[<span data-ttu-id="4a01b-235">-nostdlib</span><span class="sxs-lookup"><span data-stu-id="4a01b-235">-nostdlib</span></span>](nostdlib.md)|<span data-ttu-id="4a01b-236">导致编译器不引用标准库。</span><span class="sxs-lookup"><span data-stu-id="4a01b-236">Causes the compiler not to reference the standard libraries.</span></span>|  
|[<span data-ttu-id="4a01b-237">-nowin32manifest</span><span class="sxs-lookup"><span data-stu-id="4a01b-237">-nowin32manifest</span></span>](nowin32manifest.md)|<span data-ttu-id="4a01b-238">指示编译器不在可执行文件中嵌入任何应用程序清单。</span><span class="sxs-lookup"><span data-stu-id="4a01b-238">Instructs the compiler not to embed any application manifest into the executable file.</span></span>|  
|[<span data-ttu-id="4a01b-239">-platform</span><span class="sxs-lookup"><span data-stu-id="4a01b-239">-platform</span></span>](platform.md)|<span data-ttu-id="4a01b-240">为输出文件指定编译器面向的处理器平台。</span><span class="sxs-lookup"><span data-stu-id="4a01b-240">Specifies the processor platform the compiler targets for the output file.</span></span>|  
|[<span data-ttu-id="4a01b-241">-recurse</span><span class="sxs-lookup"><span data-stu-id="4a01b-241">-recurse</span></span>](recurse.md)|<span data-ttu-id="4a01b-242">搜索要编译的源文件的子目录。</span><span class="sxs-lookup"><span data-stu-id="4a01b-242">Searches subdirectories for source files to compile.</span></span>|  
|[<span data-ttu-id="4a01b-243">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="4a01b-243">-rootnamespace</span></span>](rootnamespace.md)|<span data-ttu-id="4a01b-244">指定所有类型声明的命名空间。</span><span class="sxs-lookup"><span data-stu-id="4a01b-244">Specifies a namespace for all type declarations.</span></span>|  
|[<span data-ttu-id="4a01b-245">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="4a01b-245">-sdkpath</span></span>](sdkpath.md)|<span data-ttu-id="4a01b-246">指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="4a01b-246">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>|  
|[<span data-ttu-id="4a01b-247">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="4a01b-247">-vbruntime</span></span>](vbruntime.md)|<span data-ttu-id="4a01b-248">指定编译器应在不引用 Visual Basic 运行库的情况下进行编译，或在引用特定运行库的情况下进行编译。</span><span class="sxs-lookup"><span data-stu-id="4a01b-248">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>|  
|[<span data-ttu-id="4a01b-249">-win32manifest</span><span class="sxs-lookup"><span data-stu-id="4a01b-249">-win32manifest</span></span>](win32manifest.md)|<span data-ttu-id="4a01b-250">标识用户定义的 Win32 应用程序清单文件要嵌入到项目的可移植可执行 (PE) 文件。</span><span class="sxs-lookup"><span data-stu-id="4a01b-250">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>|  
|`-parallel[+&#124;-]`|<span data-ttu-id="4a01b-251">指定是否使用并发生成 (+)。</span><span class="sxs-lookup"><span data-stu-id="4a01b-251">Specifies whether to use concurrent build (+).</span></span>|  
|`-checksumalgorithm:<alg>`|<span data-ttu-id="4a01b-252">指定用于计算 PDB 中存储的源文件校验和的算法。</span><span class="sxs-lookup"><span data-stu-id="4a01b-252">Specify the algorithm for calculating the source file checksum stored in PDB.</span></span>  <span data-ttu-id="4a01b-253">受支持的值为:SHA1（默认值）或 SHA256。</span><span class="sxs-lookup"><span data-stu-id="4a01b-253">Supported values are: SHA1 (default) or SHA256.</span></span> <br><span data-ttu-id="4a01b-254">由于与 SHA1 冲突，Microsoft 建议使用 SHA256 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="4a01b-254">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a01b-255">请参阅</span><span class="sxs-lookup"><span data-stu-id="4a01b-255">See also</span></span>

- [<span data-ttu-id="4a01b-256">按字母顺序列出的 Visual Basic 编译器选项</span><span class="sxs-lookup"><span data-stu-id="4a01b-256">Visual Basic Compiler Options Listed Alphabetically</span></span>](compiler-options-listed-alphabetically.md)
- [<span data-ttu-id="4a01b-257">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="4a01b-257">Manage project and solution properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
