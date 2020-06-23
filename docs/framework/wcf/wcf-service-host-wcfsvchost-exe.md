---
title: WCF 服务主机 (WcfSvcHost.exe)
description: 使用 WCF 服务主机承载和测试已实现的服务。 您可以使用 WCF 测试客户端或您自己的客户端来测试服务。
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: efc9512766d2a9cc814083ab632226d98917bf4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245721"
---
# <a name="wcf-service-host-wcfsvchostexe"></a><span data-ttu-id="6af58-104">WCF 服务主机 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="6af58-104">WCF Service Host (WcfSvcHost.exe)</span></span>

<span data-ttu-id="6af58-105">Windows Communication Foundation （WCF）服务主机（WcfSvcHost.exe）允许您启动 Visual Studio 调试器（F5）以自动承载和测试已实现的服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-105">Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="6af58-106">然后，您可以使用 WCF 测试客户端（WcfTestClient.exe）或您自己的客户端来测试服务，以查找并解决任何潜在错误。</span><span class="sxs-lookup"><span data-stu-id="6af58-106">You can then test the service using WCF Test Client (WcfTestClient.exe), or your own client, to find and fix any potential errors.</span></span>

## <a name="wcf-service-host"></a><span data-ttu-id="6af58-107">WCF 服务主机</span><span class="sxs-lookup"><span data-stu-id="6af58-107">WCF Service Host</span></span>

<span data-ttu-id="6af58-108">WCF 服务主机枚举 WCF 服务项目中的服务，加载项目的配置，并为它找到的每个服务实例化主机。</span><span class="sxs-lookup"><span data-stu-id="6af58-108">WCF Service Host enumerates the services in a WCF service project, loads the project’s configuration, and instantiates a host for each service that it finds.</span></span> <span data-ttu-id="6af58-109">该工具通过 WCF 服务模板集成到 Visual Studio 中，并在你开始调试项目时进行调用。</span><span class="sxs-lookup"><span data-stu-id="6af58-109">The tool is integrated into Visual Studio through the WCF Service template and is invoked when you start to debug your project.</span></span>

<span data-ttu-id="6af58-110">通过使用 WCF 服务主机，你可以在不编写额外代码或在开发过程中将其提交到特定主机的情况下，在 WCF 服务库项目中承载 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-110">By using WCF Service Host, you can host a WCF service (in a WCF service library project) without writing extra code or committing to a specific host during development.</span></span>

> [!NOTE]
> <span data-ttu-id="6af58-111">WCF 服务主机不支持部分信任。</span><span class="sxs-lookup"><span data-stu-id="6af58-111">WCF Service Host does not support Partial Trust.</span></span> <span data-ttu-id="6af58-112">如果要在部分信任环境中使用 WCF 服务，请不要使用 Visual Studio 中的 WCF 服务库项目模板生成服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-112">If you want to use a WCF Service in Partial Trust, do not use the WCF Service Library Project template in Visual Studio to build your service.</span></span> <span data-ttu-id="6af58-113">而是在 Visual Studio 中创建一个新网站，方法是选择 "WCF 服务网站" 模板，该模板可以在支持 WCF 部分信任的 Web 服务器中承载服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-113">Instead, create a New WebSite in Visual Studio by choosing the WCF Service WebSite template, which can host the service in a WebServer on which WCF Partial Trust is supported.</span></span>

## <a name="project-types-hosted-by-wcf-service-host"></a><span data-ttu-id="6af58-114">WCF 服务主机承载的项目类型</span><span class="sxs-lookup"><span data-stu-id="6af58-114">Project Types hosted by WCF Service Host</span></span>

<span data-ttu-id="6af58-115">WCF 服务主机可以承载以下 WCF 服务库项目类型： WCF 服务库、顺序工作流服务库、状态机工作流服务库和联合服务库。</span><span class="sxs-lookup"><span data-stu-id="6af58-115">WCF Service Host can host the following WCF service library project types: WCF Service Library, Sequential Workflow Service Library, State Machine Workflow Service Library and Syndication Service Library.</span></span> <span data-ttu-id="6af58-116">WCF 服务主机还可以托管这些可使用 "**添加项**" 功能添加到服务库项目中的服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-116">WCF Service Host can also host those services that can be added to a service library project using the **Add Item** functionality.</span></span> <span data-ttu-id="6af58-117">这包括 WCF 服务、WF 状态机服务、WF 顺序服务、XAML WF 状态机服务和 XAML WF 顺序服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-117">This includes WCF Service, WF State Machine Service, WF Sequential Service, XAML WF State Machine Service and XAML WF Sequential Service.</span></span>

