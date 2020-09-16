---
title: 如何：在托管 Windows 服务中承载 WCF 服务
description: 了解如何创建由 Windows 服务承载的 WCF 服务。 此宿主选项在 Windows 的所有版本中都是可用的。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 21d3dcb05e48154eb3f9f10d8308dc14bd046ae1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546336"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="e2749-104">如何：在托管 Windows 服务中承载 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="e2749-104">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="e2749-105">本主题概述了创建由 Windows 服务托管的 Windows Communication Foundation (WCF) 服务所需的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="e2749-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="e2749-106">此方案由托管 Windows 服务宿主选项启用，该选项是一个长时间运行的 WCF 服务，该服务在未激活消息的安全环境中 Internet Information Services (IIS) 上托管。</span><span class="sxs-lookup"><span data-stu-id="e2749-106">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="e2749-107">服务的生存期改由操作系统控制。</span><span class="sxs-lookup"><span data-stu-id="e2749-107">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="e2749-108">此宿主选项在 Windows 的所有版本中都是可用的。</span><span class="sxs-lookup"><span data-stu-id="e2749-108">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="e2749-109">可以使用 Microsoft 管理控制台 (MMC) 中的 Microsoft.ManagementConsole.SnapIn 管理 Windows 服务，并且可以将其配置为在系统启动时自动启动。</span><span class="sxs-lookup"><span data-stu-id="e2749-109">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="e2749-110">此宿主选项包括注册作为托管 Windows 服务承载 WCF 服务的应用程序域 (AppDomain) ，以便服务的进程生存期由 Windows 服务的服务控制管理器 (SCM) 控制。</span><span class="sxs-lookup"><span data-stu-id="e2749-110">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="e2749-111">服务代码包括服务协定的服务实现、Windows 服务类和安装程序类。</span><span class="sxs-lookup"><span data-stu-id="e2749-111">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="e2749-112">服务实现类 `CalculatorService` 是 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="e2749-112">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="e2749-113">`CalculatorWindowsService` 是 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="e2749-113">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="e2749-114">要符合 Windows 服务的要求，该类继承自 `ServiceBase` 并实现 `OnStart` 和 `OnStop` 方法。</span><span class="sxs-lookup"><span data-stu-id="e2749-114">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="e2749-115">在 `OnStart` 中，将为 <xref:System.ServiceModel.ServiceHost> 类型创建 `CalculatorService` 并打开它。</span><span class="sxs-lookup"><span data-stu-id="e2749-115">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="e2749-116">在 `OnStop` 中，停止并释放服务。</span><span class="sxs-lookup"><span data-stu-id="e2749-116">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="e2749-117">主机还负责提供服务主机基址，该基址已在应用程序设置中进行设置。</span><span class="sxs-lookup"><span data-stu-id="e2749-117">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="e2749-118">安装程序类继承自 <xref:System.Configuration.Install.Installer>，允许程序通过 Installutil.exe 工具安装为 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="e2749-118">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="e2749-119">构造服务并提供主机代码</span><span class="sxs-lookup"><span data-stu-id="e2749-119">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="e2749-120">创建名为 "**服务**" 的新 Visual Studio**控制台应用程序**项目。</span><span class="sxs-lookup"><span data-stu-id="e2749-120">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="e2749-121">将 Program.cs 重命名为 Service.cs。</span><span class="sxs-lookup"><span data-stu-id="e2749-121">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="e2749-122">将命名空间更改为 `Microsoft.ServiceModel.Samples` 。</span><span class="sxs-lookup"><span data-stu-id="e2749-122">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="e2749-123">添加对下列程序集的引用：</span><span class="sxs-lookup"><span data-stu-id="e2749-123">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="e2749-124">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="e2749-124">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="e2749-125">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="e2749-125">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="e2749-126">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="e2749-126">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="e2749-127">将下面的 using 语句添加到 Service.cs。</span><span class="sxs-lookup"><span data-stu-id="e2749-127">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="e2749-128">定义 `ICalculator` 服务协定，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e2749-128">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="e2749-129">在称为 `CalculatorService` 的类中实现服务协定，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e2749-129">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="e2749-130">创建从 `CalculatorWindowsService` 类继承的称为 <xref:System.ServiceProcess.ServiceBase> 的新类。</span><span class="sxs-lookup"><span data-stu-id="e2749-130">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="e2749-131">添加称为 `serviceHost` 的局部变量以引用 <xref:System.ServiceModel.ServiceHost> 实例。</span><span class="sxs-lookup"><span data-stu-id="e2749-131">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="e2749-132">定义调用 `Main` 的 `ServiceBase.Run(new CalculatorWindowsService)` 方法</span><span class="sxs-lookup"><span data-stu-id="e2749-132">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="e2749-133">通过创建并打开新 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 实例重写 <xref:System.ServiceModel.ServiceHost> 方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e2749-133">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="e2749-134">通过关闭 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 重写 <xref:System.ServiceModel.ServiceHost> 方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e2749-134">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="e2749-135">创建称为 `ProjectInstaller` 的新类，该类继承自 <xref:System.Configuration.Install.Installer>，且其 <xref:System.ComponentModel.RunInstallerAttribute> 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="e2749-135">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="e2749-136">这允许 Windows 服务由 Installutil.exe 工具安装。</span><span class="sxs-lookup"><span data-stu-id="e2749-136">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="e2749-137">移除当您创建项目时生成的 `Service` 类。</span><span class="sxs-lookup"><span data-stu-id="e2749-137">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="e2749-138">将应用程序配置文件添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="e2749-138">Add an application configuration file to the project.</span></span> <span data-ttu-id="e2749-139">将文件内容替换为下面的配置 XML。</span><span class="sxs-lookup"><span data-stu-id="e2749-139">Replace the contents of the file with the following configuration XML.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.serviceModel>    <services>
          <!-- This section is optional with the new configuration model
               introduced in .NET Framework 4. -->
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"
                   behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
            <endpoint address=""
                      binding="wsHttpBinding"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />
          </service>
        </services>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceMetadata httpGetEnabled="true"/>
              <serviceDebug includeExceptionDetailInFaults="False"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>
      </system.serviceModel>
    </configuration>
    ```

     <span data-ttu-id="e2749-140">右键单击 **解决方案资源管理器** 中的 App.config 文件，然后选择 " **属性**"。</span><span class="sxs-lookup"><span data-stu-id="e2749-140">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="e2749-141">在 " **复制到输出目录** " 下，选择 " **如果较新则复制**"</span><span class="sxs-lookup"><span data-stu-id="e2749-141">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="e2749-142">此示例显式指定配置文件中的终结点。</span><span class="sxs-lookup"><span data-stu-id="e2749-142">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="e2749-143">如果您不希望向服务添加任何终结点，则运行时为您添加默认终结点。</span><span class="sxs-lookup"><span data-stu-id="e2749-143">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="e2749-144">在此示例中，由于服务的 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 设置为 `true`，因此服务还启用了发布元数据。</span><span class="sxs-lookup"><span data-stu-id="e2749-144">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="e2749-145">有关默认终结点、绑定和行为的详细信息，请参阅[简化配置](../simplified-configuration.md)和 [WCF 服务的简化配置](../samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e2749-145">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="e2749-146">安装并运行服务</span><span class="sxs-lookup"><span data-stu-id="e2749-146">Install and run the service</span></span>

1. <span data-ttu-id="e2749-147">生成解决方案以创建 `Service.exe` 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="e2749-147">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="e2749-148">打开 Visual Studio 开发人员命令提示，并导航到项目目录。</span><span class="sxs-lookup"><span data-stu-id="e2749-148">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="e2749-149">在命令提示符处键入 `installutil bin\service.exe` 来安装 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="e2749-149">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="e2749-150">在命令提示符处键入 `services.msc` 以访问服务控制管理器 (SCM)。</span><span class="sxs-lookup"><span data-stu-id="e2749-150">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="e2749-151">Windows 服务应作为“WCFWindowsServiceSample”出现在服务中。</span><span class="sxs-lookup"><span data-stu-id="e2749-151">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="e2749-152">如果 Windows 服务正在运行，WCF 服务只能响应客户端。</span><span class="sxs-lookup"><span data-stu-id="e2749-152">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="e2749-153">若要启动该服务，请在 SCM 中右键单击该服务并选择 "启动"，或在命令提示符下键入 **net Start WCFWindowsServiceSample** 。</span><span class="sxs-lookup"><span data-stu-id="e2749-153">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="e2749-154">如果对服务进行更改，则必须首先停止并卸载服务。</span><span class="sxs-lookup"><span data-stu-id="e2749-154">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="e2749-155">若要停止该服务，请在 SCM 中右键单击该服务并选择 "停止"，或在命令提示符下 **键入 net Stop WCFWindowsServiceSample** 。</span><span class="sxs-lookup"><span data-stu-id="e2749-155">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="e2749-156">请注意，如果停止 Windows 服务然后运行客户端，则在客户端尝试访问该服务时，会发生 <xref:System.ServiceModel.EndpointNotFoundException> 异常。</span><span class="sxs-lookup"><span data-stu-id="e2749-156">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="e2749-157">若要卸载 Windows 服务，请在命令提示符下键入 **installutil.exe/u bin\service.exe** 。</span><span class="sxs-lookup"><span data-stu-id="e2749-157">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="e2749-158">示例</span><span class="sxs-lookup"><span data-stu-id="e2749-158">Example</span></span>

<span data-ttu-id="e2749-159">下面是本主题使用的完整代码列表：</span><span class="sxs-lookup"><span data-stu-id="e2749-159">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="e2749-160">与“自承载”选项一样，Windows 服务主机环境要求写入一些宿主代码作为应用程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="e2749-160">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="e2749-161">该服务作为控制台应用程序实现，且包含其自己的主机代码。</span><span class="sxs-lookup"><span data-stu-id="e2749-161">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="e2749-162">在其他主机环境（如 Internet 信息服务 (IIS) 中的 Windows 进程激活服务 (WAS) 主机）中，开发人员没有必要编写主机代码。</span><span class="sxs-lookup"><span data-stu-id="e2749-162">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2749-163">请参阅</span><span class="sxs-lookup"><span data-stu-id="e2749-163">See also</span></span>

- [<span data-ttu-id="e2749-164">简化配置</span><span class="sxs-lookup"><span data-stu-id="e2749-164">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="e2749-165">在托管应用程序中承载</span><span class="sxs-lookup"><span data-stu-id="e2749-165">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)
- [<span data-ttu-id="e2749-166">承载服务</span><span class="sxs-lookup"><span data-stu-id="e2749-166">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="e2749-167">[Windows Server App Fabric 承载功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e2749-167">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
