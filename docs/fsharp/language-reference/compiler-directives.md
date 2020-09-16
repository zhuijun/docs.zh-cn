---
title: 编译器指令
description: '了解 F # 语言预处理器指令、条件编译指令、行指令和编译器指令。'
ms.date: 12/10/2018
f1_keywords:
- '#endif_FS'
ms.openlocfilehash: c3e1a07e0e09b5ae090c550368f8a9f8ee575bfb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557315"
---
# <a name="compiler-directives"></a><span data-ttu-id="fba41-103">编译器指令</span><span class="sxs-lookup"><span data-stu-id="fba41-103">Compiler Directives</span></span>

<span data-ttu-id="fba41-104">本主题介绍处理器指令和编译器指令。</span><span class="sxs-lookup"><span data-stu-id="fba41-104">This topic describes processor directives and compiler directives.</span></span>

## <a name="preprocessor-directives"></a><span data-ttu-id="fba41-105">预处理器指令</span><span class="sxs-lookup"><span data-stu-id="fba41-105">Preprocessor Directives</span></span>

<span data-ttu-id="fba41-106">预处理器指令以 # 符号作为前缀，出现在行本身上。</span><span class="sxs-lookup"><span data-stu-id="fba41-106">A preprocessor directive is prefixed with the # symbol and appears on a line by itself.</span></span> <span data-ttu-id="fba41-107">它由预处理器进行解释，后者在编译器本身之前运行。</span><span class="sxs-lookup"><span data-stu-id="fba41-107">It is interpreted by the preprocessor, which runs before the compiler itself.</span></span>

<span data-ttu-id="fba41-108">下表列出了 F# 中可用的预处理器指令。</span><span class="sxs-lookup"><span data-stu-id="fba41-108">The following table lists the preprocessor directives that are available in F#.</span></span>

|<span data-ttu-id="fba41-109">指令</span><span class="sxs-lookup"><span data-stu-id="fba41-109">Directive</span></span>|<span data-ttu-id="fba41-110">描述</span><span class="sxs-lookup"><span data-stu-id="fba41-110">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="fba41-111">`#if`*符号*</span><span class="sxs-lookup"><span data-stu-id="fba41-111">`#if` *symbol*</span></span>|<span data-ttu-id="fba41-112">支持条件编译。</span><span class="sxs-lookup"><span data-stu-id="fba41-112">Supports conditional compilation.</span></span> <span data-ttu-id="fba41-113">如果定义了符号，则包括之后的部分中的代码 `#if` 。 *symbol*</span><span class="sxs-lookup"><span data-stu-id="fba41-113">Code in the section after the `#if` is included if the *symbol* is defined.</span></span> <span data-ttu-id="fba41-114">还可以对符号求反 `!` 。</span><span class="sxs-lookup"><span data-stu-id="fba41-114">The symbol can also be negated with `!`.</span></span>|
|`#else`|<span data-ttu-id="fba41-115">支持条件编译。</span><span class="sxs-lookup"><span data-stu-id="fba41-115">Supports conditional compilation.</span></span> <span data-ttu-id="fba41-116">如果未定义与前面的 `#if` 一起使用的符号，则将一段代码标记为包含在内。</span><span class="sxs-lookup"><span data-stu-id="fba41-116">Marks a section of code to include if the symbol used with the previous `#if` is not defined.</span></span>|
|`#endif`|<span data-ttu-id="fba41-117">支持条件编译。</span><span class="sxs-lookup"><span data-stu-id="fba41-117">Supports conditional compilation.</span></span> <span data-ttu-id="fba41-118">标记条件代码段的末尾。</span><span class="sxs-lookup"><span data-stu-id="fba41-118">Marks the end of a conditional section of code.</span></span>|
|<span data-ttu-id="fba41-119">`#`内嵌 *int*、</span><span class="sxs-lookup"><span data-stu-id="fba41-119">`#`[line] *int*,</span></span><br/><span data-ttu-id="fba41-120">`#`内嵌 *int* *字符串*、</span><span class="sxs-lookup"><span data-stu-id="fba41-120">`#`[line] *int* *string*,</span></span><br/><span data-ttu-id="fba41-121">`#`内嵌 *int* *原义字符串*</span><span class="sxs-lookup"><span data-stu-id="fba41-121">`#`[line] *int* *verbatim-string*</span></span>|<span data-ttu-id="fba41-122">指示原始源代码行和文件名以用于调试。</span><span class="sxs-lookup"><span data-stu-id="fba41-122">Indicates the original source code line and file name, for debugging.</span></span> <span data-ttu-id="fba41-123">此功能是为生成 F# 源代码的工具而提供的。</span><span class="sxs-lookup"><span data-stu-id="fba41-123">This feature is provided for tools that generate F# source code.</span></span>|
|<span data-ttu-id="fba41-124">`#nowarn`*warningcode*</span><span class="sxs-lookup"><span data-stu-id="fba41-124">`#nowarn` *warningcode*</span></span>|<span data-ttu-id="fba41-125">禁用编译器警告。</span><span class="sxs-lookup"><span data-stu-id="fba41-125">Disables a compiler warning or warnings.</span></span> <span data-ttu-id="fba41-126">若要禁用警告，请在编译器输出中查找其编号，然后将它包含在引号内。</span><span class="sxs-lookup"><span data-stu-id="fba41-126">To disable a warning, find its number from the compiler output and include it in quotation marks.</span></span> <span data-ttu-id="fba41-127">省略“FS”前缀。</span><span class="sxs-lookup"><span data-stu-id="fba41-127">Omit the "FS" prefix.</span></span> <span data-ttu-id="fba41-128">若要禁用同一行上的多个警告编号，请将每个编号用引号引起来，并使用空格分隔每个字符串。</span><span class="sxs-lookup"><span data-stu-id="fba41-128">To disable multiple warning numbers on the same line, include each number in quotation marks, and separate each string by a space.</span></span> <span data-ttu-id="fba41-129">例如：</span><span class="sxs-lookup"><span data-stu-id="fba41-129">For example:</span></span>

