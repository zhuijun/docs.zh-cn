---
ms.openlocfilehash: bbeca87b3f498213b91d942cc4f197c9d80457a8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496497"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a><span data-ttu-id="3dd70-101">与解析为 `localhost` 的 SQL Server 数据库的 TCP/IP 连接尝试失败</span><span class="sxs-lookup"><span data-stu-id="3dd70-101">Attempting a TCP/IP connection to a SQL Server database that resolves to `localhost` fails</span></span>

#### <a name="details"></a><span data-ttu-id="3dd70-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3dd70-102">Details</span></span>

<span data-ttu-id="3dd70-103">在 .NET Framework 4.6 和 4.6.1 中，与解析为 <code>localhost</code> 的 SQL Server 数据库的 TCP/IP 连接尝试失败，出现错误：“在与 SQL Server 建立连接时出现与网络相关的错误或特定于实例的错误。</span><span class="sxs-lookup"><span data-stu-id="3dd70-103">In the .NET Framework 4.6 and 4.6.1, attempting a TCP/IP connection to a SQL Server database that resolves to <code>localhost</code> fails with the error, &quot;A network-related or instance-specific error occurred while establishing a connection to SQL Server.</span></span> <span data-ttu-id="3dd70-104">未找到或无法访问服务器。</span><span class="sxs-lookup"><span data-stu-id="3dd70-104">The server was not found or was not accessible.</span></span> <span data-ttu-id="3dd70-105">请验证实例名称是否正确，SQL Server 是否已配置为允许远程连接。</span><span class="sxs-lookup"><span data-stu-id="3dd70-105">Verify that the instance name is correct and that SQL Server is configured to allow remote connections.</span></span> <span data-ttu-id="3dd70-106">（提供程序：SQL 网络接口，错误：26 - 查找服务器/指定示例时出错）&quot;</span><span class="sxs-lookup"><span data-stu-id="3dd70-106">(provider: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3dd70-107">建议</span><span class="sxs-lookup"><span data-stu-id="3dd70-107">Suggestion</span></span>

<span data-ttu-id="3dd70-108">在 .NET Framework 4.6.2 中，此问题已得到解决，并已恢复以前的行为。</span><span class="sxs-lookup"><span data-stu-id="3dd70-108">This issue has been addressed and the previous behavior restored in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="3dd70-109">若要连接到会解析为 <code>localhost</code> 的 SQL Server 数据库，请升级到 .NET Framework 4.6.2。</span><span class="sxs-lookup"><span data-stu-id="3dd70-109">To connect to a SQL Server database that resolves to <code>localhost</code>, upgrade to the .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="3dd70-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="3dd70-110">Name</span></span>    | <span data-ttu-id="3dd70-111">“值”</span><span class="sxs-lookup"><span data-stu-id="3dd70-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3dd70-112">范围</span><span class="sxs-lookup"><span data-stu-id="3dd70-112">Scope</span></span>   |<span data-ttu-id="3dd70-113">次要</span><span class="sxs-lookup"><span data-stu-id="3dd70-113">Minor</span></span>|
|<span data-ttu-id="3dd70-114">Version</span><span class="sxs-lookup"><span data-stu-id="3dd70-114">Version</span></span>|<span data-ttu-id="3dd70-115">4.6</span><span class="sxs-lookup"><span data-stu-id="3dd70-115">4.6</span></span>|
|<span data-ttu-id="3dd70-116">类型</span><span class="sxs-lookup"><span data-stu-id="3dd70-116">Type</span></span>|<span data-ttu-id="3dd70-117">运行时</span><span class="sxs-lookup"><span data-stu-id="3dd70-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3dd70-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3dd70-118">Affected APIs</span></span>

<span data-ttu-id="3dd70-119">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="3dd70-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
