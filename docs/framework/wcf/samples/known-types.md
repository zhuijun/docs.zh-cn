---
title: 已知类型
ms.date: 03/30/2017
ms.assetid: 88d83720-ca38-4b2c-86a6-f149ed1d89ec
ms.openlocfilehash: dae271384905df890b2f42196d6e0aadad66be6f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591834"
---
# <a name="known-types"></a><span data-ttu-id="ea373-102">已知类型</span><span class="sxs-lookup"><span data-stu-id="ea373-102">Known Types</span></span>
<span data-ttu-id="ea373-103">此示例演示如何在数据协定中指定有关派生类型的信息。</span><span class="sxs-lookup"><span data-stu-id="ea373-103">This sample demonstrates how to specify information about derived types in a data contract.</span></span> <span data-ttu-id="ea373-104">数据协定允许您在服务中传入和传出结构化数据。</span><span class="sxs-lookup"><span data-stu-id="ea373-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="ea373-105">在面向对象的编程中，可以用从另一个类型继承的类型来代替原始类型。</span><span class="sxs-lookup"><span data-stu-id="ea373-105">In object-oriented programming, a type that inherits from another type can be used in place of the original type.</span></span> <span data-ttu-id="ea373-106">在面向服务的编程中，传递的是架构（而不是类型），因此，类型之间的关系将不保留。</span><span class="sxs-lookup"><span data-stu-id="ea373-106">In service-oriented programming, schemas rather than types are communicated and therefore, the relationship between types is not preserved.</span></span> <span data-ttu-id="ea373-107"><xref:System.Runtime.Serialization.KnownTypeAttribute> 属性允许在数据协定中包括有关派生类型的信息。</span><span class="sxs-lookup"><span data-stu-id="ea373-107">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute allows information about derived types to be included in the data contract.</span></span> <span data-ttu-id="ea373-108">如果不使用此机制，则不能在应当使用基类型的情况下发送或接收派生类型。</span><span class="sxs-lookup"><span data-stu-id="ea373-108">If this mechanism is not used, a derived type cannot be sent or received where a base type is expected.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea373-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="ea373-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ea373-110">此服务的服务协定使用复数，如下面的示例代码中所示。</span><span class="sxs-lookup"><span data-stu-id="ea373-110">The service contract for the service uses complex numbers, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="ea373-111"><xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 应用于 `ComplexNumber` 类，这将指示在客户端和服务之间可以传递类的哪些字段。</span><span class="sxs-lookup"><span data-stu-id="ea373-111">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> is applied to the `ComplexNumber` class to indicate which fields of the class can be passed between the client and the service.</span></span> <span data-ttu-id="ea373-112">可以用 `ComplexNumberWithMagnitude` 派生类来代替 `ComplexNumber`。</span><span class="sxs-lookup"><span data-stu-id="ea373-112">The derived `ComplexNumberWithMagnitude` class can be used in place of `ComplexNumber`.</span></span> <span data-ttu-id="ea373-113"><xref:System.Runtime.Serialization.KnownTypeAttribute> 类型的 `ComplexNumber` 属性说明了这一点。</span><span class="sxs-lookup"><span data-stu-id="ea373-113">The <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on the `ComplexNumber` type indicates this.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
[KnownType(typeof(ComplexNumberWithMagnitude))]  
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
  
 <span data-ttu-id="ea373-114">`ComplexNumberWithMagnitude` 类型派生自 `ComplexNumber`，但是额外添加了一个数据成员 `Magnitude`。</span><span class="sxs-lookup"><span data-stu-id="ea373-114">The `ComplexNumberWithMagnitude` type derives from `ComplexNumber` but adds an additional data member, `Magnitude`.</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumberWithMagnitude : ComplexNumber  
{  
    public ComplexNumberWithMagnitude(double real, double imaginary) :  
        base(real, imaginary) { }  
  
    [DataMember]  
    public double Magnitude  
    {  
        get { return Math.Sqrt(Imaginary*Imaginary  + Real*Real); }  
        set { throw new NotImplementedException(); }  
    }  
}  
```  
  
 <span data-ttu-id="ea373-115">为了演示已知的类型功能，此服务的实现方式是 `ComplexNumberWithMagnitude` 仅为加法和减法返回。</span><span class="sxs-lookup"><span data-stu-id="ea373-115">To demonstrate the known types feature, the service is implemented in such a way that it returns a `ComplexNumberWithMagnitude` only for addition and subtraction.</span></span> <span data-ttu-id="ea373-116">（由于 `ComplexNumber` 属性的存在，即使协定中指定了 `KnownTypeAttribute`，这也是允许的。）</span><span class="sxs-lookup"><span data-stu-id="ea373-116">(Even though the contract specifies `ComplexNumber`, this is allowed because of the `KnownTypeAttribute` attribute).</span></span> <span data-ttu-id="ea373-117">乘法和除法仍返回基 `ComplexNumber` 类型。</span><span class="sxs-lookup"><span data-stu-id="ea373-117">Multiplication and division still return the base `ComplexNumber` type.</span></span>  
  
```csharp
public class DataContractCalculatorService : IDataContractCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real + n2.Real,  
                                      n1.Imaginary + n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        //Return the derived type.  
        return new ComplexNumberWithMagnitude(n1.Real - n2.Real,
                                 n1.Imaginary - n2.Imaginary);  
    }  
  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        //Return the base type.  
        return new ComplexNumber(real1 + real2, imaginary1 +
                                                  imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
        ComplexNumber conjugate = new ComplexNumber(n2.Real,
                                     -1*n2.Imaginary);  
        ComplexNumber numerator = Multiply(n1, conjugate);  
        ComplexNumber denominator = Multiply(n2, conjugate);  
        //Return the base type.  
        return new ComplexNumber(numerator.Real / denominator.Real,  
                                             numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="ea373-118">在客户端上，服务协定和数据协定都是在源文件 generatedClient.cs 中定义的，该文件由服务元数据中的[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)生成。</span><span class="sxs-lookup"><span data-stu-id="ea373-118">On the client, both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="ea373-119">由于在服务的数据协定中指定了 <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性，因此在使用服务时，客户端既能够接收 `ComplexNumber` 类又能够接收 `ComplexNumberWithMagnitude` 类。</span><span class="sxs-lookup"><span data-stu-id="ea373-119">Because the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute is specified in the service's data contract, the client is able to receive both the `ComplexNumber` and `ComplexNumberWithMagnitude` classes when using the service.</span></span> <span data-ttu-id="ea373-120">客户端检测它是否获得了 `ComplexNumberWithMagnitude` 并生成相应的输出：</span><span class="sxs-lookup"><span data-stu-id="ea373-120">The client detects whether it got a `ComplexNumberWithMagnitude` and generate the appropriate output:</span></span>  
  
```csharp
// Create a client  
DataContractCalculatorClient client =
    new DataContractCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber() { real = 1, imaginary = 2 };  
ComplexNumber value2 = new ComplexNumber() { real = 3, imaginary = 4 };  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.real, value1.imaginary, value2.real, value2.imaginary,  
    result.real, result.imaginary);  
if (result is ComplexNumberWithMagnitude)  
{  
    Console.WriteLine("Magnitude: {0}",
        ((ComplexNumberWithMagnitude)result).Magnitude);  
}  
else  
{  
    Console.WriteLine("No magnitude was sent from the service");  
}  
```  
  
 <span data-ttu-id="ea373-121">运行示例时，操作的请求和响应将显示在客户端控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="ea373-121">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="ea373-122">请注意，对加法和减法列显了数量级，而对乘法和除法却没有列显，这是由服务的实现方式确定的。</span><span class="sxs-lookup"><span data-stu-id="ea373-122">Note that a magnitude is printed for addition and subtraction but not for multiplication and division because of the way the service was implemented.</span></span> <span data-ttu-id="ea373-123">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="ea373-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Magnitude: 7.21110255092798  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Magnitude: 2.82842712474619  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
No magnitude was sent from the service  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
No magnitude was sent from the service  
  
    Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ea373-124">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="ea373-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ea373-125">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ea373-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ea373-126">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ea373-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ea373-127">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ea373-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ea373-128">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="ea373-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ea373-129">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="ea373-129">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ea373-130">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="ea373-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ea373-131">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="ea373-131">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\KnownTypes`  
