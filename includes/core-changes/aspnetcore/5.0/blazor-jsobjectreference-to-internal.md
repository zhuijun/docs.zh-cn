---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077587"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Blazor：JSObjectReference 和 JSInProcessObjectReference 类型已更改为 internal

ASP.NET Core 5.0 RC1 中引入的新的 `Microsoft.JSInterop.JSObjectReference` 和 `Microsoft.JSInterop.JSInProcessObjectReference` 类型已被标记为 `internal`。

#### <a name="version-introduced"></a>引入的版本

5.0 RC2

#### <a name="old-behavior"></a>旧行为

可以通过 `IJSRuntime` 从 JavaScript 互操作调用中获取 `JSObjectReference`。 例如：

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a>新行为

`JSObjectReference` 使用 [internal](../../../../docs/csharp/language-reference/keywords/internal.md) 访问修饰符。 必须改为使用 `public` `IJSObjectReference` 接口。 例如：

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` 也被标记为 `internal` 并由 `IJSInProcessObjectReference` 替换。

#### <a name="reason-for-change"></a>更改原因

此更改使 JavaScript 互操作功能与 Blazor 中的其他模式更加一致。 `IJSObjectReference` 类似于 `IJSRuntime`，因为它有类似的目的，并且有类似的方法和扩展。

#### <a name="recommended-action"></a>建议操作

分别用 `IJSObjectReference` 和 `IJSInProcessObjectReference` 替换出现的 `JSObjectReference` 和 `JSInProcessObjectReference`。

#### <a name="category"></a>类别

ASP.NET Core

#### <a name="affected-apis"></a>受影响的 API

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
