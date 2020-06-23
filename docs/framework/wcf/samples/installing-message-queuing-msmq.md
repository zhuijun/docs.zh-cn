---
title: 安装“消息队列 (MSMQ)”
description: 了解如何将消息队列4.0 和消息队列3.0 作为一次性安装过程的一部分，与 WFC 示例一起使用。
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 0d0cb87b40b1cb11eb7692c2fa1e890ec815b13d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244460"
---
# <a name="installing-message-queuing-msmq"></a><span data-ttu-id="ef15f-103">安装“消息队列 (MSMQ)”</span><span class="sxs-lookup"><span data-stu-id="ef15f-103">Installing Message Queuing (MSMQ)</span></span>
<span data-ttu-id="ef15f-104">以下过程介绍如何安装“消息队列 4.0”和“消息队列 3.0”。</span><span class="sxs-lookup"><span data-stu-id="ef15f-104">The following procedures show how to install Message Queuing 4.0 and Message Queuing 3.0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef15f-105">在 Windows XP 和 Windows Server 2003 中，消息队列4.0 不可用。</span><span class="sxs-lookup"><span data-stu-id="ef15f-105">Message Queuing 4.0 is not available in Windows XP and Windows Server 2003.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a><span data-ttu-id="ef15f-106">在 Windows Server 2008 or Windows Server 2008 R2 上安装消息队列 4.0</span><span class="sxs-lookup"><span data-stu-id="ef15f-106">To install Message Queuing 4.0 on Windows Server 2008 or Windows Server 2008 R2</span></span>  
  
1. <span data-ttu-id="ef15f-107">在服务器管理器中，单击 "**功能**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-107">In Server Manager, click **Features**.</span></span>  
  
2. <span data-ttu-id="ef15f-108">在右侧窗格中的 "**功能摘要**" 下，单击 "**添加功能**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-108">In the right-hand pane under **Features Summary**, click **Add Features**.</span></span>  
  
3. <span data-ttu-id="ef15f-109">在生成的窗口中，展开 "**消息队列**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-109">In the resulting window, expand **Message Queuing**.</span></span>  
  
4. <span data-ttu-id="ef15f-110">展开 "**消息队列服务**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-110">Expand **Message Queuing Services**.</span></span>  
  
5. <span data-ttu-id="ef15f-111">单击 "**目录服务集成**" （对于加入域的计算机），然后单击 " **HTTP 支持**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-111">Click **Directory Services Integration** (for computers joined to a Domain), then click **HTTP Support**.</span></span>  
  
6. <span data-ttu-id="ef15f-112">单击 "**下一步**"，然后单击 "**安装**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-112">Click **Next**,then click **Install**.</span></span>  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a><span data-ttu-id="ef15f-113">在 Windows 7 或 Windows Vista 上安装消息队列 4.0</span><span class="sxs-lookup"><span data-stu-id="ef15f-113">To install Message Queuing 4.0 on Windows 7 or Windows Vista</span></span>  
  
1. <span data-ttu-id="ef15f-114">打开“控制面板”</span><span class="sxs-lookup"><span data-stu-id="ef15f-114">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="ef15f-115">单击 "**程序**"，然后在 "**程序和功能**" 下，单击 "**打开和关闭 Windows 功能**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-115">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
3. <span data-ttu-id="ef15f-116">展开“Microsoft Message Queue (MSMQ) 服务器”，展开“Microsoft Message Queue (MSMQ) 服务器核心”，然后选中对应于以下要安装的“消息队列”功能的复选框：</span><span class="sxs-lookup"><span data-stu-id="ef15f-116">Expand Microsoft Message Queue (MSMQ) Server, expand Microsoft Message Queue (MSMQ) Server Core, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
    - <span data-ttu-id="ef15f-117">MSMQ Active Directory 域服务集成（用于加入域的计算机）。</span><span class="sxs-lookup"><span data-stu-id="ef15f-117">MSMQ Active Directory Domain Services Integration (for computers joined to a Domain).</span></span>  
  
    - <span data-ttu-id="ef15f-118">MSMQ HTTP 支持。</span><span class="sxs-lookup"><span data-stu-id="ef15f-118">MSMQ HTTP Support.</span></span>  
  
4. <span data-ttu-id="ef15f-119">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="ef15f-119">Click **OK**.</span></span>  
  
5. <span data-ttu-id="ef15f-120">如果系统提示您重新启动计算机，请单击 **"确定"** 以完成安装。</span><span class="sxs-lookup"><span data-stu-id="ef15f-120">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="ef15f-121">在 Windows XP 和 Windows Server 2003 上安装消息队列 3.0</span><span class="sxs-lookup"><span data-stu-id="ef15f-121">To install Message Queuing 3.0 on Windows XP and Windows Server 2003</span></span>  
  
1. <span data-ttu-id="ef15f-122">打开“控制面板”</span><span class="sxs-lookup"><span data-stu-id="ef15f-122">Open **Control Panel**.</span></span>  
  
2. <span data-ttu-id="ef15f-123">单击 "**添加删除程序**"，然后单击 "**添加 Windows 组件**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-123">Click **Add Remove Programs** and then click **Add Windows Components**.</span></span>  
  
3. <span data-ttu-id="ef15f-124">选择 "消息队列"，然后单击 "**详细信息**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-124">Select Message Queuing and click **Details**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ef15f-125">如果运行的是 Windows Server 2003，请选择 "应用程序服务器" 以访问消息队列。</span><span class="sxs-lookup"><span data-stu-id="ef15f-125">If you are running Windows Server 2003, select Application Server to access Message Queuing.</span></span>  
  
4. <span data-ttu-id="ef15f-126">确保在详细信息页上已选中“MSMQ HTTP 支持”选项。</span><span class="sxs-lookup"><span data-stu-id="ef15f-126">Ensure that the option MSMQ HTTP Support is selected on the details page.</span></span>  
  
5. <span data-ttu-id="ef15f-127">单击 **"确定"** 退出详细信息页，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="ef15f-127">Click **OK** to exit the details page, and then click **Next**.</span></span> <span data-ttu-id="ef15f-128">完成安装。</span><span class="sxs-lookup"><span data-stu-id="ef15f-128">Complete the installation.</span></span>  
  
6. <span data-ttu-id="ef15f-129">如果系统提示您重新启动计算机，请单击 **"确定"** 以完成安装。</span><span class="sxs-lookup"><span data-stu-id="ef15f-129">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef15f-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="ef15f-130">See also</span></span>

- [<span data-ttu-id="ef15f-131">设置说明</span><span class="sxs-lookup"><span data-stu-id="ef15f-131">Set-Up Instructions</span></span>](set-up-instructions.md)