<span data-ttu-id="6af58-118">但是，应该注意到该工具将不会帮助您配置主机。</span><span class="sxs-lookup"><span data-stu-id="6af58-118">You should note, however, that the tool will not help you to configure a host.</span></span> <span data-ttu-id="6af58-119">对于此项任务，必须手动编辑 App.config 文件。</span><span class="sxs-lookup"><span data-stu-id="6af58-119">For this task, you must manually edit the App.config file.</span></span> <span data-ttu-id="6af58-120">另外，此工具也不会验证用户定义的配置文件。</span><span class="sxs-lookup"><span data-stu-id="6af58-120">The tool also does not validate user-defined configuration files.</span></span>

> [!CAUTION]
> <span data-ttu-id="6af58-121">不应在生产环境中使用 WCF 服务主机来托管服务，因为它不是为此目的而设计的。</span><span class="sxs-lookup"><span data-stu-id="6af58-121">You should not use WCF Service Host to host services in a production environment, as it was not engineered for this purpose.</span></span>  <span data-ttu-id="6af58-122">WCF 服务主机不支持此类环境的可靠性、安全性和可管理性要求。</span><span class="sxs-lookup"><span data-stu-id="6af58-122">WCF Service Host does not support the reliability, security, and manageability requirements of such an environment.</span></span> <span data-ttu-id="6af58-123">请改用 IIS，因为它可以提供卓越的可靠性和监视功能，并且是承载服务的首选解决方案。</span><span class="sxs-lookup"><span data-stu-id="6af58-123">Instead, use IIS since it provides superior reliability and monitoring features, and is the preferred solution for hosting services.</span></span> <span data-ttu-id="6af58-124">完成服务开发后，应将服务从 WCF 服务主机迁移到 IIS。</span><span class="sxs-lookup"><span data-stu-id="6af58-124">Once development of your services is complete, you should migrate the services from WCF Service Host to IIS.</span></span>

## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a><span data-ttu-id="6af58-125">在 Visual Studio 中使用 WCF 服务主机的方案</span><span class="sxs-lookup"><span data-stu-id="6af58-125">Scenarios for Using WCF Service Host inside Visual Studio</span></span>

<span data-ttu-id="6af58-126">下表列出了 "**命令行参数**" 对话框中的所有参数，在 Visual Studio 的 "**解决方案资源管理器**" 中右键单击项目，选择 "**属性**"，然后选择 "**调试**" 选项卡，然后单击 "**启动项目**"，可以找到该对话框。</span><span class="sxs-lookup"><span data-stu-id="6af58-126">The following table lists all the parameters in the **Command line arguments** dialog box, which can be found by right-clicking your project in **Solutions Explorer** in Visual Studio, selecting **Properties**, then selecting the **Debug** tab and clicking **Start Project**.</span></span> <span data-ttu-id="6af58-127">这些参数在配置 WCF 服务主机时非常有用。</span><span class="sxs-lookup"><span data-stu-id="6af58-127">These parameters are useful in configuring WCF Service Host.</span></span>

|<span data-ttu-id="6af58-128">参数</span><span class="sxs-lookup"><span data-stu-id="6af58-128">Parameter</span></span>|<span data-ttu-id="6af58-129">含义</span><span class="sxs-lookup"><span data-stu-id="6af58-129">Meaning</span></span>|
|---------------|-------------|
|`/client`|<span data-ttu-id="6af58-130">一个可选参数，用于指定要在承载服务后运行的可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="6af58-130">An optional parameter that specifies the path to an executable to run after the services are hosted.</span></span> <span data-ttu-id="6af58-131">这会在托管后启动 WCF 测试客户端。</span><span class="sxs-lookup"><span data-stu-id="6af58-131">This launches WCF Test Client following hosting.</span></span>|
|`/clientArg`|<span data-ttu-id="6af58-132">将字符串指定为传递给自定义客户端应用程序的参数。</span><span class="sxs-lookup"><span data-stu-id="6af58-132">Specify a string as an argument that is passed to the custom client application.</span></span>|
|`/?`|<span data-ttu-id="6af58-133">显示帮助文本。</span><span class="sxs-lookup"><span data-stu-id="6af58-133">Displays the help text.</span></span>|

#### <a name="using-wcf-test-client"></a><span data-ttu-id="6af58-134">使用 WCF 测试客户端</span><span class="sxs-lookup"><span data-stu-id="6af58-134">Using WCF Test Client</span></span>

