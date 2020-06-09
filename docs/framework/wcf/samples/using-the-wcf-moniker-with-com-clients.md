---
title: 对 COM 客户端使用 WCF 标记
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 76b7697f431575e7bde83204739cb23f96d27064
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596482"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="a9d0a-102">对 COM 客户端使用 WCF 标记</span><span class="sxs-lookup"><span data-stu-id="a9d0a-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="a9d0a-103">此示例演示如何使用 Windows Communication Foundation （WCF）服务名字对象将 Web 服务集成到基于 COM 的开发环境中，例如 Microsoft Office Visual Basic for Applications （Office VBA）或 Visual Basic 6.0。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="a9d0a-104">本示例由 Windows 脚本宿主客户端 (.vbs)、客户端支持库 (.dll) 和 Internet 信息服务 (IIS) 承载的服务库 (.dll) 组成。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="a9d0a-105">该服务是一个计算器服务，COM 客户端将对服务调用数学运算（加、减、乘和除）。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="a9d0a-106">客户端活动显示在消息框窗口中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9d0a-107">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a9d0a-108">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a9d0a-109">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="a9d0a-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a9d0a-110">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9d0a-111">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="a9d0a-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="a9d0a-112">该服务实现一个 `ICalculator` 协定，下面的代码示例对该协定进行了如下定义。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="a9d0a-113">示例演示三种使用标记的备选方法：</span><span class="sxs-lookup"><span data-stu-id="a9d0a-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="a9d0a-114">类型化协定 - 该协定在客户端计算机上注册为 COM 可见类型。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="a9d0a-115">WSDL 协定 - 该协定以 WSDL 文档的形式提供。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="a9d0a-116">元数据交换协定 - 该协定可在运行时从元数据交换 (MEX) 终结点进行检索。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="a9d0a-117">类型化协定</span><span class="sxs-lookup"><span data-stu-id="a9d0a-117">Typed Contract</span></span>  
 <span data-ttu-id="a9d0a-118">若要对类型化协定用法使用标记，必须向 COM 注册服务协定的经适当属性化的类型。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="a9d0a-119">首先，必须使用 " [svcutil.exe" 元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)生成客户端。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="a9d0a-120">在客户端目录中通过命令提示符运行以下命令可以生成该类型化代理。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="a9d0a-121">此类必须包括在项目中，并且应将项目配置为在编译时生成一个 COM 可见的已签名程序集。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="a9d0a-122">AssemblyInfo.cs 文件中应该包括下面的属性。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="a9d0a-123">生成项目以后，通过使用 `regasm` 注册 COM 可见类型，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="a9d0a-124">创建的程序集应该添加到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="a9d0a-125">虽然并不严格要求，但这样做可简化运行时定位程序集的过程。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="a9d0a-126">下面的命令将程序集添加到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="a9d0a-127">服务标记只要求进行类型注册，并不使用代理与服务通信。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="a9d0a-128">ComCalcClient.vbs 客户端应用程序使用 `GetObject` 函数来构造服务的代理，使用服务标记语法指定服务的地址、绑定和协定。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="a9d0a-129">标记使用的参数将会指定：</span><span class="sxs-lookup"><span data-stu-id="a9d0a-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="a9d0a-130">服务终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="a9d0a-131">客户端应该用来与该终结点连接的绑定。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="a9d0a-132">虽然可以在客户端配置文件中定义自定义绑定，但本例中使用了系统定义的 wsHttpBinding。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="a9d0a-133">自定义绑定在与 Cscript.exe 处于同一目录的 Cscript.exe.config 文件中进行定义，以便可以与 Windows 脚本主机一起使用。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="a9d0a-134">在终结点受支持的协定的类型。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="a9d0a-135">此类型是在上面生成并注册的类型。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="a9d0a-136">由于 Visual Basic 脚本不提供强类型 COM 环境，因此必须指定协定的标识符。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-136">Because Visual Basic script does not provide a strongly typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="a9d0a-137">此 GUID 是 CalcProxy.tlb 中的 `interfaceID`，可以通过使用 COM 工具（如 OLE/COM 对象查看器 (OleView.exe)）来查看。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="a9d0a-138">对于强类型化环境（如 Office VBA 或 Visual Basic 6.0），添加对类型库的显式引用，然后声明代理对象的类型可用于替代协定参数。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-138">For strongly typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="a9d0a-139">这样还可在客户端应用程序开发过程中提供 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="a9d0a-140">在用服务标记构造代理实例之后，客户端应用程序可以对此代理调用方法，这将生成调用相应服务操作的服务标记基础结构。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 运行示例时，操作响应将显示在 Windows 脚本宿主消息框窗口中。 这说明了使用类型化名字对象发出 COM 调用以便与 WCF 服务进行通信的 COM 客户端。 <span data-ttu-id="a9d0a-143">虽然在客户端应用程序中使用了 COM，但与服务的通信仅由 Web 服务调用组成。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="a9d0a-144">WSDL 协定</span><span class="sxs-lookup"><span data-stu-id="a9d0a-144">WSDL Contract</span></span>  
 <span data-ttu-id="a9d0a-145">使用具有 WSDL 协定的标记不需要注册任何客户端库，但必须通过带外机制（如使用浏览器访问服务的 WSDL 终结点）来检索服务的 WSDL 协定。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="a9d0a-146">标记之后可以在执行时访问该协定。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="a9d0a-147">ComCalcClient.vbs 客户端应用程序使用 `FileSystemObject` 访问保存在本地的 WSDL 文件，然后再次使用 `GetObject` 函数来构造服务的代理。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="a9d0a-148">标记使用的参数将会指定：</span><span class="sxs-lookup"><span data-stu-id="a9d0a-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="a9d0a-149">服务终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="a9d0a-150">客户端用于与该终结点连接的绑定和在其中定义该绑定的命名空间。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="a9d0a-151">在本例中，使用 `wsHttpBinding_ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="a9d0a-152">定义协定的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="a9d0a-153">在本例中是已从 serviceWsdl.xml 文件中读取的字符串。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="a9d0a-154">协定的名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-154">The name and namespace of the contract.</span></span> <span data-ttu-id="a9d0a-155">由于 WSDL 可能包含多个协定，因此需要此标识。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a9d0a-156">默认情况下，WCF 服务为使用的每个命名空间生成单独的 WSDL 文件。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="a9d0a-157">这些文件通过使用 WSDL 导入构造连接。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="a9d0a-158">由于标记需要单个 WSDL 定义，因此服务必须使用单个命名空间（如本示例中的演示），或者必须手动合并单独的文件。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="a9d0a-159">在用服务标记构造代理实例之后，客户端应用程序可以对此代理调用方法，这将生成调用相应服务操作的服务标记基础结构。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 运行示例时，操作响应将显示在 Windows 脚本宿主消息框窗口中。 <span data-ttu-id="a9d0a-161">这说明了使用带有 WSDL 协定的名字对象进行 COM 调用以便与 WCF 服务进行通信的 COM 客户端。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="a9d0a-162">元数据交换协定</span><span class="sxs-lookup"><span data-stu-id="a9d0a-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="a9d0a-163">和 WSDL 协定一样，使用具有 MEX 协定的标记不需要注册任何客户端。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="a9d0a-164">服务的协定通过内部使用元数据交换在执行时进行检索。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="a9d0a-165">ComCalcClient.vbs 客户端应用程序也使用 `GetObject` 函数来构造服务的代理。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="a9d0a-166">标记使用的参数将会指定：</span><span class="sxs-lookup"><span data-stu-id="a9d0a-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="a9d0a-167">服务元数据交换终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="a9d0a-168">服务终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="a9d0a-169">客户端用于与该终结点连接的绑定和在其中定义该绑定的命名空间。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="a9d0a-170">在本例中，使用 `wsHttpBinding_ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="a9d0a-171">协定的名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-171">The name and namespace of the contract.</span></span> <span data-ttu-id="a9d0a-172">由于 WSDL 可能包含多个协定，因此需要此标识。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="a9d0a-173">在用服务标记构造代理实例之后，客户端应用程序可以对此代理调用方法，这将生成调用相应服务操作的服务标记基础结构。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 运行示例时，操作响应将显示在 Windows 脚本宿主消息框窗口中。 <span data-ttu-id="a9d0a-175">这表明，COM 客户端使用名字对象和 MEX 协定进行 COM 调用，以便与 WCF 服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="a9d0a-176">设置和生成示例</span><span class="sxs-lookup"><span data-stu-id="a9d0a-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="a9d0a-177">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a9d0a-178">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a9d0a-179">在 Visual Studio 开发人员命令提示中，打开语言特定文件夹下的 \client\bin 文件夹。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a9d0a-180">如果使用的是 Windows Vista、Windows Server 2008、Windows 7 或 Windows Server 2008 R2，请确保使用管理员权限运行命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-180">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="a9d0a-181">键入以 `tlbexp.exe client.dll /out:CalcProxy.tlb` 将 dll 导出到 tlb 文件中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="a9d0a-182">预期会出现“Type library exporter warning”（类型库导出程序警告），但由于不需要泛型类型，因此这不是问题。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="a9d0a-183">键入 `regasm.exe /tlb:CalcProxy.tlb client.dll` 以向 COM 注册类型。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="a9d0a-184">预期会出现“Type library exporter warning”（类型库导出程序警告），但由于不需要泛型类型，因此这不是问题。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="a9d0a-185">键入以 `gacutil.exe /i client.dll` 将程序集添加到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a9d0a-186">在同一计算机上运行示例</span><span class="sxs-lookup"><span data-stu-id="a9d0a-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="a9d0a-187">通过键入以下地址来测试是否可以使用浏览器访问服务： `http://localhost/servicemodelsamples/service.svc` 。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="a9d0a-188">在响应中应显示确认页。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="a9d0a-189">运行 \client（在语言特定文件夹内）中的 ComCalcClient.vbs。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="a9d0a-190">客户端活动将显示在消息框窗口中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="a9d0a-191">如果客户端和服务无法进行通信，请参阅[WCF 示例的故障排除提示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a9d0a-192">跨计算机运行示例</span><span class="sxs-lookup"><span data-stu-id="a9d0a-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="a9d0a-193">在服务计算机上创建一个名为 ServiceModelSamples 的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="a9d0a-194">可以使用示例中附带的 Setupvroot.bat 脚本来创建磁盘目录和虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="a9d0a-195">从 %SystemDrive%\Inetpub\wwwroot\servicemodelsamples 中将服务程序文件复制到服务计算机上的 ServiceModelSamples 虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="a9d0a-196">确保在 \bin 目录中包括这些文件。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="a9d0a-197">将 \client 文件夹（在语言特定文件夹内）中的客户端脚本文件复制到客户端计算机上。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="a9d0a-198">在该脚本文件中，更改终结点定义的地址值以与服务的新地址相匹配。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="a9d0a-199">在地址中将任何对“localhost”的引用替换为一个完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="a9d0a-200">将 WSDL 文件复制到客户端计算机。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="a9d0a-201">在 WSDL 文件 serviceWsdl.xml 中，将地址中任何对“localhost”的引用替换为一个完全限定的域名。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="a9d0a-202">将 \client\bin\ 文件夹（在语言特定文件夹内）中的 Client.dll 库复制到客户端计算机上的一个目录中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="a9d0a-203">在命令提示符下，定位到客户端计算机上的目标目录。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="a9d0a-204">如果使用的是 Windows Vista 或 Windows Server 2008，请确保以管理员身份运行命令提示符。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-204">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="a9d0a-205">键入以 `tlbexp.exe client.dll /out:CalcProxy.tlb` 将 dll 导出到 tlb 文件中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="a9d0a-206">预期会出现“Type library exporter warning”（类型库导出程序警告），但由于不需要泛型类型，因此这不是问题。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="a9d0a-207">键入 `regasm.exe /tlb:CalcProxy.tlb client.dll` 以向 COM 注册类型。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="a9d0a-208">在运行命令之前，请确保已将路径设置为包含的文件夹 `regasm.exe` 。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="a9d0a-209">键入以 `gacutil.exe /i client.dll` 将程序集添加到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="a9d0a-210">在运行命令之前，请确保已将路径设置为包含的文件夹 `gacutil.exe` 。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="a9d0a-211">测试是否可使用浏览器从客户端计算机访问服务。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="a9d0a-212">在客户端计算机上，启动 ComCalcClient.vbs。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a9d0a-213">运行示例后进行清理</span><span class="sxs-lookup"><span data-stu-id="a9d0a-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="a9d0a-214">出于安全目的，请在示例结束后删除虚拟目录定义和在安装步骤中授予的权限。</span><span class="sxs-lookup"><span data-stu-id="a9d0a-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
