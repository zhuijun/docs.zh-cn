---
title: 将数据绑定到 DataGridView 控件
ms.date: 02/08/2019
description: 了解 DataGridView 控件如何支持标准 Windows 窗体数据绑定模型，以便它可以绑定到各种数据源。
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904411"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>如何：将数据绑定到 Windows 窗体 DataGridView 控件

<xref:System.Windows.Forms.DataGridView>控件支持标准 Windows 窗体数据绑定模型，因此它可以绑定到各种数据源。 通常，您绑定到 <xref:System.Windows.Forms.BindingSource> 管理与数据源的交互的。 <xref:System.Windows.Forms.BindingSource>可以是任何 Windows 窗体数据源，在选择或修改数据位置时，这为你提供了极大的灵活性。 有关控件支持的数据源的详细信息 <xref:System.Windows.Forms.DataGridView> ，请参阅[DataGridView 控件概述](datagridview-control-overview-windows-forms.md)。  

Visual Studio 提供对 DataGridView 控件数据绑定的广泛支持。 有关详细信息，请参阅[如何：使用设计器将数据绑定到 Windows 窗体 DataGridView 控件](bind-data-to-the-datagrid-using-the-designer.md)。  

将 DataGridView 控件连接到数据：

1. 实现方法以处理有关检索数据的详细信息。 下面的代码示例实现了一个 `GetData` 初始化的方法 <xref:System.Data.SqlClient.SqlDataAdapter> ，并使用它来填充 <xref:System.Data.DataTable> 。 然后，它将绑定 <xref:System.Data.DataTable> 到 <xref:System.Windows.Forms.BindingSource> 。

2. 在窗体的 <xref:System.Windows.Forms.Form.Load> 事件处理程序中，将 <xref:System.Windows.Forms.DataGridView> 控件绑定到 <xref:System.Windows.Forms.BindingSource> ，然后调用 `GetData` 方法来检索数据。  

## <a name="example"></a>示例

此完整的代码示例从数据库中检索数据，以在 Windows 窗体中填充 DataGridView 控件。 窗体还具有用于重新加载数据并将更改提交到数据库的按钮。  

此示例需要：

- 访问 Northwind SQL Server 示例数据库。 有关安装 Northwind 示例数据库的详细信息，请参阅[获取用于 ADO.NET 代码示例的示例数据库](../../data/adonet/sql/linq/downloading-sample-databases.md)。

- 对系统、System.web、System.web 和 System.Xml 程序集的引用。  

若要生成并运行此示例，请将代码粘贴到新 Windows 窗体项目中的*Form1*代码文件中。 有关从 c # 或 Visual Basic 命令行生成的信息，请参阅[通过 csc.exe生成命令](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)行或[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
`connectionString`用 Northwind SQL Server 示例数据库连接的值填充示例中的变量。 Windows 身份验证（也称为集成安全性）是连接到数据库比在连接字符串中存储密码更为安全的方式。 有关连接安全的详细信息，请参阅[保护连接信息](../../data/adonet/protecting-connection-information.md)。  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [在 Windows 窗体 DataGridView 控件中显示数据](displaying-data-in-the-windows-forms-datagridview-control.md)
- [保护连接信息](../../data/adonet/protecting-connection-information.md)
