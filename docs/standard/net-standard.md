---
title: .NET Standard
description: 了解 .NET Standard 及其版本以及支持它的 .NET 实现。
ms.date: 02/13/2020
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: b52d69756d85e3e422b798c3ac7d53de3b538b8d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167411"
---
# <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) 是一套正式的 .NET API 规范，有望在所有 .NET 实现中推出。 推出 .NET Standard 的背后动机是要提高 .NET 生态系统中的一致性。 [ECMA 335](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) 继续为 .NET 实现行为建立统一性，尽管 ECMA 335 指定了一小组标准库，但 .NET Standard 规范包含范围更广的 .NET API。

.NET Standard 可实现以下重要情境：

- 为要实现的所有 .NET 实现定义一组统一的、与工作负荷无关的 BCL API。
- 使开发人员能够通过同一组 API 生成可在各种 .NET 实现中使用的可移植库。
- 减少甚至消除由于 .NET API 方面的原因而对共享源代码进行的条件性编译（仅适用于 OS API）。

各种 .NET 实现以特定版本的 .NET Standard 为目标。 每个 .NET 实现版本都会公布它所支持的最高 .NET Standard 版本，这种声明意味着它也支持以前的版本。 例如，.NET Framework 4.6 实现 .NET Standard 1.3。也就是说，它会公开在 .NET Standard 版本 1.0 到 1.3 中定义的所有 API。 同样，.NET Framework 4.6.1 实现 .NET Standard 1.4，而 .NET Core 1.0 则实现 .NET Standard 1.6。

## <a name="net-implementation-support"></a>.NET 实现支持

下表列出了支持每个 .NET Standard 版本的**最低**平台版本。 这意味着所列平台的更高版本也支持相应的 .NET Standard 版本。 例如，.NET Core 2.2 支持 .NET Standard 2.0 及更低版本。

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

若要查找可以定位的 .NET Standard 最高版本，请按照以下步骤操作：

1. 查找要运行的 .NET 实现所在的行。
2. 在这一行中从右向左查找可以定位的 .NET Standard 版本所在的列。
3. 列标题指示目标支持的 .NET Standard 版本。 此外可以面向任何更低的 .NET Standard 版本。 更高版本的 .NET Standard 还支持实现。
4. 对要定位的每个平台重复执行此过程。 如果有多个目标平台，应选择它们都支持的最高版本。 例如，如果要在 .NET Framework 4.5 和 .NET Core 1.0 上运行，可以使用的最高 .NET Standard 版本是 .NET Standard 1.1。

### <a name="which-net-standard-version-to-target"></a>要定位哪个 .NET Standard 版本

选择 .NET Standard 版本时，应权衡以下因素：

- 版本越高，可使用的 API 就越多。
- 版本越低，可实现它的平台就越多。

一般来说，建议尽可能定位*最低*版本 .NET Standard。 因此，在找到可以定位的最高版本 .NET Standard 后，请按照以下步骤操作：

1. 定位前一更低版本的 .NET Standard，然后生成项目。
2. 如果成功生成项目，请重复执行第 1 步。 否则，重新定位到后一较高版本，这就是应该使用的版本。

但是，定位更低版本的 .NET Standard 会引入许多支持依赖项。 如果项目定位 .NET Standard 1.x，我们建议  还定位 .NET Standard 2.0。 这简化了在 .NET Standard 2.0 兼容框架上运行的库的用户的依赖项关系图，并减少了下载所需的包数。

### <a name="net-standard-versioning-rules"></a>.NET Standard 版本控制规则

版本控制规则主要有两个：

- 累加性：.NET Standard 版本在逻辑上形成同心圆。也就是说，较高的版本包含较低版本的所有 API。 版本之间没有重大更改。
- 不可变：一旦发布，.NET Standard 版本就会冻结起来。 新 API 首先会在特定的 .NET 实现（如 .NET Core）中可用。 如果 .NET Standard 评审委员会认为新 API 应可用于所有 .NET 实现，则会将它们添加到新的 .NET Standard 版本中。

