---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: d341953b8e12b14e6a3fe8a477c16a1b3a4454ae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580432"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="afdf1-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="afdf1-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="afdf1-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="afdf1-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="afdf1-104">描述</span><span class="sxs-lookup"><span data-stu-id="afdf1-104">Description</span></span>  
 <span data-ttu-id="afdf1-105">已再次关闭消息。</span><span class="sxs-lookup"><span data-stu-id="afdf1-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="afdf1-106">消息只应关闭一次。</span><span class="sxs-lookup"><span data-stu-id="afdf1-106">A message should be closed only once.</span></span> <span data-ttu-id="afdf1-107">如果用户扩展代码发出此跟踪，则指示用户扩展代码正在关闭一个已经关闭的消息。</span><span class="sxs-lookup"><span data-stu-id="afdf1-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="afdf1-108">如果通过产品代码发出此跟踪，则指示用户扩展代码可能正在过早地关闭消息。</span><span class="sxs-lookup"><span data-stu-id="afdf1-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdf1-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="afdf1-109">See also</span></span>

- [<span data-ttu-id="afdf1-110">跟踪</span><span class="sxs-lookup"><span data-stu-id="afdf1-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="afdf1-111">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="afdf1-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="afdf1-112">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="afdf1-112">Administration and Diagnostics</span></span>](../index.md)
