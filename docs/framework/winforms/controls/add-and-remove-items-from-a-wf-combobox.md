---
title: 在 ComboBox、ListBox 或 CheckedListBox 控件中添加和删除项
ms.date: 03/30/2017
description: 了解如何仅在不使用数据绑定的情况下，添加和删除 Windows 窗体 ComboBox、ListBox 和 CheckedListBox 控件。
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
ms.openlocfilehash: f3701257bbe410bf03c4c21700705e87b581bf2e
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904437"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="d1293-103">如何：在 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件中添加或移除项</span><span class="sxs-lookup"><span data-stu-id="d1293-103">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="d1293-104">可以通过多种方式将项添加到 Windows 窗体组合框、列表框或选中的列表框中，因为这些控件可以绑定到各种数据源。</span><span class="sxs-lookup"><span data-stu-id="d1293-104">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="d1293-105">不过，本主题说明最简单的方法，并且不需要数据绑定。</span><span class="sxs-lookup"><span data-stu-id="d1293-105">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="d1293-106">显示的项通常是字符串;但是，可以使用任何对象。</span><span class="sxs-lookup"><span data-stu-id="d1293-106">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="d1293-107">控件中显示的文本是由对象的方法返回的值 `ToString` 。</span><span class="sxs-lookup"><span data-stu-id="d1293-107">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="d1293-108">添加项</span><span class="sxs-lookup"><span data-stu-id="d1293-108">To add items</span></span>  
  
1. <span data-ttu-id="d1293-109">使用类的方法将字符串或对象添加到列表 `Add` `ObjectCollection` 。</span><span class="sxs-lookup"><span data-stu-id="d1293-109">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="d1293-110">使用属性引用集合 `Items` ：</span><span class="sxs-lookup"><span data-stu-id="d1293-110">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="d1293-111">或 -</span><span class="sxs-lookup"><span data-stu-id="d1293-111">or -</span></span>  
  
2. <span data-ttu-id="d1293-112">将字符串或对象插入到列表中的所需位置， `Insert` 方法如下：</span><span class="sxs-lookup"><span data-stu-id="d1293-112">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="d1293-113">或 -</span><span class="sxs-lookup"><span data-stu-id="d1293-113">or -</span></span>  
  
3. <span data-ttu-id="d1293-114">将整个数组分配给 `Items` 集合：</span><span class="sxs-lookup"><span data-stu-id="d1293-114">Assign an entire array to the `Items` collection:</span></span>  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="d1293-115">删除项</span><span class="sxs-lookup"><span data-stu-id="d1293-115">To remove an item</span></span>  
  
1. <span data-ttu-id="d1293-116">调用 `Remove` 或 `RemoveAt` 方法来删除项。</span><span class="sxs-lookup"><span data-stu-id="d1293-116">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="d1293-117">`Remove`有一个参数，该参数指定要删除的项。`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="d1293-117">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="d1293-118">删除具有指定索引号的项。</span><span class="sxs-lookup"><span data-stu-id="d1293-118">removes the item with the specified index number.</span></span>  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### <a name="to-remove-all-items"></a><span data-ttu-id="d1293-119">删除所有项</span><span class="sxs-lookup"><span data-stu-id="d1293-119">To remove all items</span></span>  
  
1. <span data-ttu-id="d1293-120">调用 `Clear` 方法可从集合中移除所有项：</span><span class="sxs-lookup"><span data-stu-id="d1293-120">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d1293-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1293-121">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="d1293-122">如何：对 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件的内容排序</span><span class="sxs-lookup"><span data-stu-id="d1293-122">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="d1293-123">何时使用 Windows 窗体 ComboBox 而非 ListBox</span><span class="sxs-lookup"><span data-stu-id="d1293-123">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="d1293-124">用于列出选项的 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="d1293-124">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
