---
ms.openlocfilehash: 4a916a4178535763712ebd58fde1a81e456da0d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538809"
---
### <a name="directorypackagesprops-files-is-imported-by-default"></a><span data-ttu-id="1f379-101">默认导入 Directory.Packages.props 文件</span><span class="sxs-lookup"><span data-stu-id="1f379-101">Directory.Packages.props files is imported by default</span></span>

<span data-ttu-id="1f379-102">如果在项目文件夹或其任何上级中找到名为 Directory.Packages.props 的文件，则 NuGet 的 .props 文件会自动导入该文件 。</span><span class="sxs-lookup"><span data-stu-id="1f379-102">NuGet's *.props* files automatically import a file named *Directory.Packages.props* if it's found in the project folder or any of its ancestors.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1f379-103">引入的版本</span><span class="sxs-lookup"><span data-stu-id="1f379-103">Version introduced</span></span>

<span data-ttu-id="1f379-104">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="1f379-104">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="1f379-105">更改说明</span><span class="sxs-lookup"><span data-stu-id="1f379-105">Change description</span></span>

<span data-ttu-id="1f379-106">在以前的 .NET 版本中，项目文件中有一个名为 Directory.Packages.props 的文件，并且 NuGet 的 .props 文件不会在生成时自动导入该文件 。</span><span class="sxs-lookup"><span data-stu-id="1f379-106">In previous .NET versions, you could have a file named *Directory.Packages.props* in your project file and it wouldn't be automatically imported by NuGet's *.props* file at build time.</span></span>

<span data-ttu-id="1f379-107">从 .NET 5.0 开始，如果项目文件夹或其任何上级中存在这样的文件，将自动导入它。</span><span class="sxs-lookup"><span data-stu-id="1f379-107">Starting in .NET 5.0, such a file *is* automatically imported if it exists in the project folder or any of its ancestors.</span></span> <span data-ttu-id="1f379-108">如果项目文件夹中有一个具有此名称的文件，则此自动导入可能会更改生成的行为。</span><span class="sxs-lookup"><span data-stu-id="1f379-108">If you have a file with this name in your project folder, this automatic import could change behavior of the build.</span></span> <span data-ttu-id="1f379-109">例如，将导入该文件，但是与之前有所不同，如果你特意导入该文件，则导入顺序可能会发生变化。</span><span class="sxs-lookup"><span data-stu-id="1f379-109">For example, the file will be imported but it wasn't before, or the order of when it's imported could change if you specifically import it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1f379-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="1f379-110">Reason for change</span></span>

<span data-ttu-id="1f379-111">进行此更改是为了支持 NuGet 的[中央包版本控制](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions)。</span><span class="sxs-lookup"><span data-stu-id="1f379-111">This change was made in order to support [central package versioning](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) for NuGet.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1f379-112">建议操作</span><span class="sxs-lookup"><span data-stu-id="1f379-112">Recommended action</span></span>

<span data-ttu-id="1f379-113">如果不应自动导入现有 Directory.Packages.props 文件，请重命名此文件。</span><span class="sxs-lookup"><span data-stu-id="1f379-113">Rename the existing *Directory.Packages.props* file if it should not be imported automatically.</span></span>

#### <a name="category"></a><span data-ttu-id="1f379-114">类别</span><span class="sxs-lookup"><span data-stu-id="1f379-114">Category</span></span>

<span data-ttu-id="1f379-115">MSBuild</span><span class="sxs-lookup"><span data-stu-id="1f379-115">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1f379-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1f379-116">Affected APIs</span></span>

<span data-ttu-id="1f379-117">不可用</span><span class="sxs-lookup"><span data-stu-id="1f379-117">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
