---
title: 将 Windows 窗体应用移植到 .NET Core
description: 了解如何将 .NET Framework Windows 窗体应用程序移植到 .NET Core for Windows。
author: Thraka
ms.author: adegeo
ms.date: 01/24/2020
ms.openlocfilehash: efa73428c816eddc00c62c2275d3457c92284388
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206137"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>如何将 Windows 窗体桌面应用程序移植到 .NET Core

本文介绍如何将基于 Windows 窗体的桌面应用从 .NET Framework 移植到 .NET Core 3.0 或更高版本。 .NET Core 3.0 SDK 支持 Windows 窗体应用程序。 Windows 窗体仍是仅适用于 Windows 的框架，并且只能在 Windows 上运行。 示例使用 .NET Core SDK CLI 创建和管理项目。

本文中的各种名称用于标识迁移所用的文件类型。 迁移项目时，你的文件将以不同的名称命名，因此，请自行在心里将它们与下面列出的文件进行匹配：

| 文件 | 描述 |
| ---- | ----------- |
| **MyApps.sln** | 解决方案文件的名称。 |
| **MyForms.csproj** | 要移植的 .NET Framework Windows 窗体项目的名称。 |
| **MyFormsCore.csproj** | 创建的新 .NET Core 项目的名称。 |
| **MyAppCore.exe** | .NET Core Windows 窗体应用程序的可执行文件。 |

## <a name="prerequisites"></a>先决条件

