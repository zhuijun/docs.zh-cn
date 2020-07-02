---
ms.openlocfilehash: 87cb2570d3d47a2acb85b5557141c0fef885516a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621770"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>与解析为 `localhost` 的 SQL Server 数据库的 TCP/IP 连接尝试失败

#### <a name="details"></a>详细信息

在 .NET Framework 4.6 和 4.6.1 中，与解析为 <code>localhost</code> 的 SQL Server 数据库的 TCP/IP 连接尝试失败，出现错误：“在与 SQL Server 建立连接时出现与网络相关的错误或特定于实例的错误。 未找到或无法访问服务器。 请验证实例名称是否正确，SQL Server 是否已配置为允许远程连接。 （提供程序：SQL 网络接口，错误：26 - 查找服务器/指定示例时出错）&quot;

#### <a name="suggestion"></a>建议

在 .NET Framework 4.6.2 中，此问题已得到解决，并已恢复以前的行为。 若要连接到会解析为 <code>localhost</code> 的 SQL Server 数据库，请升级到 .NET Framework 4.6.2。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.6|
|类型|运行时|
