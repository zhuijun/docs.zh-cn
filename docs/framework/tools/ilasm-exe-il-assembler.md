---
title: Ilasm.exe（IL 汇编程序）
description: 开始使用 Ilasm.exe（IL 汇编程序）。 此工具从中间语言 (IL) 生成可移植可执行 (PE) 文件。
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: 1a85b3bf9509ffba6c2331d14196a6bef2bfa080
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166985"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="fccd0-104">Ilasm.exe（IL 汇编程序）</span><span class="sxs-lookup"><span data-stu-id="fccd0-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="fccd0-105">IL 汇编程序可利用中间语言 (IL) 生成可移植可执行 (PE) 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="fccd0-106">（有关 IL 的详细信息，请参阅[托管执行过程](../../standard/managed-execution-process.md)。）可以运行生成的可执行文件（包含 IL 和所需的元数据）以确定 IL 是否按预期执行。</span><span class="sxs-lookup"><span data-stu-id="fccd0-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="fccd0-107">此工具会自动随 Visual Studio 一起安装。</span><span class="sxs-lookup"><span data-stu-id="fccd0-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="fccd0-108">若要运行此工具，请使用 Visual Studio 开发人员命令提示（或 Windows 7 中的 Visual Studio 命令提示）。</span><span class="sxs-lookup"><span data-stu-id="fccd0-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="fccd0-109">有关详细信息，请参阅[命令提示](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="fccd0-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="fccd0-110">在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="fccd0-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="fccd0-111">语法</span><span class="sxs-lookup"><span data-stu-id="fccd0-111">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="fccd0-112">参数</span><span class="sxs-lookup"><span data-stu-id="fccd0-112">Parameters</span></span>

