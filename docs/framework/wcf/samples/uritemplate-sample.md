---
title: UriTemplate 示例
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: fb956882ae653f584026fefb20e261c90010ca9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591054"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="71a2d-102">UriTemplate 示例</span><span class="sxs-lookup"><span data-stu-id="71a2d-102">UriTemplate Sample</span></span>
<span data-ttu-id="71a2d-103"><xref:System.UriTemplate> 类提供了用于处理共享公共结构的 URI 组的方法。</span><span class="sxs-lookup"><span data-stu-id="71a2d-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="71a2d-104">此示例演示与 `UriTemplate` 相关的以下关键概念：</span><span class="sxs-lookup"><span data-stu-id="71a2d-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="71a2d-105">创建模板的语法。</span><span class="sxs-lookup"><span data-stu-id="71a2d-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="71a2d-106">使用 `UriTemplate` 和 <xref:System.UriTemplate.BindByName%2A> 实例化 <xref:System.UriTemplate.BindByPosition%2A> 中的 URI。</span><span class="sxs-lookup"><span data-stu-id="71a2d-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="71a2d-107">作为 <xref:System.UriTemplateTable.Match%2A> 和 `BindByName` 的反向操作的 `BindByPosition`。</span><span class="sxs-lookup"><span data-stu-id="71a2d-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="71a2d-108">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="71a2d-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="71a2d-109">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="71a2d-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="71a2d-110">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="71a2d-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="71a2d-111">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="71a2d-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="71a2d-112">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="71a2d-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="71a2d-113">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="71a2d-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71a2d-114">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="71a2d-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="71a2d-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71a2d-115">See also</span></span>

- [<span data-ttu-id="71a2d-116">UriTemplate 表</span><span class="sxs-lookup"><span data-stu-id="71a2d-116">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="71a2d-117">UriTemplate 表调度程序</span><span class="sxs-lookup"><span data-stu-id="71a2d-117">UriTemplate Table Dispatcher</span></span>](uritemplate-table-dispatcher-sample.md)
