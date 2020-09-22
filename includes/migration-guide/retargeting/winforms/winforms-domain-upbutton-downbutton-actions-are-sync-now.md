---
ms.openlocfilehash: c64431fd651fd7d53fb46231c6acc10c5cb43fff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606936"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="38416-101">WinForm 的域 upbutton 和 downbutton 操作现已同步</span><span class="sxs-lookup"><span data-stu-id="38416-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="38416-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="38416-102">Details</span></span>

<span data-ttu-id="38416-103">在 .NET Framework 4.7.1 和早期版本中，显示控件文本时会忽视 <xref:System.Windows.Forms.DomainUpDown> 控件的 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作，并且要求开发人员先使用控件上的 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 操作，再使用 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作。</span><span class="sxs-lookup"><span data-stu-id="38416-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="38416-104">从 .NET Framework 4.7.2 开始，<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 操作将在此场景中独立工作，并保持同步。</span><span class="sxs-lookup"><span data-stu-id="38416-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="38416-105">建议</span><span class="sxs-lookup"><span data-stu-id="38416-105">Suggestion</span></span>

<span data-ttu-id="38416-106">为使应用程序从这些更改获益，它必须在 .NET Framework 4.7.2 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="38416-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="38416-107">此应用程序可通过以下任何一种方式从这些更改中获益：</span><span class="sxs-lookup"><span data-stu-id="38416-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="38416-108">重新编译为面向 .NET Framework 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="38416-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="38416-109">对于面向 .NET Framework 4.7.2 或更高版本的 Windows 窗体应用程序，此更改将默认启用。</span><span class="sxs-lookup"><span data-stu-id="38416-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="38416-110">通过向应用配置文件的 `<runtime>` 部分添加以下 [AppContext 开关](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)并将其设置为 `false`，可选择弃用旧版滚动行为，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="38416-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="38416-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="38416-111">Name</span></span>    | <span data-ttu-id="38416-112">“值”</span><span class="sxs-lookup"><span data-stu-id="38416-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="38416-113">范围</span><span class="sxs-lookup"><span data-stu-id="38416-113">Scope</span></span>   | <span data-ttu-id="38416-114">边缘</span><span class="sxs-lookup"><span data-stu-id="38416-114">Edge</span></span>        |
| <span data-ttu-id="38416-115">Version</span><span class="sxs-lookup"><span data-stu-id="38416-115">Version</span></span> | <span data-ttu-id="38416-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="38416-116">4.7.2</span></span>       |
| <span data-ttu-id="38416-117">类型</span><span class="sxs-lookup"><span data-stu-id="38416-117">Type</span></span>    | <span data-ttu-id="38416-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="38416-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="38416-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="38416-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
