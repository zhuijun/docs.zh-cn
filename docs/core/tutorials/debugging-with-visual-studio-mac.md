---
title: 使用 Visual Studio for Mac 调试 .NET Core 控制台应用程序
description: 了解如何使用 Visual Studio for Mac 调试 .NET Core 控制台应用。
ms.date: 06/08/2020
ms.openlocfilehash: 7e2a25266fab40b5ef1d0a38b8bbf06a6843746b
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416011"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="f6669-103">教程：使用 Visual Studio for Mac 调试 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="f6669-103">Tutorial: Debug a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="f6669-104">本教程介绍了 Visual Studio for Mac 中提供的调试工具。</span><span class="sxs-lookup"><span data-stu-id="f6669-104">This tutorial introduces the debugging tools available in Visual Studio for Mac.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6669-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="f6669-105">Prerequisites</span></span>

- <span data-ttu-id="f6669-106">本教程适用于按照[在 Visual Studio for Mac 中创建 .NET Core 控制台应用程序](with-visual-studio-mac.md)创建的控制台应用。</span><span class="sxs-lookup"><span data-stu-id="f6669-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="use-debug-build-configuration"></a><span data-ttu-id="f6669-107">使用“调试”生成配置</span><span class="sxs-lookup"><span data-stu-id="f6669-107">Use Debug build configuration</span></span>

<span data-ttu-id="f6669-108">“调试”和“发布”是 Visual Studio 的内置生成配置 。</span><span class="sxs-lookup"><span data-stu-id="f6669-108">*Debug* and *Release* are Visual Studio's built-in build configurations.</span></span> <span data-ttu-id="f6669-109">可使用“调试”生成配置进行调试，使用“发布”配置进行最终版本分发。</span><span class="sxs-lookup"><span data-stu-id="f6669-109">You use the Debug build configuration for debugging and the Release configuration for the final release distribution.</span></span>

<span data-ttu-id="f6669-110">在“调试”配置中，程序使用完整符号调试信息编译，且不进行优化。</span><span class="sxs-lookup"><span data-stu-id="f6669-110">In the Debug configuration, a program compiles with full symbolic debug information and no optimization.</span></span> <span data-ttu-id="f6669-111">优化会使调试复杂化，因为源代码和生成的指令之间的关系更加复杂。</span><span class="sxs-lookup"><span data-stu-id="f6669-111">Optimization complicates debugging, because the relationship between source code and generated instructions is more complex.</span></span> <span data-ttu-id="f6669-112">程序的发布配置进行了完全优化，且不包含任何符号调试信息。</span><span class="sxs-lookup"><span data-stu-id="f6669-112">The release configuration of a program has no symbolic debug information and is fully optimized.</span></span>

<span data-ttu-id="f6669-113">默认情况下，Visual Studio 使用“调试”生成配置，因此不需要在调试之前对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="f6669-113">By default, Visual Studio uses the Debug build configuration, so you don't need to change it before debugging.</span></span>

1. <span data-ttu-id="f6669-114">启动 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="f6669-114">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="f6669-115">打开按照[在 Visual Studio for Mac 中创建 .NET Core 控制台应用程序](with-visual-studio-mac.md)创建的项目。</span><span class="sxs-lookup"><span data-stu-id="f6669-115">Open the project that you created in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

   <span data-ttu-id="f6669-116">当前的生成配置显示在工具栏上。</span><span class="sxs-lookup"><span data-stu-id="f6669-116">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="f6669-117">下面的工具栏图像显示 Visual Studio 配置为编译应用的“调试”版本：</span><span class="sxs-lookup"><span data-stu-id="f6669-117">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="突出显示“调试”的 Visual Studio 工具栏":::

## <a name="set-a-breakpoint"></a><span data-ttu-id="f6669-119">设置断点</span><span class="sxs-lookup"><span data-stu-id="f6669-119">Set a breakpoint</span></span>

<span data-ttu-id="f6669-120">断点会在执行包含断点的代码行之前暂时中断执行应用程序。</span><span class="sxs-lookup"><span data-stu-id="f6669-120">A *breakpoint* temporarily interrupts the execution of the application before the line with the breakpoint is executed.</span></span>

