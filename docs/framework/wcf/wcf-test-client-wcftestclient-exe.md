---
title: WCF 测试客户端 (WcfTestClient.exe)
description: 了解 WCF 测试客户端，它提供与 WCF 服务主机组合时的无缝服务测试。 提交客户端测试值并查看服务响应。
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 4f636698c538809f89ee356159839a37b73adb57
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245656"
---
# <a name="wcf-test-client-wcftestclientexe"></a><span data-ttu-id="1ce10-104">WCF 测试客户端 (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="1ce10-104">WCF Test Client (WcfTestClient.exe)</span></span>
<span data-ttu-id="1ce10-105">Windows Communication Foundation （WCF）测试客户端（WcfTestClient.exe）是一个 GUI 工具，用户使用该工具可以输入测试参数、将该输入提交给服务并查看服务发回的响应。</span><span class="sxs-lookup"><span data-stu-id="1ce10-105">Windows Communication Foundation (WCF) Test Client (WcfTestClient.exe) is a GUI tool that enables users to input test parameters, submit that input to the service, and view the response that the service sends back.</span></span> <span data-ttu-id="1ce10-106">与 WCF 服务主机结合使用时，可以提供无缝的服务测试体验。</span><span class="sxs-lookup"><span data-stu-id="1ce10-106">It provides a seamless service testing experience when combined with WCF Service Host.</span></span>

<span data-ttu-id="1ce10-107">通常，你可以在以下位置找到 WCF 测试客户端（WcfTestClient.exe）： `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` -社区可以是 "企业"、"专业" 或 "社区" 中的一个，具体取决于安装的 Visual Studio 级别。</span><span class="sxs-lookup"><span data-stu-id="1ce10-107">You can typically find the WCF Test Client (WcfTestClient.exe) in the following location: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` - Community may be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed.</span></span>

## <a name="scenarios-for-using-test-client"></a><span data-ttu-id="1ce10-108">使用测试客户端的方案</span><span class="sxs-lookup"><span data-stu-id="1ce10-108">Scenarios for Using Test Client</span></span>

<span data-ttu-id="1ce10-109">以下各节讨论最常见的方案，在这些方案中，你可以使用 WCF 测试客户端来简化开发过程。</span><span class="sxs-lookup"><span data-stu-id="1ce10-109">The following sections discuss the most common scenarios in which you can use WCF Test Client to streamline your development process.</span></span>

### <a name="inside-visual-studio"></a><span data-ttu-id="1ce10-110">Visual Studio 内部</span><span class="sxs-lookup"><span data-stu-id="1ce10-110">Inside Visual Studio</span></span>

#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a><span data-ttu-id="1ce10-111">WCF 服务主机启动 WCF 测试客户端和一项服务</span><span class="sxs-lookup"><span data-stu-id="1ce10-111">WCF Service Host Starts WCF Test Client with a Single Service</span></span>

<span data-ttu-id="1ce10-112">创建新的 WCF 服务项目并按 F5 启动调试器后，WCF 服务主机会开始在项目中承载该服务。</span><span class="sxs-lookup"><span data-stu-id="1ce10-112">After you create a new WCF service project and press F5 to start the debugger, the WCF Service Host begins to host the service in your project.</span></span> <span data-ttu-id="1ce10-113">然后，WCF 测试客户端打开并显示在配置文件中定义的服务终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="1ce10-113">Then, WCF Test Client opens and displays a list of service endpoints defined in the configuration file.</span></span> <span data-ttu-id="1ce10-114">可以测试参数和调用服务，并可以重复此过程以继续测试和验证服务。</span><span class="sxs-lookup"><span data-stu-id="1ce10-114">You can test the parameters and invoke the service, and repeat this process to continuously test and validate your service.</span></span>

#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a><span data-ttu-id="1ce10-115">WCF 服务主机启动 WCF 测试客户端和多项服务</span><span class="sxs-lookup"><span data-stu-id="1ce10-115">WCF Service Host Starts WCF Test Client with Multiple Services</span></span>

<span data-ttu-id="1ce10-116">你还可以使用 WCF 测试客户端来帮助调试包含多个服务的服务项目。</span><span class="sxs-lookup"><span data-stu-id="1ce10-116">You can also use WCF Test Client to help debug a service project that contains multiple services.</span></span> <span data-ttu-id="1ce10-117">在 WCF 测试客户端打开时，它会自动在项目中循环访问服务列表，并将其打开以供测试。</span><span class="sxs-lookup"><span data-stu-id="1ce10-117">When WCF Test Client opens, it automatically iterates the list of services in your project and opens them for testing.</span></span>

### <a name="outside-visual-studio"></a><span data-ttu-id="1ce10-118">Visual Studio 外部</span><span class="sxs-lookup"><span data-stu-id="1ce10-118">Outside Visual Studio</span></span>

<span data-ttu-id="1ce10-119">你还可以在 Visual Studio 外部调用 WCF 测试客户端（WcfTestClient.exe）来测试 Internet 上的任意服务。</span><span class="sxs-lookup"><span data-stu-id="1ce10-119">You can also invoke the WCF Test Client (WcfTestClient.exe) outside Visual Studio to test an arbitrary service on the Internet.</span></span> <span data-ttu-id="1ce10-120">若要找到此工具，请转到以下位置：</span><span class="sxs-lookup"><span data-stu-id="1ce10-120">To locate the tool, go to the following location:</span></span>

<span data-ttu-id="1ce10-121">`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE`（其中，社区可以是 "企业"、"专业" 或 "社区" 中的一个，具体取决于计算机上安装的 Visual Studio 的级别）</span><span class="sxs-lookup"><span data-stu-id="1ce10-121">`C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (where community can be one of "Enterprise", "Professional" or "Community" depending on which level of Visual Studio is installed on the machine)</span></span>

