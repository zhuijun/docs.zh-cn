---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: dd2a0b67ec140aa2e6fe1abad8e85c0206abd8ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579016"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="f144b-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="f144b-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="f144b-103">WS-AT 协议服务在等待可变参与方对结果消息的响应时超时。</span><span class="sxs-lookup"><span data-stu-id="f144b-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="f144b-104">如果参与方返回，则事务结果可能不确定。</span><span class="sxs-lookup"><span data-stu-id="f144b-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f144b-105">描述</span><span class="sxs-lookup"><span data-stu-id="f144b-105">Description</span></span>  
 <span data-ttu-id="f144b-106">当可变参与方已决定提交或中止，但未在给定时间内响应提交或回滚请求时跟踪。</span><span class="sxs-lookup"><span data-stu-id="f144b-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f144b-107">疑难解答</span><span class="sxs-lookup"><span data-stu-id="f144b-107">Troubleshooting</span></span>  
 <span data-ttu-id="f144b-108">确保所有可变参与方都能在给定时间内响应。</span><span class="sxs-lookup"><span data-stu-id="f144b-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="f144b-109">默认时间为 180 秒。</span><span class="sxs-lookup"><span data-stu-id="f144b-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="f144b-110">如果此时间不够，请增加 WS-AT 的 `VolatileOutcomeDelay` 计时器策略。</span><span class="sxs-lookup"><span data-stu-id="f144b-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f144b-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f144b-111">See also</span></span>

- [<span data-ttu-id="f144b-112">跟踪</span><span class="sxs-lookup"><span data-stu-id="f144b-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="f144b-113">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="f144b-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f144b-114">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="f144b-114">Administration and Diagnostics</span></span>](../index.md)