<span data-ttu-id="6af58-135">创建新的 WCF 服务项目并按 F5 启动调试器后，WCF 服务主机将开始承载它在项目中找到的所有服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-135">After you create a new WCF service project and press F5 to start the debugger, WCF Service Host starts hosting all the services it finds in your project.</span></span> <span data-ttu-id="6af58-136">WCF 测试客户端将自动打开并显示在配置文件中定义的服务终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="6af58-136">WCF Test Client automatically opens and displays a list of service endpoints defined in the configuration file.</span></span> <span data-ttu-id="6af58-137">可以从主窗口中测试参数并调用服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-137">From the main window, you can test the parameters and invoke your service.</span></span>

<span data-ttu-id="6af58-138">若要确保使用 WCF 测试客户端，请在 Visual Studio 的**解决方案资源管理器**中右键单击项目，选择 "**属性**"，然后选择 "**调试**" 选项卡。单击 "**启动项目**"，并确保下面出现在 "**命令行参数**" 对话框中。</span><span class="sxs-lookup"><span data-stu-id="6af58-138">To make sure that WCF Test Client is used, right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab. Click **Start Project** and ensure that the following appears in the **Command line arguments** dialog box.</span></span>

`/client:WcfTestClient.exe`

#### <a name="using-a-custom-client"></a><span data-ttu-id="6af58-139">使用自定义客户端</span><span class="sxs-lookup"><span data-stu-id="6af58-139">Using a Custom Client</span></span>

<span data-ttu-id="6af58-140">若要使用自定义客户端，请在 Visual Studio 的**解决方案资源管理器**中右键单击项目，选择 "**属性**"，然后选择 "**调试**" 选项卡。单击 "**启动项目**"，然后 `/client` 在 "**命令行参数**" 对话框中编辑参数以指向自定义客户端，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="6af58-140">To use a custom client, right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab. Click **Start Project** and edit the `/client` parameter in the **Command line arguments** dialog box to point to your custom client, as indicated in the following example.</span></span>

`/client:"path/CustomClient.exe"`

<span data-ttu-id="6af58-141">当您按 F5 再次启动服务时，WCF 服务主机将在您启动调试器时自动启动您的自定义客户端。</span><span class="sxs-lookup"><span data-stu-id="6af58-141">When you press F5 to start the service again, WCF Service Host automatically starts your custom client when you launch the debugger.</span></span>

<span data-ttu-id="6af58-142">也可以按照以下示例中的指示使用 `/clientArg:` 形参将字符串指定为传递给自定义客户端应用程序的实参。</span><span class="sxs-lookup"><span data-stu-id="6af58-142">You can also use the `/clientArg:` parameter to specify a string as an argument that is passed to the custom client application, as indicated in the following example.</span></span>

`/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`

<span data-ttu-id="6af58-143">例如，如果使用的是联合服务库模板，则可以使用以下命令行自变量：</span><span class="sxs-lookup"><span data-stu-id="6af58-143">For example, if you are using the Syndication Service Library template, you can use the following command line arguments,</span></span>

`/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`

#### <a name="specifying-no-client"></a><span data-ttu-id="6af58-144">指定无客户端</span><span class="sxs-lookup"><span data-stu-id="6af58-144">Specifying No Client</span></span>

<span data-ttu-id="6af58-145">若要指定在 WCF 服务承载后不使用任何客户端，请在 Visual Studio 的**解决方案资源管理器**中右键单击项目，选择 "**属性**"，然后选择 "**调试**" 选项卡。单击 "**启动项目**"，并将 "**命令行参数**" 对话框留空。</span><span class="sxs-lookup"><span data-stu-id="6af58-145">To specify that no client will be used after WCF service hosting, right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab. Click **Start Project** and leave the **Command line arguments** dialog box blank.</span></span>

#### <a name="using-a-custom-host"></a><span data-ttu-id="6af58-146">使用自定义主机</span><span class="sxs-lookup"><span data-stu-id="6af58-146">Using a Custom Host</span></span>

<span data-ttu-id="6af58-147">若要使用自定义主机，请在 Visual Studio 的**解决方案资源管理器**中右键单击项目，选择 "**属性**"，然后选择 "**调试**" 选项卡。单击 "**启动外部程序**"，并输入自定义主机的完整路径。</span><span class="sxs-lookup"><span data-stu-id="6af58-147">To use a custom host, right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab. Click **Start External Program** and enter the full path to the custom host.</span></span> <span data-ttu-id="6af58-148">还可以使用 "**命令行参数**" 对话框指定要传递给主机的参数。</span><span class="sxs-lookup"><span data-stu-id="6af58-148">You can also use the **Command line arguments** dialog box to specify arguments to be passed to the host.</span></span>

