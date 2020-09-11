---
title: 在 Visual Studio for Mac 中使用 .NET Core 测试 .NET Standard 类库
description: 为 .NET Core 类库创建单元测试项目。 验证 .NET Core 类库能否正确地进行单元测试。
ms.date: 06/08/2020
ms.openlocfilehash: d3c8a5e01d16047949e977f3af6a429970d996d0
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359215"
---
# <a name="test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="101e4-104">在 Visual Studio 中使用 .NET Core 测试 .NET Standard 类库</span><span class="sxs-lookup"><span data-stu-id="101e4-104">Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="101e4-105">本教程演示如何通过将测试项目添加到解决方案来自动执行单元测试。</span><span class="sxs-lookup"><span data-stu-id="101e4-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="101e4-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="101e4-106">Prerequisites</span></span>

- <span data-ttu-id="101e4-107">本教程适用于在[使用 Visual Studio for Mac 创建 .NET Standard 库](library-with-visual-studio-mac.md)中创建的解决方案。</span><span class="sxs-lookup"><span data-stu-id="101e4-107">This tutorial works with the solution that you create in [Create a .NET Standard library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="101e4-108">创建单元测试项目</span><span class="sxs-lookup"><span data-stu-id="101e4-108">Create a unit test project</span></span>

<span data-ttu-id="101e4-109">单元测试在开发和发布期间提供自动化的软件测试。</span><span class="sxs-lookup"><span data-stu-id="101e4-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="101e4-110">[MSTest](https://github.com/Microsoft/testfx-docs) 是可供选择的三个测试框架之一。</span><span class="sxs-lookup"><span data-stu-id="101e4-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="101e4-111">其他两个是 [xUnit](https://xunit.net/) 和 [nUnit](https://nunit.org/)。</span><span class="sxs-lookup"><span data-stu-id="101e4-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="101e4-112">启动 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="101e4-112">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="101e4-113">打开在[使用 Visual Studio for Mac 创建 .NET Standard 库](library-with-visual-studio-mac.md)中创建的 `ClassLibraryProjects` 解决方案。</span><span class="sxs-lookup"><span data-stu-id="101e4-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library using Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="101e4-114">在“解决方案”边栏中，按住 <kbd>Ctrl</kbd> 并单击 `ClassLibraryProjects` 解决方案，然后选择“添加” > “新建项目”。</span><span class="sxs-lookup"><span data-stu-id="101e4-114">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="101e4-115">在“新建项目”对话框中，选择“Web 和控制台”节点中的“测试”。</span><span class="sxs-lookup"><span data-stu-id="101e4-115">In the **New Project** dialog, select **Tests** from the **Web and Console** node.</span></span> <span data-ttu-id="101e4-116">依次选择“MSTest 项目”、“下一步”。</span><span class="sxs-lookup"><span data-stu-id="101e4-116">Select the **MSTest Project** followed by **Next**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="创建测试项目的 Visual Studio Mac“新建项目”对话框":::

1. <span data-ttu-id="101e4-118">选择“.NET Core 3.1”。</span><span class="sxs-lookup"><span data-stu-id="101e4-118">Select **.NET Core 3.1**.</span></span> <span data-ttu-id="101e4-119">将新项目命名为"StringLibraryTest"，然后选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="101e4-119">Name the new project "StringLibraryTest" and select **Create**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="提供项目名称的 Visual Studio Mac“新建项目”对话框":::

   <span data-ttu-id="101e4-121">Visual Studio 使用以下代码创建类文件：</span><span class="sxs-lookup"><span data-stu-id="101e4-121">Visual Studio creates a class file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="101e4-122">单元测试模板创建的源代码负责执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="101e4-122">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="101e4-123">它会导入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空间，其中包含用于单元测试的类型。</span><span class="sxs-lookup"><span data-stu-id="101e4-123">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="101e4-124">向 `UnitTest1` 类应用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="101e4-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="101e4-125">它向 `TestMethod1` 应用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="101e4-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to `TestMethod1`.</span></span>

   <span data-ttu-id="101e4-126">使用 [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) 标记的测试类中标记有 [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) 的所有测试方法都会在单元测试运行时自动执行。</span><span class="sxs-lookup"><span data-stu-id="101e4-126">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="101e4-127">添加项目引用</span><span class="sxs-lookup"><span data-stu-id="101e4-127">Add a project reference</span></span>

<span data-ttu-id="101e4-128">对于要使用 `StringLibrary` 类的测试库，请将引用添加到 `StringLibrary` 项目中。</span><span class="sxs-lookup"><span data-stu-id="101e4-128">For the test project to work with the `StringLibrary` class, add a reference to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="101e4-129">在“解决方案”边栏中，按住 <kbd>Ctrl</kbd> 并单击“StringLibraryTest”下的“依赖项”  。</span><span class="sxs-lookup"><span data-stu-id="101e4-129">In the **Solution** pad, <kbd>ctrl</kbd>-click **Dependencies** under **StringLibraryTest**.</span></span> <span data-ttu-id="101e4-130">从上下文菜单中选择“添加引用”。</span><span class="sxs-lookup"><span data-stu-id="101e4-130">Select **Add Reference** from the context menu.</span></span>

1. <span data-ttu-id="101e4-131">在“引用”对话框中，选择“StringLibrary”项目 。</span><span class="sxs-lookup"><span data-stu-id="101e4-131">In the **References** dialog, select the **StringLibrary** project.</span></span> <span data-ttu-id="101e4-132">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="101e4-132">Select **OK**.</span></span>

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Visual Studio Mac“编辑引用”对话框":::

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="101e4-134">添加并运行单元测试方法</span><span class="sxs-lookup"><span data-stu-id="101e4-134">Add and run unit test methods</span></span>

<span data-ttu-id="101e4-135">运行单元测试时，Visual Studio 执行使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 特性标记的类中标记有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 特性的所有方法。</span><span class="sxs-lookup"><span data-stu-id="101e4-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="101e4-136">当第一次遇到测试不通过或测试方法中的所有测试均已成功通过时，测试方法终止。</span><span class="sxs-lookup"><span data-stu-id="101e4-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="101e4-137">最常见的测试调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 类的成员。</span><span class="sxs-lookup"><span data-stu-id="101e4-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="101e4-138">许多断言方法至少包含两个参数，其中一个是预期的测试结果，另一个是实际的测试结果。</span><span class="sxs-lookup"><span data-stu-id="101e4-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="101e4-139">下表显示了 `Assert` 类最常调用的一些方法：</span><span class="sxs-lookup"><span data-stu-id="101e4-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="101e4-140">断言方法</span><span class="sxs-lookup"><span data-stu-id="101e4-140">Assert methods</span></span>     | <span data-ttu-id="101e4-141">函数</span><span class="sxs-lookup"><span data-stu-id="101e4-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="101e4-142">验证两个值或对象是否相等。</span><span class="sxs-lookup"><span data-stu-id="101e4-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="101e4-143">如果值或对象不相等，则断言失败。</span><span class="sxs-lookup"><span data-stu-id="101e4-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="101e4-144">验证两个对象变量引用的是否是同一个对象。</span><span class="sxs-lookup"><span data-stu-id="101e4-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="101e4-145">如果这些变量引用不同的对象，则断言失败。</span><span class="sxs-lookup"><span data-stu-id="101e4-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="101e4-146">验证条件是否为 `false`。</span><span class="sxs-lookup"><span data-stu-id="101e4-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="101e4-147">如果条件为 `true`，则断言失败。</span><span class="sxs-lookup"><span data-stu-id="101e4-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="101e4-148">验证对象是否不为 `null`。</span><span class="sxs-lookup"><span data-stu-id="101e4-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="101e4-149">如果对象为 `null`，则断言失败。</span><span class="sxs-lookup"><span data-stu-id="101e4-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="101e4-150">还可以在测试方法中使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 方法来指示它应引发的异常的类型。</span><span class="sxs-lookup"><span data-stu-id="101e4-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="101e4-151">如果未引发指定异常，则测试不通过。</span><span class="sxs-lookup"><span data-stu-id="101e4-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="101e4-152">测试 `StringLibrary.StartsWithUpper` 方法时，需要提供许多以大写字符开头的字符串。</span><span class="sxs-lookup"><span data-stu-id="101e4-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="101e4-153">在这种情况下，此方法应返回 `true`，以便可以调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="101e4-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="101e4-154">同样，需要提供许多以非大写字符开头的字符串。</span><span class="sxs-lookup"><span data-stu-id="101e4-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="101e4-155">在这种情况下，此方法应返回 `false`，以便可以调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="101e4-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="101e4-156">由于库方法处理的是字符串，因此还需要确保它能够成功处理[空字符串 (`String.Empty`)](xref:System.String.Empty)（不含字符且 <xref:System.String.Length> 为 0 的有效字符串）和 `null` 字符串（尚未初始化的字符串）。</span><span class="sxs-lookup"><span data-stu-id="101e4-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="101e4-157">可以直接将 `StartsWithUpper` 作为静态方法进行调用，并向其传递一个 <xref:System.String> 自变量。</span><span class="sxs-lookup"><span data-stu-id="101e4-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="101e4-158">或者，可以对分配给 `null` 的 `string` 变量将 `StartsWithUpper` 作为扩展方法进行调用。</span><span class="sxs-lookup"><span data-stu-id="101e4-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="101e4-159">将定义三个方法，每个方法都会对字符串数组中的各个元素调用它的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 方法。</span><span class="sxs-lookup"><span data-stu-id="101e4-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="101e4-160">你将调用方法重载，以便指定在测试失败时要显示的错误消息。</span><span class="sxs-lookup"><span data-stu-id="101e4-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="101e4-161">消息标识导致失败的字符串。</span><span class="sxs-lookup"><span data-stu-id="101e4-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="101e4-162">创建测试方法：</span><span class="sxs-lookup"><span data-stu-id="101e4-162">To create the test methods:</span></span>

1. <span data-ttu-id="101e4-163">打开 UnitTest1.cs 文件，并将代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="101e4-163">Open the *UnitTest1.cs* file and replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="101e4-164">`TestStartsWithUpper` 方法中的大写字符的测试包括希腊文大写字母 alpha (U+0391) 和西里尔文大写字母 EM (U+041C)。</span><span class="sxs-lookup"><span data-stu-id="101e4-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="101e4-165">`TestDoesNotStartWithUpper` 方法中的小写字符的测试包括希腊文小写字母 alpha (U+03B1) 和西里尔文小写字母 Ghe (U+0433)。</span><span class="sxs-lookup"><span data-stu-id="101e4-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="101e4-166">在菜单栏中，选择“文件” > “另存为” 。</span><span class="sxs-lookup"><span data-stu-id="101e4-166">On the menu bar, select **File** > **Save As**.</span></span> <span data-ttu-id="101e4-167">在对话框中，确保“编码”设置为“Unicode (UTF-8)” 。</span><span class="sxs-lookup"><span data-stu-id="101e4-167">In the dialog, make sure that **Encoding** is set to **Unicode (UTF-8)**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio“文件另存为”对话框":::

1. <span data-ttu-id="101e4-169">当系统询问你是否要替换现有文件时，请选择“替换”。</span><span class="sxs-lookup"><span data-stu-id="101e4-169">When you're asked if you want to replace the existing file, select **Replace**.</span></span>

   <span data-ttu-id="101e4-170">如果无法将源代码保存为 UTF8 编码文件，Visual Studio 可能会将其另存为 ASCII 文件。</span><span class="sxs-lookup"><span data-stu-id="101e4-170">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="101e4-171">在这种情况下，运行时将无法准确解码 ASCII 范围以外的 UTF8 字符，且测试结果也会不正确。</span><span class="sxs-lookup"><span data-stu-id="101e4-171">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="101e4-172">打开屏幕右侧的“单元测试”面板。</span><span class="sxs-lookup"><span data-stu-id="101e4-172">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="101e4-173">从菜单中选择“查看” > “测试”。</span><span class="sxs-lookup"><span data-stu-id="101e4-173">Select **View** > **Tests** from the menu.</span></span>

1. <span data-ttu-id="101e4-174">单击“停靠”图标使此面板保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="101e4-174">Click the **Dock** icon to keep the panel open.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Visual Studio for Mac“单元测试”面板停靠图标":::

1. <span data-ttu-id="101e4-176">单击“全部运行”按钮。</span><span class="sxs-lookup"><span data-stu-id="101e4-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="101e4-177">所有测试通过。</span><span class="sxs-lookup"><span data-stu-id="101e4-177">All tests pass.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio for Mac 预期测试通过":::

## <a name="handle-test-failures"></a><span data-ttu-id="101e4-179">处理测试失败</span><span class="sxs-lookup"><span data-stu-id="101e4-179">Handle test failures</span></span>

<span data-ttu-id="101e4-180">如果进行的是测试驱动开发 (TDD)，请先编写测试，然后测试会在第一次运行时失败。</span><span class="sxs-lookup"><span data-stu-id="101e4-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="101e4-181">接着将可以使测试成功的代码添加到应用。</span><span class="sxs-lookup"><span data-stu-id="101e4-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="101e4-182">在本教程中，先编写了测试要验证的应用代码然后才创建测试，所以没有看到测试失败。</span><span class="sxs-lookup"><span data-stu-id="101e4-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="101e4-183">若要验证测试是否在预期失败时失败，请在测试输入中添加无效值。</span><span class="sxs-lookup"><span data-stu-id="101e4-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="101e4-184">通过修改 `TestDoesNotStartWithUpper` 方法中的 `words` 数组来包含字符串“Error”。</span><span class="sxs-lookup"><span data-stu-id="101e4-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="101e4-185">由于 Visual Studio 将在生成运行测试的解决方案时自动保存打开的文件，因此无需手动保存。</span><span class="sxs-lookup"><span data-stu-id="101e4-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="101e4-186">重新运行测试。</span><span class="sxs-lookup"><span data-stu-id="101e4-186">Run the tests again.</span></span>

   <span data-ttu-id="101e4-187">这一次，“测试资源管理器”窗口指示有两个测试成功，还有一个失败。</span><span class="sxs-lookup"><span data-stu-id="101e4-187">This time, the **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="未通过测试的“测试资源管理器”窗口":::

1. <span data-ttu-id="101e4-189">按 <kbd>Ctrl</kbd> 并单击失败的测试 `TestDoesNotStartWithUpper`，然后从上下文菜单中选择“显示结果边栏”。</span><span class="sxs-lookup"><span data-stu-id="101e4-189"><kbd>ctrl</kbd>-click the failed test, `TestDoesNotStartWithUpper`, and select **Show Results Pad** from the context menu.</span></span>

   <span data-ttu-id="101e4-190">“结果”边栏显示断言生成的消息：“Assert.IsFalse 失败。</span><span class="sxs-lookup"><span data-stu-id="101e4-190">The **Results** pad displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="101e4-191">“Error”应返回 false；实际返回 True”。</span><span class="sxs-lookup"><span data-stu-id="101e4-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="101e4-192">由于此次失败，数组中“Error”之后的所有字符串都未进行测试。</span><span class="sxs-lookup"><span data-stu-id="101e4-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="显示 IsFalse 断言失败的“测试资源管理器”窗口":::

1. <span data-ttu-id="101e4-194">删除在步骤 1 中添加的字符串“Error”。</span><span class="sxs-lookup"><span data-stu-id="101e4-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="101e4-195">重新运行测试，测试将通过。</span><span class="sxs-lookup"><span data-stu-id="101e4-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="101e4-196">测试库的发行版本</span><span class="sxs-lookup"><span data-stu-id="101e4-196">Test the Release version of the library</span></span>

<span data-ttu-id="101e4-197">至此，在运行库的调试版本时，测试已全部通过，接下来应对库的发行版本再运行一次这些测试。</span><span class="sxs-lookup"><span data-stu-id="101e4-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="101e4-198">许多因素（包括编译器优化）有时可能会导致调试版本和发行版本出现行为差异。</span><span class="sxs-lookup"><span data-stu-id="101e4-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="101e4-199">若要测试发行版本，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="101e4-199">To test the Release build:</span></span>

1. <span data-ttu-id="101e4-200">在 Visual Studio 工具栏中，将生成配置从 **“调试”** 更改为 **“发行”** 。</span><span class="sxs-lookup"><span data-stu-id="101e4-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="突出显示发布版本的 Visual Studio 工具栏":::

1. <span data-ttu-id="101e4-202">在“解决方案”边栏中，按 <kbd>Ctrl</kbd> 并单击“StringLibrary”项目，然后从上下文菜单中选择“生成”，重新编译库。</span><span class="sxs-lookup"><span data-stu-id="101e4-202">In the **Solution** pad, <kbd>ctrl</kbd>-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="带有生成命令的 StringLibrary 上下文菜单":::

1. <span data-ttu-id="101e4-204">再次运行单元测试。</span><span class="sxs-lookup"><span data-stu-id="101e4-204">Run the unit tests again.</span></span>

   <span data-ttu-id="101e4-205">测试通过。</span><span class="sxs-lookup"><span data-stu-id="101e4-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="101e4-206">调试测试</span><span class="sxs-lookup"><span data-stu-id="101e4-206">Debug tests</span></span>

<span data-ttu-id="101e4-207">可以使用[教程：使用 Visual Studio for Mac 调试 .NET Core 控制台应用程序](debugging-with-visual-studio-mac.md)中所示的相同过程，使用单元测试项目调试代码。</span><span class="sxs-lookup"><span data-stu-id="101e4-207">You can use the same process shown in [Tutorial: Debug a .NET Core console application using Visual Studio for Mac](debugging-with-visual-studio-mac.md) to debug code using your unit test project.</span></span> <span data-ttu-id="101e4-208">按住 <kbd>Ctrl</kbd> 并单击“StringLibraryTests”项目，然后从上下文菜单中选择“启动调试项目”，而不是启动 ShowCase 应用项目。</span><span class="sxs-lookup"><span data-stu-id="101e4-208">Instead of starting the ShowCase app project, <kbd>ctrl</kbd>-click the **StringLibraryTests** project, and select **Start Debugging Project** from the context menu.</span></span> <span data-ttu-id="101e4-209">Visual Studio 启动附有调试器的测试项目。</span><span class="sxs-lookup"><span data-stu-id="101e4-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="101e4-210">执行将在添加到测试项目的任何断点或基础库代码处停止。</span><span class="sxs-lookup"><span data-stu-id="101e4-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="101e4-211">其他资源</span><span class="sxs-lookup"><span data-stu-id="101e4-211">Additional resources</span></span>

* [<span data-ttu-id="101e4-212">.NET Core 和 .NET Standard 中的单元测试</span><span class="sxs-lookup"><span data-stu-id="101e4-212">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="101e4-213">后续步骤</span><span class="sxs-lookup"><span data-stu-id="101e4-213">Next steps</span></span>

<span data-ttu-id="101e4-214">在本教程中，你对类库进行了单元测试。</span><span class="sxs-lookup"><span data-stu-id="101e4-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="101e4-215">你可以将库作为包发布到 [NuGet](https://nuget.org)，使其可供其他人使用。</span><span class="sxs-lookup"><span data-stu-id="101e4-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="101e4-216">若要了解如何操作，请遵循 NuGet 教程：</span><span class="sxs-lookup"><span data-stu-id="101e4-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="101e4-217">创建并发布包 (dotnet CLI)</span><span class="sxs-lookup"><span data-stu-id="101e4-217">Create and publish a package (dotnet CLI)</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="101e4-218">如果将库作为 NuGet 包发布，其他人可以安装并使用它。</span><span class="sxs-lookup"><span data-stu-id="101e4-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="101e4-219">若要了解如何操作，请遵循 NuGet 教程：</span><span class="sxs-lookup"><span data-stu-id="101e4-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="101e4-220">在 Visual Studio for Mac 中安装和使用包</span><span class="sxs-lookup"><span data-stu-id="101e4-220">Install and use a package in Visual Studio for Mac</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

<span data-ttu-id="101e4-221">库并非必须作为包进行分发。</span><span class="sxs-lookup"><span data-stu-id="101e4-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="101e4-222">它还可与使用它的控制台应用捆绑在一起。</span><span class="sxs-lookup"><span data-stu-id="101e4-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="101e4-223">若要了解如何发布控制台应用，请参阅本系列中前面的教程：</span><span class="sxs-lookup"><span data-stu-id="101e4-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="101e4-224">使用 Visual Studio for Mac 发布 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="101e4-224">Publish a .NET Core console application using Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
