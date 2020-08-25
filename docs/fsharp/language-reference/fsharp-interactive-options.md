---
title: 交互式选项
description: 了解 F# 交互窗口、fsi.exe 支持的命令行选项。
ms.date: 08/15/2020
ms.openlocfilehash: adc8dc86f14366720e1acbf35115d4e318a76aef
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810525"
---
# <a name="f-interactive-options"></a><span data-ttu-id="58f4e-103">F# 交互窗口选项</span><span class="sxs-lookup"><span data-stu-id="58f4e-103">F# Interactive options</span></span>

<span data-ttu-id="58f4e-104">本文介绍 F# 交互窗口支持的命令行选项 `fsi.exe` 。</span><span class="sxs-lookup"><span data-stu-id="58f4e-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="58f4e-105">F# 交互窗口接受许多与 F # 编译器相同的命令行选项，但也接受一些其他选项。</span><span class="sxs-lookup"><span data-stu-id="58f4e-105">F# Interactive accepts many of the same command-line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="58f4e-106">使用 F# 交互窗口进行脚本编写</span><span class="sxs-lookup"><span data-stu-id="58f4e-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="58f4e-107">F# 交互窗口， `dotnet fsi` 可以交互方式启动，也可以从命令行启动以运行脚本。</span><span class="sxs-lookup"><span data-stu-id="58f4e-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="58f4e-108">命令行语法为</span><span class="sxs-lookup"><span data-stu-id="58f4e-108">The command-line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="58f4e-109">F # 脚本文件的文件扩展名为 `.fsx` 。</span><span class="sxs-lookup"><span data-stu-id="58f4e-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="58f4e-110">F# 交互窗口选项的表</span><span class="sxs-lookup"><span data-stu-id="58f4e-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="58f4e-111">下表总结了 F# 交互窗口支持的选项。</span><span class="sxs-lookup"><span data-stu-id="58f4e-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="58f4e-112">可以在命令行上或通过 Visual Studio IDE 设置这些选项。</span><span class="sxs-lookup"><span data-stu-id="58f4e-112">You can set these options on the command line or through the Visual Studio IDE.</span></span> <span data-ttu-id="58f4e-113">若要在 Visual Studio IDE 中设置这些选项，请打开 " **工具** " 菜单，选择 " **选项**"，展开 " **F # 工具** " 节点，然后选择 " **F# 交互窗口**"。</span><span class="sxs-lookup"><span data-stu-id="58f4e-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options**, expand the **F# Tools** node, and then select **F# Interactive**.</span></span>

