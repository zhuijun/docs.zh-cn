---
title: 如何：在泛型 T 不是 DataRow 的位置实现 CopyToDataTable<T>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: a1427747d03f01e52f1ee7ad1fc11d47d310edbe
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590600"
---
# <a name="how-to-implement-copytodatatablet-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="e051d-102">如何：在泛型 T 不是 DataRow 的位置实现 CopyToDataTable\<T></span><span class="sxs-lookup"><span data-stu-id="e051d-102">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="e051d-103"><xref:System.Data.DataTable> 对象通常用于数据绑定。</span><span class="sxs-lookup"><span data-stu-id="e051d-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="e051d-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法接收查询结果并将数据复制到 <xref:System.Data.DataTable> 中，后者随后会使用该数据进行数据绑定。</span><span class="sxs-lookup"><span data-stu-id="e051d-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="e051d-105">但是，只在 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 源上执行 <xref:System.Collections.Generic.IEnumerable%601> 方法，其中泛型参数 `T` 的类型为 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="e051d-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e051d-106">虽然这十分有用，但是它并不允许从标量类型的序列、投影匿名类型的查询或执行表联接的查询创建表。</span><span class="sxs-lookup"><span data-stu-id="e051d-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="e051d-107">此主题描述如何实现两个自定义的 `CopyToDataTable<T>` 扩展方法，其接受类型不是 `T` 的泛型参数 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="e051d-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e051d-108">从 <xref:System.Data.DataTable> 源创建 <xref:System.Collections.Generic.IEnumerable%601> 的逻辑包含在 `ObjectShredder<T>` 类中，该类稍后被包装在两个重载的 `CopyToDataTable<T>` 扩展方法中。</span><span class="sxs-lookup"><span data-stu-id="e051d-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="e051d-109">`Shred` 类的 `ObjectShredder<T>` 方法返回填充的 <xref:System.Data.DataTable> 并接受三个输入参数：一个 <xref:System.Collections.Generic.IEnumerable%601> 源、一个 <xref:System.Data.DataTable> 和一个 <xref:System.Data.LoadOption> 枚举。</span><span class="sxs-lookup"><span data-stu-id="e051d-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="e051d-110">返回的 <xref:System.Data.DataTable> 的初始架构是以类型为 `T` 的架构为基础的。</span><span class="sxs-lookup"><span data-stu-id="e051d-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="e051d-111">如果现有表作为输入提供，则该架构必须与类型为 `T` 的架构一致。</span><span class="sxs-lookup"><span data-stu-id="e051d-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="e051d-112">每个公共属性和类型为 `T` 的字段将转换为返回的表中的 <xref:System.Data.DataColumn>。</span><span class="sxs-lookup"><span data-stu-id="e051d-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="e051d-113">如果源序列包含从 `T` 派生的类型，则为任何其他公共属性或字段扩展返回的表的架构。</span><span class="sxs-lookup"><span data-stu-id="e051d-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="e051d-114">有关使用自定义 `CopyToDataTable<T>` 方法的示例，请参阅[从查询创建数据表](creating-a-datatable-from-a-query-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="e051d-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="e051d-115">\<T>在应用程序中实现自定义 CopyToDataTable 方法</span><span class="sxs-lookup"><span data-stu-id="e051d-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1. <span data-ttu-id="e051d-116">实现 `ObjectShredder<T>` 类，以从下面的 <xref:System.Data.DataTable> 源创建 <xref:System.Collections.Generic.IEnumerable%601>：</span><span class="sxs-lookup"><span data-stu-id="e051d-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  

    <span data-ttu-id="e051d-117">前面的示例假定的属性和字段 `DataColumn` 不能为 null 值类型。</span><span class="sxs-lookup"><span data-stu-id="e051d-117">The preceding example assumes that the properties and fields of the `DataColumn` are not nullable value types.</span></span> <span data-ttu-id="e051d-118">若要处理具有可为 null 的值类型的属性和字段，请使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="e051d-118">To handle properties and fields with nullable value types, use the following code:</span></span>

    ```csharp
    // Nullable-aware code for properties.
    DataColumn dc = table.Columns.Contains(p.Name) ? table.Columns[p.Name] : table.Columns.Add(p.Name, Nullable.GetUnderlyingType(p.PropertyType) ?? p.PropertyType);

    // Nullable-aware code for fields.
    DataColumn dc = table.Columns.Contains(f.Name) ? table.Columns[f.Name] : table.Columns.Add(f.Name, Nullable.GetUnderlyingType(f.FieldType) ?? f.FieldType);
    ```

2. <span data-ttu-id="e051d-119">在下面类中实现自定义 `CopyToDataTable<T>` 扩展方法：</span><span class="sxs-lookup"><span data-stu-id="e051d-119">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3. <span data-ttu-id="e051d-120">在应用程序中添加 `ObjectShredder<T>` 类和 `CopyToDataTable<T>` 扩展方法。</span><span class="sxs-lookup"><span data-stu-id="e051d-120">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="e051d-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e051d-121">See also</span></span>

- [<span data-ttu-id="e051d-122">从查询创建数据表</span><span class="sxs-lookup"><span data-stu-id="e051d-122">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)
- [<span data-ttu-id="e051d-123">编程指南</span><span class="sxs-lookup"><span data-stu-id="e051d-123">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
