---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619851"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>ObjectContext.CreateDatabase 方法创建的日志文件名已更改，以匹配 SQL Server 规范

#### <a name="details"></a>详细信息

当直接调用 <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> 方法或通过使用 Code First 与 SqlClient 提供程序以及连接字符串中的 AttachDBFilename 值来调用此方法时，它将创建一个名为 filename_log.ldf 而非 filename.ldf 的日志文件（其中 filename 是 AttachDBFilename 值指定的文件的名称）。 此更改通过提供根据 SQL Server 规范命名的日志文件来改进调试。

#### <a name="suggestion"></a>建议

如果日志文件名对应用而言很重要，应更新该应用，以使用标准的 _log.ldf 文件名格式。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
