---
title: 将 WPF 应用迁移到 .NET Core 3.0
description: 了解如何将 Windows Presentation Foundation (WPF) 应用迁移到 .NET Core 3.0。
author: mjrousos
ms.date: 09/12/2019
ms.author: mikerou
ms.openlocfilehash: fda4f618ddb4a3edbe6f2dd9fba0b10bc618e88d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201558"
---
# <a name="migrating-wpf-apps-to-net-core"></a>将 WPF 应用迁移到 .NET Core

本文介绍将 Windows Presentation Foundation (WPF) 应用从 .NET Framework 迁移到 .NET Core 3.0 所需的步骤。 如果手头没有可供移植的 WPF 应用，但是要尝试该过程，则可以使用 [GitHub](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader) 上提供的 Bean Trader 示例应用。 原始应用（面向 .NET Framework 4.7.2）在 NetFx\BeanTraderClient 文件夹中提供。 首先，我们将说明一般情况下移植应用所需的步骤，然后演练适用于 Bean Trader 示例的特定更改。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

若要迁移到 .NET Core，必须先：

01. 了解和更新 NuGet 依赖项：

    01. 升级 NuGet 依赖项以使用 `<PackageReference>` 格式。
    01. 查看顶级 NuGet 依赖项以实现 .NET Core 或 .NET Standard 兼容性。
    01. 将 NuGet 包升级到较新版本。
    01. 使用 [.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)来了解 .NET 依赖项。

01. 将项目文件迁移到新的 SDK 样式格式：

    01. 选择是面向 .NET Core 和 .NET Framework，还是仅面向 .NET Core。
    01. 将相关项目文件属性和项复制到新的项目文件。

01. 修复生成问题：

    01. 添加对 [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility/) 包的引用。
    01. 查找并修复 API 级别差异。
    01. 删除 `appSettings` 或 `connectionStrings` 以外的 app.config 节。
    01. 如有必要，重新生成已生成的代码。

01. 运行时测试：

    01. 确认移植的应用按预期方式工作。
    01. 谨防 <xref:System.NotSupportedException> 异常。

## <a name="about-the-sample"></a>关于本示例

