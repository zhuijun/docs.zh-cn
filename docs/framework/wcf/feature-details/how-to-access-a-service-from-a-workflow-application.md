---
title: 如何：从工作流应用程序访问服务
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 2ce79b726b623c2a25bf14065682e685455ca575
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597236"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a><span data-ttu-id="56c6d-102">如何：从工作流应用程序访问服务</span><span class="sxs-lookup"><span data-stu-id="56c6d-102">How To: Access a Service From a Workflow Application</span></span>
<span data-ttu-id="56c6d-103">本主题说明如何从工作流控制台应用程序调用工作流服务。</span><span class="sxs-lookup"><span data-stu-id="56c6d-103">This topic describes how to call a workflow service from a workflow console application.</span></span> <span data-ttu-id="56c6d-104">具体取决于[如何：使用消息传递活动创建工作流服务](how-to-create-a-workflow-service-with-messaging-activities.md)主题。</span><span class="sxs-lookup"><span data-stu-id="56c6d-104">It depends on completion of the [How to: Create a Workflow Service with Messaging Activities](how-to-create-a-workflow-service-with-messaging-activities.md) topic.</span></span> <span data-ttu-id="56c6d-105">尽管本主题介绍如何从工作流应用程序调用工作流服务，但也可以使用相同的方法从工作流应用程序调用任何 Windows Communication Foundation （WCF）服务。</span><span class="sxs-lookup"><span data-stu-id="56c6d-105">Although this topic describes how to call a workflow service from a workflow application, the same methods can be used to call any Windows Communication Foundation (WCF) service from a workflow application.</span></span>

### <a name="create-a-workflow-console-application-project"></a><span data-ttu-id="56c6d-106">创建工作流控制台应用程序项目</span><span class="sxs-lookup"><span data-stu-id="56c6d-106">Create a Workflow Console Application Project</span></span>

1. <span data-ttu-id="56c6d-107">启动 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="56c6d-107">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="56c6d-108">加载在[如何：创建包含消息传递活动的工作流服务](how-to-create-a-workflow-service-with-messaging-activities.md)主题中创建的 MyWFService 项目。</span><span class="sxs-lookup"><span data-stu-id="56c6d-108">Load the MyWFService project you created in the [How to: Create a Workflow Service with Messaging Activities](how-to-create-a-workflow-service-with-messaging-activities.md) topic.</span></span>