| <span data-ttu-id="fccd0-113">参数</span><span class="sxs-lookup"><span data-stu-id="fccd0-113">Argument</span></span> | <span data-ttu-id="fccd0-114">说明</span><span class="sxs-lookup"><span data-stu-id="fccd0-114">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="fccd0-115">.il 源文件的名称。</span><span class="sxs-lookup"><span data-stu-id="fccd0-115">The name of the .il source file.</span></span> <span data-ttu-id="fccd0-116">该文件包含元数据声明指令和符号化 IL 指令。</span><span class="sxs-lookup"><span data-stu-id="fccd0-116">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="fccd0-117">可以提供多个源文件参数，以便用 Ilasm.exe 生成单个 PE 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-117">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="fccd0-118">**注意：** 确保 .il 源文件中的最后一行代码具有尾随空格或行尾字符。</span><span class="sxs-lookup"><span data-stu-id="fccd0-118">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="fccd0-119">选项</span><span class="sxs-lookup"><span data-stu-id="fccd0-119">Option</span></span> | <span data-ttu-id="fccd0-120">描述</span><span class="sxs-lookup"><span data-stu-id="fccd0-120">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="fccd0-121">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="fccd0-121">**/32bitpreferred**</span></span>|<span data-ttu-id="fccd0-122">创建 32 位首选映像 (PE32+)。</span><span class="sxs-lookup"><span data-stu-id="fccd0-122">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="fccd0-123">/alignment: `integer`</span><span class="sxs-lookup"><span data-stu-id="fccd0-123">**/alignment:** `integer`</span></span>|<span data-ttu-id="fccd0-124">将 FileAlignment 设置为由 NT Optional 标头中的 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="fccd0-124">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="fccd0-125">如果在文件中指定了 .alignment IL 指令，则此选项将重写它。</span><span class="sxs-lookup"><span data-stu-id="fccd0-125">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="fccd0-126">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="fccd0-126">**/appcontainer**</span></span>|<span data-ttu-id="fccd0-127">生成在 Windows 应用容器中运行的 .dll 或 .exe 文件作为输出 。</span><span class="sxs-lookup"><span data-stu-id="fccd0-127">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="fccd0-128">**/arm**</span><span class="sxs-lookup"><span data-stu-id="fccd0-128">**/arm**</span></span>|<span data-ttu-id="fccd0-129">指定高级 RISC 计算机 (ARM) 作为目标处理器。</span><span class="sxs-lookup"><span data-stu-id="fccd0-129">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="fccd0-130">如果未指定映像位数，则默认值为 **/32bitpreferred**。</span><span class="sxs-lookup"><span data-stu-id="fccd0-130">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="fccd0-131">/base: `integer`</span><span class="sxs-lookup"><span data-stu-id="fccd0-131">**/base:** `integer`</span></span>|<span data-ttu-id="fccd0-132">将 ImageBase 设置为由 NT Optional 标头中的 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="fccd0-132">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="fccd0-133">如果在文件指定了 .imagebase IL 指令，则此选项将重写它。</span><span class="sxs-lookup"><span data-stu-id="fccd0-133">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="fccd0-134">**/clock**</span><span class="sxs-lookup"><span data-stu-id="fccd0-134">**/clock**</span></span>|<span data-ttu-id="fccd0-135">为指定的 .il 源文件测量并报告下列编译时间（以毫秒为单位）：</span><span class="sxs-lookup"><span data-stu-id="fccd0-135">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="fccd0-136">总运行时间：执行后面的所有特定操作所花费的总时间。</span><span class="sxs-lookup"><span data-stu-id="fccd0-136">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="fccd0-137">启动：加载并打开文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-137">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="fccd0-138">发出 MD：发出元数据。</span><span class="sxs-lookup"><span data-stu-id="fccd0-138">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="fccd0-139">定义引用解析：解析对文件中的定义的引用。</span><span class="sxs-lookup"><span data-stu-id="fccd0-139">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="fccd0-140">CEE 文件生成：在内存中生成文件映像。</span><span class="sxs-lookup"><span data-stu-id="fccd0-140">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="fccd0-141">PE 文件写入：将映像写入 PE 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-141">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="fccd0-142">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="fccd0-142">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="fccd0-143">包括调试信息（局部变量名和参数名以及行号）。</span><span class="sxs-lookup"><span data-stu-id="fccd0-143">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="fccd0-144">创建 PDB 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-144">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="fccd0-145">不带任何附加值的 **/debug** 禁用 JIT 优化，并使用 PDB 文件中的序列点。</span><span class="sxs-lookup"><span data-stu-id="fccd0-145">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="fccd0-146">**IMPL** 禁用 JIT 优化，并使用隐式序列点。</span><span class="sxs-lookup"><span data-stu-id="fccd0-146">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="fccd0-147">**OPT** 启用 JIT 优化，并使用隐式序列点。</span><span class="sxs-lookup"><span data-stu-id="fccd0-147">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="fccd0-148">**/dll**</span><span class="sxs-lookup"><span data-stu-id="fccd0-148">**/dll**</span></span>|<span data-ttu-id="fccd0-149">生成 .dll 文件作为输出。</span><span class="sxs-lookup"><span data-stu-id="fccd0-149">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="fccd0-150">/enc: `file`</span><span class="sxs-lookup"><span data-stu-id="fccd0-150">**/enc:** `file`</span></span>|<span data-ttu-id="fccd0-151">从指定的源文件创建“编辑并继续”增量。</span><span class="sxs-lookup"><span data-stu-id="fccd0-151">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="fccd0-152">此参数仅可用于教学目的，不支持商业使用。</span><span class="sxs-lookup"><span data-stu-id="fccd0-152">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="fccd0-153">**/exe**</span><span class="sxs-lookup"><span data-stu-id="fccd0-153">**/exe**</span></span>|<span data-ttu-id="fccd0-154">生成可执行文件作为输出。</span><span class="sxs-lookup"><span data-stu-id="fccd0-154">Produces an executable file as output.</span></span> <span data-ttu-id="fccd0-155">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="fccd0-155">This is the default.</span></span>|
|<span data-ttu-id="fccd0-156">**/flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="fccd0-156">**/flags:** `integer`</span></span>|<span data-ttu-id="fccd0-157">将 ImageFlags 设置为由公共语言运行时标头中的 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="fccd0-157">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="fccd0-158">如果在文件中指定了 .corflags IL 指令，则此选项将重写它。</span><span class="sxs-lookup"><span data-stu-id="fccd0-158">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="fccd0-159">有关 *integer*的有效值的列表，请参见 CorHdr.h 中的 COMIMAGE_FLAGS。</span><span class="sxs-lookup"><span data-stu-id="fccd0-159">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="fccd0-160">**/fold**</span><span class="sxs-lookup"><span data-stu-id="fccd0-160">**/fold**</span></span>|<span data-ttu-id="fccd0-161">将相同的方法体合并为一体。</span><span class="sxs-lookup"><span data-stu-id="fccd0-161">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="fccd0-162">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="fccd0-162">/**highentropyva**</span></span>|<span data-ttu-id="fccd0-163">生成支持高熵地址空间布局随机化 (ASLR) 的可执行输出。</span><span class="sxs-lookup"><span data-stu-id="fccd0-163">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="fccd0-164">（ **/appcontainer**的默认值。）</span><span class="sxs-lookup"><span data-stu-id="fccd0-164">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="fccd0-165">/include: `includePath`</span><span class="sxs-lookup"><span data-stu-id="fccd0-165">**/include:** `includePath`</span></span>|<span data-ttu-id="fccd0-166">设置要在其中搜索 `#include`包含的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="fccd0-166">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="fccd0-167">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="fccd0-167">**/itanium**</span></span>|<span data-ttu-id="fccd0-168">指定 Intel 的 Itanium 作为目标处理器。</span><span class="sxs-lookup"><span data-stu-id="fccd0-168">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="fccd0-169">如果未指定映像位数，则默认值为 **/pe64**。</span><span class="sxs-lookup"><span data-stu-id="fccd0-169">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="fccd0-170">/key: `keyFile`</span><span class="sxs-lookup"><span data-stu-id="fccd0-170">**/key:** `keyFile`</span></span>|<span data-ttu-id="fccd0-171">使用 `keyFile` 中包含的私钥编译具有强签名的 `filename`。</span><span class="sxs-lookup"><span data-stu-id="fccd0-171">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="fccd0-172">**/key:**  @`keySource`</span><span class="sxs-lookup"><span data-stu-id="fccd0-172">**/key:** @`keySource`</span></span>|<span data-ttu-id="fccd0-173">使用 `keySource` 中生成的私钥编译具有强签名的 `filename`。</span><span class="sxs-lookup"><span data-stu-id="fccd0-173">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="fccd0-174">**/listing**</span><span class="sxs-lookup"><span data-stu-id="fccd0-174">**/listing**</span></span>|<span data-ttu-id="fccd0-175">在标准输出上生成列表文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-175">Produces a listing file on the standard output.</span></span> <span data-ttu-id="fccd0-176">如果省略此选项，则不生成列表文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-176">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="fccd0-177">此参数在 .NET Framework 2.0 或更高版本中不受支持。</span><span class="sxs-lookup"><span data-stu-id="fccd0-177">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="fccd0-178">/mdv: `versionString`</span><span class="sxs-lookup"><span data-stu-id="fccd0-178">**/mdv:** `versionString`</span></span>|<span data-ttu-id="fccd0-179">设置元数据版本字符串。</span><span class="sxs-lookup"><span data-stu-id="fccd0-179">Sets the metadata version string.</span></span>|
|<span data-ttu-id="fccd0-180">/msv: `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="fccd0-180">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="fccd0-181">设置元数据流版本，其中 `major` 和 `minor` 是整数。</span><span class="sxs-lookup"><span data-stu-id="fccd0-181">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="fccd0-182">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="fccd0-182">**/noautoinherit**</span></span>|<span data-ttu-id="fccd0-183">当未指定基类时，禁用从 <xref:System.Object> 的默认继承。</span><span class="sxs-lookup"><span data-stu-id="fccd0-183">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="fccd0-184">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="fccd0-184">**/nocorstub**</span></span>|<span data-ttu-id="fccd0-185">取消生成 CORExeMain 存根。</span><span class="sxs-lookup"><span data-stu-id="fccd0-185">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="fccd0-186">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="fccd0-186">**/nologo**</span></span>|<span data-ttu-id="fccd0-187">取消显示 Microsoft 启动版权标志。</span><span class="sxs-lookup"><span data-stu-id="fccd0-187">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="fccd0-188">/output: `file.ext`</span><span class="sxs-lookup"><span data-stu-id="fccd0-188">**/output:** `file.ext`</span></span>|<span data-ttu-id="fccd0-189">指定输出文件名和扩展名。</span><span class="sxs-lookup"><span data-stu-id="fccd0-189">Specifies the output file name and extension.</span></span> <span data-ttu-id="fccd0-190">默认情况下，输出文件名与第一个源文件的名称相同。</span><span class="sxs-lookup"><span data-stu-id="fccd0-190">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="fccd0-191">默认扩展名为 .exe。</span><span class="sxs-lookup"><span data-stu-id="fccd0-191">The default extension is *.exe*.</span></span> <span data-ttu-id="fccd0-192">如果指定 /dll 选项，则默认扩展名为 .dll。</span><span class="sxs-lookup"><span data-stu-id="fccd0-192">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="fccd0-193">**注意：** 指定 /output:myfile.dll 并不会设置 /dll 选项 。</span><span class="sxs-lookup"><span data-stu-id="fccd0-193">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="fccd0-194">如果不指定 /dll，结果将会是名为 myfile.dll 的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-194">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="fccd0-195">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="fccd0-195">**/optimize**</span></span>|<span data-ttu-id="fccd0-196">将长指令优化为短指令。</span><span class="sxs-lookup"><span data-stu-id="fccd0-196">Optimizes long instructions to short.</span></span> <span data-ttu-id="fccd0-197">例如，将 `br` 优化为 `br.s`。</span><span class="sxs-lookup"><span data-stu-id="fccd0-197">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="fccd0-198">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="fccd0-198">**/pe64**</span></span>|<span data-ttu-id="fccd0-199">创建 64 位映像 (PE32+)。</span><span class="sxs-lookup"><span data-stu-id="fccd0-199">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="fccd0-200">如果未指定目标处理器，则默认值为 `/itanium`。</span><span class="sxs-lookup"><span data-stu-id="fccd0-200">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="fccd0-201">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="fccd0-201">**/pdb**</span></span>|<span data-ttu-id="fccd0-202">创建 PDB 文件但不启用调试信息跟踪。</span><span class="sxs-lookup"><span data-stu-id="fccd0-202">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="fccd0-203">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="fccd0-203">**/quiet**</span></span>|<span data-ttu-id="fccd0-204">指定安静模式；不报告程序集进度。</span><span class="sxs-lookup"><span data-stu-id="fccd0-204">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="fccd0-205">/resource: `file.res`</span><span class="sxs-lookup"><span data-stu-id="fccd0-205">**/resource:** `file.res`</span></span>|<span data-ttu-id="fccd0-206">在生成的 .exe 或 .dll 文件中包括 \*.res 格式的指定资源文件 。</span><span class="sxs-lookup"><span data-stu-id="fccd0-206">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="fccd0-207">使用 **/resource** 选项只能指定一个 .res 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-207">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="fccd0-208">/ssver: `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="fccd0-208">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="fccd0-209">在 NT Optional 标头中设置子系统版本号。</span><span class="sxs-lookup"><span data-stu-id="fccd0-209">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="fccd0-210">对于 **/appcontainer** 和 **/arm** ，最低版本号为 6.02。</span><span class="sxs-lookup"><span data-stu-id="fccd0-210">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="fccd0-211">/stack: `stackSize`</span><span class="sxs-lookup"><span data-stu-id="fccd0-211">**/stack:** `stackSize`</span></span>|<span data-ttu-id="fccd0-212">将 NT Optional 标头中的 SizeOfStackReserve 值设置为 `stackSize`。</span><span class="sxs-lookup"><span data-stu-id="fccd0-212">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="fccd0-213">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="fccd0-213">**/stripreloc**</span></span>|<span data-ttu-id="fccd0-214">指定不需要基重定位。</span><span class="sxs-lookup"><span data-stu-id="fccd0-214">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="fccd0-215">/subsystem: `integer`</span><span class="sxs-lookup"><span data-stu-id="fccd0-215">**/subsystem:** `integer`</span></span>|<span data-ttu-id="fccd0-216">将 subsystem 设置为由 NT Optional 标头中的 `integer` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="fccd0-216">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="fccd0-217">如果在文件中指定了 .subsystem IL 指令，则此命令将重写它。</span><span class="sxs-lookup"><span data-stu-id="fccd0-217">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="fccd0-218">有关 `integer` 的有效值的列表，请参见 winnt.h 中的 IMAGE_SUBSYSTEM。</span><span class="sxs-lookup"><span data-stu-id="fccd0-218">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="fccd0-219">**/x64**</span><span class="sxs-lookup"><span data-stu-id="fccd0-219">**/x64**</span></span>|<span data-ttu-id="fccd0-220">指定 64 位 AMD 处理器作为目标处理器。</span><span class="sxs-lookup"><span data-stu-id="fccd0-220">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="fccd0-221">如果未指定映像位数，则默认值为 **/pe64**。</span><span class="sxs-lookup"><span data-stu-id="fccd0-221">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="fccd0-222">**/?**</span><span class="sxs-lookup"><span data-stu-id="fccd0-222">**/?**</span></span>|<span data-ttu-id="fccd0-223">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="fccd0-223">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="fccd0-224">Ilasm.exe 的所有选项都不区分大小写，并且根据前三个字母识别。</span><span class="sxs-lookup"><span data-stu-id="fccd0-224">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="fccd0-225">例如， /lis 等效于 /listing，/res:myresfile.res 等效于 /resource:myresfile.res   。指定参数的选项既可以用冒号 (:) 也可以用等号 (=) 作为选项和参数之间的分隔符。</span><span class="sxs-lookup"><span data-stu-id="fccd0-225">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="fccd0-226">例如，/output:file.ext 等效于 /output=file.ext。</span><span class="sxs-lookup"><span data-stu-id="fccd0-226">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="fccd0-227">备注</span><span class="sxs-lookup"><span data-stu-id="fccd0-227">Remarks</span></span>

