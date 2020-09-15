---
ms.openlocfilehash: 811b1a91169eeebfa056d9ecdb07d342d3b32d85
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615613"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a><span data-ttu-id="b3aab-101">Icon.ToBitmap 成功将带 PNG 帧的图标转换为位图对象</span><span class="sxs-lookup"><span data-stu-id="b3aab-101">Icon.ToBitmap successfully converts icons with PNG frames into Bitmap objects</span></span>

#### <a name="details"></a><span data-ttu-id="b3aab-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b3aab-102">Details</span></span>

<span data-ttu-id="b3aab-103">从面向 .NET Framework 4.6 的应用开始，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法成功将带 PNG 帧的图标转换为 Bitmap 对象。</span><span class="sxs-lookup"><span data-stu-id="b3aab-103">Starting with the apps that target the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into Bitmap objects.</span></span><p/><span data-ttu-id="b3aab-104">在面向 .NET Framework 4.5.2 和更早版本的应用中，如果 Icon 对象具有 PNG 帧，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法将引发 <xref:System.ArgumentOutOfRangeException> 异常。</span><span class="sxs-lookup"><span data-stu-id="b3aab-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the  <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the Icon object has PNG frames.</span></span><p/><span data-ttu-id="b3aab-105">此更改会影响以下应用：重新编译为面向 .NET Framework 4.6 的应用，以及对在 Icon 对象具有 PNG 帧时引发的 <xref:System.ArgumentOutOfRangeException> 实施特殊处理的应用。</span><span class="sxs-lookup"><span data-stu-id="b3aab-105">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an Icon object has PNG frames.</span></span> <span data-ttu-id="b3aab-106">在.NET Framework 4.6 下运行时，转换成功，不再引发 <xref:System.ArgumentOutOfRangeException> ，因此不再调用异常处理程序。</span><span class="sxs-lookup"><span data-stu-id="b3aab-106">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b3aab-107">建议</span><span class="sxs-lookup"><span data-stu-id="b3aab-107">Suggestion</span></span>

<span data-ttu-id="b3aab-108">如果不需要此行为，可以在 app.config 文件的 `<runtime>` 部分中添加下面的元素，从而保留旧行为：</span><span class="sxs-lookup"><span data-stu-id="b3aab-108">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the `<runtime>` section of your app.config file:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>

<span data-ttu-id="b3aab-109">如果 app.config 文件中已包含 `AppContextSwitchOverrides` 元素，则新值应与值特性合并，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b3aab-109">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the value attribute like this:</span></span>

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="b3aab-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="b3aab-110">Name</span></span>    | <span data-ttu-id="b3aab-111">“值”</span><span class="sxs-lookup"><span data-stu-id="b3aab-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b3aab-112">范围</span><span class="sxs-lookup"><span data-stu-id="b3aab-112">Scope</span></span>   | <span data-ttu-id="b3aab-113">次要</span><span class="sxs-lookup"><span data-stu-id="b3aab-113">Minor</span></span>       |
| <span data-ttu-id="b3aab-114">Version</span><span class="sxs-lookup"><span data-stu-id="b3aab-114">Version</span></span> | <span data-ttu-id="b3aab-115">4.6</span><span class="sxs-lookup"><span data-stu-id="b3aab-115">4.6</span></span>         |
| <span data-ttu-id="b3aab-116">类型</span><span class="sxs-lookup"><span data-stu-id="b3aab-116">Type</span></span>    | <span data-ttu-id="b3aab-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="b3aab-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b3aab-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b3aab-118">Affected APIs</span></span>

- <xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType>