<span data-ttu-id="1ce10-122">若要使用该工具，可以双击此文件名从该位置打开它，也可以从命令行启动它。</span><span class="sxs-lookup"><span data-stu-id="1ce10-122">To use the tool, double-click the file name to open it from this location, or launch it from a command line.</span></span>

<span data-ttu-id="1ce10-123">WCF 测试客户端使用任意数目的 Uri 作为命令行参数。</span><span class="sxs-lookup"><span data-stu-id="1ce10-123">WCF Test Client takes an arbitrary number of URIs as command line arguments.</span></span>  <span data-ttu-id="1ce10-124">这些 URI 是可以测试的服务的 URI。</span><span class="sxs-lookup"><span data-stu-id="1ce10-124">These are the URIs of services that can be tested.</span></span>

`wcfTestClient.exe URI1 URI2 …`

<span data-ttu-id="1ce10-125">在 "WCF 测试客户端" 窗口打开后，单击 "**文件**" -> "**添加服务**"，然后输入要打开的服务的终结点地址。</span><span class="sxs-lookup"><span data-stu-id="1ce10-125">After the WCF Test Client window is opened, click **File**->**Add Service**, and enter the endpoint address of the service you want to open.</span></span>

## <a name="wcf-test-client-user-interface"></a><span data-ttu-id="1ce10-126">WCF 测试客户端用户界面</span><span class="sxs-lookup"><span data-stu-id="1ce10-126">WCF Test Client User Interface</span></span>

<span data-ttu-id="1ce10-127">可以将 WCF 测试客户端用于单个服务或多个服务。</span><span class="sxs-lookup"><span data-stu-id="1ce10-127">You can use WCF Test Client with a single service or multiple services.</span></span>

### <a name="service-operations"></a><span data-ttu-id="1ce10-128">服务操作</span><span class="sxs-lookup"><span data-stu-id="1ce10-128">Service Operations</span></span>

<span data-ttu-id="1ce10-129">WCF 测试客户端主窗口的左窗格列出了所有可用的服务及其各自的终结点和操作。</span><span class="sxs-lookup"><span data-stu-id="1ce10-129">The left pane of the WCF Test Client main window lists all the available services, along with their respective endpoints and operations.</span></span>

<span data-ttu-id="1ce10-130">双击某个操作后，可以在具有此操作名称的新选项卡内的右窗格中查看其内容。</span><span class="sxs-lookup"><span data-stu-id="1ce10-130">When you double-click an operation, you can view its content in the right pane inside a new tab with the operation's name.</span></span>

<span data-ttu-id="1ce10-131">左窗格还列出了客户端配置文件。</span><span class="sxs-lookup"><span data-stu-id="1ce10-131">The left pane also lists client configuration files.</span></span> <span data-ttu-id="1ce10-132">双击任何项可以在新选项卡式窗口内的右窗格中显示文件的内容。</span><span class="sxs-lookup"><span data-stu-id="1ce10-132">Double-click any of the items to display the content of the file in a new tabbed window in the right pane.</span></span>

### <a name="entering-test-parameters"></a><span data-ttu-id="1ce10-133">输入测试参数</span><span class="sxs-lookup"><span data-stu-id="1ce10-133">Entering Test Parameters</span></span>