3. <span data-ttu-id="56c6d-109">在**解决方案资源管理器**中右键单击 " **MyWFService** " 解决方案，然后选择 "**添加**"、"**新建项目**"。</span><span class="sxs-lookup"><span data-stu-id="56c6d-109">Right click the **MyWFService** solution in the **Solution Explorer** and select **Add**, **New Project**.</span></span> <span data-ttu-id="56c6d-110">从项目类型列表中的 "**已安装的模板**和**工作流" 控制台应用程序**中选择 "**工作流**"。</span><span class="sxs-lookup"><span data-stu-id="56c6d-110">Select **Workflow** in the **Installed Templates** and **Workflow Console Application** from the list of project types.</span></span> <span data-ttu-id="56c6d-111">将项目命名为 MyWFClient 并保存在默认位置，如以下插图所示。</span><span class="sxs-lookup"><span data-stu-id="56c6d-111">Name the project MyWFClient and use the default location as shown in the following illustration.</span></span>

     ![“添加新项目”对话框](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     <span data-ttu-id="56c6d-113">单击 **"确定"** 按钮以关闭 "**添加新项目" 对话框**。</span><span class="sxs-lookup"><span data-stu-id="56c6d-113">Click the **OK** button to dismiss the **Add New Project Dialog**.</span></span>

4. <span data-ttu-id="56c6d-114">创建项目以后，将在设计器中打开 Workflow1.xaml 文件。</span><span class="sxs-lookup"><span data-stu-id="56c6d-114">After the project is created, the Workflow1.xaml file is opened in the designer.</span></span> <span data-ttu-id="56c6d-115">单击 "**工具箱**" 选项卡以打开 "工具箱" （如果尚未打开），然后单击图钉使 "工具箱" 窗口保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="56c6d-115">Click the **Toolbox** tab to open the toolbox if it is not already open and click the pushpin to keep the toolbox window open.</span></span>

5. <span data-ttu-id="56c6d-116">按**Ctrl** + **F5**生成并启动该服务。</span><span class="sxs-lookup"><span data-stu-id="56c6d-116">Press **Ctrl**+**F5** to build and launch the service.</span></span> <span data-ttu-id="56c6d-117">与以前一样，将启动 ASP.NET Development Server，并且 Internet Explorer 将显示 WCF 帮助页。</span><span class="sxs-lookup"><span data-stu-id="56c6d-117">As before, the ASP.NET Development Server is launched and Internet Explorer displays the WCF Help Page.</span></span> <span data-ttu-id="56c6d-118">请注意该页面的 URI，因为在下一步中，您必须使用它。</span><span class="sxs-lookup"><span data-stu-id="56c6d-118">Notice the URI for this page as you must use it in the next step.</span></span>

     ![显示 WCF 帮助页和 URI 的 IE](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. <span data-ttu-id="56c6d-120">右键单击**解决方案资源管理器**中的**MyWFClient**项目，然后选择 "**添加**  >  **服务引用**"。</span><span class="sxs-lookup"><span data-stu-id="56c6d-120">Right click the **MyWFClient** project in the **Solution Explorer** and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="56c6d-121">单击 "**发现**" 按钮，在当前解决方案中搜索任何服务。</span><span class="sxs-lookup"><span data-stu-id="56c6d-121">Click the **Discover** button to search the current solution for any services.</span></span> <span data-ttu-id="56c6d-122">在“服务”列表中，单击 Service1.xamlx 旁边的三角形。</span><span class="sxs-lookup"><span data-stu-id="56c6d-122">Click the triangle next to Service1.xamlx in the Services list.</span></span> <span data-ttu-id="56c6d-123">单击 Service1 旁边的三角形列出由 Service1 服务实现的约定。</span><span class="sxs-lookup"><span data-stu-id="56c6d-123">Click the triangle next to Service1 to list the contracts implemented by the Service1 service.</span></span> <span data-ttu-id="56c6d-124">展开 "**服务**" 列表中的**Service1**节点。</span><span class="sxs-lookup"><span data-stu-id="56c6d-124">Expand the **Service1** node in the **Services** list.</span></span> <span data-ttu-id="56c6d-125">Echo 操作显示在 "**操作**" 列表中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="56c6d-125">The Echo operation is displayed in the **Operations** list as shown in the following illustration.</span></span>

     ![“添加服务引用”对话框](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     <span data-ttu-id="56c6d-127">保留默认命名空间，然后单击 **"确定"** 以关闭**添加服务引用**对话框。</span><span class="sxs-lookup"><span data-stu-id="56c6d-127">Keep the default namespace and click **OK** to dismiss the **Add Service Reference** dialog.</span></span> <span data-ttu-id="56c6d-128">将显示以下对话框。</span><span class="sxs-lookup"><span data-stu-id="56c6d-128">The following dialog is displayed.</span></span>

     ![添加服务引用通知对话框](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     <span data-ttu-id="56c6d-130">单击 **"确定"** 以关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="56c6d-130">Click **OK** to dismiss the dialog.</span></span> <span data-ttu-id="56c6d-131">接下来，按 Ctrl+Shift+B 生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="56c6d-131">Next, press CTRL+SHIFT+B to build the solution.</span></span> <span data-ttu-id="56c6d-132">请注意，在工具箱中添加了一个名为**MyWFClient**的新部分。</span><span class="sxs-lookup"><span data-stu-id="56c6d-132">Notice in the toolbox a new section has been added called **MyWFClient.ServiceReference1.Activities**.</span></span> <span data-ttu-id="56c6d-133">展开此部分，请注意，此时已添加“Echo”活动，如以下插图所示。</span><span class="sxs-lookup"><span data-stu-id="56c6d-133">Expand this section and notice the Echo activity that has been added as shown in the following illustration.</span></span>

     ![工具箱中的回显活动](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. <span data-ttu-id="56c6d-135">将 <xref:System.Activities.Statements.Sequence> 活动拖放到设计器图面。</span><span class="sxs-lookup"><span data-stu-id="56c6d-135">Drag and drop a <xref:System.Activities.Statements.Sequence> activity onto the designer surface.</span></span> <span data-ttu-id="56c6d-136">它位于 "工具箱" 的 "**控制流**" 部分下。</span><span class="sxs-lookup"><span data-stu-id="56c6d-136">It is under the **Control Flow** section of the toolbox.</span></span>

8. <span data-ttu-id="56c6d-137"><xref:System.Activities.Statements.Sequence>在焦点为的活动中，单击 "**变量**" 链接，并添加一个名为的字符串变量 `inString` 。</span><span class="sxs-lookup"><span data-stu-id="56c6d-137">With the <xref:System.Activities.Statements.Sequence> activity in focus, click the **Variables** link and add a string variable named `inString`.</span></span> <span data-ttu-id="56c6d-138">为变量指定默认值以及名为的 `"Hello, world"` 字符串变量，如下 `outString` 图所示。</span><span class="sxs-lookup"><span data-stu-id="56c6d-138">Give the variable a default value of `"Hello, world"` as well as a string variable named `outString` as shown in the following diagram.</span></span>

     ![添加 inString 变量](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. <span data-ttu-id="56c6d-140">将**回显**活动拖放到中 <xref:System.Activities.Statements.Sequence> 。</span><span class="sxs-lookup"><span data-stu-id="56c6d-140">Drag and drop an **Echo** activity into the <xref:System.Activities.Statements.Sequence>.</span></span> <span data-ttu-id="56c6d-141">在 "属性" 窗口中，将参数和变量的参数绑定 `inMsg` 到 `inString` 变量，如下 `outMsg` `outString` 图所示。</span><span class="sxs-lookup"><span data-stu-id="56c6d-141">In the properties window bind the `inMsg` argument to the `inString` variable and the `outMsg` argument to the `outString` variable as shown in the following illustration.</span></span> <span data-ttu-id="56c6d-142">这样会将 `inString` 变量的值传入操作中，然后获取返回值，并将返回值放到 `outString` 变量中。</span><span class="sxs-lookup"><span data-stu-id="56c6d-142">This passes in the value of the `inString` variable to the operation and then takes the return value and places it in the `outString` variable.</span></span>

     ![将自变量绑定到变量](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. <span data-ttu-id="56c6d-144">将 " **WriteLine** " 活动拖放到**回响**活动下面以显示服务调用返回的字符串。</span><span class="sxs-lookup"><span data-stu-id="56c6d-144">Drag and drop a **WriteLine** activity below the **Echo** activity to display the string returned by the service call.</span></span> <span data-ttu-id="56c6d-145">" **WriteLine** " 活动位于 "工具箱" 的 "**基元**" 节点中。</span><span class="sxs-lookup"><span data-stu-id="56c6d-145">The **WriteLine** activity is located in the **Primitives** node in the toolbox.</span></span> <span data-ttu-id="56c6d-146">**Text** **WriteLine** `outString` 通过 `outString` 在**writeline**活动的文本框中键入内容，将 WriteLine 活动的 text 参数绑定到变量。</span><span class="sxs-lookup"><span data-stu-id="56c6d-146">Bind the **Text** argument of the **WriteLine** activity to the `outString` variable by typing `outString` into the text box on the **WriteLine** activity.</span></span> <span data-ttu-id="56c6d-147">现在，此工作流应该如以下插图所示。</span><span class="sxs-lookup"><span data-stu-id="56c6d-147">The workflow should now look like the following illustration.</span></span>

     ![已完成的客户端工作流](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. <span data-ttu-id="56c6d-149">右键单击 MyWFService 解决方案，然后选择 "**设置启动项目 ...**"。选择 "**多启动项目**" 单选按钮，然后在 "**操作**" 列中为每个项目选择 "**启动**"，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="56c6d-149">Right-click the MyWFService solution and select **Set Startup Projects ...**. Select the **Multiple startup projects** radio button and select **Start** for each project in the **Action** column as shown in the following illustration.</span></span>

     ![启动项目选项](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. <span data-ttu-id="56c6d-151">按 Ctrl+F5 启动服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="56c6d-151">Press Ctrl + F5 to launch both the service and the client.</span></span> <span data-ttu-id="56c6d-152">ASP.NET 开发服务器承载服务，Internet Explorer 将显示 WCF 帮助页，客户端工作流应用程序将在控制台窗口中启动，并显示从服务（"Hello，world"）返回的字符串。</span><span class="sxs-lookup"><span data-stu-id="56c6d-152">The ASP.NET Development Server hosts the service, Internet Explorer displays the WCF help page, and the client workflow application is launched in a console window and displays the string returned from the service ("Hello, world").</span></span>

## <a name="see-also"></a><span data-ttu-id="56c6d-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56c6d-153">See also</span></span>

- [<span data-ttu-id="56c6d-154">工作流服务</span><span class="sxs-lookup"><span data-stu-id="56c6d-154">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="56c6d-155">如何：使用消息传递活动创建工作流服务</span><span class="sxs-lookup"><span data-stu-id="56c6d-155">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="56c6d-156">从 Web 项目的工作流中使用 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="56c6d-156">Consuming a WCF Service from a Workflow in a Web Project</span></span>](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
