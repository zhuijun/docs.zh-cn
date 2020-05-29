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
# <a name="workflow-discovery-sample"></a>工作流发现示例
此示例演示如何使工作流服务可发现，以及如何编写搜索特定服务的自定义代码活动。  
  
## <a name="demonstrates"></a>演示  
 发现查找活动和工作流使用情况  
  
## <a name="discussion"></a>讨论区  
 在示例的第一部分中，使用配置使工作流服务可发现。 使用配置还可以正确地通过自定义元数据（如范围）应用服务。 在客户端中，该示例使用了一个自定义代码活动，该活动使用发现来搜索与特定协定匹配的服务。 该代码活动输出供发送活动在以后使用的 URI。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>设置、生成和运行示例  
  
1. 此示例使用 HTTP 终结点，这些终结点必须具有正确的 URL Acl 才能运行（有关详细信息，请参阅[配置 HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md) ）。 在具有提升权限的命令提示符下执行下面的命令应添加相应的 ACL。 如果 shell 无法理解变量格式，请将您的域和用户名替换为以下参数。  
  
    `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`
  
> [!IMPORTANT]
> 您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。 此示例位于以下目录：  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
