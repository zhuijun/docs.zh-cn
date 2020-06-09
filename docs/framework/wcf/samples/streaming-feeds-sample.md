---
title: 流处理源示例
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 551a97f3cc54915a831fc28eca6ae0ff23101e0b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589781"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="e6bdb-102">流处理源示例</span><span class="sxs-lookup"><span data-stu-id="e6bdb-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="e6bdb-103">此示例演示如何管理包含大量项的联合源。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="e6bdb-104">在服务器上，此示例演示如何延迟在源中创建各个 <xref:System.ServiceModel.Syndication.SyndicationItem> 对象，一直到项就要被写入网络流之前。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="e6bdb-105">在客户端上，该示例演示如何使用自定义联合源格式化程序读取网络流中的各个项，以使当前读取的源永远不会完全缓冲到内存中。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="e6bdb-106">为了最充分地演示联合 API 的流处理功能，此示例使用了一个似乎不可能的方案，在这个方案中，服务器公开一个包含无数个项的源。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="e6bdb-107">在这种情况下，服务器继续在源中生成新的项，一直到它认为客户端已从源中读取指定数目（默认为 10）的项为止。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="e6bdb-108">为简单起见，客户端和服务器是在同一个进程中实现的，并且使用一个共享 `ItemCounter` 对象跟踪客户端生成的项数。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="e6bdb-109">`ItemCounter` 类型存在的唯一目的是为了使示例方案能够完全终止，它并不是所演示的模式的核心元素。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="e6bdb-110">此演示利用了 Visual c # 迭代器（使用 `yield return` 关键字构造）。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="e6bdb-111">有关迭代器的详细信息，请参阅 MSDN 上的 "使用迭代器" 主题。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="e6bdb-112">服务</span><span class="sxs-lookup"><span data-stu-id="e6bdb-112">Service</span></span>  
 <span data-ttu-id="e6bdb-113">服务实现包含一个操作的基本 <xref:System.ServiceModel.Web.WebGetAttribute> 协定，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="e6bdb-114">服务通过使用 `ItemGenerator` 类创建一个可能无限的 <xref:System.ServiceModel.Syndication.SyndicationItem> 实例流（使用迭代器）来实现此协定，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```csharp
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="e6bdb-115">当服务实现创建源时，使用 `ItemGenerator.GenerateItems()` 的输出，而不是使用缓冲的项集合。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```csharp
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="e6bdb-116">因此，项流永远不会完全缓冲到内存中。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="e6bdb-117">你可以通过在方法中的语句上设置断点来观察此行为 `yield return` `ItemGenerator.GenerateItems()` ，并注意在服务返回了方法的结果后首次遇到此断点 `StreamedFeed()` 。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="e6bdb-118">客户端</span><span class="sxs-lookup"><span data-stu-id="e6bdb-118">Client</span></span>  
 <span data-ttu-id="e6bdb-119">此示例中的客户端使用自定义 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 实现，该实现延迟各个项在源中的具体化，而不是将它们缓冲到内存中。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="e6bdb-120">自定义 `StreamedAtom10FeedFormatter` 实例的使用如下所示。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="e6bdb-121">通常，在从网络中读取源的全部内容并将内容缓冲到内存中之前，并不会返回对 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> 的调用。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="e6bdb-122">但是，`StreamedAtom10FeedFormatter` 对象重写了 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> 以返回迭代器，而不是返回缓冲的集合，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```csharp  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="e6bdb-123">因此，在遍历 `ReadItems()` 结果的客户端应用程序准备好使用每个项之前，并不会从网络中读取每个项。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="e6bdb-124">您可以通过在中的语句上设置断点来观察此行为 `yield return` `StreamedAtom10FeedFormatter.DelayReadItems()` ，并注意在调用完成后第一次遇到该断点 `ReadFrom()` 。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="e6bdb-125">下面的说明演示如何生成并运行示例。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="e6bdb-126">请注意，尽管服务器在客户端读取 10 个项后停止生成项，但输出显示客户端读取的项数远远超过 10 个。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="e6bdb-127">这是因为示例使用的网络绑定以 4 KB 段传输数据。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="e6bdb-128">因此，客户端在有机会读取一个项之前，已收到 4KB 的项数据。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="e6bdb-129">这是正常的行为（以合理大小的段发送经过流处理的 HTTP 数据可以提高性能）。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e6bdb-130">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="e6bdb-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e6bdb-131">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e6bdb-132">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e6bdb-133">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e6bdb-134">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e6bdb-135">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="e6bdb-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e6bdb-136">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="e6bdb-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6bdb-137">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="e6bdb-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="e6bdb-138">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6bdb-138">See also</span></span>

- [<span data-ttu-id="e6bdb-139">独立诊断源</span><span class="sxs-lookup"><span data-stu-id="e6bdb-139">Stand-Alone Diagnostics Feed</span></span>](stand-alone-diagnostics-feed-sample.md)
