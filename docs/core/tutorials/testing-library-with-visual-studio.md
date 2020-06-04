---
title: 在 Visual Studio 中使用 .NET Core 测试 .NET Standard 类库
description: 为 .NET Core 类库创建单元测试项目。 验证 .NET Core 类库能否正确地进行单元测试。
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 79b680022484bb9222b66c3df76bdd5a06de8117
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005006"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="67c79-104">教程：在 Visual Studio 中使用 .NET Core 测试 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="67c79-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="67c79-105">本教程演示如何通过将测试项目添加到解决方案来自动执行单元测试。</span><span class="sxs-lookup"><span data-stu-id="67c79-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="67c79-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="67c79-106">Prerequisites</span></span>

- <span data-ttu-id="67c79-107">本教程适用于[在 Visual Studio 中创建 .NET Standard 库](library-with-visual-studio.md)中创建的解决方案。</span><span class="sxs-lookup"><span data-stu-id="67c79-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="67c79-108">创建单元测试项目</span><span class="sxs-lookup"><span data-stu-id="67c79-108">Create a unit test project</span></span>

1. <span data-ttu-id="67c79-109">打开[在 Visual Studio 中创建 .NET Standard 库](library-with-visual-studio.md)中创建的 `ClassLibraryProjects` 解决方案。</span><span class="sxs-lookup"><span data-stu-id="67c79-109">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="67c79-110">将名为“StringLibraryTest”的新单元测试项目添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="67c79-110">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="67c79-111">在“解决方案资源管理器”中右键单击解决方案并选择“添加” > “新建项目”。</span><span class="sxs-lookup"><span data-stu-id="67c79-111">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="67c79-112">在“添加新项目”页面，在搜索框中输入“mstest”。</span><span class="sxs-lookup"><span data-stu-id="67c79-112">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="67c79-113">从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”。</span><span class="sxs-lookup"><span data-stu-id="67c79-113">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="67c79-114">选择“MSTest 测试项目(.NET Core)”模板，然后选择“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="67c79-114">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="67c79-115">在“配置新项目”页面，在“项目名称”框中输入“StringLibraryTest”。</span><span class="sxs-lookup"><span data-stu-id="67c79-115">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="67c79-116">然后选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="67c79-116">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="67c79-117">MSTest 是可供选择的三个测试框架之一。</span><span class="sxs-lookup"><span data-stu-id="67c79-117">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="67c79-118">其他两个是 xUnit 和 nUnit。</span><span class="sxs-lookup"><span data-stu-id="67c79-118">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="67c79-119">此时，Visual Studio 会创建项目，并在具有以下代码的代码窗口中打开类文件。</span><span class="sxs-lookup"><span data-stu-id="67c79-119">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="67c79-120">如果未显示想要使用的语言，请更改页面顶部的语言选择器。</span><span class="sxs-lookup"><span data-stu-id="67c79-120">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   <span data-ttu-id="67c79-121">单元测试模板创建的源代码负责执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="67c79-121">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="67c79-122">它会导入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空间，其中包含用于单元测试的类型。</span><span class="sxs-lookup"><span data-stu-id="67c79-122">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="67c79-123">向 `UnitTest1` 类应用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 特性。</span><span class="sxs-lookup"><span data-stu-id="67c79-123">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="67c79-124">它应用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 特性来定义 C# 中的 `TestMethod1` 或 Visual Basic 中的 `TestSub`。</span><span class="sxs-lookup"><span data-stu-id="67c79-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="67c79-125">使用 [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) 标记的测试类中标记有 [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) 的所有测试方法都会在单元测试运行时自动执行。</span><span class="sxs-lookup"><span data-stu-id="67c79-125">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="67c79-126">在“解决方案资源管理器”中，右键单击“StringLibraryTest”项目的“依赖项”节点，并从上下文菜单中选择“添加项目引用”   。</span><span class="sxs-lookup"><span data-stu-id="67c79-126">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="67c79-127">在“引用管理器”对话框中，展开“项目”节点，并选择“StringLibrary”旁边的框  。</span><span class="sxs-lookup"><span data-stu-id="67c79-127">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="67c79-128">添加对 `StringLibrary` 程序集的引用后，编译器可以在编译 StringLibraryTest 项目时查找 StringLibrary 方法 。</span><span class="sxs-lookup"><span data-stu-id="67c79-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="67c79-129">选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="67c79-129">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="67c79-130">添加并运行单元测试方法</span><span class="sxs-lookup"><span data-stu-id="67c79-130">Add and run unit test methods</span></span>

