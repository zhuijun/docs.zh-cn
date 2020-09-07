---
ms.openlocfilehash: 8dc947f584d3433f0638a72f4db86ac2680c8dbf
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496333"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection 可以不再连接到 SQL Server 1997 或使用 VIA 适配器的数据库

#### <a name="details"></a>详细信息

不再支持使用[虚拟接口适配器 (VIA) 协议](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105))连接到 SQL Server 数据库。 连接字符串中可以见到用于连接到 SQL Server 数据库的协议。 VIA 连接将包含 via:&lt;servername&gt;。 如果此应用通过协议而不是 VIA（例如 tcp: 或 np:）连接到 SQL，则不会遇到中断的更改。 此外，也不再支持连接到 SQL Server 7 (1997)。

#### <a name="suggestion"></a>建议

VIA 协议已弃用，因此，应使用备用协议连接到 SQL 数据库。 使用的最常见的协议是 TCP/IP。 若要详细了解如何通过 TCP/IP 进行连接，请参阅[对数据库实例启用 TCP/IP 协议](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90))。 如果只能从 Intranet 访问数据库，在网络速度慢时，共享的管道协议可能会提供更好的性能。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时|

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->
