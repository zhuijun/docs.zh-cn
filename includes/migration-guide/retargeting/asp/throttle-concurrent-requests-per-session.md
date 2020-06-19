---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859176"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="25b3e-101">每个会话的限制并发请求数</span><span class="sxs-lookup"><span data-stu-id="25b3e-101">Throttle concurrent requests per session</span></span>

|   |   |
|---|---|
|<span data-ttu-id="25b3e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="25b3e-102">Details</span></span>|<span data-ttu-id="25b3e-103">在 .NET Framework 4.6.2 和更早版本中，ASP.NET 使用相同的 Sessionid 依次执行请求，且 ASP.NET 始终默认通过 cookie 发出 Sessionid。</span><span class="sxs-lookup"><span data-stu-id="25b3e-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="25b3e-104">如果页面响应时间较长，只需在浏览器上按 F5 即可显著降低服务器性能。</span><span class="sxs-lookup"><span data-stu-id="25b3e-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing F5 on the browser.</span></span> <span data-ttu-id="25b3e-105">在此修复程序中，我们添加了一个计数器来跟踪排队的请求，并在请求超过指定限制时终止请求。</span><span class="sxs-lookup"><span data-stu-id="25b3e-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="25b3e-106">默认值为 50。</span><span class="sxs-lookup"><span data-stu-id="25b3e-106">The default value is 50.</span></span> <span data-ttu-id="25b3e-107">如果达到限制，事件日志中会记录一条警告，并且 IIS 日志中可能会记录 HTTP 500 响应。</span><span class="sxs-lookup"><span data-stu-id="25b3e-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>|
|<span data-ttu-id="25b3e-108">建议</span><span class="sxs-lookup"><span data-stu-id="25b3e-108">Suggestion</span></span>|<span data-ttu-id="25b3e-109">若要还原旧行为，可以在 web.config 文件中添加下面的设置，从而选择禁用新行为。</span><span class="sxs-lookup"><span data-stu-id="25b3e-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="25b3e-110">范围</span><span class="sxs-lookup"><span data-stu-id="25b3e-110">Scope</span></span>|<span data-ttu-id="25b3e-111">边缘</span><span class="sxs-lookup"><span data-stu-id="25b3e-111">Edge</span></span>|
|<span data-ttu-id="25b3e-112">Version</span><span class="sxs-lookup"><span data-stu-id="25b3e-112">Version</span></span>|<span data-ttu-id="25b3e-113">4.7</span><span class="sxs-lookup"><span data-stu-id="25b3e-113">4.7</span></span>|
|<span data-ttu-id="25b3e-114">类型</span><span class="sxs-lookup"><span data-stu-id="25b3e-114">Type</span></span>|<span data-ttu-id="25b3e-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="25b3e-115">Retargeting</span></span>|
