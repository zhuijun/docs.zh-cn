---
ms.openlocfilehash: e92fe8364800b1775f0acc31d67aef66a42d0b95
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465872"
---
### <a name="obsolete-properties-on-consoleloggeroptions"></a>ConsoleLoggerOptions 上已过时的属性

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 类型和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 上的一些属性现在已过时。

#### <a name="change-description"></a>更改说明

从 .NET 5.0 开始，<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 类型和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 上的很多属性已过时。 已过时的属性是：

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

随着新的格式化程序的引入，这些属性现在单独的格式化程序上可用。

#### <a name="reason-for-change"></a>更改原因

<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> 属性是枚举类型，不能表示自定义格式化程序。

其余属性是在 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 上设置的，应用于控制台日志的这两种内置格式。 但是，由于引入了新的格式化程序 API，在特定于格式化程序的选项上表示格式更加有意义。 这项更改可更好地区分记录器和记录器格式化程序。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 8

#### <a name="recommended-action"></a>建议操作

- 使用新的 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> 属性代替 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> 属性。 例如：

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> 和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> 之间有一些区别：

  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> 只有两个可能的选项：`Default` 和 `Systemd`。
  - <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> 不区分大小写，可以是任何字符串。 保留的内置名称为 `Simple`、`Systemd` 和 `Json`（.NET 5.0 及更高版本）。
  - `"Format": "Systemd"` 映射到 `"FormatterName": "Systemd"`。
  - `"Format": "Default"` 映射到 `"FormatterName": "Simple"`。

- 对于 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> 和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> 属性，请改为在新的 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>、<xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> 或 <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 类型上使用相应的属性。 例如：

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

以下两个 JSON 代码片段显示了配置文件的更改方式。 旧配置文件：

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "Format": "Systemd",
      "IncludeScopes": true,
      "TimestampFormat": "HH:mm:ss",
      "UseUtcTimestamp": true
    }
  },
  "AllowedHosts": "*"
}
```

新配置文件：

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "FormatterName": "Systemd",
      "FormatterOptions": {
        "IncludeScopes": true,
        "TimestampFormat": "HH:mm:ss",
        "UseUtcTimestamp": true
      }
    }
  },
  "AllowedHosts": "*"
}
```

#### <a name="category"></a>类别

- Core .NET 库
- ASP.NET

#### <a name="affected-apis"></a>受影响的 API

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
