---
title: 安装问题疑难解答
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 76d8752f8bcfcb94b77a60be60e13a66436e76b8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549648"
---
# <a name="troubleshoot-setup-issues"></a><span data-ttu-id="6a9eb-102">安装问题疑难解答</span><span class="sxs-lookup"><span data-stu-id="6a9eb-102">Troubleshoot setup issues</span></span>

<span data-ttu-id="6a9eb-103">本文介绍如何解决 Windows Communication Foundation (WCF) 设置问题。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-103">This article describes how to troubleshoot Windows Communication Foundation (WCF) set up issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="6a9eb-104">有些 Windows Communication Foundation 注册表项无法通过在 .NET Framework 3.0 上执行 MSI 修复操作来修复</span><span class="sxs-lookup"><span data-stu-id="6a9eb-104">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  
 <span data-ttu-id="6a9eb-105">如果您删除下面的任何注册表项：</span><span class="sxs-lookup"><span data-stu-id="6a9eb-105">If you delete any of the following registry keys:</span></span>  
  
- <span data-ttu-id="6a9eb-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="6a9eb-106">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
- <span data-ttu-id="6a9eb-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="6a9eb-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
- <span data-ttu-id="6a9eb-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="6a9eb-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
- <span data-ttu-id="6a9eb-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="6a9eb-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
- <span data-ttu-id="6a9eb-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="6a9eb-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="6a9eb-111">如果使用从**控制面板**中的 "**添加/删除程序**" 小程序启动的 .NET Framework 3.0 安装程序运行修复，则不会重新创建这些密钥。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-111">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="6a9eb-112">若要重新正确创建这些项，用户必须卸载并重新安装 .NET Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-112">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a><span data-ttu-id="6a9eb-113">在安装 .NET Framework 3.0 软件包过程中 WMI Service Corruption 阻止 Windows Communication Foundation WMI 提供程序的安装</span><span class="sxs-lookup"><span data-stu-id="6a9eb-113">WMI Service Corruption Blocks Installation of the Windows Communication Foundation WMI provider during installation of .NET Framework 3.0 package</span></span>  
 <span data-ttu-id="6a9eb-114">WMI Service Corruption 可能阻止 Windows Communication Foundation WMI 提供程序的安装。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-114">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider.</span></span> <span data-ttu-id="6a9eb-115">在安装过程中，Windows Communication Foundation 安装程序无法使用 mofcomp.exe 组件注册 WCF .mof 文件。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-115">During installation the Windows Communication Foundation installer is unable to register the WCF .mof file using the mofcomp.exe component.</span></span> <span data-ttu-id="6a9eb-116">下面列出了几个症状：</span><span class="sxs-lookup"><span data-stu-id="6a9eb-116">The following is a list of symptoms:</span></span>  
  