<span data-ttu-id="1ce10-134">若要查看测试参数，请双击某个操作以在右侧窗格中打开它。</span><span class="sxs-lookup"><span data-stu-id="1ce10-134">To view the test parameters, double-click an operation to open it in the right pane.</span></span> <span data-ttu-id="1ce10-135">默认情况下，在**格式化**视图中显示参数，您可以为参数输入任意值以测试服务。</span><span class="sxs-lookup"><span data-stu-id="1ce10-135">The parameters are showed in **Formatted** view by default, and you can enter arbitrary values for the parameters to test the service.</span></span>

<span data-ttu-id="1ce10-136">若要查看消息的 XML，请单击 " **xml**"。</span><span class="sxs-lookup"><span data-stu-id="1ce10-136">To view the message's XML, click **XML**.</span></span> <span data-ttu-id="1ce10-137">若要将其发送到服务，请单击 "**调用**"。</span><span class="sxs-lookup"><span data-stu-id="1ce10-137">To send them to the service, click **Invoke**.</span></span>

<span data-ttu-id="1ce10-138">对于数据集参数，请单击 **...**</span><span class="sxs-lookup"><span data-stu-id="1ce10-138">For a DataSet parameter, click the **…**</span></span> <span data-ttu-id="1ce10-139">按钮 "**编辑 ...** "</span><span class="sxs-lookup"><span data-stu-id="1ce10-139">button next to **Edit…**</span></span> <span data-ttu-id="1ce10-140">在显示数据网格的新窗口中进行编辑。</span><span class="sxs-lookup"><span data-stu-id="1ce10-140">to edit it in a new window showing the DataGrid.</span></span> <span data-ttu-id="1ce10-141">请注意 "**复制数据集**" 和 "**粘贴数据集**" 按钮的外观。</span><span class="sxs-lookup"><span data-stu-id="1ce10-141">Notice the appearance of the **Copy DataSet** and **Paste DataSet** buttons.</span></span> <span data-ttu-id="1ce10-142">如果第一次编辑时 DataSet 对象的架构未知，则 DataGrid 为空。</span><span class="sxs-lookup"><span data-stu-id="1ce10-142">If the schema of the DataSet object is unknown upon the first edit, the DataGrid is empty.</span></span> <span data-ttu-id="1ce10-143">您必须将具有相同架构的 DataSet 对象粘贴到 DataGrid 中的当前对象。</span><span class="sxs-lookup"><span data-stu-id="1ce10-143">You have to paste a DataSet object with the same schema into the current object in the DataGrid.</span></span> <span data-ttu-id="1ce10-144">（请注意，需要在粘贴操作之前从其他位置复制架构。）您还可以通过单击 "**复制数据集**" 按钮来复制 dataset 对象以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-144">(Notice that you need to copy the schema from somewhere else before the paste operation.) You can also copy a Dataset object for future usage by clicking the **Copy DataSet** button.</span></span>

<span data-ttu-id="1ce10-145">服务响应将出现在测试参数下面。</span><span class="sxs-lookup"><span data-stu-id="1ce10-145">The service's response appears below the test parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="1ce10-146">如果预期的返回值是字符串，则结果将显示为带引号的字符串，即使提供的输入未包含在引号中，也是如此。</span><span class="sxs-lookup"><span data-stu-id="1ce10-146">If the expected return value is a string, the result will be displayed as a quoted string even though the input provided was not in quotes.</span></span>

<span data-ttu-id="1ce10-147">如果在创建服务约定时将特定操作指定为单向操作，则不会显示服务响应。</span><span class="sxs-lookup"><span data-stu-id="1ce10-147">If you specified a particular operation as one-way when you created the contract for the service, no service response is displayed.</span></span> <span data-ttu-id="1ce10-148">消息一旦处于排队等待发送状态，则会弹出一个对话框，通知您已成功发送消息。</span><span class="sxs-lookup"><span data-stu-id="1ce10-148">As soon as the message is queued for delivery, a dialog box pops up to notify you that the message was successfully sent.</span></span>

### <a name="session-support"></a><span data-ttu-id="1ce10-149">会话支持</span><span class="sxs-lookup"><span data-stu-id="1ce10-149">Session Support</span></span>

<span data-ttu-id="1ce10-150">使用服务操作的选项卡中的 "**启动新的代理**" 复选框可以切换会话支持。</span><span class="sxs-lookup"><span data-stu-id="1ce10-150">The **Start a new proxy** check box in a service operation's tab enables you to toggle session support.</span></span> <span data-ttu-id="1ce10-151">默认情况下清除此框。</span><span class="sxs-lookup"><span data-stu-id="1ce10-151">This box is cleared by default.</span></span>

