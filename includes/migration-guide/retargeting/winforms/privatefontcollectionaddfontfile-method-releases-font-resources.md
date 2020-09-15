---
ms.openlocfilehash: 53ded5ae6e5a025fc7992da099c3481587bb6f31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614405"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a><span data-ttu-id="1ceb9-101">PrivateFontCollection.AddFontFile 方法释放字体资源</span><span class="sxs-lookup"><span data-stu-id="1ceb9-101">PrivateFontCollection.AddFontFile method releases Font resources</span></span>

#### <a name="details"></a><span data-ttu-id="1ceb9-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1ceb9-102">Details</span></span>

<span data-ttu-id="1ceb9-103">在 .NET Framework 4.7.1 和早期版本中，为使用 <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> 方法添加到此集合的 <xref:System.Drawing.Font> 对象设置 <xref:System.Drawing.Text.PrivateFontCollection> 后，<xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> 类不会释放 GDI+ 字体资源。</span><span class="sxs-lookup"><span data-stu-id="1ceb9-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> class does not release the GDI+ font resources after the <xref:System.Drawing.Text.PrivateFontCollection> is disposed for <xref:System.Drawing.Font> objects that are added to this collection using the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> method.</span></span> <span data-ttu-id="1ceb9-104">在 .NET Framework 4.7.2 和更高版本中，<xref:System.Drawing.Text.FontCollection.Dispose%2A> 会释放作为文件添加到此集合的 GDI+ 字体。</span><span class="sxs-lookup"><span data-stu-id="1ceb9-104">In the .NET Framework 4.7.2 and later <xref:System.Drawing.Text.FontCollection.Dispose%2A> releases the GDI+ fonts that were added to the collection as files.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1ceb9-105">建议</span><span class="sxs-lookup"><span data-stu-id="1ceb9-105">Suggestion</span></span>

<span data-ttu-id="1ceb9-106">**如何选择启用或选择弃用这些更改** 为使应用程序从这些更改获益，它必须在 .NET Framework 4.7.2 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="1ceb9-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="1ceb9-107">此应用程序可通过以下任何一种方式从这些更改中获益：</span><span class="sxs-lookup"><span data-stu-id="1ceb9-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="1ceb9-108">重新编译为面向 .NET Framework 4.7.2。</span><span class="sxs-lookup"><span data-stu-id="1ceb9-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="1ceb9-109">对于面向 .NET Framework 4.7.2 或更高版本的 Windows 窗体应用程序，此更改将默认启用。</span><span class="sxs-lookup"><span data-stu-id="1ceb9-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="1ceb9-110">它面向 .NET Framework 4.7.1 或更早版本，通过向 app.config 文件的 `<runtime>` 部分添加以下 [AppContext 开关](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)并将其设置为 `false`，可选择弃用旧版辅助功能行为，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="1ceb9-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="1ceb9-111">面向 .NET Framework 4.7.2 或更高版本并希望保留旧版行为的应用程序，可通过将此 AppContext 开关显式设置为 `true` 来选择不释放字体资源。</span><span class="sxs-lookup"><span data-stu-id="1ceb9-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to not release font resources by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="1ceb9-112">“属性”</span><span class="sxs-lookup"><span data-stu-id="1ceb9-112">Name</span></span>    | <span data-ttu-id="1ceb9-113">“值”</span><span class="sxs-lookup"><span data-stu-id="1ceb9-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1ceb9-114">范围</span><span class="sxs-lookup"><span data-stu-id="1ceb9-114">Scope</span></span>   | <span data-ttu-id="1ceb9-115">边缘</span><span class="sxs-lookup"><span data-stu-id="1ceb9-115">Edge</span></span>        |
| <span data-ttu-id="1ceb9-116">Version</span><span class="sxs-lookup"><span data-stu-id="1ceb9-116">Version</span></span> | <span data-ttu-id="1ceb9-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="1ceb9-117">4.7.2</span></span>       |
| <span data-ttu-id="1ceb9-118">类型</span><span class="sxs-lookup"><span data-stu-id="1ceb9-118">Type</span></span>    | <span data-ttu-id="1ceb9-119">重定目标</span><span class="sxs-lookup"><span data-stu-id="1ceb9-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1ceb9-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1ceb9-120">Affected APIs</span></span>

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
