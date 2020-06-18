---
title: 如何：创建 MDI 子窗体
description: 了解如何使用 Visual Studio 创建多文档界面（MDI）子窗体，以显示 RichTextBox 控件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903176"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="74eee-103">如何：创建 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="74eee-103">How to: Create MDI child forms</span></span>

<span data-ttu-id="74eee-104">MDI 子窗体是[多文档界面（MDI）应用程序](multiple-document-interface-mdi-applications.md)的基本元素，因为这些形式是用户交互的中心。</span><span class="sxs-lookup"><span data-stu-id="74eee-104">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="74eee-105">在下面的过程中，你将使用 Visual Studio 创建显示控件的 MDI 子窗体，该窗体 <xref:System.Windows.Forms.RichTextBox> 类似于大多数字处理应用程序。</span><span class="sxs-lookup"><span data-stu-id="74eee-105">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="74eee-106">通过将控件替换为 <xref:System.Windows.Forms> 其他控件（如控件或控件的组合）， <xref:System.Windows.Forms.DataGridView> 您可以创建 mdi 子窗口（以及通过扩展的 mdi 应用程序），并且可能会有多种可能性。</span><span class="sxs-lookup"><span data-stu-id="74eee-106">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="74eee-107">创建 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="74eee-107">Create MDI child forms</span></span>

