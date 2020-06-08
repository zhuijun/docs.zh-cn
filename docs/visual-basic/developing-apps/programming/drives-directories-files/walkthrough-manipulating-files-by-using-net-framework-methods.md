---
title: 使用 .NET Framework 方法操作文件
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 9abb87f3f6cdefefef29eb37c2c2d4d15155e93d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406646"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="c3dad-102">演练：使用 .NET Framework 方法操作文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3dad-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>

<span data-ttu-id="c3dad-103">此演练演示了如何使用 <xref:System.IO.StreamReader> 类打开和读取文件，如何查看文件是否正被访问，如何在使用 <xref:System.IO.StreamReader> 类实例读取的文件中搜索字符串，以及如何使用 <xref:System.IO.StreamWriter> 类写入文件。</span><span class="sxs-lookup"><span data-stu-id="c3dad-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-the-application"></a><span data-ttu-id="c3dad-104">创建应用程序</span><span class="sxs-lookup"><span data-stu-id="c3dad-104">Creating the Application</span></span>

<span data-ttu-id="c3dad-105">启动 Visual Studio，并创建一个用户可用于写入指定文件的窗体来开始项目。</span><span class="sxs-lookup"><span data-stu-id="c3dad-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>

### <a name="to-create-the-project"></a><span data-ttu-id="c3dad-106">创建项目</span><span class="sxs-lookup"><span data-stu-id="c3dad-106">To create the project</span></span>

1. <span data-ttu-id="c3dad-107">在“文件”菜单上，选择“新建项目”。  </span><span class="sxs-lookup"><span data-stu-id="c3dad-107">On the **File** menu, select **New Project**.</span></span>

2. <span data-ttu-id="c3dad-108">在“新建项目”窗格中，单击“Windows 应用程序”。  </span><span class="sxs-lookup"><span data-stu-id="c3dad-108">In the **New Project** pane, click **Windows Application**.</span></span>

3. <span data-ttu-id="c3dad-109">在“名称”框中，键入 `MyDiary`，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="c3dad-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>

     <span data-ttu-id="c3dad-110">Visual Studio 将项目添加到“解决方案资源管理器”中，“Windows 窗体设计器”随即打开   。</span><span class="sxs-lookup"><span data-stu-id="c3dad-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>

4. <span data-ttu-id="c3dad-111">将下表中的控件添加到窗体中，并为其属性设置相应的值。</span><span class="sxs-lookup"><span data-stu-id="c3dad-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="c3dad-112">**对象**</span><span class="sxs-lookup"><span data-stu-id="c3dad-112">**Object**</span></span>|<bpt id="p1">**</bpt>Properties<ept id="p1">**</ept>|<span data-ttu-id="c3dad-114">**值**</span><span class="sxs-lookup"><span data-stu-id="c3dad-114">**Value**</span></span>|
|---|---|---|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c3dad-115">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-115">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-116">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="c3dad-117">**提交项**</span><span class="sxs-lookup"><span data-stu-id="c3dad-117">**Submit Entry**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c3dad-118">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-118">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-119">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="c3dad-120">**清除项**</span><span class="sxs-lookup"><span data-stu-id="c3dad-120">**Clear Entry**</span></span>|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="c3dad-121">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-121">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-122">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-122">**Text**</span></span><br /><br /> <span data-ttu-id="c3dad-123">**多行**</span><span class="sxs-lookup"><span data-stu-id="c3dad-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="c3dad-124">**请输入内容。**</span><span class="sxs-lookup"><span data-stu-id="c3dad-124">**Please enter something.**</span></span><br /><br /> `False`|

## <a name="writing-to-the-file"></a><span data-ttu-id="c3dad-125">写入文件</span><span class="sxs-lookup"><span data-stu-id="c3dad-125">Writing to the File</span></span>

<span data-ttu-id="c3dad-126">若要通过应用程序添加写入文件的功能，请使用 <xref:System.IO.StreamWriter> 类。</span><span class="sxs-lookup"><span data-stu-id="c3dad-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="c3dad-127"><xref:System.IO.StreamWriter> 设计用于特定编码的字符输出，而 <xref:System.IO.Stream> 类设计用于字节的输入和输出。</span><span class="sxs-lookup"><span data-stu-id="c3dad-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="c3dad-128">使用 <xref:System.IO.StreamWriter> 可将多行信息写入标准的文本文件。</span><span class="sxs-lookup"><span data-stu-id="c3dad-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="c3dad-129">有关 <xref:System.IO.StreamWriter> 类的详细信息，请参阅 <xref:System.IO.StreamWriter>。</span><span class="sxs-lookup"><span data-stu-id="c3dad-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>

