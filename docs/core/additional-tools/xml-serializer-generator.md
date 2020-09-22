---
title: Microsoft XML 序列化程序生成器
description: Microsoft XML 序列化程序生成器概述。 使用 XML 序列化程序生成器为项目中包含的类型生成 XML 序列化程序集。
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 8005a8a3e5202b0255ec482dfb7e3c284bc2e19b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538899"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="d299f-104">在 .NET Core 上使用 Microsoft XML 序列化程序生成器</span><span class="sxs-lookup"><span data-stu-id="d299f-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="d299f-105">本教程介绍如何在 C# .NET Core 应用程序中使用 Microsoft XML 序列化程序生成器。</span><span class="sxs-lookup"><span data-stu-id="d299f-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="d299f-106">在本教程中可学习：</span><span class="sxs-lookup"><span data-stu-id="d299f-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d299f-107">如何创建 .NET Core 应用</span><span class="sxs-lookup"><span data-stu-id="d299f-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="d299f-108">如何向 Microsoft.XmlSerializer.Generator 包中添加引用</span><span class="sxs-lookup"><span data-stu-id="d299f-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="d299f-109">如何编辑 MyApp.csproj 以添加依赖项</span><span class="sxs-lookup"><span data-stu-id="d299f-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="d299f-110">如何添加类和 XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="d299f-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="d299f-111">如何生成并运行应用程序</span><span class="sxs-lookup"><span data-stu-id="d299f-111">How to build and run the application</span></span>

<span data-ttu-id="d299f-112">正如适用于 .NET Framework 的 [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md)，[Microsoft.XmlSerializer.Generator NuGet 包](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) 是适用于 .NET Core 和 .NET 标准项目的等效项。</span><span class="sxs-lookup"><span data-stu-id="d299f-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="d299f-113">它为程序集中包含的类型创建 XML 序列化程序集，从而提高使用 <xref:System.Xml.Serialization.XmlSerializer> 序列化或反序列化这些类型对象时，XML 序列化的启动性能。</span><span class="sxs-lookup"><span data-stu-id="d299f-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d299f-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="d299f-114">Prerequisites</span></span>

<span data-ttu-id="d299f-115">完成本教程：</span><span class="sxs-lookup"><span data-stu-id="d299f-115">To complete this tutorial:</span></span>

- <span data-ttu-id="d299f-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="d299f-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="d299f-117">最喜爱的代码编辑器。</span><span class="sxs-lookup"><span data-stu-id="d299f-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="d299f-118">需要安装代码编辑器？</span><span class="sxs-lookup"><span data-stu-id="d299f-118">Need to install a code editor?</span></span> <span data-ttu-id="d299f-119">试用 [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)！</span><span class="sxs-lookup"><span data-stu-id="d299f-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="d299f-120">在 .NET Core 控制台应用程序中使用 Microsoft XML 序列化程序生成器</span><span class="sxs-lookup"><span data-stu-id="d299f-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="d299f-121">以下说明将展示如何在 .NET Core 控制台应用程序中使用 XML 序列化程序生成器。</span><span class="sxs-lookup"><span data-stu-id="d299f-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="d299f-122">创建 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="d299f-122">Create a .NET Core console application</span></span>

