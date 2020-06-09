---
title: XMLSerializer 错误
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: ce5aa6d2c579d4776f9505ae694768203e48eecf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584059"
---
# <a name="xmlserializer-faults"></a><span data-ttu-id="ab989-102">XMLSerializer 错误</span><span class="sxs-lookup"><span data-stu-id="ab989-102">XmlSerializer Faults</span></span>
<span data-ttu-id="ab989-103"><xref:System.Xml.Serialization.XmlSerializer> 错误协定示例演示如何使用 <xref:System.Xml.Serialization.XmlSerializer> 将错误信息从服务传达到客户端。</span><span class="sxs-lookup"><span data-stu-id="ab989-103">The <xref:System.Xml.Serialization.XmlSerializer> fault contract sample demonstrates how to communicate error information from a service to a client using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="ab989-104">该示例基于[入门](getting-started-sample.md)，并向服务添加了一些附加代码，以将内部异常转换为错误。</span><span class="sxs-lookup"><span data-stu-id="ab989-104">The sample is based on the [Getting Started](getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="ab989-105">客户端试图执行除数为零的运算以在服务上强制产生错误情况。</span><span class="sxs-lookup"><span data-stu-id="ab989-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab989-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="ab989-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ab989-107">已将计算器协定修改为包括 <xref:System.ServiceModel.FaultContractAttribute>，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="ab989-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span> <span data-ttu-id="ab989-108">另外，<xref:System.ServiceModel.XmlSerializerFormatAttribute> 还用于使用 <xref:System.Xml.Serialization.XmlSerializer> 启用序列化</span><span class="sxs-lookup"><span data-stu-id="ab989-108">Also, the <xref:System.ServiceModel.XmlSerializerFormatAttribute> is used to enable serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="ab989-109">对于此属性 (Attribute)，<xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> 属性 (Property) 设置为 `true`，它指示序列化程序使用 <xref:System.Xml.Serialization.XmlSerializer> 读取和写入错误。</span><span class="sxs-lookup"><span data-stu-id="ab989-109">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> property is set to `true` on this attribute, which instructs the serializer to use the <xref:System.Xml.Serialization.XmlSerializer> for reading and writing faults.</span></span>  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
  
    [OperationContract]  
    int Subtract(int n1, int n2);  
  
    [OperationContract]  
    int Multiply(int n1, int n2);  
  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="ab989-110">为客户端代理生成代码时，必须将/UseSerializerForFaults 标志应用于 " **/UseSerializerForFaults** "[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="ab989-110">When generating code for the client proxy, you must apply the **/UseSerializerForFaults** flag to [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab989-111">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="ab989-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ab989-112">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ab989-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ab989-113">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ab989-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ab989-114">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ab989-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ab989-115">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="ab989-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ab989-116">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="ab989-116">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ab989-117">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="ab989-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab989-118">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="ab989-118">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a><span data-ttu-id="ab989-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab989-119">See also</span></span>

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