<span data-ttu-id="1ce10-152">如果为特定操作（或同一服务终结点中的另一个操作）输入测试参数，并单击 "多次**调用**" 并清除复选框，则这些操作将共享一个代理，并且服务状态在多个操作中保持不变。</span><span class="sxs-lookup"><span data-stu-id="1ce10-152">When you enter test parameters for a specific operation (or another operation in the same service endpoint) and click **Invoke** multiple times with the check box cleared, these operations share one proxy and the service status is persisted across multiple operations.</span></span>

<span data-ttu-id="1ce10-153">如果选中了 "**启动新的代理**" 复选框，则将为每个**调用**启动一个新的代理，上一个会话方案将结束，并且服务状态将重置。</span><span class="sxs-lookup"><span data-stu-id="1ce10-153">If the **Start a new proxy** check box is checked, a new proxy is started for each **Invoke**, the previous session scenario is ended, and the service status is reset.</span></span>

### <a name="editing-client-configuration"></a><span data-ttu-id="1ce10-154">编辑客户端配置</span><span class="sxs-lookup"><span data-stu-id="1ce10-154">Editing Client Configuration</span></span>

<span data-ttu-id="1ce10-155">WCF 测试客户端主窗口的左窗格列出了客户端配置文件。</span><span class="sxs-lookup"><span data-stu-id="1ce10-155">The left pane of the WCF Test Client main window lists client configuration files.</span></span> <span data-ttu-id="1ce10-156">双击任何项可以在右窗格中显示文件的内容。</span><span class="sxs-lookup"><span data-stu-id="1ce10-156">Double-click any of the items to display the contents of the file in the right pane.</span></span>

#### <a name="edit-with-service-configuration-editor"></a><span data-ttu-id="1ce10-157">使用服务配置编辑器进行编辑</span><span class="sxs-lookup"><span data-stu-id="1ce10-157">Edit with Service Configuration Editor</span></span>

<span data-ttu-id="1ce10-158">右键单击左窗格中的 "**配置文件**"，然后选择上下文菜单 "**编辑并 svcconfigeditor.exe**"。</span><span class="sxs-lookup"><span data-stu-id="1ce10-158">Right-click **Config File** in the left pane and select the context menu **Edit with SvcConfigEditor**.</span></span> <span data-ttu-id="1ce10-159">服务配置编辑器启动并显示客户端配置内容。</span><span class="sxs-lookup"><span data-stu-id="1ce10-159">Service Configuration Editor is launched with the client configuration content.</span></span> <span data-ttu-id="1ce10-160">可以编辑配置，然后将其保存在此工具中。</span><span class="sxs-lookup"><span data-stu-id="1ce10-160">You can edit the configuration and save it within the tool.</span></span>

<span data-ttu-id="1ce10-161">在服务配置编辑器中保存此文件后，WCF 测试客户端将显示一条警告消息，告知你该文件已在外部修改，并询问你是否要重新加载它。</span><span class="sxs-lookup"><span data-stu-id="1ce10-161">After saving the file in Service Configuration Editor, WCF Test Client displays a warning message to inform you that the file has been modified outside and asks whether you would like to reload it.</span></span>

<span data-ttu-id="1ce10-162">如果选择 "**是**"，则 "Client.dll.config" 选项卡中的配置内容将反映在编辑器中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="1ce10-162">If you select **Yes**, the configuration content in the "Client.dll.config" tab reflects the changes you made in the editor.</span></span>

<span data-ttu-id="1ce10-163">如果选择 "**否**"，则 "Client.dll.config" 选项卡中的配置内容将保持不变，并且已修改的内容会自动保存到源文件中。</span><span class="sxs-lookup"><span data-stu-id="1ce10-163">If you select **No**, the configuration content in the "Client.dll.config" tab remains unchanged and the modified content is automatically saved to the source file.</span></span>

#### <a name="restore-to-default-configuration"></a><span data-ttu-id="1ce10-164">还原到默认配置</span><span class="sxs-lookup"><span data-stu-id="1ce10-164">Restore to Default Configuration</span></span>

<span data-ttu-id="1ce10-165">如果要取消所有更改并还原到默认的客户端配置，请右键单击左窗格中的 "**配置文件**"，然后选择上下文菜单 "**还原到默认配置**"。将加载默认配置值，并还原 "Client.dll.config" 选项卡中的内容。</span><span class="sxs-lookup"><span data-stu-id="1ce10-165">If you want to cancel all the changes and restore to the default client configuration, right-click **Config File** in the left pane and select the context menu **Restore to Default Config**. The default configuration value is loaded and content in "Client.dll.config" tab is restored.</span></span>

