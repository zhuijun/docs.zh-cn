---
title: 如何在 Office 编程中使用命名实参和可选实参（C# 编程指南）
description: 了解如何使用命名参数和可选参数来帮助访问 COM 接口，如 Microsoft Office 自动化 API。
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 7e24331d37e8fdbe2bc66a2d9f73a5f6a7242af9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864340"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="8e7b5-103">如何在 Office 编程中使用命名实参和可选实参（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="8e7b5-103">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="8e7b5-104">在 C# 4 中引入的命名参数和可选参数增强了 C# 编程中的便利性、灵活性和可读性。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-104">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="8e7b5-105">另外，这些功能显著方便了对 COM 接口（如 Microsoft Office 自动化 API）的访问。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-105">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="8e7b5-106">在下面的示例中，方法 [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) 具有十六个参数，用于表示表的各种特性，例如列数和行数、格式设置、边框、字体以及颜色。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-106">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="8e7b5-107">由于大多数时候都不需要为所有十六个参数指定特定值，因此所有这些参数都是可选的。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-107">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="8e7b5-108">但是，如果没有命名实参和可选实参，则必须为每个形参提供值或占位符值。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-108">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="8e7b5-109">有了命名实参和可选实参，则只需为项目所需的形参指定值。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-109">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="8e7b5-110">必须在计算机上安装 Microsoft Office Word 才能完成这些过程。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-110">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="8e7b5-111">创建新的控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="8e7b5-111">To create a new console application</span></span>

1. <span data-ttu-id="8e7b5-112">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-112">Start Visual Studio.</span></span>

2. <span data-ttu-id="8e7b5-113">在 **“文件”** 菜单上，指向 **“新建”** ，然后单击 **“项目”** 。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-113">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="8e7b5-114">在“模板类别”窗格中，展开“Visual C#”，然后单击“Windows”。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-114">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="8e7b5-115">查看“模板”窗格的顶部，确保“.NET Framework 4”出现在“目标框架”框中。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-115">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="8e7b5-116">在“模板”窗格中，单击“控制台应用程序”。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-116">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="8e7b5-117">在“名称”字段中键入项目的名称。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-117">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="8e7b5-118">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-118">Click **OK**.</span></span>

     <span data-ttu-id="8e7b5-119">新项目将出现在“解决方案资源管理器”中。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-119">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="8e7b5-120">添加引用</span><span class="sxs-lookup"><span data-stu-id="8e7b5-120">To add a reference</span></span>

1. <span data-ttu-id="8e7b5-121">在“解决方案资源管理器”中，右键单击你的项目名称，然后单击“添加引用”。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-121">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="8e7b5-122">此时会显示“添加引用”对话框。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-122">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="8e7b5-123">在“.NET”页上的“组件名称”列表中，选择“Microsoft.Office.Interop.Word”  。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-123">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="8e7b5-124">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="8e7b5-125">添加必要的 using 指令</span><span class="sxs-lookup"><span data-stu-id="8e7b5-125">To add necessary using directives</span></span>

1. <span data-ttu-id="8e7b5-126">在“解决方案资源管理器”中，右键单击“Program.cs”文件，然后单击“查看代码”。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="8e7b5-127">将以下 `using` 指令添加到代码文件的顶部：</span><span class="sxs-lookup"><span data-stu-id="8e7b5-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="8e7b5-128">在 Word 文档中显示文本</span><span class="sxs-lookup"><span data-stu-id="8e7b5-128">To display text in a Word document</span></span>

1. <span data-ttu-id="8e7b5-129">在“Program.cs”的 `Program` 类中，添加以下方法以创建 Word 应用程序和 Word 文档。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-129">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="8e7b5-130">[Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) 方法具有四个可选参数。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-130">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="8e7b5-131">此示例使用这些参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-131">This example uses their default values.</span></span> <span data-ttu-id="8e7b5-132">因此，调用语句中不必有参数。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-132">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="8e7b5-133">将以下代码添加到方法的末尾，以定义要在文档何处显示文本，以及要显示什么文本：</span><span class="sxs-lookup"><span data-stu-id="8e7b5-133">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="8e7b5-134">要运行应用程序</span><span class="sxs-lookup"><span data-stu-id="8e7b5-134">To run the application</span></span>

1. <span data-ttu-id="8e7b5-135">将以下语句添加到 Main：</span><span class="sxs-lookup"><span data-stu-id="8e7b5-135">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="8e7b5-136">按 <kbd>Ctrl</kbd>+<kbd>F5</kbd> 运行项目。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-136">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="8e7b5-137">此时会出现一个 Word 文档，其中包含指定的文本。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-137">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="8e7b5-138">将文本更改为表</span><span class="sxs-lookup"><span data-stu-id="8e7b5-138">To change the text to a table</span></span>
  
1. <span data-ttu-id="8e7b5-139">使用 `ConvertToTable` 方法将文本放入表中。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-139">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="8e7b5-140">该方法具有十六个可选参数。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-140">The method has sixteen optional parameters.</span></span> <span data-ttu-id="8e7b5-141">IntelliSense 将可选参数放入括号中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-141">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![ConvertToTable 方法的参数列表](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="8e7b5-143">通过使用命名实参和可选实参，可以只对要更改的形参指定值。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="8e7b5-144">将以下代码添加到方法 `DisplayInWord` 的末尾以创建一个简单的表。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="8e7b5-145">此参数指定 `range` 中文本字符串内的逗号分隔表的各个单元格。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="8e7b5-146">在 C# 早期版本中，对 `ConvertToTable` 的调用需要对每个形参使用引用实参，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="8e7b5-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="8e7b5-147">按 <kbd>Ctrl</kbd>+<kbd>F5</kbd> 运行项目。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-147">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="8e7b5-148">试验其他参数</span><span class="sxs-lookup"><span data-stu-id="8e7b5-148">To experiment with other parameters</span></span>

1. <span data-ttu-id="8e7b5-149">若要更改表以使其具有一列三行，请将 `DisplayInWord` 中的最后一行替换为以下语句，然后按 <kbd>CTRL</kbd>+<kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="8e7b5-150">若要为表指定预定义的格式，请将 `DisplayInWord` 中的最后一行替换为以下语句，然后按 <kbd>CTRL</kbd>+<kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="8e7b5-151">格式可以为任何 [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) 常量。</span><span class="sxs-lookup"><span data-stu-id="8e7b5-151">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="8e7b5-152">示例</span><span class="sxs-lookup"><span data-stu-id="8e7b5-152">Example</span></span>

<span data-ttu-id="8e7b5-153">下面的代码包括完整的示例：</span><span class="sxs-lookup"><span data-stu-id="8e7b5-153">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="8e7b5-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e7b5-154">See also</span></span>

- [<span data-ttu-id="8e7b5-155">命名参数和可选参数</span><span class="sxs-lookup"><span data-stu-id="8e7b5-155">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