1. <span data-ttu-id="f6669-121">在显示名称、日期和时间的行上设置断点。</span><span class="sxs-lookup"><span data-stu-id="f6669-121">Set a breakpoint on the line that displays the name, date, and time.</span></span> <span data-ttu-id="f6669-122">为此，请将光标放在代码行中，然后按 <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>)。</span><span class="sxs-lookup"><span data-stu-id="f6669-122">To do that, place the cursor in the line of code and press <kbd>⌘</kbd><kbd>\\</kbd> (<kbd>command</kbd>+<kbd>\\</kbd>).</span></span> <span data-ttu-id="f6669-123">设置断点的另一种方法是从菜单中选择“运行” > “切换断点”。</span><span class="sxs-lookup"><span data-stu-id="f6669-123">Another way to set a breakpoint is by selecting **Run** > **Toggle Breakpoint** from the menu.</span></span>

   <span data-ttu-id="f6669-124">Visual Studio 通过突出显示此代码行并在左边缘显示红点来指示设置了断点的行。</span><span class="sxs-lookup"><span data-stu-id="f6669-124">Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="设置断点后的 Visual Studio 程序窗口":::

1. <span data-ttu-id="f6669-126">按 <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) 以在调试模式下启动程序。</span><span class="sxs-lookup"><span data-stu-id="f6669-126">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start the program in debugging mode.</span></span> <span data-ttu-id="f6669-127">启动调试的另一种方法是从菜单中选择“运行” > “启动调试”。</span><span class="sxs-lookup"><span data-stu-id="f6669-127">Another way to start debugging is by choosing **Run** > **Start Debugging** from the menu.</span></span>

1. <span data-ttu-id="f6669-128">当程序提示输入名称时，在终端窗口中输入字符串，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f6669-128">Enter a string in the terminal window when the program prompts for a name, and then press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="f6669-129">到达断点时，程序停止执行，然后执行 `Console.WriteLine` 方法。</span><span class="sxs-lookup"><span data-stu-id="f6669-129">Program execution stops when it reaches the breakpoint, before the `Console.WriteLine` method executes.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Visual Studio 中断点的屏幕截图":::

## <a name="use-the-immediate-window"></a><span data-ttu-id="f6669-131">使用“即时”窗口</span><span class="sxs-lookup"><span data-stu-id="f6669-131">Use the Immediate window</span></span>

<span data-ttu-id="f6669-132">在“即时”窗口中，可以与正在调试的应用程序进行交互。</span><span class="sxs-lookup"><span data-stu-id="f6669-132">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="f6669-133">可以通过交互方式更改变量值，看看这样会对程序产生哪些影响。</span><span class="sxs-lookup"><span data-stu-id="f6669-133">You can interactively change the value of variables to see how it affects your program.</span></span>

1. <span data-ttu-id="f6669-134">如果“即时”窗口不可见，请选择“视图” > “调试边栏” > “即时”来显示它。</span><span class="sxs-lookup"><span data-stu-id="f6669-134">If the **Immediate** window is not visible, display it by choosing **View** > **Debug Pads** > **Immediate**.</span></span>

1. <span data-ttu-id="f6669-135">在“即时”窗口中输入 `name = "Gracie"`，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f6669-135">Enter `name = "Gracie"` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="f6669-136">在“即时”窗口中输入 `date = date.AddDays(1)`，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f6669-136">Enter `date = date.AddDays(1)` in the **Immediate** window and press <kbd>enter</kbd>.</span></span>

   <span data-ttu-id="f6669-137">“即时”窗口显示字符串变量的新值和 <xref:System.DateTime> 值的属性。</span><span class="sxs-lookup"><span data-stu-id="f6669-137">The **Immediate** window displays the new value of the string variable and the properties of the <xref:System.DateTime> value.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Visual Studio 中的“即时”窗口":::

   <span data-ttu-id="f6669-139">“局部变量”窗口显示当前正在执行的方法中定义的变量值。</span><span class="sxs-lookup"><span data-stu-id="f6669-139">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span> <span data-ttu-id="f6669-140">“局部变量”窗口中会更新刚更改的变量的值。</span><span class="sxs-lookup"><span data-stu-id="f6669-140">The values of the variables that you just changed are updated in the **Locals** window.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Visual Studio 中的“局部变量”窗口":::

