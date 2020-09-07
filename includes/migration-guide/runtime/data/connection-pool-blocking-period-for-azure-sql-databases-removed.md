---
ms.openlocfilehash: c27c63e5bbd4a144b9482a0b1cb74250ae78d91c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496452"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a><span data-ttu-id="a5499-101">已删除 Azure SQL 数据库的连接池锁定期</span><span class="sxs-lookup"><span data-stu-id="a5499-101">Connection pool blocking period for Azure SQL databases is removed</span></span>

#### <a name="details"></a><span data-ttu-id="a5499-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a5499-102">Details</span></span>

<span data-ttu-id="a5499-103">从 .NET Framework 4.6.2 起，对于发送到已知 Azure SQL 数据库（\*.database.windows.net、\*.database.chinacloudapi.cn、\*.database.usgovcloudapi.net、\*.database.cloudapi.de）的打开连接请求，删除了连接池锁定期且不会缓存打开连接错误。</span><span class="sxs-lookup"><span data-stu-id="a5499-103">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), the connection pool blocking period is removed, and connection open errors are not cached.</span></span> <span data-ttu-id="a5499-104">在出现暂时连接错误后随即重试连接打开请求。</span><span class="sxs-lookup"><span data-stu-id="a5499-104">Attempts to retry connection open requests will occur almost immediately after transient connection errors.</span></span> <span data-ttu-id="a5499-105">此更改允许立即重新尝试打开 Azure SQL 数据库的连接，从而改进了已启用云的应用的性能。</span><span class="sxs-lookup"><span data-stu-id="a5499-105">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud- enabled apps.</span></span> <span data-ttu-id="a5499-106">对于其他所有连接尝试，连接池阻止时间段还会继续强制执行。</span><span class="sxs-lookup"><span data-stu-id="a5499-106">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span><p/><span data-ttu-id="a5499-107">在 .NET Framework 4.6.1 和早期版本中，当应用在连接到数据库过程中遇到暂时性连接失败时，无法快速重试连接，因为连接池会缓存错误，并在 5 秒至 1 分钟后重新引发该错误。</span><span class="sxs-lookup"><span data-stu-id="a5499-107">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 minute.</span></span> <span data-ttu-id="a5499-108">有关详细信息，请参阅 [SQL Server 连接池 (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="a5499-108">For more information, see [SQL Server Connection Pooling (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="a5499-109">这种行为会给 Azure SQL 数据库连接带来问题，因为经常会因暂时性错误而导致连接失败，这些错误通常在几秒内便会恢复。</span><span class="sxs-lookup"><span data-stu-id="a5499-109">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="a5499-110">连接池阻止功能意味着，应用在很长一段时间内都无法连接到数据库，即使数据库可用且应用需要在几秒钟内呈现也不行。</span><span class="sxs-lookup"><span data-stu-id="a5499-110">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available and the app needs to render within a few seconds.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a5499-111">建议</span><span class="sxs-lookup"><span data-stu-id="a5499-111">Suggestion</span></span>

<span data-ttu-id="a5499-112">如果不需要此行为，可以通过设置 .NET Framework 4.6.2 中引入的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> 属性配置连接池锁定期。</span><span class="sxs-lookup"><span data-stu-id="a5499-112">If this behavior is undesirable, the connection pool blocking period can be configured by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> property introduced in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="a5499-113">该属性的值属于 <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=fullName> 枚举，可采用以下三个值中的任意一个：</span><span class="sxs-lookup"><span data-stu-id="a5499-113">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=fullName> enumeration that can take either of three values:</span></span><ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul><span data-ttu-id="a5499-114">可以通过将 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> 属性设置为 <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> 来还原以前的行为。</span><span class="sxs-lookup"><span data-stu-id="a5499-114">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>.</span></span>

| <span data-ttu-id="a5499-115">名称</span><span class="sxs-lookup"><span data-stu-id="a5499-115">Name</span></span>    | <span data-ttu-id="a5499-116">值</span><span class="sxs-lookup"><span data-stu-id="a5499-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a5499-117">范围</span><span class="sxs-lookup"><span data-stu-id="a5499-117">Scope</span></span>   |<span data-ttu-id="a5499-118">次要</span><span class="sxs-lookup"><span data-stu-id="a5499-118">Minor</span></span>|
|<span data-ttu-id="a5499-119">Version</span><span class="sxs-lookup"><span data-stu-id="a5499-119">Version</span></span>|<span data-ttu-id="a5499-120">4.6.2</span><span class="sxs-lookup"><span data-stu-id="a5499-120">4.6.2</span></span>|
|<span data-ttu-id="a5499-121">类型</span><span class="sxs-lookup"><span data-stu-id="a5499-121">Type</span></span>|<span data-ttu-id="a5499-122">运行时</span><span class="sxs-lookup"><span data-stu-id="a5499-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a5499-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a5499-123">Affected APIs</span></span>

- <xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Common.DbConnection.OpenAsync`
- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->
