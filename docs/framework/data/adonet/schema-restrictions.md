---
title: 架构限制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c0a3cafef45341cd95fa0a4f65c818129e120e44
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147819"
---
# <a name="schema-restrictions"></a><span data-ttu-id="c1bc6-102">架构限制</span><span class="sxs-lookup"><span data-stu-id="c1bc6-102">Schema Restrictions</span></span>

<span data-ttu-id="c1bc6-103">**GetSchema**方法的第二个可选参数是用于限制返回的架构信息量的限制，并将其作为字符串数组传递到**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="c1bc6-104">在数组中的位置确定可以传递的值，这等效于限制数。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="c1bc6-105">例如，下表说明使用适用于 SQL Server 的 .NET Framework 数据提供程序时“Tables”架构集合支持的限制。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="c1bc6-106">SQL Server 架构集合的其他限制在本主题的结尾处列出。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="c1bc6-107">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-107">Restriction Name</span></span>|<span data-ttu-id="c1bc6-108">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-108">Parameter Name</span></span>|<span data-ttu-id="c1bc6-109">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-109">Restriction Default</span></span>|<span data-ttu-id="c1bc6-110">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-111">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-111">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-112">TABLE_CATALOG</span></span>|<span data-ttu-id="c1bc6-113">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-113">1</span></span>|  
|<span data-ttu-id="c1bc6-114">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-114">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="c1bc6-116">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-116">2</span></span>|  
|<span data-ttu-id="c1bc6-117">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-117">Table</span></span>|@Name|<span data-ttu-id="c1bc6-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-118">TABLE_NAME</span></span>|<span data-ttu-id="c1bc6-119">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-119">3</span></span>|  
|<span data-ttu-id="c1bc6-120">TableType</span><span class="sxs-lookup"><span data-stu-id="c1bc6-120">TableType</span></span>|@TableType|<span data-ttu-id="c1bc6-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c1bc6-121">TABLE_TYPE</span></span>|<span data-ttu-id="c1bc6-122">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="c1bc6-123">指定限制值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-123">Specifying Restriction Values</span></span>  

 <span data-ttu-id="c1bc6-124">要使用“Tables”架构集合的一个限制，只需创建一个包含四个元素的字符串数组，然后在与限制数匹配的元素中填充值。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="c1bc6-125">例如，若要将 **GetSchema** 方法返回的表仅限制为 "sales" 架构中的表，请先将数组的第二个元素设置为 "sales"，然后再将其传递给 **GetSchema** 方法。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1bc6-126">`SqlClient` 和 `OracleClient` 的限制集合还有附加的 `ParameterName` 列。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="c1bc6-127">为了向后兼容，仍提供限制默认列，但是目前忽略该列。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="c1bc6-128">在指定限制值时，应使用参数化查询（而不是字符串替换）来最大程度地降低受到 SQL 注入式攻击的风险。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1bc6-129">数组中的元素数必须小于或等于指定架构集合支持的限制数，否则，将引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="c1bc6-130">可以小于最大限制数。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="c1bc6-131">缺少的限制假定为空（无限制）。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="c1bc6-132">可以通过将 **GetSchema** 方法与限制架构集合的名称（即 "限制"）一起调用，来 .NET Framework 查询受支持的限制列表。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="c1bc6-133">此时将返回 <xref:System.Data.DataTable>，包含集合名称、限制名称、默认限制值和限制数的列表。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c1bc6-134">示例</span><span class="sxs-lookup"><span data-stu-id="c1bc6-134">Example</span></span>  

 <span data-ttu-id="c1bc6-135">下面的示例演示如何使用 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server 类的 .NET Framework 数据提供程序的方法 <xref:System.Data.SqlClient.SqlConnection> 来检索与 **AdventureWorks** 示例数据库中包含的所有表有关的架构信息，并将返回的信息仅限于 "Sales" 架构中的表：</span><span class="sxs-lookup"><span data-stu-id="c1bc6-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="c1bc6-136">SQL Server 架构限制</span><span class="sxs-lookup"><span data-stu-id="c1bc6-136">SQL Server Schema Restrictions</span></span>  

 <span data-ttu-id="c1bc6-137">下表列出了 SQL Server 架构集合的限制。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="c1bc6-138">用户</span><span class="sxs-lookup"><span data-stu-id="c1bc6-138">Users</span></span>  
  
