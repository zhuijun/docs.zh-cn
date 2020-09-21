---
ms.openlocfilehash: 77e231f8ef1dde8a263b8622311099a4a404062d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606835"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a><span data-ttu-id="62605-101">HwndHost 现可在 DPI 更改期间正确重设子 HWND 的大小</span><span class="sxs-lookup"><span data-stu-id="62605-101">HwndHost now correctly resizes child-HWND during DPI changes</span></span>

#### <a name="details"></a><span data-ttu-id="62605-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="62605-102">Details</span></span>

<span data-ttu-id="62605-103">在 .NET Framework 4.7.2 和更低版本中，WPF 在预监测感知模式下运行时（例如，将应用程序从一个监视器移动到另一个监视器时），在 DPI 发生更改后，<xref:System.Windows.Interop.HwndHost> 中托管的控件的大小不正确。</span><span class="sxs-lookup"><span data-stu-id="62605-103">In .NET Framework 4.7.2 and earlier versions, when WPF was run in Per-Monitor Aware mode, controls hosted within <xref:System.Windows.Interop.HwndHost> were not sized correctly after DPI changes, such as when moving applications from one monitor to another.</span></span> <span data-ttu-id="62605-104">此修复程序可确保托管控件的大小适当。</span><span class="sxs-lookup"><span data-stu-id="62605-104">This fix ensures that hosted controls are sized appropriately.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="62605-105">建议</span><span class="sxs-lookup"><span data-stu-id="62605-105">Suggestion</span></span>

<span data-ttu-id="62605-106">为了使应用程序能够从这些更改中受益，它必须在 .NET Framework 4.7.2 或更高版本上运行，并且必须选择加入此行为，方法是将应用配置文件的 `<runtime>` 部分中的以下 [AppContext 开关](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)设置为 `false`，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="62605-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later, and it must opt-in to this behavior by setting the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the `<runtime>` section of the app config file to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="62605-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="62605-107">Name</span></span>    | <span data-ttu-id="62605-108">“值”</span><span class="sxs-lookup"><span data-stu-id="62605-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="62605-109">范围</span><span class="sxs-lookup"><span data-stu-id="62605-109">Scope</span></span>   | <span data-ttu-id="62605-110">主要</span><span class="sxs-lookup"><span data-stu-id="62605-110">Major</span></span>       |
| <span data-ttu-id="62605-111">Version</span><span class="sxs-lookup"><span data-stu-id="62605-111">Version</span></span> | <span data-ttu-id="62605-112">4.8</span><span class="sxs-lookup"><span data-stu-id="62605-112">4.8</span></span>         |
| <span data-ttu-id="62605-113">类型</span><span class="sxs-lookup"><span data-stu-id="62605-113">Type</span></span>    | <span data-ttu-id="62605-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="62605-114">Retargeting</span></span> |
