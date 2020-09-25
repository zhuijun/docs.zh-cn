---
title: 从文件中插入图像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.openlocfilehash: e70576637d44e874532aa06da4fe94115ac8ed9c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194578"
---
# <a name="inserting-an-image-from-a-file"></a><span data-ttu-id="1d17d-102">从文件中插入图像</span><span class="sxs-lookup"><span data-stu-id="1d17d-102">Inserting an Image from a File</span></span>

<span data-ttu-id="1d17d-103">可以将二进制大型对象 (BLOB) 作为二进制数据或字符数据（具体视数据源中的字段类型而定）写入数据库。</span><span class="sxs-lookup"><span data-stu-id="1d17d-103">You can write a binary large object (BLOB) to a database as either binary or character data, depending on the type of field at your data source.</span></span> <span data-ttu-id="1d17d-104">BLOB 这一通用术语是指，通常包含文档和图片的 `text`、`ntext` 和 `image` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="1d17d-104">BLOB is a generic term that refers to the `text`, `ntext`, and `image` data types, which typically contain documents and pictures.</span></span>  
  
 <span data-ttu-id="1d17d-105">若要将 BLOB 值写入数据库，请发出适当的 INSERT 或 UPDATE 语句，并将 BLOB 值作为输入参数传递 (请参阅) [配置参数和参数数据类型](../configuring-parameters-and-parameter-data-types.md) 。</span><span class="sxs-lookup"><span data-stu-id="1d17d-105">To write a BLOB value to your database, issue the appropriate INSERT or UPDATE statement and pass the BLOB value as an input parameter (see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md)).</span></span> <span data-ttu-id="1d17d-106">如果 BLOB 存储为文本（如 SQL Server `text` 字段），可以将 BLOB 作为字符串参数传递。</span><span class="sxs-lookup"><span data-stu-id="1d17d-106">If your BLOB is stored as text, such as a SQL Server `text` field, you can pass the BLOB as a string parameter.</span></span> <span data-ttu-id="1d17d-107">如果 BLOB 以二进制格式存储（如 SQL Server `image` 字段），可以将 `byte` 类型的数组作为二进制参数传递。</span><span class="sxs-lookup"><span data-stu-id="1d17d-107">If the BLOB is stored in binary format, such as a SQL Server `image` field, you can pass an array of type `byte` as a binary parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d17d-108">示例</span><span class="sxs-lookup"><span data-stu-id="1d17d-108">Example</span></span>  

 <span data-ttu-id="1d17d-109">下面的代码示例将员工信息添加到 Northwind 数据库中的 Employees 表。</span><span class="sxs-lookup"><span data-stu-id="1d17d-109">The following code example adds employee information to the Employees table in the Northwind database.</span></span> <span data-ttu-id="1d17d-110">它从文件中读取员工照片，并将它添加到表中的“照片”字段（图像字段）。</span><span class="sxs-lookup"><span data-stu-id="1d17d-110">A photo of the employee is read from a file and added to the Photo field in the table, which is an image field.</span></span>  
  
```vb  
Public Shared Sub AddEmployee( _  
  lastName As String, _  
  firstName As String, _  
  title As String, _  
  hireDate As DateTime, _  
  reportsTo As Integer, _  
  photoFilePath As String, _  
  connectionString As String)  
  
  Dim photo() as Byte = GetPhoto(photoFilePath)  
  
  Using connection As SqlConnection = New SqlConnection( _  
    connectionString)  
  
  Dim command As SqlCommand = New SqlCommand( _  
    "INSERT INTO Employees (LastName, FirstName, Title, " & _  
    "HireDate, ReportsTo, Photo) " & _  
    "Values(@LastName, @FirstName, @Title, " & _  
    "@HireDate, @ReportsTo, @Photo)", connection)
  
  command.Parameters.Add("@LastName",  _  
    SqlDbType.NVarChar, 20).Value = lastName  
  command.Parameters.Add("@FirstName", _  
    SqlDbType.NVarChar, 10).Value = firstName  
  command.Parameters.Add("@Title", _  
    SqlDbType.NVarChar, 30).Value = title  
  command.Parameters.Add("@HireDate", _  
    SqlDbType.DateTime).Value = hireDate  
  command.Parameters.Add("@ReportsTo", _  
    SqlDbType.Int).Value = reportsTo  
  
  command.Parameters.Add("@Photo", _  
    SqlDbType.Image, photo.Length).Value = photo  
  
  connection.Open()  
  command.ExecuteNonQuery()  
  
  End Using  
End Sub  
  
Public Shared Function GetPhoto(filePath As String) As Byte()  
  Dim stream As FileStream = new FileStream( _  
     filePath, FileMode.Open, FileAccess.Read)  
  Dim reader As BinaryReader = new BinaryReader(stream)  
  
  Dim photo() As Byte = reader.ReadBytes(stream.Length)  
  
  reader.Close()  
  stream.Close()  
  
  Return photo  
End Function  
```  
  
```csharp  
public static void AddEmployee(  
  string lastName,
  string firstName,
  string title,
  DateTime hireDate,
  int reportsTo,
  string photoFilePath,
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);
  
  command.Parameters.Add("@LastName",
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d17d-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="1d17d-111">See also</span></span>

- [<span data-ttu-id="1d17d-112">使用命令修改数据</span><span class="sxs-lookup"><span data-stu-id="1d17d-112">Using Commands to Modify Data</span></span>](../using-commands-to-modify-data.md)
- [<span data-ttu-id="1d17d-113">检索二进制数据</span><span class="sxs-lookup"><span data-stu-id="1d17d-113">Retrieving Binary Data</span></span>](../retrieving-binary-data.md)
- [<span data-ttu-id="1d17d-114">SQL Server 二进制和大值数据</span><span class="sxs-lookup"><span data-stu-id="1d17d-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="1d17d-115">SQL Server 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="1d17d-115">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="1d17d-116">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="1d17d-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
