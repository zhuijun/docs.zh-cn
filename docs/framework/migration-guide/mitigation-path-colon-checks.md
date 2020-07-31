---
title: 缓解：路径冒号检查
description: 了解 .NET Framework 4.6.2 中所做的更改，以支持检查正确的驱动器分隔符语法（冒号）。
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: f32ee54f88bc4747fd0d8065b0dce06b151d1d9a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475445"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="809bc-103">缓解：路径冒号检查</span><span class="sxs-lookup"><span data-stu-id="809bc-103">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="809bc-104">自面向 .NET Framework 4.6.2 的应用起，为了支持以前不受支持的路径，执行了大量更改（无论是在长度方面还是在格式方面）。</span><span class="sxs-lookup"><span data-stu-id="809bc-104">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="809bc-105">特别是，能够更加准确地检查驱动器分隔符语法（冒号）的用法是否正确。</span><span class="sxs-lookup"><span data-stu-id="809bc-105">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="809bc-106">影响</span><span class="sxs-lookup"><span data-stu-id="809bc-106">Impact</span></span>  
 <span data-ttu-id="809bc-107">这些更改阻止了 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> 方法以前支持的一些 URI 路径。</span><span class="sxs-lookup"><span data-stu-id="809bc-107">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="809bc-108">缓解</span><span class="sxs-lookup"><span data-stu-id="809bc-108">Mitigation</span></span>  
 <span data-ttu-id="809bc-109">若要解决 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> 和 <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> 方法不再支持以前可接受的路径的问题，可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="809bc-109">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="809bc-110">从 URL 中手动删除协议。</span><span class="sxs-lookup"><span data-stu-id="809bc-110">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="809bc-111">例如，从 URL 中删除 `file://`。</span><span class="sxs-lookup"><span data-stu-id="809bc-111">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="809bc-112">将 URI 传递给 <xref:System.Uri> 构造函数，并检索 <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="809bc-112">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="809bc-113">通过将 `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> 开关设置为 `true` 来选择禁用新的路径规范化。</span><span class="sxs-lookup"><span data-stu-id="809bc-113">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="809bc-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="809bc-114">See also</span></span>

- [<span data-ttu-id="809bc-115">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="809bc-115">Application compatibility</span></span>](application-compatibility.md)
