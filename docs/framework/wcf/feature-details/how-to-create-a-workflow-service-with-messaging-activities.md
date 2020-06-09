---
title: 如何：使用消息传递活动创建工作流服务
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: b4991fc9f8a6c45cae3943f1506247c42ed2b30b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597119"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a><span data-ttu-id="d0634-102">如何：使用消息传递活动创建工作流服务</span><span class="sxs-lookup"><span data-stu-id="d0634-102">How to: Create a Workflow Service with Messaging Activities</span></span>
<span data-ttu-id="d0634-103">此主题说明如何使用消息传递活动创建简单工作流服务，</span><span class="sxs-lookup"><span data-stu-id="d0634-103">This topic describes how to create a simple workflow service using messaging activities.</span></span> <span data-ttu-id="d0634-104">本主题着重介绍工作流服务的创建机制，其中的服务仅包含消息传递活动。</span><span class="sxs-lookup"><span data-stu-id="d0634-104">This topic focuses on the mechanics of creating a workflow service where the service consists solely of messaging activities.</span></span> <span data-ttu-id="d0634-105">在实际服务中，工作流包含其他许多活动。</span><span class="sxs-lookup"><span data-stu-id="d0634-105">In a real-world service, the workflow contains many other activities.</span></span> <span data-ttu-id="d0634-106">该服务实现一个名为 Echo 的操作，来获取一个字符串并将该字符串返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="d0634-106">The service implements one operation called Echo, which takes a string and returns the string to the caller.</span></span> <span data-ttu-id="d0634-107">本主题是一系列主题（包含两个主题）中的第一个。</span><span class="sxs-lookup"><span data-stu-id="d0634-107">This topic is the first in a series of two topics.</span></span> <span data-ttu-id="d0634-108">下一主题[如何：从工作流应用程序访问服务](how-to-access-a-service-from-a-workflow-application.md)讨论如何创建可以调用在本主题中创建的服务的工作流应用程序。</span><span class="sxs-lookup"><span data-stu-id="d0634-108">The next topic [How To: Access a Service From a Workflow Application](how-to-access-a-service-from-a-workflow-application.md) discusses how to create a workflow application that can call the service created in this topic.</span></span>  
  
### <a name="to-create-a-workflow-service-project"></a><span data-ttu-id="d0634-109">创建工作流服务项目</span><span class="sxs-lookup"><span data-stu-id="d0634-109">To create a workflow service project</span></span>  
  
1. <span data-ttu-id="d0634-110">启动 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="d0634-110">Start Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="d0634-111">单击 "**文件**" 菜单，选择 "**新建**"，然后单击 "**项目**" 以显示 "**新建项目" 对话框**。</span><span class="sxs-lookup"><span data-stu-id="d0634-111">Click the **File** menu, select **New**, and then **Project** to display the **New Project Dialog**.</span></span> <span data-ttu-id="d0634-112">从项目类型列表中，选择已安装模板列表中的 "**工作流**" 和 " **WCF 工作流服务应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="d0634-112">Select **Workflow** from the list of installed templates and **WCF Workflow Service Application** from the list of project types.</span></span> <span data-ttu-id="d0634-113">将项目命名 `MyWFService` 为，并使用默认位置，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-113">Name the project `MyWFService` and use the default location as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="d0634-114">单击 **"确定"** 按钮以关闭 "**新建项目" 对话框**。</span><span class="sxs-lookup"><span data-stu-id="d0634-114">Click the **OK** button to dismiss the **New Project Dialog**.</span></span>  
  
