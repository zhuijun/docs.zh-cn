---
title: 如何：在配置中指定客户端绑定
description: 了解如何在配置文件中以声明方式指定 WCF 客户端的绑定。 在此示例中，客户端将访问服务。
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 28778b6ae853199c5d7943f329bb087760f4bb11
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244486"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="4a0ff-104">如何：在配置中指定客户端绑定</span><span class="sxs-lookup"><span data-stu-id="4a0ff-104">How to: Specify a Client Binding in Configuration</span></span>
<span data-ttu-id="4a0ff-105">在此示例中，创建了一个使用计算器服务的客户端控制台应用程序，并在配置中以声明方式为该客户端指定了绑定。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-105">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="4a0ff-106">该客户端访问实现了 `CalculatorService` 接口的 `ICalculator`，并且服务和客户端都使用 <xref:System.ServiceModel.BasicHttpBinding> 类。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="4a0ff-107">上述过程假设计算器服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-107">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="4a0ff-108">有关如何生成服务的信息，请参阅[如何：在配置中指定服务绑定](how-to-specify-a-service-binding-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-108">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="4a0ff-109">它还使用 Windows Communication Foundation （WCF）提供的使用的[元数据实用工具（Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)来自动生成客户端组件。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="4a0ff-110">该工具生成用于访问服务的客户端代码和配置。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-110">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="4a0ff-111">客户端分两部分生成。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-111">The client is built in two parts.</span></span> <span data-ttu-id="4a0ff-112">Svcutil.exe 生成实现 `ClientCalculator` 接口的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="4a0ff-113">然后，通过构造 `ClientCalculator` 的实例来构造客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-113">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="4a0ff-114">通常，最佳做法是以声明方式在配置中指定绑定和地址信息，而不是在代码中强制指定。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-114">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="4a0ff-115">在代码中定义终结点通常是不可行的，因为已部署服务的绑定和地址通常与在部署服务时所用的绑定和地址不同。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-115">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="4a0ff-116">一般说来，通过将绑定和寻址信息放置在代码之外，无需重新编译或重新部署应用程序即可更改这些信息。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-116">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="4a0ff-117">您可以使用[配置编辑器工具（SvcConfigEditor.exe）](configuration-editor-tool-svcconfigeditor-exe.md)执行以下所有配置步骤。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-117">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="4a0ff-118">有关此示例的源副本，请参阅[BasicBinding](./samples/basicbinding.md)示例。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-118">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="4a0ff-119">在配置中指定客户端绑定</span><span class="sxs-lookup"><span data-stu-id="4a0ff-119">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="4a0ff-120">在命令行中，使用 Svcutil.exe 根据服务元数据生成代码。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-120">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="4a0ff-121">生成的客户端包含 `ICalculator` 接口，该接口定义了客户端实现必须满足的服务协定。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-121">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="4a0ff-122">生成的客户端还包含 `ClientCalculator` 的实现。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-122">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="4a0ff-123">Svcutil.exe 还为使用 <xref:System.ServiceModel.BasicHttpBinding> 类的客户端生成配置。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-123">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="4a0ff-124">使用 Visual Studio 时，将此文件命名 App.config。请注意，在服务的实现内部，未指定地址和绑定信息。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-124">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="4a0ff-125">而且，不必编写代码也可从配置文件中检索该信息。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-125">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="4a0ff-126">在应用程序中创建 `ClientCalculator` 的实例，然后调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-126">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="4a0ff-127">编译并运行客户端。</span><span class="sxs-lookup"><span data-stu-id="4a0ff-127">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0ff-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="4a0ff-128">See also</span></span>

- [<span data-ttu-id="4a0ff-129">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="4a0ff-129">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