<span data-ttu-id="d299f-123">打开命令提示符，创建一个名为“MyApp”的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d299f-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="d299f-124">导航到创建的文件夹，并键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="d299f-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="d299f-125">在 MyApp 项目中向 Microsoft.XmlSerializer.Generator 包添加引用</span><span class="sxs-lookup"><span data-stu-id="d299f-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="d299f-126">使用 [`dotnet add package`](../tools/dotnet-add-package.md) 命令在项目中添加引用。</span><span class="sxs-lookup"><span data-stu-id="d299f-126">Use the [`dotnet add package`](../tools/dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="d299f-127">类型：</span><span class="sxs-lookup"><span data-stu-id="d299f-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="d299f-128">添加包后，验证对 MyApp.csproj 的更改</span><span class="sxs-lookup"><span data-stu-id="d299f-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="d299f-129">打开代码编辑器并开始操作！</span><span class="sxs-lookup"><span data-stu-id="d299f-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="d299f-130">仍从生成了应用的 MyApp 目录中进行操作。</span><span class="sxs-lookup"><span data-stu-id="d299f-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="d299f-131">在文本编辑器中打开 MyApp.csproj。</span><span class="sxs-lookup"><span data-stu-id="d299f-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="d299f-132">运行 [`dotnet add package`](../tools/dotnet-add-package.md) 命令后，会将以下行添加到 MyApp.csproj 项目文件中：</span><span class="sxs-lookup"><span data-stu-id="d299f-132">After running the [`dotnet add package`](../tools/dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="d299f-133">为 .NET Core CLI 工具支持添加其他 ItemGroup 部分</span><span class="sxs-lookup"><span data-stu-id="d299f-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="d299f-134">在已检查的 `ItemGroup` 部分后添加以下行：</span><span class="sxs-lookup"><span data-stu-id="d299f-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="d299f-135">在应用程序中添加类</span><span class="sxs-lookup"><span data-stu-id="d299f-135">Add a class in the application</span></span>

<span data-ttu-id="d299f-136">在文本编辑器中打开 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="d299f-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="d299f-137">在 Program.cs 中添加名为“MyClass”的类 。</span><span class="sxs-lookup"><span data-stu-id="d299f-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="d299f-138">为 MyClass 创建 `XmlSerializer`</span><span class="sxs-lookup"><span data-stu-id="d299f-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="d299f-139">在 Main 中添加以下行，为 MyClass 创建 `XmlSerializer`：</span><span class="sxs-lookup"><span data-stu-id="d299f-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="d299f-140">编译和运行应用程序</span><span class="sxs-lookup"><span data-stu-id="d299f-140">Build and run the application</span></span>

<span data-ttu-id="d299f-141">还是在 MyApp 文件夹中，通过 [`dotnet run`](../tools/dotnet-run.md) 运行应用程序，它会在运行时自动加载和使用预生成的序列化程序。</span><span class="sxs-lookup"><span data-stu-id="d299f-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at run time.</span></span>

<span data-ttu-id="d299f-142">在控制台窗口中键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="d299f-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="d299f-143">[`dotnet run`](../tools/dotnet-run.md) 调用 [`dotnet build`](../tools/dotnet-build.md) 来确保已生成要生成的目标，然后调用 `dotnet <assembly.dll>` 运行目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="d299f-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d299f-144">本教程中用来运行应用程序的命令和步骤仅用于开发过程。</span><span class="sxs-lookup"><span data-stu-id="d299f-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="d299f-145">准备好部署应用后，查看适用于 .NET Core 应用的不同[部署策略](../deploying/index.md)和 [`dotnet publish`](../tools/dotnet-publish.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="d299f-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="d299f-146">如果一切顺利，则会在输出文件夹中生成名为“MyApp.XmlSerializers.dll”的程序集。</span><span class="sxs-lookup"><span data-stu-id="d299f-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="d299f-147">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="d299f-147">Congratulations!</span></span> <span data-ttu-id="d299f-148">你刚才已完成：</span><span class="sxs-lookup"><span data-stu-id="d299f-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d299f-149">创建 .NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="d299f-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="d299f-150">向 Microsoft.XmlSerializer.Generator 包中添加引用。</span><span class="sxs-lookup"><span data-stu-id="d299f-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="d299f-151">编辑 MyApp.csproj 以添加依赖项。</span><span class="sxs-lookup"><span data-stu-id="d299f-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="d299f-152">添加类和 XmlSerializer。</span><span class="sxs-lookup"><span data-stu-id="d299f-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="d299f-153">生成和运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="d299f-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="d299f-154">相关资源</span><span class="sxs-lookup"><span data-stu-id="d299f-154">Related resources</span></span>

- [<span data-ttu-id="d299f-155">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="d299f-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="d299f-156">如何使用 XmlSerializer 进行序列化 (C#)</span><span class="sxs-lookup"><span data-stu-id="d299f-156">How to serialize using XmlSerializer (C#)</span></span>](../../standard/linq/serialize-xmlserializer.md)
- [<span data-ttu-id="d299f-157">如何：使用 XmlSerializer (Visual Basic) 进行序列化</span><span class="sxs-lookup"><span data-stu-id="d299f-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../standard/linq/serialize-xmlserializer.md)
