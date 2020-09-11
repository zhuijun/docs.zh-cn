---
ms.openlocfilehash: e92fe8364800b1775f0acc31d67aef66a42d0b95
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465872"
---
### <a name="obsolete-properties-on-consoleloggeroptions"></a><span data-ttu-id="74e85-101">ConsoleLoggerOptions 上已过时的属性</span><span class="sxs-lookup"><span data-stu-id="74e85-101">Obsolete properties on ConsoleLoggerOptions</span></span>

<span data-ttu-id="74e85-102"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 类型和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 上的一些属性现在已过时。</span><span class="sxs-lookup"><span data-stu-id="74e85-102">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and some properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are now obsolete.</span></span>

#### <a name="change-description"></a><span data-ttu-id="74e85-103">更改说明</span><span class="sxs-lookup"><span data-stu-id="74e85-103">Change description</span></span>

<span data-ttu-id="74e85-104">从 .NET 5.0 开始，<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 类型和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 上的很多属性已过时。</span><span class="sxs-lookup"><span data-stu-id="74e85-104">Starting in .NET 5.0, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and several properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are obsolete.</span></span> <span data-ttu-id="74e85-105">已过时的属性是：</span><span class="sxs-lookup"><span data-stu-id="74e85-105">The obsolete properties are:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

<span data-ttu-id="74e85-106">随着新的格式化程序的引入，这些属性现在单独的格式化程序上可用。</span><span class="sxs-lookup"><span data-stu-id="74e85-106">With the introduction of new formatters, these properties are now available on the individual formatters.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="74e85-107">更改原因</span><span class="sxs-lookup"><span data-stu-id="74e85-107">Reason for change</span></span>

<span data-ttu-id="74e85-108"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> 属性是枚举类型，不能表示自定义格式化程序。</span><span class="sxs-lookup"><span data-stu-id="74e85-108">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> property is an enumeration type, which cannot represent a custom formatter.</span></span>

<span data-ttu-id="74e85-109">其余属性是在 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> 上设置的，应用于控制台日志的这两种内置格式。</span><span class="sxs-lookup"><span data-stu-id="74e85-109">The remaining properties were set on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> and applied to both of the built-in formats for console logs.</span></span> <span data-ttu-id="74e85-110">但是，由于引入了新的格式化程序 API，在特定于格式化程序的选项上表示格式更加有意义。</span><span class="sxs-lookup"><span data-stu-id="74e85-110">However, with the introduction of a new formatter API, it makes more sense for formatting to be represented on the formatter-specific options.</span></span> <span data-ttu-id="74e85-111">这项更改可更好地区分记录器和记录器格式化程序。</span><span class="sxs-lookup"><span data-stu-id="74e85-111">This change provides better separation between the logger and logger formatters.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="74e85-112">引入的版本</span><span class="sxs-lookup"><span data-stu-id="74e85-112">Version introduced</span></span>

<span data-ttu-id="74e85-113">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="74e85-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74e85-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="74e85-114">Recommended action</span></span>

- <span data-ttu-id="74e85-115">使用新的 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> 属性代替 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="74e85-115">Use the new <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> property in place of the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="74e85-116">例如：</span><span class="sxs-lookup"><span data-stu-id="74e85-116">For example:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <span data-ttu-id="74e85-117"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> 和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> 之间有一些区别：</span><span class="sxs-lookup"><span data-stu-id="74e85-117">There are several differences between <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:</span></span>

  - <span data-ttu-id="74e85-118"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> 只有两个可能的选项：`Default` 和 `Systemd`。</span><span class="sxs-lookup"><span data-stu-id="74e85-118"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> has only two possible options: `Default` and `Systemd`.</span></span>
  - <span data-ttu-id="74e85-119"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> 不区分大小写，可以是任何字符串。</span><span class="sxs-lookup"><span data-stu-id="74e85-119"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> is case insensitive and can be any string.</span></span> <span data-ttu-id="74e85-120">保留的内置名称为 `Simple`、`Systemd` 和 `Json`（.NET 5.0 及更高版本）。</span><span class="sxs-lookup"><span data-stu-id="74e85-120">The reserved, built-in names are `Simple`, `Systemd`, and `Json` (.NET 5.0 and later).</span></span>
  - <span data-ttu-id="74e85-121">`"Format": "Systemd"` 映射到 `"FormatterName": "Systemd"`。</span><span class="sxs-lookup"><span data-stu-id="74e85-121">`"Format": "Systemd"` maps to `"FormatterName": "Systemd"`.</span></span>
  - <span data-ttu-id="74e85-122">`"Format": "Default"` 映射到 `"FormatterName": "Simple"`。</span><span class="sxs-lookup"><span data-stu-id="74e85-122">`"Format": "Default"` maps to `"FormatterName": "Simple"`.</span></span>

- <span data-ttu-id="74e85-123">对于 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat> 和 <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> 属性，请改为在新的 <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>、<xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> 或 <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 类型上使用相应的属性。</span><span class="sxs-lookup"><span data-stu-id="74e85-123">For the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>, and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> properties, use the corresponding property on the new <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>, or <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> types instead.</span></span> <span data-ttu-id="74e85-124">例如：</span><span class="sxs-lookup"><span data-stu-id="74e85-124">For example:</span></span>

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

<span data-ttu-id="74e85-125">以下两个 JSON 代码片段显示了配置文件的更改方式。</span><span class="sxs-lookup"><span data-stu-id="74e85-125">The following two JSON snippets show how the configuration file changes.</span></span> <span data-ttu-id="74e85-126">旧配置文件：</span><span class="sxs-lookup"><span data-stu-id="74e85-126">Old configuration file:</span></span>

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

<span data-ttu-id="74e85-127">新配置文件：</span><span class="sxs-lookup"><span data-stu-id="74e85-127">New configuration file:</span></span>

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

#### <a name="category"></a><span data-ttu-id="74e85-128">类别</span><span class="sxs-lookup"><span data-stu-id="74e85-128">Category</span></span>

- <span data-ttu-id="74e85-129">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="74e85-129">Core .NET libraries</span></span>
- <span data-ttu-id="74e85-130">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="74e85-130">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74e85-131">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="74e85-131">Affected APIs</span></span>

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
