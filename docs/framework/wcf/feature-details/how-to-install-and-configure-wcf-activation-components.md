---
title: 如何：安装和配置 WCF 激活组件
description: 了解如何在 Windows Vista 上设置 Windows 进程激活服务 () 来托管不能通过 HTTP 进行通信的 WCF 服务。
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 085a69421f0aa7b763bd2222820ced4b4a7e1c81
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557861"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="3c905-103">如何：安装和配置 WCF 激活组件</span><span class="sxs-lookup"><span data-stu-id="3c905-103">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="3c905-104">本主题介绍设置 Windows 进程激活服务所需的步骤，该服务在 Windows Vista 上 (也称为) ，以承载 Windows Communication Foundation (不通过 HTTP 网络协议进行通信的 WCF) 服务。</span><span class="sxs-lookup"><span data-stu-id="3c905-104">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="3c905-105">下面的部分略述此配置的步骤：</span><span class="sxs-lookup"><span data-stu-id="3c905-105">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="3c905-106">安装 (或确认 WCF 激活组件) 的安装。</span><span class="sxs-lookup"><span data-stu-id="3c905-106">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="3c905-107">配置 WAS 以支持非 HTTP 协议。</span><span class="sxs-lookup"><span data-stu-id="3c905-107">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="3c905-108">以下过程将 Windows Vista 配置为进行 TCP 激活。</span><span class="sxs-lookup"><span data-stu-id="3c905-108">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="3c905-109">安装和配置 WAS 之后，请参阅 [中的如何：在 WAS 中承载 Wcf 服务](how-to-host-a-wcf-service-in-was.md) ，了解如何创建 wcf 服务，该服务公开了采用 WAS 的非 HTTP 终结点。</span><span class="sxs-lookup"><span data-stu-id="3c905-109">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="3c905-110">安装 WCF 非 HTTP 激活组件</span><span class="sxs-lookup"><span data-stu-id="3c905-110">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="3c905-111">单击\*\*\*\*“开始”按钮，然后单击\*\*\*\*“控制面板”。</span><span class="sxs-lookup"><span data-stu-id="3c905-111">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="3c905-112">单击“程序”\*\*\*\*，然后单击“程序和功能”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c905-112">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="3c905-113">在 " **任务** " 菜单上，单击 " **打开或关闭 Windows 功能**"。</span><span class="sxs-lookup"><span data-stu-id="3c905-113">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="3c905-114">找到 WinFX 节点，选择它，然后将其展开。</span><span class="sxs-lookup"><span data-stu-id="3c905-114">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="3c905-115">选择 " **WCF 非 Http 激活组件** " 框并保存设置。</span><span class="sxs-lookup"><span data-stu-id="3c905-115">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="3c905-116">配置 WAS 以支持 TCP 激活</span><span class="sxs-lookup"><span data-stu-id="3c905-116">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="3c905-117">若要支持 net.tcp 激活，必须首先将默认的网站绑定到一个 net.tcp 端口。</span><span class="sxs-lookup"><span data-stu-id="3c905-117">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="3c905-118">可以通过使用随 IIS 7.0 管理工具集一起安装 Appcmd.exe 来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="3c905-118">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="3c905-119">在管理员级别命令提示符窗口中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="3c905-119">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="3c905-120">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="3c905-120">This command is a single line of text.</span></span> <span data-ttu-id="3c905-121">此命令将 net.tcp 网站绑定添加到以任何主机名侦听 TCP 端口 808 的默认网站。</span><span class="sxs-lookup"><span data-stu-id="3c905-121">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="3c905-122">尽管网站内的所有应用程序共享一个公共 net.tcp 绑定，但是每个应用程序可以单独启用 net.tcp 支持。</span><span class="sxs-lookup"><span data-stu-id="3c905-122">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="3c905-123">若要启用应用程序的 net.tcp，请从管理员级别命令提示符运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="3c905-123">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="3c905-124">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="3c905-124">This command is a single line of text.</span></span> <span data-ttu-id="3c905-125">此命令允许 \<*WCF Application*> 使用和访问/应用程序 `http://localhost/<WCF Application>` `net.tcp://localhost/<WCF Application>` 。</span><span class="sxs-lookup"><span data-stu-id="3c905-125">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="3c905-126">移除为此示例添加的 net.tcp 网站绑定。</span><span class="sxs-lookup"><span data-stu-id="3c905-126">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="3c905-127">为方便起见，在位于示例目录中名为 RemoveNetTcpSiteBinding.cmd 的批处理文件中实现以下两个步骤。</span><span class="sxs-lookup"><span data-stu-id="3c905-127">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="3c905-128">通过在管理员级别命令提示符窗口中运行以下命令，从启用的协议列表移除 net.tcp。</span><span class="sxs-lookup"><span data-stu-id="3c905-128">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="3c905-129">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="3c905-129">This command is a single line of text.</span></span>

    2. <span data-ttu-id="3c905-130">通过在提升的命令提示符窗口中运行以下命令移除 net.tcp 网站绑定：</span><span class="sxs-lookup"><span data-stu-id="3c905-130">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="3c905-131">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="3c905-131">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="3c905-132">从启用的协议列表中移除 net.tcp</span><span class="sxs-lookup"><span data-stu-id="3c905-132">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="3c905-133">若要从启用的协议列表中移除 net.tcp，请在管理员级别命令提示符窗口中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="3c905-133">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="3c905-134">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="3c905-134">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="3c905-135">移除 net.tcp 网站绑定</span><span class="sxs-lookup"><span data-stu-id="3c905-135">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="3c905-136">要移除 net.tcp 网站绑定，请在管理员级别命令提示窗口中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="3c905-136">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="3c905-137">此命令是单行文本。</span><span class="sxs-lookup"><span data-stu-id="3c905-137">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c905-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="3c905-138">See also</span></span>

- [<span data-ttu-id="3c905-139">TCP 激活</span><span class="sxs-lookup"><span data-stu-id="3c905-139">TCP Activation</span></span>](../samples/tcp-activation.md)
- [<span data-ttu-id="3c905-140">MSMQ 激活</span><span class="sxs-lookup"><span data-stu-id="3c905-140">MSMQ Activation</span></span>](../samples/msmq-activation.md)
- [<span data-ttu-id="3c905-141">NamedPipe 激活</span><span class="sxs-lookup"><span data-stu-id="3c905-141">NamedPipe Activation</span></span>](../samples/namedpipe-activation.md)
- <span data-ttu-id="3c905-142">[Windows Server App Fabric 承载功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3c905-142">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
