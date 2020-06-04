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
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="b7bcf-103">教程：使用 Visual Studio 调试 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="b7bcf-103">Tutorial: Debug a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="b7bcf-104">本教程介绍了 Visual Studio 中提供的调试工具。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-104">This tutorial introduces the debugging tools available in Visual Studio.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b7bcf-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="b7bcf-105">Prerequisites</span></span>

- <span data-ttu-id="b7bcf-106">本教程适用于[在 Visual Studio 2019 中创建 .NET Core 控制台应用程序](with-visual-studio.md)中创建的控制台应用。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-106">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="debug-build-configuration"></a><span data-ttu-id="b7bcf-107">“调试”生成配置</span><span class="sxs-lookup"><span data-stu-id="b7bcf-107">Debug build configuration</span></span>

<span data-ttu-id="b7bcf-108">“调试”和“发布”是 Visual Studio 的两种默认生成配置。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-108">*Debug* and *Release* are two of Visual Studio's default build configurations.</span></span> <span data-ttu-id="b7bcf-109">当前的生成配置显示在工具栏上。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-109">The current build configuration is shown on the toolbar.</span></span> <span data-ttu-id="b7bcf-110">下面的工具栏图像显示 Visual Studio 配置为编译应用的“调试”版本：</span><span class="sxs-lookup"><span data-stu-id="b7bcf-110">The following toolbar image shows that Visual Studio is configured to compile the Debug version of the app:</span></span>

