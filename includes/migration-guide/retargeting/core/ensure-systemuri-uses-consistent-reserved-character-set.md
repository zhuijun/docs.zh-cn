---
ms.openlocfilehash: 21921156295d89aad04f3197fef9fa322f3c8c87
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614331"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a><span data-ttu-id="b4964-101">确保 System.Uri 使用一致的保留字符集</span><span class="sxs-lookup"><span data-stu-id="b4964-101">Ensure System.Uri uses a consistent reserved character set</span></span>

#### <a name="details"></a><span data-ttu-id="b4964-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b4964-102">Details</span></span>

<span data-ttu-id="b4964-103">在 <xref:System.Uri?displayProperty=fullName> 中，某些有时会被解码的百分比编码字符现在始终保持编码状态。</span><span class="sxs-lookup"><span data-stu-id="b4964-103">In <xref:System.Uri?displayProperty=fullName>, certain percent-encoded characters that were sometimes decoded are now consistently left encoded.</span></span> <span data-ttu-id="b4964-104">这种情况发生在访问 URI 的路径、查询、片段或用户信息组件的属性和方法中。</span><span class="sxs-lookup"><span data-stu-id="b4964-104">This occurs across the properties and methods that access the path, query, fragment, or userinfo components of the URI.</span></span> <span data-ttu-id="b4964-105">仅当以下两项均为 true 时，该行为才会更改：</span><span class="sxs-lookup"><span data-stu-id="b4964-105">The behavior will change only when both of the following are true:</span></span>

- <span data-ttu-id="b4964-106">URI 包含以下任意保留字符的编码形式：`:`、`'`、`(`、`)`、`!` 或 `*`。</span><span class="sxs-lookup"><span data-stu-id="b4964-106">The URI contains the encoded form of any of the following reserved characters: `:`, `'`, `(`, `)`, `!` or `*`.</span></span>
- <span data-ttu-id="b4964-107">URI 包含 Unicode 或编码的非保留字符。</span><span class="sxs-lookup"><span data-stu-id="b4964-107">The URI contains a Unicode or encoded non-reserved character.</span></span> <span data-ttu-id="b4964-108">如果以上两项均为 true，则编码的保留字符保持编码状态。</span><span class="sxs-lookup"><span data-stu-id="b4964-108">If both of the above are true, the encoded reserved characters are left encoded.</span></span> <span data-ttu-id="b4964-109">在先前版本的 .NET Framework 中，它们为解码状态。</span><span class="sxs-lookup"><span data-stu-id="b4964-109">In previous versions of the .NET Framework, they are decoded.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b4964-110">建议</span><span class="sxs-lookup"><span data-stu-id="b4964-110">Suggestion</span></span>

<span data-ttu-id="b4964-111">对于面向 .NET Framework 4.7.2 及更高版本的应用程序，默认启用新的解码行为。</span><span class="sxs-lookup"><span data-stu-id="b4964-111">For applications that target versions of .NET Framework starting with 4.7.2, the new decoding behavior is enabled by default.</span></span> <span data-ttu-id="b4964-112">如果不需要此更改，可通过将以下 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 开关添加到应用程序配置文件的 `<runtime>` 部分，从而禁用更改：</span><span class="sxs-lookup"><span data-stu-id="b4964-112">If this change is undesirable, you can disable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true" />
</runtime>
```

<span data-ttu-id="b4964-113">对于面向 .NET Framework 早期版本，但在 .NET Framework 4.7.2 及更高版本下运行的应用程序，默认禁用新的解码行为。</span><span class="sxs-lookup"><span data-stu-id="b4964-113">For applications that target earlier versions of the .NET Framework but are running under versions starting with .NET Framework 4.7.2, the new decoding behavior is disabled by default.</span></span> <span data-ttu-id="b4964-114">可通过将以下 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 开关添加到应用程序配置文件的 `<runtime>` 部分，进行启用：</span><span class="sxs-lookup"><span data-stu-id="b4964-114">You can enable it by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switch to the `<runtime>` section of the application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false" />
</runtime>
```

| <span data-ttu-id="b4964-115">“属性”</span><span class="sxs-lookup"><span data-stu-id="b4964-115">Name</span></span>    | <span data-ttu-id="b4964-116">“值”</span><span class="sxs-lookup"><span data-stu-id="b4964-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b4964-117">范围</span><span class="sxs-lookup"><span data-stu-id="b4964-117">Scope</span></span>   | <span data-ttu-id="b4964-118">次要</span><span class="sxs-lookup"><span data-stu-id="b4964-118">Minor</span></span>       |
| <span data-ttu-id="b4964-119">版本</span><span class="sxs-lookup"><span data-stu-id="b4964-119">Version</span></span> | <span data-ttu-id="b4964-120">4.7.2</span><span class="sxs-lookup"><span data-stu-id="b4964-120">4.7.2</span></span>       |
| <span data-ttu-id="b4964-121">类型</span><span class="sxs-lookup"><span data-stu-id="b4964-121">Type</span></span>    | <span data-ttu-id="b4964-122">重定目标</span><span class="sxs-lookup"><span data-stu-id="b4964-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b4964-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b4964-123">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
