---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614399"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="cf4d7-101">存在嵌套 ToolStripMenuItems 时，ContextMenuStrip.SourceControl 属性包含有效控件</span><span class="sxs-lookup"><span data-stu-id="cf4d7-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="cf4d7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cf4d7-102">Details</span></span>

<span data-ttu-id="cf4d7-103">在 .NET Framework 4.7.1 和更早版本中，用户从嵌套 <xref:System.Windows.Forms.ToolStripMenuItem> 控件中打开菜单时，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 属性会错误地返回 null。</span><span class="sxs-lookup"><span data-stu-id="cf4d7-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="cf4d7-104">在 .NET Framework 4.7.2 及更高版本中，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl> 属性始终设置为实际的源代码管理。</span><span class="sxs-lookup"><span data-stu-id="cf4d7-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cf4d7-105">建议</span><span class="sxs-lookup"><span data-stu-id="cf4d7-105">Suggestion</span></span>

<span data-ttu-id="cf4d7-106">**如何选择启用或选择弃用这些更改** 为使应用程序从这些更改获益，它必须在 .NET Framework 4.7.2 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="cf4d7-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="cf4d7-107">此应用程序可通过以下任何一种方式从这些更改中获益：</span><span class="sxs-lookup"><span data-stu-id="cf4d7-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="cf4d7-108">它面向 .NET Framework 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="cf4d7-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="cf4d7-109">对于面向 .NET Framework 4.7.2 或更高版本的 Windows 窗体应用程序，此更改将默认启用。</span><span class="sxs-lookup"><span data-stu-id="cf4d7-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="cf4d7-110">它面向 .NET Framework 4.7.1 或更早版本，通过向 app.config 文件的 `<runtime>` 部分添加以下 [AppContext 开关](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)并将其设置为 `false`，可选择弃用旧版辅助功能行为，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="cf4d7-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="cf4d7-111">面向 .NET Framework 4.7.2 或更高版本并希望保留旧版行为的应用程序，可通过将此 AppContext 开关显式设置为 `true` 来选择启用旧版源代码管理值。</span><span class="sxs-lookup"><span data-stu-id="cf4d7-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="cf4d7-112">“属性”</span><span class="sxs-lookup"><span data-stu-id="cf4d7-112">Name</span></span>    | <span data-ttu-id="cf4d7-113">“值”</span><span class="sxs-lookup"><span data-stu-id="cf4d7-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cf4d7-114">范围</span><span class="sxs-lookup"><span data-stu-id="cf4d7-114">Scope</span></span>   | <span data-ttu-id="cf4d7-115">边缘</span><span class="sxs-lookup"><span data-stu-id="cf4d7-115">Edge</span></span>        |
| <span data-ttu-id="cf4d7-116">Version</span><span class="sxs-lookup"><span data-stu-id="cf4d7-116">Version</span></span> | <span data-ttu-id="cf4d7-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="cf4d7-117">4.7.2</span></span>       |
| <span data-ttu-id="cf4d7-118">类型</span><span class="sxs-lookup"><span data-stu-id="cf4d7-118">Type</span></span>    | <span data-ttu-id="cf4d7-119">重定目标</span><span class="sxs-lookup"><span data-stu-id="cf4d7-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cf4d7-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="cf4d7-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