## <a name="specification"></a>规范

.NET Standard 规范是一组标准化的 API。 此规范由 .NET 实现者（具体而言，由 Microsoft（包括 .NET Framework、NET Core 和 Mono）和 Unity）进行维护。 在通过 [GitHub](https://github.com/dotnet/standard) 建立新 .NET Standard 版本的过程中，采用公众反馈流程。

### <a name="official-artifacts"></a>正式项目

正式规范是一组用于定义标准中包含的 API 的 .cs 文件。 [dotnet/standard 存储库](https://github.com/dotnet/standard)中的 [Ref 目录](https://github.com/dotnet/standard/tree/master/src/netstandard/ref)定义了 .NET Standard API。

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) 元包（[源代码](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)）描述用于部分定义一个或多个 .NET Standard 版本的库集。

给定的组件（如 `System.Runtime`）描述：

- .NET Standard 的一部分（即其范围）。
- .NET Standard 在此范围内的多个版本。

标准库提供派生项目以方便读取，并实现某些开发人员方案（例如，使用编译器）。

- [Markdown 中的 API 列表](https://github.com/dotnet/standard/tree/master/docs/versions)
- 引用程序集，以 NuGet 包的形式分发，由 [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) 元包引用。

### <a name="package-representation"></a>包表示形式

.NET Standard 引用程序集的主要分发载体是 NuGet 包。 实现会以适用于每个 .NET 实现的各种方式提供。

NuGet 包面向一个或多个[框架](frameworks.md)。 .NET Standard 包定位“.NET Standard”框架。 可以使用 `netstandard` [精简 TFM](frameworks.md)（例如 `netstandard1.4`）来设定 .NET Standard 框架作为目标。 如果构建的库将用于在多个运行时上运行，就应将此框架作为目标。 对于最广泛的 API 集，将 `netstandard2.0` 设定为目标，因为 .NET Standard 2.0 的可用 API 数量比 .NET Standard 1.6 的两倍还多。

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) 元包引用定义 .NET Standard 的一整套 NuGet 包。  要指定 `netstandard` 作为目标，最常见的方法是引用此元包。 它描述并提供了对大约 40 个 .NET 库及定义 .Net Standard 的相关 API 的访问权限。 可以引用以 `netstandard` 为目标的其他包来使用其他 API。

### <a name="versioning"></a>版本管理

规范并不是单一的，而是一组版本不断线性递增的 API。 该标准的第一个版本建立了一组基准 API。 后续版本将添加 API，并继承以前的版本定义的 API。 在从标准中移除 API 方面，并没有成文的规定。

.NET Standard 并不特定于任何一种 .NET 实现，也不与其中任一运行时的版本控制方案匹配。

添加到任何实现（例如 .NET Framework、.NET Core 和 Mono）的 API 可被视为适合添加到规范中的候选项，尤其是本质上非常重要的 API。 [.NET Standard 的新版本](https://github.com/dotnet/standard/blob/master/docs/versions.md)根据 .NET 实现版本进行创建，以便可以定位 .NET Standard PCL 中的新 API。 [.NET Core 版本控制](../core/versions/index.md)中更详细介绍了版本控制机制。

.NET Standard 版本控制对于库的使用至关重要。 在 .NET Standard 版本既定的情况下，可以使用定位相同或更低版本的库。 下面的做法介绍了使用 .NET Standard PCL（专用于 .NET Standard 定位）的工作流。

- 选择要用于 PCL 的 .NET Standard 版本。
- 使用依赖相同或更低 .NET Standard 版本的库。
- 如果发现依赖更高 .NET Standard 版本的库，要么需要采用相同的版本，要么不要使用此库。

## <a name="target-net-standard"></a>定位 .NET Standard

可以结合使用 `netstandard` 框架和 NETStandard.Library 元包来[构建.NET Standard 库](../core/tutorials/libraries.md)。

## <a name="net-framework-compatibility-mode"></a>.NET Framework 兼容性模式

从 .NET Standard 2.0 开始，引入了 .NET Framework 兼容性模式。 此兼容性模式允许 .NET Standard 项目引用 .NET Framework 库，就像其针对 .NET Standard 编译一样。 引用 .NET Framework 库并不适用于所有项目，，例如使用 Windows Presentation Foundation (WPF) API 的库。

有关详细信息，请参阅 [.NET Framework兼容性模式](../core/porting/third-party-deps.md#net-framework-compatibility-mode)。

## <a name="net-standard-libraries-and-visual-studio"></a>.NET Standard 库和 Visual Studio

要在 Visual Studio 中生成 .NET Standard 库，请确保 Windows 上已安装 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或 Visual Studio 2017 版本 15.3 或更高版本，或 macOS 上已安装 [Visual Studio for Mac 版本 7.1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 或更高版本。

如果项目中只需使用 .NET Standard 2.0 库，也可在 Visual Studio 2015 中执行此操作。 但是需要安装 NuGet client 3.6 或更高版本。 可从 [NuGet 下载](https://www.nuget.org/downloads)页面下载适用于 Visual Studio 2015 的 NuGet 客户端。

## <a name="comparison-to-portable-class-libraries"></a>与可移植类库的比较

.NET Standard 将取代[可移植类库 (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md)。 .NET Standard 可对标准 BCL 进行组织，从而提高跨 .NET 实现的一致性，改善创建可移植库的体验。 定位 .NET Standard 的库是 PCL 或“基于 .NET Standard 的 PCL”。 现有 PCL 是“基于配置文件的 PCL”。

虽然 .NET Standard 和 PCL 配置文件的创建目的类似，但在一些重要方面也存在差异。

类似之处：

- 定义可用于二进制代码共享的 API。

差异：

- .NET Standard 是一套组织有序的 API，而 PCL 配置文件是由现有平台的交集定义。
- .NET Standard 的版本线性递增，而 PCL 配置文件则不是这样。
- PCL 配置文件代表 Microsoft 平台，而 .NET Standard 与平台无关。

### <a name="pcl-compatibility"></a>PCL 兼容性

.NET Standard 与一部分 PCL 配置文件兼容。 .NET Standard 1.0、1.1 和 1.2 分别与一组 PCL 配置文件重叠。 这种重叠是由以下两个原因产生的：

- 使基于 .NET Standard 的 PCL 能够引用基于配置文件的 PCL。
- 使基于配置文件的 PCL 能够打包为基于 .NET Standard 的 PCL。

基于配置文件的 PCL 兼容性由 [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet 包提供。 引用包含基于配置文件的 PCL 的 NuGet 包时，需要这种依赖性。

与以常规方式打包的基于配置文件的 PCL 相比，打包为 `netstandard` 的基于配置文件的 PCL 更易于使用。 `netstandard` 打包符合现有用户的需要。

下面列出了与 .NET Standard 兼容的 PCL 配置文件集：

| PCL 配置文件 | .NET Standard | PCL 平台
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4.5、Windows 8
| Profile31   | 1.0           | Windows 8.1、Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1、Windows Phone 8.1
| Profile44   | 1.2           | .NET Framework 4.5.1、Windows 8.1
| Profile49   | 1.0           | .NET Framework 4.5、Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET Framework 4.5、Windows 8、Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1、Windows Phone Silverlight 8.1
| Profile111  | 1.1           | .NET Framework 4.5、Windows 8、Windows Phone 8.1
| Profile151  | 1.2           | .NET Framework 4.5.1、Windows 8.1、Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1、Windows Phone 8.1、Windows Phone Silverlight 8.1
| Profile259  | 1.0           | .NET Framework 4.5、Windows 8, Windows Phone 8.1、Windows Phone Silverlight 8

## <a name="see-also"></a>请参阅

- [.NET Standard 版本](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [生成 .NET Standard 库](../core/tutorials/library-with-visual-studio.md)
- [跨平台定位](./library-guidance/cross-platform-targeting.md)