<span data-ttu-id="58f4e-114">其中列表显示在 F# 交互窗口选项参数中，列表元素由分号分隔 (`;`) 。</span><span class="sxs-lookup"><span data-stu-id="58f4e-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="58f4e-115">选项</span><span class="sxs-lookup"><span data-stu-id="58f4e-115">Option</span></span>|<span data-ttu-id="58f4e-116">说明</span><span class="sxs-lookup"><span data-stu-id="58f4e-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="58f4e-117">用于指示 F# 交互窗口将剩余的参数作为命令行参数处理 F # 程序或脚本，您可以使用 **Fsi.exe my.application.commandlineargs**的代码访问这些参数。</span><span class="sxs-lookup"><span data-stu-id="58f4e-117">Used to instruct F# Interactive to treat remaining arguments as command-line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="58f4e-118">**--checked**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-119">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-120">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-121">**--代码页： &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="58f4e-122">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-123">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-125">输出警告和错误消息的颜色。</span><span class="sxs-lookup"><span data-stu-id="58f4e-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="58f4e-126">**--crossoptimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-127">启用或禁用跨模块优化。</span><span class="sxs-lookup"><span data-stu-id="58f4e-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="58f4e-128">**--debug**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="58f4e-129">**--debug：**[**full**&#124;**pdbonly**&#124;**可移植**&#124;**嵌入**]</span><span class="sxs-lookup"><span data-stu-id="58f4e-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="58f4e-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="58f4e-131">**-g：**[**full**&#124;**pdbonly**&#124;**可移植**&#124;**嵌入**]</span><span class="sxs-lookup"><span data-stu-id="58f4e-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="58f4e-132">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-133">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-134">**--define： &lt; string&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="58f4e-135">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-136">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-137">**--确定性**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-138">生成一个确定性程序集 (包括模块版本 GUID 和时间戳) 。</span><span class="sxs-lookup"><span data-stu-id="58f4e-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="58f4e-139">**--exec**</span><span class="sxs-lookup"><span data-stu-id="58f4e-139">**--exec**</span></span>|<span data-ttu-id="58f4e-140">指示 F # interactive 在加载文件或运行命令行上给定的脚本文件后退出。</span><span class="sxs-lookup"><span data-stu-id="58f4e-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="58f4e-141">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="58f4e-141">**--fullpaths**</span></span>|<span data-ttu-id="58f4e-142">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-143">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-144">**--gui**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-145">启用或禁用 Windows 窗体事件循环。</span><span class="sxs-lookup"><span data-stu-id="58f4e-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="58f4e-146">默认是启用的。</span><span class="sxs-lookup"><span data-stu-id="58f4e-146">The default is enabled.</span></span>|
|<span data-ttu-id="58f4e-147">**--帮助**</span><span class="sxs-lookup"><span data-stu-id="58f4e-147">**--help**</span></span><br /><br /><span data-ttu-id="58f4e-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="58f4e-148">**-?**</span></span>|<span data-ttu-id="58f4e-149">用于显示命令行语法和每个选项的简短说明。</span><span class="sxs-lookup"><span data-stu-id="58f4e-149">Used to display the command-line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="58f4e-150">**--lib： &lt; 文件夹-列表&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="58f4e-151">**-I： &lt; 文件夹列表&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="58f4e-152">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-153">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-154">**--load： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="58f4e-155">在启动时编译给定的源代码，并将已编译的 F # 构造加载到会话中。</span><span class="sxs-lookup"><span data-stu-id="58f4e-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span>|
|<span data-ttu-id="58f4e-156">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="58f4e-156">**--mlcompatibility**</span></span>|<span data-ttu-id="58f4e-157">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-157">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-158">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-158">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-159">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="58f4e-159">**--noframework**</span></span>|<span data-ttu-id="58f4e-160">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-160">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-161">有关详细信息，请参阅 [编译器选项](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="58f4e-161">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="58f4e-162">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="58f4e-162">**--nologo**</span></span>|<span data-ttu-id="58f4e-163">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-163">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-164">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-164">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-165">**--nowarn： &lt; warning-list&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-165">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="58f4e-166">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-166">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-167">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-167">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-168">**--optimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-168">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-169">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-169">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-170">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-170">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-171">**--preferreduilang： &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-171">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="58f4e-172">指定首选输出语言区域性名称 (例如，es，ja-jp) 。</span><span class="sxs-lookup"><span data-stu-id="58f4e-172">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="58f4e-173">**--quiet**</span><span class="sxs-lookup"><span data-stu-id="58f4e-173">**--quiet**</span></span>|<span data-ttu-id="58f4e-174">抑制 F# 交互窗口输出到 **stdout** 流。</span><span class="sxs-lookup"><span data-stu-id="58f4e-174">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="58f4e-175">**--引用-调试**</span><span class="sxs-lookup"><span data-stu-id="58f4e-175">**--quotations-debug**</span></span>|<span data-ttu-id="58f4e-176">指定应为从 F # 引号文本和反射定义派生的表达式发出额外的调试信息。</span><span class="sxs-lookup"><span data-stu-id="58f4e-176">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="58f4e-177">调试信息将添加到 F # 表达式树节点的自定义属性中。</span><span class="sxs-lookup"><span data-stu-id="58f4e-177">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="58f4e-178">请参阅 [代码引用](code-quotations.md) 和 [CustomAttributes](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html#CustomAttributes)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-178">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html#CustomAttributes).</span></span>|
|<span data-ttu-id="58f4e-179">**--readline**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-179">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-180">启用或禁用交互模式下的 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="58f4e-180">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="58f4e-181">**--reference： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-181">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="58f4e-182">**-r： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-182">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="58f4e-183">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-183">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-184">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-184">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-185">**--tailcalls**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-185">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-186">启用或禁用 tail IL 指令，这将导致为尾递归函数重用堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="58f4e-186">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="58f4e-187">默认情况下会启用此选项。</span><span class="sxs-lookup"><span data-stu-id="58f4e-187">This option is enabled by default.</span></span>|
|<span data-ttu-id="58f4e-188">**--targetprofile： &lt; string&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-188">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="58f4e-189">指定此程序集的目标框架配置文件。</span><span class="sxs-lookup"><span data-stu-id="58f4e-189">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="58f4e-190">有效值为 `mscorlib`、`netcore` 或 `netstandard`。</span><span class="sxs-lookup"><span data-stu-id="58f4e-190">Valid values are `mscorlib`, `netcore`, or `netstandard`.</span></span> <span data-ttu-id="58f4e-191">默认为 `mscorlib`。</span><span class="sxs-lookup"><span data-stu-id="58f4e-191">The default is `mscorlib`.</span></span>|
|<span data-ttu-id="58f4e-192">**--use： &lt; filename&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-192">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="58f4e-193">通知解释器在启动时使用给定文件作为初始输入。</span><span class="sxs-lookup"><span data-stu-id="58f4e-193">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="58f4e-194">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="58f4e-194">**--utf8output**</span></span>|<span data-ttu-id="58f4e-195">与 fsc.exe 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-195">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="58f4e-196">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-196">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-197">**--warning： &lt; 警告级别&gt;**</span><span class="sxs-lookup"><span data-stu-id="58f4e-197">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="58f4e-198">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-198">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-199">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-199">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-200">**--warnaserror**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="58f4e-200">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="58f4e-201">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-201">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-202">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-202">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="58f4e-203">**--warnaserror**[ **+**&#124;**-** ]：\*\* &lt; int-list &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="58f4e-203">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="58f4e-204">与 **fsc.exe** 编译器选项相同。</span><span class="sxs-lookup"><span data-stu-id="58f4e-204">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="58f4e-205">有关详细信息，请参阅 [编译器选项](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="58f4e-205">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="58f4e-206">F# 交互窗口结构化打印</span><span class="sxs-lookup"><span data-stu-id="58f4e-206">F# Interactive structured printing</span></span>

<span data-ttu-id="58f4e-207">F# 交互窗口 (`dotnet fsi`) 使用 [结构化纯文本格式](plaintext-formatting.md) 的扩展版本来报告值。</span><span class="sxs-lookup"><span data-stu-id="58f4e-207">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="58f4e-208">`%A`支持纯文本格式的所有功能，一些功能还可自定义。</span><span class="sxs-lookup"><span data-stu-id="58f4e-208">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="58f4e-209">如果输出控制台支持颜色，打印将着色。</span><span class="sxs-lookup"><span data-stu-id="58f4e-209">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="58f4e-210">将限制放置在显示的字符串的长度，除非显式计算该字符串。</span><span class="sxs-lookup"><span data-stu-id="58f4e-210">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="58f4e-211">可以通过对象使用一组可由用户定义的设置 `fsi` 。</span><span class="sxs-lookup"><span data-stu-id="58f4e-211">A set of user-definable settings is available via the `fsi` object.</span></span>

<span data-ttu-id="58f4e-212">用于自定义报告值的纯文本打印的可用设置包括：</span><span class="sxs-lookup"><span data-stu-id="58f4e-212">The available settings to customize plain text printing for reported values are:</span></span>

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="58f4e-213">自定义 `AddPrinter` 和 `AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="58f4e-213">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="58f4e-214">可以使用和自定义打印 F# 交互窗口输出 `fsi.AddPrinter` `fsi.AddPrintTransformer` 。</span><span class="sxs-lookup"><span data-stu-id="58f4e-214">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="58f4e-215">第一个函数提供文本来替换对象打印。</span><span class="sxs-lookup"><span data-stu-id="58f4e-215">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="58f4e-216">第二个函数返回要改为显示的代理项对象。</span><span class="sxs-lookup"><span data-stu-id="58f4e-216">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="58f4e-217">例如，请考虑以下 F # 代码：</span><span class="sxs-lookup"><span data-stu-id="58f4e-217">For example, consider the following F# code:</span></span>

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

<span data-ttu-id="58f4e-218">如果在 F# 交互窗口中执行该示例，则会根据格式设置选项集输出。</span><span class="sxs-lookup"><span data-stu-id="58f4e-218">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="58f4e-219">在这种情况下，它会影响日期和时间的格式：</span><span class="sxs-lookup"><span data-stu-id="58f4e-219">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="58f4e-220">`fsi.AddPrintTransformer` 可用于为打印提供代理项对象：</span><span class="sxs-lookup"><span data-stu-id="58f4e-220">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="58f4e-221">此输出：</span><span class="sxs-lookup"><span data-stu-id="58f4e-221">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="58f4e-222">如果传递给的转换器函数 `fsi.AddPrintTransformer` 返回 `null` ，则会忽略 print 转换器。</span><span class="sxs-lookup"><span data-stu-id="58f4e-222">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="58f4e-223">这可用于通过从类型开始筛选任何输入值 `obj` 。</span><span class="sxs-lookup"><span data-stu-id="58f4e-223">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="58f4e-224">例如：</span><span class="sxs-lookup"><span data-stu-id="58f4e-224">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="58f4e-225">此输出：</span><span class="sxs-lookup"><span data-stu-id="58f4e-225">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="58f4e-226">相关主题</span><span class="sxs-lookup"><span data-stu-id="58f4e-226">Related topics</span></span>

|<span data-ttu-id="58f4e-227">Title</span><span class="sxs-lookup"><span data-stu-id="58f4e-227">Title</span></span>|<span data-ttu-id="58f4e-228">描述</span><span class="sxs-lookup"><span data-stu-id="58f4e-228">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="58f4e-229">编译器选项</span><span class="sxs-lookup"><span data-stu-id="58f4e-229">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="58f4e-230">介绍可用于 F # 编译器的命令行选项 **fsc.exe**。</span><span class="sxs-lookup"><span data-stu-id="58f4e-230">Describes command-line options available for the F# compiler, **fsc.exe**.</span></span>|
