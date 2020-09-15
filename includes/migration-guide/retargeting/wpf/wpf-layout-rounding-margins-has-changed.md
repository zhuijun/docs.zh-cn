---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615614"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a><span data-ttu-id="9bfaa-101">边距的 WPF 布局舍入已更改</span><span class="sxs-lookup"><span data-stu-id="9bfaa-101">WPF layout rounding of margins has changed</span></span>

#### <a name="details"></a><span data-ttu-id="9bfaa-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9bfaa-102">Details</span></span>

<span data-ttu-id="9bfaa-103">边距舍入的方式以及边框和边框内的背景已更改。</span><span class="sxs-lookup"><span data-stu-id="9bfaa-103">The way in which margins are rounded and borders and the background inside of them has changed.</span></span> <span data-ttu-id="9bfaa-104">此更改的结果是：</span><span class="sxs-lookup"><span data-stu-id="9bfaa-104">As a result of this change:</span></span>

- <span data-ttu-id="9bfaa-105">元素的宽度或高度最多可以扩大或收缩一个像素。</span><span class="sxs-lookup"><span data-stu-id="9bfaa-105">The width or height of elements may grow or shrink by at most one pixel.</span></span>
- <span data-ttu-id="9bfaa-106">对象的位置最多可以移动一个像素。</span><span class="sxs-lookup"><span data-stu-id="9bfaa-106">The placement of an object can move by at most one pixel.</span></span>
- <span data-ttu-id="9bfaa-107">居中的元素最多可以垂直或水平地偏离中心一个像素。</span><span class="sxs-lookup"><span data-stu-id="9bfaa-107">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>
<span data-ttu-id="9bfaa-108">默认情况下，仅对面向 .NET Framework 4.6 的应用启用此新布局。</span><span class="sxs-lookup"><span data-stu-id="9bfaa-108">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9bfaa-109">建议</span><span class="sxs-lookup"><span data-stu-id="9bfaa-109">Suggestion</span></span>

<span data-ttu-id="9bfaa-110">由于这种修改往往会消除高 DPI 处 WPF 控件的右侧或底部剪辑，因此面向早期版本的 .NET framework 但在.NET Framework 4.6 上运行的应用可以通过将下面的行添加到 app.config 文件的 `<runtime>` 部分来选择加入此新行为：</span><span class="sxs-lookup"><span data-stu-id="9bfaa-110">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

<span data-ttu-id="9bfaa-111">面向 .NET Framework 4.6 但希望 WPF 控件使用之前的布局算法来呈现的应用可以通过将下面的行添加到 app.config 文件的 `<runtime>` 部分来执行此操作：</span><span class="sxs-lookup"><span data-stu-id="9bfaa-111">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the `<runtime>` section of the app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| <span data-ttu-id="9bfaa-112">“属性”</span><span class="sxs-lookup"><span data-stu-id="9bfaa-112">Name</span></span>    | <span data-ttu-id="9bfaa-113">“值”</span><span class="sxs-lookup"><span data-stu-id="9bfaa-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9bfaa-114">范围</span><span class="sxs-lookup"><span data-stu-id="9bfaa-114">Scope</span></span>   | <span data-ttu-id="9bfaa-115">次要</span><span class="sxs-lookup"><span data-stu-id="9bfaa-115">Minor</span></span>       |
| <span data-ttu-id="9bfaa-116">Version</span><span class="sxs-lookup"><span data-stu-id="9bfaa-116">Version</span></span> | <span data-ttu-id="9bfaa-117">4.6</span><span class="sxs-lookup"><span data-stu-id="9bfaa-117">4.6</span></span>         |
| <span data-ttu-id="9bfaa-118">类型</span><span class="sxs-lookup"><span data-stu-id="9bfaa-118">Type</span></span>    | <span data-ttu-id="9bfaa-119">重定目标</span><span class="sxs-lookup"><span data-stu-id="9bfaa-119">Retargeting</span></span> |
