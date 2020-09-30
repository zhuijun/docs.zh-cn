---
title: 使用插件创建 .NET Core 应用程序
description: 了解如何创建支持插件的 .NET Core 应用程序。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: ce7ac826feaf4542307abefde6d40a319d78e423
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247587"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="dea3a-103">使用插件创建 .NET Core 应用程序</span><span class="sxs-lookup"><span data-stu-id="dea3a-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="dea3a-104">本教程展示了如何创建自定义的 <xref:System.Runtime.Loader.AssemblyLoadContext> 来加载插件。</span><span class="sxs-lookup"><span data-stu-id="dea3a-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="dea3a-105"><xref:System.Runtime.Loader.AssemblyDependencyResolver> 用于解析插件的依赖项。</span><span class="sxs-lookup"><span data-stu-id="dea3a-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="dea3a-106">该教程正确地将插件依赖项与主机应用程序隔离开来。</span><span class="sxs-lookup"><span data-stu-id="dea3a-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="dea3a-107">将了解如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="dea3a-107">You'll learn how to:</span></span>

- <span data-ttu-id="dea3a-108">构建支持插件的项目。</span><span class="sxs-lookup"><span data-stu-id="dea3a-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="dea3a-109">创建自定义 <xref:System.Runtime.Loader.AssemblyLoadContext> 加载每个插件。</span><span class="sxs-lookup"><span data-stu-id="dea3a-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="dea3a-110">使用 <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> 类型允许插件具有依赖项。</span><span class="sxs-lookup"><span data-stu-id="dea3a-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="dea3a-111">只需复制生成项目就可以轻松部署的作者插件。</span><span class="sxs-lookup"><span data-stu-id="dea3a-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dea3a-112">系统必备</span><span class="sxs-lookup"><span data-stu-id="dea3a-112">Prerequisites</span></span>

