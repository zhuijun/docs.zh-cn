---
title: 如何：将服务名字对象用于 WSDL 协定
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 70d7e9ff45616f832597ebc48db00198967935c6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601135"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="f8067-102">如何：将服务名字对象用于 WSDL 协定</span><span class="sxs-lookup"><span data-stu-id="f8067-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="f8067-103">在某些情况下，您可能希望具有完全自包含的 COM 互操作客户端。</span><span class="sxs-lookup"><span data-stu-id="f8067-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="f8067-104">您要调用的服务可能不会公开 MEX 终结点，而 WCF 客户端 DLL 可能不会为 COM 互操作注册。</span><span class="sxs-lookup"><span data-stu-id="f8067-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="f8067-105">在这些情况下，您可以创建用于描述该服务的 WSDL 文件，并将该文件传递到 WCF 服务标记中。</span><span class="sxs-lookup"><span data-stu-id="f8067-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="f8067-106">本主题描述如何使用 WCF WSDL 标记调用 WCF 入门示例。</span><span class="sxs-lookup"><span data-stu-id="f8067-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="f8067-107">使用 WSDL 服务标记</span><span class="sxs-lookup"><span data-stu-id="f8067-107">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="f8067-108">打开并生成 GettingStarted 示例解决方案。</span><span class="sxs-lookup"><span data-stu-id="f8067-108">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="f8067-109">打开 Internet Explorer 并浏览到， `http://localhost/ServiceModelSamples/Service.svc` 确保该服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="f8067-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="f8067-110">在 Service.cs 文件中，将下面的属性添加到 CalculatorService 类中：</span><span class="sxs-lookup"><span data-stu-id="f8067-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="f8067-111">将绑定命名空间添加到服务 App.config 中：</span><span class="sxs-lookup"><span data-stu-id="f8067-111">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="f8067-112">为要读取的应用程序创建 WSDL 文件。</span><span class="sxs-lookup"><span data-stu-id="f8067-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="f8067-113">由于命名空间是在步骤3和步骤4中添加的，因此可以使用 IE 通过浏览到来查询服务的整个 WSDL 说明 `http://localhost/ServiceModelSamples/Service.svc?wsdl` 。</span><span class="sxs-lookup"><span data-stu-id="f8067-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="f8067-114">然后，将文件从 Internet Explorer 另存为 serviceWSDL.xml。</span><span class="sxs-lookup"><span data-stu-id="f8067-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="f8067-115">如果未在步骤 3 和 4 中指定命名空间，则从查询上述 URL 返回的 WSDL 文档将不是完整的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="f8067-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="f8067-116">返回的 WSDL 文档将包括导入其他 WSDL 文档的多条导入语句。</span><span class="sxs-lookup"><span data-stu-id="f8067-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="f8067-117">您必须完成每条导入语句并生成完整的 WSDL 文档，从而将从服务返回的 WSDL 与导入的 WSDL 合并在一起。</span><span class="sxs-lookup"><span data-stu-id="f8067-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="f8067-118">打开 Visual Basic 6.0 并创建一个新的 Standard .exe 文件。</span><span class="sxs-lookup"><span data-stu-id="f8067-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="f8067-119">在窗体中添加一个按钮并双击该按钮，以将以下代码添加到 Click 处理程序中：</span><span class="sxs-lookup"><span data-stu-id="f8067-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > 如果标记的格式不正确，或者服务不可用，则对 `GetObject` 的调用将返回一个错误，指示“无效的语法”。  <span data-ttu-id="f8067-121">如果您收到此错误，请确保所使用的标记正确无误且服务可用。</span><span class="sxs-lookup"><span data-stu-id="f8067-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="f8067-122">运行 Visual Basic 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f8067-122">Run the Visual Basic application.</span></span> <span data-ttu-id="f8067-123">将显示一个消息框，其中列出调用 Subtract(145, 76.54) 的结果。</span><span class="sxs-lookup"><span data-stu-id="f8067-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8067-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8067-124">See also</span></span>

- [<span data-ttu-id="f8067-125">入门</span><span class="sxs-lookup"><span data-stu-id="f8067-125">Getting Started</span></span>](../samples/getting-started-sample.md)
- [<span data-ttu-id="f8067-126">COM 应用程序集成概述</span><span class="sxs-lookup"><span data-stu-id="f8067-126">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)
