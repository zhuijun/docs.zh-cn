---
title: 如何：使用 COM+ 服务模型配置工具
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: f9e761bafd84726b51a2010a932c68c67c37f899
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595279"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="6eb29-102">如何：使用 COM+ 服务模型配置工具</span><span class="sxs-lookup"><span data-stu-id="6eb29-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="6eb29-103">在选择了适当的宿主模式之后，就可使用 COM+ 服务模型配置命令行工具 (ComSvcConfig.exe) 来配置将作为 Web 服务公开的应用程序接口。</span><span class="sxs-lookup"><span data-stu-id="6eb29-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6eb29-104">你必须具有计算机上的管理员身份，才能执行下列各项任务。</span><span class="sxs-lookup"><span data-stu-id="6eb29-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="6eb29-105">在 Windows 7 计算机上使用 ComSvcConfig.exe 配置 Web 服务以使用最新服务模型版本（当前版本为 v4.5）时，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6eb29-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1. <span data-ttu-id="6eb29-106">将注册表项设置 `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 为 DWORD 值0x00000001</span><span class="sxs-lookup"><span data-stu-id="6eb29-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2. <span data-ttu-id="6eb29-107">运行 comsvcconfig.exe</span><span class="sxs-lookup"><span data-stu-id="6eb29-107">Run comsvcconfig.exe</span></span>  
  
3. <span data-ttu-id="6eb29-108">将步骤 1 中的注册表项还原到其原始值，或者在不存在原始值时将该注册表项删除。</span><span class="sxs-lookup"><span data-stu-id="6eb29-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6eb29-109">还原此注册表项十分重要。</span><span class="sxs-lookup"><span data-stu-id="6eb29-109">Reverting this registry key is important.</span></span> <span data-ttu-id="6eb29-110">这是一个兼容性注册表项。</span><span class="sxs-lookup"><span data-stu-id="6eb29-110">This is a compatibility key.</span></span> <span data-ttu-id="6eb29-111">不还原此更改可能会造成在计算机上运行的其他 .NET 应用程序产生问题）</span><span class="sxs-lookup"><span data-stu-id="6eb29-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="6eb29-112">在 Windows 8 计算机上使用 Comsvcconfig.exe/install 时，会显示一个对话框，其中显示 "你的电脑上的应用需要以下 Windows 功能： .NET Framework 3.5 （包括 .NET 2.0 和 .NET 3.0" （如果未安装 .NET Framework 3.5）。</span><span class="sxs-lookup"><span data-stu-id="6eb29-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="6eb29-113">可忽略此对话框。</span><span class="sxs-lookup"><span data-stu-id="6eb29-113">This dialog may be ignored.</span></span> <span data-ttu-id="6eb29-114">或者，可以将 OnlyUseLatestCLR 注册表项设置为 DWORD 值 0x00000001</span><span class="sxs-lookup"><span data-stu-id="6eb29-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="6eb29-115">使用 COM + 宿主模式将接口添加到作为 Web 服务公开的接口集</span><span class="sxs-lookup"><span data-stu-id="6eb29-115">To add an interface to the set of interfaces exposed as Web services, using the COM+ hosting mode</span></span>  
  
- <span data-ttu-id="6eb29-116">使用 `/install` 和 `/hosting:complus` 选项运行 ComSvcConfig，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6eb29-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="6eb29-117">此命令将 `IFinances` 组件（它属于 OnlineStore COM+ 应用程序）的 `ItemOrders.IFinancial` 接口添加到将作为 Web 服务公开的接口集。</span><span class="sxs-lookup"><span data-stu-id="6eb29-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="6eb29-118">此服务使用 COM+ 宿主模式，因此要求显式激活应用程序。</span><span class="sxs-lookup"><span data-stu-id="6eb29-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="6eb29-119">尽管可以将通配符星号（ \* ）字符用于组件和接口，但应避免使用它，因为你可能希望仅将选定的功能作为 Web 服务公开。</span><span class="sxs-lookup"><span data-stu-id="6eb29-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="6eb29-120">如果对此组件的将来版本运行命令，则使用通配符可能意外地公开在确定配置语法时尚不存在的接口。</span><span class="sxs-lookup"><span data-stu-id="6eb29-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="6eb29-121">/verbose 选项指示该工具除显示所有错误以外，还要显示警告。</span><span class="sxs-lookup"><span data-stu-id="6eb29-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="6eb29-122">所公开的服务的协定将包含 `IFinances` 接口中的所有方法。</span><span class="sxs-lookup"><span data-stu-id="6eb29-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
## <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="6eb29-123">如果使用 COM + 宿主模式，则仅将接口中的特定方法添加到作为 Web 服务公开的接口集</span><span class="sxs-lookup"><span data-stu-id="6eb29-123">To add only specific methods from an interface to the set of interfaces exposed as Web services, using the COM+ hosting mode</span></span>  
  