|<span data-ttu-id="c1bc6-139">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-139">Restriction Name</span></span>|<span data-ttu-id="c1bc6-140">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-140">Parameter Name</span></span>|<span data-ttu-id="c1bc6-141">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-141">Restriction Default</span></span>|<span data-ttu-id="c1bc6-142">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-143">User_Name</span></span>|@Name|<span data-ttu-id="c1bc6-144">name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-144">name</span></span>|<span data-ttu-id="c1bc6-145">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="c1bc6-146">数据库</span><span class="sxs-lookup"><span data-stu-id="c1bc6-146">Databases</span></span>  
  
|<span data-ttu-id="c1bc6-147">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-147">Restriction Name</span></span>|<span data-ttu-id="c1bc6-148">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-148">Parameter Name</span></span>|<span data-ttu-id="c1bc6-149">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-149">Restriction Default</span></span>|<span data-ttu-id="c1bc6-150">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-151">名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-151">Name</span></span>|@Name|<span data-ttu-id="c1bc6-152">名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-152">Name</span></span>|<span data-ttu-id="c1bc6-153">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="c1bc6-154">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-154">Tables</span></span>  
  
|<span data-ttu-id="c1bc6-155">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-155">Restriction Name</span></span>|<span data-ttu-id="c1bc6-156">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-156">Parameter Name</span></span>|<span data-ttu-id="c1bc6-157">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-157">Restriction Default</span></span>|<span data-ttu-id="c1bc6-158">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-159">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-159">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-160">TABLE_CATALOG</span></span>|<span data-ttu-id="c1bc6-161">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-161">1</span></span>|  
|<span data-ttu-id="c1bc6-162">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-162">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="c1bc6-164">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-164">2</span></span>|  
|<span data-ttu-id="c1bc6-165">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-165">Table</span></span>|@Name|<span data-ttu-id="c1bc6-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-166">TABLE_NAME</span></span>|<span data-ttu-id="c1bc6-167">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-167">3</span></span>|  
|<span data-ttu-id="c1bc6-168">TableType</span><span class="sxs-lookup"><span data-stu-id="c1bc6-168">TableType</span></span>|@TableType|<span data-ttu-id="c1bc6-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c1bc6-169">TABLE_TYPE</span></span>|<span data-ttu-id="c1bc6-170">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c1bc6-171">列</span><span class="sxs-lookup"><span data-stu-id="c1bc6-171">Columns</span></span>  
  
|<span data-ttu-id="c1bc6-172">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-172">Restriction Name</span></span>|<span data-ttu-id="c1bc6-173">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-173">Parameter Name</span></span>|<span data-ttu-id="c1bc6-174">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-174">Restriction Default</span></span>|<span data-ttu-id="c1bc6-175">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-176">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-176">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-177">TABLE_CATALOG</span></span>|<span data-ttu-id="c1bc6-178">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-178">1</span></span>|  
|<span data-ttu-id="c1bc6-179">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-179">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="c1bc6-181">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-181">2</span></span>|  
|<span data-ttu-id="c1bc6-182">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-182">Table</span></span>|@Table|<span data-ttu-id="c1bc6-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-183">TABLE_NAME</span></span>|<span data-ttu-id="c1bc6-184">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-184">3</span></span>|  
|<span data-ttu-id="c1bc6-185">列</span><span class="sxs-lookup"><span data-stu-id="c1bc6-185">Column</span></span>|@Column|<span data-ttu-id="c1bc6-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-186">COLUMN_NAME</span></span>|<span data-ttu-id="c1bc6-187">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="c1bc6-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="c1bc6-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="c1bc6-189">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-189">Restriction Name</span></span>|<span data-ttu-id="c1bc6-190">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-190">Parameter Name</span></span>|<span data-ttu-id="c1bc6-191">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-191">Restriction Default</span></span>|<span data-ttu-id="c1bc6-192">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-193">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-193">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-194">TABLE_CATALOG</span></span>|<span data-ttu-id="c1bc6-195">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-195">1</span></span>|  
|<span data-ttu-id="c1bc6-196">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-196">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="c1bc6-198">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-198">2</span></span>|  
|<span data-ttu-id="c1bc6-199">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-199">Table</span></span>|@Table|<span data-ttu-id="c1bc6-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-200">TABLE_NAME</span></span>|<span data-ttu-id="c1bc6-201">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-201">3</span></span>|  
|<span data-ttu-id="c1bc6-202">列</span><span class="sxs-lookup"><span data-stu-id="c1bc6-202">Column</span></span>|@Column|<span data-ttu-id="c1bc6-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-203">COLUMN_NAME</span></span>|<span data-ttu-id="c1bc6-204">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="c1bc6-205">视图</span><span class="sxs-lookup"><span data-stu-id="c1bc6-205">Views</span></span>  
  
