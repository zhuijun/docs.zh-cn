---
title: 如何：将服务名字对象与元数据交换协定一起使用
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 04a940a6e8f010e5cd851684c5fc62bab2a1a034
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601161"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="880ea-102">如何：将服务名字对象与元数据交换协定一起使用</span><span class="sxs-lookup"><span data-stu-id="880ea-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="880ea-103">开发一些新的 WCF 服务后，你可能会决定希望能够从脚本或 Visual Basic 6.0 应用程序调用这些服务。</span><span class="sxs-lookup"><span data-stu-id="880ea-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="880ea-104">一种方法是生成 WCF 客户端程序集，使用 COM 注册该程序集，将程序集安装到 GAC 中，然后从 Visual Basic 代码引用 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="880ea-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="880ea-105">分发应用程序时，还必须分发 WCF 客户端程序集。</span><span class="sxs-lookup"><span data-stu-id="880ea-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="880ea-106">然后，用户必须使用 COM 注册 WCF 客户端程序集，并且将该程序集放置在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="880ea-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="880ea-107">WCF COM 互操作还允许您在不依赖 WCF 客户端程序集的情况下进行相同的服务调用。</span><span class="sxs-lookup"><span data-stu-id="880ea-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="880ea-108">利用 WCF 名字对象，您可以通过指定元数据交换（Mex）终结点 URI，从任何与 COM 兼容的语言（Visual Basic、VBScript、Visual Basic for Applications （VBA）等）调用任何 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="880ea-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="880ea-109">本主题说明如何使用指定 Mex 终结点的 WCF 名字对象调用入门 WCF 示例。</span><span class="sxs-lookup"><span data-stu-id="880ea-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="880ea-110">WCF 客户端程序集定义的类型永远不会实际实例化。</span><span class="sxs-lookup"><span data-stu-id="880ea-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="880ea-111">该程序集只用于元数据。</span><span class="sxs-lookup"><span data-stu-id="880ea-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="880ea-112">使用带有 Mex 地址的服务标记</span><span class="sxs-lookup"><span data-stu-id="880ea-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="880ea-113">生成入门示例，并使用 Internet Explorer 浏览到其 URL （ `http://localhost/ServiceModelSamples/Service.svc` ）以确保服务正常工作。</span><span class="sxs-lookup"><span data-stu-id="880ea-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (`http://localhost/ServiceModelSamples/Service.svc`) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="880ea-114">生成 Visual Basic 脚本或包含以下代码的 Visual Basic 应用程序：</span><span class="sxs-lookup"><span data-stu-id="880ea-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="880ea-115">运行 Visual Basic 应用程序或脚本。</span><span class="sxs-lookup"><span data-stu-id="880ea-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="880ea-116">您所调用的服务必须公开标记的 Mex 终结点，以便能够从服务中读取元数据。</span><span class="sxs-lookup"><span data-stu-id="880ea-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="880ea-117">有关详细信息，请参阅[如何：使用配置文件发布服务的元数据](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="880ea-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="880ea-118">如果标记格式不正确，或如果服务不可用，则对 `GetObject` 的调用将返回一个错误，指示“语法无效”。</span><span class="sxs-lookup"><span data-stu-id="880ea-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="880ea-119">如果您收到此错误，请确保所使用的标记正确无误且服务可用。</span><span class="sxs-lookup"><span data-stu-id="880ea-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880ea-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="880ea-120">See also</span></span>

- [<span data-ttu-id="880ea-121">如何：使用未注册的 Windows Communication Foundation 服务名字对象</span><span class="sxs-lookup"><span data-stu-id="880ea-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="880ea-122">如何：将服务名字对象用于 WSDL 协定</span><span class="sxs-lookup"><span data-stu-id="880ea-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)
