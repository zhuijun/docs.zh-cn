---
title: ServiceModel 注册工具 (ServiceModelReg.exe)
description: 如果在服务激活过程中遇到问题，请使用此命令行工具来管理在一台计算机上注册 WCF 和 WF 组件。
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245890"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="f5ed2-103">ServiceModel 注册工具 (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="f5ed2-103">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="f5ed2-104">利用此命令行工具可以管理 WCF 和 WF 组件在单一计算机上的注册。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-104">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="f5ed2-105">在正常情况下，不应使用此工具，因为 WCF 和WF 组件在安装时配置。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-105">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="f5ed2-106">但如果您遇到服务激活方面的问题，可以尝试使用此工具注册组件。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-106">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5ed2-107">语法</span><span class="sxs-lookup"><span data-stu-id="f5ed2-107">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5ed2-108">备注</span><span class="sxs-lookup"><span data-stu-id="f5ed2-108">Remarks</span></span>  
 <span data-ttu-id="f5ed2-109">可在以下位置中找到此工具：</span><span class="sxs-lookup"><span data-stu-id="f5ed2-109">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="f5ed2-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f5ed2-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="f5ed2-111">当在 Windows Vista 上运行 "带中注册" 工具时，" **Windows 功能**" 对话框可能不会反映 Windows Communication Foundation 启用**Microsoft .NET FRAMEWORK 3.0**的**HTTP 激活**选项。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-111">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="f5ed2-112">可以通过单击 "**开始**"，然后单击 "**运行**"，然后键入 " **OptionalFeatures**" 来访问 " **Windows 功能**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-112">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="f5ed2-113">下表介绍可用于 ServiceModelReg.exe 的选项。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-113">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="f5ed2-114">选项</span><span class="sxs-lookup"><span data-stu-id="f5ed2-114">Option</span></span>|<span data-ttu-id="f5ed2-115">说明</span><span class="sxs-lookup"><span data-stu-id="f5ed2-115">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="f5ed2-116">安装所有 WCF 和 WF 组件。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-116">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="f5ed2-117">卸载所有 WCF 和 WF 组件。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-117">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="f5ed2-118">修复所有 WCF 和 WF 组件。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-118">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="f5ed2-119">安装使用 –c 指定的 WCF 和 WF 组件。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-119">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="f5ed2-120">卸载使用 –c 指定的 WCF 和 WF 组件。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-120">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="f5ed2-121">安装或卸载组件：</span><span class="sxs-lookup"><span data-stu-id="f5ed2-121">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="f5ed2-122">-httpnamespace – HTTP 命名空间保留</span><span class="sxs-lookup"><span data-stu-id="f5ed2-122">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="f5ed2-123">-tcpportsharing – TCP 端口共享服务</span><span class="sxs-lookup"><span data-stu-id="f5ed2-123">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="f5ed2-124">-tcpactivation – TCP 激活服务（.NET 4 客户端配置文件不支持）</span><span class="sxs-lookup"><span data-stu-id="f5ed2-124">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="f5ed2-125">-namedpipeactivation –命名管道激活服务（.NET 4 客户端配置文件不支持</span><span class="sxs-lookup"><span data-stu-id="f5ed2-125">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="f5ed2-126">-msmqactivation – MSMQ 激活服务（.NET 4 客户端配置文件不支持</span><span class="sxs-lookup"><span data-stu-id="f5ed2-126">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="f5ed2-127">-etw-ETW 事件跟踪清单（Windows Vista 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="f5ed2-127">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="f5ed2-128">安静模式（仅显示错误日志记录）</span><span class="sxs-lookup"><span data-stu-id="f5ed2-128">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="f5ed2-129">详细模式。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-129">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="f5ed2-130">取消版权和标题消息。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-130">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="f5ed2-131">显示帮助文本</span><span class="sxs-lookup"><span data-stu-id="f5ed2-131">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="f5ed2-132">修复 FileLoadException 错误</span><span class="sxs-lookup"><span data-stu-id="f5ed2-132">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="f5ed2-133">如果在计算机上安装了早期版本的 WCF，则在 `FileLoadFoundException` 运行 servicemodelreg.exe 工具注册新安装时，可能会收到错误。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-133">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="f5ed2-134">即使从以前的安装中手动移除了文件（但保留 machine.config 设置不变），也可能发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-134">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="f5ed2-135">错误消息类似于以下内容。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-135">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="f5ed2-136">从错误消息中，您应注意到早期的客户技术预览 (CTP) 版本安装了 System.ServiceModel 2.0.0.0 版程序集。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-136">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="f5ed2-137">而已发布 System.ServiceModel 程序集的当前版本为 3.0.0.0。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-137">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="f5ed2-138">因此，当你想要在安装了 WCF 的早期 CTP 版本但未完全卸载的计算机上安装官方 WCF 版本时，会遇到此问题。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-138">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="f5ed2-139">ServiceModelReg.exe 无法清除以前的版本项，也无法注册新的版本项。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-139">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="f5ed2-140">唯一的解决方法是手动编辑 machine.config。您可以在以下位置找到此文件。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-140">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="f5ed2-141">如果在64位计算机上运行 WCF，还应在此位置编辑同一文件。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-141">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="f5ed2-142">在此文件中找到引用 "System.servicemodel，Version = 2.0.0.0" 的任何 XML 节点，删除它们和任何子节点。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-142">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="f5ed2-143">保存文件并重新运行 ServiceModelReg.exe 可解决此问题。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-143">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f5ed2-144">示例</span><span class="sxs-lookup"><span data-stu-id="f5ed2-144">Examples</span></span>  
 <span data-ttu-id="f5ed2-145">下面的示例演示如何使用 ServiceModelReg.exe 工具的最常用选项。</span><span class="sxs-lookup"><span data-stu-id="f5ed2-145">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
