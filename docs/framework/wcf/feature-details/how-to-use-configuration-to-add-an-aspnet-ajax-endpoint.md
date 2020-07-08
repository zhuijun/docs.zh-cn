---
title: 如何：使用配置来添加 ASP.NET AJAX 终结点
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 97f8174161068f2c72b6bd2bc4e8a3044f5bccdd
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051657"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="6f21f-102">如何：使用配置来添加 ASP.NET AJAX 终结点</span><span class="sxs-lookup"><span data-stu-id="6f21f-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="6f21f-103">Windows Communication Foundation （WCF）允许你创建一个服务，该服务使可从客户端网站上的 JavaScript 中调用的 ASP.NET 启用 AJAX 的终结点可用。</span><span class="sxs-lookup"><span data-stu-id="6f21f-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="6f21f-104">若要创建此类终结点，可以使用配置文件（与所有其他 Windows Communication Foundation （WCF）终结点一样），或使用不需要任何配置元素的方法。</span><span class="sxs-lookup"><span data-stu-id="6f21f-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="6f21f-105">本主题演示配置方法。</span><span class="sxs-lookup"><span data-stu-id="6f21f-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="6f21f-106">允许服务终结点成为 ASP.NET 启用 AJAX 的过程部分包括将终结点配置为使用 <xref:System.ServiceModel.WebHttpBinding> 和来添加 [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) 终结点行为。</span><span class="sxs-lookup"><span data-stu-id="6f21f-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="6f21f-107">配置终结点后，实现和托管服务的步骤与任何 WCF 服务使用的步骤类似。</span><span class="sxs-lookup"><span data-stu-id="6f21f-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="6f21f-108">有关工作示例，请参阅[使用 HTTP POST 的 AJAX 服务](../samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="6f21f-108">For a working example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="6f21f-109">有关如何在不使用配置的情况下配置 ASP.NET AJAX 终结点的详细信息，请参阅[如何：在不使用配置的情况下添加 ASP.NET AJAX 终结点](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="6f21f-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="6f21f-110">创建基本 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="6f21f-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="6f21f-111">使用以特性标记的接口定义基本 WCF 服务协定 <xref:System.ServiceModel.ServiceContractAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="6f21f-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="6f21f-112">用 <xref:System.ServiceModel.OperationContractAttribute> 标记每个操作。</span><span class="sxs-lookup"><span data-stu-id="6f21f-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="6f21f-113">确保设置 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="6f21f-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="6f21f-114">使用 `ICalculator` 实现 `CalculatorService` 服务协定。</span><span class="sxs-lookup"><span data-stu-id="6f21f-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. <span data-ttu-id="6f21f-115">定义 `ICalculator` 和 `CalculatorService` 实现的命名空间，方法是将它们放置在一个命名空间块中。</span><span class="sxs-lookup"><span data-stu-id="6f21f-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="6f21f-116">创建服务的 ASP.NET AJAX 终结点</span><span class="sxs-lookup"><span data-stu-id="6f21f-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="6f21f-117">创建一个行为配置，并 [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) 为该服务的 ASP.NET 启用 AJAX 的终结点指定行为。</span><span class="sxs-lookup"><span data-stu-id="6f21f-117">Create a behavior configuration and specify the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="6f21f-118">为使用 <xref:System.ServiceModel.WebHttpBinding> 和前面的步骤中定义的 ASP.NET AJAX 行为的服务创建终结点。</span><span class="sxs-lookup"><span data-stu-id="6f21f-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="6f21f-119">在 IIS 中承载服务</span><span class="sxs-lookup"><span data-stu-id="6f21f-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="6f21f-120">若要在 IIS 中承载服务，请使用应用程序中的 .svc 扩展创建名为 service 的新文件。</span><span class="sxs-lookup"><span data-stu-id="6f21f-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="6f21f-121">通过为服务添加适当的[ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)指令信息来编辑此文件。</span><span class="sxs-lookup"><span data-stu-id="6f21f-121">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="6f21f-122">例如，`CalculatorService` 示例的服务文件中的内容包含以下信息。</span><span class="sxs-lookup"><span data-stu-id="6f21f-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```aspx-csharp
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="6f21f-123">有关在 IIS 中承载的详细信息，请参阅[如何：在 iis 中承载 WCF 服务](how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="6f21f-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="6f21f-124">调用服务</span><span class="sxs-lookup"><span data-stu-id="6f21f-124">To call the service</span></span>  
  
1. <span data-ttu-id="6f21f-125">终结点是在相对于 .svc 文件的空地址处配置的，因此该服务现在可用，并可通过将请求发送到服务 .svc/ \<operation> -例如，为该操作发送服务。 `Add`</span><span class="sxs-lookup"><span data-stu-id="6f21f-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="6f21f-126">可以通过在 ASP.NET AJAX 脚本管理器控件的脚本集合中输入终结点 URL 来使用它。</span><span class="sxs-lookup"><span data-stu-id="6f21f-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="6f21f-127">有关示例，请参阅[使用 HTTP POST 的 AJAX 服务](../samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="6f21f-127">For an example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f21f-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f21f-128">See also</span></span>

- [<span data-ttu-id="6f21f-129">为 ASP.NET AJAX 创建 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="6f21f-129">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="6f21f-130">如何：将支持 AJAX 的 ASP.NET Web 服务迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="6f21f-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
