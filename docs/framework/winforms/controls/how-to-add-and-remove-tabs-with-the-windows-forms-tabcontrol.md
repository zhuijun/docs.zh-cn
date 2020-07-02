---
title: 添加和删除 TabControl 的选项卡
description: 了解如何添加和删除带有 Windows 窗体 TabControl 控件的选项卡，其中包含两个 TabPage 控件。 通过 TabPages 属性访问这些选项卡。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 7e67d0bbc13bd7d9c8835dc6fb9b9c5c9333b8bf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618072"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="ee919-104">如何：使用 Windows 窗体 TabControl 添加和移除选项卡</span><span class="sxs-lookup"><span data-stu-id="ee919-104">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="ee919-105">默认情况下， <xref:System.Windows.Forms.TabControl> 控件包含两个 <xref:System.Windows.Forms.TabPage> 控件。</span><span class="sxs-lookup"><span data-stu-id="ee919-105">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="ee919-106">您可以通过属性访问这些选项卡 <xref:System.Windows.Forms.TabControl.TabPages%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ee919-106">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="ee919-107">以编程方式添加选项卡</span><span class="sxs-lookup"><span data-stu-id="ee919-107">To add a tab programmatically</span></span>  
  
- <span data-ttu-id="ee919-108">使用 <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> 属性的方法 <xref:System.Windows.Forms.TabControl.TabPages%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ee919-108">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="ee919-109">以编程方式删除选项卡</span><span class="sxs-lookup"><span data-stu-id="ee919-109">To remove a tab programmatically</span></span>  
  
- <span data-ttu-id="ee919-110">若要删除选定的选项卡，请使用 <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> 属性的方法 <xref:System.Windows.Forms.TabControl.TabPages%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ee919-110">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="ee919-111">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="ee919-111">-or-</span></span>  
  
- <span data-ttu-id="ee919-112">若要删除所有选项卡，请使用 <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> 属性的方法 <xref:System.Windows.Forms.TabControl.TabPages%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ee919-112">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ee919-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="ee919-113">See also</span></span>

- [<span data-ttu-id="ee919-114">TabControl 控件概述</span><span class="sxs-lookup"><span data-stu-id="ee919-114">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="ee919-115">如何：将控件添加到选项卡页</span><span class="sxs-lookup"><span data-stu-id="ee919-115">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="ee919-116">如何：禁用选项卡页</span><span class="sxs-lookup"><span data-stu-id="ee919-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="ee919-117">如何：更改 Windows 窗体 TabControl 的外观</span><span class="sxs-lookup"><span data-stu-id="ee919-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
