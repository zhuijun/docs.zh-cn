---
title: 与 ASP.NET Web 服务的互操作性
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: f38209ffe2161e58528a108b29e730665a65da37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598861"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="d0445-102">与 ASP.NET Web 服务的互操作性</span><span class="sxs-lookup"><span data-stu-id="d0445-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="d0445-103">可以通过确保使用这两种技术实现的服务符合 WS-I Basic Profile 1.1 规范，来实现 ASP.NET Web 服务与 Windows Communication Foundation （WCF） Web 服务之间的互操作性。</span><span class="sxs-lookup"><span data-stu-id="d0445-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="d0445-104">符合 WS-I Basic Profile 1.1 的 ASP.NET Web 服务可通过 WCF 系统提供的绑定与 WCF 客户端进行互操作 <xref:System.ServiceModel.BasicHttpBinding> 。</span><span class="sxs-lookup"><span data-stu-id="d0445-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="d0445-105">使用 ASP.NET 2.0 选项将 <xref:System.Web.Services.WebService> 和属性添加 <xref:System.Web.Services.WebMethodAttribute> 到接口而不是类，并编写类来实现接口，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="d0445-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="d0445-106">使用此选项是首选方法，因为具有 <xref:System.Web.Services.WebService> 属性的接口为服务所执行的操作构成了一个协定，在以不同方式实现该协定的各个类中，都可重用该协定。</span><span class="sxs-lookup"><span data-stu-id="d0445-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="d0445-107">避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 特性依据 SOAP 消息正文元素的完全限定名称将消息路由到方法，而应使用 `SOAPAction` 标头。</span><span class="sxs-lookup"><span data-stu-id="d0445-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="d0445-108">WCF 使用 `SOAPAction` HTTP 标头来路由消息。</span><span class="sxs-lookup"><span data-stu-id="d0445-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="d0445-109">只要为 XML 显式定义了命名空间，则在默认情况下，<xref:System.Xml.Serialization.XmlSerializer> 将类型序列化为的 XML 与 <xref:System.Runtime.Serialization.DataContractSerializer> 将类型序列化为的 XML 在语义上完全相同。</span><span class="sxs-lookup"><span data-stu-id="d0445-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="d0445-110">定义与 Web 服务一起使用的数据类型时，如果采用 WCF，则请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d0445-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="d0445-111">使用 .NET Framework 类而不是 XML 架构来定义该类型。</span><span class="sxs-lookup"><span data-stu-id="d0445-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="d0445-112">仅将 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 添加到该类，使用后者显式定义类型的命名空间。</span><span class="sxs-lookup"><span data-stu-id="d0445-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="d0445-113">不要添加 <xref:System.Xml.Serialization> 命名空间中的其他属性来控制如何将 .NET Framework 类转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="d0445-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="d0445-114">通过采用此方法，以后可将 .NET 类转换为附加了 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 的数据协定，而无需为了传输而对类序列化成的 XML 进行重大更改。</span><span class="sxs-lookup"><span data-stu-id="d0445-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="d0445-115">ASP.NET Web 服务在消息中使用的类型可以作为数据协定由 WCF 应用程序进行处理，从而实现其他优势，并提高 WCF 应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="d0445-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="d0445-116">避免使用 Internet Information Services (IIS) 提供的身份验证选项。</span><span class="sxs-lookup"><span data-stu-id="d0445-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="d0445-117">WCF 客户端不支持它们。</span><span class="sxs-lookup"><span data-stu-id="d0445-117">WCF clients do not support them.</span></span> <span data-ttu-id="d0445-118">如果服务必须是安全的，请使用 WCF 提供的选项，因为这些选项非常可靠，并且基于标准协议。</span><span class="sxs-lookup"><span data-stu-id="d0445-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="d0445-119">由加载 ServiceModel HttpModule 而导致的性能影响</span><span class="sxs-lookup"><span data-stu-id="d0445-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="d0445-120">在 .NET Framework 3.0 中，WCF `HttpModule` 安装在根 Web.config 文件中，因此，每个 ASP.NET 应用程序都启用了 WCF。</span><span class="sxs-lookup"><span data-stu-id="d0445-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="d0445-121">这可能会影响性能，因此，可以移除 Web.config 文件的 `ServiceModel`，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="d0445-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="d0445-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0445-122">See also</span></span>

- [<span data-ttu-id="d0445-123">如何：配置 WCF 服务以与 ASP.NET Web 服务客户端进行互操作</span><span class="sxs-lookup"><span data-stu-id="d0445-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](config-wcf-service-with-aspnet-web-service.md)
