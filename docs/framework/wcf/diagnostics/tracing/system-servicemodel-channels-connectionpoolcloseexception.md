---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 0a312d192546655dc327667c00f4f2bbc0c15fdb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602034"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="733f1-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="733f1-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="733f1-103">关闭此连接池中的连接时发生异常。</span><span class="sxs-lookup"><span data-stu-id="733f1-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="733f1-104">描述</span><span class="sxs-lookup"><span data-stu-id="733f1-104">Description</span></span>  
 <span data-ttu-id="733f1-105">此错误级别跟踪指示关闭 Windows Communication Foundation （WCF）的连接池功能所使用的连接池时出错。</span><span class="sxs-lookup"><span data-stu-id="733f1-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="733f1-106">一种可能的原因是一个池连接或一组池连接在 CloseTimeout 内未成功关闭。</span><span class="sxs-lookup"><span data-stu-id="733f1-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="733f1-107">当引发此异常时，将中止该池内所有剩余的未关闭连接，并放弃其他池内的未关闭连接。</span><span class="sxs-lookup"><span data-stu-id="733f1-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733f1-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="733f1-108">See also</span></span>

- [<span data-ttu-id="733f1-109">跟踪</span><span class="sxs-lookup"><span data-stu-id="733f1-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="733f1-110">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="733f1-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="733f1-111">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="733f1-111">Administration and Diagnostics</span></span>](../index.md)
