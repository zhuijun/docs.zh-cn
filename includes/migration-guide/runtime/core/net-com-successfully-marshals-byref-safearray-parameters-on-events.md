---
ms.openlocfilehash: 1907c9b82c9685899d328f67da8001c0fa4fb697
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497860"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM 成功封送事件上的 ByRef SafeArray 参数

#### <a name="details"></a>详细信息

在 .NET Framework 4.7.2 及更低版本中，COM 事件上的 ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) 参数无法封送回本机代码。  进行此更改后，[SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) 现在可成功进行封送。<ul><li>[x] Quirked</li></ul>

#### <a name="suggestion"></a>建议

如果正确封送 COM 事件上的 ByRef SafeArray 参数会中断执行，则可以通过将以下配置开关添加到应用程序配置来禁用此代码：<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.8|
|类型|运行时|

#### <a name="affected-apis"></a>受影响的 API

无法通过 API 分析检测到。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
