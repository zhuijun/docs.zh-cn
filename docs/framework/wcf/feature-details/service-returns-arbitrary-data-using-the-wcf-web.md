---
title: 如何：使用 WCF Web HTTP 编程模型创建返回任意数据的服务
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 9753fbc9b333cb7e89ddc8dff030cb1f62ede23b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600356"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="8e191-102">如何：使用 WCF Web HTTP 编程模型创建返回任意数据的服务</span><span class="sxs-lookup"><span data-stu-id="8e191-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="8e191-103">有时，开发人员必须完全控制从服务操作返回数据的方式。</span><span class="sxs-lookup"><span data-stu-id="8e191-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="8e191-104">当服务操作必须返回 WCF 不支持的格式的数据时，就会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="8e191-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="8e191-105">本主题讨论如何使用 WCF WEB HTTP 编程模型来创建此类服务。</span><span class="sxs-lookup"><span data-stu-id="8e191-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="8e191-106">此服务具有一个返回流的操作。</span><span class="sxs-lookup"><span data-stu-id="8e191-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="8e191-107">实现服务协定</span><span class="sxs-lookup"><span data-stu-id="8e191-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="8e191-108">定义服务协定。</span><span class="sxs-lookup"><span data-stu-id="8e191-108">Define the service contract.</span></span> <span data-ttu-id="8e191-109">该协定名为 `IImageServer`，具有一个名为 `GetImage` 的方法，该方法返回 <xref:System.IO.Stream>。</span><span class="sxs-lookup"><span data-stu-id="8e191-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="8e191-110">由于方法返回，因此 <xref:System.IO.Stream> WCF 假设操作对从服务操作返回的字节具有完全控制，并且不会对返回的数据应用任何格式设置。</span><span class="sxs-lookup"><span data-stu-id="8e191-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="8e191-111">实现服务协定。</span><span class="sxs-lookup"><span data-stu-id="8e191-111">Implement the service contract.</span></span> <span data-ttu-id="8e191-112">该协定只有一个操作：`GetImage`。</span><span class="sxs-lookup"><span data-stu-id="8e191-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="8e191-113">此方法生成一个位图，再以 .jpg 格式将其保存到 <xref:System.IO.MemoryStream>。</span><span class="sxs-lookup"><span data-stu-id="8e191-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="8e191-114">随后，操作将该流返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="8e191-114">The operation then returns that stream to the caller.</span></span>  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     <span data-ttu-id="8e191-115">请注意代码的倒数第二行：`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="8e191-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="8e191-116">这会将内容类型标头设置为 `"image/jpeg"` 。</span><span class="sxs-lookup"><span data-stu-id="8e191-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="8e191-117">虽然此示例演示如何返回 .jpg 文件，但可以对其进行修改，以任意格式返回所需的任意类型的数据。</span><span class="sxs-lookup"><span data-stu-id="8e191-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="8e191-118">该操作必须检索或生成数据，然后将它写入流。</span><span class="sxs-lookup"><span data-stu-id="8e191-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="8e191-119">承载服务</span><span class="sxs-lookup"><span data-stu-id="8e191-119">To host the service</span></span>  
  
1. <span data-ttu-id="8e191-120">创建用于承载服务的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="8e191-120">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="8e191-121">在 `Main` 方法中创建一个变量以保存服务的基址。</span><span class="sxs-lookup"><span data-stu-id="8e191-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="8e191-122">为服务创建一个 <xref:System.ServiceModel.ServiceHost> 实例，指定服务类和基址。</span><span class="sxs-lookup"><span data-stu-id="8e191-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="8e191-123">使用 <xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior> 添加一个终结点。</span><span class="sxs-lookup"><span data-stu-id="8e191-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="8e191-124">打开服务主机。</span><span class="sxs-lookup"><span data-stu-id="8e191-124">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="8e191-125">等待用户按 Enter 终止服务。</span><span class="sxs-lookup"><span data-stu-id="8e191-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="8e191-126">使用 Internet Explorer 调用原始服务</span><span class="sxs-lookup"><span data-stu-id="8e191-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="8e191-127">运行该服务，您应看到来自它的以下输出。</span><span class="sxs-lookup"><span data-stu-id="8e191-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="8e191-128">打开 Internet Explorer 并键入 `http://localhost:8000/Service/GetImage?width=50&height=40`，您应看到一个黄色矩形，有蓝色对角线穿过其中心。</span><span class="sxs-lookup"><span data-stu-id="8e191-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e191-129">示例</span><span class="sxs-lookup"><span data-stu-id="8e191-129">Example</span></span>  
 <span data-ttu-id="8e191-130">下面列出了此主题的完整代码。</span><span class="sxs-lookup"><span data-stu-id="8e191-130">The following is a complete listing of the code for this topic.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e191-131">编译代码</span><span class="sxs-lookup"><span data-stu-id="8e191-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="8e191-132">编译示例代码时，请引用 System.ServiceModel.dll 和 System.ServiceModel.Web.dll。</span><span class="sxs-lookup"><span data-stu-id="8e191-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e191-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e191-133">See also</span></span>

- [<span data-ttu-id="8e191-134">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="8e191-134">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
