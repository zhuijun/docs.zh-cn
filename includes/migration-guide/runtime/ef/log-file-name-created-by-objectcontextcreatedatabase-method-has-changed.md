---
ms.openlocfilehash: e77e37156de759856c8a6f2e0c009caf9e1fe826
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497305"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="76f14-101">ObjectContext.CreateDatabase 方法创建的日志文件名已更改，以匹配 SQL Server 规范</span><span class="sxs-lookup"><span data-stu-id="76f14-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="76f14-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="76f14-102">Details</span></span>

<span data-ttu-id="76f14-103">当直接调用 <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> 方法或通过使用 Code First 与 SqlClient 提供程序以及连接字符串中的 AttachDBFilename 值来调用此方法时，它将创建一个名为 filename_log.ldf 而非 filename.ldf 的日志文件（其中 filename 是 AttachDBFilename 值指定的文件的名称）。</span><span class="sxs-lookup"><span data-stu-id="76f14-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="76f14-104">此更改通过提供根据 SQL Server 规范命名的日志文件来改进调试。</span><span class="sxs-lookup"><span data-stu-id="76f14-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="76f14-105">建议</span><span class="sxs-lookup"><span data-stu-id="76f14-105">Suggestion</span></span>

<span data-ttu-id="76f14-106">如果日志文件名对应用而言很重要，应更新该应用，以使用标准的 _log.ldf 文件名格式。</span><span class="sxs-lookup"><span data-stu-id="76f14-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="76f14-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="76f14-107">Name</span></span>    | <span data-ttu-id="76f14-108">“值”</span><span class="sxs-lookup"><span data-stu-id="76f14-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="76f14-109">范围</span><span class="sxs-lookup"><span data-stu-id="76f14-109">Scope</span></span>   |<span data-ttu-id="76f14-110">边缘</span><span class="sxs-lookup"><span data-stu-id="76f14-110">Edge</span></span>|
|<span data-ttu-id="76f14-111">Version</span><span class="sxs-lookup"><span data-stu-id="76f14-111">Version</span></span>|<span data-ttu-id="76f14-112">4.5</span><span class="sxs-lookup"><span data-stu-id="76f14-112">4.5</span></span>|
|<span data-ttu-id="76f14-113">类型</span><span class="sxs-lookup"><span data-stu-id="76f14-113">Type</span></span>|<span data-ttu-id="76f14-114">运行时</span><span class="sxs-lookup"><span data-stu-id="76f14-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="76f14-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="76f14-115">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`

-->