<span data-ttu-id="67c79-131">运行单元测试时，Visual Studio 执行使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 特性标记的类中标记有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 特性的所有方法。</span><span class="sxs-lookup"><span data-stu-id="67c79-131">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="67c79-132">当第一次遇到测试不通过或测试方法中的所有测试均已成功通过时，测试方法终止。</span><span class="sxs-lookup"><span data-stu-id="67c79-132">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="67c79-133">最常见的测试调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 类的成员。</span><span class="sxs-lookup"><span data-stu-id="67c79-133">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="67c79-134">许多断言方法至少包含两个参数，其中一个是预期的测试结果，另一个是实际的测试结果。</span><span class="sxs-lookup"><span data-stu-id="67c79-134">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="67c79-135">下表显示了 `Assert` 类最常调用的一些方法：</span><span class="sxs-lookup"><span data-stu-id="67c79-135">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="67c79-136">断言方法</span><span class="sxs-lookup"><span data-stu-id="67c79-136">Assert methods</span></span>     | <span data-ttu-id="67c79-137">函数</span><span class="sxs-lookup"><span data-stu-id="67c79-137">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="67c79-138">验证两个值或对象是否相等。</span><span class="sxs-lookup"><span data-stu-id="67c79-138">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="67c79-139">如果值或对象不相等，则断言失败。</span><span class="sxs-lookup"><span data-stu-id="67c79-139">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="67c79-140">验证两个对象变量引用的是否是同一个对象。</span><span class="sxs-lookup"><span data-stu-id="67c79-140">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="67c79-141">如果这些变量引用不同的对象，则断言失败。</span><span class="sxs-lookup"><span data-stu-id="67c79-141">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="67c79-142">验证条件是否为 `false`。</span><span class="sxs-lookup"><span data-stu-id="67c79-142">Verifies that a condition is `false`.</span></span> <span data-ttu-id="67c79-143">如果条件为 `true`，则断言失败。</span><span class="sxs-lookup"><span data-stu-id="67c79-143">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="67c79-144">验证对象是否不为 `null`。</span><span class="sxs-lookup"><span data-stu-id="67c79-144">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="67c79-145">如果对象为 `null`，则断言失败。</span><span class="sxs-lookup"><span data-stu-id="67c79-145">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="67c79-146">还可以在测试方法中使用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 方法来指示它应引发的异常的类型。</span><span class="sxs-lookup"><span data-stu-id="67c79-146">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="67c79-147">如果未引发指定异常，则测试不通过。</span><span class="sxs-lookup"><span data-stu-id="67c79-147">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="67c79-148">测试 `StringLibrary.StartsWithUpper` 方法时，需要提供许多以大写字符开头的字符串。</span><span class="sxs-lookup"><span data-stu-id="67c79-148">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="67c79-149">在这种情况下，此方法应返回 `true`，以便可以调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="67c79-149">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="67c79-150">同样，需要提供许多以非大写字符开头的字符串。</span><span class="sxs-lookup"><span data-stu-id="67c79-150">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="67c79-151">在这种情况下，此方法应返回 `false`，以便可以调用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="67c79-151">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="67c79-152">由于库方法处理的是字符串，因此还需要确保它能够成功处理[空字符串 (`String.Empty`)](xref:System.String.Empty)（不含字符且 <xref:System.String.Length> 为 0 的有效字符串）和 `null` 字符串（尚未初始化的字符串）。</span><span class="sxs-lookup"><span data-stu-id="67c79-152">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="67c79-153">如果对 <xref:System.String> 实例调用 `StartsWithUpper` 作为扩展方法，无法向其传递 `null` 字符串。</span><span class="sxs-lookup"><span data-stu-id="67c79-153">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="67c79-154">不过，还可以直接将其作为静态方法进行调用，并向其传递一个 <xref:System.String> 自变量。</span><span class="sxs-lookup"><span data-stu-id="67c79-154">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="67c79-155">将定义三个方法，每个方法都会对字符串数组中的各个元素反复调用它的 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 方法。</span><span class="sxs-lookup"><span data-stu-id="67c79-155">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="67c79-156">由于测试方法在第一次遇到测试不通过时会立即失败，因此将调用方法重载，以便传递字符串来指明方法调用中使用的字符串值。</span><span class="sxs-lookup"><span data-stu-id="67c79-156">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="67c79-157">创建测试方法：</span><span class="sxs-lookup"><span data-stu-id="67c79-157">To create the test methods:</span></span>

