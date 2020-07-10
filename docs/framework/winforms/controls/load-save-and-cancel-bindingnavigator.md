---
title: 向 BindingNavigator 控件添加 "加载"、"保存" 和 "取消" 按钮
description: 了解如何向 Windows 窗体 BindingNavigator 控件添加 "加载"、"保存" 和 "取消" 按钮。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173414"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="48ae9-103">如何：向 Windows 窗体 BindingNavigator 控件添加“加载”、“保存”和“取消”按钮</span><span class="sxs-lookup"><span data-stu-id="48ae9-103">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="48ae9-104"><xref:System.Windows.Forms.BindingNavigator>控件是一种特殊用途的 <xref:System.Windows.Forms.ToolStrip> 控件，用于在窗体上导航和操作绑定到数据的控件。</span><span class="sxs-lookup"><span data-stu-id="48ae9-104">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="48ae9-105">由于它是一个 <xref:System.Windows.Forms.ToolStrip> 控件，因此 <xref:System.Windows.Forms.BindingNavigator> 可以轻松修改组件，以包含用户的其他或其他命令。</span><span class="sxs-lookup"><span data-stu-id="48ae9-105">Because it's a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="48ae9-106">在下面的过程中， <xref:System.Windows.Forms.TextBox> 控件绑定到数据， <xref:System.Windows.Forms.ToolStrip> 添加到窗体中的控件将被修改为包含 "加载"、"保存" 和 "取消" 按钮。</span><span class="sxs-lookup"><span data-stu-id="48ae9-106">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="48ae9-107">向 BindingNavigator 组件添加 "加载"、"保存" 和 "取消" 按钮</span><span class="sxs-lookup"><span data-stu-id="48ae9-107">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="48ae9-108">在 Visual Studio 中，向 <xref:System.Windows.Forms.TextBox> 窗体添加一个控件。</span><span class="sxs-lookup"><span data-stu-id="48ae9-108">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="48ae9-109">将其绑定到 <xref:System.Windows.Forms.BindingSource> 绑定到数据源的。</span><span class="sxs-lookup"><span data-stu-id="48ae9-109">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="48ae9-110">在此示例中， <xref:System.Windows.Forms.BindingSource> 绑定到数据库。</span><span class="sxs-lookup"><span data-stu-id="48ae9-110">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="48ae9-111">生成数据集和表适配器后，将控件拖 <xref:System.Windows.Forms.BindingNavigator> 到窗体上。</span><span class="sxs-lookup"><span data-stu-id="48ae9-111">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="48ae9-112"><xref:System.Windows.Forms.BindingNavigator> <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> <xref:System.Windows.Forms.BindingSource> 在绑定到控件的窗体上，将控件的属性设置为。</span><span class="sxs-lookup"><span data-stu-id="48ae9-112">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="48ae9-113">选择 <xref:System.Windows.Forms.BindingNavigator> 控件。</span><span class="sxs-lookup"><span data-stu-id="48ae9-113">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="48ae9-114">单击 "设计器操作" 标志符号 (![ 小型黑色箭头 ](./media/designer-actions-glyph.gif)) ，此时将显示 " **BindingNavigator 任务**" 对话框，然后选择 "**编辑项目**"。</span><span class="sxs-lookup"><span data-stu-id="48ae9-114">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="48ae9-115">**项集合编辑器**随即出现。</span><span class="sxs-lookup"><span data-stu-id="48ae9-115">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="48ae9-116">在**Items 集合编辑器**中，完成以下操作：</span><span class="sxs-lookup"><span data-stu-id="48ae9-116">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="48ae9-117"><xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.ToolStripButton> 通过选择适当的类型 <xref:System.Windows.Forms.ToolStripItem> 并单击 "**添加**" 按钮，添加一个和三个项。</span><span class="sxs-lookup"><span data-stu-id="48ae9-117">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="48ae9-118">分别将 <xref:System.Windows.Forms.ToolStripItem.Name%2A> 按钮的属性设置为**LoadButton**、 **SaveButton**和**CancelButton**。</span><span class="sxs-lookup"><span data-stu-id="48ae9-118">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="48ae9-119">将 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 按钮的属性设置为 "**加载**"、"**保存**" 和 "**取消**"。</span><span class="sxs-lookup"><span data-stu-id="48ae9-119">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="48ae9-120">将 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 每个按钮的属性设置为 "**文本**"。</span><span class="sxs-lookup"><span data-stu-id="48ae9-120">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="48ae9-121">或者，您可以将此属性设置为**image**或**ImageAndText**，并将该图像设置为显示在 <xref:System.Windows.Forms.ToolStripItem.Image%2A> 属性中。</span><span class="sxs-lookup"><span data-stu-id="48ae9-121">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="48ae9-122">单击“确定”  关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="48ae9-122">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="48ae9-123">这些按钮将添加到 <xref:System.Windows.Forms.ToolStrip> 。</span><span class="sxs-lookup"><span data-stu-id="48ae9-123">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="48ae9-124">右键单击窗体，然后选择 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="48ae9-124">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="48ae9-125">在代码编辑器中，找到将数据加载到表适配器的代码行。</span><span class="sxs-lookup"><span data-stu-id="48ae9-125">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="48ae9-126">此代码是在步骤2中设置数据绑定时生成的。</span><span class="sxs-lookup"><span data-stu-id="48ae9-126">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="48ae9-127">此代码应类似于以下内容： `TableAdapterName.Fill(DataSetName.TableName)` 。</span><span class="sxs-lookup"><span data-stu-id="48ae9-127">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="48ae9-128">它最有可能是窗体的 <xref:System.Windows.Forms.Form.Load> 事件。</span><span class="sxs-lookup"><span data-stu-id="48ae9-128">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="48ae9-129">为之前创建的负载的事件创建事件处理程序 <xref:System.Windows.Forms.ToolStripItem.Click> **Load** <xref:System.Windows.Forms.ToolStripButton> ，并将此数据加载到其中。</span><span class="sxs-lookup"><span data-stu-id="48ae9-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="48ae9-130">你的代码现在应如下所示：</span><span class="sxs-lookup"><span data-stu-id="48ae9-130">Your code should now look similar to the following:</span></span>

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. <span data-ttu-id="48ae9-131">为之前创建的 Save 的事件创建事件处理程序 <xref:System.Windows.Forms.ToolStripItem.Click> **Save** <xref:System.Windows.Forms.ToolStripButton> ，并编写代码以更新控件所绑定到的表中的数据。</span><span class="sxs-lookup"><span data-stu-id="48ae9-131">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="48ae9-132">在某些情况下， <xref:System.Windows.Forms.BindingNavigator> 组件已经有 "**保存**" 按钮，但 Windows 窗体设计器未生成任何代码。</span><span class="sxs-lookup"><span data-stu-id="48ae9-132">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="48ae9-133">在这种情况下，你可以将前面的代码放在 <xref:System.Windows.Forms.ToolStripItem.Click> 该按钮的事件处理程序中，而不是在上创建一个全新的按钮 <xref:System.Windows.Forms.ToolStrip> 。</span><span class="sxs-lookup"><span data-stu-id="48ae9-133">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="48ae9-134">但是，默认情况下，此按钮处于禁用状态，因此必须将 <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> 该按钮的属性设置为 `true` 才能使按钮正常工作。</span><span class="sxs-lookup"><span data-stu-id="48ae9-134">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="48ae9-135">为之前创建的 "取消" 事件创建事件处理程序 <xref:System.Windows.Forms.ToolStripItem.Click> **Cancel** <xref:System.Windows.Forms.ToolStripButton> ，然后编写代码以取消对显示的数据记录所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="48ae9-135">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="48ae9-136"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的作用域为数据行。</span><span class="sxs-lookup"><span data-stu-id="48ae9-136">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="48ae9-137">在导航到下一条记录之前，保存在查看单个记录时所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="48ae9-137">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="48ae9-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="48ae9-138">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="48ae9-139">BindingNavigator 控件</span><span class="sxs-lookup"><span data-stu-id="48ae9-139">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="48ae9-140">BindingSource 组件概述</span><span class="sxs-lookup"><span data-stu-id="48ae9-140">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
