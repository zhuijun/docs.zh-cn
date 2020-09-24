---
ms.openlocfilehash: 54bee14f6de409550357194e905b6ee5d8ef8f18
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678989"
---
### <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="71fad-101">对于 WPF 和 WinForms 应用，OutputType 设置为 WinExe</span><span class="sxs-lookup"><span data-stu-id="71fad-101">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="71fad-102">对于 Windows Presentation Foundation (WPF) 和 Windows 窗体应用，`OutputType` 自动设置为 `WinExe`。</span><span class="sxs-lookup"><span data-stu-id="71fad-102">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="71fad-103">如果 `OutputType` 设置为 `WinExe`，则在执行应用时不会打开控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="71fad-103">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="71fad-104">更改说明</span><span class="sxs-lookup"><span data-stu-id="71fad-104">Change description</span></span>

<span data-ttu-id="71fad-105">在早期版本的 .NET 中，使用为项目文件中的 `OutputType` 指定的值。</span><span class="sxs-lookup"><span data-stu-id="71fad-105">In previous versions of .NET, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="71fad-106">例如：</span><span class="sxs-lookup"><span data-stu-id="71fad-106">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="71fad-107">从 .NET 5.0 开始，对于 WPF 和 Windows 窗体应用，`OutputType` 自动设置为 `WinExe`。</span><span class="sxs-lookup"><span data-stu-id="71fad-107">Starting in .NET 5.0, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps.</span></span> <span data-ttu-id="71fad-108">例如：</span><span class="sxs-lookup"><span data-stu-id="71fad-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

#### <a name="reason-for-change"></a><span data-ttu-id="71fad-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="71fad-109">Reason for change</span></span>

<span data-ttu-id="71fad-110">假定在执行 WPF 或 Windows 窗体应用时，大多数用户不希望打开控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="71fad-110">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="71fad-111">此外，[这些应用程序类型现在使用 .NET SDK](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) 而不是 Windows 桌面 SDK，因此会设置正确的默认值。</span><span class="sxs-lookup"><span data-stu-id="71fad-111">In addition, [now that these application types use the .NET SDK](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="71fad-112">而且，添加了对面向 iOS 和 Android 的支持时，如果多个平台使用相同的输出类型，则在这些平台之间进行多目标操作将更轻松。</span><span class="sxs-lookup"><span data-stu-id="71fad-112">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="71fad-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="71fad-113">Version introduced</span></span>

<span data-ttu-id="71fad-114">.NET 5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="71fad-114">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="71fad-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="71fad-115">Recommended action</span></span>

<span data-ttu-id="71fad-116">你无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="71fad-116">No action is required in your part.</span></span> <span data-ttu-id="71fad-117">但是，如果你想还原为旧行为，请在项目文件中将 `DisableWinExeOutputInference` 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="71fad-117">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

#### <a name="category"></a><span data-ttu-id="71fad-118">类别</span><span class="sxs-lookup"><span data-stu-id="71fad-118">Category</span></span>

- <span data-ttu-id="71fad-119">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="71fad-119">Windows Forms</span></span>
- <span data-ttu-id="71fad-120">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="71fad-120">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="71fad-121">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="71fad-121">Affected APIs</span></span>

<span data-ttu-id="71fad-122">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="71fad-122">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