`#nowarn "9" "40"`

<span data-ttu-id="fba41-130">禁用警告的效果适用于整个文件，包括指令前面的部分文件。 |</span><span class="sxs-lookup"><span data-stu-id="fba41-130">The effect of disabling a warning applies to the entire file, including portions of the file that precede the directive.|</span></span>

## <a name="conditional-compilation-directives"></a><span data-ttu-id="fba41-131">条件编译指令</span><span class="sxs-lookup"><span data-stu-id="fba41-131">Conditional Compilation Directives</span></span>

<span data-ttu-id="fba41-132">通过其中一个指令停用的代码在 Visual Studio Code 编辑器中显示为灰色。</span><span class="sxs-lookup"><span data-stu-id="fba41-132">Code that is deactivated by one of these directives appears dimmed in the Visual Studio Code Editor.</span></span>

> [!NOTE]
> <span data-ttu-id="fba41-133">条件编译指令的行为与它在其他语言中的行为不同。</span><span class="sxs-lookup"><span data-stu-id="fba41-133">The behavior of the conditional compilation directives is not the same as it is in other languages.</span></span> <span data-ttu-id="fba41-134">例如，不能使用涉及符号的布尔表达式，并且 `true` 和 `false` 没有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="fba41-134">For example, you cannot use Boolean expressions involving symbols, and `true` and `false` have no special meaning.</span></span> <span data-ttu-id="fba41-135">在 `if` 指令中使用的符号必须通过命令行或在项目设置中定义；没有 `define` 预处理器指令。</span><span class="sxs-lookup"><span data-stu-id="fba41-135">Symbols that you use in the `if` directive must be defined by the command line or in the project settings; there is no `define` preprocessor directive.</span></span>

<span data-ttu-id="fba41-136">以下代码演示了 `#if`、`#else` 和 `#endif` 指令的用法。</span><span class="sxs-lookup"><span data-stu-id="fba41-136">The following code illustrates the use of the `#if`, `#else`, and `#endif` directives.</span></span> <span data-ttu-id="fba41-137">在此示例中，代码包含两个版本的 `function1` 定义。</span><span class="sxs-lookup"><span data-stu-id="fba41-137">In this example, the code contains two versions of the definition of `function1`.</span></span> <span data-ttu-id="fba41-138">当 `VERSION1` 使用 [-define 编译器选项](./compiler-options.md)定义时，将 `#if` 激活指令和指令之间的代码 `#else` 。</span><span class="sxs-lookup"><span data-stu-id="fba41-138">When `VERSION1` is defined by using the [-define compiler option](./compiler-options.md), the code between the `#if` directive and the `#else` directive is activated.</span></span> <span data-ttu-id="fba41-139">否则，会激活 `#else` 与 `#endif` 之间的代码。</span><span class="sxs-lookup"><span data-stu-id="fba41-139">Otherwise, the code between `#else` and `#endif` is activated.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