#### <a name="validate-changes"></a><span data-ttu-id="1ce10-166">验证更改</span><span class="sxs-lookup"><span data-stu-id="1ce10-166">Validate Changes</span></span>

<span data-ttu-id="1ce10-167">在 WCF 测试客户端中加载保存的更改时，将根据 WCF 架构检查配置是否有效。</span><span class="sxs-lookup"><span data-stu-id="1ce10-167">When saved changes are being loaded in WCF Test Client, the configuration is checked for validity against WCF schema.</span></span> <span data-ttu-id="1ce10-168">如果发现错误，将显示一个对话框来给出错误详细信息。</span><span class="sxs-lookup"><span data-stu-id="1ce10-168">If errors are found, a dialog box is displayed to show error details.</span></span>

<span data-ttu-id="1ce10-169">在代理生成、二进制编译或服务调用期间，支持编辑的菜单项（即 "编辑 ..."、"还原 ..." 等）已禁用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-169">During proxy generation, binary compiling, or service invoking, menu items that support editing (that is, "Edit …", "Restore …", and so on) are disabled.</span></span> <span data-ttu-id="1ce10-170">在将更新的配置加载到 WCF 测试客户端时，也会禁用服务调用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-170">Service invocation is also disabled when loading updated configuration to WCF Test Client.</span></span>

#### <a name="persist-client-configuration"></a><span data-ttu-id="1ce10-171">使客户端配置保持不变</span><span class="sxs-lookup"><span data-stu-id="1ce10-171">Persist Client Configuration</span></span>

<span data-ttu-id="1ce10-172">"**工具** -> **选项** -> **客户端配置**" 选项卡包含 "**启动服务时始终重新生成配置**" 选项（默认情况下启用）。</span><span class="sxs-lookup"><span data-stu-id="1ce10-172">The **Tools**->**Options**->**Client Configuration** tab contains an **Always Regenerate Config When Launching Services** option, which is enabled by default.</span></span> <span data-ttu-id="1ce10-173">此选项指定每次 WCF 测试客户端加载服务时，它会根据最新的服务协定和服务 App.config 文件重新生成配置文件。</span><span class="sxs-lookup"><span data-stu-id="1ce10-173">This option specifies that every time WCF Test Client loads a service, it regenerates a configuration file based on the latest service contract and service App.config files.</span></span>

<span data-ttu-id="1ce10-174">如果已编辑 WCF 服务的客户端配置并希望始终使用此更新的文件来调试服务，则可以取消选中 "**重新生成**" 选项。</span><span class="sxs-lookup"><span data-stu-id="1ce10-174">If you have edited the client configuration for your WCF service and want to always use this updated file to debug your service, you can uncheck the **Regenerate** option.</span></span> <span data-ttu-id="1ce10-175">这样，即使在更新服务并重新打开 WCF 测试客户端时，Client.dll.config 文件也是您以前更新的文件，而不是根据更新后的服务重新生成的文件。</span><span class="sxs-lookup"><span data-stu-id="1ce10-175">By doing so, even when you update the service and reopen WCF Test Client, the Client.dll.config file is the one you updated previously instead of a regenerated one based on the updated service.</span></span>

<span data-ttu-id="1ce10-176">但是，您可能需要编辑此配置文件以使其与重新生成的代理一致。</span><span class="sxs-lookup"><span data-stu-id="1ce10-176">However, you might need to edit the configuration file to make it consistent with the regenerated proxy.</span></span> <span data-ttu-id="1ce10-177">如果由于更新了服务而导致重新生成的代理与配置文件不匹配，则调用该服务时将出错。</span><span class="sxs-lookup"><span data-stu-id="1ce10-177">If the regenerated proxy and configuration file are mismatched due to an updated service, errors will occur when the service is invoked.</span></span>

> [!CAUTION]
> <span data-ttu-id="1ce10-178">如果您已修改了客户端配置文件并选择以后再使用它，则可以在以下位置找到此文件：</span><span class="sxs-lookup"><span data-stu-id="1ce10-178">If you have modified the client configuration file and select to reuse it in the future, you can find the file in the following location:</span></span>
>
> <span data-ttu-id="1ce10-179">\Documents 和 Settings \\ [用户帐户] \My Documents\Test 客户端项目。</span><span class="sxs-lookup"><span data-stu-id="1ce10-179">\Documents and Settings\\[User Account]\My Documents\Test Client Projects.</span></span>
>
> <span data-ttu-id="1ce10-180">任何存储到客户端配置文件的已更新的凭据信息都是由此文件夹的访问控制列表 (ACL) 保护的。</span><span class="sxs-lookup"><span data-stu-id="1ce10-180">Any updated credential information stored to the client configuration file is protected by the Access Control List (ACL) of this folder.</span></span>

