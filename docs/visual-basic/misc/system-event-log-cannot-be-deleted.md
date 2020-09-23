---
title: 不能删除系统事件日志
ms.date: 07/20/2015
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
ms.openlocfilehash: 444c18f24f63c0c8e206ebf6fe3c77632df2fbd0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078666"
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="ca7b3-102">不能删除系统事件日志</span><span class="sxs-lookup"><span data-stu-id="ca7b3-102">System event log cannot be deleted</span></span>

<span data-ttu-id="ca7b3-103">试图删除系统事件日志（该日志是不能被删除的）。</span><span class="sxs-lookup"><span data-stu-id="ca7b3-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="ca7b3-104">系统日志跟踪系统事件（如系统启动和硬件故障）。</span><span class="sxs-lookup"><span data-stu-id="ca7b3-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca7b3-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="ca7b3-105">To correct this error</span></span>  
  
- <span data-ttu-id="ca7b3-106">请考虑让应用程序写入应用程序或自定义日志，而不是系统事件日志。</span><span class="sxs-lookup"><span data-stu-id="ca7b3-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
- <span data-ttu-id="ca7b3-107">请勿试图删除系统事件日志。</span><span class="sxs-lookup"><span data-stu-id="ca7b3-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7b3-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="ca7b3-108">See also</span></span>

- <span data-ttu-id="ca7b3-109">[管理事件日志](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ca7b3-109">[Administering Event Logs](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="ca7b3-110">[如何：创建和移除自定义事件日志](/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ca7b3-110">[How to: Create and Remove Custom Event Logs](/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span></span>