<span data-ttu-id="fba41-140">F# 中没有 `#define` 预处理器指令。</span><span class="sxs-lookup"><span data-stu-id="fba41-140">There is no `#define` preprocessor directive in F#.</span></span> <span data-ttu-id="fba41-141">必须使用编译器选项或项目设置来定义 `#if` 指令使用的符号。</span><span class="sxs-lookup"><span data-stu-id="fba41-141">You must use the compiler option or project settings to define the symbols used by the `#if` directive.</span></span>

<span data-ttu-id="fba41-142">条件编译指令可以进行嵌套。</span><span class="sxs-lookup"><span data-stu-id="fba41-142">Conditional compilation directives can be nested.</span></span> <span data-ttu-id="fba41-143">缩进对于预处理器指令并不重要。</span><span class="sxs-lookup"><span data-stu-id="fba41-143">Indentation is not significant for preprocessor directives.</span></span>

<span data-ttu-id="fba41-144">你还可以使用对符号求反 `!` 。</span><span class="sxs-lookup"><span data-stu-id="fba41-144">You can also negate a symbol with `!`.</span></span> <span data-ttu-id="fba41-145">在此示例中，仅当 _不_ 调试时，字符串的值才是：</span><span class="sxs-lookup"><span data-stu-id="fba41-145">In this example, a string's value is something only when _not_ debugging:</span></span>

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a><span data-ttu-id="fba41-146">行指令</span><span class="sxs-lookup"><span data-stu-id="fba41-146">Line Directives</span></span>

<span data-ttu-id="fba41-147">在生成时，编译器会通过引用每个错误发生时所在的行号来报告 F# 代码中的错误。</span><span class="sxs-lookup"><span data-stu-id="fba41-147">When building, the compiler reports errors in F# code by referencing line numbers on which each error occurs.</span></span> <span data-ttu-id="fba41-148">这些行号从 1 开始（表示文件中的第一行）。</span><span class="sxs-lookup"><span data-stu-id="fba41-148">These line numbers start at 1 for the first line in a file.</span></span> <span data-ttu-id="fba41-149">但是，如果要从另一种工具生成 F# 源代码，则生成的代码中的行号通常没什么意义，因为生成的 F# 代码中的错误很可能是由其他来源导致的。</span><span class="sxs-lookup"><span data-stu-id="fba41-149">However, if you are generating F# source code from another tool, the line numbers in the generated code are generally not of interest, because the errors in the generated F# code most likely arise from another source.</span></span> <span data-ttu-id="fba41-150">`#line` 指令提供了一种方法，使生成 F# 源代码的工具的作者可以将有关原始行号和源文件的信息传递给生成的 F# 代码。</span><span class="sxs-lookup"><span data-stu-id="fba41-150">The `#line` directive provides a way for authors of tools that generate F# source code to pass information about the original line numbers and source files to the generated F# code.</span></span>

<span data-ttu-id="fba41-151">使用 `#line` 指令时，必须将文件名括在引号内。</span><span class="sxs-lookup"><span data-stu-id="fba41-151">When you use the `#line` directive, file names must be enclosed in quotation marks.</span></span> <span data-ttu-id="fba41-152">除非原义标记 (`@`) 出现在字符串前面，否则必须使用两个反斜杠字符（而不是一个）对反斜杠字符进行转义，才能在路径中使用它们。</span><span class="sxs-lookup"><span data-stu-id="fba41-152">Unless the verbatim token (`@`) appears in front of the string, you must escape backslash characters by using two backslash characters instead of one in order to use them in the path.</span></span> <span data-ttu-id="fba41-153">以下是有效的行标记。</span><span class="sxs-lookup"><span data-stu-id="fba41-153">The following are valid line tokens.</span></span> <span data-ttu-id="fba41-154">在这些示例中，假设原始文件 `Script1` 会在通过某种工具运行时产生自动生成的 F# 代码文件，并且这些指令的位置处的代码是从文件 `Script1` 中第 25 行处的一些标记生成的。</span><span class="sxs-lookup"><span data-stu-id="fba41-154">In these examples, assume that the original file `Script1` results in an automatically generated F# code file when it is run through a tool, and that the code at the location of these directives is generated from some tokens at line 25 in file `Script1`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

