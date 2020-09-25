---
title: 将 XML 值指定为参数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.openlocfilehash: 20a573da0221704451f10138cb854523d5a17f17
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183047"
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="0fe2f-102">将 XML 值指定为参数</span><span class="sxs-lookup"><span data-stu-id="0fe2f-102">Specifying XML Values as Parameters</span></span>

<span data-ttu-id="0fe2f-103">如果查询需要值为 XML 字符串的参数，开发人员可以使用 SqlXml 数据类型的实例提供该值\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-103">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="0fe2f-104">真的没有任何窍门；SQL Server 中的 XML 列接受参数值的方式与其他数据类型完全相同。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-104">There really are no tricks; XML columns in SQL Server accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fe2f-105">示例</span><span class="sxs-lookup"><span data-stu-id="0fe2f-105">Example</span></span>  

 <span data-ttu-id="0fe2f-106">以下控制台应用程序在 AdventureWorks 数据库中新建一个表\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-106">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="0fe2f-107">新表包括一个名为 SalesID 的列和一个名为 SalesInfo 的 XML 列\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-107">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fe2f-108">默认情况下，在安装 SQL Server 时不安装 AdventureWorks 示例数据库\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-108">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="0fe2f-109">可以通过运行 SQL Server 安装程序来安装它。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-109">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="0fe2f-110">该示例准备一个 <xref:System.Data.SqlClient.SqlCommand> 对象以在新表中插入行。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-110">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="0fe2f-111">保存的文件为 SalesInfo 列提供所需的 XML 数据\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-111">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="0fe2f-112">若要创建运行示例所需的文件，请在与项目相同的文件夹中创建一个新的文本文件。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-112">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="0fe2f-113">将文件命名为 MyTestStoreData.xml。</span><span class="sxs-lookup"><span data-stu-id="0fe2f-113">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="0fe2f-114">在记事本中打开该文件，然后复制并粘贴以下文本：</span><span class="sxs-lookup"><span data-stu-id="0fe2f-114">Open the file in Notepad and copy and paste the following text:</span></span>  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Xml  
  
Module Module1  
    Sub Main()  
  
        Using connection As SqlConnection = New SqlConnection(GetConnectionString())  
        connection.Open()  
  
        ' Create a sample table (dropping first if it already  
        ' exists.)  
        Dim commandNewTable As String = _  
         "IF EXISTS (SELECT * FROM dbo.sysobjects " & _  
         "WHERE id = object_id(N'[dbo].[XmlDataTypeSample]') " & _  
         "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " & _  
         "DROP TABLE [dbo].[XmlDataTypeSample];" & _  
         "CREATE TABLE [dbo].[XmlDataTypeSample](" & _  
         "[SalesID] [int] IDENTITY(1,1) NOT NULL, " & _  
         "[SalesInfo] [xml])"  
  
        Dim commandAdd As New _  
         SqlCommand(commandNewTable, connection)  
        commandAdd.ExecuteNonQuery()  
  
        Dim commandText As String = _  
         "INSERT INTO [dbo].[XmlDataTypeSample] " & _  
           "([SalesInfo] ) " & _  
           "VALUES(@xmlParameter )"  
  
        Dim command As New SqlCommand(commandText, connection)  
  
        ' Read the saved XML document as a
        ' SqlXml-data typed variable.  
        Dim newXml As SqlXml = _  
         New SqlXml(New XmlTextReader("MyTestStoreData.xml"))  
  
        ' Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml)  
  
        Dim result As Integer = command.ExecuteNonQuery()  
        Console.WriteLine(result & " row was added.")  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Using  
End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +
            "DROP TABLE [dbo].[XmlDataTypeSample];" +
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =
            "INSERT INTO [dbo].[XmlDataTypeSample] " +
            "([SalesInfo] ) " +
            "VALUES(@xmlParameter )";  
        SqlCommand command =
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a
        //  SqlXml-data typed variable.  
        SqlXml newXml =
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,
        // you can retrieve it from a configuration file.
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fe2f-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="0fe2f-115">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="0fe2f-116">SQL Server 中的 XML 数据</span><span class="sxs-lookup"><span data-stu-id="0fe2f-116">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)
- [<span data-ttu-id="0fe2f-117">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="0fe2f-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
