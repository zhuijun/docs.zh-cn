---
ms.openlocfilehash: 49041ce906ab0bb8b9482b79c44302465c4ca788
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702312"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a>全球化 API 在 Windows 上使用 ICU 库

当在 Windows 10 2019 年 5 月更新或更高版本上运行时，.NET 5.0 及更高版本使用 [Unicode 国际组件 (ICU)](http://site.icu-project.org/home) 库来实现全球化功能。

#### <a name="change-description"></a>更改描述

以前，.NET 库使用[区域语言支持 (NLS)](/windows/win32/intl/national-language-support) API 来实现全球化功能。 例如，NLS 函数用于获取区域性数据（例如日期和时间格式模式），比较字符串，并在适当的区域中执行字符串大小写。

从 .NET 5.0 开始，如果应用在 Windows 10 2019 年 5 月更新或更高版本上运行，.NET 库将使用 [ICU](http://site.icu-project.org/home) 全球化 API。 Windows 10 2019 年 5 月更新及更高版本随 ICU 本机库一起提供。 如果 .NET 运行时无法加载 ICU，它将改用 NLS。

引入此更改的原因有两个：

- 应用跨平台（包括 Linux、macOS 和 Windows）具有相同的全球化行为。
- 应用可以通过使用自定义 ICU 库来控制全球化行为。

#### <a name="version-introduced"></a>引入的版本

.NET 5.0 预览版 4

#### <a name="recommended-action"></a>建议操作

开发人员一方不需要执行任何操作。 但是，如果你想要继续使用 NLS 全球化 API，则可以将[运行时开关](../../../../docs/core/run-time-config/globalization.md#nls)设置为还原到该行为。

#### <a name="category"></a>类别

全球化

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <xref:System.Globalization?displayProperty=fullName> 命名空间中的大多数类型

<!--

#### Affected APIs

- `T:System.Span%601`
- `T:System.String`
- `N:System.Globalization`

-->
