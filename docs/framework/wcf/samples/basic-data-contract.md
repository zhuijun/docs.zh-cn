---
title: 基本数据协定
ms.date: 03/30/2017
helpviewer_keywords:
- Data Contract
ms.assetid: b124e9e0-cb73-4ae0-b9c3-e6cdf5eced98
ms.openlocfilehash: 66df6a1d7c2df17e79925490644891c0a536b1cd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585488"
---
# <a name="basic-data-contract"></a><span data-ttu-id="c3b05-102">基本数据协定</span><span class="sxs-lookup"><span data-stu-id="c3b05-102">Basic Data Contract</span></span>

<span data-ttu-id="c3b05-103">本示例演示如何实现数据协定。</span><span class="sxs-lookup"><span data-stu-id="c3b05-103">This sample demonstrates how to implement a data contract.</span></span> <span data-ttu-id="c3b05-104">数据协定允许您在服务中传入和传出结构化数据。</span><span class="sxs-lookup"><span data-stu-id="c3b05-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="c3b05-105">此示例基于[入门](getting-started-sample.md)，但使用复数而不是基本数值类型。</span><span class="sxs-lookup"><span data-stu-id="c3b05-105">This sample is based on the [Getting Started](getting-started-sample.md) but uses complex numbers instead of basic numeric types.</span></span>

<span data-ttu-id="c3b05-106">在本示例中，服务是由 Internet 信息服务 (IIS) 承载的，客户端是一个控制台应用程序 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="c3b05-106">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>

> [!NOTE]
> <span data-ttu-id="c3b05-107">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="c3b05-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="c3b05-108">此服务的服务协定使用复数，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="c3b05-108">The service contract for this service uses complex numbers, as shown in the following sample code.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);
    [OperationContract]
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);
    [OperationContract]
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);
    [OperationContract]
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);
}
```

 <span data-ttu-id="c3b05-109"><xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 属性已应用于 `ComplexNumber` 类的定义，指示可以在客户端和服务之间通过网络传递该类的哪些字段，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="c3b05-109">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes have been applied to the definition of the `ComplexNumber` class to indicate which fields of the class can be passed over the wire between the client and the service, as shown in the following sample code.</span></span>

```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public class ComplexNumber
{
    [DataMember]
    public double Real = 0.0D;
    [DataMember]
    public double Imaginary = 0.0D;

    public ComplexNumber(double real, double imaginary)
    {
        this.Real = real;
        this.Imaginary = imaginary;
    }
}
```

<span data-ttu-id="c3b05-110">服务实现计算并返回相应结果，接受并返回 `ComplexNumber` 类型的数字。</span><span class="sxs-lookup"><span data-stu-id="c3b05-110">The service implementation calculates and returns the appropriate result, accepting and returning numbers of the `ComplexNumber` type.</span></span>

```csharp
// This is the service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)
    {
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +
                                                      n2.Imaginary);
    }

    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)
    {
        return new ComplexNumber(n1.Real - n2.Real, n1.Imaginary -
                                                     n2.Imaginary);
    }
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)
    {
        double real1 = n1.Real * n2.Real;
        double imaginary1 = n1.Real * n2.Imaginary;
        double imaginary2 = n2.Real * n1.Imaginary;
        double real2 = n1.Imaginary * n2.Imaginary * -1;
        return new ComplexNumber(real1 + real2, imaginary1 +
                                                 imaginary2);
    }

    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)
    {
         ComplexNumber conjugate =
              new ComplexNumber(n2.Real, -1*n2.Imaginary);
         ComplexNumber numerator = Multiply(n1, conjugate);
         ComplexNumber denominator = Multiply(n2, conjugate);
         return new ComplexNumber(numerator.Real / denominator.Real,
                                               numerator.Imaginary);
    }
}
```

<span data-ttu-id="c3b05-111">客户端实现也使用复数。</span><span class="sxs-lookup"><span data-stu-id="c3b05-111">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="c3b05-112">服务协定和数据协定都是在源文件 generatedClient.cs 中定义的，该文件由服务元数据中的[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)生成。</span><span class="sxs-lookup"><span data-stu-id="c3b05-112">Both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span>

```csharp
// Create a client.
DataContractCalculatorClient client = new DataContractCalculatorClient();
// Call the Add service operation.
ComplexNumber value1 = new ComplexNumber()
                    {
                        Real = 1,
                        Imaginary = 2
                    };
ComplexNumber value2 = new ComplexNumber()
                    {
                        Real = 3,
                        Imaginary = 4
                    };
ComplexNumber result = proxy.Add(value1, value2);
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",
      value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,
      result.Real, result.Imaginary);
    …
}
```

<span data-ttu-id="c3b05-113">运行示例时，操作的请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="c3b05-113">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="c3b05-114">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="c3b05-114">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(1 + 2i, 3 + 4i) = 4 + 6i
Subtract(1 + 2i, 3 + 4i) = -2 + -2i
Multiply(2 + 3i, 4 + 7i) = -13 + 26i
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3b05-115">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="c3b05-115">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c3b05-116">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c3b05-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c3b05-117">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c3b05-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="c3b05-118">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c3b05-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3b05-119">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="c3b05-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3b05-120">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="c3b05-120">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c3b05-121">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="c3b05-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3b05-122">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="c3b05-122">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\Basic`
