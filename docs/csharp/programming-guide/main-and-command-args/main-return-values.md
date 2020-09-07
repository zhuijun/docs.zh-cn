---
title: Main() 返回值 - C# 编程指南
description: 了解 Main() 返回值。 查看代码示例、编译器生成的代码和其他可用资源。
ms.date: 08/02/2017
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 469ed872c1c8c4eb41eecd04277d4fc53fb3d112
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414638"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="9a354-104">Main() 返回值（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="9a354-104">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="9a354-105">`Main` 方法可以返回 `void`：</span><span class="sxs-lookup"><span data-stu-id="9a354-105">The `Main` method can return `void`:</span></span>

 [!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

<span data-ttu-id="9a354-106">还可以返回 `int`：</span><span class="sxs-lookup"><span data-stu-id="9a354-106">It can also return an `int`:</span></span>

 [!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

<span data-ttu-id="9a354-107">如果未使用 `Main` 的返回值，则返回 `void` 可以使代码变得略微简单。</span><span class="sxs-lookup"><span data-stu-id="9a354-107">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="9a354-108">但是，返回整数可使程序将状态信息传递给调用可执行文件的其他程序或脚本。</span><span class="sxs-lookup"><span data-stu-id="9a354-108">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="9a354-109">来自 `Main` 的返回值视为进程的退出代码。</span><span class="sxs-lookup"><span data-stu-id="9a354-109">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="9a354-110">如果从 `Main` 返回 `void`，则退出代码将为隐式 `0`。</span><span class="sxs-lookup"><span data-stu-id="9a354-110">If `void` is returned from `Main`, the exit code will be implicitly `0`.</span></span> <span data-ttu-id="9a354-111">以下示例演示了如何访问 `Main` 的返回值。</span><span class="sxs-lookup"><span data-stu-id="9a354-111">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="9a354-112">示例</span><span class="sxs-lookup"><span data-stu-id="9a354-112">Example</span></span>

<span data-ttu-id="9a354-113">此示例使用 [.NET Core](../../../core/introduction.md) 命令行工具。</span><span class="sxs-lookup"><span data-stu-id="9a354-113">This example uses [.NET Core](../../../core/introduction.md) command-line tools.</span></span> <span data-ttu-id="9a354-114">如果不熟悉 .NET Core 命令行工具，可通过本[入门文章](../../../core/tutorials/with-visual-studio-code.md)进行了解。</span><span class="sxs-lookup"><span data-stu-id="9a354-114">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="9a354-115">修改 program.cs 中的 `Main` 方法，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="9a354-115">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="9a354-116">在 Windows 中执行程序时，从 `Main` 函数返回的任何值都存储在环境变量中。</span><span class="sxs-lookup"><span data-stu-id="9a354-116">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="9a354-117">可使用批处理文件中的 `ERRORLEVEL` 或 PowerShell 中的 `$LastExitCode` 来检索此环境变量。</span><span class="sxs-lookup"><span data-stu-id="9a354-117">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="9a354-118">可使用 [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` 命令构建应用程序。</span><span class="sxs-lookup"><span data-stu-id="9a354-118">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="9a354-119">接下来，创建一个 Powershell 脚本来运行应用程序并显示结果。</span><span class="sxs-lookup"><span data-stu-id="9a354-119">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="9a354-120">将以下代码粘贴到文本文件中，并在包含该项目的文件夹中将其另存为 `test.ps1`。</span><span class="sxs-lookup"><span data-stu-id="9a354-120">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="9a354-121">可通过在 PowerShell 提示符下键入 `test.ps1` 来运行 PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="9a354-121">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="9a354-122">因为代码返回零，所以批处理文件将报告成功。</span><span class="sxs-lookup"><span data-stu-id="9a354-122">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="9a354-123">但是，如果将 MainReturnValTest.cs 更改为返回非零值，然后重新编译程序，则 PowerShell 脚本的后续执行将报告为失败。</span><span class="sxs-lookup"><span data-stu-id="9a354-123">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the powershell script will report failure.</span></span>

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="9a354-124">示例输出</span><span class="sxs-lookup"><span data-stu-id="9a354-124">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="9a354-125">Async Main 返回值</span><span class="sxs-lookup"><span data-stu-id="9a354-125">Async Main return values</span></span>

<span data-ttu-id="9a354-126">Async Main 返回值将在 `Main` 中调用异步方法时所需的样本代码移动到编译器生成的代码中。</span><span class="sxs-lookup"><span data-stu-id="9a354-126">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="9a354-127">以前，需要编写此结构来调用异步代码并确保程序运行至异步操作完成：</span><span class="sxs-lookup"><span data-stu-id="9a354-127">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="9a354-128">现在，可以将其替代为：</span><span class="sxs-lookup"><span data-stu-id="9a354-128">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="9a354-129">新语法的优点是编译器始终生成正确的代码。</span><span class="sxs-lookup"><span data-stu-id="9a354-129">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="9a354-130">编译器生成的代码</span><span class="sxs-lookup"><span data-stu-id="9a354-130">Compiler-generated code</span></span>

<span data-ttu-id="9a354-131">当应用程序入口点返回 `Task` 或 `Task<int>` 时，编译器生成一个新的入口点，该入口点调用应用程序代码中声明的入口点方法。</span><span class="sxs-lookup"><span data-stu-id="9a354-131">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="9a354-132">假设此入口点名为 `$GeneratedMain`，编译器将为这些入口点生成以下代码：</span><span class="sxs-lookup"><span data-stu-id="9a354-132">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="9a354-133">`static Task Main()` 导致编译器发出 `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();` 的等效项</span><span class="sxs-lookup"><span data-stu-id="9a354-133">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="9a354-134">`static Task Main(string[])` 导致编译器发出 `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` 的等效项</span><span class="sxs-lookup"><span data-stu-id="9a354-134">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="9a354-135">`static Task<int> Main()` 导致编译器发出 `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();` 的等效项</span><span class="sxs-lookup"><span data-stu-id="9a354-135">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="9a354-136">`static Task<int> Main(string[])` 导致编译器发出 `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` 的等效项</span><span class="sxs-lookup"><span data-stu-id="9a354-136">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="9a354-137">如果示例在 `Main` 方法上使用 `async` 修饰符，则编译器将生成相同的代码。</span><span class="sxs-lookup"><span data-stu-id="9a354-137">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a354-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="9a354-138">See also</span></span>

- [<span data-ttu-id="9a354-139">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="9a354-139">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9a354-140">C# 参考</span><span class="sxs-lookup"><span data-stu-id="9a354-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9a354-141">Main() 和命令行参数</span><span class="sxs-lookup"><span data-stu-id="9a354-141">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="9a354-142">如何显示命令行参数</span><span class="sxs-lookup"><span data-stu-id="9a354-142">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
