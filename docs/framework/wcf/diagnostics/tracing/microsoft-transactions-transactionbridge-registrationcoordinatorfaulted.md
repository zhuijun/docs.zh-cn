---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: ad9d82162313e46626e5e2fa6f4ef99bf0139162
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599641"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="e392e-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="e392e-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="e392e-103">WS-AT 协议服务从其协调程序接收到错误作为对注册消息的响应。</span><span class="sxs-lookup"><span data-stu-id="e392e-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e392e-104">描述</span><span class="sxs-lookup"><span data-stu-id="e392e-104">Description</span></span>  
 <span data-ttu-id="e392e-105">在本地 TransactionManager 由于所返回的错误而无法向其上级 TransactionManager 注册时跟踪。</span><span class="sxs-lookup"><span data-stu-id="e392e-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e392e-106">疑难解答</span><span class="sxs-lookup"><span data-stu-id="e392e-106">Troubleshooting</span></span>  
 <span data-ttu-id="e392e-107">检查返回的错误的跟踪消息。</span><span class="sxs-lookup"><span data-stu-id="e392e-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e392e-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e392e-108">See also</span></span>

- [<span data-ttu-id="e392e-109">跟踪</span><span class="sxs-lookup"><span data-stu-id="e392e-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="e392e-110">使用跟踪来排除应用程序故障</span><span class="sxs-lookup"><span data-stu-id="e392e-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e392e-111">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="e392e-111">Administration and Diagnostics</span></span>](../index.md)