- <span data-ttu-id="6eb29-124">使用 `/install` 和 `/hosting:complus` 选项以及所需方法的显式命名运行 ComSvcConfig，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6eb29-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="6eb29-125">此命令仅将 `Credit` 接口中的 `Debit` 和 `IFinances` 方法作为操作添加到所公开的服务协定中。</span><span class="sxs-lookup"><span data-stu-id="6eb29-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="6eb29-126">此接口中的其他所有方法将在协定中省略，并且无法从 Web 服务客户端调用。</span><span class="sxs-lookup"><span data-stu-id="6eb29-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="6eb29-127">使用 Web 宿主模式将接口添加到作为 Web 服务公开的接口集</span><span class="sxs-lookup"><span data-stu-id="6eb29-127">To add an interface to the set of interfaces exposed as Web services, using the Web hosting mode</span></span>  
  
- <span data-ttu-id="6eb29-128">使用 `/install` 选项和 `/hosting:was` 选项运行 ComSvcConfig，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6eb29-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="6eb29-129">此命令将 `IStockLevels` 组件（它属于 OnlineWarehouse COM+ 应用程序）的 `ItemInventory.Warehouse` 接口添加到将作为 Web 服务公开的接口集。</span><span class="sxs-lookup"><span data-stu-id="6eb29-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="6eb29-130">此服务以 Web 方式承载在 IIS 的 OnlineWarehouse 虚拟目录中，而不是承载在 COM+ 中，因此应用程序将根据需要自动激活。</span><span class="sxs-lookup"><span data-stu-id="6eb29-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="6eb29-131">若要使用 Web 承载的进程内配置，必须使用组件服务管理控制台将 COM+ 应用程序配置为作为库应用程序而不是服务器应用程序运行。</span><span class="sxs-lookup"><span data-stu-id="6eb29-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="6eb29-132">被配置为服务器应用程序的应用程序使用标准 Web 承载模式，并促使进程跃点处理每个请求。</span><span class="sxs-lookup"><span data-stu-id="6eb29-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="6eb29-133">`/mex` 选项用于添加其他元数据交换 (MEX) 服务终结点，它们与应用程序的服务终结点使用相同的传输协议，以支持要从服务中检索协定定义的客户端。</span><span class="sxs-lookup"><span data-stu-id="6eb29-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
## <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="6eb29-134">移除指定接口的 Web 服务</span><span class="sxs-lookup"><span data-stu-id="6eb29-134">To remove a Web service for a specified interface</span></span>  
  
- <span data-ttu-id="6eb29-135">使用 `/uninstall` 选项运行 ComSvcConfig，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6eb29-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="6eb29-136">此命令将移除 `IFinances` 组件（它属于 OnlineStore COM+ 应用程序）上的 `ItemOrders.Financial` 接口。</span><span class="sxs-lookup"><span data-stu-id="6eb29-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
## <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="6eb29-137">列出当前公开的接口</span><span class="sxs-lookup"><span data-stu-id="6eb29-137">To list currently exposed interfaces</span></span>  
  
- <span data-ttu-id="6eb29-138">使用 `/list` 选项运行 ComSvcConfig，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6eb29-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="6eb29-139">此命令列出当前公开的接口以及相应的地址和绑定详细信息，范围局限于本地计算机。</span><span class="sxs-lookup"><span data-stu-id="6eb29-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
## <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="6eb29-140">列出当前公开的特定接口</span><span class="sxs-lookup"><span data-stu-id="6eb29-140">To list specific currently exposed interfaces</span></span>  
  
- <span data-ttu-id="6eb29-141">使用 `/list` 选项运行 ComSvcConfig，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6eb29-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="6eb29-142">此命令列出当前公开的 COM+ 承载接口以及相应的地址和绑定详细信息，范围局限于本地计算机上的 OnlineStore COM+ 应用程序。</span><span class="sxs-lookup"><span data-stu-id="6eb29-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
## <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="6eb29-143">显示可与此实用工具一起使用的选项的帮助</span><span class="sxs-lookup"><span data-stu-id="6eb29-143">To display help on the options that can be used with the utility</span></span>  
  
- <span data-ttu-id="6eb29-144">使用 /? 选项运行 ComSvcConfig，</span><span class="sxs-lookup"><span data-stu-id="6eb29-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="6eb29-145">如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="6eb29-145">option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6eb29-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6eb29-146">See also</span></span>

- [<span data-ttu-id="6eb29-147">与 COM + 应用程序集成概述</span><span class="sxs-lookup"><span data-stu-id="6eb29-147">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