|<span data-ttu-id="c1bc6-206">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-206">Restriction Name</span></span>|<span data-ttu-id="c1bc6-207">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-207">Parameter Name</span></span>|<span data-ttu-id="c1bc6-208">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-208">Restriction Default</span></span>|<span data-ttu-id="c1bc6-209">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-210">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-210">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-211">TABLE_CATALOG</span></span>|<span data-ttu-id="c1bc6-212">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-212">1</span></span>|  
|<span data-ttu-id="c1bc6-213">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-213">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="c1bc6-215">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-215">2</span></span>|  
|<span data-ttu-id="c1bc6-216">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-216">Table</span></span>|@Table|<span data-ttu-id="c1bc6-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-217">TABLE_NAME</span></span>|<span data-ttu-id="c1bc6-218">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="c1bc6-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="c1bc6-219">ViewColumns</span></span>  
  
|<span data-ttu-id="c1bc6-220">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-220">Restriction Name</span></span>|<span data-ttu-id="c1bc6-221">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-221">Parameter Name</span></span>|<span data-ttu-id="c1bc6-222">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-222">Restriction Default</span></span>|<span data-ttu-id="c1bc6-223">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-224">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-224">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-225">VIEW_CATALOG</span></span>|<span data-ttu-id="c1bc6-226">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-226">1</span></span>|  
|<span data-ttu-id="c1bc6-227">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-227">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="c1bc6-229">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-229">2</span></span>|  
|<span data-ttu-id="c1bc6-230">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-230">Table</span></span>|@Table|<span data-ttu-id="c1bc6-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-231">VIEW_NAME</span></span>|<span data-ttu-id="c1bc6-232">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-232">3</span></span>|  
|<span data-ttu-id="c1bc6-233">列</span><span class="sxs-lookup"><span data-stu-id="c1bc6-233">Column</span></span>|@Column|<span data-ttu-id="c1bc6-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-234">COLUMN_NAME</span></span>|<span data-ttu-id="c1bc6-235">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c1bc6-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c1bc6-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c1bc6-237">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-237">Restriction Name</span></span>|<span data-ttu-id="c1bc6-238">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-238">Parameter Name</span></span>|<span data-ttu-id="c1bc6-239">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-239">Restriction Default</span></span>|<span data-ttu-id="c1bc6-240">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-241">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-241">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="c1bc6-243">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-243">1</span></span>|  
|<span data-ttu-id="c1bc6-244">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-244">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="c1bc6-246">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-246">2</span></span>|  
|<span data-ttu-id="c1bc6-247">名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-247">Name</span></span>|@Name|<span data-ttu-id="c1bc6-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="c1bc6-249">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-249">3</span></span>|  
|<span data-ttu-id="c1bc6-250">参数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-250">Parameter</span></span>|@Parameter|<span data-ttu-id="c1bc6-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-251">PARAMETER_NAME</span></span>|<span data-ttu-id="c1bc6-252">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c1bc6-253">过程</span><span class="sxs-lookup"><span data-stu-id="c1bc6-253">Procedures</span></span>  
  
