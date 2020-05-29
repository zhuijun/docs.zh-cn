---
title: 工作流发现示例
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1c6210472b594aec02bdf47f472a1a8b1823230c
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202064"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="6ac5d-102">工作流发现示例</span><span class="sxs-lookup"><span data-stu-id="6ac5d-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="6ac5d-103">此示例演示如何使工作流服务可发现，以及如何编写搜索特定服务的自定义代码活动。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6ac5d-104">演示</span><span class="sxs-lookup"><span data-stu-id="6ac5d-104">Demonstrates</span></span>  
 <span data-ttu-id="6ac5d-105">发现查找活动和工作流使用情况</span><span class="sxs-lookup"><span data-stu-id="6ac5d-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="6ac5d-106">讨论区</span><span class="sxs-lookup"><span data-stu-id="6ac5d-106">Discussion</span></span>  
 <span data-ttu-id="6ac5d-107">在示例的第一部分中，使用配置使工作流服务可发现。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="6ac5d-108">使用配置还可以正确地通过自定义元数据（如范围）应用服务。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="6ac5d-109">在客户端中，该示例使用了一个自定义代码活动，该活动使用发现来搜索与特定协定匹配的服务。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="6ac5d-110">该代码活动输出供发送活动在以后使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6ac5d-111">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="6ac5d-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6ac5d-112">此示例使用 HTTP 终结点，这些终结点必须具有正确的 URL Acl 才能运行（有关详细信息，请参阅[配置 HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md) ）。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="6ac5d-113">在具有提升权限的命令提示符下执行下面的命令应添加相应的 ACL。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="6ac5d-114">如果 shell 无法理解变量格式，请将您的域和用户名替换为以下参数。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
    `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`
  
> [!IMPORTANT]
> <span data-ttu-id="6ac5d-115">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6ac5d-116">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="6ac5d-116">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6ac5d-117">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="6ac5d-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6ac5d-118">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="6ac5d-118">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
