---
title: 在 Visual Studio 中创建 .NET Standard 类库
description: 了解如何使用 Visual Studio 创建 .NET Standard 类库。
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005220"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a>教程：在 Visual Studio 中创建 .NET Standard 库

类库定义的是可以由应用程序调用的类型和方法。 借助面向 .NET Standard 2.0 的类库，任何支持相应 .NET Standard 版本的 .NET 实现都可以调用库。 完成类库时，可以决定是要将其作为第三方组件进行分布，还是要将其作为与一个或多个应用程序捆绑在一起的组件进行添加。

> [!NOTE]
> 有关 .NET Standard 版本及其支持的平台列表，请参阅 [.NET Standard](../../standard/net-standard.md)。

在本教程中，将创建包含一个字符串处理方法的简单实用工具库。 我们把它作为[扩展方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)进行实现，这样就可以把它作为 <xref:System.String> 类成员进行调用。

## <a name="prerequisites"></a>先决条件

- 安装了具有“.NET Core 跨平台开发”工作负载的 [Visual Studio 2019 版本 16.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 选择此工作负载时，将自动安装 .NET Core 3.1 SDK。

  有关详细信息，请参阅[安装 .NET Core SDK](../install/sdk.md?pivots=os-windows) 一文中的[在 Visual Studio 中安装](../install/sdk.md?pivots=os-windows#install-with-visual-studio)部分。

## <a name="create-a-visual-studio-solution"></a>创建 Visual Studio 解决方案

首先，创建一个空白解决方案来放置类库项目。 Visual Studio 解决方案用作一个或多个项目的容器。 将其他相关项目添加到同一个解决方案中。

创建空白解决方案：

1. 打开 Visual Studio。

2. 在“开始”窗口上，选择“创建新项目”。

3. 在“创建新项目”页面上，在搜索框中输入“解决方案”。 选择“空白解决方案”模板，然后选择“下一步”。

   ![Visual Studio 中的空白解决方案模板](media/library-with-visual-studio/blank-solution.png)

4. 在“配置新项目”页面上，在“项目名称”框中输入“ClassLibraryProjects”。 然后选择“创建”。

## <a name="create-a-class-library-project"></a>创建类库项目

1. 将名为“StringLibrary”的新 .NET Standard 类库项目添加到解决方案。

   1. 在“解决方案资源管理器”中，右键单击解决方案并选择“添加” > “新建项目”  。

   1. 在“创建新项目”页面上，在搜索框中输入“库”。 从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”。 选择“类库 (.NET Standard)”模板，然后选择“下一步”。

   1. 在“配置新项目”页面，在“项目名称”框中输入“StringLibrary”。 然后，选择“创建”。

1. 请检查以确保库面向 .NET Standard 的正确版本。 右键单击“解决方案资源管理器”中的库项目，然后选择“属性”。 “目标框架”文本框显示项目面向 .NET Standard 2.0。

   ![类库的项目属性](./media/library-with-visual-studio/library-project-properties.png)

1. 如果使用 Visual Basic，请清除“根命名空间”文本框中的文本。

   ![类库的项目属性](./media/library-with-visual-studio/vb/library-project-properties.png)

   对于每个项目，Visual Basic 会自动创建一个与项目名称对应的命名空间。 在本教程中，通过使用代码文件中的 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 关键字定义顶级命名空间。

1. 将 Class1.cs 或 Class1.vb 代码窗口中的代码替换为以下代码，并保存文件 。 如果未显示想要使用的语言，请更改页面顶部的语言选择器。

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   类库 `UtilityLibraries.StringLibrary`包含一个名为 `StartsWithUpper` 的方法。 此方法会返回 <xref:System.Boolean> 值，以指明当前字符串实例是否以大写字符开头。 Unicode 标准会区分大小写字符。 如果为大写字符，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法返回 `true`。

1. 在菜单栏上，选择“生成” > “生成解决方案”以验证项目是否正确编译 。

## <a name="add-a-console-app-to-the-solution"></a>向解决方案添加控制台应用

使用控制台应用程序中的类库，此应用程序将提示用户输入字符串，并报告字符串第一个字符是否大写。

1. 将名为“ShowCase”的新 .NET Core 控制台应用程序添加到解决方案。

   1. 在“解决方案资源管理器”中右键单击解决方案并选择“添加” > “新建项目”。

   1. 在“创建新项目”页面，在搜索框中输入“控制台”。 从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”。

   1. 选择“控制台应用 (.NET Core)”模板，然后选择“下一步”。

   1. 在“配置新项目”页面，在“项目名称”框中输入“ShowCase”。 然后选择“创建”。

1. 在“**解决方案资源管理器**”中，右键单击“**ShowCase**”项目，在上下文菜单中选择“**设为启动项目**”。

   ![Visual Studio 中用于设置启动项目的项目上下文菜单](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. 最初，新的控制台应用项目无权访问类库。 若要允许该项目调用类库中的方法，可以创建对类库项目的项目引用。 在“解决方案资源管理器”中，右键单击 `ShowCase` 项目的“依赖项”节点，并选择“添加项目引用”  。

   ![在 Visual Studio 中添加引用上下文菜单](media/library-with-visual-studio/add-reference-context-menu.png)

1. 在“引用管理器”对话框中，选择“StringLibrary”项目，然后选择“确定”按钮  。

   ![选择了“StringLibrary”的“引用管理器”对话框](media/library-with-visual-studio/manage-project-references.png)

1. 在“Program.cs”或“Program.vb”文件的代码窗口中，将所有代码替换为以下代码 。

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   该代码使用 `row` 变量来维护写入到控制台窗口的数据行数计数。 如果大于或等于 25，该代码将清除控制台窗口，并向用户显示一条消息。

   该程序会提示用户输入字符串。 它会指明字符串是否以大写字符开头。 如果用户没有输入字符串就按 Enter 键，那么应用程序会终止，控制台窗口会关闭。

1. 必要时，将工具栏更改为编译 `ShowCase` 项目的“调试”版本。 选择“ShowCase”按钮上的绿色箭头，编译并运行程序。

   ![Visual Studio 中显示“调试”按钮的项目工具栏](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. 输入字符串并按 Enter 以试用程序，然后按 Enter 退出 。

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="运行展示的控制台窗口":::

## <a name="next-steps"></a>后续步骤

在本教程中，你创建了一个解决方案，添加了一个库项目，并添加了一个使用该库的控制台应用项目。 在下一教程中，将向解决方案中添加单元测试项目。

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用 .NET Core 测试 .NET Standard 库](testing-library-with-visual-studio.md)