|<span data-ttu-id="c1bc6-254">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-254">Restriction Name</span></span>|<span data-ttu-id="c1bc6-255">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-255">Parameter Name</span></span>|<span data-ttu-id="c1bc6-256">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-256">Restriction Default</span></span>|<span data-ttu-id="c1bc6-257">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-258">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-258">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="c1bc6-260">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-260">1</span></span>|  
|<span data-ttu-id="c1bc6-261">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-261">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="c1bc6-263">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-263">2</span></span>|  
|<span data-ttu-id="c1bc6-264">名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-264">Name</span></span>|@Name|<span data-ttu-id="c1bc6-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="c1bc6-266">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-266">3</span></span>|  
|<span data-ttu-id="c1bc6-267">类型</span><span class="sxs-lookup"><span data-stu-id="c1bc6-267">Type</span></span>|@Type|<span data-ttu-id="c1bc6-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c1bc6-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="c1bc6-269">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="c1bc6-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="c1bc6-270">IndexColumns</span></span>  
  
|<span data-ttu-id="c1bc6-271">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-271">Restriction Name</span></span>|<span data-ttu-id="c1bc6-272">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-272">Parameter Name</span></span>|<span data-ttu-id="c1bc6-273">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-273">Restriction Default</span></span>|<span data-ttu-id="c1bc6-274">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-275">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-275">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="c1bc6-276">db_name()</span></span>|<span data-ttu-id="c1bc6-277">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-277">1</span></span>|  
|<span data-ttu-id="c1bc6-278">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-278">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="c1bc6-279">user_name()</span></span>|<span data-ttu-id="c1bc6-280">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-280">2</span></span>|  
|<span data-ttu-id="c1bc6-281">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-281">Table</span></span>|@Table|<span data-ttu-id="c1bc6-282">o.name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-282">o.name</span></span>|<span data-ttu-id="c1bc6-283">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-283">3</span></span>|  
|<span data-ttu-id="c1bc6-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="c1bc6-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="c1bc6-285">x.name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-285">x.name</span></span>|<span data-ttu-id="c1bc6-286">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-286">4</span></span>|  
|<span data-ttu-id="c1bc6-287">列</span><span class="sxs-lookup"><span data-stu-id="c1bc6-287">Column</span></span>|@Column|<span data-ttu-id="c1bc6-288">c.name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-288">c.name</span></span>|<span data-ttu-id="c1bc6-289">5</span><span class="sxs-lookup"><span data-stu-id="c1bc6-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c1bc6-290">索引</span><span class="sxs-lookup"><span data-stu-id="c1bc6-290">Indexes</span></span>  
  
|<span data-ttu-id="c1bc6-291">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-291">Restriction Name</span></span>|<span data-ttu-id="c1bc6-292">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-292">Parameter Name</span></span>|<span data-ttu-id="c1bc6-293">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-293">Restriction Default</span></span>|<span data-ttu-id="c1bc6-294">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-295">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-295">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="c1bc6-296">db_name()</span></span>|<span data-ttu-id="c1bc6-297">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-297">1</span></span>|  
|<span data-ttu-id="c1bc6-298">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-298">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="c1bc6-299">user_name()</span></span>|<span data-ttu-id="c1bc6-300">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-300">2</span></span>|  
|<span data-ttu-id="c1bc6-301">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-301">Table</span></span>|@Table|<span data-ttu-id="c1bc6-302">o.name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-302">o.name</span></span>|<span data-ttu-id="c1bc6-303">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="c1bc6-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="c1bc6-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="c1bc6-305">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-305">Restriction Name</span></span>|<span data-ttu-id="c1bc6-306">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-306">Parameter Name</span></span>|<span data-ttu-id="c1bc6-307">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-307">Restriction Default</span></span>|<span data-ttu-id="c1bc6-308">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="c1bc6-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-310">assemblies.name</span></span>|<span data-ttu-id="c1bc6-311">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-311">1</span></span>|  
|<span data-ttu-id="c1bc6-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="c1bc6-312">udt_name</span></span>|@UDTName|<span data-ttu-id="c1bc6-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="c1bc6-313">types.assembly_class</span></span>|<span data-ttu-id="c1bc6-314">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="c1bc6-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="c1bc6-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="c1bc6-316">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-316">Restriction Name</span></span>|<span data-ttu-id="c1bc6-317">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-317">Parameter Name</span></span>|<span data-ttu-id="c1bc6-318">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-318">Restriction Default</span></span>|<span data-ttu-id="c1bc6-319">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-320">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-320">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="c1bc6-322">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-322">1</span></span>|  
|<span data-ttu-id="c1bc6-323">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-323">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="c1bc6-325">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-325">2</span></span>|  
|<span data-ttu-id="c1bc6-326">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-326">Table</span></span>|@Table|<span data-ttu-id="c1bc6-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-327">TABLE_NAME</span></span>|<span data-ttu-id="c1bc6-328">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-328">3</span></span>|  
|<span data-ttu-id="c1bc6-329">名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-329">Name</span></span>|@Name|<span data-ttu-id="c1bc6-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="c1bc6-331">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="c1bc6-332">SQL Server 2008     </span><span class="sxs-lookup"><span data-stu-id="c1bc6-332">SQL Server 2008 Schema Restrictions</span></span>  

 <span data-ttu-id="c1bc6-333">下表列出了 SQL Server 2008 架构集合的限制。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="c1bc6-334">这些限制从 .NET Framework 版本 3.5 SP1 和 SQL Server 2008 开始生效。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="c1bc6-335">.NET Framework 和 SQL Server 的早期版本不支持这些限制。</span><span class="sxs-lookup"><span data-stu-id="c1bc6-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="c1bc6-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="c1bc6-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="c1bc6-337">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-337">Restriction Name</span></span>|<span data-ttu-id="c1bc6-338">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-338">Parameter Name</span></span>|<span data-ttu-id="c1bc6-339">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-339">Restriction Default</span></span>|<span data-ttu-id="c1bc6-340">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-341">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-341">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-342">TABLE_CATALOG</span></span>|<span data-ttu-id="c1bc6-343">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-343">1</span></span>|  
