---
ms.openlocfilehash: 41e80a9dbcfa2a857e0b52674ef0724a542458a0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539445"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>本地化：ResourceManagerWithCultureStringLocalizer 类和 WithCulture 接口成员已删除

.NET 5.0 预览版 1 删除了 [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) 类和 [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) 方法。

有关上下文，请参阅 [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) 和 [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324)。 有关此更改的讨论，请参阅 [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756)。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 1

#### <a name="old-behavior"></a>旧行为

`ResourceManagerWithCultureStringLocalizer` 类和 `ResourceManagerStringLocalizer.WithCulture` 方法[在 .NET Core 3.0 预览版 3 及更高版本中已过时](../../../../docs/core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)。

#### <a name="new-behavior"></a>新行为

.NET 5.0 预览版 1 中删除了 `ResourceManagerWithCultureStringLocalizer` 类和 `ResourceManagerStringLocalizer.WithCulture` 方法。 有关所做更改的清单，请参阅 [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files) 上的拉取请求。

#### <a name="reason-for-change"></a>更改原因

[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) 类和 [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) 方法通常会让本地化用户混淆。 创建自定义 <xref:Microsoft.Extensions.Localization.IStringLocalizer> 实现时，混淆尤其严重。 这个类和方法给使用者的印象是 `IStringLocalizer` 实例应“按语言、按资源”。 实际上，实例应该仅“按资源”。 在运行时，<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 属性确定要使用的语言。

#### <a name="recommended-action"></a>建议操作

停止使用 `ResourceManagerWithCultureStringLocalizer` 类和 `ResourceManagerStringLocalizer.WithCulture` 方法。

#### <a name="category"></a>类别

ASP.NET Core

#### <a name="affected-apis"></a>受影响的 API

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
