---
title: 教程：使用 Windows Communication Foundation 客户端
description: 了解如何创建客户端实例、编译应用程序以及与服务进行通信，这是有关创建 WCF 应用程序的一系列文章。
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c94d5f8af679580c4194aaaadeda759098953d2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244330"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="39f85-103">教程：使用 Windows Communication Foundation 客户端</span><span class="sxs-lookup"><span data-stu-id="39f85-103">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="39f85-104">本教程介绍创建基本 Windows Communication Foundation （WCF）应用程序所需的五个任务中的最后一个。</span><span class="sxs-lookup"><span data-stu-id="39f85-104">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="39f85-105">有关教程的概述，请参阅[教程： Windows Communication Foundation 应用程序入门](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="39f85-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="39f85-106">创建并配置 Windows Communication Foundation （WCF）代理后，您可以创建一个客户端实例并编译该客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="39f85-106">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="39f85-107">然后，你可以使用它来与 WCF 服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="39f85-107">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="39f85-108">在本教程中，你将了解如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="39f85-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="39f85-109">添加代码以使用 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="39f85-109">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="39f85-110">测试 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="39f85-110">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="39f85-111">添加代码以使用 WCF 客户端</span><span class="sxs-lookup"><span data-stu-id="39f85-111">Add code to use the WCF client</span></span>

<span data-ttu-id="39f85-112">客户端代码执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="39f85-112">The client code does the following steps:</span></span>

- <span data-ttu-id="39f85-113">实例化 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="39f85-113">Instantiates the WCF client.</span></span>
- <span data-ttu-id="39f85-114">从生成的代理调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="39f85-114">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="39f85-115">完成操作调用后关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="39f85-115">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="39f85-116">从**GettingStartedClient**项目中打开**Program.cs**或**Module1**文件，并将其代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="39f85-116">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

<span data-ttu-id="39f85-117">请注意 `using` 导入的（对于 Visual c #）或 `Imports` （对于 Visual Basic）语句 `GettingStartedClient.ServiceReference1` 。</span><span class="sxs-lookup"><span data-stu-id="39f85-117">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="39f85-118">此语句将导入 Visual Studio 生成的带有**添加服务引用**函数的代码。</span><span class="sxs-lookup"><span data-stu-id="39f85-118">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="39f85-119">此代码实例化 WCF 代理，并调用计算器服务公开的每个服务操作。</span><span class="sxs-lookup"><span data-stu-id="39f85-119">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="39f85-120">然后，它会关闭代理并结束程序。</span><span class="sxs-lookup"><span data-stu-id="39f85-120">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="39f85-121">测试 WCF 客户端</span><span class="sxs-lookup"><span data-stu-id="39f85-121">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="39f85-122">从 Visual Studio 测试应用程序</span><span class="sxs-lookup"><span data-stu-id="39f85-122">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="39f85-123">保存并生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="39f85-123">Save and build the solution.</span></span>

2. <span data-ttu-id="39f85-124">选择**GettingStartedLib**文件夹，然后从快捷菜单中选择 "**设为启动项目**"。</span><span class="sxs-lookup"><span data-stu-id="39f85-124">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="39f85-125">从 "**启动项目**" 中，从下拉列表中选择 " **GettingStartedLib** "，然后选择 "**运行**" 或按**F5**。</span><span class="sxs-lookup"><span data-stu-id="39f85-125">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="39f85-126">在命令提示符下测试应用程序</span><span class="sxs-lookup"><span data-stu-id="39f85-126">Test the application from a command prompt</span></span>

1. <span data-ttu-id="39f85-127">以管理员身份打开命令提示符，然后导航到你的 Visual Studio 解决方案目录。</span><span class="sxs-lookup"><span data-stu-id="39f85-127">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="39f85-128">若要启动该服务：输入*GettingStartedHost\bin\Debug\GettingStartedHost.exe*。</span><span class="sxs-lookup"><span data-stu-id="39f85-128">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="39f85-129">若要启动客户端：请打开另一个命令提示符，导航到你的 Visual Studio 解决方案目录，然后输入*GettingStartedClient\bin\Debug\GettingStartedClient.exe*。</span><span class="sxs-lookup"><span data-stu-id="39f85-129">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="39f85-130">*GettingStartedHost.exe*生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="39f85-130">*GettingStartedHost.exe* produces the following output:</span></span>

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   <span data-ttu-id="39f85-131">*GettingStartedClient.exe*生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="39f85-131">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="39f85-132">后续步骤</span><span class="sxs-lookup"><span data-stu-id="39f85-132">Next steps</span></span>

<span data-ttu-id="39f85-133">你现在已经完成了 WCF 入门教程中的所有任务。</span><span class="sxs-lookup"><span data-stu-id="39f85-133">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="39f85-134">在本教程中，你将了解：</span><span class="sxs-lookup"><span data-stu-id="39f85-134">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="39f85-135">在本教程中，你将了解如何执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="39f85-135">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="39f85-136">添加代码以使用 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="39f85-136">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="39f85-137">测试 WCF 客户端。</span><span class="sxs-lookup"><span data-stu-id="39f85-137">Test the WCF client.</span></span>

<span data-ttu-id="39f85-138">如果在任何步骤中遇到问题或错误，请按照故障排除一文中的步骤进行修复。</span><span class="sxs-lookup"><span data-stu-id="39f85-138">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39f85-139">排查 WCF 入门教程</span><span class="sxs-lookup"><span data-stu-id="39f85-139">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
