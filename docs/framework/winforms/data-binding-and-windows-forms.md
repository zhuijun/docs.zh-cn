---
title: 数据绑定
description: 了解如何绑定到在运行时计算的值数组、从文件中读取数据，或者从 Windows 窗体中的其他控件的值派生。
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- data [Windows Forms], data binding
- reports [Windows Forms], Windows Forms
- lookup tables [Windows Forms], data binding
- data [Windows Forms], complex data binding
- data binding [Windows Forms], Windows Forms
- data [Windows Forms], simple data binding
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: 419aac5e-819b-4aad-88b0-73a2f8c0bd27
ms.openlocfilehash: 78e8a3287c565cfa7dae56b68c0eb57f48c30ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619658"
---
# <a name="data-binding-and-windows-forms"></a>数据绑定和 Windows 窗体
在 Windows 窗体中，你不仅可以绑定到传统的数据源，还可以绑定到几乎任何包含数据的结构。 可以绑定到你在运行时、从文件读取时或从其他控件的值派生时计算的一数组值。  
  
 此外，你可将任何控件的任何属性绑定到数据源。 在传统数据绑定中，你通常将显示属性（例如 <xref:System.Windows.Forms.Control.Text%2A> 控件的 <xref:System.Windows.Forms.TextBox> 属性）绑定到数据源。 使用 .NET Framework，还可以选择通过绑定设置其他属性。 你可以使用绑定来执行以下任务：  
  
- 设置图像控件的图形。  
  
- 设置一个或多个控件的背景色。  
  
- 设置控件的大小。  
  
 从根本上讲，数据绑定是一种设置窗体上任何控件的任何运行时可访问属性的自动方法。  
  
## <a name="types-of-data-binding"></a>数据绑定的类型  
 Windows 窗体可以利用两种类型的数据绑定：简单绑定和复杂绑定。 每一种都有不同的优势。  
  
|数据绑定的类型|描述|  
|--------------------------|-----------------|  
|简单数据绑定|控件绑定到单个数据元素（如数据集表的列中的值）的能力。 对于诸如 <xref:System.Windows.Forms.TextBox> 控件或 <xref:System.Windows.Forms.Label> 控件的控件，即通常只显示单个值的控件，通常使用这种绑定。 事实上，控件上的任何属性都可以绑定到数据库中的字段。 Visual Studio 中提供了此功能的广泛支持。<br /><br /> 有关详情，请参阅：<br /><br /> -   [与数据绑定相关的接口](interfaces-related-to-data-binding.md)<br />-   [如何：在 Windows 窗体中导航数据](how-to-navigate-data-in-windows-forms.md)<br />-   [如何：在 Windows 窗体上创建简单绑定控件](how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|复杂数据绑定|控件绑定一个以上数据元素（通常为一个数据库中的一个以上的记录）的能力。 复杂绑定也称基于列表的绑定。 支持复杂绑定的控件示例为 <xref:System.Windows.Forms.DataGridView>、<xref:System.Windows.Forms.ListBox> 和 <xref:System.Windows.Forms.ComboBox> 控件。 有关复杂数据绑定的示例，请参阅[如何：将 Windows 窗体 ComboBox 或 ListBox 控件绑定到数据](./controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)。|  
  
## <a name="bindingsource-component"></a>BindingSource 组件  
 为了简化数据绑定，Windows 窗体让你可将数据源绑定到 <xref:System.Windows.Forms.BindingSource> 组件，然后将控件绑定到 <xref:System.Windows.Forms.BindingSource>。 你可以在简单或复杂绑定方案中使用 <xref:System.Windows.Forms.BindingSource>。 在任一种情况下，<xref:System.Windows.Forms.BindingSource> 均充当数据源和绑定控件的中介，提供更改通知货币管理和其他服务。  
  
## <a name="common-scenarios-that-employ-data-binding"></a>采用数据绑定的常见方案  
 几乎每个商业应用程序都使用读取自一种类型或另一种类型的数据源的信息，方法通常是数据绑定。 以下列表显示了几个最常见的利用数据绑定作为数据表示和操作方法的方案。  
  
|方案|说明|  
|--------------|-----------------|  
|报表|报表为你提供了一种灵活的方式来显示和汇总打印出的文档中的数据。 一种很常见的做法是：创建一个将数据源的选定内容打印到屏幕或打印机的报表。 常见的报表包括列表、发票和摘要。 通常将项格式化成列表的列，在每个列表项下组织子项，但你应选择最适合数据的布局。|  
|数据输入|输入大量相关数据或提示用户输入信息的常用方法是使用数据输入表单。 用户可以使用文本框、选项按钮、下拉列表和复选框来输入信息或选择选项。 然后提交信息并将其存储在数据库中，数据库结构基于所输入的信息。|  
|大纲/细节关系|大纲/细节应用程序是查看相关数据的一种格式。 具体来说，有两个彼此间有关系的数据表 — 在经典商业示例中，“顾客”表和“订单”表之间存在联系客户和对应订单的关系。 有关使用两个 Windows 窗体控件创建主/详细应用程序的详细信息 <xref:System.Windows.Forms.DataGridView> ，请参阅[如何：使用两个 Windows 窗体 DataGridView 控件创建主窗体/详细信息窗体](./controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|查找表|另一个常见的数据表示/操作方案是表查找。 通常情况下，作为较大数据显示的一部分，<xref:System.Windows.Forms.ComboBox> 控件用于显示和操作数据。 关键在于 <xref:System.Windows.Forms.ComboBox> 控件中显示的数据与写入数据库中的数据不同。 例如，如果你有一个显示杂货店中的物料的 <xref:System.Windows.Forms.ComboBox> 控件，你可能想要查看产品名称（面包、牛奶、鸡蛋）。 但是，为了便于在数据库中检索信息或使数据库标准化，你可能会将给定订单特定项的信息存储为物料编号（#501、#603 等等）。 因此，你窗体上的 <xref:System.Windows.Forms.ComboBox> 控件中的杂货物料“友好名称”和存在于订单中的物料编号间有着隐式联系。 这就是表查找的实质。 有关详细信息，请参阅[如何：使用 Windows 窗体 BindingSource 组件创建查找表](./controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md)。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Binding>
- [Windows 窗体数据绑定](windows-forms-data-binding.md)
- [如何：将 Windows 窗体 DataGrid 控件绑定到数据源](./controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [BindingSource 组件](./controls/bindingsource-component.md)
