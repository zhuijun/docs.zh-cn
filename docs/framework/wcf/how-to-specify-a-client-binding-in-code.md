---
title: 如何：在代码中指定客户端绑定
description: 了解如何在代码中以强制方式为 WCF 客户端指定绑定。 在此示例中，客户端将访问服务。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: e5e1dff98121985a598579d83043de838e21e5f1
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244499"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="f5bc8-104">如何：在代码中指定客户端绑定</span><span class="sxs-lookup"><span data-stu-id="f5bc8-104">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="f5bc8-105">在本示例中，创建了一个使用计算器服务的客户端，并在代码中以强制方式指定该客户端的绑定。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-105">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="f5bc8-106">该客户端访问实现了 `CalculatorService` 接口的 `ICalculator`，并且服务和客户端都使用 <xref:System.ServiceModel.BasicHttpBinding> 类。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="f5bc8-107">此过程假设计算器服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-107">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="f5bc8-108">有关生成服务的信息，请参阅[如何：在配置中指定服务绑定](how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-108">For information about building the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="f5bc8-109">它还使用 " [Svcutil.exe" 的元数据实用工具（）](servicemodel-metadata-utility-tool-svcutil-exe.md)WINDOWS COMMUNICATION FOUNDATION （WCF）来自动生成客户端组件。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="f5bc8-110">该工具生成用于访问服务的客户端代码。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-110">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="f5bc8-111">客户端分两部分生成。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-111">The client is built in two parts.</span></span> <span data-ttu-id="f5bc8-112">Svcutil.exe 生成实现 `ClientCalculator` 接口的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="f5bc8-113">然后，通过构造 `ClientCalculator` 的一个实例，并在代码中指定服务的绑定和地址，构造此客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-113">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="f5bc8-114">有关此示例的源副本，请参阅[BasicBinding](./samples/basicbinding.md)示例。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-114">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="f5bc8-115">在代码中指定自定义绑定</span><span class="sxs-lookup"><span data-stu-id="f5bc8-115">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="f5bc8-116">在命令行中，使用 Svcutil.exe 根据服务元数据生成代码。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-116">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="f5bc8-117">生成的客户端包含 `ICalculator` 接口，该接口定义了客户端实现必须满足的服务协定。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-117">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="f5bc8-118">生成的客户端还包含 `ClientCalculator` 的实现。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-118">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="f5bc8-119">创建 `ClientCalculator` 的一个实例（该实例在客户端应用程序中使用 <xref:System.ServiceModel.BasicHttpBinding> 类），然后调用指定地址上的服务操作。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-119">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="f5bc8-120">编译并运行客户端。</span><span class="sxs-lookup"><span data-stu-id="f5bc8-120">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bc8-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5bc8-121">See also</span></span>

- [<span data-ttu-id="f5bc8-122">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="f5bc8-122">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
