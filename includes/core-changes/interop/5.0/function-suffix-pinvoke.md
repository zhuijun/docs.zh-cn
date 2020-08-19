---
ms.openlocfilehash: e128bdb5735b3e4844356ad4807cc092f6f2b105
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062415"
---
### <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="3dddc-101">不在非 Windows 平台上探测 A/W 后缀</span><span class="sxs-lookup"><span data-stu-id="3dddc-101">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="3dddc-102">在非 Windows 平台上探测 P/Invoke 期间，.NET 运行时不再向函数导出名称添加 `A` 或 `W` 后缀。</span><span class="sxs-lookup"><span data-stu-id="3dddc-102">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3dddc-103">引入的版本</span><span class="sxs-lookup"><span data-stu-id="3dddc-103">Version introduced</span></span>

<span data-ttu-id="3dddc-104">5.0 预览版 4</span><span class="sxs-lookup"><span data-stu-id="3dddc-104">5.0 Preview 4</span></span>

#### <a name="change-description"></a><span data-ttu-id="3dddc-105">更改描述</span><span class="sxs-lookup"><span data-stu-id="3dddc-105">Change description</span></span>

<span data-ttu-id="3dddc-106">[Windows 有一项约定](/windows/win32/intl/conventions-for-function-prototypes)，即要求向 Windows SDK 函数名称添加 `A` 或 `W` 后缀，这分别与 Windows 代码页面和 Unicode 版本相对应。</span><span class="sxs-lookup"><span data-stu-id="3dddc-106">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="3dddc-107">对于之前版本的 .NET，在导出对 P/Invoke 的发现结果的过程中，CoreCLR 和 Mono 运行时在所有平台上都会向导出名称添加 `A` 或 `W` 后缀。</span><span class="sxs-lookup"><span data-stu-id="3dddc-107">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="3dddc-108">而对于 .NET 5.0 及更高版本，在导出发现结果的过程中，仅在 Windows 上向导出名称添加 `A` 或 `W` 后缀。</span><span class="sxs-lookup"><span data-stu-id="3dddc-108">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="3dddc-109">在 Unix 平台上，不会添加后缀。</span><span class="sxs-lookup"><span data-stu-id="3dddc-109">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="3dddc-110">在 Windows 平台上，这两种运行时的语义保持不变。</span><span class="sxs-lookup"><span data-stu-id="3dddc-110">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3dddc-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="3dddc-111">Reason for change</span></span>

<span data-ttu-id="3dddc-112">此项更改旨在简化跨平台探测。</span><span class="sxs-lookup"><span data-stu-id="3dddc-112">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="3dddc-113">如果非 Windows 平台不包含此语义，则不得产生此项开销。</span><span class="sxs-lookup"><span data-stu-id="3dddc-113">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3dddc-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="3dddc-114">Recommended action</span></span>

<span data-ttu-id="3dddc-115">若要缓解此更改的影响，可在非 Windows 平台上手动添加所需的后缀。</span><span class="sxs-lookup"><span data-stu-id="3dddc-115">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="3dddc-116">例如：</span><span class="sxs-lookup"><span data-stu-id="3dddc-116">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

#### <a name="category"></a><span data-ttu-id="3dddc-117">类别</span><span class="sxs-lookup"><span data-stu-id="3dddc-117">Category</span></span>

<span data-ttu-id="3dddc-118">Interop</span><span class="sxs-lookup"><span data-stu-id="3dddc-118">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3dddc-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3dddc-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

-->
