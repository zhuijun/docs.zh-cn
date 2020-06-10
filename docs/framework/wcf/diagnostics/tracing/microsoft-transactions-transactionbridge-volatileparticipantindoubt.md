---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: ab1c2c8afe3a66536810a614cc6deac12519cb9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599628"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="b8f44-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="b8f44-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="b8f44-103">协议服务从无法识别的可变参与者接收到已准备或重播消息。</span><span class="sxs-lookup"><span data-stu-id="b8f44-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="b8f44-104">已向参与者返回错误，声明事务的结果不确定。</span><span class="sxs-lookup"><span data-stu-id="b8f44-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b8f44-105">描述</span><span class="sxs-lookup"><span data-stu-id="b8f44-105">Description</span></span>  
 <span data-ttu-id="b8f44-106">在本地事务管理器从它已经忘记的可变参与者接收到已准备或重播消息时进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="b8f44-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b8f44-107">疑难解答</span><span class="sxs-lookup"><span data-stu-id="b8f44-107">Troubleshooting</span></span>  
 <span data-ttu-id="b8f44-108">调查来自可变参与者的最新消息的可能原因。</span><span class="sxs-lookup"><span data-stu-id="b8f44-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f44-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b8f44-109">See also</span></span>

- [<span data-ttu-id="b8f44-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="b8f44-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="b8f44-111">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="b8f44-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b8f44-112">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="b8f44-112">Administration and Diagnostics</span></span>](../index.md)
