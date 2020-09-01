---
description: extern 修饰符 - C# 参考
title: extern 修饰符 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 25eb5e6642d8b608bedcb4e9adadde4d84c2bae9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138964"
---
# <a name="extern-c-reference"></a><span data-ttu-id="b9685-103">extern（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="b9685-103">extern (C# Reference)</span></span>

<span data-ttu-id="b9685-104">`extern` 修饰符用于声明在外部实现的方法。</span><span class="sxs-lookup"><span data-stu-id="b9685-104">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="b9685-105">`extern` 修饰符的常见用法是在使用 Interop 服务调入非托管代码时与 `DllImport` 特性一起使用。</span><span class="sxs-lookup"><span data-stu-id="b9685-105">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="b9685-106">在这种情况下，还必须将方法声明为 `static`，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="b9685-106">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="b9685-107">`extern` 关键字还可以定义外部程序集别名，使得可以从单个程序集中引用同一组件的不同版本。</span><span class="sxs-lookup"><span data-stu-id="b9685-107">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="b9685-108">有关详细信息，请参阅[外部别名](extern-alias.md)。</span><span class="sxs-lookup"><span data-stu-id="b9685-108">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="b9685-109">将 [abstract](abstract.md) 和 `extern` 修饰符一起使用来修改同一成员是错误的做法。</span><span class="sxs-lookup"><span data-stu-id="b9685-109">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="b9685-110">使用 `extern` 修饰符意味着方法是在 C# 代码的外部实现的，而使用 `abstract` 修饰符意味着类中未提供方法实现。</span><span class="sxs-lookup"><span data-stu-id="b9685-110">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="b9685-111">extern 关键字用于 C# 中时会比用于 C++ 中时受到更多的限制。</span><span class="sxs-lookup"><span data-stu-id="b9685-111">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="b9685-112">若要比较 C# 关键字与 C++ 关键字，请参见 C++ 语言参考中的“使用 extern 指定链接”。</span><span class="sxs-lookup"><span data-stu-id="b9685-112">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="b9685-113">示例 1</span><span class="sxs-lookup"><span data-stu-id="b9685-113">Example 1</span></span>

<span data-ttu-id="b9685-114">在此示例中，程序接收来自用户的字符串并将该字符串显示在消息框中。</span><span class="sxs-lookup"><span data-stu-id="b9685-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="b9685-115">程序使用从 User32.dll 库导入的 `MessageBox` 方法。</span><span class="sxs-lookup"><span data-stu-id="b9685-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="b9685-116">示例 2</span><span class="sxs-lookup"><span data-stu-id="b9685-116">Example 2</span></span>

<span data-ttu-id="b9685-117">此示例阐释了调入 C 库（本机 DLL）的 C# 程序。</span><span class="sxs-lookup"><span data-stu-id="b9685-117">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="b9685-118">创建以下 C 文件并将其命名为 `cmdll.c`：</span><span class="sxs-lookup"><span data-stu-id="b9685-118">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="b9685-119">从 Visual Studio 安装目录打开 Visual Studio x64（或 x32）本机工具命令提示符窗口，并通过在命令提示符处键入“cl -LD cmdll.c”来编译 `cmdll.c` 文件\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9685-119">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="b9685-120">在相同的目录中，创建以下 C# 文件并将其命名为 `cm.cs`：</span><span class="sxs-lookup"><span data-stu-id="b9685-120">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

    ```csharp
    // cm.cs
    using System;
    using System.Runtime.InteropServices;
    public class MainClass
    {
        [DllImport("Cmdll.dll")]
          public static extern int SampleMethod(int x);

        static void Main()
        {
            Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
        }
    }
    ```

4. <span data-ttu-id="b9685-121">从 Visual Studio 安装目录打开一个 Visual Studio x64（或 x32）本机工具命令提示符窗口，并通过键入以下内容来编译 `cm.cs` 文件：</span><span class="sxs-lookup"><span data-stu-id="b9685-121">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="b9685-122">“csc cm.cs”（针对 x64 命令提示符）或“csc -platform:x86 cm.cs”（针对 x32 命令提示符）\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="b9685-122">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="b9685-123">这将创建可执行文件 `cm.exe`。</span><span class="sxs-lookup"><span data-stu-id="b9685-123">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="b9685-124">运行 `cm.exe`。</span><span class="sxs-lookup"><span data-stu-id="b9685-124">Run `cm.exe`.</span></span> <span data-ttu-id="b9685-125">`SampleMethod` 方法将值 5 传递到 DLL 文件，这将返回该值与 10 相乘后的结果。</span><span class="sxs-lookup"><span data-stu-id="b9685-125">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="b9685-126">该程序生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="b9685-126">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="b9685-127">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="b9685-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b9685-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="b9685-128">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="b9685-129">C# 参考</span><span class="sxs-lookup"><span data-stu-id="b9685-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b9685-130">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="b9685-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b9685-131">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="b9685-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b9685-132">修饰符</span><span class="sxs-lookup"><span data-stu-id="b9685-132">Modifiers</span></span>](index.md)