3. <span data-ttu-id="d0634-115">创建项目之后，将在设计器中打开 Service1.xamlx 文件，如以下插图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-115">When the project is created, the Service1.xamlx file is opened in the designer as shown in the following illustration.</span></span>  
  
     ![屏幕截图显示设计器中的 open Service1. .xamlx 文件。](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     <span data-ttu-id="d0634-117">右键单击标记为 "**顺序服务**" 的活动，然后选择 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="d0634-117">Right-click the activity labeled **Sequential Service** and select **Delete**.</span></span>  
  
### <a name="to-implement-the-workflow-service"></a><span data-ttu-id="d0634-118">实现工作流服务</span><span class="sxs-lookup"><span data-stu-id="d0634-118">To implement the workflow service</span></span>  
  
1. <span data-ttu-id="d0634-119">选择屏幕左侧的 "**工具箱**" 选项卡以显示 "工具箱"，然后单击图钉使窗口保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="d0634-119">Select the **Toolbox** tab on the left side of the screen to display the toolbox and click the pushpin to keep the window open.</span></span> <span data-ttu-id="d0634-120">展开 "工具箱" 的 "**消息传送**" 部分以显示消息传递活动和消息传递活动模板，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-120">Expand the **Messaging** section of the toolbox to display the messaging activities and the messaging activity templates as shown in the following illustration.</span></span>  
  
     ![显示已展开消息传递部分的工具箱的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. <span data-ttu-id="d0634-122">将**ReceiveAndSendReply**模板拖放到工作流设计器中。</span><span class="sxs-lookup"><span data-stu-id="d0634-122">Drag and drop a **ReceiveAndSendReply** template to the workflow designer.</span></span> <span data-ttu-id="d0634-123">这会创建一个 <xref:System.Activities.Statements.Sequence> 活动，其中包含一个**接收**活动，后跟一个 <xref:System.ServiceModel.Activities.SendReply> 活动，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-123">This creates a <xref:System.Activities.Statements.Sequence> activity with a **Receive** activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity as shown in the following illustration.</span></span>  
  
     ![显示 ReceiveAndSendReply 模板的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     <span data-ttu-id="d0634-125">请注意，已将 <xref:System.ServiceModel.Activities.SendReply> 活动的<xref:System.ServiceModel.Activities.SendReply.Request%2A> 属性设置为 `Receive`，即<xref:System.ServiceModel.Activities.Receive> 活动要答复的<xref:System.ServiceModel.Activities.SendReply> 活动的名称。</span><span class="sxs-lookup"><span data-stu-id="d0634-125">Notice that the <xref:System.ServiceModel.Activities.SendReply> activity’s <xref:System.ServiceModel.Activities.SendReply.Request%2A> property is set to `Receive`, the name of the <xref:System.ServiceModel.Activities.Receive> activity to which the <xref:System.ServiceModel.Activities.SendReply> activity is replying.</span></span>  
  
3. <span data-ttu-id="d0634-126">在 " <xref:System.ServiceModel.Activities.Receive> 活动类型" 文本框中， `Echo` 将其标记为**OperationName**。</span><span class="sxs-lookup"><span data-stu-id="d0634-126">In the <xref:System.ServiceModel.Activities.Receive> activity type `Echo` into the textbox labeled **OperationName**.</span></span> <span data-ttu-id="d0634-127">此步骤定义服务所实现操作的名称。</span><span class="sxs-lookup"><span data-stu-id="d0634-127">This defines the name of the operation the service implements.</span></span>  
  
     ![显示要指定操作名称的位置的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. <span data-ttu-id="d0634-129"><xref:System.ServiceModel.Activities.Receive>选定活动后，单击 "**视图**" 菜单并选择 "**属性窗口**"，打开 "属性" 窗口（如果尚未打开）。</span><span class="sxs-lookup"><span data-stu-id="d0634-129">With the <xref:System.ServiceModel.Activities.Receive> activity selected, open the properties window if not already open by clicking the **View** menu and selecting **Properties Window**.</span></span> <span data-ttu-id="d0634-130">在 "**属性" 窗口**中向下滚动，直到看到 " **CanCreateInstance** "，然后单击相应的复选框，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-130">In the **Properties Window** scroll down until you see **CanCreateInstance** and click the checkbox as shown in the following illustration.</span></span> <span data-ttu-id="d0634-131">此设置使工作流服务主机可以在接收消息时创建服务的新实例（如果需要）。</span><span class="sxs-lookup"><span data-stu-id="d0634-131">This setting enables the workflow service host to create a new instance of the service (if needed) when a message is received.</span></span>  
  
     ![显示 CanCreateInstance 属性的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. <span data-ttu-id="d0634-133">选择 <xref:System.Activities.Statements.Sequence> 活动，然后单击设计器左下角的 "**变量**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="d0634-133">Select the <xref:System.Activities.Statements.Sequence> activity and click the **Variables** button in the lower left corner of the designer.</span></span> <span data-ttu-id="d0634-134">这样将显示变量编辑器。</span><span class="sxs-lookup"><span data-stu-id="d0634-134">This displays the variables editor.</span></span> <span data-ttu-id="d0634-135">单击 "**创建变量**" 链接，添加用于存储发送到操作的字符串的变量。</span><span class="sxs-lookup"><span data-stu-id="d0634-135">Click the **Create Variable** link to add a variable to store the string sent to the operation.</span></span> <span data-ttu-id="d0634-136">将变量命名为 `msg` ，并将其**变量**类型设置为字符串，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-136">Name the variable `msg` and set its **Variable** type to String as shown in the following illustration.</span></span>  
  
     ![显示如何添加变量的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     <span data-ttu-id="d0634-138">再次单击 "**变量**" 按钮以关闭 "变量编辑器"。</span><span class="sxs-lookup"><span data-stu-id="d0634-138">Click the **Variables** button again to close the variables editor.</span></span>  
  
6. <span data-ttu-id="d0634-139">单击 "**定义"。**</span><span class="sxs-lookup"><span data-stu-id="d0634-139">Click the **Define..**</span></span> <span data-ttu-id="d0634-140">链接 **，以** <xref:System.ServiceModel.Activities.Receive> 显示 "**内容定义**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="d0634-140">link in the **Content** text box in the <xref:System.ServiceModel.Activities.Receive> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="d0634-141">选择 "**参数**" 单选按钮，单击 "**添加新参数**" 链接， `inMsg` 在 "**名称**" 文本框中键入，在 "**类型**" 下拉列表框中选择 "**字符串**"，然后 `msg` 在 "**分配到**" 文本框中键入，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-141">Select the **Parameters** radio button, click the **Add new Parameter** link, type `inMsg` in the **name** text box, select **String** in the **Type** drop down list box, and type `msg` in the **Assign To** text box as shown in the following illustration.</span></span>  
  
     ![显示添加参数内容的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     <span data-ttu-id="d0634-143">此步骤指定由 Receive 活动接收字符串参数，并且将该数据绑定到 `msg` 变量。</span><span class="sxs-lookup"><span data-stu-id="d0634-143">This specifies that the Receive activity receives string parameter and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="d0634-144">单击 **"确定"** 以关闭 "**内容定义**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="d0634-144">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
7. <span data-ttu-id="d0634-145">单击活动的 "**内容**" 框中的 "**定义 ...** " 链接 <xref:System.ServiceModel.Activities.SendReply> ，以显示 "**内容定义**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="d0634-145">Click the **Define...** link in the **Content** box in the <xref:System.ServiceModel.Activities.SendReply> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="d0634-146">选择 "**参数**" 单选按钮，单击 "**添加新参数**" 链接，在 " `outMsg` **名称**" 文本框中键入，在 "**类型**" 下拉列表框中选择 "**字符串**"，然后在 " `msg` **值**" 文本框中显示，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-146">Select the **Parameters** radio button, click the **Add new Parameter** link, type `outMsg` in the **name** textbox, select **String** in the **Type** dropdown list box, and `msg` in the **Value** text box as shown in the following illustration.</span></span>  
  
     ![显示如何添加 outMsg 参数的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     <span data-ttu-id="d0634-148">此步骤指定由 <xref:System.ServiceModel.Activities.SendReply> 活动发送消息或消息协定类型，并且将该数据绑定到 `msg` 变量。</span><span class="sxs-lookup"><span data-stu-id="d0634-148">This specifies that the <xref:System.ServiceModel.Activities.SendReply> activity sends a message or message contract type and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="d0634-149">由于此活动是 <xref:System.ServiceModel.Activities.SendReply> 活动，因此这意味着 `msg` 中的数据用于填充活动发送回客户端的消息。</span><span class="sxs-lookup"><span data-stu-id="d0634-149">Because this is a <xref:System.ServiceModel.Activities.SendReply> activity, this means the data in `msg` is used to populate the message the activity sends back to the client.</span></span> <span data-ttu-id="d0634-150">单击 **"确定"** 以关闭 "**内容定义**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="d0634-150">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
8. <span data-ttu-id="d0634-151">单击 "**生成**" 菜单并选择 "**生成解决方案**"，保存并生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="d0634-151">Save and build the solution by clicking the **Build** menu and selecting **Build Solution**.</span></span>  
  
## <a name="configure-the-workflow-service-project"></a><span data-ttu-id="d0634-152">配置工作流服务项目</span><span class="sxs-lookup"><span data-stu-id="d0634-152">Configure the Workflow Service Project</span></span>  
 <span data-ttu-id="d0634-153">现在工作流服务是完整的。</span><span class="sxs-lookup"><span data-stu-id="d0634-153">The workflow service is complete.</span></span> <span data-ttu-id="d0634-154">本节介绍如何配置工作流服务解决方案以易于承载和运行。</span><span class="sxs-lookup"><span data-stu-id="d0634-154">This section explains how to configure the workflow service solution to make it easy to host and run.</span></span> <span data-ttu-id="d0634-155">此解决方案使用 ASP.NET Development Server 承载服务。</span><span class="sxs-lookup"><span data-stu-id="d0634-155">This solution uses the ASP.NET Development Server to host the service.</span></span>  
  
#### <a name="to-set-project-start-up-options"></a><span data-ttu-id="d0634-156">设置项目启动选项</span><span class="sxs-lookup"><span data-stu-id="d0634-156">To set project start up options</span></span>  
  
1. <span data-ttu-id="d0634-157">在**解决方案资源管理器**中，右键单击**MyWFService** ，然后选择 "**属性**" 以显示 "**项目属性**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="d0634-157">In the **Solution Explorer**, right-click **MyWFService** and select **Properties** to display the **Project Properties** dialog.</span></span>  
  
2. <span data-ttu-id="d0634-158">选择 " **Web** " 选项卡，选择 "**启动操作**" 下的**特定页面**，然后 `Service1.xamlx` 在文本框中键入，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-158">Select the **Web** tab and select **Specific Page** under **Start Action** and type `Service1.xamlx` in the text box as shown in the following illustration.</span></span>  
  
     ![显示 "项目属性" 对话框的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     <span data-ttu-id="d0634-160">此步骤在 ASP.NET Development Server 中承载 Service1.xamlx 中定义的服务。</span><span class="sxs-lookup"><span data-stu-id="d0634-160">This hosts the service defined in Service1.xamlx in the ASP.NET Development Server.</span></span>  
  
3. <span data-ttu-id="d0634-161">按 Ctrl + F5 启动服务。</span><span class="sxs-lookup"><span data-stu-id="d0634-161">Press Ctrl + F5 to launch the service.</span></span> <span data-ttu-id="d0634-162">ASP.NET Development Server 图标显示在桌面的右下角，如以下图像所示。</span><span class="sxs-lookup"><span data-stu-id="d0634-162">The ASP.NET Development Server icon is displayed in the lower right side of the desktop as shown in the following image.</span></span>  
  
     ![显示 ASP.NET 开发人员服务器图标的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     <span data-ttu-id="d0634-164">此外，Internet Explorer 显示服务的 WCF 服务帮助页。</span><span class="sxs-lookup"><span data-stu-id="d0634-164">In addition, Internet Explorer displays the WCF Service Help Page for the service.</span></span>  
  
     ![显示 "WCF 服务帮助" 页的屏幕截图。](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. <span data-ttu-id="d0634-166">继续[学习如何：从工作流应用程序访问服务](how-to-access-a-service-from-a-workflow-application.md)主题来创建调用此服务的工作流客户端。</span><span class="sxs-lookup"><span data-stu-id="d0634-166">Continue on to the [How To: Access a Service From a Workflow Application](how-to-access-a-service-from-a-workflow-application.md) topic to create a workflow client that calls this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0634-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0634-167">See also</span></span>

- [<span data-ttu-id="d0634-168">工作流服务</span><span class="sxs-lookup"><span data-stu-id="d0634-168">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="d0634-169">承载工作流服务概述</span><span class="sxs-lookup"><span data-stu-id="d0634-169">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [<span data-ttu-id="d0634-170">消息传递活动</span><span class="sxs-lookup"><span data-stu-id="d0634-170">Messaging Activities</span></span>](messaging-activities.md)
