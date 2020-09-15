---
ms.openlocfilehash: 3d1dc8dec18212afd815aa3de7fc82c8a1f680dc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617791"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="d8ed3-101">HwndHost 现可在 DPI 更改期间正确重设子 HWND 的大小</span><span class="sxs-lookup"><span data-stu-id="d8ed3-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="d8ed3-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d8ed3-102">Details</span></span>

<span data-ttu-id="d8ed3-103">在 .NET Framework 4.7.2 和更低版本中，WPF 在预监测感知模式下运行时（例如，将应用程序从一个监视器移动到另一个监视器时），在 DPI 发生更改后，<xref:System.Windows.Interop.HwndHost> 中托管的控件的大小不正确。</span><span class="sxs-lookup"><span data-stu-id="d8ed3-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="d8ed3-104">此修复程序可确保托管控件的大小适当。</span><span class="sxs-lookup"><span data-stu-id="d8ed3-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d8ed3-105">建议</span><span class="sxs-lookup"><span data-stu-id="d8ed3-105">Suggestion</span></span>

<span data-ttu-id="d8ed3-106">为了使应用程序能够从这些更改中受益，它必须在 .NET Framework 4.7.2 或更高版本上运行，并且必须选择加入此行为，方法是将应用配置文件的 `<runtime>` 部分中的以下 [AppContext 开关](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)设置为 `false`，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d8ed3-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="d8ed3-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="d8ed3-107">Name</span></span>    | <span data-ttu-id="d8ed3-108">“值”</span><span class="sxs-lookup"><span data-stu-id="d8ed3-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d8ed3-109">范围</span><span class="sxs-lookup"><span data-stu-id="d8ed3-109">Scope</span></span>   | <span data-ttu-id="d8ed3-110">主要</span><span class="sxs-lookup"><span data-stu-id="d8ed3-110">Major</span></span>       |
| <span data-ttu-id="d8ed3-111">Version</span><span class="sxs-lookup"><span data-stu-id="d8ed3-111">Version</span></span> | <span data-ttu-id="d8ed3-112">4.8</span><span class="sxs-lookup"><span data-stu-id="d8ed3-112">4.8</span></span>         |
| <span data-ttu-id="d8ed3-113">类型</span><span class="sxs-lookup"><span data-stu-id="d8ed3-113">Type</span></span>    | <span data-ttu-id="d8ed3-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="d8ed3-114">Retargeting</span></span> |
