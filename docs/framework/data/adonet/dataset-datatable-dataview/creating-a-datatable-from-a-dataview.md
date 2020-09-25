---
title: 从数据视图中创建数据表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d45cf41-d8ae-4409-af3e-a96a7e476d85
ms.openlocfilehash: 42843ec40f4f7271526e341dc53bdbc2ef11db38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198725"
---
# <a name="creating-a-datatable-from-a-dataview"></a><span data-ttu-id="c7719-102">从数据视图中创建数据表</span><span class="sxs-lookup"><span data-stu-id="c7719-102">Creating a DataTable from a DataView</span></span>

<span data-ttu-id="c7719-103">如果从数据源检索到数据，并且使用该数据填充了 <xref:System.Data.DataTable>，则在可能需要对返回的数据进行排序和筛选，或者通过其他方式限制返回的数据时，不必重新检索该数据。</span><span class="sxs-lookup"><span data-stu-id="c7719-103">Once you have retrieved data from a data source, and have filled a <xref:System.Data.DataTable> with the data, you may want to sort, filter, or otherwise limit the returned data without retrieving it again.</span></span> <span data-ttu-id="c7719-104"><xref:System.Data.DataView> 类可以实现此目的。</span><span class="sxs-lookup"><span data-stu-id="c7719-104">The <xref:System.Data.DataView> class makes this possible.</span></span> <span data-ttu-id="c7719-105">此外，如果需要从创建新的 <xref:System.Data.DataTable> <xref:System.Data.DataView> ，可以使用 <xref:System.Data.DataView.ToTable%2A> 方法将所有行和列或者数据的一个子集复制到新的中 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="c7719-105">In addition, if you need to create a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView>, you can use the <xref:System.Data.DataView.ToTable%2A> method to copy all the rows and columns, or a subset of the data into a new <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c7719-106"><xref:System.Data.DataView.ToTable%2A> 方法使您可以：</span><span class="sxs-lookup"><span data-stu-id="c7719-106">The <xref:System.Data.DataView.ToTable%2A> method provides overloads to:</span></span>  
  
- <span data-ttu-id="c7719-107">创建一个 <xref:System.Data.DataTable>，包含属于 <xref:System.Data.DataView> 中的一个列子集。</span><span class="sxs-lookup"><span data-stu-id="c7719-107">Create a <xref:System.Data.DataTable> containing columns that are a subset of the columns in the <xref:System.Data.DataView>.</span></span>  
  
- <span data-ttu-id="c7719-108">创建一个， <xref:System.Data.DataTable> 其中仅包含中的非重复行 <xref:System.Data.DataView> ，类似到 transact-sql 中的 distinct 关键字。</span><span class="sxs-lookup"><span data-stu-id="c7719-108">Create a <xref:System.Data.DataTable> that includes only distinct rows from the <xref:System.Data.DataView>, analogously to the DISTINCT keyword in Transact-SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7719-109">示例</span><span class="sxs-lookup"><span data-stu-id="c7719-109">Example</span></span>  

 <span data-ttu-id="c7719-110">下面的控制台应用程序示例创建一个 <xref:System.Data.DataTable> ，它包含**AdventureWorks**示例数据库中的**Person**表中的数据。</span><span class="sxs-lookup"><span data-stu-id="c7719-110">The following console application example creates a <xref:System.Data.DataTable> that contains data from the **Person.Contact** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="c7719-111">接下来，该示例基于创建一个经过排序和筛选的 <xref:System.Data.DataView> <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="c7719-111">Next, the example creates a sorted and filtered <xref:System.Data.DataView> based on the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c7719-112">在显示和的内容之后 <xref:System.Data.DataTable> <xref:System.Data.DataView> ，该示例 <xref:System.Data.DataTable> 通过调用方法，从创建一个新的 <xref:System.Data.DataView> <xref:System.Data.DataView.ToTable%2A> ，仅选择可用列的子集。</span><span class="sxs-lookup"><span data-stu-id="c7719-112">After displaying the contents of the <xref:System.Data.DataTable> and the <xref:System.Data.DataView>, the example creates a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView> by calling the <xref:System.Data.DataView.ToTable%2A> method, selecting only a subset of the available columns.</span></span> <span data-ttu-id="c7719-113">最后，该示例显示新的 <xref:System.Data.DataTable> 的内容。</span><span class="sxs-lookup"><span data-stu-id="c7719-113">Finally, the example displays the contents of the new <xref:System.Data.DataTable>.</span></span>  
  
