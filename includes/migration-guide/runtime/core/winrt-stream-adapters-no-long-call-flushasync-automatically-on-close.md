---
ms.openlocfilehash: 2b4f35fe15f806897e5e4d85ee774b2e4572d974
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496207"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="f7a4b-101">WinRT 流适配器不再在关闭时自动调用 FlushAsync</span><span class="sxs-lookup"><span data-stu-id="f7a4b-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="f7a4b-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f7a4b-102">Details</span></span>

<span data-ttu-id="f7a4b-103">在 Windows 应用商店的应用中，Windows 运行时流适配器不再从 Dispose 方法调用 FlushAsync 方法。</span><span class="sxs-lookup"><span data-stu-id="f7a4b-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f7a4b-104">建议</span><span class="sxs-lookup"><span data-stu-id="f7a4b-104">Suggestion</span></span>

<span data-ttu-id="f7a4b-105">此更改应该为透明。</span><span class="sxs-lookup"><span data-stu-id="f7a4b-105">This change should be transparent.</span></span> <span data-ttu-id="f7a4b-106">开发人员可以通过编写如下代码还原之前的行为：</span><span class="sxs-lookup"><span data-stu-id="f7a4b-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="f7a4b-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="f7a4b-107">Name</span></span>    | <span data-ttu-id="f7a4b-108">“值”</span><span class="sxs-lookup"><span data-stu-id="f7a4b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f7a4b-109">范围</span><span class="sxs-lookup"><span data-stu-id="f7a4b-109">Scope</span></span>   |<span data-ttu-id="f7a4b-110">透明</span><span class="sxs-lookup"><span data-stu-id="f7a4b-110">Transparent</span></span>|
|<span data-ttu-id="f7a4b-111">Version</span><span class="sxs-lookup"><span data-stu-id="f7a4b-111">Version</span></span>|<span data-ttu-id="f7a4b-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f7a4b-112">4.5.1</span></span>|
|<span data-ttu-id="f7a4b-113">类型</span><span class="sxs-lookup"><span data-stu-id="f7a4b-113">Type</span></span>|<span data-ttu-id="f7a4b-114">运行时</span><span class="sxs-lookup"><span data-stu-id="f7a4b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f7a4b-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f7a4b-115">Affected APIs</span></span>

<span data-ttu-id="f7a4b-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="f7a4b-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