### <a name="adding-removing-and-refreshing-services"></a><span data-ttu-id="1ce10-181">添加、删除和刷新服务</span><span class="sxs-lookup"><span data-stu-id="1ce10-181">Adding, Removing and Refreshing Services</span></span>

#### <a name="add-service"></a><span data-ttu-id="1ce10-182">添加服务</span><span class="sxs-lookup"><span data-stu-id="1ce10-182">Add Service</span></span>

<span data-ttu-id="1ce10-183">单击 "**文件**" " -> **添加服务**" 将服务添加到 WCF 测试客户端。</span><span class="sxs-lookup"><span data-stu-id="1ce10-183">Click **File**->**Add Service** to add a service to WCF Test Client.</span></span> <span data-ttu-id="1ce10-184">然后您需要键入要添加的服务的 URI（终结点地址）。</span><span class="sxs-lookup"><span data-stu-id="1ce10-184">You are then required to type the URI (endpoint address) of the service to be added.</span></span> <span data-ttu-id="1ce10-185">该服务的地址可以是 mex 地址，也可以是 WSDL 地址。</span><span class="sxs-lookup"><span data-stu-id="1ce10-185">The service’s address can be a mex address or WSDL address.</span></span>

<span data-ttu-id="1ce10-186">你还可以在 "**最近使用的服务**" 子菜单中找到10个最近添加的服务终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="1ce10-186">You can also find a list of 10 recently added services' endpoints in the **Recent Services** submenu.</span></span> <span data-ttu-id="1ce10-187">如果选择其中一个，则会将指定的服务添加到 WCF 测试客户端。</span><span class="sxs-lookup"><span data-stu-id="1ce10-187">If you select one of them, the specified service is added to WCF Test Client.</span></span>

<span data-ttu-id="1ce10-188">您还可以右键单击服务树的根服务**项目**，然后选择 "**添加服务**" 以获得相同的结果。</span><span class="sxs-lookup"><span data-stu-id="1ce10-188">You can also right-click the root of service tree **My Service Projects**, and select **Add Service** to achieve the same result.</span></span>

<span data-ttu-id="1ce10-189">在代理生成、二进制编译或服务调用期间，支持添加服务的菜单项被禁用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-189">During proxy generation, binary compiling, or service invocation, menu items that support adding a service are disabled.</span></span> <span data-ttu-id="1ce10-190">服务调用也被禁用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-190">Service invocation is also disabled.</span></span>

#### <a name="remove-service"></a><span data-ttu-id="1ce10-191">移除服务</span><span class="sxs-lookup"><span data-stu-id="1ce10-191">Remove Service</span></span>

<span data-ttu-id="1ce10-192">右键单击要删除的服务的根服务，然后选择 "**删除服务**" 以从 WCF 测试客户端中删除服务。</span><span class="sxs-lookup"><span data-stu-id="1ce10-192">Right-click the service root of the service to be removed, and select **Remove Service** to remove a service from WCF Test Client.</span></span>

<span data-ttu-id="1ce10-193">在代理生成、二进制编译或服务调用期间，支持删除服务的菜单项被禁用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-193">During proxy generation, binary compiling, or service invocation, menu items that support removing a service are disabled.</span></span> <span data-ttu-id="1ce10-194">服务调用也被禁用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-194">Service invocation is also disabled.</span></span>

#### <a name="refresh-service"></a><span data-ttu-id="1ce10-195">刷新服务</span><span class="sxs-lookup"><span data-stu-id="1ce10-195">Refresh Service</span></span>

<span data-ttu-id="1ce10-196">如果在 WCF 测试客户端运行期间对服务进行了更改，并且想要确保该服务的 WCF 测试客户端实现是最新的，请右键单击该服务的根服务，然后选择 "**刷新服务**"。</span><span class="sxs-lookup"><span data-stu-id="1ce10-196">If a change is made to the service while WCF Test Client is running and you want to ensure that the WCF Test Client implementation for that service is up-to-date, right-click the service root of the service, and select **Refresh Service**.</span></span> <span data-ttu-id="1ce10-197">请注意，刷新后服务状态将重置。</span><span class="sxs-lookup"><span data-stu-id="1ce10-197">Note that after refreshing, the service status is reset.</span></span>