|<span data-ttu-id="c1bc6-344">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-344">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="c1bc6-346">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-346">2</span></span>|  
|<span data-ttu-id="c1bc6-347">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-347">Table</span></span>|@Table|<span data-ttu-id="c1bc6-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-348">TABLE_NAME</span></span>|<span data-ttu-id="c1bc6-349">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="c1bc6-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="c1bc6-350">AllColumns</span></span>  
  
|<span data-ttu-id="c1bc6-351">限制名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-351">Restriction Name</span></span>|<span data-ttu-id="c1bc6-352">参数名称</span><span class="sxs-lookup"><span data-stu-id="c1bc6-352">Parameter Name</span></span>|<span data-ttu-id="c1bc6-353">限制默认值</span><span class="sxs-lookup"><span data-stu-id="c1bc6-353">Restriction Default</span></span>|<span data-ttu-id="c1bc6-354">限制数</span><span class="sxs-lookup"><span data-stu-id="c1bc6-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="c1bc6-355">目录</span><span class="sxs-lookup"><span data-stu-id="c1bc6-355">Catalog</span></span>|@Catalog|<span data-ttu-id="c1bc6-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c1bc6-356">TABLE_CATALOG</span></span>|<span data-ttu-id="c1bc6-357">1</span><span class="sxs-lookup"><span data-stu-id="c1bc6-357">1</span></span>|  
|<span data-ttu-id="c1bc6-358">所有者</span><span class="sxs-lookup"><span data-stu-id="c1bc6-358">Owner</span></span>|@Owner|<span data-ttu-id="c1bc6-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c1bc6-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="c1bc6-360">2</span><span class="sxs-lookup"><span data-stu-id="c1bc6-360">2</span></span>|  
|<span data-ttu-id="c1bc6-361">表</span><span class="sxs-lookup"><span data-stu-id="c1bc6-361">Table</span></span>|@Table|<span data-ttu-id="c1bc6-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-362">TABLE_NAME</span></span>|<span data-ttu-id="c1bc6-363">3</span><span class="sxs-lookup"><span data-stu-id="c1bc6-363">3</span></span>|  
|<span data-ttu-id="c1bc6-364">列</span><span class="sxs-lookup"><span data-stu-id="c1bc6-364">Column</span></span>|@Column|<span data-ttu-id="c1bc6-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c1bc6-365">COLUMN_NAME</span></span>|<span data-ttu-id="c1bc6-366">4</span><span class="sxs-lookup"><span data-stu-id="c1bc6-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1bc6-367">请参阅</span><span class="sxs-lookup"><span data-stu-id="c1bc6-367">See also</span></span>

- [<span data-ttu-id="c1bc6-368">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="c1bc6-368">ADO.NET Overview</span></span>](ado-net-overview.md)