### <a name="to-add-writing-functionality"></a><span data-ttu-id="c3dad-130">添加写入功能</span><span class="sxs-lookup"><span data-stu-id="c3dad-130">To add writing functionality</span></span>

1. <span data-ttu-id="c3dad-131">从“视图”菜单中选择“代码”，以打开代码编辑器。  </span><span class="sxs-lookup"><span data-stu-id="c3dad-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>

2. <span data-ttu-id="c3dad-132">由于该应用程序引用 <xref:System.IO> 命名空间，因此，请在代码的最开头处，在窗体的类声明（以 `Public Class Form1` 开始）之前，添加以下语句。</span><span class="sxs-lookup"><span data-stu-id="c3dad-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#35)]

     <span data-ttu-id="c3dad-133">写入文件前，必须创建一个 <xref:System.IO.StreamWriter> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="c3dad-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>

3. <span data-ttu-id="c3dad-134">从“视图”菜单中选择“设计器”，以返回“Windows 窗体设计器”。   </span><span class="sxs-lookup"><span data-stu-id="c3dad-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="c3dad-135">双击 `Submit` 按钮，为该按钮创建一个 <xref:System.Windows.Forms.Control.Click> 事件处理程序，然后添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="c3dad-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#36)]

> [!NOTE]
> <span data-ttu-id="c3dad-136">Visual Studio 集成开发环境 (IDE) 将返回代码编辑器，并将插入点放在应在其中添加代码的事件处理程序内。</span><span class="sxs-lookup"><span data-stu-id="c3dad-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>