![突出显示“调试”的 Visual Studio 工具栏](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

<span data-ttu-id="b7bcf-112">首先运行应用的“调试”版本。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-112">Begin by running the Debug version of the app.</span></span> <span data-ttu-id="b7bcf-113">“调试”生成配置会禁用大多数编译器优化，并在生成过程中提供更丰富的信息。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-113">The Debug build configuration turns off most compiler optimizations and provides richer information during the build process.</span></span>

## <a name="set-a-breakpoint"></a><span data-ttu-id="b7bcf-114">设置断点</span><span class="sxs-lookup"><span data-stu-id="b7bcf-114">Set a breakpoint</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="b7bcf-115">单击该行代码窗口的左边缘，在显示名称、日期和时间的行上设置断点。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-115">Set a *breakpoint* on the line that displays the name, date, and time, by clicking in the left margin of the code window on that line.</span></span> <span data-ttu-id="b7bcf-116">设置断点的另一种方法是通过将光标置于代码行中，然后按 F9 或从菜单栏中选择“调试” > “切换断点”来进行设置  。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-116">Another way to set a breakpoint is by placing the cursor in the line of code and then pressing **F9** or choosing **Debug** > **Toggle Breakpoint** from the menu bar.</span></span>

   <span data-ttu-id="b7bcf-117">断点会在执行包含断点的代码行之前暂时中断执行应用程序。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-117">A breakpoint temporarily interrupts the execution of the application *before* the line with the breakpoint is executed.</span></span>

   <span data-ttu-id="b7bcf-118">如下图所示，Visual Studio 通过突出显示此代码行并在左边缘显示红点来指示设置了断点的行。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-118">As the following image shows, Visual Studio indicates the line on which the breakpoint is set by highlighting it and displaying a red dot in the left margin.</span></span>

   ![设置断点后的 Visual Studio 程序窗口](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. <span data-ttu-id="b7bcf-120">现在，选择工具栏上含绿色箭头的“HelloWorld”按钮，在调试模式下运行程序。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-120">Run the program in Debug mode by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span> <span data-ttu-id="b7bcf-121">启动调试的其他方法是按 F5 或选择“调试” > “启动调试”  。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-121">Other ways to start debugging are by pressing **F5** or by choosing **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="b7bcf-122">当程序提示输入名称时，在控制台窗口中输入字符串，然后按 Enter。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-122">Enter a string in the console window when the program prompts for a name, and then press **Enter**.</span></span>

1. <span data-ttu-id="b7bcf-123">到达断点时，程序停止执行，然后执行 `Console.WriteLine` 方法。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-123">Program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span> <span data-ttu-id="b7bcf-124">“局部变量”窗口显示当前正在执行的方法中定义的变量值。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-124">The **Locals** window displays the values of variables that are defined in the currently executing method.</span></span>

   ![Visual Studio 中断点的屏幕截图](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. <span data-ttu-id="b7bcf-126">在“即时”窗口中，可以与正在调试的应用程序进行交互。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-126">The **Immediate** window lets you interact with the application you're debugging.</span></span> <span data-ttu-id="b7bcf-127">可以通过交互方式更改变量值，看看这样会对程序产生哪些影响。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-127">You can interactively change the value of variables to see how it affects your program.</span></span>

   1. <span data-ttu-id="b7bcf-128">如果“即时”窗口不可见，请选择“调试” > “Windows” > “即时”来显示它。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-128">If the **Immediate** window is not visible, display it by choosing **Debug** > **Windows** > **Immediate**.</span></span>

   1. <span data-ttu-id="b7bcf-129">在“即时”窗口中输入 `name = "Gracie"`，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-129">Enter `name = "Gracie"` in the **Immediate** window and press the **Enter** key.</span></span>

   1. <span data-ttu-id="b7bcf-130">在“即时”窗口中输入 `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`，然后按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-130">Enter `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` in the **Immediate** window and press the **Enter** key.</span></span>

   <span data-ttu-id="b7bcf-131">“即时”窗口显示字符串变量的值和 <xref:System.DateTime> 值的属性。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-131">The **Immediate** window displays the value of the string variable and the properties of the <xref:System.DateTime> value.</span></span> <span data-ttu-id="b7bcf-132">此外，“局部变量”窗口中也会更新变量值。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-132">In addition, the values of the variables are updated in the **Locals** window.</span></span>

   ![Visual Studio 2019 中的“局部变量”和“即时”窗口](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. <span data-ttu-id="b7bcf-134">选择工具栏中的“继续”按钮继续执行程序。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-134">Continue program execution by selecting the **Continue** button in the toolbar.</span></span> <span data-ttu-id="b7bcf-135">继续操作的另一种方法是选择“调试” > “继续” 。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-135">Another way to continue is by choosing **Debug** > **Continue**.</span></span>

   <span data-ttu-id="b7bcf-136">控制台窗口中显示的值对应于在“即时”窗口中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-136">The values displayed in the console window correspond to the changes you made in the **Immediate** window.</span></span>

   ![显示输入值的控制台窗口](./media/debugging-with-visual-studio/console-window.png)

1. <span data-ttu-id="b7bcf-138">按任意键，退出应用程序并停止调试。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-138">Press any key to exit the application and stop debugging.</span></span>

## <a name="set-a-conditional-breakpoint"></a><span data-ttu-id="b7bcf-139">设置条件断点</span><span class="sxs-lookup"><span data-stu-id="b7bcf-139">Set a conditional breakpoint</span></span>

<span data-ttu-id="b7bcf-140">程序显示用户输入的字符串。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-140">The program displays the string that the user enters.</span></span> <span data-ttu-id="b7bcf-141">如果用户没有输入任何内容，情况又如何呢？</span><span class="sxs-lookup"><span data-stu-id="b7bcf-141">What happens if the user doesn't enter anything?</span></span> <span data-ttu-id="b7bcf-142">可使用名为“条件断点”的实用调试功能来测试这种情况，该功能可在满足一个或多个条件时中断程序执行。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-142">You can test this with a useful debugging feature called a *conditional breakpoint*, which breaks program execution when one or more conditions are met.</span></span>

<span data-ttu-id="b7bcf-143">若要设置条件断点，并测试用户无法输入字符串时的情况如何，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b7bcf-143">To set a conditional breakpoint and test what happens when the user fails to enter a string, do the following:</span></span>

1. <span data-ttu-id="b7bcf-144">右键单击表示断点的红点。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-144">Right-click on the red dot that represents the breakpoint.</span></span> <span data-ttu-id="b7bcf-145">在上下文菜单中，选择“条件”，打开“断点设置”对话框 。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-145">In the context menu, select **Conditions** to open the **Breakpoint Settings** dialog.</span></span> <span data-ttu-id="b7bcf-146">选择“条件”框（如果尚未选择）。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-146">Select the box for **Conditions** if it's not already selected.</span></span>

   ![显示断点设置面板的编辑器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. <span data-ttu-id="b7bcf-148">对于条件表达式，在显示测试 `x` 是否为 5 的示例代码的字段中输入以下代码。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-148">For the **Conditional Expression**, enter the following code in the field that shows example code that tests if `x` is 5.</span></span> <span data-ttu-id="b7bcf-149">如果未显示想要使用的语言，请更改页面顶部的语言选择器。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-149">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="b7bcf-150">每次命中断点时，调试器都会调用 `String.IsNullOrEmpty(name)` 方法，仅当该方法调用返回 `true` 时，它才会在此行上中断。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-150">Each time the breakpoint is hit, the debugger calls the `String.IsNullOrEmpty(name)` method, and it breaks on this line only if the method call returns `true`.</span></span>

   <span data-ttu-id="b7bcf-151">与条件表达式不同，你可以指定命中次数，这样程序就会在语句的执行次数达到指定值时中断执行；也可以指定筛选条件，这样就可以根据诸如线程标识符、进程名称或线程名称之类的属性来中断程序执行 。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-151">Instead of a conditional expression, you can specify a *hit count*, which interrupts program execution before a statement is executed a specified number of times, or a *filter condition*, which interrupts program execution based on such attributes as a thread identifier, process name, or thread name.</span></span>

1. <span data-ttu-id="b7bcf-152">选择“关闭”以关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-152">Select **Close** to close the dialog.</span></span>

1. <span data-ttu-id="b7bcf-153">通过按 F5 调试来启动程序。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-153">Start the program with debugging by pressing **F5**.</span></span>

1. <span data-ttu-id="b7bcf-154">在控制台窗口中，在看到输入名称的提示时按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-154">In the console window, press the **Enter** key when prompted to enter your name.</span></span>

1. <span data-ttu-id="b7bcf-155">由于符合指定的条件（`name` 为 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>），因此程序会在到达断点时以及在 `Console.WriteLine` 方法执行之前停止执行。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-155">Because the condition you specified (`name` is either `null` or <xref:System.String.Empty?displayProperty=nameWithType>) has been satisfied, program execution stops when it reaches the breakpoint and before the `Console.WriteLine` method executes.</span></span>

1. <span data-ttu-id="b7bcf-156">选择“局部变量”窗口，其中显示当前正在执行的方法的局部变量值。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-156">Select the **Locals** window, which shows the values of variables that are local to the currently executing method.</span></span> <span data-ttu-id="b7bcf-157">在这种情况下，`Main` 是当前正在执行的方法。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-157">In this case, `Main` is the currently executing method.</span></span> <span data-ttu-id="b7bcf-158">请注意，`name` 变量的值为 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-158">Observe that the value of the `name` variable is `""`, or <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>

1. <span data-ttu-id="b7bcf-159">在“即时”窗口中输入下面的语句并按 Enter，确认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-159">Confirm the value is an empty string by entering the following statement in the **Immediate** window and pressing **Enter**.</span></span> <span data-ttu-id="b7bcf-160">结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-160">The result is `true`.</span></span>

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   <span data-ttu-id="b7bcf-161">问号指示即时窗口[计算表达式](/visualstudio/ide/reference/immediate-window#enter-commands)。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-161">The question mark directs the immediate window to [evaluate an expression](/visualstudio/ide/reference/immediate-window#enter-commands).</span></span>

   ![在执行语句后返回值 true 的即时窗口 - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. <span data-ttu-id="b7bcf-163">选择工具栏上的“继续”按钮，继续执行程序。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-163">Select the **Continue** button on the toolbar to continue program execution.</span></span>

1. <span data-ttu-id="b7bcf-164">按任意键，关闭控制台窗口并停止调试。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-164">Press any key to close the console window and stop debugging.</span></span>

1. <span data-ttu-id="b7bcf-165">单击代码窗口左边缘上的点，清除断点。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-165">Clear the breakpoint by clicking on the dot in the left margin of the code window.</span></span> <span data-ttu-id="b7bcf-166">清除断点的另一种方法是在选中代码行时选择“调试”>“切换断点”。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-166">Another way to clear a breakpoint is by choosing **Debug > Toggle Breakpoint** while the line of code is selected.</span></span>

## <a name="step-through-a-program"></a><span data-ttu-id="b7bcf-167">单步执行程序</span><span class="sxs-lookup"><span data-stu-id="b7bcf-167">Step through a program</span></span>

<span data-ttu-id="b7bcf-168">使用 Visual Studio，还可以单步执行程序，并监视其执行情况。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-168">Visual Studio also allows you to step line by line through a program and monitor its execution.</span></span> <span data-ttu-id="b7bcf-169">通常可以设置断点，并通过程序代码的一小部分执行程序流。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-169">Ordinarily, you'd set a breakpoint and follow program flow through a small part of your program code.</span></span> <span data-ttu-id="b7bcf-170">由于程序很小，因此可以单步执行整个程序。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-170">Since your program is small, you can step through the entire program.</span></span>

1. <span data-ttu-id="b7bcf-171">选择“调试” > “单步执行” 。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-171">Choose **Debug** > **Step Into**.</span></span> <span data-ttu-id="b7bcf-172">一次调试一个语句的另一种方法是按 F11。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-172">Another way to debug one statement at a time is by pressing **F11**.</span></span>

   <span data-ttu-id="b7bcf-173">Visual Studio 会在要执行的下一行旁边突出显示一个箭头。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-173">Visual Studio highlights and displays an arrow beside the next line of execution.</span></span>

   <span data-ttu-id="b7bcf-174">C#</span><span class="sxs-lookup"><span data-stu-id="b7bcf-174">C#</span></span>

   ![Visual Studio 单步执行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   <span data-ttu-id="b7bcf-176">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7bcf-176">Visual Basic</span></span>

   ![Visual Studio 单步执行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   <span data-ttu-id="b7bcf-178">此时，“局部变量”窗口显示 `args` 数组为空，`name` 和 `date` 具有默认值。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-178">At this point, the **Locals** window shows that the `args` array is empty, and `name` and `date` have default values.</span></span> <span data-ttu-id="b7bcf-179">此外，Visual Studio 还打开了一个空白控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-179">In addition, Visual Studio has opened a blank console window.</span></span>

1. <span data-ttu-id="b7bcf-180">按下 F11。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-180">Press **F11**.</span></span> <span data-ttu-id="b7bcf-181">Visual Studio 现在突出显示要执行的下一行。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-181">Visual Studio now highlights the next line of execution.</span></span> <span data-ttu-id="b7bcf-182">“局部变量”窗口保持不变，控制台窗口仍为空白。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-182">The **Locals** window is unchanged, and the console window remains blank.</span></span>

   <span data-ttu-id="b7bcf-183">C#</span><span class="sxs-lookup"><span data-stu-id="b7bcf-183">C#</span></span>

   ![Visual Studio 单步执行方法源 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   <span data-ttu-id="b7bcf-185">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7bcf-185">Visual Basic</span></span>

   ![Visual Studio 单步执行方法源 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. <span data-ttu-id="b7bcf-187">按下 F11。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-187">Press **F11**.</span></span> <span data-ttu-id="b7bcf-188">Visual Studio 突出显示包含 `name` 变量赋值的语句。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-188">Visual Studio highlights the statement that includes the `name` variable assignment.</span></span> <span data-ttu-id="b7bcf-189">“局部变量”窗口显示 `name` 为 `null`，控制台窗口显示字符串“What is your name?”。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-189">The **Locals** window shows that `name` is `null`, and the console window displays the string "What is your name?".</span></span>

1. <span data-ttu-id="b7bcf-190">在控制台窗口中输入字符串，然后按 Enter，从而响应提示。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-190">Respond to the prompt by entering a string in the console window and pressing **Enter**.</span></span> <span data-ttu-id="b7bcf-191">控制台无响应，输入的字符串未显示在控制台窗口中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法将捕获输入。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-191">The console is unresponsive, and the string you entered isn't displayed in the console window, but the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method will nevertheless capture your input.</span></span>

1. <span data-ttu-id="b7bcf-192">按下 F11。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-192">Press **F11**.</span></span> <span data-ttu-id="b7bcf-193">Visual Studio 突出显示包含 `date` 变量赋值（在 Visual Basic 中为 `currentDate`）的语句。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-193">Visual Studio highlights the statement that includes the `date` variable assignment (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="b7bcf-194">“局部变量”窗口显示 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法调用返回的值。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-194">The **Locals** window shows the value returned by the call to the <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7bcf-195">控制台窗口还显示在提示符处输入的字符串。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-195">The console window also displays the string you entered at the prompt.</span></span>

1. <span data-ttu-id="b7bcf-196">按下 F11。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-196">Press **F11**.</span></span> <span data-ttu-id="b7bcf-197">“局部变量”窗口显示通过 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性赋值后的 `date` 变量值。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-197">The **Locals** window shows the value of the `date` variable after the assignment from the <xref:System.DateTime.Now?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b7bcf-198">控制台窗口保持不变。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-198">The console window is unchanged.</span></span>

1. <span data-ttu-id="b7bcf-199">按下 F11。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-199">Press **F11**.</span></span> <span data-ttu-id="b7bcf-200">Visual Studio 调用 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-200">Visual Studio calls the <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b7bcf-201">控制台窗口会显示格式化的字符串。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-201">The console window displays the formatted string.</span></span>

1. <span data-ttu-id="b7bcf-202">选择“调试” > “跳出” 。停止分步执行的另一种方法是按 Shift+F11 。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-202">Choose **Debug** > **Step Out**. Another way to stop step-by-step execution is by pressing **Shift**+**F11**.</span></span>

   <span data-ttu-id="b7bcf-203">控制台窗口会显示一条消息，并等待用户按任意键。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-203">The console window displays a message and waits for you to press a key.</span></span>

1. <span data-ttu-id="b7bcf-204">按任意键，关闭控制台窗口并停止调试。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-204">Press any key to close the console window and stop debugging.</span></span>

## <a name="build-a-release-version"></a><span data-ttu-id="b7bcf-205">生成“发布”版本</span><span class="sxs-lookup"><span data-stu-id="b7bcf-205">Build a Release version</span></span>

<span data-ttu-id="b7bcf-206">测试应用程序的“调试”版本后，还应该编译并测试“发布”版本。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-206">Once you've tested the Debug version of your application, you should also compile and test the Release version.</span></span> <span data-ttu-id="b7bcf-207">发布版本包含编译器优化，有时可能会对应用程序的行为产生不良影响。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-207">The Release version incorporates compiler optimizations that can sometimes negatively affect the behavior of an application.</span></span> <span data-ttu-id="b7bcf-208">例如，旨在提升性能的编译器优化可能会在多线程应用程序中创建争用条件。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-208">For example, compiler optimizations that are designed to improve performance can create race conditions in multithreaded applications.</span></span>

<span data-ttu-id="b7bcf-209">若要生成和测试控制台应用程序的发布版本，请将工具栏上的生成配置从“调试”更改为“发布”。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-209">To build and test the Release version of your console application, change the build configuration on the toolbar from **Debug** to **Release**.</span></span>

![默认 Visual Studio 工具栏，其中突出显示调试](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

<span data-ttu-id="b7bcf-211">按 F5 或选择“生成”菜单中的“生成解决方案”后，Visual Studio 会编译应用程序的“发布”版本。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-211">When you press **F5** or choose **Build Solution** from the **Build** menu, Visual Studio compiles the Release version of the application.</span></span> <span data-ttu-id="b7bcf-212">可像测试“调试”版本一样测试“发布”版本。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-212">You can test it as you did the Debug version.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b7bcf-213">后续步骤</span><span class="sxs-lookup"><span data-stu-id="b7bcf-213">Next steps</span></span>

<span data-ttu-id="b7bcf-214">在本教程中，你使用了 Visual Studio 调试工具。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-214">In this tutorial, you used Visual Studio debugging tools.</span></span> <span data-ttu-id="b7bcf-215">在下一教程中，你将发布应用的可部署版本。</span><span class="sxs-lookup"><span data-stu-id="b7bcf-215">In the next tutorial, you publish a deployable version of the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7bcf-216">使用 Visual Studio 发布 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="b7bcf-216">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
