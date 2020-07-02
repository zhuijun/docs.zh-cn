---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619826"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="e7bbd-101">ADO.NET 现在尝试自动重连已中断的 SQL 连接</span><span class="sxs-lookup"><span data-stu-id="e7bbd-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="e7bbd-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e7bbd-102">Details</span></span>

<span data-ttu-id="e7bbd-103">从 .NET Framework 4.5.1 开始，.NET Framework 将尝试自动重新连接已中断的 SQL 连接。</span><span class="sxs-lookup"><span data-stu-id="e7bbd-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="e7bbd-104">虽然这通常会使应用更可靠，但在少数情况下，应用需要知道连接已断开，以便重新连接时可采取一些操作。</span><span class="sxs-lookup"><span data-stu-id="e7bbd-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e7bbd-105">建议</span><span class="sxs-lookup"><span data-stu-id="e7bbd-105">Suggestion</span></span>

<span data-ttu-id="e7bbd-106">如果由于兼容性问题而不希望使用此功能，则可通过将连接字符串（或 <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>）的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> 属性设置为 0 来禁用此功能。</span><span class="sxs-lookup"><span data-stu-id="e7bbd-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="e7bbd-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="e7bbd-107">Name</span></span>    | <span data-ttu-id="e7bbd-108">“值”</span><span class="sxs-lookup"><span data-stu-id="e7bbd-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e7bbd-109">范围</span><span class="sxs-lookup"><span data-stu-id="e7bbd-109">Scope</span></span>   |<span data-ttu-id="e7bbd-110">边缘</span><span class="sxs-lookup"><span data-stu-id="e7bbd-110">Edge</span></span>|
|<span data-ttu-id="e7bbd-111">Version</span><span class="sxs-lookup"><span data-stu-id="e7bbd-111">Version</span></span>|<span data-ttu-id="e7bbd-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="e7bbd-112">4.5.1</span></span>|
|<span data-ttu-id="e7bbd-113">类型</span><span class="sxs-lookup"><span data-stu-id="e7bbd-113">Type</span></span>|<span data-ttu-id="e7bbd-114">运行时</span><span class="sxs-lookup"><span data-stu-id="e7bbd-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7bbd-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e7bbd-115">Affected APIs</span></span>

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