1. <span data-ttu-id="c3dad-137">若要写入该文件，请使用 <xref:System.IO.StreamWriter> 类的 <xref:System.IO.StreamWriter.Write%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c3dad-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="c3dad-138">在 `Dim fw As StreamWriter` 后直接添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="c3dad-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="c3dad-139">不需要担心如果找不到该文件会引发异常，因为如果它不存在，将创建该文件。</span><span class="sxs-lookup"><span data-stu-id="c3dad-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>

     [!code-vb[VbVbcnMyFileSystem#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#37)]

2. <span data-ttu-id="c3dad-140">在 `Dim ReadString As String` 后直接添加以下代码，确保用户无法提交空项。</span><span class="sxs-lookup"><span data-stu-id="c3dad-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#38)]

3. <span data-ttu-id="c3dad-141">因为这是日记，所以用户需要为每一项指定一个日期。</span><span class="sxs-lookup"><span data-stu-id="c3dad-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="c3dad-142">在 `fw = New StreamWriter("C:\MyDiary.txt", True)` 之后插入以下代码，以将变量 `Today` 设置为当前日期。</span><span class="sxs-lookup"><span data-stu-id="c3dad-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>

     [!code-vb[VbVbcnMyFileSystem#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#39)]

4. <span data-ttu-id="c3dad-143">最后，附加代码以清除 <xref:System.Windows.Forms.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="c3dad-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c3dad-144">将以下代码添加到 `Clear` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件中。</span><span class="sxs-lookup"><span data-stu-id="c3dad-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>

     [!code-vb[VbVbcnMyFileSystem#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#40)]

## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="c3dad-145">将显示功能添加到日记</span><span class="sxs-lookup"><span data-stu-id="c3dad-145">Adding Display Features to the Diary</span></span>

<span data-ttu-id="c3dad-146">在本节中，将添加一项功能，用于显示 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中的最新项。</span><span class="sxs-lookup"><span data-stu-id="c3dad-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c3dad-147">还可以添加 <xref:System.Windows.Forms.ComboBox> 以显示各种项，同时用户可从中选择一个显示在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中的条目。</span><span class="sxs-lookup"><span data-stu-id="c3dad-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c3dad-148"><xref:System.IO.StreamReader> 类的实例从 `MyDiary.txt` 中读取。</span><span class="sxs-lookup"><span data-stu-id="c3dad-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="c3dad-149">与 <xref:System.IO.StreamWriter> 类一样，<xref:System.IO.StreamReader> 可与文本文件一起使用。</span><span class="sxs-lookup"><span data-stu-id="c3dad-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>

<span data-ttu-id="c3dad-150">在此演练的这一节中，请将下表中的控件添加到窗体中，并为其属性设置相应的值。</span><span class="sxs-lookup"><span data-stu-id="c3dad-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="c3dad-151">控件</span><span class="sxs-lookup"><span data-stu-id="c3dad-151">Control</span></span>|<span data-ttu-id="c3dad-152">属性</span><span class="sxs-lookup"><span data-stu-id="c3dad-152">Properties</span></span>|<span data-ttu-id="c3dad-153">值</span><span class="sxs-lookup"><span data-stu-id="c3dad-153">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="c3dad-154">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-154">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-155">**可见**</span><span class="sxs-lookup"><span data-stu-id="c3dad-155">**Visible**</span></span><br /><br /> <span data-ttu-id="c3dad-156">**Size**</span><span class="sxs-lookup"><span data-stu-id="c3dad-156">**Size**</span></span><br /><br /> <span data-ttu-id="c3dad-157">**多行**</span><span class="sxs-lookup"><span data-stu-id="c3dad-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c3dad-158">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-158">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-159">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="c3dad-160">**显示**</span><span class="sxs-lookup"><span data-stu-id="c3dad-160">**Display**</span></span>|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c3dad-161">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-161">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-162">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="c3dad-163">**获取项**</span><span class="sxs-lookup"><span data-stu-id="c3dad-163">**Get Entries**</span></span>|
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="c3dad-164">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-164">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-165">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-165">**Text**</span></span><br /><br /> <span data-ttu-id="c3dad-166">**启用**</span><span class="sxs-lookup"><span data-stu-id="c3dad-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="c3dad-167">**选择一项**</span><span class="sxs-lookup"><span data-stu-id="c3dad-167">**Select an Entry**</span></span><br /><br /> `False`|

### <a name="to-populate-the-combo-box"></a><span data-ttu-id="c3dad-168">填充组合框</span><span class="sxs-lookup"><span data-stu-id="c3dad-168">To populate the combo box</span></span>

1. <span data-ttu-id="c3dad-169">`PickEntries`<xref:System.Windows.Forms.ComboBox> 用于显示用户提交每一项的日期，这样，用户就可以选择特定日期的项。</span><span class="sxs-lookup"><span data-stu-id="c3dad-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="c3dad-170">创建 `GetEntries` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序并添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="c3dad-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#41)]

2. <span data-ttu-id="c3dad-171">若要测试代码，请按 F5 编译该应用程序，然后单击“获取项”。 </span><span class="sxs-lookup"><span data-stu-id="c3dad-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="c3dad-172">单击 <xref:System.Windows.Forms.ComboBox> 中的下拉箭头，以显示条目日期。</span><span class="sxs-lookup"><span data-stu-id="c3dad-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>

### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="c3dad-173">选择并显示个别项</span><span class="sxs-lookup"><span data-stu-id="c3dad-173">To choose and display individual entries</span></span>

1. <span data-ttu-id="c3dad-174">创建 `Display` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序并添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="c3dad-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#42)]

2. <span data-ttu-id="c3dad-175">若要测试代码，请按 F5 编译该应用程序，然后提交一项。</span><span class="sxs-lookup"><span data-stu-id="c3dad-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="c3dad-176">单击“获取项”，从 <xref:System.Windows.Forms.ComboBox> 中选择一项，然后单击“显示”。</span><span class="sxs-lookup"><span data-stu-id="c3dad-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="c3dad-177">所选条目的内容显示在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中。</span><span class="sxs-lookup"><span data-stu-id="c3dad-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="c3dad-178">允许用户删除或修改项</span><span class="sxs-lookup"><span data-stu-id="c3dad-178">Enabling Users to Delete or Modify Entries</span></span>

<span data-ttu-id="c3dad-179">最后，可以包括其他功能，以允许用户使用 `DeleteEntry` 和 `EditEntry` 按钮来删除或修改项。</span><span class="sxs-lookup"><span data-stu-id="c3dad-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="c3dad-180">除非显示有项，否则这两个按钮都保持禁用状态。</span><span class="sxs-lookup"><span data-stu-id="c3dad-180">Both buttons remain disabled unless an entry is displayed.</span></span>

<span data-ttu-id="c3dad-181">将下表中的控件添加到窗体中，并为其属性设置相应的值。</span><span class="sxs-lookup"><span data-stu-id="c3dad-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>

|<span data-ttu-id="c3dad-182">控件</span><span class="sxs-lookup"><span data-stu-id="c3dad-182">Control</span></span>|<span data-ttu-id="c3dad-183">属性</span><span class="sxs-lookup"><span data-stu-id="c3dad-183">Properties</span></span>|<span data-ttu-id="c3dad-184">值</span><span class="sxs-lookup"><span data-stu-id="c3dad-184">Values</span></span>|
|-------------|----------------|------------|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c3dad-185">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-185">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-186">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-186">**Text**</span></span><br /><br /> <span data-ttu-id="c3dad-187">**启用**</span><span class="sxs-lookup"><span data-stu-id="c3dad-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="c3dad-188">**删除项**</span><span class="sxs-lookup"><span data-stu-id="c3dad-188">**Delete Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c3dad-189">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-189">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-190">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-190">**Text**</span></span><br /><br /> <span data-ttu-id="c3dad-191">**启用**</span><span class="sxs-lookup"><span data-stu-id="c3dad-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="c3dad-192">**编辑项**</span><span class="sxs-lookup"><span data-stu-id="c3dad-192">**Edit Entry**</span></span><br /><br /> `False`|
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="c3dad-193">**Name**</span><span class="sxs-lookup"><span data-stu-id="c3dad-193">**Name**</span></span><br /><br /> <span data-ttu-id="c3dad-194">**文本**</span><span class="sxs-lookup"><span data-stu-id="c3dad-194">**Text**</span></span><br /><br /> <span data-ttu-id="c3dad-195">**启用**</span><span class="sxs-lookup"><span data-stu-id="c3dad-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="c3dad-196">**提交编辑**</span><span class="sxs-lookup"><span data-stu-id="c3dad-196">**Submit Edit**</span></span><br /><br /> `False`|

### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="c3dad-197">允许删除和修改项</span><span class="sxs-lookup"><span data-stu-id="c3dad-197">To enable deletion and modification of entries</span></span>

1. <span data-ttu-id="c3dad-198">在 `DisplayEntry.Text = ReadString` 之后，将以下代码添加到 `Display` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="c3dad-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#43)]

2. <span data-ttu-id="c3dad-199">创建 `DeleteEntry` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序并添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="c3dad-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#44)]

3. <span data-ttu-id="c3dad-200">用户显示某一项时，`EditEntry` 按钮将变为启用状态。</span><span class="sxs-lookup"><span data-stu-id="c3dad-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="c3dad-201">在 `DisplayEntry.Text = ReadString` 之后，将以下代码添加到 `Display` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="c3dad-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>

     [!code-vb[VbVbcnMyFileSystem#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#45)]

4. <span data-ttu-id="c3dad-202">创建 `EditEntry` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序并添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="c3dad-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>

     [!code-vb[VbVbcnMyFileSystem#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#46)]

5. <span data-ttu-id="c3dad-203">创建 `SubmitEdit` 按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理程序并添加以下代码</span><span class="sxs-lookup"><span data-stu-id="c3dad-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>

     [!code-vb[VbVbcnMyFileSystem#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#47)]

<span data-ttu-id="c3dad-204">若要测试代码，请按 F5 编译该应用程序。</span><span class="sxs-lookup"><span data-stu-id="c3dad-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="c3dad-205">单击“获取项”，选择一项，然后单击“显示”。  </span><span class="sxs-lookup"><span data-stu-id="c3dad-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="c3dad-206">条目将出现在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中。</span><span class="sxs-lookup"><span data-stu-id="c3dad-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c3dad-207">单击“编辑项”  。</span><span class="sxs-lookup"><span data-stu-id="c3dad-207">Click **Edit Entry**.</span></span> <span data-ttu-id="c3dad-208">条目将出现在 `Entry`<xref:System.Windows.Forms.TextBox> 中。</span><span class="sxs-lookup"><span data-stu-id="c3dad-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="c3dad-209">编辑 `Entry`<xref:System.Windows.Forms.TextBox> 中的项，然后单击“提交编辑”  。</span><span class="sxs-lookup"><span data-stu-id="c3dad-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="c3dad-210">打开 `MyDiary.txt` 文件以确认所做的更正。</span><span class="sxs-lookup"><span data-stu-id="c3dad-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="c3dad-211">现在，选择一项，然后单击“删除项”  。</span><span class="sxs-lookup"><span data-stu-id="c3dad-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="c3dad-212">当 <xref:System.Windows.Forms.MessageBox> 请求确认时，请单击“确定”  。</span><span class="sxs-lookup"><span data-stu-id="c3dad-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="c3dad-213">关闭该应用程序，然后打开 `MyDiary.txt`，以确认该项已删除。</span><span class="sxs-lookup"><span data-stu-id="c3dad-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3dad-214">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c3dad-214">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="c3dad-215">演练</span><span class="sxs-lookup"><span data-stu-id="c3dad-215">Walkthroughs</span></span>](../../../walkthroughs.md)
