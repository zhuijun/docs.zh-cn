---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619826"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET 现在尝试自动重连已中断的 SQL 连接

#### <a name="details"></a>详细信息

从 .NET Framework 4.5.1 开始，.NET Framework 将尝试自动重新连接已中断的 SQL 连接。 虽然这通常会使应用更可靠，但在少数情况下，应用需要知道连接已断开，以便重新连接时可采取一些操作。

#### <a name="suggestion"></a>建议

如果由于兼容性问题而不希望使用此功能，则可通过将连接字符串（或 <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>）的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> 属性设置为 0 来禁用此功能。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5.1|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
