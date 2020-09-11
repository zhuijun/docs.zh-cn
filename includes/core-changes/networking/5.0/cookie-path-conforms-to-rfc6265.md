---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465503"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>Cookie 路径处理现在符合 RFC 6265

[RFC 6265](https://tools.ietf.org/html/rfc6265) 中定义的路径处理算法是针对 <xref:System.Net.Cookie> 和 <xref:System.Net.CookieContainer> 类实现的。

#### <a name="version-introduced"></a>引入的版本

5.0

#### <a name="change-description"></a>更改描述

- 无需再将 <xref:System.Net.Cookie.Path> 属性作为请求路径的前缀。
- <xref:System.Net.Cookie.Path> 的默认值的计算和路径匹配算法是按照 RFC 6265 的[第 5.1.4 节](https://tools.ietf.org/html/rfc6265#section-5.1.4)中的定义实现的。

#### <a name="recommended-action"></a>建议操作

在大多数情况下，无需执行任何操作。 但是，如果代码依赖于 <xref:System.Net.Cookie.Path> 验证，则需要在代码中实现所需的验证。 如果代码依赖于 <xref:System.Net.Cookie.Path> 的默认值计算，请考虑手动提供 <xref:System.Net.Cookie.Path> 值，而不使用默认值。

#### <a name="category"></a>类别

网络

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
