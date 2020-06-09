---
title: MTOM 编码
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: cf048e1e6b2e2785accc1bde0336f07e3d84ae5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602526"
---
# <a name="mtom-encoding"></a><span data-ttu-id="73823-102">MTOM 编码</span><span class="sxs-lookup"><span data-stu-id="73823-102">MTOM Encoding</span></span>
<span data-ttu-id="73823-103">此示例演示如何将消息传输优化机制 (MTOM) 消息编码与 WSHttpBinding 一起使用。</span><span class="sxs-lookup"><span data-stu-id="73823-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="73823-104">MTOM 是一种机制，用来以原始字节形式传输包含 SOAP 消息的较大二进制附件，从而使所传输的消息较小。</span><span class="sxs-lookup"><span data-stu-id="73823-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="73823-105">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="73823-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="73823-106">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="73823-106">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="73823-107">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="73823-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="73823-108">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="73823-108">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="73823-109">默认情况下，WSHttpBinding 以正常文本 XML 形式发送和接收消息。</span><span class="sxs-lookup"><span data-stu-id="73823-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="73823-110">若要允许发送和接收 MTOM 消息，请在绑定的配置中设置 `messageEncoding` 属性 (Attribute)（如下面的示例代码中所示），或者使用 `MessageEncoding` 属性 (Property) 直接在绑定中进行设置。</span><span class="sxs-lookup"><span data-stu-id="73823-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="73823-111">服务或客户端现在可以发送和接收 MTOM 消息了。</span><span class="sxs-lookup"><span data-stu-id="73823-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="73823-112">MTOM 编码器可以优化字节和流的数组。</span><span class="sxs-lookup"><span data-stu-id="73823-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="73823-113">在下面的示例中，操作使用 `Stream` 参数，因此可以进行优化。</span><span class="sxs-lookup"><span data-stu-id="73823-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="73823-114">为该示例选择的协定会将二进制数据传输到服务，并将上载的字节数作为返回值接收。</span><span class="sxs-lookup"><span data-stu-id="73823-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="73823-115">在安装服务之后运行客户端时，服务会显示数字 1000，这表示收到了全部 1000 个字节。</span><span class="sxs-lookup"><span data-stu-id="73823-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="73823-116">剩下的输出列出了在各种负载情况下经过优化和未经优化的消息大小。</span><span class="sxs-lookup"><span data-stu-id="73823-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="73823-117">使用 MTOM 的目的在于优化对较大的二进制负载的传输。</span><span class="sxs-lookup"><span data-stu-id="73823-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="73823-118">对于较小的二进制负载来说，使用 MTOM 发送 SOAP 消息会产生显著的开销，但是，当这些负载增大到几千个字节时，该开销会变得微不足道。</span><span class="sxs-lookup"><span data-stu-id="73823-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="73823-119">原因在于，正常文本 XML 使用 Base64 对二进制数据进行编码，这要求每三个字节对应四个字符，从而使得数据的大小增加三分之一。</span><span class="sxs-lookup"><span data-stu-id="73823-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="73823-120">MTOM 能够以原始字节形式传输二进制数据，这会缩短编码/解码时间并生成较小的消息。</span><span class="sxs-lookup"><span data-stu-id="73823-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="73823-121">与当今的业务文档和数字照片相比，几千个字节的阈值是非常小的。</span><span class="sxs-lookup"><span data-stu-id="73823-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="73823-122">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="73823-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="73823-123">使用以下命令安装 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="73823-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="73823-124">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="73823-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="73823-125">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="73823-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="73823-126">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="73823-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
