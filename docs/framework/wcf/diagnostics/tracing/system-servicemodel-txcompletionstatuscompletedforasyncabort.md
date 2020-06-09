---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: 8371dba79573f480b264ed6185b8cf0098e3cb2a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576572"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="7708a-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="7708a-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="7708a-103">指定操作的指定事务由于异步中止而完成。</span><span class="sxs-lookup"><span data-stu-id="7708a-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7708a-104">描述</span><span class="sxs-lookup"><span data-stu-id="7708a-104">Description</span></span>  
 <span data-ttu-id="7708a-105">由于另一名参与者赞成中止，发生超时，或事务的参与者内部出现另一错误，因此当前事务被中止。</span><span class="sxs-lookup"><span data-stu-id="7708a-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7708a-106">疑难解答</span><span class="sxs-lookup"><span data-stu-id="7708a-106">Troubleshooting</span></span>  
 <span data-ttu-id="7708a-107">如果这是意外中止，请检查所有系统日志，以确定发生该中止的真正原因。</span><span class="sxs-lookup"><span data-stu-id="7708a-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7708a-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7708a-108">See also</span></span>

- [<span data-ttu-id="7708a-109">跟踪</span><span class="sxs-lookup"><span data-stu-id="7708a-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="7708a-110">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="7708a-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7708a-111">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="7708a-111">Administration and Diagnostics</span></span>](../index.md)
