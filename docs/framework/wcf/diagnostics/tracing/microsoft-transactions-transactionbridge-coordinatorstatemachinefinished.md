---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 3b9a3703e49c3932f62fcfb6994c9028b074bbe8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594408"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="efd56-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="efd56-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="efd56-103">用于协调器登记的状态机已进入已完成状态。</span><span class="sxs-lookup"><span data-stu-id="efd56-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="efd56-104">描述</span><span class="sxs-lookup"><span data-stu-id="efd56-104">Description</span></span>  
 <span data-ttu-id="efd56-105">本地事务管理器认为高级协调器登记已完成 2pc 处理时跟踪。</span><span class="sxs-lookup"><span data-stu-id="efd56-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="efd56-106">登记的结果可以是“已提交”、“已中止”或“已忘记”。</span><span class="sxs-lookup"><span data-stu-id="efd56-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="efd56-107">本地事务管理器在“准备”过程中对“只读”投票时也会进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="efd56-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efd56-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="efd56-108">See also</span></span>

- [<span data-ttu-id="efd56-109">跟踪</span><span class="sxs-lookup"><span data-stu-id="efd56-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="efd56-110">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="efd56-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="efd56-111">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="efd56-111">Administration and Diagnostics</span></span>](../index.md)
