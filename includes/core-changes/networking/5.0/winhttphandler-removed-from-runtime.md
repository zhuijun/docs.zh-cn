---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608483"
---
### <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="c0d60-101">已从 .NET 运行时中删除 WinHttpHandler</span><span class="sxs-lookup"><span data-stu-id="c0d60-101">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="c0d60-102">`WinHttpHandler` 类已从 System.Net.Http.dll 程序集删除。</span><span class="sxs-lookup"><span data-stu-id="c0d60-102">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="c0d60-103">它现在仅作为带外 (OOB) [NuGet 包](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)提供。</span><span class="sxs-lookup"><span data-stu-id="c0d60-103">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c0d60-104">引入的版本</span><span class="sxs-lookup"><span data-stu-id="c0d60-104">Version introduced</span></span>

<span data-ttu-id="c0d60-105">5.0</span><span class="sxs-lookup"><span data-stu-id="c0d60-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="c0d60-106">更改描述</span><span class="sxs-lookup"><span data-stu-id="c0d60-106">Change description</span></span>

<span data-ttu-id="c0d60-107">在以前的 .NET 版本中，<xref:System.Net.Http.WinHttpHandler> 类作为核心 .NET 库的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="c0d60-107">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="c0d60-108">从 .NET 5.0 开始，<xref:System.Net.Http.WinHttpHandler> 类仅作为单独安装的 [NuGet 包](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)提供。</span><span class="sxs-lookup"><span data-stu-id="c0d60-108">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c0d60-109">建议操作</span><span class="sxs-lookup"><span data-stu-id="c0d60-109">Recommended action</span></span>

<span data-ttu-id="c0d60-110">安装 [System.Net.Http.WinHttpHandler NuGet 包](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。</span><span class="sxs-lookup"><span data-stu-id="c0d60-110">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="c0d60-111">或者，如果不需要特定于 WinHTTP 的功能，请改用 <xref:System.Net.Http.SocketsHttpHandler>。</span><span class="sxs-lookup"><span data-stu-id="c0d60-111">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

#### <a name="category"></a><span data-ttu-id="c0d60-112">类别</span><span class="sxs-lookup"><span data-stu-id="c0d60-112">Category</span></span>

<span data-ttu-id="c0d60-113">网络</span><span class="sxs-lookup"><span data-stu-id="c0d60-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c0d60-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c0d60-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
