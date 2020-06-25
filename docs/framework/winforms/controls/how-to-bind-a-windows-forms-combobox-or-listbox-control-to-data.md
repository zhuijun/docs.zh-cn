---
title: 将 ComboBox 或 ListBox 控件绑定到数据
description: 了解如何将 Windows 窗体 ComboBox 和 ListBox 绑定到数据，以执行浏览数据库中的数据、输入新数据或编辑现有数据等任务。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 0c07dc90ddc91061c5f34b5a237082cb444e89d9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324071"
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>如何：将 Windows 窗体 ComboBox 控件或 ListBox 控件绑定到数据
您可以将和绑定到 <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ListBox> 数据来执行任务，例如，在数据库中浏览数据、输入新数据或编辑现有数据。  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>绑定 ComboBox 或 ListBox 控件  
  
1. 将 `DataSource` 属性设置为数据源对象。 可能的数据源包括 <xref:System.Windows.Forms.BindingSource> 绑定到数据、数据表、数据视图、数据集、数据视图管理器、数组或实现接口的任何类 <xref:System.Collections.IList> 。 有关详细信息，请参阅[Windows 窗体支持的数据源](../data-sources-supported-by-windows-forms.md)。  
  
2. 如果要绑定到表，请将属性设置 `DisplayMember` 为数据源中的列的名称。  
  
     \- 或 -  
  
     如果要绑定到 <xref:System.Collections.IList> ，请在列表中将显示成员设置为该类型的公共属性。  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    > 如果绑定到不实现接口的数据源（ <xref:System.ComponentModel.IBindingList> 例如 <xref:System.Collections.ArrayList> ），则在更新数据源时，将不会更新绑定控件的数据。 例如，如果您有一个绑定到的组合框， <xref:System.Collections.ArrayList> 并且数据已添加到 <xref:System.Collections.ArrayList> ，则这些新项将不会出现在组合框中。 但是，您可以通过 <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> 在控件绑定到的类的实例上调用和方法来强制更新组合框 <xref:System.Windows.Forms.BindingContext> 。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [Windows 窗体数据绑定](../windows-forms-data-binding.md)
- [数据绑定和 Windows 窗体](../data-binding-and-windows-forms.md)
- [用于列出选项的 Windows 窗体控件](windows-forms-controls-used-to-list-options.md)
