---
ms.openlocfilehash: e65ba0edb132f5cded244a69d58e43ffea76a039
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606864"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="f9169-101">SqlConnection 可以不再连接到 SQL Server 1997 或使用 VIA 适配器的数据库</span><span class="sxs-lookup"><span data-stu-id="f9169-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="f9169-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f9169-102">Details</span></span>

<span data-ttu-id="f9169-103">不再支持使用[虚拟接口适配器 (VIA) 协议](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105))连接到 SQL Server 数据库。</span><span class="sxs-lookup"><span data-stu-id="f9169-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="f9169-104">连接字符串中可以见到用于连接到 SQL Server 数据库的协议。</span><span class="sxs-lookup"><span data-stu-id="f9169-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="f9169-105">VIA 连接将包含 via:&lt;servername&gt;。</span><span class="sxs-lookup"><span data-stu-id="f9169-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="f9169-106">如果此应用通过协议而不是 VIA（例如 tcp: 或 np:）连接到 SQL，则不会遇到中断的更改。</span><span class="sxs-lookup"><span data-stu-id="f9169-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="f9169-107">此外，也不再支持连接到 SQL Server 7 (1997)。</span><span class="sxs-lookup"><span data-stu-id="f9169-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f9169-108">建议</span><span class="sxs-lookup"><span data-stu-id="f9169-108">Suggestion</span></span>

<span data-ttu-id="f9169-109">VIA 协议已弃用，因此，应使用备用协议连接到 SQL 数据库。</span><span class="sxs-lookup"><span data-stu-id="f9169-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="f9169-110">使用的最常见的协议是 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="f9169-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="f9169-111">若要详细了解如何通过 TCP/IP 进行连接，请参阅[对数据库实例启用 TCP/IP 协议](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="f9169-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="f9169-112">如果只能从 Intranet 访问数据库，在网络速度慢时，共享的管道协议可能会提供更好的性能。</span><span class="sxs-lookup"><span data-stu-id="f9169-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="f9169-113">“属性”</span><span class="sxs-lookup"><span data-stu-id="f9169-113">Name</span></span>    | <span data-ttu-id="f9169-114">“值”</span><span class="sxs-lookup"><span data-stu-id="f9169-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f9169-115">范围</span><span class="sxs-lookup"><span data-stu-id="f9169-115">Scope</span></span>   |<span data-ttu-id="f9169-116">边缘</span><span class="sxs-lookup"><span data-stu-id="f9169-116">Edge</span></span>|
|<span data-ttu-id="f9169-117">Version</span><span class="sxs-lookup"><span data-stu-id="f9169-117">Version</span></span>|<span data-ttu-id="f9169-118">4.5</span><span class="sxs-lookup"><span data-stu-id="f9169-118">4.5</span></span>|
|<span data-ttu-id="f9169-119">类型</span><span class="sxs-lookup"><span data-stu-id="f9169-119">Type</span></span>|<span data-ttu-id="f9169-120">运行时</span><span class="sxs-lookup"><span data-stu-id="f9169-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f9169-121">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f9169-121">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->
