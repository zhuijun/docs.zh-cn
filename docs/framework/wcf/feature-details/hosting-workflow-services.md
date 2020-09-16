---
title: 承载工作流服务
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 95d8d8b8ea15ef543471afb19462ccb424e8e39b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555804"
---
# <a name="hosting-workflow-services"></a><span data-ttu-id="a1c50-102">承载工作流服务</span><span class="sxs-lookup"><span data-stu-id="a1c50-102">Hosting Workflow Services</span></span>

<span data-ttu-id="a1c50-103">工作流服务在承载后才能对传入消息做出响应。</span><span class="sxs-lookup"><span data-stu-id="a1c50-103">A workflow service must be hosted for it to respond to incoming messages.</span></span> <span data-ttu-id="a1c50-104">工作流服务使用的是 WCF 消息传递基础结构，因此承载的方式也类似。</span><span class="sxs-lookup"><span data-stu-id="a1c50-104">Workflow services use the WCF messaging infrastructure and are therefore hosted in similar ways.</span></span> <span data-ttu-id="a1c50-105">与 WCF 服务类似，工作流服务可承载于任何托管应用程序、Internet Information Services (IIS) 下，或在) 的 Windows 进程激活服务 (下。</span><span class="sxs-lookup"><span data-stu-id="a1c50-105">Like WCF services, workflow services can be hosted in any managed application, under Internet Information Services (IIS), or under Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="a1c50-106">此外，可以在 Windows Server App Fabric 下承载工作流服务。</span><span class="sxs-lookup"><span data-stu-id="a1c50-106">In addition, workflow services can be hosted under Windows Server App Fabric.</span></span> <span data-ttu-id="a1c50-107">有关 Windows Server App Fabric 的详细信息，请参阅 [Windows Server App fabric 文档](/previous-versions/appfabric/ff384253(v=azure.10))、 [appfabric 托管功能](/previous-versions/appfabric/ee677189(v=azure.10))和 [appfabric 托管概念](/previous-versions/appfabric/ee677371(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="a1c50-107">For more information about Windows Server App Fabric see [Windows Server App Fabric documentation](/previous-versions/appfabric/ff384253(v=azure.10)), [AppFabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10)), and [AppFabric Hosting Concepts](/previous-versions/appfabric/ee677371(v=azure.10)).</span></span> <span data-ttu-id="a1c50-108">有关承载 WCF 服务的各种方式的详细信息，请参阅 [托管服务](../hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a1c50-108">For more information about the various ways to host WCF services see [Hosting Services](../hosting-services.md).</span></span>

## <a name="hosting-in-a-managed-application"></a><span data-ttu-id="a1c50-109">在托管应用程序中承载</span><span class="sxs-lookup"><span data-stu-id="a1c50-109">Hosting in a managed application</span></span>
 <span data-ttu-id="a1c50-110">若要在托管应用程序中承载工作流服务，请使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 类。</span><span class="sxs-lookup"><span data-stu-id="a1c50-110">To host a workflow service in a managed application, use the <xref:System.ServiceModel.Activities.WorkflowServiceHost> class.</span></span> <span data-ttu-id="a1c50-111"><xref:System.ServiceModel.Activities.WorkflowServiceHost> 构造函数可用于指定单一工作流服务实例、工作流服务定义或使用工作流消息传递活动的活动。</span><span class="sxs-lookup"><span data-stu-id="a1c50-111">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> constructor allows you to specify a singleton workflow service instance, a workflow service definition, or an activity that uses the workflow messaging activities.</span></span> <span data-ttu-id="a1c50-112">调用 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 将导致服务开始侦听传入消息。</span><span class="sxs-lookup"><span data-stu-id="a1c50-112">Calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> causes the service to start listening for incoming messages.</span></span>

## <a name="hosting-under-iis-or-was"></a><span data-ttu-id="a1c50-113">在 IIS 或 WAS 下承载</span><span class="sxs-lookup"><span data-stu-id="a1c50-113">Hosting under IIS or WAS</span></span>
 <span data-ttu-id="a1c50-114">在 IIS 或 WAS 下承载工作流服务时，涉及到创建虚拟目录以及将定义服务及其行为的文件放在该虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="a1c50-114">Hosting a workflow service under IIS or WAS involves creating a virtual directory and placing files in the virtual directory that define the service and its behavior.</span></span> <span data-ttu-id="a1c50-115">此时可能出现以下几种情况：</span><span class="sxs-lookup"><span data-stu-id="a1c50-115">When hosting a workflow service under IIS or WAS there are several possibilities:</span></span>

- <span data-ttu-id="a1c50-116">将定义工作流服务的 .xamlx 文件放在 IIS/WAS 虚拟目录中，同时放入指定服务行为、终结点和其他配置元素的 Web.config 文件。</span><span class="sxs-lookup"><span data-stu-id="a1c50-116">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory along with a Web.config file that specifies the service behaviors, endpoints, and other configuration elements.</span></span>

- <span data-ttu-id="a1c50-117">将定义工作流服务的 .xamlx 文件放在一个 IIS/WAS 虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="a1c50-117">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory.</span></span> <span data-ttu-id="a1c50-118">.xamlx 文件指定要公开的终结点。</span><span class="sxs-lookup"><span data-stu-id="a1c50-118">The .xamlx file specifies the endpoints to expose.</span></span> <span data-ttu-id="a1c50-119">终结点将在 `WorkflowService.Endpoints` 元素中指定，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="a1c50-119">Endpoints are specified in a `WorkflowService.Endpoints` element as shown in the following example.</span></span>

    ```xml
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
      <WorkflowService.Endpoints>
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">
          <Endpoint.Binding>
            <BasicHttpBinding />
          </Endpoint.Binding>
        </Endpoint>
      </WorkflowService.Endpoints>
    <!-- ... -->
    </WorkflowService>
    ```

    > [!NOTE]
    > <span data-ttu-id="a1c50-120">不能在 .xamlx 文件中指定行为，因此，如果需要指定行为设置，则必须使用 Web.config。</span><span class="sxs-lookup"><span data-stu-id="a1c50-120">Behaviors cannot be specified in a .xamlx file, so you must use a Web.config if you need to specify behavior settings.</span></span>

- <span data-ttu-id="a1c50-121">将定义工作流服务的 .xamlx 文件放在一个 IIS/WAS 虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="a1c50-121">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory.</span></span> <span data-ttu-id="a1c50-122">另外，将一个 .svc 文件放在该虚拟目录中。</span><span class="sxs-lookup"><span data-stu-id="a1c50-122">In addition, place a .svc file in the virtual directory.</span></span> <span data-ttu-id="a1c50-123">使用 .svc 文件可以指定自定义 Web 服务主机工厂、应用自定义行为或者从自定义位置加载配置。</span><span class="sxs-lookup"><span data-stu-id="a1c50-123">The .svc file allows you to specify a custom Web service host factory, apply custom behavior, or load configuration from a custom location.</span></span>

- <span data-ttu-id="a1c50-124">将一个程序集放在 IIS/WAS 虚拟目录中，该程序集包含一个使用 WCF 消息传递活动的活动。</span><span class="sxs-lookup"><span data-stu-id="a1c50-124">Place an assembly in the IIS/WAS virtual directory that contains an activity that uses the WCF messaging activities.</span></span>

 <span data-ttu-id="a1c50-125">定义工作流服务的 .xamlx 文件必须包含一个 <`Service`> 根元素或包含从派生的任何类型的根元素 <xref:System.Workflow.ComponentModel.Activity> 。</span><span class="sxs-lookup"><span data-stu-id="a1c50-125">A .xamlx file that defines a workflow service must contain a <`Service`> root element or a root element that contains any type derived from <xref:System.Workflow.ComponentModel.Activity>.</span></span> <span data-ttu-id="a1c50-126">使用 Visual Studio 活动模板时，会创建一个 .xamlx 文件。</span><span class="sxs-lookup"><span data-stu-id="a1c50-126">When using the Visual Studio activity template, a .xamlx file is created.</span></span> <span data-ttu-id="a1c50-127">使用 WCF 工作流服务模板时，将创建一个 .xamlx 文件。</span><span class="sxs-lookup"><span data-stu-id="a1c50-127">When using the WCF Workflow Service template, a .xamlx file is created.</span></span>

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a><span data-ttu-id="a1c50-128">在 Windows Server App Fabric 下承载工作流服务</span><span class="sxs-lookup"><span data-stu-id="a1c50-128">Hosting Workflow Services under Windows Server App Fabric</span></span>
 <span data-ttu-id="a1c50-129">在 Windows Server App Fabric 下承载工作流服务的方式与在 IIS/WAS 下的承载方式相同。</span><span class="sxs-lookup"><span data-stu-id="a1c50-129">Hosting a workflow service under Windows Server App Fabric is done in the same way as hosting under IIS/WAS.</span></span> <span data-ttu-id="a1c50-130">唯一区别在于会安装 Windows Server App Fabric。</span><span class="sxs-lookup"><span data-stu-id="a1c50-130">The only difference is the fact that Windows Server App Fabric is installed.</span></span> <span data-ttu-id="a1c50-131">Windows Server App Fabric 提供了添加到 Internet 信息服务管理器的工具，以及 powershell commandlets。</span><span class="sxs-lookup"><span data-stu-id="a1c50-131">Windows Server App Fabric provides tools that are added to Internet Information Services Manager, as well as powershell commandlets.</span></span> <span data-ttu-id="a1c50-132">这些工具可简化工作流服务和 WCF 服务的部署、管理和跟踪。</span><span class="sxs-lookup"><span data-stu-id="a1c50-132">These tools simplify deploying, managing, and tracking of workflow services and WCF services.</span></span>

## <a name="referencing-custom-activities"></a><span data-ttu-id="a1c50-133">引用自定义活动</span><span class="sxs-lookup"><span data-stu-id="a1c50-133">Referencing Custom Activities</span></span>
 <span data-ttu-id="a1c50-134">必须将对自定义活动的引用添加到 `Assemblies` <> 下的 <> 部分， `System.Web.Compilation` 以便将这些引用加载到应用程序域中，并且 XAML 反序列化程序能够查找类型。</span><span class="sxs-lookup"><span data-stu-id="a1c50-134">References to custom activities must be added to the <`Assemblies`> section under <`System.Web.Compilation`> so that they are loaded into the Application Domain and the XAML deserializer is able to locate the types.</span></span> <span data-ttu-id="a1c50-135">可以在应用程序级别进行这些设置；如果要将这些设置应用于计算机上的所有应用程序，则可在根 Web.config 中进行这些设置。</span><span class="sxs-lookup"><span data-stu-id="a1c50-135">These settings can be made at the application level or in the root Web.config if the settings should be applied to all applications on the machine.</span></span>

## <a name="deployment"></a><span data-ttu-id="a1c50-136">部署</span><span class="sxs-lookup"><span data-stu-id="a1c50-136">Deployment</span></span>
 <span data-ttu-id="a1c50-137">系统中已经创建 Web 部署工具，以方便部署作业。</span><span class="sxs-lookup"><span data-stu-id="a1c50-137">The Web Deployment tool has been created to make the job of deployment easier.</span></span> <span data-ttu-id="a1c50-138">通过使用该工具，可以在 IIS 6.0 和 IIS 7.0 之间迁移应用程序，同步服务器场，并打包、存档和部署 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a1c50-138">The tool allows you to migrate applications between IIS 6.0 and IIS 7.0, synchronize server farms, and package, archive and deploy Web applications.</span></span> <span data-ttu-id="a1c50-139">有关详细信息，请参阅 [MS 部署工具](https://go.microsoft.com/fwlink/?LinkId=178690)。</span><span class="sxs-lookup"><span data-stu-id="a1c50-139">For more information, see [MS Deployment Tool](https://go.microsoft.com/fwlink/?LinkId=178690).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1c50-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="a1c50-140">See also</span></span>

- [<span data-ttu-id="a1c50-141">工作流服务主机内部机制</span><span class="sxs-lookup"><span data-stu-id="a1c50-141">Workflow Service Host Internals</span></span>](workflow-service-host-internals.md)
- [<span data-ttu-id="a1c50-142">配置 WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="a1c50-142">Configuring WorkflowServiceHost</span></span>](configuring-workflowservicehost.md)