1. <span data-ttu-id="f6669-142">按 <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) 以继续调试。</span><span class="sxs-lookup"><span data-stu-id="f6669-142">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

   <span data-ttu-id="f6669-143">终端中显示的值对应于在“即时”窗口中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="f6669-143">The values displayed in the terminal correspond to the changes you made in the **Immediate** window.</span></span>

   <span data-ttu-id="f6669-144">如果看不到终端，请选择底部导航栏中的“终端 - HelloWorld”。</span><span class="sxs-lookup"><span data-stu-id="f6669-144">If you don't see the Terminal, select **Terminal - HelloWorld** in the bottom navigation bar.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="底部导航栏中的“终端 - Hello World”":::

1. <span data-ttu-id="f6669-146">按任意键退出程序。</span><span class="sxs-lookup"><span data-stu-id="f6669-146">Press any key to exit the program.</span></span>

1. <span data-ttu-id="f6669-147">关闭终端窗口。</span><span class="sxs-lookup"><span data-stu-id="f6669-147">Close the terminal window.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="f6669-148">设置条件断点</span><span class="sxs-lookup"><span data-stu-id="f6669-148">Set a conditional breakpoint</span></span>

<span data-ttu-id="f6669-149">程序显示用户输入的字符串。</span><span class="sxs-lookup"><span data-stu-id="f6669-149">The program displays a string that the user enters.</span></span> <span data-ttu-id="f6669-150">如果用户没有输入任何内容，情况又如何呢？</span><span class="sxs-lookup"><span data-stu-id="f6669-150">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="f6669-151">可以使用名为“条件断点”的有用调试功能对此进行测试。</span><span class="sxs-lookup"><span data-stu-id="f6669-151">You can test this with a useful debugging feature called a *conditional breakpoint*.</span></span>

1. <span data-ttu-id="f6669-152">按 <kbd>Ctrl</kbd> 并单击表示断点的红点。</span><span class="sxs-lookup"><span data-stu-id="f6669-152"><kbd>ctrl</kbd>-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="f6669-153">在上下文菜单中，选择“编辑断点”。</span><span class="sxs-lookup"><span data-stu-id="f6669-153">In the context menu, select **Edit Breakpoint**.</span></span>

1. <span data-ttu-id="f6669-154">在“编辑断点”对话框中，在遵循“且以下条件为 true”的字段中输入以下代码，然后选择“应用”  。</span><span class="sxs-lookup"><span data-stu-id="f6669-154">In the **Edit Breakpoint** dialog, enter the following code in the field that follows **And the following condition is true**, and select **Apply**.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="显示断点设置面板的编辑器":::

   <span data-ttu-id="f6669-156">每次命中断点时，调试器都会调用 `String.IsNullOrEmpty(name)` 方法，仅当该方法调用返回 `true` 时，它才会在此行上中断。</span><span class="sxs-lookup"><span data-stu-id="f6669-156">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="f6669-157">可以指定“命中次数”（而不是条件表达式），这样程序就会在语句的执行次数达到指定值时中断执行。</span><span class="sxs-lookup"><span data-stu-id="f6669-157">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times.</span></span>

1. <span data-ttu-id="f6669-158">按 <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) 以启动调试。</span><span class="sxs-lookup"><span data-stu-id="f6669-158">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

1. <span data-ttu-id="f6669-159">在终端窗口中，在系统提示输入姓名时按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="f6669-159">In the terminal window, press <kbd>enter</kbd> when prompted to enter your name.</span></span>

   <span data-ttu-id="f6669-160">由于符合指定的条件（`name` 为 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>），因此程序会在到达断点时停止执行。</span><span class="sxs-lookup"><span data-stu-id="f6669-160">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint.</span></span>

1. <span data-ttu-id="f6669-161">选择“局部变量”窗口，其中显示当前正在执行的方法的局部变量值。</span><span class="sxs-lookup"><span data-stu-id="f6669-161">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="f6669-162">在这种情况下，`Main` 是当前正在执行的方法。</span><span class="sxs-lookup"><span data-stu-id="f6669-162">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="f6669-163">请注意，`name` 变量的值为 `""`，即 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f6669-163">Observe that the value of the `name` variable is `""`, that is, <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="f6669-164">还可以通过在“即时”窗口中输入 `name` 变量名称并按 <kbd>Enter</kbd> 来看到值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="f6669-164">You can also see that the value is an empty string by entering the `name` variable name in the **Immediate** window and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="显示名称为空字符串的“即时”窗口":::