<span data-ttu-id="fccd0-228">IL 汇编程序有助于工具供应商设计和实现 IL 生成器。</span><span class="sxs-lookup"><span data-stu-id="fccd0-228">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="fccd0-229">通过使用 Ilasm.exe，工具和编译器开发人员可以专注于生成 IL 和元数据，而无需考虑如何以 PE 文件格式发出 IL。</span><span class="sxs-lookup"><span data-stu-id="fccd0-229">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="fccd0-230">与面向运行时的其他编译器（如 C# 和 Visual Basic）类似，Ilasm.exe 不产生中间对象文件，并且不需要链接阶段即可形成 PE 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-230">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="fccd0-231">IL 汇编程序可以展现以运行时为目标的编程语言的所有现有元数据和 IL 功能。</span><span class="sxs-lookup"><span data-stu-id="fccd0-231">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="fccd0-232">这使得用上面任何编程语言编写的托管代码都可以在 IL 汇编程序中充分展现并且可以用 Ilasm.exe 编译。</span><span class="sxs-lookup"><span data-stu-id="fccd0-232">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="fccd0-233">如果 .il 源文件中的最后一行代码不具有尾随空格或行尾字符，则编译可能会失败。</span><span class="sxs-lookup"><span data-stu-id="fccd0-233">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="fccd0-234">可以将 Ilasm.exe 与它的配套工具 [Ildasm.exe](ildasm-exe-il-disassembler.md)一起使用 。</span><span class="sxs-lookup"><span data-stu-id="fccd0-234">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="fccd0-235">Ildasm.exe 利用包含 IL 代码的 PE 文件，创建适合输入到 Ilasm.exe 的文本文件 。</span><span class="sxs-lookup"><span data-stu-id="fccd0-235">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="fccd0-236">这很有用，例如在编译用并非支持所有运行时元数据特性的编程语言编写的代码时。</span><span class="sxs-lookup"><span data-stu-id="fccd0-236">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="fccd0-237">通过 Ildasm.exe 编译该代码并运行输出后，可以手动编辑生成的 IL 文本文件以添加缺少的属性。</span><span class="sxs-lookup"><span data-stu-id="fccd0-237">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="fccd0-238">然后可通过 Ilasm.exe 运行此文本文件，生成最终的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-238">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="fccd0-239">也可以使用此方法从最初由不同的编译器生成的数个 PE 文件生成一个 PE 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-239">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="fccd0-240">目前，无法对包含嵌入的本机代码的 PE 文件（例如，由 Visual C++ 生成的 PE 文件）使用此技术。</span><span class="sxs-lookup"><span data-stu-id="fccd0-240">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="fccd0-241">为尽可能准确地使用 Ildasm.exe 和 Ilasm.exe 的这种组合，默认情况下汇编程序不会将可能已在 IL 源中写入（或可能由其他编译程序发出）的长编码替换为短编码 。</span><span class="sxs-lookup"><span data-stu-id="fccd0-241">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="fccd0-242">请尽可能使用 **/optimize** 选项替代为短编码。</span><span class="sxs-lookup"><span data-stu-id="fccd0-242">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="fccd0-243">Ildasm.exe 只对磁盘上的文件进行操作。</span><span class="sxs-lookup"><span data-stu-id="fccd0-243">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="fccd0-244">它不对安装在全局程序集缓存中的文件进行操作。</span><span class="sxs-lookup"><span data-stu-id="fccd0-244">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="fccd0-245">有关 IL 语法的更多信息，请参见 Windows SDK 中的 asmparse.grammar 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-245">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="fccd0-246">版本信息</span><span class="sxs-lookup"><span data-stu-id="fccd0-246">Version Information</span></span>