1. <span data-ttu-id="67c79-158">将 UnitTest1.cs 或 UnitTest1.vb 代码窗口中的代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="67c79-158">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="67c79-159">`TestStartsWithUpper` 方法中的大写字符的测试包括希腊文大写字母 alpha (U+0391) 和西里尔文大写字母 EM (U+041C)。</span><span class="sxs-lookup"><span data-stu-id="67c79-159">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="67c79-160">`TestDoesNotStartWithUpper` 方法中的小写字符的测试包括希腊文小写字母 alpha (U+03B1) 和西里尔文小写字母 Ghe (U+0433)。</span><span class="sxs-lookup"><span data-stu-id="67c79-160">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="67c79-161">在菜单栏上，选择“文件” > “将 UnitTest1.cs 另存为”或“文件” > “将 UnitTest1.vb 另存为”。</span><span class="sxs-lookup"><span data-stu-id="67c79-161">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="67c79-162">在“文件另存为”对话框中，选择“保存”按钮旁边的箭头，然后选择“保存时使用编码”。</span><span class="sxs-lookup"><span data-stu-id="67c79-162">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="67c79-163">![Visual Studio“文件另存为”对话框](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="67c79-163">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="67c79-164">在“确认另存为”对话框中，选择“是”按钮，保存文件。</span><span class="sxs-lookup"><span data-stu-id="67c79-164">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="67c79-165">在“高级保存选项”对话框的“编码”下拉列表中，选择“Unicode (UTF-8 带签名) - 代码页 65001”，然后选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="67c79-165">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="67c79-166">![Visual Studio“高级保存选项”对话框](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="67c79-166">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="67c79-167">如果无法将源代码保存为 UTF8 编码文件，Visual Studio 可能会将其另存为 ASCII 文件。</span><span class="sxs-lookup"><span data-stu-id="67c79-167">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="67c79-168">在这种情况下，运行时将无法准确解码 ASCII 范围以外的 UTF8 字符，且测试结果也会不正确。</span><span class="sxs-lookup"><span data-stu-id="67c79-168">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="67c79-169">在菜单栏上，选择“测试” > “运行所有测试” 。</span><span class="sxs-lookup"><span data-stu-id="67c79-169">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="67c79-170">如果“测试资源管理器”窗口未打开，请选择“测试” > “测试资源管理器”来将其打开  。</span><span class="sxs-lookup"><span data-stu-id="67c79-170">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="67c79-171">“通过的测试”部分列出了三个测试，“摘要”部分报告了测试运行结果。</span><span class="sxs-lookup"><span data-stu-id="67c79-171">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="67c79-172">![通过测试的“测试资源管理器”窗口](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="67c79-172">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="67c79-173">处理测试失败</span><span class="sxs-lookup"><span data-stu-id="67c79-173">Handle test failures</span></span>

<span data-ttu-id="67c79-174">由于运行的测试均通过，因此需进行少量改动，以使其中一个测试方法失败：</span><span class="sxs-lookup"><span data-stu-id="67c79-174">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="67c79-175">通过修改 `TestDoesNotStartWithUpper` 方法中的 `words` 数组来包含字符串“Error”。</span><span class="sxs-lookup"><span data-stu-id="67c79-175">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="67c79-176">由于 Visual Studio 将在生成运行测试的解决方案时自动保存打开的文件，因此无需手动保存。</span><span class="sxs-lookup"><span data-stu-id="67c79-176">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="67c79-177">从菜单栏中选择“测试” > “运行所有测试”，运行测试 。</span><span class="sxs-lookup"><span data-stu-id="67c79-177">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="67c79-178">“测试资源管理器”窗口指示有两个测试成功，还有一个失败。</span><span class="sxs-lookup"><span data-stu-id="67c79-178">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="67c79-179">![未通过测试的“测试资源管理器”窗口](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="67c79-179">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="67c79-180">选择失败的测试，`TestDoesNotStartWith`。</span><span class="sxs-lookup"><span data-stu-id="67c79-180">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="67c79-181">“测试资源管理器”窗口显示断言生成的消息：“Assert.IsFalse 失败。</span><span class="sxs-lookup"><span data-stu-id="67c79-181">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="67c79-182">“Error”应返回 false；实际返回 True”。</span><span class="sxs-lookup"><span data-stu-id="67c79-182">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="67c79-183">由于此次失败，数组中“Error”之后的所有字符串都未进行测试。</span><span class="sxs-lookup"><span data-stu-id="67c79-183">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="67c79-184">![显示 IsFalse 断言失败的“测试资源管理器”窗口](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="67c79-184">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="67c79-185">撤消在步骤 1 中执行的修改并删除字符串“Error”。</span><span class="sxs-lookup"><span data-stu-id="67c79-185">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="67c79-186">重新运行测试，测试将通过。</span><span class="sxs-lookup"><span data-stu-id="67c79-186">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="67c79-187">测试库的发行版本</span><span class="sxs-lookup"><span data-stu-id="67c79-187">Test the Release version of the library</span></span>

<span data-ttu-id="67c79-188">至此，在运行库的调试版本时，测试已全部通过，接下来应对库的发行版本再运行一次这些测试。</span><span class="sxs-lookup"><span data-stu-id="67c79-188">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="67c79-189">许多因素（包括编译器优化）有时可能会导致调试版本和发行版本出现行为差异。</span><span class="sxs-lookup"><span data-stu-id="67c79-189">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="67c79-190">若要测试发行版本，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="67c79-190">To test the Release build:</span></span>

1. <span data-ttu-id="67c79-191">在 Visual Studio 工具栏中，将生成配置从 **“调试”** 更改为 **“发行”** 。</span><span class="sxs-lookup"><span data-stu-id="67c79-191">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="67c79-192">![突出显示发布版本的 Visual Studio 工具栏](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="67c79-192">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="67c79-193">在“解决方案资源管理器”中，右键单击“StringLibrary”项目，从上下文菜单中选择“生成”，重新编译库。</span><span class="sxs-lookup"><span data-stu-id="67c79-193">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="67c79-194">![带有生成命令的 StringLibrary 上下文菜单](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="67c79-194">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="67c79-195">从菜单栏中选择“测试运行” > “所有测试”，运行单元测试 。</span><span class="sxs-lookup"><span data-stu-id="67c79-195">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="67c79-196">测试通过。</span><span class="sxs-lookup"><span data-stu-id="67c79-196">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="67c79-197">其他资源</span><span class="sxs-lookup"><span data-stu-id="67c79-197">Additional resources</span></span>

- [<span data-ttu-id="67c79-198">单元测试基础知识 - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="67c79-198">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)

## <a name="next-steps"></a><span data-ttu-id="67c79-199">后续步骤</span><span class="sxs-lookup"><span data-stu-id="67c79-199">Next steps</span></span>

<span data-ttu-id="67c79-200">在本教程中，你对类库进行了单元测试。</span><span class="sxs-lookup"><span data-stu-id="67c79-200">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="67c79-201">你可以将库作为包发布到 [NuGet](https://nuget.org)，使其可供其他人使用。</span><span class="sxs-lookup"><span data-stu-id="67c79-201">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="67c79-202">若要了解如何操作，请遵循 NuGet 教程：</span><span class="sxs-lookup"><span data-stu-id="67c79-202">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="67c79-203">使用 Visual Studio 创建和发布 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="67c79-203">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="67c79-204">如果将库作为 NuGet 包发布，其他人可以安装并使用它。</span><span class="sxs-lookup"><span data-stu-id="67c79-204">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="67c79-205">若要了解如何操作，请遵循 NuGet 教程：</span><span class="sxs-lookup"><span data-stu-id="67c79-205">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="67c79-206">在 Visual Studio 中安装和使用包</span><span class="sxs-lookup"><span data-stu-id="67c79-206">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="67c79-207">库并非必须作为包进行分发。</span><span class="sxs-lookup"><span data-stu-id="67c79-207">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="67c79-208">它还可与使用它的控制台应用捆绑在一起。</span><span class="sxs-lookup"><span data-stu-id="67c79-208">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="67c79-209">若要了解如何发布控制台应用，请参阅本系列中前面的教程：</span><span class="sxs-lookup"><span data-stu-id="67c79-209">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="67c79-210">使用 Visual Studio 发布 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="67c79-210">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
