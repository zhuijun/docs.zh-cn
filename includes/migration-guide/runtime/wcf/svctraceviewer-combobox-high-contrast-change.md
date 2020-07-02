---
ms.openlocfilehash: 06f4186e8f233f5c769dfc5e05d2de5eacd9b053
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621931"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="ceab5-101">svcTraceViewer ComboBox 对比度更改</span><span class="sxs-lookup"><span data-stu-id="ceab5-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="ceab5-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ceab5-102">Details</span></span>

<span data-ttu-id="ceab5-103">在 [Microsoft Service Trace Viewer 工具](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)中，在某些高对比度主题中，ComboBox 控件未以正确的颜色显示。</span><span class="sxs-lookup"><span data-stu-id="ceab5-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="ceab5-104">此问题已在 .NET Framework 4.7.2 中解决。</span><span class="sxs-lookup"><span data-stu-id="ceab5-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="ceab5-105">但是，由于 .NET Framework SDK 后向兼容性要求，因此默认情况下客户无法看到该修复程序。</span><span class="sxs-lookup"><span data-stu-id="ceab5-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="ceab5-106">.NET 4.8 通过将以下 [AppContext 配置开关](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)添加到 svcTraceViewer.exe.config 文件来表示此更改：</span><span class="sxs-lookup"><span data-stu-id="ceab5-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a><span data-ttu-id="ceab5-107">建议</span><span class="sxs-lookup"><span data-stu-id="ceab5-107">Suggestion</span></span>

<ul><li><span data-ttu-id="ceab5-108">如何选择退出更改 如果不希望更改高对比度行为，可通过从 svcTraceViewer.exe.config 文件中删除以下部分来禁用它：</span><span class="sxs-lookup"><span data-stu-id="ceab5-108">How to opt out of the change If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span></li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="ceab5-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="ceab5-109">Name</span></span>    | <span data-ttu-id="ceab5-110">“值”</span><span class="sxs-lookup"><span data-stu-id="ceab5-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ceab5-111">范围</span><span class="sxs-lookup"><span data-stu-id="ceab5-111">Scope</span></span>   |<span data-ttu-id="ceab5-112">边缘</span><span class="sxs-lookup"><span data-stu-id="ceab5-112">Edge</span></span>|
|<span data-ttu-id="ceab5-113">Version</span><span class="sxs-lookup"><span data-stu-id="ceab5-113">Version</span></span>|<span data-ttu-id="ceab5-114">4.8</span><span class="sxs-lookup"><span data-stu-id="ceab5-114">4.8</span></span>|
|<span data-ttu-id="ceab5-115">类型</span><span class="sxs-lookup"><span data-stu-id="ceab5-115">Type</span></span>|<span data-ttu-id="ceab5-116">运行时</span><span class="sxs-lookup"><span data-stu-id="ceab5-116">Runtime</span></span>|
