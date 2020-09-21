---
ms.openlocfilehash: 5529b8379c5cb9f1bc525e0c2340f6b885e35822
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606223"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="3d144-101">存在嵌套 ToolStripMenuItems 时，ContextMenuStrip.SourceControl 属性包含有效控件</span><span class="sxs-lookup"><span data-stu-id="3d144-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="3d144-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3d144-102">Details</span></span>

<span data-ttu-id="3d144-103">在 .NET Framework 4.7.1 和更早版本中，用户从嵌套 <xref:System.Windows.Forms.ToolStripMenuItem> 控件中打开菜单时，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 属性会错误地返回 null。</span><span class="sxs-lookup"><span data-stu-id="3d144-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="3d144-104">在 .NET Framework 4.7.2 及更高版本中，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl> 属性始终设置为实际的源代码管理。</span><span class="sxs-lookup"><span data-stu-id="3d144-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3d144-105">建议</span><span class="sxs-lookup"><span data-stu-id="3d144-105">Suggestion</span></span>

<span data-ttu-id="3d144-106">**如何选择启用或选择弃用这些更改** 为使应用程序从这些更改获益，它必须在 .NET Framework 4.7.2 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="3d144-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="3d144-107">此应用程序可通过以下任何一种方式从这些更改中获益：</span><span class="sxs-lookup"><span data-stu-id="3d144-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="3d144-108">它面向 .NET Framework 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="3d144-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="3d144-109">对于面向 .NET Framework 4.7.2 或更高版本的 Windows 窗体应用程序，此更改将默认启用。</span><span class="sxs-lookup"><span data-stu-id="3d144-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="3d144-110">它面向 .NET Framework 4.7.1 或更早版本，通过向 app.config 文件的 `<runtime>` 部分添加以下 [AppContext 开关](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)并将其设置为 `false`，可选择弃用旧版辅助功能行为，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="3d144-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="3d144-111">面向 .NET Framework 4.7.2 或更高版本并希望保留旧版行为的应用程序，可通过将此 AppContext 开关显式设置为 `true` 来选择启用旧版源代码管理值。</span><span class="sxs-lookup"><span data-stu-id="3d144-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="3d144-112">“属性”</span><span class="sxs-lookup"><span data-stu-id="3d144-112">Name</span></span>    | <span data-ttu-id="3d144-113">“值”</span><span class="sxs-lookup"><span data-stu-id="3d144-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3d144-114">范围</span><span class="sxs-lookup"><span data-stu-id="3d144-114">Scope</span></span>   | <span data-ttu-id="3d144-115">边缘</span><span class="sxs-lookup"><span data-stu-id="3d144-115">Edge</span></span>        |
| <span data-ttu-id="3d144-116">Version</span><span class="sxs-lookup"><span data-stu-id="3d144-116">Version</span></span> | <span data-ttu-id="3d144-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="3d144-117">4.7.2</span></span>       |
| <span data-ttu-id="3d144-118">类型</span><span class="sxs-lookup"><span data-stu-id="3d144-118">Type</span></span>    | <span data-ttu-id="3d144-119">重定目标</span><span class="sxs-lookup"><span data-stu-id="3d144-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3d144-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3d144-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
