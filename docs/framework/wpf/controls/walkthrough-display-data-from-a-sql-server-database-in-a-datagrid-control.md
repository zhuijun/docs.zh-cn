---
title: 演练：在 DataGrid 控件中显示 SQL Server 数据库中的数据
description: 了解如何使用本演练从 SQL Server 数据库中获取数据，并将其显示在 Windows Presentation Foundation DataGrid 控件中。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: cc41979c869021c9c363f3f68ce590d4702e068c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167548"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>演练：在 DataGrid 控件中显示 SQL Server 数据库中的数据

在本演练中，您将从 SQL Server 数据库中检索数据，并在控件中显示这些数据 <xref:System.Windows.Controls.DataGrid> 。 使用 ADO.NET 实体框架创建表示数据的实体类，并使用 LINQ 编写从实体类中检索指定数据的查询。

## <a name="prerequisites"></a>先决条件

您需要满足以下条件才能完成本演练：

- Visual Studio。

- 访问附加了 AdventureWorks 示例数据库的 SQL Server 或 SQL Server Express 的正在运行的实例。 可以从[GitHub](https://github.com/Microsoft/sql-server-samples/releases)下载 AdventureWorks 数据库。

## <a name="create-entity-classes"></a>创建实体类

1. 在 Visual Basic 或 c # 中创建一个新的 WPF 应用程序项目，然后将其命名为 `DataGridSQLExample` 。

2. 在解决方案资源管理器中，右键单击项目，指向 "**添加**"，然后选择 "**新建项**"。

     将显示“添加新项”对话框。

3. 在 "已安装的模板" 窗格中，选择 "**数据**"，然后在模板列表中，选择 " **ADO.NET 实体数据模型**"。

     ![ADO.NET 实体数据模型项模板](../../wcf/feature-details/media/ado-net-entity-data-model-item-template.png)

4. 命名该文件 `AdventureWorksModel.edmx` ，然后单击 "**添加**"。

     此时将显示实体数据模型向导。

5. 在 "选择模型内容" 屏幕上，**从数据库中选择 EF 设计器**，然后单击 "**下一步**"。

6. 在 "选择你的数据连接" 屏幕中，提供与 AdventureWorksLT2008 数据库的连接。 有关详细信息，请参阅 "[选择您的数据连接" 对话框](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100))。

    请确保已选中 "名称" `AdventureWorksLT2008Entities` 和 "**将 App.Config 中的存储实体连接设置**" 复选框，然后单击 "**下一步**"。

7. 在 "选择数据库对象" 屏幕上，展开 "表" 节点，然后选择 " **Product** " 和 " **ProductCategory** " 表。

     您可以为所有表生成实体类;但是，在此示例中，只检索这两个表中的数据。

     ![从表中选择 Product 和 ProductCategory](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. 单击“完成”。

     "产品" 和 "ProductCategory" 实体将显示在 Entity Designer 中。

     ![Product 和 ProductCategory 实体模型](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>检索和显示数据

1. 打开 Mainwindow.xaml 文件。

2. 将 <xref:System.Windows.FrameworkElement.Width%2A> 的属性设置 <xref:System.Windows.Window> 为450。

3. 在 XAML 编辑器中，在 <xref:System.Windows.Controls.DataGrid> 和标记之间添加以下标记， `<Grid>` `</Grid>` 以添加一个 <xref:System.Windows.Controls.DataGrid> 名为的 `dataGrid1` 。

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![含 DataGrid 的窗口](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. 选择 <xref:System.Windows.Window>。

5. 使用属性窗口或 XAML 编辑器，为事件指定的事件处理程序 <xref:System.Windows.Window> `Window_Loaded` <xref:System.Windows.FrameworkElement.Loaded> 。 有关详细信息，请参阅[如何：创建简单的事件处理程序](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。

     下面显示了 Mainwindow.xaml 的 XAML。

    > [!NOTE]
    > 如果使用 Visual Basic，请在 Mainwindow.xaml 的第一行中将替换 `x:Class="DataGridSQLExample.MainWindow"` 为 `x:Class="MainWindow"` 。

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. 打开的代码隐藏文件（Mainwindow.xaml 或 MainWindow.xaml.cs） <xref:System.Windows.Window> 。

7. 添加以下代码以仅检索联接的表中的特定值，并将 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 的属性设置 <xref:System.Windows.Controls.DataGrid> 为查询的结果。

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. 运行示例。

     应该会看到一个 <xref:System.Windows.Controls.DataGrid> 显示数据的。

     ![带有来自 SQL 数据库的数据的 DataGrid](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.DataGrid>