1. <span data-ttu-id="f6669-166">按 <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) 以继续调试。</span><span class="sxs-lookup"><span data-stu-id="f6669-166">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to continue debugging.</span></span>

1. <span data-ttu-id="f6669-167">在终端窗口中，按任意键退出程序。</span><span class="sxs-lookup"><span data-stu-id="f6669-167">In the terminal window, press any key to exit the program.</span></span>

1. <span data-ttu-id="f6669-168">关闭终端窗口。</span><span class="sxs-lookup"><span data-stu-id="f6669-168">Close the terminal window.</span></span>

1. <span data-ttu-id="f6669-169">单击代码窗口左边缘上的红点，清除断点。</span><span class="sxs-lookup"><span data-stu-id="f6669-169">Clear the breakpoint by clicking on the red dot in the left margin of the code window.</span></span> <span data-ttu-id="f6669-170">清除断点的另一种方法是在选中代码行时选择“运行”>“切换断点”。</span><span class="sxs-lookup"><span data-stu-id="f6669-170">Another way to clear a breakpoint is by choosing **Run > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="f6669-171">单步执行程序</span><span class="sxs-lookup"><span data-stu-id="f6669-171">Step through a program</span></span>

<span data-ttu-id="f6669-172">使用 Visual Studio，还可以单步执行程序，并监视其执行情况。</span><span class="sxs-lookup"><span data-stu-id="f6669-172">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="f6669-173">通常可以设置断点，并通过程序代码的一小部分执行程序流。</span><span class="sxs-lookup"><span data-stu-id="f6669-173">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="f6669-174">由于此程序很小，因此可以单步执行整个程序。</span><span class="sxs-lookup"><span data-stu-id="f6669-174">Since this program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="f6669-175">在标记 `Main` 方法的开头的大括号处设置断点（按 <kbd>command</kbd>+<kbd>\\</kbd>）。</span><span class="sxs-lookup"><span data-stu-id="f6669-175">Set a breakpoint on the curly brace that marks the start of the `Main` method (press <kbd>command</kbd>+<kbd>\\</kbd>).</span></span>

1. <span data-ttu-id="f6669-176">按 <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) 以启动调试。</span><span class="sxs-lookup"><span data-stu-id="f6669-176">Press <kbd>⌘</kbd><kbd>↵</kbd> (<kbd>command</kbd>+<kbd>enter</kbd>) to start debugging.</span></span>

   <span data-ttu-id="f6669-177">Visual Studio 在包含断点的行上停止。</span><span class="sxs-lookup"><span data-stu-id="f6669-177">Visual Studio stops on the line with the breakpoint.</span></span>

1. <span data-ttu-id="f6669-178">按 <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) 或选择“运行” > “单步执行”以推进一行。</span><span class="sxs-lookup"><span data-stu-id="f6669-178">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>) or select **Run** > **Step Into** to advance one line.</span></span>

   <span data-ttu-id="f6669-179">Visual Studio 会在要执行的下一行旁边突出显示一个箭头。</span><span class="sxs-lookup"><span data-stu-id="f6669-179">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Visual Studio 单步执行方法":::

   <span data-ttu-id="f6669-181">此时，“局部变量”窗口显示 `args` 数组为空，`name` 和 `date` 具有默认值。</span><span class="sxs-lookup"><span data-stu-id="f6669-181">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="f6669-182">此外，Visual Studio 还打开了一个空白终端。</span><span class="sxs-lookup"><span data-stu-id="f6669-182">In addition, Visual Studio has opened a blank terminal.</span></span>

1. <span data-ttu-id="f6669-183">按 <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)。</span><span class="sxs-lookup"><span data-stu-id="f6669-183">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="f6669-184">Visual Studio 突出显示包含 `name` 变量赋值的语句。</span><span class="sxs-lookup"><span data-stu-id="f6669-184">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="f6669-185">“局部变量”窗口显示 `name` 为 `null`，终端显示字符串“What is your name?”。</span><span class="sxs-lookup"><span data-stu-id="f6669-185">The **Locals** window shows that `name` is `null`, and the terminal displays the string "What is your name?".</span></span>