## <a name="wcf-service-host-user-interface"></a><span data-ttu-id="6af58-149">WCF 服务主机用户界面</span><span class="sxs-lookup"><span data-stu-id="6af58-149">WCF Service Host User Interface</span></span>

<span data-ttu-id="6af58-150">最初调用 WCF 服务主机（通过在 Visual Studio 中按 F5）时，" **WCF 服务主机**" 窗口将自动打开。</span><span class="sxs-lookup"><span data-stu-id="6af58-150">When you initially invoke WCF Service Host (by pressing F5 inside Visual Studio), the **WCF Service Host** window automatically opens.</span></span> <span data-ttu-id="6af58-151">当 WCF 服务主机正在运行时，该程序的图标将出现在通知区域中。</span><span class="sxs-lookup"><span data-stu-id="6af58-151">When WCF Service Host is running, the program's icon appears in the notification area.</span></span> <span data-ttu-id="6af58-152">双击该图标以打开 " **WCF 服务主机**" 窗口</span><span class="sxs-lookup"><span data-stu-id="6af58-152">Double-click the icon to open the **WCF Service Host** window</span></span>

<span data-ttu-id="6af58-153">当服务承载期间发生错误时，"WCF 服务主机" 对话框将打开以显示相关信息。</span><span class="sxs-lookup"><span data-stu-id="6af58-153">When errors occur during service hosting, WCF Service Host dialog box will open to display relevant information.</span></span>

<span data-ttu-id="6af58-154">" **WCF 服务主机**" 主窗口包含以下两个菜单：</span><span class="sxs-lookup"><span data-stu-id="6af58-154">The **WCF Service Host** main window contains two menus:</span></span>

- <span data-ttu-id="6af58-155">**File**：包含**Close**和**Exit**命令。</span><span class="sxs-lookup"><span data-stu-id="6af58-155">**File**: Contains the **Close** and **Exit** commands.</span></span> <span data-ttu-id="6af58-156">单击 "**关闭**" 时，" **WCF 服务主机**" 对话框将关闭，但会继续托管服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-156">When you click **Close**, the **WCF Service Host** dialog box closes, but the services continue to be hosted.</span></span> <span data-ttu-id="6af58-157">单击 "**退出**" 时，WCF 服务主机也会关闭。</span><span class="sxs-lookup"><span data-stu-id="6af58-157">When you click **Exit**, WCF Service Host is also shut down.</span></span> <span data-ttu-id="6af58-158">这还将停止所有承载的服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-158">This also stops all hosted services.</span></span>

- <span data-ttu-id="6af58-159">**Help**：包含包含版本信息的**About**命令。</span><span class="sxs-lookup"><span data-stu-id="6af58-159">**Help**: Contains the **About** command that contains version information.</span></span> <span data-ttu-id="6af58-160">它还包含可打开帮助文件的**帮助**命令。</span><span class="sxs-lookup"><span data-stu-id="6af58-160">It also contains the **Help** command that can open a help file.</span></span>

<span data-ttu-id="6af58-161">" **WCF 服务主机**" 主窗口包含以下两个区域：</span><span class="sxs-lookup"><span data-stu-id="6af58-161">The main **WCF Service Host** window contains two areas:</span></span>

- <span data-ttu-id="6af58-162">第一个区域为 "**服务**"。</span><span class="sxs-lookup"><span data-stu-id="6af58-162">The first area is **Service**.</span></span> <span data-ttu-id="6af58-163">该区域包含一个显示所有服务基本信息的列表。</span><span class="sxs-lookup"><span data-stu-id="6af58-163">It contains a list that displays basic information of all services.</span></span> <span data-ttu-id="6af58-164">这些信息包括：</span><span class="sxs-lookup"><span data-stu-id="6af58-164">The information includes:</span></span>

  - <span data-ttu-id="6af58-165">**服务**：列出所有服务。</span><span class="sxs-lookup"><span data-stu-id="6af58-165">**Service**: Lists all the services.</span></span>

  - <span data-ttu-id="6af58-166">**状态**：列出服务的状态。</span><span class="sxs-lookup"><span data-stu-id="6af58-166">**Status**: Lists the status of the service.</span></span> <span data-ttu-id="6af58-167">有效值为 "已启动"、"已停止" 和 "错误"。</span><span class="sxs-lookup"><span data-stu-id="6af58-167">Valid values are "Started", "Stopped," and "Error".</span></span>

  - <span data-ttu-id="6af58-168">**元数据地址**：显示服务的元数据地址。</span><span class="sxs-lookup"><span data-stu-id="6af58-168">**Metadata Address**: Displays the metadata address of the services.</span></span>

