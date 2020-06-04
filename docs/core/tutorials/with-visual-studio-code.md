---
title: 使用 Visual Studio Code 通过 .NET Core 创建控制台应用程序
description: 了解如何使用 Visual Studio Code 和 .NET Core CLI 创建 .NET Core 控制台应用程序。
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201706"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a>教程：使用 Visual Studio Code 通过 .NET Core 创建控制台应用程序

本教程演示如何使用 Visual Studio Code 和 .NET Core CLI 创建并运行 .NET Core 控制台应用程序。 项目任务（如创建、编译和运行项目）是使用 CLI 完成的，因此，如果你愿意，可以使用其他代码编辑器来学习本教程并在终端中运行命令。

## <a name="prerequisites"></a>先决条件

1. 已安装 [C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) 的 [Visual Studio Code](https://code.visualstudio.com/)。 有关如何在 Visual Studio Code 上安装扩展的信息，请访问 [VS Code 扩展市场](https://code.visualstudio.com/docs/editor/extension-gallery)。
2. [.NET Core 3.1 SDK 或更高版本](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>创建应用

1. 打开 Visual Studio Code。

1. 创建项目。

   1. 在主菜单中选择“文件” > “打开文件夹”/“打开…”，创建“HelloWorld”文件夹，然后单击“选择文件夹”/“打开”   。

      默认情况下，文件夹名称将是项目名称和命名空间名称。 稍后将在本教程中添加代码，假定项目命名空间为 `HelloWorld`。

   1. 在主菜单中选择“视图” > “终端”，从 Visual Studio Code 中打开“终端”  。

      “终端”在“HelloWorld”文件夹中连同命令提示符一起打开。

   1. 在“终端”中输入以下命令：

      ```dotnetcli
      dotnet new console
      ```

.NET Core 控制台应用程序模板将定义类 `Program`，其中包含一个需要将 <xref:System.String> 数组用作参数的方法 `Main`。 Program.cs 文件具有以下代码：

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

`Main` 是应用程序入口点，同时也是在应用程序启动时由运行时自动调用的方法。 *args* 数组中包含在应用程序启动时提供的所有命令行自变量。

该模板创建一个简单的应用程序，以调用 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法来显示“Hello World!” 显示文本字符串“Hello World!”。

## <a name="run-the-app"></a>运行应用

在“终端”中运行以下命令：

```dotnetcli
dotnet run
```

程序显示“Hello World!” 然后结束。

![dotnet run 命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>增强应用

改进应用程序，使其提示用户输入名字，并将其与日期和时间一同显示。

1. 单击打开 *Program.cs*。

   在 Visual Studio Code 中首次打开 C# 文件时，会在编辑器中加载 [OmniSharp](https://www.omnisharp.net/)。

   ![打开 Program.cs 文件](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code 提示添加缺少的资产时选择“是”，以生成和调试应用。

   ![提示添加缺少的资产](media/with-visual-studio-code/missing-assets.png)

1. 将 Program.cs 中 `Main` 方法的内容（当前只是调用 `Console.WriteLine` 的行）替换为以下代码：

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   此代码在控制台中显示“What is your name?”， 然后等待用户输入字符串并按 Enter。 它会将此字符串存储到名为 `name` 的变量中。 它还会检索 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性的值（其中包含当前的本地时间），并将此值赋给 `date` 变量。 最后，它会在控制台窗口中显示这些值。

   `\n` 表示一个换行符。

   字符串前面的美元符号 (`$`) 使你可以将表达式（如变量名称）放入字符串中的大括号内。 表达式值将代替表达式插入到字符串中。 此语法称为[内插字符串](../../csharp/language-reference/tokens/interpolated.md)。

1. 保存更改。

   > [!IMPORTANT]
   > 在 Visual Studio Code 中，必须显式保存更改。 与 Visual Studio 不同，生成和运行应用时不会自动保存文件更改。

1. 再次运行程序：

   ```dotnetcli
   dotnet run
   ```

1. 出现提示时，输入名称并按 Enter 键。

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="包含经过修改的程序输出的“终端”窗口":::

1. 按任意键退出程序。

## <a name="additional-resources"></a>其他资源

- [设置 Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>后续步骤

在本教程中，你创建了一个 .NET Core 应用程序。 在下一教程中，你将调试该应用。

> [!div class="nextstepaction"]
> [使用 Visual Studio Code 调试 .NET Core 控制台应用程序](debugging-with-visual-studio-code.md)
