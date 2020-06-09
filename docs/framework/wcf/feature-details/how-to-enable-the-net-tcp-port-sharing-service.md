---
title: 如何：启用 Net.TCP 端口共享服务
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 8b305b98d620636328866bce848411f395053485
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593123"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="0b329-102">如何：启用 Net.TCP 端口共享服务</span><span class="sxs-lookup"><span data-stu-id="0b329-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="0b329-103">Windows Communication Foundation （WCF）使用称为 Net.tcp 端口共享服务的 Windows 服务，以便在多个进程之间共享 TCP 端口。</span><span class="sxs-lookup"><span data-stu-id="0b329-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="0b329-104">此服务作为 WCF 的一部分进行安装，但默认情况下不启用该服务作为安全预防措施，因此在首次使用之前必须手动启用。</span><span class="sxs-lookup"><span data-stu-id="0b329-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="0b329-105">本主题描述如何使用 Microsoft 管理控制台 (MMC) 管理单元配置 Net TCP 端口共享服务。</span><span class="sxs-lookup"><span data-stu-id="0b329-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="0b329-106">启用 Net.tcp 端口共享服务并手动启动后，请参阅[如何：配置 WCF 服务以使用端口共享](how-to-configure-a-wcf-service-to-use-port-sharing.md)，了解有关如何将服务配置为使用此服务的信息。</span><span class="sxs-lookup"><span data-stu-id="0b329-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="0b329-107">有关使用 net.tcp：//端口共享的示例，请参阅[Net.tcp 端口共享示例](../samples/net-tcp-port-sharing-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0b329-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="0b329-108">使用 MMC 启用 Net.TCP 端口共享服务</span><span class="sxs-lookup"><span data-stu-id="0b329-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="0b329-109">从 "开始" 菜单中，打开 "命令提示符" 窗口并键入 `services.msc` 或打开 "运行"，然后 `services.msc` 在 "打开" 框中键入来打开服务管理控制台。</span><span class="sxs-lookup"><span data-stu-id="0b329-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="0b329-110">在服务列表的 "**名称**" 列中，右键单击**Net.tcp 端口共享服务**，然后从菜单中选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="0b329-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="0b329-111">若要启用该服务的手动启动，请在 "**属性**" 窗口中选择 "**常规**" 选项卡，并在 "**启动类型**" 框中选择 "手动"，然后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="0b329-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="0b329-112">若要启动该服务，请在 "服务状态" 区域中，单击 "**开始**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="0b329-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="0b329-113">现在，服务状态区域应显示为“已启动”。</span><span class="sxs-lookup"><span data-stu-id="0b329-113">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="0b329-114">若要返回到服务列表，请单击 **"确定**"，然后退出 MMC 控制台。</span><span class="sxs-lookup"><span data-stu-id="0b329-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b329-115">示例</span><span class="sxs-lookup"><span data-stu-id="0b329-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b329-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b329-116">See also</span></span>

- [<span data-ttu-id="0b329-117">Net.TCP 端口共享</span><span class="sxs-lookup"><span data-stu-id="0b329-117">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="0b329-118">配置 Net.TCP 端口共享服务</span><span class="sxs-lookup"><span data-stu-id="0b329-118">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