- 适用于要执行的任何设计器工作的 [Visual Studio 2019 16.5 预览版 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) 或更高版本。 建议更新到最新的 [Visual Studio 预览版](https://visualstudio.microsoft.com/vs/preview/)。

  安装以下 Visual Studio 工作负载：
  
  - .NET 桌面开发
  - .NET Core 跨平台开发

- 在解决方案中顺利生成和运行的有效 Windows 窗体项目。
- 用 C# 编码的项目。

> [!NOTE]
> 仅在 Visual Studio 2019 或更高版本中支持 .NET Core 3.0 项目。 从 Visual Studio 2019 版本 16.5 预览版 1 开始，还支持 .NET Core Windows 窗体设计器。
>
> 若要启用该设计器，请转到“工具” > “选项” > “环境” > “预览功能”，然后选择“将预览版 Windows 窗体设计器用于 .NET Core 应用”选项。

### <a name="consider"></a>考虑

移植 .NET Framework Windows 窗体应用程序时，必须考虑以下几个事项。

01. 检查应用程序是否适合迁移。

    使用 [.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)确定项目将会迁移到 .NET Core 3.0。 如果项目存在 .NET Core 3.0 相关问题，分析器可帮助你识别这些问题。

01. 使用的是不同版本的 Windows 窗体。

    发布 .NET Core 3.0 预览版 1 时，Windows 窗体在 GitHub 上公布了开放源代码。 .NET Core Windows 窗体的代码是 .NET Framework Windows 窗体基本代码的一个分支。 可能存在一些差异导致应用程序无法移植。

01. 使用 [Windows 兼容包][compat-pack]可有助于进行迁移。

    某些 API 可在 .NET Framework 中使用，但不可用于 .NET Core 3.0。 [Windows 兼容包][compat-pack]增加了很多这些 API，有助于使 Windows 窗体应用与 .NET Core 兼容。

01. 更新项目使用的 NuGet 包。

    在执行任何迁移之前使用最新版 NuGet 包始终是一个不错的做法。 如果应用程序引用任何 NuGet 包，请将它们更新到最新版本。 确保成功生成应用程序。 升级后，如果存在任何包错误，请将包降级到不会破坏代码的最新版本。

## <a name="create-a-new-sdk-project"></a>创建新的 SDK 项目

创建的新 .NET Core 3.0 项目必须位于不同于 .NET Framework 项目的目录中。 如果它们位于同一目录中，可能会与 obj 目录中生成的文件发生冲突。 本例中，我们将在 SolutionFolder 目录中创建一个名为 MyFormsAppCore 的目录 ：

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

接下来，需要在 MyFormsAppCore 目录中创建 MyFormsCore.csproj 项目 。 可以使用所选的文本编辑器手动创建此文件。 粘贴以下 XML：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

如果不想手动创建项目文件，可以使用 Visual Studio 或 .NET Core SDK 生成项目。 但是，必须删除项目模板生成的所有其他文件（项目文件除外）。 若要使用 SDK，请从 SolutionFolder 目录运行以下命令：

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

创建 MyFormsCore.csproj 后，目录结构应如下所示：

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

使用 Visual Studio 或 SolutionFolder 目录中的 .NET Core CLI 将 MyFormsCore.csproj 项目添加到 MyApps.sln  ：

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>修复程序集信息生成

使用 .NET Framework 创建的 Windows 窗体项目包含一个 `AssemblyInfo.cs` 文件，该文件包含诸如要生成的程序集的版本等程序集特性。 SDK 样式的项目会根据 SDK 项目文件自动生成此信息。 同时具有两种类型的“程序集信息”时，会产生冲突。 通过禁用自动生成可以解决此问题，这会强制项目使用现有的 `AssemblyInfo.cs` 文件。

若要添加到主 `<PropertyGroup>` 节点，有三个设置项。

- **GenerateAssemblyInfo**\
将此属性设置为 `false` 时，它不会生成程序集特性。 这可以避免与 .NET Framework 项目中的现有 `AssemblyInfo.cs` 文件冲突。

- **AssemblyName**\
此属性的值是编译时创建的输出二进制。 该名称不需要添加扩展名。 例如，使用 `MyCoreApp` 生成 `MyCoreApp.exe`。

- **RootNamespace**\
项目使用的默认命名空间。 它应该与 .NET Framework 项目的默认命名空间匹配。

将这三个元素添加到 `MyFormsCore.csproj` 文件中的 `<PropertyGroup>` 节点：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>添加源代码

现在，MyFormsCore.csproj 项目不编译任何代码。 默认情况下，.NET Core 项目会自动包含当前目录和所有子目录中的所有源代码。 必须使用相对路径配置项目以包含 .NET Framework 项目中的代码。 如果 .NET Framework 项目使用了 .resx 文件作为窗体的图标和资源，则还需要包含这些文件。

将以下 `<ItemGroup>` 节点添加到项目中。 每个语句都包含一个文件 glob 模式，其中包含子目录。

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

或者，可以为 .NET Framework 项目中的每个文件创建一个 `<Compile>` 或 `<EmbeddedResource>` 条目。

## <a name="add-nuget-packages"></a>添加 NuGet 包

将 .NET Framework 项目引用的每个 NuGet 包添加到 .NET Core 项目。

很可能你的 .NET Framework Windows 窗体应用程序有一个 packages.config 文件，其中包含项目引用的所有 NuGet 包的列表。 可以查看此列表以确定要添加到 .NET Core 项目的 NuGet 包。 例如，如果 .NET Framework 项目引用了 `MetroFramework`、`MetroFramework.Design` 和 `MetroFramework.Fonts` NuGet 包，则使用 Visual Studio 或 SolutionFolder 目录中的 .NET Core CLI 将每个包添加到项目中：

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

之前的命令会将以下 NuGet 引用添加到 MyFormsCore.csproj 项目：

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>移植控件库

如果要移植 Windows 窗体控件库项目，操作说明与移植 .NET Framework Windows 窗体应用程序项目相同，只不过在一些设置上存在差异。 并且此操作中不编译到可执行文件，而是编译到库。 除了包含源代码的文件 glob 的路径之外，可执行项目和库项目之间的区别也很小。

借助上一步的示例，详细介绍正在处理的项目和文件。

| 文件 | 描述 |
| ---- | ----------- |
| **MyApps.sln** | 解决方案文件的名称。 |
| **MyControls.csproj** | 要移植的 .NET Framework Windows 窗体控件项目的名称。 |
| **MyControlsCore.csproj** | 创建的新 .NET Core 库项目的名称。 |
| **MyCoreControls.dll** | .NET Core Windows 窗体控件库。 |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

请考虑 `MyControlsCore.csproj` 项目与先前创建的 `MyFormsCore.csproj` 项目之间的差异。

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

以下是 .NET Core Windows 窗体控件库项目文件的示例：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>

    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>

</Project>
```

如你所见，`<OutputType>` 节点已被删除，默认使编译器生成库而不是可执行文件。 `<AssemblyName>` 和 `<RootNamespace>` 已更改。 具体来说，`<RootNamespace>` 应匹配正在移植的 Windows 窗体控件库的命名空间。 最后，`<Compile>` 和 `<EmbeddedResource>` 节点已调整为指向要移植的 Windows 窗体控件库的文件夹。

接下来，在主要的 .NET Core MyFormsCore.csproj 项目中，添加对新 .NET Core Windows 窗体控件库的引用。 使用 Visual Studio 或 .NET Core CLI 从 SolutionFolder 目录添加引用：

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

上一个命令将以下内容添加到 MyFormsCore.csproj 项目中：

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a>编译问题

如果在编译项目时遇到问题，可能是由于正在使用的一些仅适用于 Windows 的 API 在 .NET Framework 中可用，但在 .NET Core 中不可用。 可以尝试将 [Windows 兼容包][compat-pack] NuGet 包添加到项目中。 此包仅在 Windows 上运行，为 .NET Core 和 .NET Standard 项目添加了大约 20,000 个 Windows API。

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

上一个命令将以下内容添加到 MyFormsCore.csproj 项目中：

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Windows Forms Designer — Windows 窗体设计器

如本文所述，Visual Studio 2019 仅支持 .NET Framework 项目中的窗体设计器。 通过创建并行 .NET Core 项目，可以在使用 .NET Framework 项目设计窗体时通过 .NET Core 测试项目。 解决方案文件包括 .NET Framework 和 .NET Core 项目。 在 .NET Framework 项目中添加和设计窗体和控件，并且根据添加到 .NET Core 项目的文件 glob 模式，任何新的或更改的文件将自动包含在 .NET Core 项目中。

一旦 Visual Studio 2019 支持 Windows 窗体设计器，就可以将 .NET Core 项目文件的内容复制/粘贴到 .NET Framework 项目文件中。 然后删除使用 `<Source>` 和 `<EmbeddedResource>` 项添加的文件 glob 模式。 修复由应用程序使用的任何项目引用的路径。 这可以有效地将 .NET Framework 项目升级到 .NET Core 项目。

## <a name="next-steps"></a>后续步骤

- 了解[从 .NET Framework 到 .NET Core 的中断性变更](../compatibility/fx-core.md)。
- 详细了解 [Windows 兼容包][compat-pack]。
- 观看将 .NET Framework Windows 窗体项目移植到 .NET Core 的[视频](https://www.youtube.com/watch?v=upVQEUc_KwU)。

[compat-pack]: windows-compat-pack.md
