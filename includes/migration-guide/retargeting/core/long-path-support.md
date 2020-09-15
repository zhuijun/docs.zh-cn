---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614347"
---
### <a name="long-path-support"></a><span data-ttu-id="4c91a-101">长路径支持</span><span class="sxs-lookup"><span data-stu-id="4c91a-101">Long path support</span></span>

#### <a name="details"></a><span data-ttu-id="4c91a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4c91a-102">Details</span></span>

<span data-ttu-id="4c91a-103">从面向 .NET Framework 4.6.2 的应用开始，支持长路径（最多 32K 个字符），并删除了 260 个字符（或 `MAX_PATH`）的路径长度限制。对于经过重新编译以面向 .NET Framework 4.6.2 的应用，之前因路径超过 260 个字符而引发 <xref:System.IO.PathTooLongException?displayProperty=fullName> 的代码路径，现在仅在以下情况下引发 <xref:System.IO.PathTooLongException?displayProperty=fullName>：</span><span class="sxs-lookup"><span data-stu-id="4c91a-103">Starting with apps that target the .NET Framework 4.6.2, long paths (of up to 32K characters) are supported, and the 260-character (or `MAX_PATH`) limitation on path lengths has been removed.For apps that are recompiled to target the .NET Framework 4.6.2, code paths that previously threw a <xref:System.IO.PathTooLongException?displayProperty=fullName> because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException?displayProperty=fullName> only under the following conditions:</span></span>

- <span data-ttu-id="4c91a-104">路径长度必须大于 <xref:System.Int16.MaxValue> (32,767) 个字符。</span><span class="sxs-lookup"><span data-stu-id="4c91a-104">The length of the path is greater than <xref:System.Int16.MaxValue> (32,767) characters.</span></span>
- <span data-ttu-id="4c91a-105">操作系统返回 `COR_E_PATHTOOLONG` 或其等同项。</span><span class="sxs-lookup"><span data-stu-id="4c91a-105">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>
<span data-ttu-id="4c91a-106">对于面向 .NET Framework 4.6.1 及更早版本的应用，只要路径超过 260 个字符，运行时就会自动引发 <xref:System.IO.PathTooLongException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="4c91a-106">For apps that target the .NET Framework 4.6.1 and earlier versions, the runtime automatically throws a <xref:System.IO.PathTooLongException?displayProperty=fullName> whenever a path exceeds 260 characters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4c91a-107">建议</span><span class="sxs-lookup"><span data-stu-id="4c91a-107">Suggestion</span></span>

<span data-ttu-id="4c91a-108">对于面向 .NET Framework 4.6.2 的应用，如果无需长路径支持，可通过将以下内容添加到 `app.config` 文件的 `<runtime>` 部分来选择弃用该支持：</span><span class="sxs-lookup"><span data-stu-id="4c91a-108">For apps that target the .NET Framework 4.6.2, you can opt out of long path support if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

<span data-ttu-id="4c91a-109">对于面向旧版 .NET Framework，但在 .NET Framework 4.6.2 或更高版本上运行的应用，可通过将以下内容添加到 `app.config` 文件的 `<runtime>` 部分来选择启用长路径支持：</span><span class="sxs-lookup"><span data-stu-id="4c91a-109">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.6.2 or later, you can opt in to long path support by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| <span data-ttu-id="4c91a-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="4c91a-110">Name</span></span>    | <span data-ttu-id="4c91a-111">“值”</span><span class="sxs-lookup"><span data-stu-id="4c91a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4c91a-112">范围</span><span class="sxs-lookup"><span data-stu-id="4c91a-112">Scope</span></span>   | <span data-ttu-id="4c91a-113">次要</span><span class="sxs-lookup"><span data-stu-id="4c91a-113">Minor</span></span>       |
| <span data-ttu-id="4c91a-114">Version</span><span class="sxs-lookup"><span data-stu-id="4c91a-114">Version</span></span> | <span data-ttu-id="4c91a-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="4c91a-115">4.6.2</span></span>       |
| <span data-ttu-id="4c91a-116">类型</span><span class="sxs-lookup"><span data-stu-id="4c91a-116">Type</span></span>    | <span data-ttu-id="4c91a-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="4c91a-117">Retargeting</span></span> |
