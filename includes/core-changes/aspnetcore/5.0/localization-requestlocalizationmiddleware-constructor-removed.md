---
ms.openlocfilehash: db941229e02064ee856829417d6762aa17b0b926
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309131"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>本地化：请求本地化中间件中删除了已过时的构造函数

缺少 <xref:Microsoft.Extensions.Logging.ILoggerFactory> 参数的 <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> 构造函数[在此提交中](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)被标记为已过时。 ASP.NET Core 5.0 中删除了已过时的构造函数。 有关讨论，请参阅 [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785)。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 8

#### <a name="old-behavior"></a>旧行为

存在已过时的 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 构造函数。

#### <a name="new-behavior"></a>新行为

不存在已过时的 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 构造函数。

#### <a name="reason-for-change"></a>更改原因

此更改可确保请求本地化中间件始终有权访问记录器。

#### <a name="recommended-action"></a>建议操作

在手动构造 `RequestLocalizationMiddleware` 实例时，在构造函数中传递 `ILoggerFactory` 实例。 如果在该上下文中没有可用的有效 `ILoggerFactory` 实例，请考虑为中间件构造函数传递 <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> 实例。

#### <a name="category"></a>类别

ASP.NET Core

#### <a name="affected-apis"></a>受影响的 API

[RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
