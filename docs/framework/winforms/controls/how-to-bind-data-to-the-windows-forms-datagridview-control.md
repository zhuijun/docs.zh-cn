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
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="30743-103">如何：将数据绑定到 Windows 窗体 DataGridView 控件</span><span class="sxs-lookup"><span data-stu-id="30743-103">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="30743-104"><xref:System.Windows.Forms.DataGridView>控件支持标准 Windows 窗体数据绑定模型，因此它可以绑定到各种数据源。</span><span class="sxs-lookup"><span data-stu-id="30743-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="30743-105">通常，您绑定到 <xref:System.Windows.Forms.BindingSource> 管理与数据源的交互的。</span><span class="sxs-lookup"><span data-stu-id="30743-105">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="30743-106"><xref:System.Windows.Forms.BindingSource>可以是任何 Windows 窗体数据源，在选择或修改数据位置时，这为你提供了极大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="30743-106">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="30743-107">有关控件支持的数据源的详细信息 <xref:System.Windows.Forms.DataGridView> ，请参阅[DataGridView 控件概述](datagridview-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="30743-107">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="30743-108">Visual Studio 提供对 DataGridView 控件数据绑定的广泛支持。</span><span class="sxs-lookup"><span data-stu-id="30743-108">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="30743-109">有关详细信息，请参阅[如何：使用设计器将数据绑定到 Windows 窗体 DataGridView 控件](bind-data-to-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="30743-109">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="30743-110">将 DataGridView 控件连接到数据：</span><span class="sxs-lookup"><span data-stu-id="30743-110">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="30743-111">实现方法以处理有关检索数据的详细信息。</span><span class="sxs-lookup"><span data-stu-id="30743-111">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="30743-112">下面的代码示例实现了一个 `GetData` 初始化的方法 <xref:System.Data.SqlClient.SqlDataAdapter> ，并使用它来填充 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="30743-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="30743-113">然后，它将绑定 <xref:System.Data.DataTable> 到 <xref:System.Windows.Forms.BindingSource> 。</span><span class="sxs-lookup"><span data-stu-id="30743-113">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="30743-114">在窗体的 <xref:System.Windows.Forms.Form.Load> 事件处理程序中，将 <xref:System.Windows.Forms.DataGridView> 控件绑定到 <xref:System.Windows.Forms.BindingSource> ，然后调用 `GetData` 方法来检索数据。</span><span class="sxs-lookup"><span data-stu-id="30743-114">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="30743-115">示例</span><span class="sxs-lookup"><span data-stu-id="30743-115">Example</span></span>

<span data-ttu-id="30743-116">此完整的代码示例从数据库中检索数据，以在 Windows 窗体中填充 DataGridView 控件。</span><span class="sxs-lookup"><span data-stu-id="30743-116">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="30743-117">窗体还具有用于重新加载数据并将更改提交到数据库的按钮。</span><span class="sxs-lookup"><span data-stu-id="30743-117">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="30743-118">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="30743-118">This example requires:</span></span>

- <span data-ttu-id="30743-119">访问 Northwind SQL Server 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="30743-119">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="30743-120">有关安装 Northwind 示例数据库的详细信息，请参阅[获取用于 ADO.NET 代码示例的示例数据库](../../data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="30743-120">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="30743-121">对系统、System.web、System.web 和 System.Xml 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="30743-121">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="30743-122">若要生成并运行此示例，请将代码粘贴到新 Windows 窗体项目中的*Form1*代码文件中。</span><span class="sxs-lookup"><span data-stu-id="30743-122">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="30743-123">有关从 c # 或 Visual Basic 命令行生成的信息，请参阅[通过 csc.exe生成命令](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)行或[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="30743-123">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="30743-124">`connectionString`用 Northwind SQL Server 示例数据库连接的值填充示例中的变量。</span><span class="sxs-lookup"><span data-stu-id="30743-124">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="30743-125">Windows 身份验证（也称为集成安全性）是连接到数据库比在连接字符串中存储密码更为安全的方式。</span><span class="sxs-lookup"><span data-stu-id="30743-125">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="30743-126">有关连接安全的详细信息，请参阅[保护连接信息](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="30743-126">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="30743-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30743-127">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="30743-128">在 Windows 窗体 DataGridView 控件中显示数据</span><span class="sxs-lookup"><span data-stu-id="30743-128">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="30743-129">保护连接信息</span><span class="sxs-lookup"><span data-stu-id="30743-129">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
