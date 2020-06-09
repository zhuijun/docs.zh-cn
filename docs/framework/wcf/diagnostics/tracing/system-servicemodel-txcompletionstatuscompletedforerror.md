---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 2bc71d18480fa19be66cbfa1687a7b63eb548309
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601447"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="194a8-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="194a8-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="194a8-103">由于未处理的执行异常，导致指定操作的指定事务处于完成状态。</span><span class="sxs-lookup"><span data-stu-id="194a8-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="194a8-104">描述</span><span class="sxs-lookup"><span data-stu-id="194a8-104">Description</span></span>  
 <span data-ttu-id="194a8-105">在尝试完成当前事务过程中发生错误时跟踪。</span><span class="sxs-lookup"><span data-stu-id="194a8-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="194a8-106">在将答复或错误发送给调用方之前，会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="194a8-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="194a8-107">疑难解答</span><span class="sxs-lookup"><span data-stu-id="194a8-107">Troubleshooting</span></span>  
 <span data-ttu-id="194a8-108">检查跟踪的消息，以查找异常消息和所有可操作的项。</span><span class="sxs-lookup"><span data-stu-id="194a8-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="194a8-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="194a8-109">See also</span></span>

- [<span data-ttu-id="194a8-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="194a8-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="194a8-111">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="194a8-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="194a8-112">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="194a8-112">Administration and Diagnostics</span></span>](../index.md)