1. <span data-ttu-id="6a9eb-117">.NET Framework 3.0 安装成功完成，但未注册 WCF WMI 提供程序。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-117">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2. <span data-ttu-id="6a9eb-118">应用程序事件日志中显示一个错误事件，该事件指示在注册 WCF 的 WMI 提供程序或运行 mofcomp.exe 时出现问题。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-118">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3. <span data-ttu-id="6a9eb-119">用户的 %temp% 目录中名为 dd_wcf_retCA\* 的安装日志文件包含对注册 WCF WMI 提供程序失败的引用。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-119">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4. <span data-ttu-id="6a9eb-120">事件日志或安装跟踪日志文件中可能会列出以下异常之一：</span><span class="sxs-lookup"><span data-stu-id="6a9eb-120">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="6a9eb-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: 使用“E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof”执行 E:\WINDOWS\system32\wbem\mofcomp.exe 发生意外结果 3</span><span class="sxs-lookup"><span data-stu-id="6a9eb-121">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="6a9eb-122">或者：</span><span class="sxs-lookup"><span data-stu-id="6a9eb-122">or:</span></span>  
  
     <span data-ttu-id="6a9eb-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: “System.Management.ManagementPath”的类型初始值设定项引发异常。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-123">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="6a9eb-124">---> COMException (0x80040154) ：检索 CLSID 为 {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} 的组件的 COM 类工厂因以下错误而失败：80040154。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-124">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="6a9eb-125">或者：</span><span class="sxs-lookup"><span data-stu-id="6a9eb-125">or:</span></span>  
  
     <span data-ttu-id="6a9eb-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: 无法加载文件或程序集“C:\WINDOWS\system32\wbem\mofcomp.exe”或其一个依赖项。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-126">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="6a9eb-127">系统找不到指定的文件。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-127">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="6a9eb-128">文件名:“C:\WINDOWS\system32\wbem\mofcomp.exe”</span><span class="sxs-lookup"><span data-stu-id="6a9eb-128">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="6a9eb-129">若要解决前面说明的问题，必须按照以下步骤操作。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-129">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1. <span data-ttu-id="6a9eb-130">运行 [WMI Diagnosis Utility](https://www.microsoft.com/download/details.aspx?id=7684) 以修复 WMI 服务。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-130">Run the [WMI Diagnosis Utility](https://www.microsoft.com/download/details.aspx?id=7684) to repair the WMI service.</span></span> <span data-ttu-id="6a9eb-131">有关使用此工具的详细信息，请参阅 [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-131">For more information about using this tool, see [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="6a9eb-132">使用**控制面板**中的 "**添加/删除程序**" 小程序修复 .NET Framework 3.0 安装，或卸载/重新安装 .NET Framework 3.0。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-132">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a><span data-ttu-id="6a9eb-133">在安装 .NET Framework 3.5 后修复 .NET Framework 3.0 会移除 .NET Framework 3.5 在 machine.config 中引入的配置元素</span><span class="sxs-lookup"><span data-stu-id="6a9eb-133">Repairing .NET Framework 3.0 after .NET Framework 3.5 Installation Removes Configuration Elements Introduced by .NET Framework 3.5 in machine.config</span></span>  
 <span data-ttu-id="6a9eb-134">如果在安装 .NET Framework 3.5 后修复 .NET Framework 3.0，则会删除 machine.config 中 .NET Framework 3.5 引入的配置元素。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-134">If you do a repair of .NET Framework 3.0 after you installed .NET Framework 3.5, configuration elements introduced by .NET Framework 3.5 in machine.config are removed.</span></span> <span data-ttu-id="6a9eb-135">但是，web.config 保持不变。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-135">However, the web.config remains intact.</span></span> <span data-ttu-id="6a9eb-136">解决方法是在此之后通过 ARP 修复 .NET Framework 3.5，或使用 [工作流服务注册工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md) 与交换机一起使用 `/c` 。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-136">The workaround is to repair .NET Framework 3.5 after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="6a9eb-137">[工作流服务注册工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md) 可在%Windir%\Microsoft.NET\framework\v3.5\ 或%windir%\microsoft.net\framework64\v3.5\ 中找到中找到</span><span class="sxs-lookup"><span data-stu-id="6a9eb-137">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="6a9eb-138">安装 .NET Framework 3.5 之后，为 WCF/WF Webhost 正确配置 IIS</span><span class="sxs-lookup"><span data-stu-id="6a9eb-138">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  
 <span data-ttu-id="6a9eb-139">如果 .NET Framework 3.5 安装无法配置与 WCF 相关的其他 IIS 配置设置，则会在安装日志中记录错误并继续。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-139">When .NET Framework 3.5 installation fails to configure additional WCF-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="6a9eb-140">对运行 WorkflowServices 应用程序的任何尝试都将失败，因为缺少必需的配置设置。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-140">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="6a9eb-141">例如，加载 xoml 或规则服务会失败。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-141">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="6a9eb-142">若要解决此问题，请使用 [工作流服务注册工具 ( 带有开关的 # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md) `/c` 在计算机上正确配置 IIS 脚本映射。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-142">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="6a9eb-143">[工作流服务注册工具 ( # A0) ](workflow-service-registration-tool-wfservicesreg-exe.md) 可在%Windir%\Microsoft.NET\framework\v3.5\ 或%windir%\microsoft.net\framework64\v3.5\ 中找到中找到</span><span class="sxs-lookup"><span data-stu-id="6a9eb-143">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a><span data-ttu-id="6a9eb-144">未能从程序集 "System.servicemodel，Version 3.0.0.0，Culture = 中立，PublicKeyToken = b77a5c561934e089" 加载类型 "HttpModule"</span><span class="sxs-lookup"><span data-stu-id="6a9eb-144">Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'</span></span>  
 <span data-ttu-id="6a9eb-145">如果安装 .NET Framework 4 并启用 WCF HTTP 激活，则会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="6a9eb-145">This error occurs if .NET Framework 4 is installed and then WCF HTTP Activation is enabled.</span></span> <span data-ttu-id="6a9eb-146">若要解决此问题，请从 Visual Studio 的开发人员命令提示中运行以下命令行：</span><span class="sxs-lookup"><span data-stu-id="6a9eb-146">To resolve the issue run the following command-line from inside the Developer Command Prompt for Visual Studio:</span></span>  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a9eb-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a9eb-147">See also</span></span>

- [<span data-ttu-id="6a9eb-148">设置说明</span><span class="sxs-lookup"><span data-stu-id="6a9eb-148">Set-Up Instructions</span></span>](./samples/set-up-instructions.md)
