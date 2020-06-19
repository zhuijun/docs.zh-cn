---
ms.openlocfilehash: 72f907c117748fb19ca0663f24445a8c978afd32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235556"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle 现在需要 HWND 值

|   |   |
|---|---|
|详细信息|借助 .NET Framework 2.0 中引入的 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 值，应用程序可以注册父窗口句柄值，这样任何需要访问密钥的 UI（如 PIN 提示或同意对话框）将会作为指定窗口的子模式打开。从面向 .NET Framework 4.7 的应用开始，Windows 窗体应用程序可使用如下所示的代码设置 <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 属性：<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>在先前版本的 .NET Framework 中，该值应为 <xref:System.IntPtr?displayProperty=name>，表示内存中驻留 [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) 值的位置。 在 Windows 7 和更早版本上，将属性设置为 form.Handle 不会造成任何影响，但在 Windows 8 和更高版本中，此操作会导致“<xref:System.Security.Cryptography.CryptographicException?displayProperty=name>：参数不正确。”|
|建议|如果应用程序要注册父窗口关系且面向 .NET Framework 4.7 或更高版本，建议使用简易窗体：<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>如果用户已确定要传递的正确值是保留 <code>form.Handle</code> 值的内存位置地址，可通过将 AppContext 开关 <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> 设置为 <code>true</code> 来选择弃用此行为更改：<ol><li>以编程方式在 AppContext 上设置兼容性开关，如[此处](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)所述。</li><li>在 app.config 文件的 <code>&lt;runtime&gt;</code> 部分中添加下面的代码行：</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>相反，如果用户希望在旧版 .NET Framework 中加载应用程序时选择启用 .NET Framework 4.7 运行时上的新行为，则可将 AppContext 开关设置为 <code>false</code>。|
|范围|次要|
|Version|4.7|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|
