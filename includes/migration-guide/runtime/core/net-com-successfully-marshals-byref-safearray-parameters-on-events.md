---
ms.openlocfilehash: 77e9d28d79a92cf1523e4ef5779d78394b00ae80
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621930"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a><span data-ttu-id="c27d4-101">.NET COM 成功封送事件上的 ByRef SafeArray 参数</span><span class="sxs-lookup"><span data-stu-id="c27d4-101">.NET COM successfully marshals ByRef SafeArray parameters on events</span></span>

#### <a name="details"></a><span data-ttu-id="c27d4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c27d4-102">Details</span></span>

<span data-ttu-id="c27d4-103">在 .NET Framework 4.7.2 及更低版本中，COM 事件上的 ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) 参数无法封送回本机代码。</span><span class="sxs-lookup"><span data-stu-id="c27d4-103">In the .NET Framework 4.7.2 and earlier versions, a ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) parameter on a COM event would fail to marshal back to native code.</span></span>  <span data-ttu-id="c27d4-104">进行此更改后，[SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) 现在可成功进行封送。</span><span class="sxs-lookup"><span data-stu-id="c27d4-104">With this change the [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) is now marshalled successfully.</span></span><ul><li><span data-ttu-id="c27d4-105">[x] Quirked</span><span class="sxs-lookup"><span data-stu-id="c27d4-105">[ x ] Quirked</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="c27d4-106">建议</span><span class="sxs-lookup"><span data-stu-id="c27d4-106">Suggestion</span></span>

<span data-ttu-id="c27d4-107">如果正确封送 COM 事件上的 ByRef SafeArray 参数会中断执行，则可以通过将以下配置开关添加到应用程序配置来禁用此代码：</span><span class="sxs-lookup"><span data-stu-id="c27d4-107">If properly marshalling ByRef SafeArray parameters on COM Events breaks execution, you can disable this code by adding the following configuration switch to your application config:</span></span><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c27d4-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="c27d4-108">Name</span></span>    | <span data-ttu-id="c27d4-109">“值”</span><span class="sxs-lookup"><span data-stu-id="c27d4-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c27d4-110">范围</span><span class="sxs-lookup"><span data-stu-id="c27d4-110">Scope</span></span>   |<span data-ttu-id="c27d4-111">次要</span><span class="sxs-lookup"><span data-stu-id="c27d4-111">Minor</span></span>|
|<span data-ttu-id="c27d4-112">Version</span><span class="sxs-lookup"><span data-stu-id="c27d4-112">Version</span></span>|<span data-ttu-id="c27d4-113">4.8</span><span class="sxs-lookup"><span data-stu-id="c27d4-113">4.8</span></span>|
|<span data-ttu-id="c27d4-114">类型</span><span class="sxs-lookup"><span data-stu-id="c27d4-114">Type</span></span>|<span data-ttu-id="c27d4-115">运行时</span><span class="sxs-lookup"><span data-stu-id="c27d4-115">Runtime</span></span>|
