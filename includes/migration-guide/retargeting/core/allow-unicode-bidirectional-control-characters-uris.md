---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614322"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a><span data-ttu-id="c1698-101">允许在 URI 中使用 Unicode 双向控制字符</span><span class="sxs-lookup"><span data-stu-id="c1698-101">Allow Unicode Bidirectional Control Characters in URIs</span></span>

#### <a name="details"></a><span data-ttu-id="c1698-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c1698-102">Details</span></span>

<span data-ttu-id="c1698-103">Unicode 指定数个特殊控制字符，用于指定文本方向。</span><span class="sxs-lookup"><span data-stu-id="c1698-103">Unicode specifies several special control characters used to specify the orientation of text.</span></span> <span data-ttu-id="c1698-104">在 .NET Framework 先前版本中，即使这些字符已经以百分比编码形式出现，但还是会被错误地从所有 URI 中去除。</span><span class="sxs-lookup"><span data-stu-id="c1698-104">In previous versions of the .NET Framework, these characters were incorrectly stripped from all URIs even if they were present in their percent-encoded form.</span></span> <span data-ttu-id="c1698-105">为了更好地遵守 [RFC 3987](https://tools.ietf.org/html/rfc3987)，现在，我们允许在 URI 中使用这些字符。</span><span class="sxs-lookup"><span data-stu-id="c1698-105">In order to better follow [RFC 3987](https://tools.ietf.org/html/rfc3987), we now allow these characters in URIs.</span></span> <span data-ttu-id="c1698-106">如果在 URI 中出现未编码的字符，则对其进行百分比编码。</span><span class="sxs-lookup"><span data-stu-id="c1698-106">When found unencoded in a URI, they are percent-encoded.</span></span> <span data-ttu-id="c1698-107">如果出现百分比编码的字符，则原样保留。</span><span class="sxs-lookup"><span data-stu-id="c1698-107">When found percent-encoded they are left as-is.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c1698-108">建议</span><span class="sxs-lookup"><span data-stu-id="c1698-108">Suggestion</span></span>

<span data-ttu-id="c1698-109">对于面向 .NET Framework 4.7.2 及更高版本的应用程序，默认启用对 Unicode 双向字符的支持。</span><span class="sxs-lookup"><span data-stu-id="c1698-109">For applications that target versions of .NET Framework starting with 4.7.2, support for Unicode bidirectional characters is enabled by default.</span></span> <span data-ttu-id="c1698-110">如果不需要此更改，可通过将以下 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 开关添加到应用程序配置文件的 `<runtime>` 部分，从而禁用更改：</span><span class="sxs-lookup"><span data-stu-id="c1698-110">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

<span data-ttu-id="c1698-111">对于面向 .NET Framework 早期版本但在 .NET Framework 4.7.2 及更高版本下运行的应用程序，默认禁用对 Unicode 双向字符的支持。</span><span class="sxs-lookup"><span data-stu-id="c1698-111">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, support for Unicode bidirectional characters is disabled by default.</span></span> <span data-ttu-id="c1698-112">可通过将以下 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 开关添加到应用程序配置文件的 `<runtime>` 部分，进行启用：</span><span class="sxs-lookup"><span data-stu-id="c1698-112">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file::</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| <span data-ttu-id="c1698-113">“属性”</span><span class="sxs-lookup"><span data-stu-id="c1698-113">Name</span></span>    | <span data-ttu-id="c1698-114">“值”</span><span class="sxs-lookup"><span data-stu-id="c1698-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c1698-115">范围</span><span class="sxs-lookup"><span data-stu-id="c1698-115">Scope</span></span>   | <span data-ttu-id="c1698-116">次要</span><span class="sxs-lookup"><span data-stu-id="c1698-116">Minor</span></span>       |
| <span data-ttu-id="c1698-117">版本</span><span class="sxs-lookup"><span data-stu-id="c1698-117">Version</span></span> | <span data-ttu-id="c1698-118">4.7.2</span><span class="sxs-lookup"><span data-stu-id="c1698-118">4.7.2</span></span>       |
| <span data-ttu-id="c1698-119">类型</span><span class="sxs-lookup"><span data-stu-id="c1698-119">Type</span></span>    | <span data-ttu-id="c1698-120">重定目标</span><span class="sxs-lookup"><span data-stu-id="c1698-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c1698-121">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c1698-121">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