<span data-ttu-id="1ce10-198">在代理生成、二进制编译或服务调用期间，支持刷新服务的菜单项被禁用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-198">During proxy generation, binary compiling, or service invocation, menu items that support refreshing a service are disabled.</span></span> <span data-ttu-id="1ce10-199">服务调用也被禁用。</span><span class="sxs-lookup"><span data-stu-id="1ce10-199">Service invocation is also disabled.</span></span>

## <a name="location-of-files-generated-by-the-test-client"></a><span data-ttu-id="1ce10-200">测试客户端生成的文件的位置</span><span class="sxs-lookup"><span data-stu-id="1ce10-200">Location of Files Generated by the Test Client</span></span>

<span data-ttu-id="1ce10-201">默认情况下，WCF 测试客户端将生成的客户端代码和配置文件存储在 "%Appdata%\local\temp\test client projects 客户端项目" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="1ce10-201">By default, WCF Test Client stores generated client code and configuration files in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span> <span data-ttu-id="1ce10-202">在 WCF 测试客户端退出后删除此文件夹。</span><span class="sxs-lookup"><span data-stu-id="1ce10-202">This folder is deleted after WCF Test Client exits.</span></span> <span data-ttu-id="1ce10-203">如果在 WCF 测试客户端中修改了某个配置文件，并且禁用了 "**启动服务时始终重新生成配置**" 选项，则已修改的文件将复制到 "我的 Documents\Test 客户端项目" 下的 "CachedConfig" 文件夹中，并将映射（元数据地址到文件名称） XML 文件作为索引。</span><span class="sxs-lookup"><span data-stu-id="1ce10-203">If a configuration file is modified in WCF Test Client and the **Always Regenerate Config When Launching Services** option is disabled, the modified file is copied to the "CachedConfig" folder under "My Documents\Test Client Projects" with a mapping (metadata-address-to-file-name) XML file as an index.</span></span>

<span data-ttu-id="1ce10-204">你还可以在命令行中启动 WCF 测试客户端，使用 `/ProjectPath` 开关指定新的所需路径来存储生成的文件，或者使用 `/RestoreProjectPath` 开关还原默认位置。</span><span class="sxs-lookup"><span data-stu-id="1ce10-204">You can also start WCF Test Client in a command line, use the `/ProjectPath` switch to specify a new desired path for storing generated files, or use the `/RestoreProjectPath` switch to restore the default location.</span></span> <span data-ttu-id="1ce10-205">语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="1ce10-205">The syntax is as follows:</span></span>

`wcfTestClient.exe /ProjectPath [desired location]`

<span data-ttu-id="1ce10-206">运行此命令不会打开 WCF 测试客户端。</span><span class="sxs-lookup"><span data-stu-id="1ce10-206">Running this command does not open WCF Test Client.</span></span> <span data-ttu-id="1ce10-207">而只会更改文件夹位置。</span><span class="sxs-lookup"><span data-stu-id="1ce10-207">Only the folder location is changed.</span></span> <span data-ttu-id="1ce10-208">您可以运行此命令，而不管 WCF 测试客户端是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="1ce10-208">You can run this command whether WCF Test Client is running or not.</span></span> <span data-ttu-id="1ce10-209">重新启动 WCF 测试客户端时，将应用新位置。</span><span class="sxs-lookup"><span data-stu-id="1ce10-209">The new location is applied when WCF Test Client is restarted.</span></span> <span data-ttu-id="1ce10-210">位置信息可以保存在注册表中，也可以保存在 "%Appdata%\local\temp\test client projects 客户端项目" 文件夹中的 WcfTestClient.exe。</span><span class="sxs-lookup"><span data-stu-id="1ce10-210">The location information can be saved in registry, or in the WcfTestClient.exe.option file in the "%appdata%\Local\temp\Test Client Projects" folder.</span></span>

## <a name="features-supported-by-wcf-test-client"></a><span data-ttu-id="1ce10-211">WCF 测试客户端支持的功能</span><span class="sxs-lookup"><span data-stu-id="1ce10-211">Features supported by WCF Test Client</span></span>

<span data-ttu-id="1ce10-212">以下是 WCF 测试客户端支持的功能列表：</span><span class="sxs-lookup"><span data-stu-id="1ce10-212">The following is a list of features supported by WCF Test Client:</span></span>

- <span data-ttu-id="1ce10-213">服务调用：请求/响应和单向消息。</span><span class="sxs-lookup"><span data-stu-id="1ce10-213">Service Invocation: Request/Response and One-way message.</span></span>

- <span data-ttu-id="1ce10-214">绑定：Svcutil.exe 支持的所有绑定。</span><span class="sxs-lookup"><span data-stu-id="1ce10-214">Bindings: all bindings supported by Svcutil.exe.</span></span>

