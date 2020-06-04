---
title: 使用 Visual Studio 调试 .NET Core 控制台应用程序
description: 了解如何使用 Visual Studio 调试 .NET Core 控制台应用。
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4bd2a8a0e4b3cea55e209306dd3788552e4b61f3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005409"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>教程：使用 Visual Studio 调试 .NET Core 控制台应用程序

本教程介绍了 Visual Studio 中提供的调试工具。

## <a name="prerequisites"></a>先决条件

- 本教程适用于[在 Visual Studio 2019 中创建 .NET Core 控制台应用程序](with-visual-studio.md)中创建的控制台应用。

## <a name="debug-build-configuration"></a>“调试”生成配置

“调试”和“发布”是 Visual Studio 的两种默认生成配置。 当前的生成配置显示在工具栏上。 下面的工具栏图像显示 Visual Studio 配置为编译应用的“调试”版本：

![突出显示“调试”的 Visual Studio 工具栏](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

首先运行应用的“调试”版本。 “调试”生成配置会禁用大多数编译器优化，并在生成过程中提供更丰富的信息。

## <a name="set-a-breakpoint"></a>设置断点

<!-- markdownlint-disable MD025 -->

1. 单击该行代码窗口的左边缘，在显示名称、日期和时间的行上设置断点。 设置断点的另一种方法是通过将光标置于代码行中，然后按 F9 或从菜单栏中选择“调试” > “切换断点”来进行设置  。

   断点会在执行包含断点的代码行之前暂时中断执行应用程序。

   如下图所示，Visual Studio 通过突出显示此代码行并在左边缘显示红点来指示设置了断点的行。

   ![设置断点后的 Visual Studio 程序窗口](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. 现在，选择工具栏上含绿色箭头的“HelloWorld”按钮，在调试模式下运行程序。 启动调试的其他方法是按 F5 或选择“调试” > “启动调试”  。

1. 当程序提示输入名称时，在控制台窗口中输入字符串，然后按 Enter。

1. 到达断点时，程序停止执行，然后执行 `Console.WriteLine` 方法。 “局部变量”窗口显示当前正在执行的方法中定义的变量值。

   ![Visual Studio 中断点的屏幕截图](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. 在“即时”窗口中，可以与正在调试的应用程序进行交互。 可以通过交互方式更改变量值，看看这样会对程序产生哪些影响。

   1. 如果“即时”窗口不可见，请选择“调试” > “Windows” > “即时”来显示它。

   1. 在“即时”窗口中输入 `name = "Gracie"`，然后按 Enter 键。

   1. 在“即时”窗口中输入 `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`，然后按 Enter 键。

   “即时”窗口显示字符串变量的值和 <xref:System.DateTime> 值的属性。 此外，“局部变量”窗口中也会更新变量值。

   ![Visual Studio 2019 中的“局部变量”和“即时”窗口](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. 选择工具栏中的“继续”按钮继续执行程序。 继续操作的另一种方法是选择“调试” > “继续” 。

   控制台窗口中显示的值对应于在“即时”窗口中所做的更改。

   ![显示输入值的控制台窗口](./media/debugging-with-visual-studio/console-window.png)

1. 按任意键，退出应用程序并停止调试。

## <a name="set-a-conditional-breakpoint"></a>设置条件断点

程序显示用户输入的字符串。 如果用户没有输入任何内容，情况又如何呢？ 可使用名为“条件断点”的实用调试功能来测试这种情况，该功能可在满足一个或多个条件时中断程序执行。

若要设置条件断点，并测试用户无法输入字符串时的情况如何，请执行以下操作：

1. 右键单击表示断点的红点。 在上下文菜单中，选择“条件”，打开“断点设置”对话框 。 选择“条件”框（如果尚未选择）。

   ![显示断点设置面板的编辑器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. 对于条件表达式，在显示测试 `x` 是否为 5 的示例代码的字段中输入以下代码。 如果未显示想要使用的语言，请更改页面顶部的语言选择器。

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   每次命中断点时，调试器都会调用 `String.IsNullOrEmpty(name)` 方法，仅当该方法调用返回 `true` 时，它才会在此行上中断。

   与条件表达式不同，你可以指定命中次数，这样程序就会在语句的执行次数达到指定值时中断执行；也可以指定筛选条件，这样就可以根据诸如线程标识符、进程名称或线程名称之类的属性来中断程序执行 。

1. 选择“关闭”以关闭对话框。

1. 通过按 F5 调试来启动程序。

1. 在控制台窗口中，在看到输入名称的提示时按 Enter 键。

1. 由于符合指定的条件（`name` 为 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>），因此程序会在到达断点时以及在 `Console.WriteLine` 方法执行之前停止执行。

1. 选择“局部变量”窗口，其中显示当前正在执行的方法的局部变量值。 在这种情况下，`Main` 是当前正在执行的方法。 请注意，`name` 变量的值为 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。

1. 在“即时”窗口中输入下面的语句并按 Enter，确认值为空字符串。 结果为 `true`。

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   问号指示即时窗口[计算表达式](/visualstudio/ide/reference/immediate-window#enter-commands)。

   ![在执行语句后返回值 true 的即时窗口 - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. 选择工具栏上的“继续”按钮，继续执行程序。

1. 按任意键，关闭控制台窗口并停止调试。

1. 单击代码窗口左边缘上的点，清除断点。 清除断点的另一种方法是在选中代码行时选择“调试”>“切换断点”。

## <a name="step-through-a-program"></a>单步执行程序

使用 Visual Studio，还可以单步执行程序，并监视其执行情况。 通常可以设置断点，并通过程序代码的一小部分执行程序流。 由于程序很小，因此可以单步执行整个程序。

1. 选择“调试” > “单步执行” 。 一次调试一个语句的另一种方法是按 F11。

   Visual Studio 会在要执行的下一行旁边突出显示一个箭头。

   C#

   ![Visual Studio 单步执行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Visual Studio 单步执行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   此时，“局部变量”窗口显示 `args` 数组为空，`name` 和 `date` 具有默认值。 此外，Visual Studio 还打开了一个空白控制台窗口。

1. 按下 F11。 Visual Studio 现在突出显示要执行的下一行。 “局部变量”窗口保持不变，控制台窗口仍为空白。

   C#

   ![Visual Studio 单步执行方法源 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Visual Studio 单步执行方法源 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. 按下 F11。 Visual Studio 突出显示包含 `name` 变量赋值的语句。 “局部变量”窗口显示 `name` 为 `null`，控制台窗口显示字符串“What is your name?”。

1. 在控制台窗口中输入字符串，然后按 Enter，从而响应提示。 控制台无响应，输入的字符串未显示在控制台窗口中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法将捕获输入。

1. 按下 F11。 Visual Studio 突出显示包含 `date` 变量赋值（在 Visual Basic 中为 `currentDate`）的语句。 “局部变量”窗口显示 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法调用返回的值。 控制台窗口还显示在提示符处输入的字符串。

1. 按下 F11。 “局部变量”窗口显示通过 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性赋值后的 `date` 变量值。 控制台窗口保持不变。

1. 按下 F11。 Visual Studio 调用 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 控制台窗口会显示格式化的字符串。

1. 选择“调试” > “跳出” 。停止分步执行的另一种方法是按 Shift+F11 。

   控制台窗口会显示一条消息，并等待用户按任意键。

1. 按任意键，关闭控制台窗口并停止调试。

## <a name="build-a-release-version"></a>生成“发布”版本

测试应用程序的“调试”版本后，还应该编译并测试“发布”版本。 发布版本包含编译器优化，有时可能会对应用程序的行为产生不良影响。 例如，旨在提升性能的编译器优化可能会在多线程应用程序中创建争用条件。

若要生成和测试控制台应用程序的发布版本，请将工具栏上的生成配置从“调试”更改为“发布”。

![默认 Visual Studio 工具栏，其中突出显示调试](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

按 F5 或选择“生成”菜单中的“生成解决方案”后，Visual Studio 会编译应用程序的“发布”版本。 可像测试“调试”版本一样测试“发布”版本。

## <a name="next-steps"></a>后续步骤

在本教程中，你使用了 Visual Studio 调试工具。 在下一教程中，你将发布应用的可部署版本。

> [!div class="nextstepaction"]
> [使用 Visual Studio 发布 .NET Core 控制台应用程序](publishing-with-visual-studio.md)
