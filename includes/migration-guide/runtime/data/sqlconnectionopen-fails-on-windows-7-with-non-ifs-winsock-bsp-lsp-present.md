---
ms.openlocfilehash: 9ab1686f60bcdbfef5f18576be17aee8c931f9aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497633"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="ea29a-101">SqlConnection.Open 在存在非 IFS Winsock BSP 或 LSP 的 Windows 7 中会失败</span><span class="sxs-lookup"><span data-stu-id="ea29a-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

#### <a name="details"></a><span data-ttu-id="ea29a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ea29a-102">Details</span></span>

<span data-ttu-id="ea29a-103">如果在存在非 IFS Winsock BSP 或 LSP 的 Windows 7 计算机上运行，<xref:System.Data.SqlClient.SqlConnection.Open> 和 <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> 在 .NET Framework 4.5 中将会失败。若要确定是否安装了非 IFS BSP 或 LSP，请使用 <code>netsh WinSock Show Catalog</code> 命令，并查看每个返回的 <code>Winsock Catalog Provider Entry</code> 项。</span><span class="sxs-lookup"><span data-stu-id="ea29a-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="ea29a-104">如果服务标志值设置了 <code>0x20000</code> 位，提供程序将使用 IFS 句柄，并将正确运行。</span><span class="sxs-lookup"><span data-stu-id="ea29a-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="ea29a-105">如果 <code>0x20000</code> 位已清除（未设置），则它将是非 IFS BSP 或 LSP。</span><span class="sxs-lookup"><span data-stu-id="ea29a-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ea29a-106">建议</span><span class="sxs-lookup"><span data-stu-id="ea29a-106">Suggestion</span></span>

<span data-ttu-id="ea29a-107">此 bug 已在 .NET Framework 4.5.2 中得到修复，因此升级 .NET Framework 可避免出现此问题。</span><span class="sxs-lookup"><span data-stu-id="ea29a-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="ea29a-108">或者，可通过删除任何已安装的非 IFS Winsock LSP 来避免出现此问题。</span><span class="sxs-lookup"><span data-stu-id="ea29a-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>

| <span data-ttu-id="ea29a-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="ea29a-109">Name</span></span>    | <span data-ttu-id="ea29a-110">“值”</span><span class="sxs-lookup"><span data-stu-id="ea29a-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ea29a-111">范围</span><span class="sxs-lookup"><span data-stu-id="ea29a-111">Scope</span></span>   |<span data-ttu-id="ea29a-112">次要</span><span class="sxs-lookup"><span data-stu-id="ea29a-112">Minor</span></span>|
|<span data-ttu-id="ea29a-113">Version</span><span class="sxs-lookup"><span data-stu-id="ea29a-113">Version</span></span>|<span data-ttu-id="ea29a-114">4.5</span><span class="sxs-lookup"><span data-stu-id="ea29a-114">4.5</span></span>|
|<span data-ttu-id="ea29a-115">类型</span><span class="sxs-lookup"><span data-stu-id="ea29a-115">Type</span></span>|<span data-ttu-id="ea29a-116">运行时</span><span class="sxs-lookup"><span data-stu-id="ea29a-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ea29a-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ea29a-117">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->
