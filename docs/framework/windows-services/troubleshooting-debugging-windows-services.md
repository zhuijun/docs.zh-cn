---
title: 疑难解答：调试 Windows 服务
description: 开始调试 Windows 服务。 调试 Windows 服务应用程序时，服务和 Windows 服务管理器会交互。
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
author: ghogen
ms.openlocfilehash: 935f5dcbd369ba5d723cc0e947ba708afdd590ea
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925535"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="7ccff-104">疑难解答：调试 Windows 服务</span><span class="sxs-lookup"><span data-stu-id="7ccff-104">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="7ccff-105">在调试 Windows 服务应用程序时，服务和 Windows 服务管理器  交互。</span><span class="sxs-lookup"><span data-stu-id="7ccff-105">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="7ccff-106">Service Manager 通过调用 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法来启动服务，然后等待 30 秒以便 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法返回。</span><span class="sxs-lookup"><span data-stu-id="7ccff-106">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="7ccff-107">如果此时该方法未返回，则管理器将显示服务无法启动的错误。</span><span class="sxs-lookup"><span data-stu-id="7ccff-107">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="7ccff-108">按[如何：调试 Windows 服务应用程序](how-to-debug-windows-service-applications.md)中所述调试 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法时，必须注意这 30 秒的时间。</span><span class="sxs-lookup"><span data-stu-id="7ccff-108">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="7ccff-109">如果在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中放置断点并且未在 30 秒内逐步执行该断点，则管理器将不会启动该服务。</span><span class="sxs-lookup"><span data-stu-id="7ccff-109">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ccff-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ccff-110">See also</span></span>

- [<span data-ttu-id="7ccff-111">如何：调试 Windows 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="7ccff-111">How to: Debug Windows Service Applications</span></span>](how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="7ccff-112">Windows 服务应用程序介绍</span><span class="sxs-lookup"><span data-stu-id="7ccff-112">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