<span data-ttu-id="fba41-155">这些标记指示在此位置生成的 F# 代码派生自位于 `Script1` 中第 `25` 行上或附近的一些构造。</span><span class="sxs-lookup"><span data-stu-id="fba41-155">These tokens indicate that the F# code generated at this location is derived from some constructs at or near line `25` in `Script1`.</span></span>

## <a name="compiler-directives"></a><span data-ttu-id="fba41-156">编译器指令</span><span class="sxs-lookup"><span data-stu-id="fba41-156">Compiler Directives</span></span>

<span data-ttu-id="fba41-157">编译器指令类似于预处理器指令，因为它们以 # 符号作为前缀，但它们留给编译器进行解释和处理，而不是由预处理器进行解释。</span><span class="sxs-lookup"><span data-stu-id="fba41-157">Compiler directives resemble preprocessor directives, because they are prefixed with a # sign, but instead of being interpreted by the preprocessor, they are left for the compiler to interpret and act on.</span></span>

<span data-ttu-id="fba41-158">下表列出了在 F# 中可用的编译器指令。</span><span class="sxs-lookup"><span data-stu-id="fba41-158">The following table lists the compiler directive that is available in F#.</span></span>

|<span data-ttu-id="fba41-159">指令</span><span class="sxs-lookup"><span data-stu-id="fba41-159">Directive</span></span>|<span data-ttu-id="fba41-160">描述</span><span class="sxs-lookup"><span data-stu-id="fba41-160">Description</span></span>|
|---------|-----------|
|<span data-ttu-id="fba41-161">`#light` ["on" &#124; "off"]</span><span class="sxs-lookup"><span data-stu-id="fba41-161">`#light` ["on"&#124;"off"]</span></span>|<span data-ttu-id="fba41-162">启用或禁用轻量语法，以便与其他版本的 ML 兼容。</span><span class="sxs-lookup"><span data-stu-id="fba41-162">Enables or disables lightweight syntax, for compatibility with other versions of ML.</span></span> <span data-ttu-id="fba41-163">默认情况下，轻量语法处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="fba41-163">By default, lightweight syntax is enabled.</span></span> <span data-ttu-id="fba41-164">详细语法始终处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="fba41-164">Verbose syntax is always enabled.</span></span> <span data-ttu-id="fba41-165">因此，可以同时使用轻量语法和详细语法。</span><span class="sxs-lookup"><span data-stu-id="fba41-165">Therefore, you can use both lightweight syntax and verbose syntax.</span></span> <span data-ttu-id="fba41-166">指令 `#light` 本身等效于 `#light "on"`。</span><span class="sxs-lookup"><span data-stu-id="fba41-166">The directive `#light` by itself is equivalent to `#light "on"`.</span></span> <span data-ttu-id="fba41-167">如果指定 `#light "off"`，则必须对所有语言构造使用详细语法。</span><span class="sxs-lookup"><span data-stu-id="fba41-167">If you specify `#light "off"`, you must use verbose syntax for all language constructs.</span></span> <span data-ttu-id="fba41-168">F# 文档中展示的语法基于使用轻量语法这一假设。</span><span class="sxs-lookup"><span data-stu-id="fba41-168">Syntax in the documentation for F# is presented with the assumption that you are using lightweight syntax.</span></span> <span data-ttu-id="fba41-169">有关详细信息，请参阅 [详细语法](verbose-syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="fba41-169">For more information, see [Verbose Syntax](verbose-syntax.md).</span></span>|

<span data-ttu-id="fba41-170">对于解释器 ( # A0) 指令，请参阅 [与 F # 交互编程](../tutorials/fsharp-interactive/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fba41-170">For interpreter (fsi.exe) directives, see [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fba41-171">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fba41-171">See also</span></span>

- [<span data-ttu-id="fba41-172">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="fba41-172">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="fba41-173">编译器选项</span><span class="sxs-lookup"><span data-stu-id="fba41-173">Compiler Options</span></span>](compiler-options.md)
