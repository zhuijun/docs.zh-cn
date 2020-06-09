---
title: 安全性验证
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 70408976469b1cbcf9c4679bd91d81872ec74ae1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599966"
---
# <a name="security-validation"></a><span data-ttu-id="8a4d9-102">安全验证</span><span class="sxs-lookup"><span data-stu-id="8a4d9-102">Security validation</span></span>
<span data-ttu-id="8a4d9-103">此示例演示如何使用自定义行为来验证计算机上的服务，以确保服务符合特定条件。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="8a4d9-104">在此示例中，自定义行为通过以下方法验证服务：扫描服务上的每个终结点，并查看这些终结点是否包含安全的绑定元素。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="8a4d9-105">此示例基于[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a4d9-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="8a4d9-107">终结点验证自定义行为</span><span class="sxs-lookup"><span data-stu-id="8a4d9-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="8a4d9-108">通过将用户代码添加到 `Validate` 接口中包含的 <xref:System.ServiceModel.Description.IServiceBehavior> 方法，可以为某个服务或终结点指定自定义行为，以便执行用户定义的操作。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="8a4d9-109">下面的代码用于遍历服务中包含的每个终结点，这将在其绑定集合中搜索安全的绑定。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="8a4d9-110">通过将下面的代码添加到 Web.config 文件可以添加服务可识别的 `serviceValidate` 行为扩展。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>
    ...
</system.serviceModel>
```  
  
 <span data-ttu-id="8a4d9-111">将行为扩展添加到服务之后，现在即可将 `endpointValidate` 行为添加到 Web.config 文件的行为列表中，从而添加到服务中。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="8a4d9-112">添加到 Web.config 文件的行为及其扩展可将行为应用到各个服务，而添加到 Machine.config 文件的行为及其扩展则将行为应用到计算机上的每个活动服务。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a4d9-113">向所有服务中添加行为时，建议在进行任何更改之前备份 Machine.config 文件。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="8a4d9-114">现在运行此示例的 client\bin 目录中提供的客户端。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="8a4d9-115">引发异常，并出现以下消息： "无法激活请求的服务 http://localhost/servicemodelsamples/service.svc 。"</span><span class="sxs-lookup"><span data-stu-id="8a4d9-115">An exception is thrown with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="8a4d9-116">这是预期的行为，因为终结点验证行为认为某个终结点不安全，并阻止服务启动。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="8a4d9-117">该行为还会引发一个内部异常，以描述哪个终结点不安全，并在“System.ServiceModel 4.0.0.0”源和“WebHost”类别下的系统事件查看器中写入一则消息。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="8a4d9-118">还可以在此示例中打开对服务的跟踪。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="8a4d9-119">这样可以使用户查看终结点验证行为引发的异常，方法是：使用服务跟踪查看器工具打开生成的服务跟踪。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
### <a name="view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="8a4d9-120">查看事件查看器中失败的终结点验证异常消息</span><span class="sxs-lookup"><span data-stu-id="8a4d9-120">View failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="8a4d9-121">单击 "**开始**" 菜单，然后选择 "**运行 ...**"。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="8a4d9-122">键入 `eventvwr` ，然后单击 **“确定”**。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="8a4d9-123">在事件查看器 "窗口中，单击"**应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="8a4d9-124">在**应用程序**窗口中的 "WebHost" 类别下双击最近添加的 "system.servicemodel 4.0.0.0" 事件，以查看不安全的终结点消息。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="8a4d9-125">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="8a4d9-125">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8a4d9-126">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8a4d9-127">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8a4d9-128">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8a4d9-129">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8a4d9-130">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="8a4d9-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8a4d9-131">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="8a4d9-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a4d9-132">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="8a4d9-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="8a4d9-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a4d9-133">See also</span></span>

- <span data-ttu-id="8a4d9-134">[AppFabric 监视示例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8a4d9-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
