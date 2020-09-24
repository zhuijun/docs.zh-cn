---
title: 使用 OracleDataReader 从多个 REF CURSOR 中检索数据
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: 5f0c50cb2c1ec4581c67d2f055e5bf50a82f4809
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150643"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a><span data-ttu-id="e874f-102">使用 OracleDataReader 从多个 REF CURSOR 中检索数据</span><span class="sxs-lookup"><span data-stu-id="e874f-102">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>

<span data-ttu-id="e874f-103">此 Microsoft Visual Basic 示例执行一个 PL/SQL 存储过程，返回两个 REF CURSOR 参数，并使用 <xref:System.Data.OracleClient.OracleDataReader> 读取值。</span><span class="sxs-lookup"><span data-stu-id="e874f-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click( _  
  ByVal sender As Object, ByVal e As System.EventArgs)  _  
  Handles Button1.Click  
  
  Dim connString As New String( _  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter( _  
      "EMPCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
    cmd.Parameters.Add(New OracleParameter(_  
      "DEPTCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
    While (rdr.Read())  
        REM do something with the values from the EMP table
    End While  
  
    rdr.NextResult()  
    While (rdr.Read())  
        REM do something with the values from the DEPT table
    End While  
    rdr.Close()  
  End Using  
End Sub
```  
  
## <a name="see-also"></a><span data-ttu-id="e874f-104">请参阅</span><span class="sxs-lookup"><span data-stu-id="e874f-104">See also</span></span>

- [<span data-ttu-id="e874f-105">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="e874f-105">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="e874f-106">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="e874f-106">ADO.NET Overview</span></span>](ado-net-overview.md)
