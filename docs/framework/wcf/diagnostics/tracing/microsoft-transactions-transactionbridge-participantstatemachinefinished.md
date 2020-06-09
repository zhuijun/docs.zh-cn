---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 0652b3b76c155431b68c5ee0dc8f83977f9845a5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594356"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="0d870-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="0d870-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="0d870-103">参与者列入的状态机进入已完成状态。</span><span class="sxs-lookup"><span data-stu-id="0d870-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0d870-104">描述</span><span class="sxs-lookup"><span data-stu-id="0d870-104">Description</span></span>  
 <span data-ttu-id="0d870-105">从属参与者列入已完成 2pc 处理时跟踪。</span><span class="sxs-lookup"><span data-stu-id="0d870-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="0d870-106">列入的结果可以是“已提交”或“已中止”。</span><span class="sxs-lookup"><span data-stu-id="0d870-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="0d870-107">此外，还会跟踪是否有参与者在“准备”过程中投票“只读”。</span><span class="sxs-lookup"><span data-stu-id="0d870-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d870-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d870-108">See also</span></span>

- [<span data-ttu-id="0d870-109">跟踪</span><span class="sxs-lookup"><span data-stu-id="0d870-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="0d870-110">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="0d870-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0d870-111">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="0d870-111">Administration and Diagnostics</span></span>](../index.md)
