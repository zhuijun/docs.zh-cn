---
ms.openlocfilehash: 55a26f1ab27792cbedf3f31b797f37d3f768d51a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497779"
---
### <a name="aspnet-fix-handling-of-inputattributes-and-labelattributes-for-webforms-checkbox-control"></a><span data-ttu-id="1747c-101">ASP.NET 修复了处理 WebForms CheckBox 控件的 InputAttributes 和 LabelAttributes 的问题</span><span class="sxs-lookup"><span data-stu-id="1747c-101">ASP.NET Fix handling of InputAttributes and LabelAttributes for WebForms CheckBox control</span></span>

#### <a name="details"></a><span data-ttu-id="1747c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1747c-102">Details</span></span>

<span data-ttu-id="1747c-103">对于面向 .NET Framework 4.7.2 及更低版本的应用程序，以编程方式添加到 WebForms <xref:System.Web.UI.WebControls.CheckBox> 控件的 <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> 和 <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> 将在回发后丢失。</span><span class="sxs-lookup"><span data-stu-id="1747c-103">For applications that target .NET Framework 4.7.2 and earlier versions, <xref:System.Web.UI.WebControls.CheckBox.InputAttributes?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.CheckBox.LabelAttributes?displayProperty=nameWithType> that are programmatically added to a WebForms <xref:System.Web.UI.WebControls.CheckBox> control are lost after postback.</span></span> <span data-ttu-id="1747c-104">对于面向 .NET Framework 4.8 或更高版本的应用程序，它们会在回发后保留。</span><span class="sxs-lookup"><span data-stu-id="1747c-104">For applications that target .NET Framework 4.8 or later versions, they are preserved after postback.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1747c-105">建议</span><span class="sxs-lookup"><span data-stu-id="1747c-105">Suggestion</span></span>

<span data-ttu-id="1747c-106">要在回发时还原属性的正确行为，请将 <code>targetFrameworkVersion</code> 设置为 4.8 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="1747c-106">For the correct behavior for restoring attributes on postback, set the <code>targetFrameworkVersion</code> to 4.8 or higher.</span></span> <span data-ttu-id="1747c-107">例如：</span><span class="sxs-lookup"><span data-stu-id="1747c-107">For example:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.web&gt;&#13;&#10;&lt;httpRuntime targetFramework=&quot;4.8&quot;/&gt;&#13;&#10;&lt;/system.web&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="1747c-108">将其设置为更低版本或根本不设置会保留旧的错误行为。</span><span class="sxs-lookup"><span data-stu-id="1747c-108">Setting it lower, or not at all, preserves the old incorrect behavior.</span></span>

| <span data-ttu-id="1747c-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="1747c-109">Name</span></span>    | <span data-ttu-id="1747c-110">“值”</span><span class="sxs-lookup"><span data-stu-id="1747c-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1747c-111">范围</span><span class="sxs-lookup"><span data-stu-id="1747c-111">Scope</span></span>   |<span data-ttu-id="1747c-112">未知</span><span class="sxs-lookup"><span data-stu-id="1747c-112">Unknown</span></span>|
|<span data-ttu-id="1747c-113">Version</span><span class="sxs-lookup"><span data-stu-id="1747c-113">Version</span></span>|<span data-ttu-id="1747c-114">4.8</span><span class="sxs-lookup"><span data-stu-id="1747c-114">4.8</span></span>|
|<span data-ttu-id="1747c-115">类型</span><span class="sxs-lookup"><span data-stu-id="1747c-115">Type</span></span>|<span data-ttu-id="1747c-116">运行时</span><span class="sxs-lookup"><span data-stu-id="1747c-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1747c-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1747c-117">Affected APIs</span></span>

- <xref:System.Web.UI.WebControls.CheckBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.UI.WebControls.CheckBox`

-->