1. <span data-ttu-id="74eee-108">在 Visual Studio 中创建新的 Windows 窗体应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="74eee-108">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="74eee-109">在窗体的 "**属性**" 窗口中，将其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 属性设置为，并将 `true` 其属性设置 `WindowsState` 为 `Maximized` 。</span><span class="sxs-lookup"><span data-stu-id="74eee-109">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="74eee-110">这将该表单指定为适合子窗口的 MDI 容器。</span><span class="sxs-lookup"><span data-stu-id="74eee-110">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="74eee-111">将 <xref:System.Windows.Forms.MenuStrip> 控件从 `Toolbox` 中拖到窗体上。</span><span class="sxs-lookup"><span data-stu-id="74eee-111">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="74eee-112">将其 `Text` 属性设置为 " **File**"。</span><span class="sxs-lookup"><span data-stu-id="74eee-112">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="74eee-113">单击 " **Items** " 属性旁边的省略号（...），然后单击 "**添加**" 以添加两个子工具栏菜单项。</span><span class="sxs-lookup"><span data-stu-id="74eee-113">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="74eee-114">将 `Text` 这些项的属性设置为 "**新建**" 和 "**窗口**"。</span><span class="sxs-lookup"><span data-stu-id="74eee-114">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="74eee-115">在“解决方案资源管理器”中，右键单击项目，然后选择“添加” > “新项”。</span><span class="sxs-lookup"><span data-stu-id="74eee-115">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="74eee-116">在 "**添加新项**" 对话框中，从 "**模板**" 窗格中选择**Windows 窗体**（在 Visual Basic 或 Visual c # 中）或**Windows 窗体应用程序（.net）** （在 Visual C++ 中）。</span><span class="sxs-lookup"><span data-stu-id="74eee-116">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="74eee-117">在 "**名称**" 框中，将窗体命名为**Form2**。</span><span class="sxs-lookup"><span data-stu-id="74eee-117">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="74eee-118">选择 "**打开**"，将窗体添加到项目。</span><span class="sxs-lookup"><span data-stu-id="74eee-118">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="74eee-119">在此步骤中创建的 MDI 子窗体是标准的 Windows 窗体。</span><span class="sxs-lookup"><span data-stu-id="74eee-119">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="74eee-120">因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 属性，该属性允许你控制窗体的透明度。</span><span class="sxs-lookup"><span data-stu-id="74eee-120">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="74eee-121">但是，<xref:System.Windows.Forms.Form.Opacity%2A> 属性旨在用于顶级窗口。</span><span class="sxs-lookup"><span data-stu-id="74eee-121">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="74eee-122">不要将其与 MDI 子窗体同时使用，否则可能会引起绘制问题。</span><span class="sxs-lookup"><span data-stu-id="74eee-122">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="74eee-123">此窗体将作为 MDI 子窗体的模板。</span><span class="sxs-lookup"><span data-stu-id="74eee-123">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="74eee-124">**Windows 窗体设计器**随即打开，并显示**Form2**。</span><span class="sxs-lookup"><span data-stu-id="74eee-124">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="74eee-125">从 "**工具箱**" 中，将 " **RichTextBox** " 控件拖到窗体上。</span><span class="sxs-lookup"><span data-stu-id="74eee-125">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="74eee-126">在 "**属性**" 窗口中，将 `Anchor` 属性设置为**Top，Left** ，并将 `Dock` 属性设置为 " **Fill**"。</span><span class="sxs-lookup"><span data-stu-id="74eee-126">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="74eee-127">这导致即使在调整 MDI 子窗体的大小，<xref:System.Windows.Forms.RichTextBox> 控件也会完全填充该窗体的区域。</span><span class="sxs-lookup"><span data-stu-id="74eee-127">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="74eee-128">双击 "**新建**" 菜单项为其创建 <xref:System.Windows.Forms.Control.Click> 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="74eee-128">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="74eee-129">插入类似于下面的代码，以便在用户单击 "**新建**" 菜单项时创建新的 MDI 子窗体。</span><span class="sxs-lookup"><span data-stu-id="74eee-129">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="74eee-130">在下面的示例中，事件处理程序处理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="74eee-130">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="74eee-131">请注意，根据您的应用程序体系结构的具体情况，您的**新**菜单项可能不是 `MenuItem2` 。</span><span class="sxs-lookup"><span data-stu-id="74eee-131">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   <span data-ttu-id="74eee-132">在 c + + 中，在 Form1 的顶部添加以下 `#include` 指令：</span><span class="sxs-lookup"><span data-stu-id="74eee-132">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="74eee-133">在 "**属性**" 窗口顶部的下拉列表中，选择与 "**文件**" 菜单条对应的菜单条，并将 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 属性设置为窗口 <xref:System.Windows.Forms.ToolStripMenuItem> 。</span><span class="sxs-lookup"><span data-stu-id="74eee-133">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="74eee-134">这使 "**窗口**" 菜单能够维护打开的 MDI 子窗口的列表（活动子窗口旁有一个复选标记）。</span><span class="sxs-lookup"><span data-stu-id="74eee-134">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="74eee-135">按 **F5** 运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="74eee-135">Press **F5** to run the application.</span></span> <span data-ttu-id="74eee-136">通过从 "**文件**" 菜单中选择 "**新建**"，可以创建新的 MDI 子窗体，它们将在 "**窗口**" 菜单项中保持跟踪。</span><span class="sxs-lookup"><span data-stu-id="74eee-136">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="74eee-137">当 MDI 子窗体具有一个 <xref:System.Windows.Forms.MainMenu> 组件（通常带有菜单项的菜单结构），而且它在有 <xref:System.Windows.Forms.MainMenu> 组件（通常带有菜单项的菜单结构）的 MDI 父窗体中打开时，如果设置了 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 属性（或 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 属性），这些菜单项就会自动合并。</span><span class="sxs-lookup"><span data-stu-id="74eee-137">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="74eee-138">将两个 <xref:System.Windows.Forms.MainMenu> 组件的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 属性和子窗体的所有菜单项设置为 <xref:System.Windows.Forms.MenuMerge.MergeItems>。</span><span class="sxs-lookup"><span data-stu-id="74eee-138">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="74eee-139">此外，设置 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 属性，以便这两个菜单的菜单项按所需顺序显示。</span><span class="sxs-lookup"><span data-stu-id="74eee-139">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="74eee-140">此外，请记住，关闭 MDI 父窗体时，每个 MDI 子窗体先引发一个 <xref:System.Windows.Forms.Form.Closing> 事件，再引发 MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件。</span><span class="sxs-lookup"><span data-stu-id="74eee-140">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="74eee-141">取消 MDI 子窗体的 <xref:System.Windows.Forms.Form.Closing> 事件将不会阻止引发 MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件；但是，MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 参数将设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="74eee-141">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="74eee-142">通过将 <xref:System.ComponentModel.CancelEventArgs> 参数设置为 `false` 可以强制 MDI 父窗体和所有 MDI 子窗体关闭。</span><span class="sxs-lookup"><span data-stu-id="74eee-142">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="74eee-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="74eee-143">See also</span></span>

- [<span data-ttu-id="74eee-144">多文档界面 (MDI) 应用程序</span><span class="sxs-lookup"><span data-stu-id="74eee-144">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="74eee-145">如何：创建 MDI 父窗体</span><span class="sxs-lookup"><span data-stu-id="74eee-145">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="74eee-146">如何：确定活动的 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="74eee-146">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="74eee-147">如何：将数据发送到活动的 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="74eee-147">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="74eee-148">如何：排列 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="74eee-148">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
