---
ms.openlocfilehash: 148312743dd274728b178951548889dc3a680528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614342"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a><span data-ttu-id="81ed2-101">ZipArchiveEntry 对象的 FullName 属性中的路径分隔符更改</span><span class="sxs-lookup"><span data-stu-id="81ed2-101">Change in path separator character in FullName property of ZipArchiveEntry objects</span></span>

#### <a name="details"></a><span data-ttu-id="81ed2-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="81ed2-102">Details</span></span>

<span data-ttu-id="81ed2-103">对于面向 .NET Framework 4.6.1 及更高版本的应用，在通过重载 <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> 方法创建的 <xref:System.IO.Compression.ZipArchiveEntry> 对象的 <xref:System.IO.Compression.ZipArchiveEntry.FullName> 属性中，路径分隔符已从反斜杠 ("\") 更改为正斜杠（“/”）。</span><span class="sxs-lookup"><span data-stu-id="81ed2-103">For apps that target the .NET Framework 4.6.1 and later versions, the path separator character has changed from a backslash ("\") to a forward slash ("/") in the <xref:System.IO.Compression.ZipArchiveEntry.FullName> property of <xref:System.IO.Compression.ZipArchiveEntry>  objects created by overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> method.</span></span> <span data-ttu-id="81ed2-104">该更改使 .NET 实现遵循 [.ZIP 文件格式规范](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)的 4.4.17.1 部分，还允许 .ZIP 存档在非 Windows 系统上进行解压缩。</span><span class="sxs-lookup"><span data-stu-id="81ed2-104">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span><br /><span data-ttu-id="81ed2-105">对于面向非 Windows 操作系统（如 Macintosh）上旧版 .NET Framework 的应用程序，解压缩其创建的 zip 文件将无法保留目录结构。</span><span class="sxs-lookup"><span data-stu-id="81ed2-105">Decompressing a zip file created by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="81ed2-106">例如，在 Macintosh 上，该应用创建一组文件，它们的文件名与目录路径相连，还与任何反斜杠（“\”）字符和文件名相连。</span><span class="sxs-lookup"><span data-stu-id="81ed2-106">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("") characters, and the filename.</span></span> <span data-ttu-id="81ed2-107">因此，不会保留解压缩的文件的目录结构。</span><span class="sxs-lookup"><span data-stu-id="81ed2-107">As a result, the directory structure of decompressed files is not preserved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="81ed2-108">建议</span><span class="sxs-lookup"><span data-stu-id="81ed2-108">Suggestion</span></span>

<span data-ttu-id="81ed2-109">对于在 Windows 操作系统上由 .NET Framework <xref:System.IO?displayProperty=nameWithType> 命名空间中的 API 解压缩的 .ZIP 文件，此更改造成的影响应该是最小的，因为这些 API 可以无缝地将正斜杠（“/”）或 ("\") 当作路径分隔符处理。</span><span class="sxs-lookup"><span data-stu-id="81ed2-109">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO?displayProperty=nameWithType> namespace should be minimal, since these APIs can seamlessly handle either a forward slash ("/") or a backslash ("\") as the path separator character.</span></span><br /><span data-ttu-id="81ed2-110">如果不需要此更改，可在应用程序配置文件的 [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分中添加配置设置，从而选择弃用此更改。</span><span class="sxs-lookup"><span data-stu-id="81ed2-110">If this change is undesirable, you can opt out of it by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="81ed2-111">以下示例显示 `<runtime>` 部分和 `Switch.System.IO.Compression.ZipFile.UseBackslash` 选择弃用开关：</span><span class="sxs-lookup"><span data-stu-id="81ed2-111">The following example shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-out switch:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

<span data-ttu-id="81ed2-112">此外，对于面向先前版本的 .NET Framework，但在 .NET Framework 4.6.1 及更高版本上运行的应用，可通过将配置设置添加到应用程序配置文件的 [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分来选择启用此行为。</span><span class="sxs-lookup"><span data-stu-id="81ed2-112">In addition, apps that target previous versions of the .NET Framework but are running on the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding a configuration setting to the [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="81ed2-113">以下展示了 `<runtime>` 部分和 `Switch.System.IO.Compression.ZipFile.UseBackslash` 选择弃用开关。</span><span class="sxs-lookup"><span data-stu-id="81ed2-113">The following shows both the `<runtime>` section and the `Switch.System.IO.Compression.ZipFile.UseBackslash` opt-in switch.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| <span data-ttu-id="81ed2-114">“属性”</span><span class="sxs-lookup"><span data-stu-id="81ed2-114">Name</span></span>    | <span data-ttu-id="81ed2-115">“值”</span><span class="sxs-lookup"><span data-stu-id="81ed2-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="81ed2-116">范围</span><span class="sxs-lookup"><span data-stu-id="81ed2-116">Scope</span></span>   | <span data-ttu-id="81ed2-117">边缘</span><span class="sxs-lookup"><span data-stu-id="81ed2-117">Edge</span></span>        |
| <span data-ttu-id="81ed2-118">Version</span><span class="sxs-lookup"><span data-stu-id="81ed2-118">Version</span></span> | <span data-ttu-id="81ed2-119">4.6.1</span><span class="sxs-lookup"><span data-stu-id="81ed2-119">4.6.1</span></span>       |
| <span data-ttu-id="81ed2-120">类型</span><span class="sxs-lookup"><span data-stu-id="81ed2-120">Type</span></span>    | <span data-ttu-id="81ed2-121">重定目标</span><span class="sxs-lookup"><span data-stu-id="81ed2-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="81ed2-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="81ed2-122">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
