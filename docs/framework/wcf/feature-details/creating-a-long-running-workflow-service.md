---
title: 创建长时间运行的工作流服务
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 4ae01201230bf848c045158424db60097d8dd767
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599342"
---
# <a name="create-a-long-running-workflow-service"></a><span data-ttu-id="dd1c3-102">创建长时间运行的工作流服务</span><span class="sxs-lookup"><span data-stu-id="dd1c3-102">Create a Long-running Workflow Service</span></span>

<span data-ttu-id="dd1c3-103">本主题描述如何创建长时间运行的工作流服务。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="dd1c3-104">长时间运行的工作流服务可能会运行很长一段时间。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="dd1c3-105">在某一时刻，工作流可能会转入空闲状态，等待一些附加信息。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="dd1c3-106">当这种情况发生时，工作流将保存到 SQL 数据库并从内存中删除。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="dd1c3-107">当附加信息变得可用时，工作流实例将重新加载回内存，继续执行。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="dd1c3-108">在此方案中，您将实现一个非常简化的订单系统。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="dd1c3-109">客户端向工作流服务发送初始消息以启动订单。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="dd1c3-110">此服务将订单 ID 返回给客户端。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-110">It returns an order ID to the client.</span></span> <span data-ttu-id="dd1c3-111">此时，工作流服务要等待来自客户端的另一条消息，它转入空闲状态并保存到 SQL Server 数据库。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="dd1c3-112">当客户端发送下一条消息订购项目时，工作流服务将重新加载回内存，完成处理此订单。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="dd1c3-113">在代码示例中它将返回一个字符串，指示项目已添加到订单中。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="dd1c3-114">代码示例并不是技术的现实应用，而是作为一个简单的示例来说明长时间运行的工作流服务。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="dd1c3-115">本主题假定你知道如何创建 Visual Studio 2012 项目和解决方案。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-115">This topic assumes you know how to create Visual Studio 2012 projects and solutions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd1c3-116">必备条件</span><span class="sxs-lookup"><span data-stu-id="dd1c3-116">Prerequisites</span></span>

<span data-ttu-id="dd1c3-117">您必须安装了下列软件才能使用本演练：</span><span class="sxs-lookup"><span data-stu-id="dd1c3-117">You must have the following software installed to use this walkthrough:</span></span>

1. <span data-ttu-id="dd1c3-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="dd1c3-118">Microsoft SQL Server 2008</span></span>

2. <span data-ttu-id="dd1c3-119">Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="dd1c3-119">Visual Studio 2012</span></span>

