---
ms.openlocfilehash: f75a652f15be6b0d184db20dc5cd8aafd80539fe
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614406"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="c5be6-101">WinForm 的域 upbutton 和 downbutton 操作现已同步</span><span class="sxs-lookup"><span data-stu-id="c5be6-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="c5be6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c5be6-102">Details</span></span>

<span data-ttu-id="c5be6-103">在 .NET Framework 4.7.1 和早期版本中，显示控件文本时会忽视 <xref:System.Windows.Forms.DomainUpDown> 控件的 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作，并且要求开发人员先使用控件上的 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 操作，再使用 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作。</span><span class="sxs-lookup"><span data-stu-id="c5be6-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="c5be6-104">从 .NET Framework 4.7.2 开始，<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 操作将在此场景中独立工作，并保持同步。</span><span class="sxs-lookup"><span data-stu-id="c5be6-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c5be6-105">建议</span><span class="sxs-lookup"><span data-stu-id="c5be6-105">Suggestion</span></span>

<span data-ttu-id="c5be6-106">为使应用程序从这些更改获益，它必须在 .NET Framework 4.7.2 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="c5be6-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="c5be6-107">此应用程序可通过以下任何一种方式从这些更改中获益：</span><span class="sxs-lookup"><span data-stu-id="c5be6-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="c5be6-108">重新编译为面向 .NET Framework 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="c5be6-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="c5be6-109">对于面向 .NET Framework 4.7.2 或更高版本的 Windows 窗体应用程序，此更改将默认启用。</span><span class="sxs-lookup"><span data-stu-id="c5be6-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="c5be6-110">通过向应用配置文件的 `<runtime>` 部分添加以下 [AppContext 开关](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)并将其设置为 `false`，可选择弃用旧版滚动行为，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="c5be6-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c5be6-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="c5be6-111">Name</span></span>    | <span data-ttu-id="c5be6-112">“值”</span><span class="sxs-lookup"><span data-stu-id="c5be6-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c5be6-113">范围</span><span class="sxs-lookup"><span data-stu-id="c5be6-113">Scope</span></span>   | <span data-ttu-id="c5be6-114">边缘</span><span class="sxs-lookup"><span data-stu-id="c5be6-114">Edge</span></span>        |
| <span data-ttu-id="c5be6-115">Version</span><span class="sxs-lookup"><span data-stu-id="c5be6-115">Version</span></span> | <span data-ttu-id="c5be6-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="c5be6-116">4.7.2</span></span>       |
| <span data-ttu-id="c5be6-117">类型</span><span class="sxs-lookup"><span data-stu-id="c5be6-117">Type</span></span>    | <span data-ttu-id="c5be6-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="c5be6-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c5be6-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c5be6-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
