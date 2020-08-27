---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720174"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a>Unix 上 UNC 路径的 URI 识别

现在，<xref:System.Uri> 类将以两个正斜杠 (`//`) 开头的字符串识别为 Unix 操作系统上的通用命名约定 (UNC) 路径。 此更改使此类字符串的行为在所有平台中保持一致。

#### <a name="change-description"></a>更改描述

在早期版本的 .NET 中，<xref:System.Uri> 类将以两个正斜杠开头的字符串（例如 `//contoso`）识别为 Unix 操作系统上的绝对文件路径。 但是，在 Windows 上，此类字符串被识别为 UNC 路径。

从 .NET 5.0 开始，<xref:System.Uri> 类将以两个正斜杠开头的字符串识别为所有平台（包括 Unix）上的 UNC 路径。 此外，属性的行为遵循 UNC 语义：

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> 返回 `true`。
- 路径中的反斜杠替换为正斜杠。 例如，`//first\second` 重命名为 `//first/second`。
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> 不对字符进行百分号编码。 例如，`//first/\uFFF0` 不转换为 `//first/%EF%BF%B0`。

#### <a name="version-introduced"></a>引入的版本

5.0

#### <a name="recommended-action"></a>建议操作

开发人员一方不需要执行任何操作。

#### <a name="category"></a>类别

Core .NET 库

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