```vb  
Private Sub DemonstrateDataView()  
    ' Retrieve a DataTable from the AdventureWorks sample database.  
    ' connectionString is assumed to be a valid connection string.  
    Dim adapter As New SqlDataAdapter( _  
       "SELECT FirstName, LastName, EmailAddress FROM Person.Contact WHERE FirstName LIKE 'Mich%'", connectionString)  
    Dim table As New DataTable  
  
    adapter.Fill(table)  
    Console.WriteLine("Original table name: " & table.TableName)  
    ' Print current table values.  
    PrintTableOrView(table, "Current Values in Table")  
  
    ' Now create a DataView based on the DataTable.  
    ' Sort and filter the data.  
    Dim view As DataView = table.DefaultView  
    view.Sort = "LastName, FirstName"  
    view.RowFilter = "LastName > 'M'"  
    PrintTableOrView(view, "Current Values in View")  
  
    ' Create a new DataTable based on the DataView,  
    ' requesting only two columns with distinct values  
    ' in the columns.  
    Dim newTable As DataTable = view.ToTable("UniqueLastNames", True, "FirstName", "LastName")  
    PrintTableOrView(newTable, "Table created from DataView")  
    Console.WriteLine("New table name: " & newTable.TableName)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
    End Sub  
  
Private Sub PrintTableOrView(ByVal dv As DataView, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
    Dim table As DataTable = dv.Table  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the view.  
    For Each rowView As DataRowView In dv  
        sw = New System.IO.StringWriter  
  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(rowView(col.ColumnName).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
End Sub  
  
Private Sub PrintTableOrView(ByVal table As DataTable, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the table.  
    For Each row As DataRow In table.Rows  
        sw = New System.IO.StringWriter  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(row(col).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
    End Sub  
End Module  
```  
  
```csharp  
private static void DemonstrateDataView()  
{  
// Retrieve a DataTable from the AdventureWorks sample database.  
// connectionString is assumed to be a valid connection string.  
SqlDataAdapter adapter = new SqlDataAdapter(  
    "SELECT FirstName, LastName, EmailAddress " +  
    "FROM Person.Contact WHERE FirstName LIKE 'Mich%'",
       GetConnectionString());  
DataTable table = new DataTable();  
  
adapter.Fill(table);  
Console.WriteLine("Original table name: " + table.TableName);  
// Print current table values.  
PrintTableOrView(table, "Current Values in Table");  
  
// Now create a DataView based on the DataTable.  
// Sort and filter the data.  
DataView view = table.DefaultView;  
view.Sort = "LastName, FirstName";  
view.RowFilter = "LastName > 'M'";  
PrintTableOrView(view, "Current Values in View");  
  
// Create a new DataTable based on the DataView,  
// requesting only two columns with distinct values  
// in the columns.  
DataTable newTable = view.ToTable("UniqueLastNames",  
     true, "FirstName", "LastName");  
PrintTableOrView(newTable, "Table created from DataView");  
Console.WriteLine("New table name: " + newTable.TableName);  
  
Console.WriteLine("Press any key to continue.");  
Console.ReadKey();  
}  
  
private static void PrintTableOrView(DataView dv, string label)  
{  
System.IO.StringWriter sw;  
string output;  
DataTable table = dv.Table;  
  
Console.WriteLine(label);  
  
// Loop through each row in the view.  
foreach (DataRowView rowView in dv)  
{  
    sw = new System.IO.StringWriter();  
  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(rowView[col.ColumnName].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
}  
Console.WriteLine();  
}  
  
private static void PrintTableOrView(DataTable table, string label)  
{  
System.IO.StringWriter sw;  
string output;  
  
Console.WriteLine(label);  
  
// Loop through each row in the table.  
foreach (DataRow row in table.Rows)  
{  
    sw = new System.IO.StringWriter();  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(row[col].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
} //  
Console.WriteLine();  
}  
```  
  
 <span data-ttu-id="c7719-114">}</span><span class="sxs-lookup"><span data-stu-id="c7719-114">}</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7719-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="c7719-115">See also</span></span>

- <xref:System.Data.DataView.ToTable%2A>
- [<span data-ttu-id="c7719-116">DataView</span><span class="sxs-lookup"><span data-stu-id="c7719-116">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="c7719-117">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="c7719-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
