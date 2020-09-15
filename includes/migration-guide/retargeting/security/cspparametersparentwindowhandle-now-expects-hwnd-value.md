---
ms.openlocfilehash: 4b5c886ad35afbbf0a68e03b3174ab9ea1f5524f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614366"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a><span data-ttu-id="df025-101">CspParameters.ParentWindowHandle 现在需要 HWND 值</span><span class="sxs-lookup"><span data-stu-id="df025-101">CspParameters.ParentWindowHandle now expects HWND value</span></span>

#### <a name="details"></a><span data-ttu-id="df025-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="df025-102">Details</span></span>

<span data-ttu-id="df025-103">借助 .NET Framework 2.0 中引入的 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 值，应用程序可以注册父窗口句柄值，这样任何需要访问密钥的 UI（如 PIN 提示或同意对话框）将会作为指定窗口的子模式打开。从面向 .NET Framework 4.7 的应用开始，Windows 窗体应用程序可使用如下所示的代码设置 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 属性：</span><span class="sxs-lookup"><span data-stu-id="df025-103">The <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> value, introduced in .NET Framework 2.0, allows an application to register a parent window handle value such that any UI required to access the key (such as a PIN prompt or consent dialog) opens as a modal child to the specified window.Starting with apps that target the .NET Framework 4.7, a Windows Forms application can set the <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> property with code like the following:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="df025-104">在先前版本的 .NET Framework 中，该值应为 <xref:System.IntPtr?displayProperty=fullName>，表示内存中驻留 [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) 值的位置。</span><span class="sxs-lookup"><span data-stu-id="df025-104">In previous versions of the .NET Framework, the value was expected to be an <xref:System.IntPtr?displayProperty=fullName> representing a location in memory where the [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) value resided.</span></span> <span data-ttu-id="df025-105">在 Windows 7 和更早版本上，将属性设置为 form.Handle 不会造成任何影响，但在 Windows 8 和更高版本中，此操作会导致“<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>：参数不正确。”</span><span class="sxs-lookup"><span data-stu-id="df025-105">Setting the property to form.Handle on Windows 7 and earlier versions had no effect, but on Windows 8 and later versions, it results in a &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>: The parameter is incorrect.&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="df025-106">建议</span><span class="sxs-lookup"><span data-stu-id="df025-106">Suggestion</span></span>

<span data-ttu-id="df025-107">如果应用程序要注册父窗口关系且面向 .NET Framework 4.7 或更高版本，建议使用简易窗体：</span><span class="sxs-lookup"><span data-stu-id="df025-107">Applications targeting .NET Framework 4.7 or higher wishing to register a parent window relationship are encouraged to use the simplified form:</span></span>

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

<span data-ttu-id="df025-108">如果用户已确定要传递的正确值是保留 `form.Handle` 值的内存位置地址，可通过将 AppContext 开关 `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` 设置为 `true` 来选择弃用此行为更改：</span><span class="sxs-lookup"><span data-stu-id="df025-108">Users who had identified that the correct value to pass was the address of a memory location which held the value `form.Handle` can opt out of the behavior change by setting the AppContext switch `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` to `true`:</span></span>

- <span data-ttu-id="df025-109">以编程方式在 AppContext 上设置兼容性开关，如[此处](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)所述。</span><span class="sxs-lookup"><span data-stu-id="df025-109">By programmatically setting compat switches on the AppContext, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="df025-110">在 app.config 文件的 `<runtime>` 部分中添加下面的代码行：</span><span class="sxs-lookup"><span data-stu-id="df025-110">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

<span data-ttu-id="df025-111">相反，如果用户希望在旧版 .NET Framework 中加载应用程序时选择启用 .NET Framework 4.7 运行时上的新行为，则可将 AppContext 开关设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="df025-111">Conversely, users who wish to opt in to the new behavior on the .NET Framework 4.7 runtime when the application loads under older .NET Framework versions can set the AppContext switch to `false`.</span></span>

| <span data-ttu-id="df025-112">“属性”</span><span class="sxs-lookup"><span data-stu-id="df025-112">Name</span></span>    | <span data-ttu-id="df025-113">“值”</span><span class="sxs-lookup"><span data-stu-id="df025-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="df025-114">范围</span><span class="sxs-lookup"><span data-stu-id="df025-114">Scope</span></span>   | <span data-ttu-id="df025-115">次要</span><span class="sxs-lookup"><span data-stu-id="df025-115">Minor</span></span>       |
| <span data-ttu-id="df025-116">Version</span><span class="sxs-lookup"><span data-stu-id="df025-116">Version</span></span> | <span data-ttu-id="df025-117">4.7</span><span class="sxs-lookup"><span data-stu-id="df025-117">4.7</span></span>         |
| <span data-ttu-id="df025-118">类型</span><span class="sxs-lookup"><span data-stu-id="df025-118">Type</span></span>    | <span data-ttu-id="df025-119">重定目标</span><span class="sxs-lookup"><span data-stu-id="df025-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="df025-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="df025-120">Affected APIs</span></span>

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
