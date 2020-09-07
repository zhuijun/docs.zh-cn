---
ms.openlocfilehash: 8dc947f584d3433f0638a72f4db86ac2680c8dbf
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496333"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="34894-101">SqlConnection 可以不再连接到 SQL Server 1997 或使用 VIA 适配器的数据库</span><span class="sxs-lookup"><span data-stu-id="34894-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="34894-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="34894-102">Details</span></span>

<span data-ttu-id="34894-103">不再支持使用[虚拟接口适配器 (VIA) 协议](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105))连接到 SQL Server 数据库。</span><span class="sxs-lookup"><span data-stu-id="34894-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="34894-104">连接字符串中可以见到用于连接到 SQL Server 数据库的协议。</span><span class="sxs-lookup"><span data-stu-id="34894-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="34894-105">VIA 连接将包含 via:&lt;servername&gt;。</span><span class="sxs-lookup"><span data-stu-id="34894-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="34894-106">如果此应用通过协议而不是 VIA（例如 tcp: 或 np:）连接到 SQL，则不会遇到中断的更改。</span><span class="sxs-lookup"><span data-stu-id="34894-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="34894-107">此外，也不再支持连接到 SQL Server 7 (1997)。</span><span class="sxs-lookup"><span data-stu-id="34894-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="34894-108">建议</span><span class="sxs-lookup"><span data-stu-id="34894-108">Suggestion</span></span>

<span data-ttu-id="34894-109">VIA 协议已弃用，因此，应使用备用协议连接到 SQL 数据库。</span><span class="sxs-lookup"><span data-stu-id="34894-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="34894-110">使用的最常见的协议是 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="34894-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="34894-111">若要详细了解如何通过 TCP/IP 进行连接，请参阅[对数据库实例启用 TCP/IP 协议](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="34894-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="34894-112">如果只能从 Intranet 访问数据库，在网络速度慢时，共享的管道协议可能会提供更好的性能。</span><span class="sxs-lookup"><span data-stu-id="34894-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="34894-113">“属性”</span><span class="sxs-lookup"><span data-stu-id="34894-113">Name</span></span>    | <span data-ttu-id="34894-114">“值”</span><span class="sxs-lookup"><span data-stu-id="34894-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="34894-115">范围</span><span class="sxs-lookup"><span data-stu-id="34894-115">Scope</span></span>   |<span data-ttu-id="34894-116">边缘</span><span class="sxs-lookup"><span data-stu-id="34894-116">Edge</span></span>|
|<span data-ttu-id="34894-117">Version</span><span class="sxs-lookup"><span data-stu-id="34894-117">Version</span></span>|<span data-ttu-id="34894-118">4.5</span><span class="sxs-lookup"><span data-stu-id="34894-118">4.5</span></span>|
|<span data-ttu-id="34894-119">类型</span><span class="sxs-lookup"><span data-stu-id="34894-119">Type</span></span>|<span data-ttu-id="34894-120">运行时</span><span class="sxs-lookup"><span data-stu-id="34894-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="34894-121">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="34894-121">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->
