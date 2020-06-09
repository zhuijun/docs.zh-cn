---
title: 如何：使用双工协定访问服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597210"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="9de78-102">如何：使用双工协定访问服务</span><span class="sxs-lookup"><span data-stu-id="9de78-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="9de78-103">Windows Communication Foundation （WCF）的一项功能是能够创建使用双工消息传递模式的服务。</span><span class="sxs-lookup"><span data-stu-id="9de78-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="9de78-104">此模式允许服务通过回调与客户端进行通信。</span><span class="sxs-lookup"><span data-stu-id="9de78-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="9de78-105">本主题演示在实现回调接口的客户端类中创建 WCF 客户端的步骤。</span><span class="sxs-lookup"><span data-stu-id="9de78-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="9de78-106">双向绑定向服务公开客户端的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="9de78-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="9de78-107">客户端应使用安全来确保仅连接到自己信任的服务。</span><span class="sxs-lookup"><span data-stu-id="9de78-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="9de78-108">有关创建基本 WCF 服务和客户端的教程，请参阅[入门教程](../getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="9de78-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="9de78-109">访问双工服务</span><span class="sxs-lookup"><span data-stu-id="9de78-109">To access a duplex service</span></span>

1. <span data-ttu-id="9de78-110">创建包含两个接口的服务。</span><span class="sxs-lookup"><span data-stu-id="9de78-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="9de78-111">第一个接口用于服务，第二个接口用于回调。</span><span class="sxs-lookup"><span data-stu-id="9de78-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="9de78-112">有关创建双工服务的详细信息，请参阅[如何：创建双工协定](how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="9de78-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="9de78-113">运行服务。</span><span class="sxs-lookup"><span data-stu-id="9de78-113">Run the service.</span></span>

3. <span data-ttu-id="9de78-114">使用 " [svcutil.exe" 元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)为客户端生成协定（接口）。</span><span class="sxs-lookup"><span data-stu-id="9de78-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="9de78-115">有关如何执行此操作的信息，请参阅[如何：创建客户端](../how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="9de78-115">For information about how to do this, see  [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="9de78-116">在客户端类中实现回调接口，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="9de78-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. <span data-ttu-id="9de78-117">创建 <xref:System.ServiceModel.InstanceContext> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="9de78-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="9de78-118">构造函数需要客户端类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="9de78-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="9de78-119">使用需要对象的构造函数创建 WCF 客户端的实例 <xref:System.ServiceModel.InstanceContext> 。</span><span class="sxs-lookup"><span data-stu-id="9de78-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="9de78-120">该构造函数的第二个参数是配置文件中找到的终结点的名称。</span><span class="sxs-lookup"><span data-stu-id="9de78-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="9de78-121">根据需要调用 WCF 客户端的方法。</span><span class="sxs-lookup"><span data-stu-id="9de78-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="9de78-122">示例</span><span class="sxs-lookup"><span data-stu-id="9de78-122">Example</span></span>

<span data-ttu-id="9de78-123">下面的代码示例演示如何创建一个访问双工协定的客户端类。</span><span class="sxs-lookup"><span data-stu-id="9de78-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9de78-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9de78-124">See also</span></span>

- [<span data-ttu-id="9de78-125">入门教程</span><span class="sxs-lookup"><span data-stu-id="9de78-125">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="9de78-126">如何：创建双工协定</span><span class="sxs-lookup"><span data-stu-id="9de78-126">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="9de78-127">ServiceModel 元数据实用工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9de78-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="9de78-128">如何：创建客户端</span><span class="sxs-lookup"><span data-stu-id="9de78-128">How to: Create a Client</span></span>](../how-to-create-a-wcf-client.md)
- [<span data-ttu-id="9de78-129">如何：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="9de78-129">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
