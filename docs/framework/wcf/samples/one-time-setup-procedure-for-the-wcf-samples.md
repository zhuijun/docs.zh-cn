---
title: Windows Communication Foundation 示例的一次性安装过程
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: bf25ea4734bad007fa3ac19df0664932d981519c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548112"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a><span data-ttu-id="d734d-102">Windows Communication Foundation 示例的一次性安装过程</span><span class="sxs-lookup"><span data-stu-id="d734d-102">One-Time Setup Procedure for the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="d734d-103">大多数 Windows Communication Foundation (WCF) 示例承载在 Internet Information Services (IIS) 中，并从公共虚拟目录中运行。</span><span class="sxs-lookup"><span data-stu-id="d734d-103">Most of the Windows Communication Foundation (WCF) samples are hosted in Internet Information Services (IIS) and run from a common virtual directory.</span></span> <span data-ttu-id="d734d-104">此一次性安装过程在磁盘上创建一个文件夹;它还向 IIS 添加一个名为 **ServiceModelSamples**的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="d734d-104">This one-time setup procedure creates a folder on the disk; it also adds a virtual directory to IIS named **ServiceModelSamples**.</span></span>

<span data-ttu-id="d734d-105">**ServiceModelSamples**虚拟目录用于生成和运行使用 IIS 承载的服务的所有示例。</span><span class="sxs-lookup"><span data-stu-id="d734d-105">The **ServiceModelSamples** virtual directory is used for building and running all samples that use an IIS-hosted service.</span></span> <span data-ttu-id="d734d-106">这是运行示例所需的唯一虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="d734d-106">This is the only virtual directory that is required to run the samples.</span></span> <span data-ttu-id="d734d-107">绑定示例将替换以前在此虚拟目录部署的所有服务；只有最近生成的示例将在此虚拟目录中部署并可用。</span><span class="sxs-lookup"><span data-stu-id="d734d-107">Building a sample will replace any previously deployed service at this virtual directory; only the most recently built sample will be deployed and available in this virtual directory.</span></span>

> [!NOTE]
> <span data-ttu-id="d734d-108">必须在本地管理员帐户下运行所有命令。</span><span class="sxs-lookup"><span data-stu-id="d734d-108">You must run all commands under a local administrator account.</span></span> <span data-ttu-id="d734d-109">如果你使用的是 Windows 7、Windows Vista 或 Windows Server 2008 R2，则还必须使用提升的权限运行命令提示符。</span><span class="sxs-lookup"><span data-stu-id="d734d-109">If you are using Windows 7, Windows Vista, or Windows Server 2008 R2, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="d734d-110">为此，请右键单击 "命令提示符" 图标，然后单击 "以 **管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="d734d-110">To do so, right-click the command prompt icon, and then click **Run as administrator**.</span></span> <span data-ttu-id="d734d-111">本主题中的所有命令都必须在具有合适路径设置的命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="d734d-111">All commands in this topic must be run in a command prompt that has the appropriate path settings.</span></span>  <span data-ttu-id="d734d-112">确保这一点的最简单方法是使用 Visual Studio 命令提示。</span><span class="sxs-lookup"><span data-stu-id="d734d-112">The easiest way to ensure this is by using the Visual Studio Command Prompt.</span></span> <span data-ttu-id="d734d-113">若要打开此提示，请单击 " **开始**"，选择 " **所有程序**"，向下滚动到 " **visual studio 2010**"，选择 **Visual Studio Tools**，右键单击 " \*\*visual studio 命令提示符" (2010) \*\*"，然后单击" 以 **管理员身份运行**"。</span><span class="sxs-lookup"><span data-stu-id="d734d-113">To open this prompt, click **Start**, select **All Programs**, scroll down to **Visual Studio 2010**, select **Visual Studio Tools**, right-click **Visual Studio Command Prompt (2010)**, and then click **Run as administrator**.</span></span> <span data-ttu-id="d734d-114">如果安装了 Visual Studio 学习版，但此命令提示不可用，则必须向系统路径添加“C:\Windows\Microsoft.Net\Framework\v4.0”。</span><span class="sxs-lookup"><span data-stu-id="d734d-114">If you have one of the Visual Studio Express editions installed, this command prompt is not available, and you will have to add "C:\Windows\Microsoft.Net\Framework\v4.0" to the system path.</span></span>

### <a name="one-time-setup-procedure-for-wcf-samples"></a><span data-ttu-id="d734d-115">WCF 示例的一次性安装过程</span><span class="sxs-lookup"><span data-stu-id="d734d-115">One-time setup procedure for WCF samples</span></span>

