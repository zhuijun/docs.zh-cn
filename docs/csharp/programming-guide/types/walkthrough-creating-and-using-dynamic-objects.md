---
title: 演练：创建并使用动态对象（C# 和 Visual Basic）
description: 在本演练中，了解如何创建和使用动态对象。 创建自定义动态对象和使用“IronPython”库的项目。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
ms.openlocfilehash: 144651d3b14f6f6093ab07f1df7be10e6d05ae89
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381250"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a><span data-ttu-id="b952b-104">演练：创建并使用动态对象（C# 和 Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b952b-104">Walkthrough: Creating and Using Dynamic Objects (C# and Visual Basic)</span></span>

<span data-ttu-id="b952b-105">动态对象会在运行时（而非编译时）公开属性和方法等成员。</span><span class="sxs-lookup"><span data-stu-id="b952b-105">Dynamic objects expose members such as properties and methods at run time, instead of at compile time.</span></span> <span data-ttu-id="b952b-106">这使你能够创建对象以处理与静态类型或格式不匹配的结构。</span><span class="sxs-lookup"><span data-stu-id="b952b-106">This enables you to create objects to work with structures that do not match a static type or format.</span></span> <span data-ttu-id="b952b-107">例如，可以使用动态对象来引用 HTML 文档对象模型 (DOM)，该模型包含有效 HTML 标记元素和特性的任意组合。</span><span class="sxs-lookup"><span data-stu-id="b952b-107">For example, you can use a dynamic object to reference the HTML Document Object Model (DOM), which can contain any combination of valid HTML markup elements and attributes.</span></span> <span data-ttu-id="b952b-108">由于每个 HTML 文档都是唯一的，因此在运行时将确定特定 HTML 文档的成员。</span><span class="sxs-lookup"><span data-stu-id="b952b-108">Because each HTML document is unique, the members for a particular HTML document are determined at run time.</span></span> <span data-ttu-id="b952b-109">引用 HTML 元素的特性的常用方法是，将该特性的名称传递给该元素的 `GetProperty` 方法。</span><span class="sxs-lookup"><span data-stu-id="b952b-109">A common method to reference an attribute of an HTML element is to pass the name of the attribute to the `GetProperty` method of the element.</span></span> <span data-ttu-id="b952b-110">若要引用 HTML 元素 `<div id="Div1">` 的 `id` 特性，首先获取对 `<div>` 元素的引用，然后使用 `divElement.GetProperty("id")`。</span><span class="sxs-lookup"><span data-stu-id="b952b-110">To reference the `id` attribute of the HTML element `<div id="Div1">`, you first obtain a reference to the `<div>` element, and then use `divElement.GetProperty("id")`.</span></span> <span data-ttu-id="b952b-111">如果使用动态对象，则可以将 `id` 特性引用为 `divElement.id`。</span><span class="sxs-lookup"><span data-stu-id="b952b-111">If you use a dynamic object, you can reference the `id` attribute as `divElement.id`.</span></span>  
  
 <span data-ttu-id="b952b-112">动态对象还提供对 IronPython 和 IronRuby 等动态语言的便捷访问。</span><span class="sxs-lookup"><span data-stu-id="b952b-112">Dynamic objects also provide convenient access to dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="b952b-113">可以使用动态对象来引用在运行时解释的动态脚本。</span><span class="sxs-lookup"><span data-stu-id="b952b-113">You can use a dynamic object to refer to a dynamic script that is interpreted at run time.</span></span>  
  
 <span data-ttu-id="b952b-114">使用晚期绑定引用动态对象。</span><span class="sxs-lookup"><span data-stu-id="b952b-114">You reference a dynamic object by using late binding.</span></span> <span data-ttu-id="b952b-115">在 C# 中，将晚期绑定对象的类型指定为 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="b952b-115">In C#, you specify the type of a late-bound object as `dynamic`.</span></span> <span data-ttu-id="b952b-116">在 Visual Basic 中，将晚期绑定对象的类型指定为 `Object`。</span><span class="sxs-lookup"><span data-stu-id="b952b-116">In Visual Basic, you specify the type of a late-bound object as `Object`.</span></span> <span data-ttu-id="b952b-117">有关详细信息，请参阅[动态](../../language-reference/builtin-types/reference-types.md)和[早期绑定和晚期绑定](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b952b-117">For more information, see [dynamic](../../language-reference/builtin-types/reference-types.md) and [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span></span>  
  
 <span data-ttu-id="b952b-118">可以使用 <xref:System.Dynamic?displayProperty=nameWithType> 命名空间中的类来创建自定义动态对象。</span><span class="sxs-lookup"><span data-stu-id="b952b-118">You can create custom dynamic objects by using the classes in the <xref:System.Dynamic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b952b-119">例如，可以创建 <xref:System.Dynamic.ExpandoObject> 并在运行时指定该对象的成员。</span><span class="sxs-lookup"><span data-stu-id="b952b-119">For example, you can create an <xref:System.Dynamic.ExpandoObject> and specify the members of that object at run time.</span></span> <span data-ttu-id="b952b-120">还可以创建继承 <xref:System.Dynamic.DynamicObject> 类的自己的类型。</span><span class="sxs-lookup"><span data-stu-id="b952b-120">You can also create your own type that inherits the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="b952b-121">然后，可以替代 <xref:System.Dynamic.DynamicObject> 类的成员以提供运行时动态功能。</span><span class="sxs-lookup"><span data-stu-id="b952b-121">You can then override the members of the <xref:System.Dynamic.DynamicObject> class to provide run-time dynamic functionality.</span></span>  
  
 <span data-ttu-id="b952b-122">在本演练中，将要执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="b952b-122">In this walkthrough you will perform the following tasks:</span></span>  
  
- <span data-ttu-id="b952b-123">创建一个自定义对象，该对象会将文本文件的内容作为对象的属性动态公开。</span><span class="sxs-lookup"><span data-stu-id="b952b-123">Create a custom object that dynamically exposes the contents of a text file as properties of an object.</span></span>  
  
- <span data-ttu-id="b952b-124">创建使用 `IronPython` 库的项目。</span><span class="sxs-lookup"><span data-stu-id="b952b-124">Create a project that uses an `IronPython` library.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b952b-125">先决条件</span><span class="sxs-lookup"><span data-stu-id="b952b-125">Prerequisites</span></span>  

<span data-ttu-id="b952b-126">需要 [IronPython](https://ironpython.net/) for .NET 才能完成此演练。</span><span class="sxs-lookup"><span data-stu-id="b952b-126">You need [IronPython](https://ironpython.net/) for .NET to complete this walkthrough.</span></span> <span data-ttu-id="b952b-127">转到其[下载页](https://ironpython.net/download/)以获取最新版本。</span><span class="sxs-lookup"><span data-stu-id="b952b-127">Go to their [Download page](https://ironpython.net/download/) to obtain the latest version.</span></span>
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a><span data-ttu-id="b952b-128">创建自定义动态对象</span><span class="sxs-lookup"><span data-stu-id="b952b-128">Creating a Custom Dynamic Object</span></span>

<span data-ttu-id="b952b-129">在本演练中创建的第一个项目将定义一个搜索文本文件内容的自定义动态对象。</span><span class="sxs-lookup"><span data-stu-id="b952b-129">The first project that you create in this walkthrough defines a custom dynamic object that searches the contents of a text file.</span></span> <span data-ttu-id="b952b-130">要搜索的文本由动态属性的名称指定。</span><span class="sxs-lookup"><span data-stu-id="b952b-130">Text to search for is specified by the name of a dynamic property.</span></span> <span data-ttu-id="b952b-131">例如，如果调用代码指定 `dynamicFile.Sample`，则动态类将返回一个字符串泛型列表，其中包含该文件中以“Sample”开头的所有行。</span><span class="sxs-lookup"><span data-stu-id="b952b-131">For example, if calling code specifies `dynamicFile.Sample`, the dynamic class returns a generic list of strings that contains all of the lines from the file that begin with "Sample".</span></span> <span data-ttu-id="b952b-132">搜索不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b952b-132">The search is case-insensitive.</span></span> <span data-ttu-id="b952b-133">动态类还支持两个可选参数。</span><span class="sxs-lookup"><span data-stu-id="b952b-133">The dynamic class also supports two optional arguments.</span></span> <span data-ttu-id="b952b-134">第一个参数是一个搜索选项枚举值，它指定动态类应在行的开头、行的结尾或行中任意位置搜索匹配项。</span><span class="sxs-lookup"><span data-stu-id="b952b-134">The first argument is a search option enum value that specifies that the dynamic class should search for matches at the start of the line, the end of the line, or anywhere in the line.</span></span> <span data-ttu-id="b952b-135">第二个参数指定动态类应在搜索之前去除每行中的前导空格和尾部空格。</span><span class="sxs-lookup"><span data-stu-id="b952b-135">The second argument specifies that the dynamic class should trim leading and trailing spaces from each line before searching.</span></span> <span data-ttu-id="b952b-136">例如，如果调用代码指定 `dynamicFile.Sample(StringSearchOption.Contains)`，则动态类将在行中的任意位置搜索“Sample”。</span><span class="sxs-lookup"><span data-stu-id="b952b-136">For example, if calling code specifies `dynamicFile.Sample(StringSearchOption.Contains)`, the dynamic class searches for "Sample" anywhere in a line.</span></span> <span data-ttu-id="b952b-137">如果调用代码指定 `dynamicFile.Sample(StringSearchOption.StartsWith, false)`，则动态类将在每行的开头搜索“Sample”，但不会删除前导空格和尾部空格。</span><span class="sxs-lookup"><span data-stu-id="b952b-137">If calling code specifies `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, the dynamic class searches for "Sample" at the start of each line, and does not remove leading and trailing spaces.</span></span> <span data-ttu-id="b952b-138">动态类的默认行为是在每行的开头搜索匹配项，并删除前导空格和尾部空格。</span><span class="sxs-lookup"><span data-stu-id="b952b-138">The default behavior of the dynamic class is to search for a match at the start of each line and to remove leading and trailing spaces.</span></span>  
  
### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="b952b-139">创建自定义动态类</span><span class="sxs-lookup"><span data-stu-id="b952b-139">To create a custom dynamic class</span></span>  
  
1. <span data-ttu-id="b952b-140">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="b952b-140">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="b952b-141">在 **“文件”** 菜单上指向 **“新建”** ，然后单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="b952b-141">On the **File** menu, point to **New** and then click **Project**.</span></span>  
  
3. <span data-ttu-id="b952b-142">在“新建项目”对话框的“项目类型”窗格中，确保选中“Windows”。</span><span class="sxs-lookup"><span data-stu-id="b952b-142">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="b952b-143">在“模板”窗格中，选择“控制台应用程序”。</span><span class="sxs-lookup"><span data-stu-id="b952b-143">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="b952b-144">在“名称”框中，键入 `DynamicSample`，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="b952b-144">In the **Name** box, type `DynamicSample`, and then click **OK**.</span></span> <span data-ttu-id="b952b-145">新项目创建完成。</span><span class="sxs-lookup"><span data-stu-id="b952b-145">The new project is created.</span></span>  
  
4. <span data-ttu-id="b952b-146">右键单击 DynamicSample 项目，指向“添加”，然后单击“类”。</span><span class="sxs-lookup"><span data-stu-id="b952b-146">Right-click the DynamicSample project and point to **Add**, and then click **Class**.</span></span> <span data-ttu-id="b952b-147">在“名称”框中，键入 `ReadOnlyFile`，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="b952b-147">In the **Name** box, type `ReadOnlyFile`, and then click **OK**.</span></span> <span data-ttu-id="b952b-148">这将添加一个包含 ReadOnlyFile 类的新文件。</span><span class="sxs-lookup"><span data-stu-id="b952b-148">A new file is added that contains the ReadOnlyFile class.</span></span>  
  
5. <span data-ttu-id="b952b-149">在 ReadOnlyFile.cs 或 ReadOnlyFile.vb 文件的顶部，添加以下代码以导入 <xref:System.IO?displayProperty=nameWithType> 和 <xref:System.Dynamic?displayProperty=nameWithType> 命名空间。</span><span class="sxs-lookup"><span data-stu-id="b952b-149">At the top of the ReadOnlyFile.cs or ReadOnlyFile.vb file, add the following code to import the <xref:System.IO?displayProperty=nameWithType> and <xref:System.Dynamic?displayProperty=nameWithType> namespaces.</span></span>  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6. <span data-ttu-id="b952b-150">自定义动态对象使用一个枚举来确定搜索条件。</span><span class="sxs-lookup"><span data-stu-id="b952b-150">The custom dynamic object uses an enum to determine the search criteria.</span></span> <span data-ttu-id="b952b-151">在类语句的前面，添加以下枚举定义。</span><span class="sxs-lookup"><span data-stu-id="b952b-151">Before the class statement, add the following enum definition.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7. <span data-ttu-id="b952b-152">更新类语句以继承 `DynamicObject` 类，如以下代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="b952b-152">Update the class statement to inherit the `DynamicObject` class, as shown in the following code example.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. <span data-ttu-id="b952b-153">将以下代码添加到 `ReadOnlyFile` 类，定义一个用于文件路径的私有字段，并定义 `ReadOnlyFile` 类的构造函数。</span><span class="sxs-lookup"><span data-stu-id="b952b-153">Add the following code to the `ReadOnlyFile` class to define a private field for the file path and a constructor for the `ReadOnlyFile` class.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. <span data-ttu-id="b952b-154">将下面的 `GetPropertyValue` 方法添加到 `ReadOnlyFile` 类。</span><span class="sxs-lookup"><span data-stu-id="b952b-154">Add the following `GetPropertyValue` method to the `ReadOnlyFile` class.</span></span> <span data-ttu-id="b952b-155">`GetPropertyValue` 方法接收搜索条件作为输入，并返回文本文件中符合该搜索条件的行。</span><span class="sxs-lookup"><span data-stu-id="b952b-155">The `GetPropertyValue` method takes, as input, search criteria and returns the lines from a text file that match that search criteria.</span></span> <span data-ttu-id="b952b-156">由 `ReadOnlyFile` 类提供的动态方法将调用 `GetPropertyValue` 方法以检索其各自的结果。</span><span class="sxs-lookup"><span data-stu-id="b952b-156">The dynamic methods provided by the `ReadOnlyFile` class call the `GetPropertyValue` method to retrieve their respective results.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. <span data-ttu-id="b952b-157">在 `GetPropertyValue` 方法后，添加以下代码以替代 <xref:System.Dynamic.DynamicObject> 类的 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b952b-157">After the `GetPropertyValue` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="b952b-158">请求动态类的成员且未指定任何参数时，将调用 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b952b-158">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method is called when a member of a dynamic class is requested and no arguments are specified.</span></span> <span data-ttu-id="b952b-159">`binder` 参数包含有关被引用成员的信息，而 `result` 参数则引用为指定的成员返回的结果。</span><span class="sxs-lookup"><span data-stu-id="b952b-159">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="b952b-160"><xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法会返回一个布尔值，如果请求的成员存在，则返回的布尔值为 `true`，否则返回的布尔值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="b952b-160">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. <span data-ttu-id="b952b-161">在 `TryGetMember` 方法后，添加以下代码以替代 <xref:System.Dynamic.DynamicObject> 类的 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b952b-161">After the `TryGetMember` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="b952b-162">使用参数请求动态类的成员时，将调用 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b952b-162">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method is called when a member of a dynamic class is requested with arguments.</span></span> <span data-ttu-id="b952b-163">`binder` 参数包含有关被引用成员的信息，而 `result` 参数则引用为指定的成员返回的结果。</span><span class="sxs-lookup"><span data-stu-id="b952b-163">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="b952b-164">`args` 参数包含一个传递给成员的参数的数组。</span><span class="sxs-lookup"><span data-stu-id="b952b-164">The `args` argument contains an array of the arguments that are passed to the member.</span></span> <span data-ttu-id="b952b-165"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法会返回一个布尔值，如果请求的成员存在，则返回的布尔值为 `true`，否则返回的布尔值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="b952b-165">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>  
  
    <span data-ttu-id="b952b-166">`TryInvokeMember` 方法的自定义版本期望第一个参数为上一步骤中定义的 `StringSearchOption` 枚举中的值。</span><span class="sxs-lookup"><span data-stu-id="b952b-166">The custom version of the `TryInvokeMember` method expects the first argument to be a value from the `StringSearchOption` enum that you defined in a previous step.</span></span> <span data-ttu-id="b952b-167">`TryInvokeMember` 方法期望第二个参数为一个布尔值。</span><span class="sxs-lookup"><span data-stu-id="b952b-167">The `TryInvokeMember` method expects the second argument to be a Boolean value.</span></span> <span data-ttu-id="b952b-168">如果这两个参数有一个或全部为有效值，则将它们传递给 `GetPropertyValue` 方法以检索结果。</span><span class="sxs-lookup"><span data-stu-id="b952b-168">If one or both arguments are valid values, they are passed to the `GetPropertyValue` method to retrieve the results.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. <span data-ttu-id="b952b-169">保存并关闭文件。</span><span class="sxs-lookup"><span data-stu-id="b952b-169">Save and close the file.</span></span>  
  
#### <a name="to-create-a-sample-text-file"></a><span data-ttu-id="b952b-170">创建示例文本文件</span><span class="sxs-lookup"><span data-stu-id="b952b-170">To create a sample text file</span></span>  
  
1. <span data-ttu-id="b952b-171">右键单击 DynamicSample 项目，指向“添加”，然后单击“新建项”。</span><span class="sxs-lookup"><span data-stu-id="b952b-171">Right-click the DynamicSample project and point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="b952b-172">在“已安装的模板”窗格中，选择“常规”，然后选择“文本文件”模板。</span><span class="sxs-lookup"><span data-stu-id="b952b-172">In the **Installed Templates** pane, select **General**, and then select the **Text File** template.</span></span> <span data-ttu-id="b952b-173">在“名称”框中保留默认名称 TextFile1.txt，然后单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="b952b-173">Leave the default name of TextFile1.txt in the **Name** box, and then click **Add**.</span></span> <span data-ttu-id="b952b-174">这会将一个新的文本文件添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="b952b-174">A new text file is added to the project.</span></span>  
  
2. <span data-ttu-id="b952b-175">将以下文本复制到 TextFile1.txt 文件。</span><span class="sxs-lookup"><span data-stu-id="b952b-175">Copy the following text to the TextFile1.txt file.</span></span>  
  
    ```text  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3. <span data-ttu-id="b952b-176">保存并关闭文件。</span><span class="sxs-lookup"><span data-stu-id="b952b-176">Save and close the file.</span></span>  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a><span data-ttu-id="b952b-177">创建一个使用自定义动态对象的示例应用程序</span><span class="sxs-lookup"><span data-stu-id="b952b-177">To create a sample application that uses the custom dynamic object</span></span>  
  
1. <span data-ttu-id="b952b-178">在“解决方案资源管理器”中，双击 Module1.vb 文件（如果使用的是 Visual Basic）或 Program.cs 文件（如果使用的是 Visual C#）。</span><span class="sxs-lookup"><span data-stu-id="b952b-178">In **Solution Explorer**, double-click the Module1.vb file if you are using Visual Basic or the Program.cs file if you are using Visual C#.</span></span>  
  
2. <span data-ttu-id="b952b-179">将以下代码添加到 Main 过程，为 TextFile1.txt 文件创建一个 `ReadOnlyFile` 类的实例。</span><span class="sxs-lookup"><span data-stu-id="b952b-179">Add the following code to the Main procedure to create an instance of the `ReadOnlyFile` class for the TextFile1.txt file.</span></span> <span data-ttu-id="b952b-180">代码将使用晚期绑定来调用动态成员，并检索包含字符串“Customer”的文本行。</span><span class="sxs-lookup"><span data-stu-id="b952b-180">The code uses late binding to call dynamic members and retrieve lines of text that contain the string "Customer".</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3. <span data-ttu-id="b952b-181">保存文件，然后按 Ctrl+F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="b952b-181">Save the file and press CTRL+F5 to build and run the application.</span></span>  
  
## <a name="calling-a-dynamic-language-library"></a><span data-ttu-id="b952b-182">调用动态语言库</span><span class="sxs-lookup"><span data-stu-id="b952b-182">Calling a Dynamic Language Library</span></span>  

<span data-ttu-id="b952b-183">在此演练中创建的下一项目将访问以动态语言 IronPython 编写的库。</span><span class="sxs-lookup"><span data-stu-id="b952b-183">The next project that you create in this walkthrough accesses a library that is written in the dynamic language IronPython.</span></span>
  
### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="b952b-184">创建自定义动态类</span><span class="sxs-lookup"><span data-stu-id="b952b-184">To create a custom dynamic class</span></span>
  
1. <span data-ttu-id="b952b-185">在 Visual Studio 中的“文件”菜单上，指向“新建”，然后单击“项目”。</span><span class="sxs-lookup"><span data-stu-id="b952b-185">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2. <span data-ttu-id="b952b-186">在“新建项目”对话框的“项目类型”窗格中，确保选中“Windows”。</span><span class="sxs-lookup"><span data-stu-id="b952b-186">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="b952b-187">在“模板”窗格中，选择“控制台应用程序”。</span><span class="sxs-lookup"><span data-stu-id="b952b-187">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="b952b-188">在“名称”框中，键入 `DynamicIronPythonSample`，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="b952b-188">In the **Name** box, type `DynamicIronPythonSample`, and then click **OK**.</span></span> <span data-ttu-id="b952b-189">新项目创建完成。</span><span class="sxs-lookup"><span data-stu-id="b952b-189">The new project is created.</span></span>  
  
3. <span data-ttu-id="b952b-190">如果使用的是 Visual Basic，请右击 DynamicIronPythonSample 项目，然后单击“属性”。</span><span class="sxs-lookup"><span data-stu-id="b952b-190">If you are using Visual Basic, right-click the DynamicIronPythonSample project and then click **Properties**.</span></span> <span data-ttu-id="b952b-191">单击“引用”选项卡。单击“添加”按钮。</span><span class="sxs-lookup"><span data-stu-id="b952b-191">Click the **References** tab. Click the **Add** button.</span></span> <span data-ttu-id="b952b-192">如果使用的是 Visual C#，请在“解决方案资源管理器”中，右键单击“引用”文件夹，然后单击“添加引用”。</span><span class="sxs-lookup"><span data-stu-id="b952b-192">If you are using Visual C#, in **Solution Explorer**, right-click the **References** folder and then click **Add Reference**.</span></span>  
  
4. <span data-ttu-id="b952b-193">在“浏览”选项卡上，浏览到安装 IronPython 库的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b952b-193">On the **Browse** tab, browse to the folder where the IronPython libraries are installed.</span></span> <span data-ttu-id="b952b-194">例如，C:\Program Files\IronPython 2.6 for .NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="b952b-194">For example, C:\Program Files\IronPython 2.6 for .NET 4.0.</span></span> <span data-ttu-id="b952b-195">选择“IronPython.dll”、“IronPython.Modules.dll”、“Microsoft.Scripting.dll”和“Microsoft.Dynamic.dll”库。</span><span class="sxs-lookup"><span data-stu-id="b952b-195">Select the **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, and **Microsoft.Dynamic.dll** libraries.</span></span> <span data-ttu-id="b952b-196">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="b952b-196">Click **OK**.</span></span>  
  
5. <span data-ttu-id="b952b-197">如果使用的是 Visual Basic，请编辑 Module1.vb 文件。</span><span class="sxs-lookup"><span data-stu-id="b952b-197">If you are using Visual Basic, edit the Module1.vb file.</span></span> <span data-ttu-id="b952b-198">如果使用的是 Visual C#，请编辑 Program.cs 文件。</span><span class="sxs-lookup"><span data-stu-id="b952b-198">If you are using Visual C#, edit the Program.cs file.</span></span>  
  
6. <span data-ttu-id="b952b-199">在文件的顶部，添加以下代码以从 IronPython 库导入 `Microsoft.Scripting.Hosting` 和 `IronPython.Hosting` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="b952b-199">At the top of the file, add the following code to import the `Microsoft.Scripting.Hosting` and `IronPython.Hosting` namespaces from the IronPython libraries.</span></span>  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7. <span data-ttu-id="b952b-200">在 Main 方法中，添加以下代码以创建用于托管 IronPython 库的新 `Microsoft.Scripting.Hosting.ScriptRuntime` 对象。</span><span class="sxs-lookup"><span data-stu-id="b952b-200">In the Main method, add the following code to create a new `Microsoft.Scripting.Hosting.ScriptRuntime` object to host the IronPython libraries.</span></span> <span data-ttu-id="b952b-201">`ScriptRuntime` 对象加载 IronPython 库模块 random.py。</span><span class="sxs-lookup"><span data-stu-id="b952b-201">The `ScriptRuntime` object loads the IronPython library module random.py.</span></span>  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8. <span data-ttu-id="b952b-202">在用于加载 random.py 模块的代码之后，添加以下代码以创建一个整数数组。</span><span class="sxs-lookup"><span data-stu-id="b952b-202">After the code to load the random.py module, add the following code to create an array of integers.</span></span> <span data-ttu-id="b952b-203">数组传递给 random.py 模块的 `shuffle` 方法，该方法对数组中的值进行随机排序。</span><span class="sxs-lookup"><span data-stu-id="b952b-203">The array is passed to the `shuffle` method of the random.py module, which randomly sorts the values in the array.</span></span>  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. <span data-ttu-id="b952b-204">保存文件，然后按 Ctrl+F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="b952b-204">Save the file and press CTRL+F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b952b-205">请参阅</span><span class="sxs-lookup"><span data-stu-id="b952b-205">See also</span></span>

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [<span data-ttu-id="b952b-206">使用类型 dynamic</span><span class="sxs-lookup"><span data-stu-id="b952b-206">Using Type dynamic</span></span>](./using-type-dynamic.md)
- [<span data-ttu-id="b952b-207">早期绑定和后期绑定</span><span class="sxs-lookup"><span data-stu-id="b952b-207">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="b952b-208">dynamic</span><span class="sxs-lookup"><span data-stu-id="b952b-208">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="b952b-209">实现动态接口（可从 Microsoft TechNet 下载 PDF）</span><span class="sxs-lookup"><span data-stu-id="b952b-209">Implementing Dynamic Interfaces (downloadable PDF from Microsoft TechNet)</span></span>](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
