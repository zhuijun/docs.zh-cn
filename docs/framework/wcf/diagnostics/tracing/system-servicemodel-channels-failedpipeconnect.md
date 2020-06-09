---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: 790a15e5401850f2767cb06f5f321ad80c674f2b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582408"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="90478-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="90478-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="90478-103">尝试连接到指定的管道终结点失败。</span><span class="sxs-lookup"><span data-stu-id="90478-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="90478-104">将在指定的超时期限内再次进行尝试。</span><span class="sxs-lookup"><span data-stu-id="90478-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="90478-105">描述</span><span class="sxs-lookup"><span data-stu-id="90478-105">Description</span></span>  
 <span data-ttu-id="90478-106">此信息跟踪指示未能连接到指定的管道终结点。</span><span class="sxs-lookup"><span data-stu-id="90478-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="90478-107">如果未找到指定的管道终结点或指定的管道终结点正忙，则可能会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="90478-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="90478-108">将进行更多的尝试（两次尝试之间的时间较短），直到尝试成功或 OpenTimeout 过期。</span><span class="sxs-lookup"><span data-stu-id="90478-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90478-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90478-109">See also</span></span>

- [<span data-ttu-id="90478-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="90478-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="90478-111">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="90478-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="90478-112">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="90478-112">Administration and Diagnostics</span></span>](../index.md)