<span data-ttu-id="fccd0-247">从 .NET Framework 4.5 开始，可以使用类似于下面的代码将自定义特性附加到接口实现：</span><span class="sxs-lookup"><span data-stu-id="fccd0-247">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="fccd0-248">从 .NET Framework 4.5 开始，可以指定任意封送 BLOB（二进制大型对象），方法是使用其原始二进制表示形式，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="fccd0-248">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="fccd0-249">有关 IL 语法的更多信息，请参见 Windows SDK 中的 asmparse.grammar 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-249">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="fccd0-250">示例</span><span class="sxs-lookup"><span data-stu-id="fccd0-250">Examples</span></span>

<span data-ttu-id="fccd0-251">下面的命令对 IL 文件 myTestFile.il 进行汇编并生成可执行文件 myTestFile.exe 。</span><span class="sxs-lookup"><span data-stu-id="fccd0-251">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="fccd0-252">下面的命令对 IL 文件 myTestFile.il 进行汇编并生成 .dll 文件 myTestFile.dll  。</span><span class="sxs-lookup"><span data-stu-id="fccd0-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="fccd0-253">下面的命令对 IL 文件 myTestFile.il 进行汇编并生成 .dll 文件 myNewTestFile.dll  。</span><span class="sxs-lookup"><span data-stu-id="fccd0-253">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="fccd0-254">下面的代码示例演示了一个向控制台显示“Hello World!”的极其简单的</span><span class="sxs-lookup"><span data-stu-id="fccd0-254">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="fccd0-255">“Hello World!”。</span><span class="sxs-lookup"><span data-stu-id="fccd0-255">to the console.</span></span> <span data-ttu-id="fccd0-256">可编译此代码，然后使用 [Ildasm.exe](ildasm-exe-il-disassembler.md) 工具生成 IL 文件。</span><span class="sxs-lookup"><span data-stu-id="fccd0-256">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="fccd0-257">下面的 IL 代码示例对应于前面的 C# 代码示例。</span><span class="sxs-lookup"><span data-stu-id="fccd0-257">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="fccd0-258">可使用 IL Assembler 工具将此代码编译为程序集。</span><span class="sxs-lookup"><span data-stu-id="fccd0-258">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="fccd0-259">IL 和 C# 代码示例都向控制台显示</span><span class="sxs-lookup"><span data-stu-id="fccd0-259">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="fccd0-260">“Hello World!”。</span><span class="sxs-lookup"><span data-stu-id="fccd0-260">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="fccd0-261">请参阅</span><span class="sxs-lookup"><span data-stu-id="fccd0-261">See also</span></span>

- [<span data-ttu-id="fccd0-262">工具</span><span class="sxs-lookup"><span data-stu-id="fccd0-262">Tools</span></span>](index.md)
- [<span data-ttu-id="fccd0-263">Ildasm.exe（IL 反汇编程序）</span><span class="sxs-lookup"><span data-stu-id="fccd0-263">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="fccd0-264">托管执行过程</span><span class="sxs-lookup"><span data-stu-id="fccd0-264">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="fccd0-265">命令提示</span><span class="sxs-lookup"><span data-stu-id="fccd0-265">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