- <span data-ttu-id="dea3a-113">安装 [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="dea3a-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="dea3a-114">创建应用程序</span><span class="sxs-lookup"><span data-stu-id="dea3a-114">Create the application</span></span>

<span data-ttu-id="dea3a-115">第一步是创建应用程序：</span><span class="sxs-lookup"><span data-stu-id="dea3a-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="dea3a-116">创建新文件夹，并在该文件夹中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="dea3a-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="dea3a-117">为了更容易生成项目，请在同一文件夹中创建一个 Visual Studio 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="dea3a-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="dea3a-118">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="dea3a-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="dea3a-119">运行以下命令，向解决方案添加应用项目：</span><span class="sxs-lookup"><span data-stu-id="dea3a-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="dea3a-120">现在，我们可以填写应用程序的主干。</span><span class="sxs-lookup"><span data-stu-id="dea3a-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="dea3a-121">使用下面的代码替换 AppWithPlugin/Program.cs 文件中的代码： </span><span class="sxs-lookup"><span data-stu-id="dea3a-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="dea3a-122">创建插件接口</span><span class="sxs-lookup"><span data-stu-id="dea3a-122">Create the plugin interfaces</span></span>

<span data-ttu-id="dea3a-123">使用插件生成应用的下一步是定义插件需要实现的接口。</span><span class="sxs-lookup"><span data-stu-id="dea3a-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="dea3a-124">我们建议创建类库，其中包含计划用于在应用和插件之间通信的任何类型。</span><span class="sxs-lookup"><span data-stu-id="dea3a-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="dea3a-125">此部分允许将插件接口作为包发布，而无需发布完整的应用程序。</span><span class="sxs-lookup"><span data-stu-id="dea3a-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="dea3a-126">在项目的根文件夹中，运行 `dotnet new classlib -o PluginBase`。</span><span class="sxs-lookup"><span data-stu-id="dea3a-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="dea3a-127">并运行 `dotnet sln add PluginBase/PluginBase.csproj` 向解决方案文件添加项目。</span><span class="sxs-lookup"><span data-stu-id="dea3a-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="dea3a-128">删除 `PluginBase/Class1.cs` 文件，并使用以下接口定义在名为 `ICommand.cs` 的 `PluginBase` 文件夹中创建新的文件：</span><span class="sxs-lookup"><span data-stu-id="dea3a-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

<span data-ttu-id="dea3a-129">此 `ICommand` 接口是所有插件将实现的接口。</span><span class="sxs-lookup"><span data-stu-id="dea3a-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="dea3a-130">由于已定义 `ICommand` 接口，所以应用程序项目可以填写更多内容。</span><span class="sxs-lookup"><span data-stu-id="dea3a-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="dea3a-131">使用根文件夹中的 `dotnet add AppWithPlugin/AppWithPlugin.csproj reference PluginBase/PluginBase.csproj` 命令将引用从 `AppWithPlugin` 项目添加到 `PluginBase` 项目。</span><span class="sxs-lookup"><span data-stu-id="dea3a-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin/AppWithPlugin.csproj reference PluginBase/PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="dea3a-132">使用以下代码片段替换 `// Load commands from plugins` 注释，使其能够从给定文件路径加载插件：</span><span class="sxs-lookup"><span data-stu-id="dea3a-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

<span data-ttu-id="dea3a-133">然后用以下代码片段替换 `// Output the loaded commands` 注释：</span><span class="sxs-lookup"><span data-stu-id="dea3a-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="dea3a-134">使用以下代码片段替换 `// Execute the command with the name passed as an argument` 注释：</span><span class="sxs-lookup"><span data-stu-id="dea3a-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="dea3a-135">最后，将静态方法添加到名为 `LoadPlugin` 和 `CreateCommands` 的 `Program` 类，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dea3a-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a><span data-ttu-id="dea3a-136">加载插件</span><span class="sxs-lookup"><span data-stu-id="dea3a-136">Load plugins</span></span>

<span data-ttu-id="dea3a-137">现在，应用程序可以正确加载和实例化来自已加载的插件程序集的命令，但仍然无法加载插件程序集。</span><span class="sxs-lookup"><span data-stu-id="dea3a-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="dea3a-138">使用以下内容在 AppWithPlugin 文件夹中创建名为 PluginLoadContext.cs 的文件：  </span><span class="sxs-lookup"><span data-stu-id="dea3a-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="dea3a-139">`PluginLoadContext` 类型派生自 <xref:System.Runtime.Loader.AssemblyLoadContext>。</span><span class="sxs-lookup"><span data-stu-id="dea3a-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="dea3a-140">`AssemblyLoadContext` 类型是运行时中的特殊类型，该类型允许开发人员将已加载的程序集隔离到不同的组中，以确保程序集版本不冲突。</span><span class="sxs-lookup"><span data-stu-id="dea3a-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="dea3a-141">此外，自定义 `AssemblyLoadContext` 可以选择不同路径来加载程序集格式并重写默认行为。</span><span class="sxs-lookup"><span data-stu-id="dea3a-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="dea3a-142">`PluginLoadContext` 使用 .NET Core 3.0 中引入的 `AssemblyDependencyResolver` 类型的实例将程序集名称解析为路径。</span><span class="sxs-lookup"><span data-stu-id="dea3a-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="dea3a-143">`AssemblyDependencyResolver` 对象是使用 .NET 类库的路径构造的。</span><span class="sxs-lookup"><span data-stu-id="dea3a-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="dea3a-144">它根据类库的 .deps.json 文件（其路径传递给 `AssemblyDependencyResolver` 构造函数）将程序集和本机库解析为它们的相对路径。</span><span class="sxs-lookup"><span data-stu-id="dea3a-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="dea3a-145">自定义 `AssemblyLoadContext` 使插件能够拥有自己的依赖项，`AssemblyDependencyResolver` 使正确加载依赖项变得容易。</span><span class="sxs-lookup"><span data-stu-id="dea3a-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="dea3a-146">由于 `AppWithPlugin` 项目具有 `PluginLoadContext` 类型，所以请使用以下正文更新 `Program.LoadPlugin` 方法：</span><span class="sxs-lookup"><span data-stu-id="dea3a-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

<span data-ttu-id="dea3a-147">通过为每个插件使用不同的 `PluginLoadContext` 实例，插件可以具有不同的甚至冲突的依赖项，而不会出现问题。</span><span class="sxs-lookup"><span data-stu-id="dea3a-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="dea3a-148">不具有依赖项的简单插件</span><span class="sxs-lookup"><span data-stu-id="dea3a-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="dea3a-149">返回到根文件夹，执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="dea3a-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="dea3a-150">运行以下命令，新建一个名为 `HelloPlugin` 的类库项目：</span><span class="sxs-lookup"><span data-stu-id="dea3a-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="dea3a-151">运行以下命令，将项目添加到 `AppWithPlugin` 解决方案中：</span><span class="sxs-lookup"><span data-stu-id="dea3a-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="dea3a-152">使用以下内容将 HelloPlugin/Class1.cs 文件替换为名为 HelloCommand.cs 的文件：  </span><span class="sxs-lookup"><span data-stu-id="dea3a-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="dea3a-153">现在，打开 HelloPlugin.csproj 文件  。</span><span class="sxs-lookup"><span data-stu-id="dea3a-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="dea3a-154">它应类似于以下内容：</span><span class="sxs-lookup"><span data-stu-id="dea3a-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="dea3a-155">在 `<Project>` 标记之间添加以下元素：</span><span class="sxs-lookup"><span data-stu-id="dea3a-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

<span data-ttu-id="dea3a-156">`<Private>false</Private>` 元素很重要。</span><span class="sxs-lookup"><span data-stu-id="dea3a-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="dea3a-157">它告知 MSBuild 不要将 PluginBase.dll 复制到 HelloPlugin 的输出目录  。</span><span class="sxs-lookup"><span data-stu-id="dea3a-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="dea3a-158">如果 PluginBase.dll 程序集出现在输出目录中，`PluginLoadContext` 将在那里查找到该程序集并在加载 HelloPlugin.dll 程序集时加载它。</span><span class="sxs-lookup"><span data-stu-id="dea3a-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="dea3a-159">此时，`HelloPlugin.HelloCommand` 类型将从 `HelloPlugin` 项目的输出目录中的 PluginBase.dll 实现 `ICommand` 接口，而不是加载到默认加载上下文中的 `ICommand` 接口。</span><span class="sxs-lookup"><span data-stu-id="dea3a-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="dea3a-160">因为运行时将这两种类型视为不同程序集的不同类型，所以 `AppWithPlugin.Program.CreateCommands` 方法找不到命令。</span><span class="sxs-lookup"><span data-stu-id="dea3a-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="dea3a-161">因此，对包含插件接口的程序集的引用需要 `<Private>false</Private>` 元数据。</span><span class="sxs-lookup"><span data-stu-id="dea3a-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="dea3a-162">同样，如果 `PluginBase` 引用其他包，则 `<ExcludeAssets>runtime</ExcludeAssets>` 元素也很重要。</span><span class="sxs-lookup"><span data-stu-id="dea3a-162">Similarly, the `<ExcludeAssets>runtime</ExcludeAssets>` element is also important if the `PluginBase` references other packages.</span></span> <span data-ttu-id="dea3a-163">此设置与 `<Private>false</Private>` 的效果相同，但适用于 `PluginBase` 项目或它的某个依赖项可能包括的包引用。</span><span class="sxs-lookup"><span data-stu-id="dea3a-163">This setting has the same effect as `<Private>false</Private>` but works on package references that the `PluginBase` project or one of its dependencies may include.</span></span>

<span data-ttu-id="dea3a-164">因为 `HelloPlugin` 项目已完成，所以应该更新 `AppWithPlugin` 项目，以确认可以找到 `HelloPlugin` 插件的位置。</span><span class="sxs-lookup"><span data-stu-id="dea3a-164">Now that the `HelloPlugin` project is complete, you should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="dea3a-165">在 `// Paths to plugins to load` 注释后，添加 `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"`（根据所使用的 .NET Core 版本，此路径可能有所不同）作为 `pluginPaths` 数组的元素。</span><span class="sxs-lookup"><span data-stu-id="dea3a-165">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` (this path could be different based on the .NET Core version you use) as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="dea3a-166">具有库依赖项的插件</span><span class="sxs-lookup"><span data-stu-id="dea3a-166">Plugin with library dependencies</span></span>

<span data-ttu-id="dea3a-167">几乎所有插件都比简单的“Hello World”更复杂，而且许多插件都具有其他库上的依赖项。</span><span class="sxs-lookup"><span data-stu-id="dea3a-167">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="dea3a-168">示例中的 `JsonPlugin` 和 `OldJson` 插件项目显示了具有 `Newtonsoft.Json` 上的 NuGet 包依赖项的两个插件示例。</span><span class="sxs-lookup"><span data-stu-id="dea3a-168">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="dea3a-169">项目文件本身没有关于项目引用的任何特殊信息，并且（在将插件路径添加到 `pluginPaths` 数组之后）即使是在 AppWithPlugin 应用的同一执行中运行，插件也能完美运行。</span><span class="sxs-lookup"><span data-stu-id="dea3a-169">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="dea3a-170">但是，这些项目不会将引用的程序集复制到它们的输出目录中，因此需要将这些程序集显示在用户的计算机上，以便插件能够正常工作。</span><span class="sxs-lookup"><span data-stu-id="dea3a-170">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="dea3a-171">解决此问题有两种方法。</span><span class="sxs-lookup"><span data-stu-id="dea3a-171">There are two ways to work around this problem.</span></span> <span data-ttu-id="dea3a-172">第一种是使用 `dotnet publish` 命令发布类库。</span><span class="sxs-lookup"><span data-stu-id="dea3a-172">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="dea3a-173">或者，如果希望能够将 `dotnet build` 的输出用于插件，可以在插件的项目文件中的 `<PropertyGroup>` 标记之间添加 `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` 属性。</span><span class="sxs-lookup"><span data-stu-id="dea3a-173">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="dea3a-174">有关示例，请参阅 `XcopyablePlugin` 插件项目。</span><span class="sxs-lookup"><span data-stu-id="dea3a-174">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="dea3a-175">示例中的其他示例</span><span class="sxs-lookup"><span data-stu-id="dea3a-175">Other examples in the sample</span></span>

<span data-ttu-id="dea3a-176">可以在 [dotnet/samples 存储库](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin)中找到本教程的完整源代码。</span><span class="sxs-lookup"><span data-stu-id="dea3a-176">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="dea3a-177">完成的示例包括 `AssemblyDependencyResolver` 行为的一些其他示例。</span><span class="sxs-lookup"><span data-stu-id="dea3a-177">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="dea3a-178">例如，`AssemblyDependencyResolver` 对象还可以解析本机库和 NuGet 包中所包含的已本地化的附属程序集。</span><span class="sxs-lookup"><span data-stu-id="dea3a-178">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="dea3a-179">示例存储库中的 `UVPlugin` 和 `FrenchPlugin` 演示了这些方案。</span><span class="sxs-lookup"><span data-stu-id="dea3a-179">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a><span data-ttu-id="dea3a-180">从 NuGet 包引用插件接口</span><span class="sxs-lookup"><span data-stu-id="dea3a-180">Reference a plugin interface from a NuGet package</span></span>

<span data-ttu-id="dea3a-181">假设存在应用 A，它具有 NuGet 包（名为 `A.PluginBase`）中定义的插件接口。</span><span class="sxs-lookup"><span data-stu-id="dea3a-181">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="dea3a-182">如何在插件项目中正确引用包？</span><span class="sxs-lookup"><span data-stu-id="dea3a-182">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="dea3a-183">对于项目引用，使用项目文件的 `ProjectReference` 元素上的 `<Private>false</Private>` 元数据会阻止将 dll 复制到输出。</span><span class="sxs-lookup"><span data-stu-id="dea3a-183">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="dea3a-184">若要正确引用 `A.PluginBase` 包，应将项目文件中的 `<PackageReference>` 元素更改为以下内容：</span><span class="sxs-lookup"><span data-stu-id="dea3a-184">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="dea3a-185">此操作会阻止将 `A.PluginBase` 程序集复制到插件的输出目录，并确保插件将使用 A 版本的 `A.PluginBase`。</span><span class="sxs-lookup"><span data-stu-id="dea3a-185">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="dea3a-186">插件目标框架建议</span><span class="sxs-lookup"><span data-stu-id="dea3a-186">Plugin target framework recommendations</span></span>

<span data-ttu-id="dea3a-187">因为插件依赖项加载使用 .deps.json 文件，所以存在一个与插件的目标框架相关的问题  。</span><span class="sxs-lookup"><span data-stu-id="dea3a-187">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="dea3a-188">具体来说，插件应该以运行时为目标，比如 .NET Core 3.0，而不是某一版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="dea3a-188">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="dea3a-189">.deps.json  文件基于项目所针对的框架生成，而且由于许多与 .NET Standard 兼容的包提供了用于针对 .NET Standard 进行生成的引用程序集和用于特定运行时的实现程序集，因此 .deps.json  可能无法正确查看实现程序集，或者它可能会获取 .NET Standard 版本的程序集，而不是期望的 .NET Core 版本的程序集。</span><span class="sxs-lookup"><span data-stu-id="dea3a-189">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

## <a name="plugin-framework-references"></a><span data-ttu-id="dea3a-190">插件框架引用</span><span class="sxs-lookup"><span data-stu-id="dea3a-190">Plugin framework references</span></span>

<span data-ttu-id="dea3a-191">插件当前无法向该过程引入新的框架。</span><span class="sxs-lookup"><span data-stu-id="dea3a-191">Currently, plugins can't introduce new frameworks into the process.</span></span> <span data-ttu-id="dea3a-192">例如，无法将使用 `Microsoft.AspNetCore.App` 框架的插件加载到只使用根 `Microsoft.NETCore.App` 框架的应用程序中。</span><span class="sxs-lookup"><span data-stu-id="dea3a-192">For example, you can't load a plugin that uses the `Microsoft.AspNetCore.App` framework into an application that only uses the root `Microsoft.NETCore.App` framework.</span></span> <span data-ttu-id="dea3a-193">主机应用程序必须声明对插件所需的全部框架的引用。</span><span class="sxs-lookup"><span data-stu-id="dea3a-193">The host application must declare references to all frameworks needed by plugins.</span></span>
