---
title: DataContractSerializer 示例
description: 此示例演示 WCF 中的 DataContractSerializer，它为数据协定类执行常规序列化和反序列化服务。
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: c2f62c8926f09e2d4cdea1941909e7d8f59c43a0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244395"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="8e28b-103">DataContractSerializer 示例</span><span class="sxs-lookup"><span data-stu-id="8e28b-103">DataContractSerializer Sample</span></span>
<span data-ttu-id="8e28b-104">DataContractSerializer 示例演示为数据协定类执行常规序列化和反序列化服务的 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="8e28b-104">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="8e28b-105">该示例创建一个 `Record` 对象，将其序列化到内存流，然后将该内存流反序列化回另一个 `Record` 对象，以演示的用法 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="8e28b-105">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="8e28b-106">然后示例使用二进制编写器序列化 `Record` 对象以演示编写器如何影响序列化。</span><span class="sxs-lookup"><span data-stu-id="8e28b-106">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e28b-107">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="8e28b-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8e28b-108">在下面的示例代码中显示 `Record` 的数据协定：</span><span class="sxs-lookup"><span data-stu-id="8e28b-108">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="8e28b-109">该示例代码创建一个名为 `Record` 的 `record1` 对象，然后显示该对象。</span><span class="sxs-lookup"><span data-stu-id="8e28b-109">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="8e28b-110">然后示例使用 <xref:System.Runtime.Serialization.DataContractSerializer> 将 `record1` 序列化为内存流。</span><span class="sxs-lookup"><span data-stu-id="8e28b-110">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="8e28b-111">接下来，示例使用 <xref:System.Runtime.Serialization.DataContractSerializer> 将内存流反序列化回一个新的 `Record` 对象并显示它。</span><span class="sxs-lookup"><span data-stu-id="8e28b-111">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="8e28b-112">在默认情况下，`DataContractSerializer` 使用 XML 的文本表示形式将对象编码为流。</span><span class="sxs-lookup"><span data-stu-id="8e28b-112">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="8e28b-113">但是，您可以通过传入不同的编写器来影响 XML 的编码。</span><span class="sxs-lookup"><span data-stu-id="8e28b-113">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="8e28b-114">本示例通过调用 <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> 创建一个二进制编写器。</span><span class="sxs-lookup"><span data-stu-id="8e28b-114">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="8e28b-115">然后示例在调用 <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> 时将编写器和记录对象传递到序列化程序。</span><span class="sxs-lookup"><span data-stu-id="8e28b-115">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="8e28b-116">最后，示例刷新编写器并报告流的长度。</span><span class="sxs-lookup"><span data-stu-id="8e28b-116">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="8e28b-117">在运行该示例时，会显示原始记录和反序列化记录，接着是文本编码和二进制编码的长度之间的比较。</span><span class="sxs-lookup"><span data-stu-id="8e28b-117">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="8e28b-118">在客户端窗口中按 Enter 可以关闭客户端。</span><span class="sxs-lookup"><span data-stu-id="8e28b-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8e28b-119">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="8e28b-119">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8e28b-120">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="8e28b-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8e28b-121">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="8e28b-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8e28b-122">若要启动该示例，请通过在命令提示符处键入 client\bin\client.exe 启动客户端。</span><span class="sxs-lookup"><span data-stu-id="8e28b-122">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8e28b-123">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="8e28b-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8e28b-124">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="8e28b-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8e28b-125">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="8e28b-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8e28b-126">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="8e28b-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