- <span data-ttu-id="1ce10-215">控制会话。</span><span class="sxs-lookup"><span data-stu-id="1ce10-215">Controlling Session.</span></span>

- <span data-ttu-id="1ce10-216">消息协定。</span><span class="sxs-lookup"><span data-stu-id="1ce10-216">Message Contract.</span></span>

- <span data-ttu-id="1ce10-217">XML 序列化。</span><span class="sxs-lookup"><span data-stu-id="1ce10-217">XML serialization.</span></span>

<span data-ttu-id="1ce10-218">以下是 WCF 测试客户端不支持的功能的列表：</span><span class="sxs-lookup"><span data-stu-id="1ce10-218">The following is a list of features not supported by WCF Test Client:</span></span>

- <span data-ttu-id="1ce10-219">类型：<xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message>、<xref:System.Xml.XmlElement>、<xref:System.Xml.XmlAttribute>、<xref:System.Xml.XmlNode>、实现 <xref:System.Xml.Serialization.IXmlSerializable> 接口的类型（包括相关 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 特性）、<xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 类型以及 ADO.NET <xref:System.Data.DataTable> 类型。</span><span class="sxs-lookup"><span data-stu-id="1ce10-219">Types: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, types that implement the <xref:System.Xml.Serialization.IXmlSerializable> interface, including the related <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribute, and the <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> types and the ADO.NET <xref:System.Data.DataTable> type.</span></span>

- <span data-ttu-id="1ce10-220">双工协定。</span><span class="sxs-lookup"><span data-stu-id="1ce10-220">Duplex contract.</span></span>

- <span data-ttu-id="1ce10-221">事务。</span><span class="sxs-lookup"><span data-stu-id="1ce10-221">Transaction.</span></span>

- <span data-ttu-id="1ce10-222">安全性： CardSpace、证书和用户名/密码。</span><span class="sxs-lookup"><span data-stu-id="1ce10-222">Security: CardSpace , Certificate, and Username/Password.</span></span>

- <span data-ttu-id="1ce10-223">绑定：WSFederationbinding、任何上下文绑定和 Https 绑定、WebHttpbinding（Json 响应消息支持）。</span><span class="sxs-lookup"><span data-stu-id="1ce10-223">Bindings: WSFederationbinding, any Context bindings and Https binding, WebHttpbinding (Json response message support).</span></span>

## <a name="closing-wcf-test-client"></a><span data-ttu-id="1ce10-224">关闭 WCF 测试客户端</span><span class="sxs-lookup"><span data-stu-id="1ce10-224">Closing WCF Test Client</span></span>

<span data-ttu-id="1ce10-225">可以通过以下方式关闭 WCF 测试客户端：</span><span class="sxs-lookup"><span data-stu-id="1ce10-225">You can close WCF Test Client in the following ways:</span></span>

- <span data-ttu-id="1ce10-226">在 **“文件”** 菜单中，单击 **“退出”**。</span><span class="sxs-lookup"><span data-stu-id="1ce10-226">On the **File** menu, click **Exit**.</span></span> <span data-ttu-id="1ce10-227">或者，在 WCF 测试客户端主窗口中，单击 "**关闭**"。</span><span class="sxs-lookup"><span data-stu-id="1ce10-227">Alternatively, in the WCF Test Client main window, click **Close**.</span></span> <span data-ttu-id="1ce10-228">这两个操作还会关闭 WCF 服务自动主机，并在 Visual Studio 启动 WCF 测试客户端时停止 Visual Studio 调试过程。</span><span class="sxs-lookup"><span data-stu-id="1ce10-228">Both of these actions also shut down WCF Service Auto Host and stop the Visual Studio debugging process if WCF Test Client was launched by Visual Studio.</span></span>

- <span data-ttu-id="1ce10-229">右键单击通知区域中的 " **WCF 服务主机**" 图标，然后单击 "**退出"。**</span><span class="sxs-lookup"><span data-stu-id="1ce10-229">Right-click the **WCF Service Host** icon in the notification area, and then click **Exit.**</span></span> <span data-ttu-id="1ce10-230">这会关闭 WCF 服务自动主机和 WCF 测试客户端，并停止 Visual Studio 调试过程。</span><span class="sxs-lookup"><span data-stu-id="1ce10-230">This shuts down both WCF Service Auto Host and WCF Test Client and stops the Visual Studio debugging process.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ce10-231">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ce10-231">See also</span></span>

- [<span data-ttu-id="1ce10-232">WCF 服务主机 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="1ce10-232">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