3. <span data-ttu-id="dd1c3-120">Microsoft [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd1c3-120">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>

4. <span data-ttu-id="dd1c3-121">你熟悉 WCF 和 Visual Studio 2012，并且知道如何创建项目/解决方案。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-121">You are familiar with WCF and Visual Studio 2012 and know how to create projects/solutions.</span></span>

## <a name="set-up-the-sql-database"></a><span data-ttu-id="dd1c3-122">设置 SQL 数据库</span><span class="sxs-lookup"><span data-stu-id="dd1c3-122">Set up the SQL Database</span></span>

1. <span data-ttu-id="dd1c3-123">为了使工作流服务实例能够持久化，您必须安装 Microsoft SQL Server，并配置一个数据库来存储持久化工作流实例。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-123">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="dd1c3-124">通过单击 "**开始**" 按钮，选择 "**所有程序**"、" **Microsoft SQL Server 2008**" 和 " **MICROSOFT sql Management Studio**" 来运行 microsoft sql Management Studio。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-124">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>

2. <span data-ttu-id="dd1c3-125">单击 "**连接**" 按钮登录到 SQL Server 实例</span><span class="sxs-lookup"><span data-stu-id="dd1c3-125">Click the **Connect** button to log on to the SQL Server instance</span></span>

3. <span data-ttu-id="dd1c3-126">右键单击树视图中的 "**数据库**"，然后选择 "**新建数据库"。**</span><span class="sxs-lookup"><span data-stu-id="dd1c3-126">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="dd1c3-127">创建名为的新数据库 `SQLPersistenceStore` 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-127">to create a new database called `SQLPersistenceStore`.</span></span>

4. <span data-ttu-id="dd1c3-128">在 SQLPersistenceStore 数据库上运行位于 C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en 目录中的 SqlWorkflowInstanceStoreSchema.sql 脚本文件，以设置所需的数据库架构。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-128">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>

5. <span data-ttu-id="dd1c3-129">在 SQLPersistenceStore 数据库上运行位于 C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en 目录中的 SqlWorkflowInstanceStoreLogic.sql 脚本文件，以设置所需的数据库逻辑。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-129">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>

## <a name="create-the-web-hosted-workflow-service"></a><span data-ttu-id="dd1c3-130">创建 Web 承载的工作流服务</span><span class="sxs-lookup"><span data-stu-id="dd1c3-130">Create the Web Hosted Workflow Service</span></span>

1. <span data-ttu-id="dd1c3-131">创建一个空的 Visual Studio 2012 解决方案，将其命名为 `OrderProcessing` 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-131">Create an empty Visual Studio 2012 solution, name it `OrderProcessing`.</span></span>

2. <span data-ttu-id="dd1c3-132">向该解决方案添加一个名为 `OrderService` 的新 WCF 工作流服务应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-132">Add a new WCF Workflow Service Application project called `OrderService` to the solution.</span></span>

3. <span data-ttu-id="dd1c3-133">在 "项目属性" 对话框中，选择 " **Web** " 选项卡。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-133">In the project properties dialog, select the **Web** tab.</span></span>

    1. <span data-ttu-id="dd1c3-134">在 "**启动操作**" 下，选择 "**特定页**" 并指定 `Service1.xamlx` 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-134">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>

        <span data-ttu-id="dd1c3-135">![工作流服务项目 Web 属性](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png ""创建 web 承载的工作流服务特定页" 选项")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-135">![Workflow Service Project Web Properties](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Create the web hosted workflow service - Specific Page option")</span></span>

    2. <span data-ttu-id="dd1c3-136">在 "**服务器**" 下选择 "**使用本地 IIS Web 服务器**"。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-136">Under **Servers** select **Use Local IIS Web server**.</span></span>

        <span data-ttu-id="dd1c3-137">![本地 Web 服务器设置](./media/creating-a-long-running-workflow-service/use-local-web-server.png "创建 web 承载的工作流服务-使用本地 IIS Web 服务器选项")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-137">![Local Web Server Settings](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Create the web hosted workflow service - Use Local IIS Web Server option")</span></span>

        > [!WARNING]
        > <span data-ttu-id="dd1c3-138">若要进行此设置，必须在管理员模式下运行 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-138">You must run Visual Studio 2012 in administrator mode to make this setting.</span></span>

        <span data-ttu-id="dd1c3-139">这两个步骤将工作流服务项目配置为由 IIS 承载。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-139">These two steps configure the workflow service project to be hosted by IIS.</span></span>

4. <span data-ttu-id="dd1c3-140">`Service1.xamlx`如果尚未打开，请将其打开，并删除现有的**ReceiveRequest**和**SendResponse**活动。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-140">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>

