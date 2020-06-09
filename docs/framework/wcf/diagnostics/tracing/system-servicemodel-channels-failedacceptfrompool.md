---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 5bfa31d0eaf3b00017512eddc60bfa99eda619e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84582577"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="49e71-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="49e71-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="49e71-103">尝试重新使用已入池连接失败。</span><span class="sxs-lookup"><span data-stu-id="49e71-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="49e71-104">将在指定的超时期限内再次进行尝试。</span><span class="sxs-lookup"><span data-stu-id="49e71-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="49e71-105">描述</span><span class="sxs-lookup"><span data-stu-id="49e71-105">Description</span></span>  
 <span data-ttu-id="49e71-106">此信息跟踪指示尝试重新使用已入池连接时发生错误。</span><span class="sxs-lookup"><span data-stu-id="49e71-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="49e71-107">之所以发生此情况，原因在于已入池连接不兼容、未就绪或仍处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="49e71-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="49e71-108">在给定的超时范围内将进行重新使用其他已入池连接的更多尝试，如果未找到任何可使用的连接，则会创建新的连接。</span><span class="sxs-lookup"><span data-stu-id="49e71-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e71-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49e71-109">See also</span></span>

- [<span data-ttu-id="49e71-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="49e71-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="49e71-111">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="49e71-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="49e71-112">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="49e71-112">Administration and Diagnostics</span></span>](../index.md)
