---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720176"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a><span data-ttu-id="a1243-101">在 Unix 上正确分析包含非 ASCII 字符的 URI 路径</span><span class="sxs-lookup"><span data-stu-id="a1243-101">URI paths with non-ASCII characters parse correctly on Unix</span></span>

<span data-ttu-id="a1243-102">在 <xref:System.Uri?displayProperty=fullName> 类中修复了一个 bug，包含非 ASCII 字符的绝对 URI 路径现在可以在 Unix 平台上正确分析。</span><span class="sxs-lookup"><span data-stu-id="a1243-102">A bug was fixed in the <xref:System.Uri?displayProperty=fullName> class such that absolute URI paths that contain non-ASCII characters now parse correctly on Unix platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a1243-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="a1243-103">Change description</span></span>

<span data-ttu-id="a1243-104">在早期版本的 .NET 中，不能在 Unix 平台上正确分析包含非 ASCII 字符的绝对 URI 路径，并且会复制该路径的段。</span><span class="sxs-lookup"><span data-stu-id="a1243-104">In previous versions of .NET, absolute URI paths that contain non-ASCII characters are parsed incorrectly on Unix platforms, and segments of the path are duplicated.</span></span> <span data-ttu-id="a1243-105">（绝对路径是以“/”开头的路径。）.NET 5.0 的分析问题已得以修复。</span><span class="sxs-lookup"><span data-stu-id="a1243-105">(Absolute paths are those that start with "/".) The parsing issue has been fixed for .NET 5.0.</span></span> <span data-ttu-id="a1243-106">如果从早期版本的 .NET 迁移到 .NET 5.0 或更高版本，则会获得由 <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>、<xref:System.Uri.ToString?displayProperty=nameWithType> 和其他 <xref:System.Uri> 成员生成的不同的值。</span><span class="sxs-lookup"><span data-stu-id="a1243-106">If you move from a previous version of .NET to .NET 5.0 or later, you'll get different values produced by <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType>, <xref:System.Uri.ToString?displayProperty=nameWithType>, and other <xref:System.Uri> members.</span></span>

<span data-ttu-id="a1243-107">在 Unix 上运行时，请考虑以下代码的输出。</span><span class="sxs-lookup"><span data-stu-id="a1243-107">Consider the output of the following code when run on Unix.</span></span>

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

<span data-ttu-id="a1243-108">先前 .NET 版本的输出：</span><span class="sxs-lookup"><span data-stu-id="a1243-108">Output on previous .NET version:</span></span>

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

<span data-ttu-id="a1243-109">.NET 5.0 或更高版本的输出：</span><span class="sxs-lookup"><span data-stu-id="a1243-109">Output on .NET 5.0 or later version:</span></span>

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a><span data-ttu-id="a1243-110">引入的版本</span><span class="sxs-lookup"><span data-stu-id="a1243-110">Version introduced</span></span>

<span data-ttu-id="a1243-111">5.0</span><span class="sxs-lookup"><span data-stu-id="a1243-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a1243-112">建议操作</span><span class="sxs-lookup"><span data-stu-id="a1243-112">Recommended action</span></span>

<span data-ttu-id="a1243-113">如果你具有需要和说明重复路径段的代码，则可以删除该代码。</span><span class="sxs-lookup"><span data-stu-id="a1243-113">If you have code that expects and accounts for the duplicated path segments, you can remove that code.</span></span>

#### <a name="category"></a><span data-ttu-id="a1243-114">类别</span><span class="sxs-lookup"><span data-stu-id="a1243-114">Category</span></span>

<span data-ttu-id="a1243-115">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="a1243-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a1243-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a1243-116">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
