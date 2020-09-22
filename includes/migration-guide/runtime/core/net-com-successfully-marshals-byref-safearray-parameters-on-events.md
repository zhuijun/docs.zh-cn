---
ms.openlocfilehash: aadf5eb85c8736c29639d49bc8baf21545d2467c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606927"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="2e740-101">.NET COM 成功封送事件上的 ByRef SafeArray 参数</span><span class="sxs-lookup"><span data-stu-id="2e740-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="2e740-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="2e740-102">Details</span></span>

<span data-ttu-id="2e740-103">在 .NET Framework 4.7.2 及更低版本中，COM 事件上的 ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) 参数无法封送回本机代码。</span><span class="sxs-lookup"><span data-stu-id="2e740-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="2e740-104">进行此更改后，[SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) 现在可成功进行封送。</span><span class="sxs-lookup"><span data-stu-id="2e740-104">With this change the [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="2e740-105">[x] Quirked</span><span class="sxs-lookup"><span data-stu-id="2e740-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="2e740-106">建议</span><span class="sxs-lookup"><span data-stu-id="2e740-106">Suggestion</span></span>

<span data-ttu-id="2e740-107">如果正确封送 COM 事件上的 ByRef SafeArray 参数会中断执行，则可以通过将以下配置开关添加到应用程序配置来禁用此代码：</span><span class="sxs-lookup"><span data-stu-id="2e740-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2e740-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="2e740-108">Name</span></span>    | <span data-ttu-id="2e740-109">“值”</span><span class="sxs-lookup"><span data-stu-id="2e740-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2e740-110">范围</span><span class="sxs-lookup"><span data-stu-id="2e740-110">Scope</span></span>   |<span data-ttu-id="2e740-111">次要</span><span class="sxs-lookup"><span data-stu-id="2e740-111">Minor</span></span>|
|<span data-ttu-id="2e740-112">Version</span><span class="sxs-lookup"><span data-stu-id="2e740-112">Version</span></span>|<span data-ttu-id="2e740-113">4.8</span><span class="sxs-lookup"><span data-stu-id="2e740-113">4.8</span></span>|
|<span data-ttu-id="2e740-114">类型</span><span class="sxs-lookup"><span data-stu-id="2e740-114">Type</span></span>|<span data-ttu-id="2e740-115">运行时</span><span class="sxs-lookup"><span data-stu-id="2e740-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2e740-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2e740-116">Affected APIs</span></span>

<span data-ttu-id="2e740-117">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="2e740-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
