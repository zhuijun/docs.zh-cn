---
ms.openlocfilehash: c10d617e07ca2fa0239298d449d93cf833b83fce
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275497"
---
### <a name="calls-to-claimsidentity-constructors"></a>调用 ClaimsIdentity 构造函数

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.6.2 开始，具有 <xref:System.Security.Principal.IIdentity?displayProperty=name> 参数的 <xref:System.Security.Claims.ClaimsIdentity> 构造函数设置 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 属性的方式发生了变化。 如果 <xref:System.Security.Principal.IIdentity?displayProperty=name> 参数是 <xref:System.Security.Claims.ClaimsIdentity> 对象，且该 <xref:System.Security.Claims.ClaimsIdentity> 对象的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 属性不为 <code>null</code>，则 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 属性是使用 <xref:System.Security.Claims.ClaimsIdentity.Clone> 方法附加的。 在 Framework 4.6.1 及早期版本中，<xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 属性作为现有引用进行附加。由于此更改，从 .NET Framework 4.6.2 开始，新 <xref:System.Security.Claims.ClaimsIdentity> 对象的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 属性不等于构造函数的 <xref:System.Security.Principal.IIdentity?displayProperty=name> 参数的 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> 属性。 在 .NET Framework 4.6.1 及更早版本中，它们是相等的。|
|建议|如果不需要此行为，可以在应用程序配置文件中将 <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> 开关设置为 <code>true</code>，从而还原旧行为。 为此，必须在 web.config 文件的 <code>&lt;runtime&gt;</code> 部分中添加以下内容：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|Version|4.6.2|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)></li></ul>|