1. <span data-ttu-id="d734d-116">确保已设置 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="d734d-116">Ensure that ASP.NET is set up.</span></span> <span data-ttu-id="d734d-117">有关如何设置 ASP.NET 的详细信息，请参阅 [Internet 信息服务托管说明](internet-information-service-hosting-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="d734d-117">For more information about how to set up ASP.NET, see [Internet Information Service Hosting Instructions](internet-information-service-hosting-instructions.md).</span></span>

2. <span data-ttu-id="d734d-118">确保安装 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="d734d-118">Ensure that .NET Framework 4 is installed.</span></span> <span data-ttu-id="d734d-119">在以下目录中搜索 (或更高版本) ： **\Windows\Microsoft.NET\Framework**</span><span class="sxs-lookup"><span data-stu-id="d734d-119">Search the following directory for v4.0 (or later): **\Windows\Microsoft.NET\Framework**</span></span>

3. <span data-ttu-id="d734d-120">请确保已安装 Visual Studio 2012 或更高版本，或者你的操作系统为 Windows Server 2008 SP2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="d734d-120">Ensure you have Visual Studio 2012 or later installed, or your operating system is Windows Server 2008 SP2 or later.</span></span>

4. <span data-ttu-id="d734d-121">运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d734d-121">Run the following commands.</span></span> <span data-ttu-id="d734d-122">有关这些命令必须运行的详细信息，请参阅 [IIS 托管服务失败](/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="d734d-122">For more information about why these commands must be run, see [IIS Hosted Service Fails](/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90)).</span></span>

    > [!WARNING]
    > <span data-ttu-id="d734d-123">如果重新安装 IIS，则需要再次运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d734d-123">If IIS is reinstalled, the following commands will need to be run again.</span></span>

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > <span data-ttu-id="d734d-124">运行该命令 `aspnet_regiis –i –enable` 会使默认应用池使用 .NET Framework 4 运行，这可能会为同一台计算机上的其他应用程序产生不兼容问题。</span><span class="sxs-lookup"><span data-stu-id="d734d-124">Running the command `aspnet_regiis –i –enable` will make the Default App Pool run using .NET Framework 4, which may produce incompatibility issues for other applications on the same computer.</span></span>

5. <span data-ttu-id="d734d-125">按照 [防火墙说明](firewall-instructions.md) 启用示例使用的端口。</span><span class="sxs-lookup"><span data-stu-id="d734d-125">Follow the [Firewall Instructions](firewall-instructions.md) for enabling the ports used by the samples.</span></span>

6. <span data-ttu-id="d734d-126">检查以下默认目录： \<InstallDrive> ：**\ WF_WCF_Samples**。</span><span class="sxs-lookup"><span data-stu-id="d734d-126">Check for the following default directory: \<InstallDrive>:**\WF_WCF_Samples**.</span></span> <span data-ttu-id="d734d-127">如果之前已安装这些示例，则该目录为默认目录。</span><span class="sxs-lookup"><span data-stu-id="d734d-127">If the samples were previously installed, this is the default directory.</span></span>

7. <span data-ttu-id="d734d-128">如果未安装这些示例，请从 [ (WCF) Windows Communication Foundation 安装它们，并 Windows Workflow Foundation () 的 WF .NET Framework 示例](https://www.microsoft.com/download/details.aspx?id=21459)。</span><span class="sxs-lookup"><span data-stu-id="d734d-128">If the samples are not installed, install them from [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

8. <span data-ttu-id="d734d-129">安装示例后，请参阅： \<InstallDrive> ：\*\*\ WF_WCF_Samples \wcf\setup \\ \*\*</span><span class="sxs-lookup"><span data-stu-id="d734d-129">After installing the samples, go to : \<InstallDrive>:**\WF_WCF_Samples\WCF\Setup\\**</span></span>

9. <span data-ttu-id="d734d-130">运行 **Setupvroot.bat** 的批处理文件。</span><span class="sxs-lookup"><span data-stu-id="d734d-130">Run the **Setupvroot.bat** batch file.</span></span> <span data-ttu-id="d734d-131">将执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="d734d-131">The following steps are performed:</span></span>

    - <span data-ttu-id="d734d-132">将在 IIS 中创建一个名为 ServiceModelSamples 的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="d734d-132">A virtual directory is created in IIS named ServiceModelSamples.</span></span>

    - <span data-ttu-id="d734d-133">新建名为 %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples 和 %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin 的磁盘目录。</span><span class="sxs-lookup"><span data-stu-id="d734d-133">New disk directories are created named %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples and %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin.</span></span>

    <span data-ttu-id="d734d-134">如果想要手动设置这些目录，请参阅 [虚拟目录设置说明](virtual-directory-setup-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="d734d-134">If you prefer to set up these directories manually, see the [Virtual Directory Setup Instructions](virtual-directory-setup-instructions.md).</span></span> <span data-ttu-id="d734d-135">若要恢复此步骤中所进行的所有更改，请在使用完示例后运行一次 cleanupvroot.bat。</span><span class="sxs-lookup"><span data-stu-id="d734d-135">To revert all changes done in this step, run cleanupvroot.bat after you finish using the samples.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d734d-136">除非运行 cleanupvroot.bat，否则此过程只能在计算机上执行一次。</span><span class="sxs-lookup"><span data-stu-id="d734d-136">This procedure must be performed only once on a computer, unless cleanupvroot.bat is run.</span></span>

10. <span data-ttu-id="d734d-137">您必须向在其下生成示例的帐户和 Network Service 用户授予对 %SystemDrive%\inetpub\wwwroot 的修改权限。</span><span class="sxs-lookup"><span data-stu-id="d734d-137">You must grant permission to modify for %SystemDrive%\inetpub\wwwroot to the account under which you are building the samples and the Network Service user.</span></span> <span data-ttu-id="d734d-138">在生成过程中，某些 Web 承载的示例可能会尝试将已编译的二进制文件复制到上述位置，如果你没有设置相应权限，则生成过程将中断。</span><span class="sxs-lookup"><span data-stu-id="d734d-138">While building, some Web-hosted samples might attempt to copy the compiled binaries to the previously mentioned location, and if you have not set the appropriate permissions, the build will break.</span></span> <span data-ttu-id="d734d-139">或者，你可以保留这些权限，并以管理员身份运行 SDK 命令提示或 Visual Studio 命令提示符 (2012) ，或在 Visual Studio 2012 中生成示例，同时以管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="d734d-139">Alternatively, you can leave the permissions as they are and run the SDK command prompt or Visual Studio Command Prompt (2012) as Administrator, or build the samples in Visual Studio 2012, also run as Administrator.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d734d-140">如果未完成此步骤，IIS 承载的所有示例都将在生成时失败。</span><span class="sxs-lookup"><span data-stu-id="d734d-140">If this step is not completed, all IIS-hosted samples will fail while building.</span></span> <span data-ttu-id="d734d-141">确保正确设置权限，或者同时以管理员身份运行 SDK 命令提示和 Visual Studio 命令提示 (2012)。</span><span class="sxs-lookup"><span data-stu-id="d734d-141">Ensure that you set the permissions correctly, or run both the SDK command prompt and Visual Studio Command Prompt (2012) as Administrator.</span></span>

11. <span data-ttu-id="d734d-142">在计算机上创建一个 C:\logs 目录；某些示例可能需要此目录。</span><span class="sxs-lookup"><span data-stu-id="d734d-142">Create a C:\logs directory on the computer; some samples might be expecting it.</span></span> <span data-ttu-id="d734d-143">确保向合适的帐户授予了对此文件夹的写访问权限。</span><span class="sxs-lookup"><span data-stu-id="d734d-143">Make sure that the appropriate account has write access granted to this folder.</span></span> <span data-ttu-id="d734d-144">对于 Windows 7、Windows Vista 和 Windows Server 2008 R2，此帐户为 **Network Service**。</span><span class="sxs-lookup"><span data-stu-id="d734d-144">For Windows 7, Windows Vista, and Windows Server 2008 R2, this account is **Network Service**.</span></span> <span data-ttu-id="d734d-145">对于 Windows Server 2008，该帐户为 NT Authority\Network Service。</span><span class="sxs-lookup"><span data-stu-id="d734d-145">For  Windows Server 2008, the account is NT Authority\Network Service.</span></span> <span data-ttu-id="d734d-146">对于 Windows XP 和 Windows Server 2003，帐户为 ASPNET。</span><span class="sxs-lookup"><span data-stu-id="d734d-146">For Windows XP and Windows Server 2003, the account is ASPNET.</span></span>

12. <span data-ttu-id="d734d-147">运行 Setupcerttool.bat 文件。</span><span class="sxs-lookup"><span data-stu-id="d734d-147">Run the Setupcerttool.bat file.</span></span> <span data-ttu-id="d734d-148">此文件位于  \<InstallPath> \ WF_WCF_Samples \wcf\setup\ 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="d734d-148">This file is located in the  \<InstallPath>\WF_WCF_Samples\WCF\Setup\  folder.</span></span>  <span data-ttu-id="d734d-149">此脚本将执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="d734d-149">This script will perform the following tasks:</span></span>

    - <span data-ttu-id="d734d-150">生成 FindPrivateKey 工具。</span><span class="sxs-lookup"><span data-stu-id="d734d-150">Build the FindPrivateKey tool.</span></span>

    - <span data-ttu-id="d734d-151">创建一个名为 %ProgramFiles%\ServiceModelSampleTools 的目录。</span><span class="sxs-lookup"><span data-stu-id="d734d-151">Create a directory called %ProgramFiles%\ServiceModelSampleTools.</span></span>

    - <span data-ttu-id="d734d-152">将新的 FindPrivateKey 工具复制到此目录。</span><span class="sxs-lookup"><span data-stu-id="d734d-152">Copy the new FindPrivateKey tool to this directory.</span></span>

    <span data-ttu-id="d734d-153">使用证书且承载于 IIS 中的示例需要使用此工具。</span><span class="sxs-lookup"><span data-stu-id="d734d-153">This tool is required by samples that use certificates and are hosted in IIS.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d734d-154">出于安全方面的考虑，请记住在完成这些示例后，通过运行名为 Cleanupvroot.bat 的批处理文件来移除虚拟目录定义和在上面的设置步骤中授予的权限。</span><span class="sxs-lookup"><span data-stu-id="d734d-154">For security purposes, remember to remove the virtual directory definition and permissions granted in the setup steps above by running the batch file named Cleanupvroot.bat after you are finished with the samples.</span></span>

13. <span data-ttu-id="d734d-155">自承载（不承载于 IIS 中）的示例需要在计算机上注册要侦听的 HTTP 地址的权限。</span><span class="sxs-lookup"><span data-stu-id="d734d-155">Samples that are self-hosted (not hosted in IIS) require permission to register HTTP addresses on the computer for listening.</span></span> <span data-ttu-id="d734d-156">用于 HTTP 命名空间预留的权限由用于运行该示例的用户帐户提供。</span><span class="sxs-lookup"><span data-stu-id="d734d-156">The permission for an HTTP namespace reservation comes from the user account used to run the sample.</span></span> <span data-ttu-id="d734d-157">默认情况下，管理员帐户具有注册任何 HTTP 地址的权限。</span><span class="sxs-lookup"><span data-stu-id="d734d-157">By default, administrator accounts have the permission to register any HTTP address.</span></span> <span data-ttu-id="d734d-158">必须向非管理员帐户授予针对示例所使用的 HTTP 命名空间的权限。</span><span class="sxs-lookup"><span data-stu-id="d734d-158">Non-administrator accounts must be granted permission for the HTTP namespaces used by the samples.</span></span> <span data-ttu-id="d734d-159">有关如何配置命名空间预留的详细信息，请参阅[配置 HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="d734d-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span>

14. <span data-ttu-id="d734d-160">有些示例需要使用消息队列。</span><span class="sxs-lookup"><span data-stu-id="d734d-160">Some samples require Message Queuing.</span></span> <span data-ttu-id="d734d-161">有关安装说明，请参阅 [安装消息队列 (MSMQ) ](installing-message-queuing-msmq.md) 。</span><span class="sxs-lookup"><span data-stu-id="d734d-161">See [Installing Message Queuing (MSMQ)](installing-message-queuing-msmq.md) for installation instructions.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d734d-162">确保在运行需要消息队列的任何示例之前启动 MSMQ 服务。</span><span class="sxs-lookup"><span data-stu-id="d734d-162">Ensure that you start the MSMQ service before you run any samples that require Message Queuing.</span></span>

15. <span data-ttu-id="d734d-163">有些示例需要使用证书。</span><span class="sxs-lookup"><span data-stu-id="d734d-163">Some samples require certificates.</span></span> <span data-ttu-id="d734d-164">请参阅 [Internet Information Services (IIS) 服务器证书安装说明](iis-server-certificate-installation-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="d734d-164">See [Internet Information Services (IIS) Server Certificate Installation Instructions](iis-server-certificate-installation-instructions.md).</span></span>