- <span data-ttu-id="6af58-169">第二个区域是**附加信息**。</span><span class="sxs-lookup"><span data-stu-id="6af58-169">The second area is **Additional Information**.</span></span> <span data-ttu-id="6af58-170">当在**服务**区域中选择特定的服务行时，它会显示服务状态的详细说明。</span><span class="sxs-lookup"><span data-stu-id="6af58-170">It displays a detailed explanation of the service status when the specific service line is selected in the **Service** area.</span></span> <span data-ttu-id="6af58-171">如果状态为“错误”，则可以在屏幕上查看完整的错误消息。</span><span class="sxs-lookup"><span data-stu-id="6af58-171">If the status is Error, you can view the full error message on the screen.</span></span>

## <a name="stopping-wcf-service-host"></a><span data-ttu-id="6af58-172">停止 WCF 服务主机</span><span class="sxs-lookup"><span data-stu-id="6af58-172">Stopping WCF Service Host</span></span>

<span data-ttu-id="6af58-173">可以通过以下四种方法关闭 WCF 服务主机：</span><span class="sxs-lookup"><span data-stu-id="6af58-173">You can shut down WCF Service Host in the following four ways:</span></span>

- <span data-ttu-id="6af58-174">在 Visual Studio 中停止调试会话。</span><span class="sxs-lookup"><span data-stu-id="6af58-174">Stop the debugging session in Visual Studio.</span></span>

- <span data-ttu-id="6af58-175">从 " **WCF 服务主机**" 窗口中的 "**文件**" 菜单中选择 "**退出**"。</span><span class="sxs-lookup"><span data-stu-id="6af58-175">Select **Exit** from the **File** menu in the **WCF Service Host** window.</span></span>

- <span data-ttu-id="6af58-176">从 "系统通知" 区域中的 "WCF 服务主机任务栏" 图标的上下文菜单中选择 "**退出**"。</span><span class="sxs-lookup"><span data-stu-id="6af58-176">Select **Exit** from context menu of WCF Service Host tray icon in the system notification area.</span></span>

- <span data-ttu-id="6af58-177">如果正在使用 WCF 测试客户端，则退出它。</span><span class="sxs-lookup"><span data-stu-id="6af58-177">Exit WCF Test Client if it is being used.</span></span>

## <a name="using-service-host-without-administrator-privilege"></a><span data-ttu-id="6af58-178">在无管理员权限的情况下使用服务主机</span><span class="sxs-lookup"><span data-stu-id="6af58-178">Using Service Host without Administrator privilege</span></span>

<span data-ttu-id="6af58-179">若要使没有管理员权限的用户能够开发 WCF 服务，请在 http://+:8731/Design_Time_Addresses 安装 Visual Studio 的过程中为命名空间 "" 创建 ACL （访问控制列表）。</span><span class="sxs-lookup"><span data-stu-id="6af58-179">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="6af58-180">该 ACL 被设置为“(UI)”，这将包括登录到此计算机的所有交互用户。</span><span class="sxs-lookup"><span data-stu-id="6af58-180">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="6af58-181">管理员可以在此 ACL 中添加或删除用户，或者打开其他端口。此 ACL 使用户可以使用 WCF 服务自动主机（wcfSvcHost.exe），而无需授予其管理员权限。</span><span class="sxs-lookup"><span data-stu-id="6af58-181">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>

<span data-ttu-id="6af58-182">你可以使用提升的管理员帐户在 Windows Vista 中使用 netsh.exe 工具来修改访问权限。</span><span class="sxs-lookup"><span data-stu-id="6af58-182">You can modify access using the netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="6af58-183">下面是使用 netsh.exe 的示例。</span><span class="sxs-lookup"><span data-stu-id="6af58-183">The following is an example of using netsh.exe.</span></span>

```console
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>
```

<span data-ttu-id="6af58-184">有关 netsh.exe 的详细信息，请参阅 "[如何使用 Netsh.exe 工具和命令行开关](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))"。</span><span class="sxs-lookup"><span data-stu-id="6af58-184">For more information on netsh.exe, see "[How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10))".</span></span>

## <a name="see-also"></a><span data-ttu-id="6af58-185">请参阅</span><span class="sxs-lookup"><span data-stu-id="6af58-185">See also</span></span>

- [<span data-ttu-id="6af58-186">WCF 测试客户端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="6af58-186">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