5. <span data-ttu-id="dd1c3-141">选择 "**顺序服务**" 活动，单击 "**变量**" 链接，并添加下图中显示的变量。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-141">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="dd1c3-142">通过执行此操作，会添加一些稍后将在工作流服务中使用的变量。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-142">Doing this adds some variables that will be used later on in the workflow service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="dd1c3-143">如果 CorrelationHandle 不在 "变量类型" 下拉下，请从下拉选择 "**浏览类型**"。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-143">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="dd1c3-144">在 "**类型名称**" 框中键入 CorrelationHandle，从列表框中选择 "CorrelationHandle"，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-144">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>

    <span data-ttu-id="dd1c3-145">![添加变量](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "向顺序服务活动中添加变量。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-145">![Add Variables](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Add variables to the Sequential Service activity.")</span></span>

6. <span data-ttu-id="dd1c3-146">将**ReceiveAndSendReply**活动模板拖放到**顺序服务**活动中。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-146">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="dd1c3-147">这组活动将接收来自客户端的消息，并发送回复。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-147">This set of activities will receive a message from a client and send a reply back.</span></span>

    1. <span data-ttu-id="dd1c3-148">选择 "**接收**" 活动，并设置下图中突出显示的属性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-148">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>

        <span data-ttu-id="dd1c3-149">![设置 Receive 活动属性](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "设置 "接收" 活动属性。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-149">![Set Receive Activity Properties](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Set the Receive activity properties.")</span></span>

        <span data-ttu-id="dd1c3-150">DisplayName 属性设置在设计器中显示的 Receive 活动的名称。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-150">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="dd1c3-151">ServiceContractName 和 OperationName 属性指定 Receive 活动实现的服务协定和操作的名称。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-151">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> <span data-ttu-id="dd1c3-152">有关如何在工作流服务中使用约定的详细信息，请参阅[在工作流中使用约定](using-contracts-in-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-152">For more information about how contracts are used in Workflow services see [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>

    2. <span data-ttu-id="dd1c3-153">单击 " **ReceiveStartOrder** " 活动中的 "**定义 ...** " 链接，并设置下图中显示的属性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-153">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="dd1c3-154">请注意，"**参数**" 单选按钮已选中，名为的参数 `p_customerName` 绑定到 `customerName` 变量。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-154">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="dd1c3-155">这会将**receive**活动配置为接收某些数据并将这些数据绑定到本地变量。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-155">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>

        <span data-ttu-id="dd1c3-156">![设置由 Receive 活动接收的数据](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "设置由 Receive 活动接收的数据的属性。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-156">![Setting the data received by the Receive activity](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Set the properties for data received by the Receive activity.")</span></span>

    3. <span data-ttu-id="dd1c3-157">选择**SendReplyToReceive**活动，并设置下图中显示的突出显示的属性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-157">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>

        <span data-ttu-id="dd1c3-158">![设置 SendReply 活动的属性](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-158">![Setting the properties of the SendReply activity](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")</span></span>

    4. <span data-ttu-id="dd1c3-159">单击 " **SendReplyToStartOrder** " 活动中的 "**定义 ...** " 链接，并设置下图中显示的属性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-159">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="dd1c3-160">请注意，"**参数**" 单选按钮处于选中状态;名为的参数 `p_orderId` 绑定到 `orderId` 变量。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-160">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="dd1c3-161">此设置指定 SendReplyToStartOrder 活动将类型字符串的值返回给调用方。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-161">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>

        <span data-ttu-id="dd1c3-162">![配置 SendReply 活动内容数据](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "配置 SetReplyToStartOrder 活动的设置。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-162">![Configuring the SendReply activity content data](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Configure setting for SetReplyToStartOrder activity.")</span></span>

    5. <span data-ttu-id="dd1c3-163">将 "Assign" 活动拖放到 " **Receive** " 和 " **SendReply** " 活动之间，并设置属性，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="dd1c3-163">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>

        <span data-ttu-id="dd1c3-164">![添加 Assign 活动](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "添加 "分配" 活动。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-164">![Adding an assign activity](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Add an assign activity.")</span></span>

        <span data-ttu-id="dd1c3-165">这将创建一个新的订单 ID，并将该值放在 orderId 变量中。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-165">This creates a new order ID and places the value in the orderId variable.</span></span>

    6. <span data-ttu-id="dd1c3-166">选择 " **ReplyToStartOrder** " 活动。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-166">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="dd1c3-167">在 "属性" 窗口中，单击 " **CorrelationInitializers**" 的省略号按钮。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-167">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="dd1c3-168">选择 "**添加初始值设定项**" 链接， `orderIdHandle` 在 "初始值设定项" 文本框中输入，为相关类型选择 "查询相关初始值设定项"，然后在 "XPATH 查询" 下拉框下选择 p_orderId。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-168">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="dd1c3-169">这些设置如下图所示。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-169">These settings are shown in the following illustration.</span></span> <span data-ttu-id="dd1c3-170">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-170">Click **OK**.</span></span>  <span data-ttu-id="dd1c3-171">这将初始化客户端与此工作流服务实例之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-171">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="dd1c3-172">当接收到包含此订单 ID 的消息时，将该消息路由至此工作流服务实例。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-172">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>

        <span data-ttu-id="dd1c3-173">![添加相关初始值设定项](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "添加相关初始值设定项。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-173">![Adding a correlation initializer](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Add a correlation initializer.")</span></span>

7. <span data-ttu-id="dd1c3-174">将另一个 " **ReceiveAndSendReply** " 活动拖放到工作流的末尾（在包含第一个**接收**和**SendReply**活动的**序列**之外）。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-174">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="dd1c3-175">这将接收客户端发送的第二条消息，并对它做出响应。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-175">This will receive the second message sent by the client and respond to it.</span></span>

    1. <span data-ttu-id="dd1c3-176">选择包含新添加的**接收**和**SendReply**活动的**序列**，然后单击 "**变量**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-176">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="dd1c3-177">添加下图中突出显示的变量：</span><span class="sxs-lookup"><span data-stu-id="dd1c3-177">Add the variable highlighted in the following illustration:</span></span>

        <span data-ttu-id="dd1c3-178">![添加新变量](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "添加 ItemId 变量。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-178">![Adding new variables](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Add the ItemId variable.")</span></span>

        <span data-ttu-id="dd1c3-179">还 `orderResult` 在范围内添加为**字符串** `Sequence` 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-179">Also add `orderResult` as **String** in the `Sequence` scope.</span></span>

    2. <span data-ttu-id="dd1c3-180">选择 "**接收**" 活动，并设置下图中显示的属性：</span><span class="sxs-lookup"><span data-stu-id="dd1c3-180">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>

        <span data-ttu-id="dd1c3-181">![设置接收活动属性](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "设置 "接收活动" 属性。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-181">![Set the Receive activity properties](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Set the Receive activities properties.")</span></span>

        > [!NOTE]
        > <span data-ttu-id="dd1c3-182">别忘了用更改**ServiceContractName**字段 `../IAddItem` 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-182">Don't forget to change **ServiceContractName** field with `../IAddItem`.</span></span>

    3. <span data-ttu-id="dd1c3-183">单击 " **ReceiveAddItem** " 活动中的 "**定义 ...** " 链接，并添加下图中显示的参数：这将配置 receive 活动，以接受两个参数，即订单 ID 和所订购项的 id。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-183">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>

        <span data-ttu-id="dd1c3-184">![为第二次接收指定参数](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "配置 receive 活动以接收两个参数。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-184">![Specifying parameters for the second receive](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Configure the receive activity to receive two parameters.")</span></span>

    4. <span data-ttu-id="dd1c3-185">单击 " **CorrelateOn** " 省略号按钮，然后输入 `orderIdHandle` 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-185">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="dd1c3-186">在 " **XPath 查询**" 下，单击下拉箭头并选择 `p_orderId` 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-186">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="dd1c3-187">这将对第二个接收活动配置相关性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-187">This configures the correlation on the second receive activity.</span></span> <span data-ttu-id="dd1c3-188">有关关联的详细信息，请参阅[关联](correlation.md)。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-188">For more information about correlation see [Correlation](correlation.md).</span></span>

        <span data-ttu-id="dd1c3-189">![设置 CorrelatesOn 属性](./media/creating-a-long-running-workflow-service/correlateson-setting.png "设置 CorrelatesOn 属性。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-189">![Setting the CorrelatesOn property](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Set the CorrelatesOn property.")</span></span>

    5. <span data-ttu-id="dd1c3-190">将一个**If**活动拖放到**ReceiveAddItem**活动后面。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-190">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="dd1c3-191">此活动的行为与 if 语句类似。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-191">This activity acts just like an if statement.</span></span>

        1. <span data-ttu-id="dd1c3-192">将**Condition**属性设置为`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="dd1c3-192">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>

        2. <span data-ttu-id="dd1c3-193">将 " **assign** " 活动拖放到 " **Then** " 部分，然后将另一个分配给**Else**节，按下图所示设置 "**分配**" 活动的属性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-193">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>

            <span data-ttu-id="dd1c3-194">![分配服务调用的结果](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "分配服务调用的结果。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-194">![Assigning the result of the service call](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Assign the result of the service call.")</span></span>

            <span data-ttu-id="dd1c3-195">如果条件为， `true` 则将执行 " **Then** " 部分。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-195">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="dd1c3-196">如果条件为，则 `false` 执行 " **Else** " 部分。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-196">If the condition is `false` the **Else** section is executed.</span></span>

        3. <span data-ttu-id="dd1c3-197">选择**SendReplyToReceive**活动，并设置下图中显示的**DisplayName**属性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-197">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>

            <span data-ttu-id="dd1c3-198">![设置 SendReply 活动属性](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "设置 SendReply 活动属性。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-198">![Setting the SendReply activity properties](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Set the SendReply activity property.")</span></span>

        4. <span data-ttu-id="dd1c3-199">单击 " **SetReplyToAddItem** " 活动中的 "**定义 ...** " 链接，并对其进行配置，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-199">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="dd1c3-200">这会将**SendReplyToAddItem**活动配置为返回变量中的值 `orderResult` 。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-200">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>

            <span data-ttu-id="dd1c3-201">![设置 SendReply 活动的数据绑定](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "设置 SendReplyToAddItem 活动的属性。")</span><span class="sxs-lookup"><span data-stu-id="dd1c3-201">![Setting the data binding for the SendReply activity](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Set property for SendReplyToAddItem activity.")</span></span>

8. <span data-ttu-id="dd1c3-202">打开 web.config 文件，并在部分中添加以下元素， \<behavior> 以启用工作流持久性。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-202">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > <span data-ttu-id="dd1c3-203">确保替换上面代码段中的主机和 SQL Server 实例名称。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-203">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>

9. <span data-ttu-id="dd1c3-204">生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-204">Build the solution.</span></span>

## <a name="create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="dd1c3-205">创建用于调用工作流服务的客户端应用程序</span><span class="sxs-lookup"><span data-stu-id="dd1c3-205">Create a Client Application to Call the Workflow Service</span></span>

1. <span data-ttu-id="dd1c3-206">将一个名为 `OrderClient` 的新控制台应用程序项目添加到解决方案中。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-206">Add a new Console application project called `OrderClient` to the solution.</span></span>

2. <span data-ttu-id="dd1c3-207">向 `OrderClient` 项目中添加对以下程序集的引用：</span><span class="sxs-lookup"><span data-stu-id="dd1c3-207">Add references to the following assemblies to the `OrderClient` project</span></span>

    1. <span data-ttu-id="dd1c3-208">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="dd1c3-208">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="dd1c3-209">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="dd1c3-209">System.ServiceModel.Activities.dll</span></span>

3. <span data-ttu-id="dd1c3-210">添加对工作流服务的服务引用，并将 `OrderService` 指定为命名空间。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-210">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>

4. <span data-ttu-id="dd1c3-211">在客户端项目的 `Main()` 方法中，添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="dd1c3-211">In the `Main()` method of the client project add the following code:</span></span>

    ```csharp
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5. <span data-ttu-id="dd1c3-212">生成解决方案，并运行 `OrderClient` 应用程序。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-212">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="dd1c3-213">客户端将显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="dd1c3-213">The client will display the following text:</span></span>

    ```output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. <span data-ttu-id="dd1c3-214">若要验证工作流服务是否已持久化，请转到 "**开始**" 菜单，选择 "**所有程序**"， **Microsoft SQL Server 2008**， **SQL Server Management Studio**，开始 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-214">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>

    1. <span data-ttu-id="dd1c3-215">在左侧窗格中，依次展开 **"数据库**"、"数据库"、" **SQLPersistenceStore**"、"**视图**" 和 " **DurableInstancing** "，然后选择 "**选择前1000行**"。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-215">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="dd1c3-216">在**结果**窗格中，验证是否已列出至少一个实例。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-216">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="dd1c3-217">如果运行时出现异常，则可能存在先前运行的其他实例。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-217">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="dd1c3-218">您可以通过右键单击 " **DurableInstancing** "，然后选择 "**编辑前200行**"，再按 "**执行**" 按钮，选择结果窗格中的所有行，然后选择 "**删除**" 来删除现有行。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-218">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="dd1c3-219">若要验证数据库中显示的实例是否为应用程序创建的实例，请在运行客户端之前验证实例视图是否为空。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-219">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="dd1c3-220">客户端开始运行后，重新运行查询（选择前 1000 行），并确认已添加新实例。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-220">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>

7. <span data-ttu-id="dd1c3-221">按 Enter 将添加项目消息发送至工作流服务。</span><span class="sxs-lookup"><span data-stu-id="dd1c3-221">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="dd1c3-222">客户端将显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="dd1c3-222">The client will display the following text:</span></span>

    ```output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a><span data-ttu-id="dd1c3-223">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd1c3-223">See also</span></span>

- [<span data-ttu-id="dd1c3-224">工作流服务</span><span class="sxs-lookup"><span data-stu-id="dd1c3-224">Workflow Services</span></span>](workflow-services.md)
