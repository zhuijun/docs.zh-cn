---
title: 使用 dotnet-svcutil.xmlserializer
description: 了解如何使用 `dotnet-svcutil.xmlserializer` NuGet 包为 .NET Core 项目预生成序列化程序集。
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 14bb2e8a85ec35f08b0a83b9734a64d751074f1b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284320"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="b6f29-103">在 .NET Core 上使用 dotnet-svcutil.xmlserializer</span><span class="sxs-lookup"><span data-stu-id="b6f29-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="b6f29-104">`dotnet-svcutil.xmlserializer` NuGet 包可以为 .NET Core 项目预生成序列化程序集。</span><span class="sxs-lookup"><span data-stu-id="b6f29-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="b6f29-105">它为客户端应用程序中由 WCF 服务协定使用的且可由 XmlSerializer 序列化的类型预生成 C# 序列化代码。</span><span class="sxs-lookup"><span data-stu-id="b6f29-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="b6f29-106">当序列化或反序列化这些类型的对象时，这会提高 XML 序列化的启动性能。</span><span class="sxs-lookup"><span data-stu-id="b6f29-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6f29-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="b6f29-107">Prerequisites</span></span>

* <span data-ttu-id="b6f29-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="b6f29-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="b6f29-109">你最喜欢的代码编辑器</span><span class="sxs-lookup"><span data-stu-id="b6f29-109">Your favorite code editor</span></span>

<span data-ttu-id="b6f29-110">可以使用命令 `dotnet --info` 检查已安装哪些版本的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="b6f29-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="b6f29-111">入门</span><span class="sxs-lookup"><span data-stu-id="b6f29-111">Getting started</span></span>

<span data-ttu-id="b6f29-112">在 .NET Core 控制台应用程序中使用 `dotnet-svcutil.xmlserializer`：</span><span class="sxs-lookup"><span data-stu-id="b6f29-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="b6f29-113">在 .NET Framework 中使用默认模板“WCF 服务应用程序”创建一个名为“MyWCFService”的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="b6f29-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="b6f29-114">在服务方法上添加 `[XmlSerializerFormat]` 属性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b6f29-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="b6f29-115">创建 .NET Core 控制台应用程序作为面向 .NET Core 2.1 或更高版本的 WCF 客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="b6f29-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="b6f29-116">例如，使用以下命令创建名为“MyWCFClient”的应用：</span><span class="sxs-lookup"><span data-stu-id="b6f29-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="b6f29-117">要确保项目面向 .NET Core 2.1 或更高版本，请检查项目文件中的 `TargetFramework` XML 元素：</span><span class="sxs-lookup"><span data-stu-id="b6f29-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="b6f29-118">通过运行以下命令将包引用添加到 `System.ServiceModel.Http`：</span><span class="sxs-lookup"><span data-stu-id="b6f29-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="b6f29-119">添加 WCF 客户端代码：</span><span class="sxs-lookup"><span data-stu-id="b6f29-119">Add the WCF Client code:</span></span>

    ```csharp
    using System.ServiceModel;

        class Program
        {
            static void Main(string[] args)
            {
                var myBinding = new BasicHttpBinding();
                var myEndpoint = new EndpointAddress("http://localhost:2561/Service1.svc"); //Fill your service url here
                var myChannelFactory = new ChannelFactory<IService1>(myBinding, myEndpoint);
                IService1 client = myChannelFactory.CreateChannel();
                string s = client.GetData(1);
                ((ICommunicationObject)client).Close();
            }
        }

    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

5. <span data-ttu-id="b6f29-120">通过运行以下命令将引用添加到 `dotnet-svcutil.xmlserializer` 包：</span><span class="sxs-lookup"><span data-stu-id="b6f29-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="b6f29-121">运行该命令应向项目文件中添加一个类似于以下内容的条目：</span><span class="sxs-lookup"><span data-stu-id="b6f29-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="b6f29-122">通过运行 `dotnet build` 生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="b6f29-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="b6f29-123">如果一切顺利，则会在输出文件夹中生成名为“MyWCFClient.XmlSerializers.dll”的程序集。</span><span class="sxs-lookup"><span data-stu-id="b6f29-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="b6f29-124">如果该工具无法生成程序集，将在生成输出中看到警告。</span><span class="sxs-lookup"><span data-stu-id="b6f29-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="b6f29-125">例如，通过在浏览器中运行 `http://localhost:2561/Service1.svc` 来启动 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="b6f29-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="b6f29-126">然后启动客户端应用程序，它将在运行时自动加载和使用预生成的序列化程序。</span><span class="sxs-lookup"><span data-stu-id="b6f29-126">Then start the client application, and it will automatically load and use the pre-generated serializers at run time.</span></span>
