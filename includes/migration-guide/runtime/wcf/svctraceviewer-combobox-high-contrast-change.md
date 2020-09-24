---
ms.openlocfilehash: 4bc8db52efdfe483acb4f6b6e33c4fa7716e0b79
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770826"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a><span data-ttu-id="42758-101">svcTraceViewer ComboBox 对比度更改</span><span class="sxs-lookup"><span data-stu-id="42758-101">svcTraceViewer ComboBox high contrast change</span></span>

#### <a name="details"></a><span data-ttu-id="42758-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="42758-102">Details</span></span>

<span data-ttu-id="42758-103">在 [Microsoft Service Trace Viewer 工具](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)中，在某些高对比度主题中，ComboBox 控件未以正确的颜色显示。</span><span class="sxs-lookup"><span data-stu-id="42758-103">In the [Microsoft Service Trace Viewer tool](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), ComboBox controls were not displayed in the correct color in certain high contrast themes.</span></span> <span data-ttu-id="42758-104">此问题已在 .NET Framework 4.7.2 中解决。</span><span class="sxs-lookup"><span data-stu-id="42758-104">The issue was fixed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="42758-105">但是，由于 .NET Framework SDK 后向兼容性要求，因此默认情况下客户无法看到该修复程序。</span><span class="sxs-lookup"><span data-stu-id="42758-105">However, due to .NET Framework SDK backward compatibility requirements, the fix was not visible to customers by default.</span></span> <span data-ttu-id="42758-106">.NET 4.8 通过将以下 [AppContext 配置开关](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)添加到 svcTraceViewer.exe.config 文件来表示此更改：</span><span class="sxs-lookup"><span data-stu-id="42758-106">.NET 4.8 surfaces this change by adding the following [AppContext configuration switches](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the svcTraceViewer.exe.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

#### <a name="suggestion"></a><span data-ttu-id="42758-107">建议</span><span class="sxs-lookup"><span data-stu-id="42758-107">Suggestion</span></span>

<span data-ttu-id="42758-108">如果不希望更改高对比度行为，可通过从 svcTraceViewer.exe.config 文件中删除以下部分来禁用它：</span><span class="sxs-lookup"><span data-stu-id="42758-108">If you don't want to have the high contrast behavior change, you can disable it by removing the following section from the svcTraceViewer.exe.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

| <span data-ttu-id="42758-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="42758-109">Name</span></span>    | <span data-ttu-id="42758-110">“值”</span><span class="sxs-lookup"><span data-stu-id="42758-110">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="42758-111">范围</span><span class="sxs-lookup"><span data-stu-id="42758-111">Scope</span></span>   | <span data-ttu-id="42758-112">边缘</span><span class="sxs-lookup"><span data-stu-id="42758-112">Edge</span></span>    |
| <span data-ttu-id="42758-113">Version</span><span class="sxs-lookup"><span data-stu-id="42758-113">Version</span></span> | <span data-ttu-id="42758-114">4.8</span><span class="sxs-lookup"><span data-stu-id="42758-114">4.8</span></span>     |
| <span data-ttu-id="42758-115">类型</span><span class="sxs-lookup"><span data-stu-id="42758-115">Type</span></span>    | <span data-ttu-id="42758-116">运行时</span><span class="sxs-lookup"><span data-stu-id="42758-116">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="42758-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="42758-117">Affected APIs</span></span>

<span data-ttu-id="42758-118">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="42758-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
