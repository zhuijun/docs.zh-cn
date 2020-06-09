---
title: 源格式化程序 (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 7b535a5090d3c7df59b7faada35fc324a77b5651
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594668"
---
# <a name="feed-formatter-json"></a>源格式化程序 (JSON)
本示例演示如何使用自定义 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 来序列化 JavaScript 对象符号 (JSON) 格式的 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 类的实例。  
  
## <a name="architecture-of-the-sample"></a>示例的体系结构  
 本示例实现一个从 `JsonFeedFormatter` 继承的名为 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的类。 `JsonFeedFormatter` 类依靠 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 来读写 JSON 格式的数据。 在内部，格式化程序使用名为 `JsonSyndicationFeed` 和 `JsonSyndicationItem` 的一组自定义数据协定类型来控制由序列化程序生成的 JSON 数据的格式。 对于最终用户，这些实现的详细信息是不可见的，从而可以针对标准 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 类进行调用。  
  
## <a name="writing-json-feeds"></a>编写 JSON 源  
 通过与 `JsonFeedFormatter` 一起使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>（在本示例中实现），可实现编写 JSON 源，如下面的示例代码所示。  
  
```csharp  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a>读取 JSON 源  
 使用 <xref:System.ServiceModel.Syndication.SyndicationFeed> 可以实现从 JSON 格式的数据流中获取 `JsonFeedFormatter`，如下面的代码所示。  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1. 确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。  
  
3. 若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。  
  
> [!IMPORTANT]
> 您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。 此示例位于以下目录：  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
