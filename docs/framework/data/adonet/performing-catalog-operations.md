---
title: 执行目录操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
ms.openlocfilehash: 802762592a63a2046abcde8ed83ac67be47faf96
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161641"
---
# <a name="performing-catalog-operations"></a><span data-ttu-id="807b5-102">执行目录操作</span><span class="sxs-lookup"><span data-stu-id="807b5-102">Performing Catalog Operations</span></span>

<span data-ttu-id="807b5-103">若要执行命令以修改数据库或目录（如 CREATE TABLE 或 CREATE PROCEDURE 语句），请使用相应的 SQL 语句和**连接**对象创建**命令**对象。</span><span class="sxs-lookup"><span data-stu-id="807b5-103">To execute a command to modify a database or catalog, such as the CREATE TABLE or CREATE PROCEDURE statement, create a **Command** object using the appropriate SQL statements and a **Connection** object.</span></span> <span data-ttu-id="807b5-104">通过**命令**对象的**ExecuteNonQuery**方法执行该命令。</span><span class="sxs-lookup"><span data-stu-id="807b5-104">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="807b5-105">以下代码示例在 Microsoft SQL Server 数据库中创建一个存储过程。</span><span class="sxs-lookup"><span data-stu-id="807b5-105">The following code example creates a stored procedure in a Microsoft SQL Server database.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a><span data-ttu-id="807b5-106">请参阅</span><span class="sxs-lookup"><span data-stu-id="807b5-106">See also</span></span>

- [<span data-ttu-id="807b5-107">使用命令修改数据</span><span class="sxs-lookup"><span data-stu-id="807b5-107">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="807b5-108">命令和参数</span><span class="sxs-lookup"><span data-stu-id="807b5-108">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="807b5-109">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="807b5-109">ADO.NET Overview</span></span>](ado-net-overview.md)
