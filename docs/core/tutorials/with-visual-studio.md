---
title: 在 Visual Studio 中使用 .NET Core 创建控制台应用程序
description: 了解如何使用 Visual Studio 通过 C# 或 Visual Basic 创建 .NET Core 控制台应用程序。
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 9c3456cd8c940e53e8a70c1d3a7c3b09de77c21d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201587"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a>教程：在 Visual Studio 2019 中创建 .NET Core 控制台应用程序

本教程演示如何在 Visual Studio 2019 中创建和运行 .NET Core 控制台应用程序。

## <a name="prerequisites"></a>先决条件

- 安装了具有“.NET Core 跨平台开发”工作负载的 [Visual Studio 2019 版本 16.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。 选择此工作负载时，将自动安装 .NET Core 3.1 SDK。

  有关详细信息，请参阅[安装 .NET Core SDK](../install/sdk.md?pivots=os-windows) 一文中的[在 Visual Studio 中安装](../install/sdk.md?pivots=os-windows#install-with-visual-studio)部分。

## <a name="create-the-app"></a>创建应用

<!-- markdownlint-disable MD025 -->

1. 打开 Visual Studio 2019。

1. 创建一个名为“HelloWorld”的新 .NET Core 控制台应用项目。

   1. 在“开始”页上，选择“创建新项目”。

      ![在 Visual Studio“开始”页选择“创建新项目”按钮](./media/with-visual-studio/start-window.png)

   1. 在“创建新项目”页面，在搜索框中输入“控制台”。 接下来，从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”  。 选择“控制台应用 (.NET Core)”模板，然后选择“下一步”。

      ![使用所选筛选器创建新项目窗口](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > 如果看不到 .NET Core 模板，则可能缺少所需的工作负载。 在“找不到所需内容?”消息下，选择“安装更多工具和功能”链接。 Visual Studio 安装程序随即打开。 确保安装了“.NET Core 跨平台开发”工作负载。

   1. 在“配置新项目”页面，在“项目名称”框中输入“HelloWorld”。 然后选择“创建”。

      ![为新项目窗口配置“项目名称”、“位置”和“解决方案名称”字段](./media/with-visual-studio/configure-new-project.png)

   .NET Core 控制台应用程序模板将定义类 `Program`，其中包含一个需要将 <xref:System.String> 数组用作参数的方法 `Main`。 `Main` 是应用程序入口点，同时也是在应用程序启动时由运行时自动调用的方法。 *args* 数组中包含在应用程序启动时提供的所有命令行自变量。

   如果未显示想要使用的语言，请更改页面顶部的语言选择器。

   ```csharp
   using System;

   namespace HelloWorld
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   用于创建简单的“Hello World”应用程序的模板。 它会调用 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法来显示“Hello World!” 显示文本字符串“Hello World!”。

## <a name="run-the-app"></a>运行应用

1. 若要运行程序，请在工具栏上选择“HelloWorld”，或按 F5。

   ![已选择“HelloWorld 运行”按钮的 Visual Studio 工具栏](./media/with-visual-studio/run-program.png)

   此时将打开在屏幕上显示文本“Hello World!” 并附带一些 Visual Studio 调试信息的控制台窗口。

   ![控制台窗口，其中显示 Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. 按任意键关闭控制台窗口。

## <a name="enhance-the-app"></a>增强应用

改进应用程序，使其提示用户输入名字，并将其与日期和时间一同显示。 以下指令可修改应用并再次运行应用：

1. 将 `Main` 方法的内容（当前只是调用 `Console.WriteLine` 的行）替换为以下代码：

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="Snippet1":::

   此代码在控制台中显示“What is your name?”， 然后等待用户输入字符串并按 Enter 键。 它会将此字符串存储到名为 `name` 的变量中。 它还会检索 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性的值（其中包含当前的本地时间），并将此值赋给 `date` 变量（Visual Basic 中为 `currentDate`）。 最后，它会在控制台窗口中显示这些值。

   `\n`（Visual Basic 中为 `vbCrLf`）表示换行符。

   字符串前面的美元符号 (`$`) 使你可以将表达式（如变量名称）放入字符串中的大括号内。 表达式值将代替表达式插入到字符串中。 此语法称为[内插字符串](../../csharp/language-reference/tokens/interpolated.md)。

1. 若要运行程序，请在工具栏上选择“HelloWorld”，或按 F5。

1. 出现提示时，输入名称并按 Enter 键。

   ![控制台窗口，含已修改程序的输出](./media/with-visual-studio/hello-world-update.png)

1. 按任意键关闭控制台窗口。

## <a name="next-steps"></a>后续步骤

在本教程中，你创建了一个 .NET Core 应用程序。 在下一教程中，你将调试该应用。

> [!div class="nextstepaction"]
> [在 Visual Studio 中调试 .NET Core 控制台应用程序](debugging-with-visual-studio.md)
