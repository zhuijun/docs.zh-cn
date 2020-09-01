---
description: '#line - C# 参考'
title: '#line - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: e2a5ecb6c29184123b8a88ae1b12caf24ec7296a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137989"
---
# <a name="line-c-reference"></a><span data-ttu-id="f5ffe-103">#line（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f5ffe-103">#line (C# Reference)</span></span>

<span data-ttu-id="f5ffe-104">借助 `#line`，可修改编译器的行号及（可选）用于错误和警告的文件名输出。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-104">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="f5ffe-105">以下示例演示如何报告与行号相关联的两个警告。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-105">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="f5ffe-106">`#line 200` 指令将下一行的行号强制设为 200（尽管默认值为 #6）；在执行下一个 `#line` 指令前，文件名都会报告为“特殊”。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-106">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="f5ffe-107">`#line default` 指令将行号恢复至默认行号，这会对上一指令重新编号的行进行计数。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-107">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

<span data-ttu-id="f5ffe-108">编译产生以下输出：</span><span class="sxs-lookup"><span data-stu-id="f5ffe-108">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="f5ffe-109">备注</span><span class="sxs-lookup"><span data-stu-id="f5ffe-109">Remarks</span></span>

<span data-ttu-id="f5ffe-110">可在生成过程的自动、中间步骤中使用 `#line` 指令。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-110">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="f5ffe-111">例如，如果已从原始源代码文件中删除行，但仍希望编译器基于文件中的原始行号生成输出，可在删除行后，使用 `#line` 来模拟原始行号。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-111">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="f5ffe-112">`#line hidden` 指令能对调试程序隐藏连续行，当开发者逐行执行代码时，介于 `#line hidden` 和下一 `#line` 指令（假设它不是其他 `#line hidden` 指令）间的任何行都将被跳过。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-112">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="f5ffe-113">还可通过此选项允许 ASP.NET 区分用户定义和计算机生成的代码。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-113">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="f5ffe-114">虽然此功能主要用于 ASP.NET，但可能更多的源生成器会利用此功能。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-114">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="f5ffe-115">`#line hidden` 指令不影响错误报告中的文件名或行号。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-115">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="f5ffe-116">也就是说，如果在隐藏块中遇到错误，编译器将报告错误的当前文件名和行号。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-116">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="f5ffe-117">`#line filename` 指令可指定要在编译器输出中显示的文件名。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-117">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="f5ffe-118">默认情况下，将使用源代码文件的实际名称。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-118">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="f5ffe-119">该文件名必须以双引号 ("") 引起来，且必须位于行号之后。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-119">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="f5ffe-120">源代码文件中可包含任意数目的 `#line` 指令。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-120">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="f5ffe-121">示例 1</span><span class="sxs-lookup"><span data-stu-id="f5ffe-121">Example 1</span></span>

<span data-ttu-id="f5ffe-122">下列示例演示调试程序如何忽略代码中的隐藏行。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-122">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="f5ffe-123">运行示例时，它将显示三行文本。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-123">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="f5ffe-124">但是，如果按照示例所示设置断点、并按 F10 逐行执行代码，可观察到调试程序忽略隐藏行。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-124">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="f5ffe-125">另请注意，即使在隐藏行设置断点，调试程序仍将忽略它。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-125">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f5ffe-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5ffe-126">See also</span></span>

- [<span data-ttu-id="f5ffe-127">C# 参考</span><span class="sxs-lookup"><span data-stu-id="f5ffe-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f5ffe-128">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="f5ffe-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f5ffe-129">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="f5ffe-129">C# Preprocessor Directives</span></span>](./index.md)