本文引用 [Bean Trader 示例应用](https://github.com/dotnet/windows-desktop/tree/master/Samples/BeanTrader)，因为它使用了各种依赖项，而这些依赖项类似于实际 WPF 应用可能包含的依赖项。 该应用并不大，但在复杂性方面要比“Hello World”高出一步。 该应用演示在移植实际应用时可能会遇到的一些问题。 该应用与 WCF 服务进行通信，因此若要使它正常运行，还需要运行 BeanTraderServer 项目（在同一个 GitHub 存储库中提供），并确保 BeanTraderClient 配置指向正确的终结点。 （默认情况下，该示例假设服务器在 `http://localhost:8090` 处的相同计算机上运行，如果在本地启动 BeanTraderServer，则是这种情况。）

请记住，此示例应用旨在演示 .NET Core 移植挑战和解决方案。 它并不打算演示 WPF 最佳做法。 事实上，它故意包含一些反模式，以确保在移植时至少遇到几个有趣的挑战。

## <a name="getting-ready"></a>做好准备

将 .NET Framework 应用迁移到 .NET Core 的主要挑战是其依赖项可能会以不同方式工作或根本无法工作。 迁移比以前容易得多；现在有许多 NuGet 包面向 .NET Standard。 从 .NET Core 2.0 开始，.NET Framework 和 .NET Core 外围应用已变得十分类似。 尽管如此，仍然存在一些差异（NuGet 包提供的支持和可用 .NET API）。 迁移的第一步是查看应用的依赖项，并确保引用采用的格式可轻松迁移到 .NET Core。

### <a name="upgrade-to-packagereference-nuget-references"></a>升级到 `<PackageReference>` NuGet 引用

较旧 .NET Framework 项目通常会在的 packages.config 文件中列出其 NuGet 依赖项。 新的 SDK 样式项目文件格式将 NuGet 包引用为 csproj 文件本身中的 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 元素，而不是在单独的配置文件中。

迁移时，使用 `<PackageReference>` 样式引用有两个优点：

- 这是新 .NET Core 项目文件所需的 NuGet 引用的样式。 如果已在使用 `<PackageReference>`，则可以将这些项目文件元素直接复制并粘贴到新项目中。
- 与 packages.config 文件不同，`<PackageReference>` 元素只引用项目直接依赖的顶级依赖项。 所有其他可传递 NuGet 包将在还原时确定，并记录在自动生成的 obj\project.assets.json 文件中。 这样可以更轻松地确定项目所具有的依赖项，这在确定所需依赖项是否可在 .NET Core 中正常工作时非常有用。

将 .NET Framework 应用迁移到 .NET Core 的第一步是将它更新为使用 `<PackageReference>` NuGet 引用。 Visual Studio 使此过程变得简单。 只需在 Visual Studio 的“解决方案资源管理器”中右键单击项目的 packages.config 文件，然后选择“将 packages.config 迁移到 PackageReference”。

![升级到 PackageReference](./media/convert-project-from-net-framework/package-reference-migration.png)

将出现一个对话框，显示计算出的顶级 NuGet 依赖项，并询问应将其他哪些 NuGet 包提升到顶级。 Bean Trader 示例不需要其他任何包是顶级包，因此可以取消选中所有这些框。 然后，单击“确定”，packages.config 文件会删除，而 `<PackageReference>` 元素会添加到项目文件中。

`<PackageReference>` 样式引用不会在本地将 NuGet 包存储在包文件夹中。 而是以全局方式将它们作为优化进行存储。 迁移完成之后，编辑 csproj 文件，删除任何引用以前来自 ..\packages 目录的分析器的 `<Analyzer>` 元素。 别担心；由于仍然具有 NuGet 包引用，因此这些分析器将包含在项目中。 只需清理旧的 packages.config 样式 `<Analyzer>` 元素。

### <a name="review-nuget-packages"></a>查看 NuGet 包

现在可以看到项目所依赖的顶级 NuGet 包，可以查看这些包在 .NET Core 中是否可用。 可以通过在 [nuget.org](https://www.nuget.org/) 上查看包的依赖项来确定它是否支持 .NET Core。社区创建的 [fuget.org](https://www.fuget.org/) 网站在包信息页面顶部突出显示此信息。

面向 .NET Core 3.0 时，面向 .NET Core 或 .NET Standard 的任何包都应该可正常工作（因为 .NET Core 实现了 .NET Standard 外围应用）。 在某些情况下，所用包的特定版本不面向 .NET Core 或 .NET Standard，但较新版本会面向。 在这种情况下，应考虑升级到最新版本的包。

也可以使用面向 .NET Framework 的包，但这会带来一些风险。 允许 .NET core 到 .NET Framework 的依赖项，因为 .NET Core 和 .NET Framework 外围应用非常类似，足以使此类依赖项通常可正常工作。 但是，如果包尝试使用 .NET Core 中不存在的 .NET API，则会遇到运行时异常。 因此，只应在没有其他选项可用时才引用 .NET Framework 包，并了解这样做会带来测试负担。

如果引用的包不面向 .NET Core 或 .NET Standard，则必须考虑其他替代方法：

- 是否有其他类似的包可代替使用？ 有时，NuGet 作者会发布库的单独“.Core”版本，专门面向 .NET Core。 Enterprise Library 包是社区发布“.NetCore”替代方法的一个示例。 在其他情况下，适用于特定服务的较新 SDK（有时具有不同的包名称）可用于 .NET Standard。 如果没有可用的替代方法，则可以继续使用面向 .NET Framework 的包，请记住，在 .NET Core 上运行后，需要对它们进行全面测试。

Bean Trader 示例具有以下顶级 NuGet 依赖项：

- [Castle.Windsor，版本 4.1.1](https://www.castleproject.org/projects/windsor/)  

  此包面向 .NET Standard 1.6，因此它可在 .NET Core 上正常工作。

- [Microsoft.CodeAnalysis.FxCopAnalyzers，版本 2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3)  
  这是一个元包，因此，它支持哪些平台并不明显，但[文档](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisfxcopanalyzers)指示其最新版本 (2.9.2) 将适用于 .NET Framework 和 .NET Core。

- [Nito.AsyncEx，版本 4.0.1](https://www.nuget.org/packages/Nito.AsyncEx/4.0.1)  

  此包不面向 .NET Core，但较新的 5.0 版本面向。 这在迁移时十分常见，因为许多 NuGet 包最近添加了 .NET Standard 支持，但较旧项目版本仅面向 .NET Framework。 如果版本差异只是次版本差异，则通常可轻松升级到较新版本。 由于这是主版本更改，因此需要小心升级，因为包中可能存在中断性变更。 不过，有一条很好的前进道路。

- [MahApps.Metro，版本 1.6.5](https://www.nuget.org/packages/MahApps.Metro/1.6.5)  

  此包也不面向 .NET Core，但较新的预发行版 (2.0-alpha) 面向。 同样，必须注意中断性变更，但较新的包令人鼓舞。

Bean Trader 示例的 NuGet 依赖项全都面向 .NET Standard/.NET Core，或具有面向它们的较新版本，因此此处不可能存在任何阻塞性问题。

### <a name="upgrade-nuget-packages"></a>升级 NuGet 包

如果可能，最好此时使用更近的版本升级仅面向 .NET Core 或 .NET Standard 的任何包的版本（项目仍面向 .NET Framework），以便及早发现和解决任何中断性变更。

如果不想对现有 .NET Framework 版本的应用进行任何重大更改，则可以等到具有面向 .NET Core 的新项目文件。 但是，提前将 NuGet 包升级到 .NET Core 兼容版本会使迁移过程更加轻松（即使在创建新项目文件后），并减少了应用的 .NET Framework 与 .NET Core 版本之间的差异数量。

使用 Bean Trader 示例时，可以轻松地进行所有必要的升级（使用 Visual Studio 的 NuGet 包管理器），但有一个例外：从 MahApps.Metro 1.6.5 升级到 2.0 会展示与主题和辅色管理 API 相关的中断性变更。

理想情况下，该应用将更新为使用较新版本的包（因为这更有可能在 .NET Core 上正常工作）。 但在某些情况下，这可能不可行。 在这些情况下，请不要升级 MahApps.Metro，因为所需更改十分繁琐，而本教程侧重于迁移到 .NET Core 3，而不是 MahApps.Metro 2。 另外，这是一个低风险 .NET Framework 依赖项，因为 Bean Trader 应用仅执行一小部分的 MahApps.Metro。 当然，它需要进行测试，以确保在迁移完成后所有内容都可正常工作。 如果这是一个实际方案，最好提交一个问题以跟踪迁移到 MahApps.Metro 版本 2.0 的工作，因为现在不执行迁移会留下一些技术债务。

将 NuGet 包更新到最新版本后，Bean Trader 示例项目文件中的 `<PackageReference>` 项组应如下所示。

```xml
<ItemGroup>
  <PackageReference Include="Castle.Windsor">
    <Version>4.1.1</Version>
  </PackageReference>
  <PackageReference Include="MahApps.Metro">
    <Version>1.6.5</Version>
  </PackageReference>
  <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers">
    <Version>2.9.2</Version>
  </PackageReference>
  <PackageReference Include="Nito.AsyncEx">
    <Version>5.0.0</Version>
  </PackageReference>
</ItemGroup>
```

### <a name="net-framework-portability-analysis"></a>.NET Framework 可移植性分析

了解项目 NuGet 依赖项的状态后，接下来要考虑的事项是 .NET Framework API 依赖项。 [.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)工具可用于了解项目使用的哪些 .NET API 在其他 .NET 平台上可用。

该工具作为 [Visual Studio 插件](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)、[命令行工具](https://github.com/Microsoft/dotnet-apiport/releases)或包装在[简单 GUI](https://github.com/Microsoft/dotnet-apiport-ui) 来提供，这简化了其选项。 可以在[将桌面应用移植到 .NET Core](https://devblogs.microsoft.com/dotnet/porting-desktop-apps-to-net-core/) 博客文章中了解有关通过 GUI 使用 .NET 可移植性分析器 (API Port) 的更多信息。 如果希望使用命令行，则所需步骤是：

1. 下载 [.NET 可移植性分析器](https://github.com/Microsoft/dotnet-apiport/releases)（如果尚未安装）。
1. 确保要移植 .NET Framework 应用成功生成（无论如何，在迁移之前这都是一个好主意）。
1. 使用如下所示的命令行运行 API Port。

    ```console
    ApiPort.exe analyze -f <PathToBeanTraderBinaries> -r html -r excel -t ".NET Core"
    ```

    `-f` 参数指定包含要分析的二进制文件的路径。 `-r` 参数指定所需的输出文件格式。 `-t` 参数指定要对其分析 API 使用情况的 .NET 平台。 在这种情况下，需要 .NET Core。

打开 HTML 报告时，第一个部分将列出所有已分析的二进制文件以及它们使用的 .NET API 在目标平台上可用的百分比。 该百分比本身并无意义。 更有用的是查看缺少的特定 API。 为此，请选择程序集名称或向下滚动到各个程序集的报告。

专注于你拥有源代码的程序集。 例如，在 Bean Trader ApiPort 报告中列出了很多二进制文件，但其中大多数都属于 NuGet 包。 `Castle.Windsor` 显示它依赖于 .NET Core 中缺少的某些 System.Web API。 这不必担心，因为先前已验证 `Castle.Windsor` 支持 .NET Core。 NuGet 包通常具有不同的二进制文件以用于不同的 .NET 平台，因此，只要包还面向 .NET Standard 或 .NET Core，.NET Framework 版本的 `Castle.Windsor` 是否使用 System.Web API 便无关要紧。

对于 Bean Trader 示例，需要考虑的唯一二进制文件是 BeanTraderClient，报告会显示仅缺少两个 .NET API：`System.ServiceModel.ClientBase<T>.Close` 和 `System.ServiceModel.ClientBase<T>.Open`。

![BeanTraderClient 可移植性报告](./media/convert-project-from-net-framework/portability-report.png)

这些不太可能是阻塞性问题，因为 WCF 客户端 API（多半）在 .NET Core 上受支持，因此必须有可用于这些中央 API 的替代方法。 事实上，查看 `System.ServiceModel` 的 .NET Core 外围应用（使用 <https://apisof.net>）时可发现，.NET Core 中存在异步替代方法。

根据此报告以及以前的 NuGet 依赖项分析，将 Bean Trader 示例迁移到 .NET Core 应该不会有大问题。 你已为实际开始迁移的下一步做好准备。

## <a name="migrating-the-project-file"></a>迁移项目文件

如果应用未使用新的 [SDK 样式项目文件格式](../../core/tools/csproj.md)，则需要新的项目文件以面向 .NET Core。 可以替换现有 csproj 文件，或者如果想使现有项目保持其当前状态不变，则可以添加面向 .NET Core 的新 csproj 文件。 可以使用具有[多目标](../../standard/library-guidance/cross-platform-targeting.md)（指定多个 `<TargetFrameworks>` 目标）的单个 SDK 样式项目文件，生成适用于 .NET Framework 和 .NET Core 的应用版本。

若要创建新的项目文件，可以在 Visual Studio 中创建新的 WPF 项目，或在临时目录中使用 `dotnet new wpf` 命令生成项目文件，然后将它复制/重命名为正确的位置。 还有一个社区创建的工具 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017)，可自动执行某些项目文件迁移。 该工具十分有用，但仍需要人工查看结果，以确保迁移的所有详细信息都正确。 该工具不能以最佳方式处理的一个特定方面是从 packages.config 文件迁移 NuGet 包。 如果该工具对仍使用 packages.config 文件引用 NuGet 包的项目文件运行，则它将自动迁移到 `<PackageReference>` 元素，但会为所有包（而不只是顶级包）添加 `<PackageReference>` 元素。 如果已使用 Visual Studio 迁移到 `<PackageReference>` 元素（如本示例中所做的那样），则该工具可帮助执行转换的其余部分。 正如 Scott Hanselman 在[他有关迁移 csproj 文件的博客文章](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx)中所建议的那样，手动移植具有教育意义，并且在只有几个项目要移植时可获得更好的结果。 但是，如果要移植数十个或数百个项目文件，则类似于 [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) 这样的工具可能会很有帮助。

若要为 Bean Trader 示例创建新项目文件，请在临时目录中运行 `dotnet new wpf`，并将生成的 .csproj 文件移动到 BeanTraderClient 文件夹中，并将它重命名为 BeanTraderClient.Core.csproj。

由于新项目文件格式会自动包含它在其目录中或目录下找到的 C# 文件、resx 文件和 XAML 文件，因此项目文件已几乎完成！ 若要完成迁移，请并排打开新旧项目文件并浏览旧项目文件，以查看是否包含任何需要迁移的信息。 在 Bean Trader 示例中，应将以下各项复制到新项目中：

- `<RootNamespace>`、`<AssemblyName>` 和 `<ApplicationIcon>` 属性全都应进行复制。

- 还需要将 `<GenerateAssemblyInfo>false</GenerateAssemblyInfo>` 属性添加到新项目文件，因为 Bean Trader 示例在 AssemblyInfo.cs 文件中包含程序集级别特性（如 `[AssemblyTitle]`）。 默认情况下，新的 SDK 样式项目将基于 csproj 文件中的属性来自动生成这些特性。 因为在此例中不希望发生这种情况（自动生成的特性会与 AssemblyInfo.cs 中的特性冲突），所以可以通过 `<GenerateAssemblyInfo>` 禁用自动生成的特性。

- 虽然 resx 文件会作为嵌入的资源自动包含在内，但其他 `<Resource>` 项（如图像）不会这样。 因此，复制 `<Resource>` 元素以用于嵌入图像和图标文件。 可以使用新项目文件格式对 glob 模式的支持将 png 引用简化为单行：`<Resource Include="**\*.png" />`。

- 同样，`<None>` 项会自动包含在内，但它们在默认情况下不会复制到输出目录。 由于 Bean Trader 项目包含复制到输出目录的 `<None>` 项（使用 `PreserveNewest` 行为），因此需要为该文件更新自动填充的 `<None>` 项，如下所示。

  ```xml
  <None Update="BeanTrader.pfx">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
  ```

- Bean Trader 示例包含一个 XAML 文件 (Default.Accent.xaml) 作为 `Content`（而不是作为 `Page`），因为在运行时会从文件的 XAML 加载此文件中定义的主题和辅色，而不是嵌入在应用本身中。 但是，新项目系统会自动将此文件作为 `<Page>` 包含在内，因为它是 XAML 文件。 因此，需要删除作为页面的 XAML 文件 (`<Page Remove="**\Default.Accent.xaml" />`)，并将它添加为内容。

  ```xml
  <Content Include="Resources\Themes\Default.Accent.xaml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </Content>
  ```

- 最后，通过复制具有所有 `<PackageReference>` 元素的 `<ItemGroup>` 来添加 NuGet 引用。 如果以前未将 NuGet 包升级到与 .NET Core 兼容的版本，则可以现在执行该操作，因为包引用处于特定于 .NET Core 的项目中。

此时，应该可以将新项目添加到 BeanTrader 解决方案，并在 Visual Studio 中打开它。 项目应在“解决方案资源管理器”中正确显示，`dotnet restore BeanTraderClient.Core.csproj` 应成功还原包（有两个与面向 .NET Framework 使用的 MahApps.Metro 版本相关的预期警告）。

尽管可以并排保留两个项目文件（如果要完全按照原样继续生成旧项目，甚至可能需要这样做），但它会使迁移过程复杂化（两个项目将尝试使用相同的 bin 和 obj 文件夹），并且通常是不必要的。 如果要同时为 .NET Core 和 .NET Framework 目标进行生成，则可以改为将新项目文件中的 `<TargetFramework>netcoreapp3.0</TargetFramework>` 属性替换为 `<TargetFrameworks>netcoreapp3.0;net472</TargetFrameworks>`。 对于 Bean Trader 示例，删除旧项目文件 (BeanTraderClient.csproj)，因为不再需要它。 如果想要同时保留两个项目文件，请务必让它们生成到不同的输出和中间输出路径。

## <a name="fix-build-issues"></a>修复生成问题

移植过程的第三步是获取要生成的项目。 将项目文件转换为 SDK 样式项目后，某些应用已成功生成。 如果你的应用是这种情况，那么祝贺你！ 可以转到步骤 4。 其他应用需要一些更新才能针对 .NET Core 进行生成。 例如，如果现在尝试对 Bean Trader 示例项目运行 `dotnet build`（或在 Visual Studio 中生成它），将会出现许多错误，但是可以快速修复它们。

### <a name="systemservicemodel-references-and-microsoftwindowscompatibility"></a>System.ServiceModel 引用和 Microsoft.Windows.Compatibility

常见错误源是对可用于 .NET Core 但不会自动包含在 .NET Core 应用元包中的 API 缺少引用。 若要解决此情况，应引用 `Microsoft.Windows.Compatibility` 包。 兼容性包中包含一组广泛的在 Windows 桌面应用中十分常见的 API，例如 WCF 客户端、目录服务、注册表、配置、ACL API 等。

对于 Bean Trader 示例，大多数生成错误是由于缺少 <xref:System.ServiceModel> 类型引起的。 可以通过引用必要的 WCF NuGet 包来解决这些问题。 不过，WCF 客户端 API 处于 `Microsoft.Windows.Compatibility` 包中，因此引用兼容性包是更好的解决方案（因为它还解决与 API 相关的任何问题以及兼容性包提供的 WCF 问题解决方案）。 `Microsoft.Windows.Compatibility` 包在大多数 .NET Core 3.0 WPF 和 WinForms 移植方案中会很有帮助。 将 NuGet 引用添加到 `Microsoft.Windows.Compatibility` 之后，只剩下一个生成错误！

### <a name="cleaning-up-unused-files"></a>清理未使用的文件

经常出现的一种类型的迁移问题与以前未包含在生成中的 C# 和 XAML 文件相关，而自动包含所有源文件的新 SDK 样式项目会选择它们。

在 Bean Trader 示例中看到的下一个生成错误是指 OldUnusedViewModel.cs 中的错误接口实现。 文件名是一个提示，但在检查时，你会发现此源文件不正确。 它以前不会导致问题，因为原始 .NET Framework 项目中未包含它。 现在会自动包含磁盘上存在但未包含在旧 csproj 中的源文件。

对于这类一次性问题，可方便地与以前的 csproj 进行比较，以确认不需要该文件，然后对它执行 `<Compile Remove="" />`，或者如果任何位置都不再需要源文件，可删除它。 在此例中，可安全地只是删除 OldUnusedViewModel.cs。

如果有许多需要以这种方式排除的源文件，则可以通过在项目文件中将 `<EnableDefaultCompileItems>` 属性设置为 false 来禁用 C# 文件的自动包含。 然后，可以将 `<Compile Include>` 项从旧项目文件复制到新文件，以便仅生成要包含的源文件。 同样，`<EnableDefaultPageItems>` 可用于关闭 XAML 页面的自动包含，而 `<EnableDefaultItems>` 可以通过单个属性控制这两者。

### <a name="a-brief-aside-on-multi-pass-compilers"></a>多遍编译器简介

从 Bean Trader 示例中删除有问题的文件之后，可以重新生成，将收到四个错误。 之前是否遇到过其中一个？ 为什么错误数量会上升？ C# 编译器是[多遍编译器](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)。 这意味着它会浏览每个源文件两次。 首先，编译器仅查看每个源文件中的元数据和声明，并标识任何声明级别问题。 这些是已修复的错误。 然后，它会再次浏览代码以将 C# 源文件生成为 IL；这些是现在看到的第二组错误。

> [!NOTE]
> C# 编译器[不仅是浏览两次](https://docs.microsoft.com/archive/blogs/ericlippert/how-many-passes)，但最终结果是，类似于这样的大型代码更改的编译器错误往往以两个波次的形式出现。

### <a name="third-party-dependency-fixes-castlewindsor"></a>第三方依赖项修补程序 (Castle.Windsor)

在某些迁移方案中出现的另一类问题是 .NET Framework 与 .NET Core 版本的依赖项之间的 API 差异。 即使 NuGet 包同时面向 .NET Framework 和 .NET Standard 或 .NET Core，也可能会有不同的库用于不同的 .NET 目标。 这使包可以支持许多不同的 .NET 平台，而这可能需要不同的实现。 这还意味着，在面向不同的 .NET 平台时，库中可能存在较小的 API 差异。

将在 Bean Trader 示例中看到的下一组错误与 `Castle.Windsor` API 相关。 .NET Core Bean Trader 项目使用的 `Castle.Windsor` 版本与面向 .NET Framework 的项目相同 (4.1.1)，但适用于这两个平台的实现略有不同。

在此例中，你将看到以下需要修复的问题：

1. `Castle.MicroKernel.Registration.Classes.FromThisAssembly` 在 .NET Core 上不可用。 不过有类似的 API `Classes.FromAssemblyContaining` 可用，因此我们可以将 `Classes.FromThisAssembly()` 的两次使用替换为对 `Classes.FromAssemblyContaining(t)` 的调用，其中 `t` 是进行调用的类型。
1. Bootstrapper.cs 中的 `Castle.Windsor.Installer.FromAssembly` 也是如此。这在 .NET Core 中不可用。 相反，该调用可以替换为 `FromAssembly.Containing(typeof(Bootstrapper))`。

### <a name="updating-wcf-client-usage"></a>更新 WCF 客户端使用

修复了 `Castle.Windsor` 差异后，.NET Core Bean Trader 项目中剩下的最后一个生成错误是 `BeanTraderServiceClient`（派生自 `DuplexClientBase`）没有 `Open` 方法。 这并不令人吃惊，因为在此迁移过程开始时，.NET 可移植性分析器便突出显示了此 API。 不过，查看 `BeanTraderServiceClient` 会让我们注意到一个更大的问题。 此 WCF 客户端由 [Svcutil.exe](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具自动生成。

Svcutil 生成的 WCF 客户端旨在用于 .NET Framework。

使用 svcutil 生成的 WCF 客户端的解决方案将需要重新生成与 .NET Standard 兼容的客户端以用便与 .NET Core 一起使用。 旧客户端无法正常工作的主要原因之一是它们依赖于应用配置来定义 WCF 绑定和终结点。 由于 .NET Standard WCF API 可以跨平台工作（其中 System.Configuration API 不可用），因此适用于 .NET Core 和 .NET Standard 方案的 WCF 客户端必须以编程方式（而不是在配置中）定义绑定和终结点。

事实上，依赖于 `<system.serviceModel>` app.config 节的任何 WCF 客户端使用（无论是使用 Svcutil 还是手动创建）都需要进行更改以在 .NET Core 上正常工作。

可以通过两种方式自动生成与 .NET Standard 兼容的 WCF 客户端：

- `dotnet-svcutil` 工具是一种 .NET 工具，它生成 WCF 客户端的方式与 Svcutil 以前的工作方式类似。
- Visual Studio 可以使用其连接的服务功能的 [WCF Web Service Reference](../../core/additional-tools/wcf-web-service-reference-guide.md) 选项生成 WCF 客户端。

这两种方法都行之有效。 当然，也可以自己编写 WCF 客户端代码。 对于此示例，我选择使用 Visual Studio 连接的服务功能。 若要执行该操作，请在 Visual Studio 的解决方案资源管理器中右键单击 BeanTraderClient.Core 项目，然后选择“添加” > “连接的服务”。 接下来，选择 WCF Web Service Reference Provider。 这会显示一个对话框，可以在其中指定后端 Bean Trader Web 服务的地址（如果是在本地运行服务器，则为 `localhost:8080`）和生成的类型应使用的命名空间（例如 BeanTrader.Service）。

![WCF Web Service Reference“连接的服务”对话框](./media/convert-project-from-net-framework/connected-service-dialog.png)

选择“完成”按钮之后，将向项目添加新的“连接的服务”节点，并在该节点下添加一个 Reference.cs 文件，其中包含用于访问 Bean Trader 服务的新 .NET Standard WCF 客户端。 如果查看该文件中的 `GetEndpointAddress` 或 `GetBindingForEndpoint` 方法，则会看到现在是以编程方式（而不是通过应用配置）生成绑定和终结点。 “添加连接的服务”功能可能还会在项目文件中添加对某些 System.ServiceModel 包的引用，这些引用并不需要，因为所有必需的 WCF 包都通过 Microsoft.Windows.Compatibility 包含在内。 检查 csproj 以查看是否添加了任何额外的 System.ServiceModel `<PackageReference>` 项，如果是，则删除它们。

现在，我们的项目具有新的 WCF 客户端类（在 Reference.cs 中），但是它也仍然具有旧的类（在 BeanTrader.cs 中）。 此时有两个选项：

- 如果希望能够生成原始 .NET Framework 项目（与面向 .NET Core 的新项目一起），则可以在 .NET Core 项目的 csproj 文件中使用 `<Compile Remove="BeanTrader.cs" />` 项，使应用的 .NET Framework 和 .NET Core 版本使用不同的 WCF 客户端。 这样做的优点是使现有 .NET Framework 项目不变，但缺点是，使用生成的 WCF 客户端的代码在 .NET Core 情况下可能需要与在 .NET Framework 项目中略有不同，因此可能需要使用 `#if` 指令有条件地编译某些 WCF 客户端使用（例如创建客户端），以便在针对 .NET Core 进行生成时以一种方式工作，而在针对 .NET Framework 进行生成时以另一种方式工作。

- 另一方面，如果现有 .NET Framework 项目中的一些代码改动是可接受的，则可以将 BeanTrader.cs 全部删除。 由于新 WCF 客户端是针对 .NET Standard 而生成的，因此它将在 .NET Core 和 .NET Framework 方案中正常工作。 如果除了 .NET Core 之外，还要针对 .NET Framework 进行生成（通过多目标或具有两个 csproj 文件），则可以这一新的 Reference.cs 文件用于这两个目标。 此方法的优点是，代码无需分叉即可支持两个不同的 WCF 客户端；将在所有位置使用相同的代码。 缺点是它涉及更改（可能稳定的）.NET Framework 项目。

对于 Bean Trader 示例，如果使迁移更简单，则可以对原始项目进行少量更改，因此请按照以下步骤来协调 WCF 客户端使用：

01. 使用解决方案资源管理器中的“添加现有项”上下文菜单将新 Reference.cs 文件添加到 .NET Framework BeanTraderClient.csproj 项目。 请务必添加为“链接”，以便两个项目使用相同文件（与复制 C# 文件相反）。 如果在使用单个 csproj 同时针对 .NET Core 和 .NET Framework 进行生成（使用多目标），则无需执行此步骤。

01. 删除 BeanTrader.cs。

01. 新 WCF 客户端类似于旧客户端，但生成的代码中的一些命名空间是不同的。 因此需要更新项目，以便通过 BeanTrader.Service（或所选的任何命名空间名称）使用 WCF 客户端类型（而不是 BeanTrader.Model 或不使用命名空间）。 生成 BeanTraderClient.Core.csproj 将有助于标识需要进行这些更改的位置。 C# 和 XAML 源文件中都需要进行修复。

01. 最后会发现 BeanTraderServiceClientFactory.cs 中有一个错误，因为 `BeanTraderServiceClient` 类型的可用构造函数已更改。 过去可以提供 `InstanceContext` 参数（从 `Castle.Windsor` IoC 容器使用 `CallbackHandler` 进行创建）。 新构造函数会创建新 `CallbackHandler`。 但是，`BeanTraderServiceClient`的基类型中存在与所需内容匹配的构造函数。 由于自动生成的 WCF 客户端代码全都存在于分部类中，因此可以轻松地对它进行扩展。 为此，请创建一个名为 BeanTraderServiceClient.cs 的新文件，然后创建一个具有该相同名称的分部类（使用 BeanTrader.Service 命名空间）。 然后，将一个构造函数添加到该分部类型，如下所示。

    ```csharp
    public BeanTraderServiceClient(System.ServiceModel.InstanceContext callbackInstance) :
        base(callbackInstance, EndpointConfiguration.NetTcpBinding_BeanTraderService)
            { }
    ```

进行这些更改后，Bean Trader 示例现在使用与 .NET Standard 兼容的新 WCF 客户端，你可以在 TradingService.cs 中进行更改 `Open` 调用的最终修复，以改用使用 `await OpenAsync`。

解决了 WCF 问题后，Bean Trader 示例的 .NET Core 版本现在可完全生成！

## <a name="runtime-testing"></a>运行时测试

很容易忘记的一点是，项目针对 .NET Core 完全生成后，迁移工作并未就此完成。 为测试移植的应用留出时间也非常重要。 成功生成后，确保应用可按预期运行和工作，尤其是在使用任何面向 .NET Framework 的包时。

让我们尝试启动移植的 Bean Trader 应用，来看看会发生什么情况。 该应用不久便失败，出现以下异常。

```output
System.Configuration.ConfigurationErrorsException: 'Configuration system failed to initialize'

Inner Exception
ConfigurationErrorsException: Unrecognized configuration section system.serviceModel.
```

这当然很有意义。 请记住，WCF 不再使用应用配置，因此需要删除 app.config 文件的旧 system.serviceModel 节。 更新的 WCF 客户端在其代码中包含所有相同的信息，因此不再需要该 config 节。 如果希望可在 app.config 中配置 WCF 终结点，则可以将它添加为应用设置，并更新 WCF 客户端代码，以从配置中检索 WCF 服务终结点。

删除 app.config 的 system.serviceModel 节之后，应用将启动，但是在用户登录时会失败，并出现另一个异常。

```output
System.PlatformNotSupportedException: 'Operation is not supported on this platform.'
```

不支持的 API 为 `Func<T>.BeginInvoke`。 如 [dotnet/corefx#5940](https://github.com/dotnet/corefx/issues/5940) 中所述，由于基础远程处理依赖项，.NET Core 不支持委托类型上的 `BeginInvoke` 和 `EndInvoke` 方法。 此问题及其修复在[针对 .NET Core 迁移 Delegate.BeginInvoke 调用](https://devblogs.microsoft.com/dotnet/migrating-delegate-begininvoke-calls-for-net-core/)博客文章中进行了更详细的说明，但要点是应将 `BeginInvoke` 和 `EndInvoke` 调用替换为 `Task.Run`（如果可能，则替换为异步替代方法）。 在此处应用常规解决方案，`BeginInvoke` 调用可以替换为由 `Task.Run` 启动的 `Invoke` 调用。

```csharp
Task.Run(() =>
{
    return userInfoRetriever.Invoke();
}).ContinueWith(result =>
{
    // BeginInvoke's callback is replaced with ContinueWith
    var task = result.ConfigureAwait(false);
    CurrentTrader = task.GetAwaiter().GetResult();
}, TaskScheduler.Default);
```

删除 `BeginInvoke` 使用之后，Bean Trader 应用可在 .NET Core 上成功运行！

![在 .NET Core 上运行的 Bean Trader](./media/convert-project-from-net-framework/running-on-core.png)

所有应用都是不同的，因此将自己的应用迁移到 .NET Core 所需的具体步骤会有所不同。 不过希望 Bean Trader 示例可演示常规工作流以及可以预期的问题类型。 而且，尽管本文篇幅很长，但是 Bean Trader 示例中使它可在 .NET Core 上正常工作所需的实际更改是相当有限的。 许多应用以相同方式迁移到 .NET Core；只需要进行有限的代码更改，甚至不需要任何更改。