1. <span data-ttu-id="f6669-186">在控制台窗口中输入字符串，然后按 <kbd>Enter</kbd>，从而响应提示。</span><span class="sxs-lookup"><span data-stu-id="f6669-186">Respond to the prompt by entering a string in the console window and pressing <kbd>enter</kbd>.</span></span>

1. <span data-ttu-id="f6669-187">按 <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)。</span><span class="sxs-lookup"><span data-stu-id="f6669-187">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="f6669-188">Visual Studio 突出显示包含 `date` 变量赋值的语句。</span><span class="sxs-lookup"><span data-stu-id="f6669-188">Visual Studio highlights the statement that includes the `date` variable assignment.</span></span> <span data-ttu-id="f6669-189">“局部变量”窗口显示 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法调用返回的值。</span><span class="sxs-lookup"><span data-stu-id="f6669-189">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f6669-190">终端显示在提示符处输入的字符串。</span><span class="sxs-lookup"><span data-stu-id="f6669-190">The terminal displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="f6669-191">按 <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)。</span><span class="sxs-lookup"><span data-stu-id="f6669-191">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="f6669-192">“局部变量”窗口显示通过 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性赋值后的 `date` 变量值。</span><span class="sxs-lookup"><span data-stu-id="f6669-192">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f6669-193">终端无变化。</span><span class="sxs-lookup"><span data-stu-id="f6669-193">The terminal is unchanged.</span></span>

1. <span data-ttu-id="f6669-194">按 <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>)。</span><span class="sxs-lookup"><span data-stu-id="f6669-194">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>I</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>I</kbd>).</span></span>

   <span data-ttu-id="f6669-195">Visual Studio 调用 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="f6669-195">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f6669-196">终端会显示格式化的字符串。</span><span class="sxs-lookup"><span data-stu-id="f6669-196">The terminal displays the formatted string.</span></span>

1. <span data-ttu-id="f6669-197">按 <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) 或选择“运行” > “单步跳出”。</span><span class="sxs-lookup"><span data-stu-id="f6669-197">Press <kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>U</kbd>) or select **Run** > **Step Out**.</span></span>

   <span data-ttu-id="f6669-198">终端会显示一条消息，并等待用户按任意键。</span><span class="sxs-lookup"><span data-stu-id="f6669-198">The terminal displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="f6669-199">按任意键退出程序。</span><span class="sxs-lookup"><span data-stu-id="f6669-199">Press any key to exit the program.</span></span>

## <a name="use-release-build-configuration"></a><span data-ttu-id="f6669-200">使用“发布”生成配置</span><span class="sxs-lookup"><span data-stu-id="f6669-200">Use Release build configuration</span></span>

<span data-ttu-id="f6669-201">测试应用程序的“调试”版本后，还应该编译并测试“发布”版本。</span><span class="sxs-lookup"><span data-stu-id="f6669-201">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="f6669-202">发布版本包含编译器优化，可能会对应用程序的行为产生不良影响。</span><span class="sxs-lookup"><span data-stu-id="f6669-202">The Release version incorporates compiler optimizations that can negatively affect the behavior of an application.</span></span> <span data-ttu-id="f6669-203">例如，旨在提升性能的编译器优化可能会在多线程应用程序中创建争用条件。</span><span class="sxs-lookup"><span data-stu-id="f6669-203">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="f6669-204">若要生成和测试控制台应用程序的发布版本，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="f6669-204">To build and test the Release version of the console application, do the following steps:</span></span>

1. <span data-ttu-id="f6669-205">将工具栏上的生成配置从“调试”更改为“发布”。</span><span class="sxs-lookup"><span data-stu-id="f6669-205">Change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="突出显示“调试”的默认 Visual Studio 工具栏":::

1. <span data-ttu-id="f6669-207">按 <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) 以运行但不调试。</span><span class="sxs-lookup"><span data-stu-id="f6669-207">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run without debugging.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f6669-208">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f6669-208">Next steps</span></span>

<span data-ttu-id="f6669-209">在本教程中，你使用了 Visual Studio 调试工具。</span><span class="sxs-lookup"><span data-stu-id="f6669-209">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="f6669-210">在下一教程中，你将发布应用的可部署版本。</span><span class="sxs-lookup"><span data-stu-id="f6669-210">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f6669-211">使用 Visual Studio for Mac 发布 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="f6669-211">Publish a .NET Core console application with Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
