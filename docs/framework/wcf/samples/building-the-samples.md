---
title: 生成 Windows Communication Foundation 示例
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 53599b3b1827651b48df9921bb59a679a36ee39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592614"
---
# <a name="building-the-windows-communication-foundation-samples"></a><span data-ttu-id="18228-102">生成 Windows Communication Foundation 示例</span><span class="sxs-lookup"><span data-stu-id="18228-102">Building the Windows Communication Foundation Samples</span></span>

<span data-ttu-id="18228-103">可以使用 Visual Studio IDE 或从命令行使用**msbuild**命令生成 WINDOWS COMMUNICATION FOUNDATION （WCF）示例。</span><span class="sxs-lookup"><span data-stu-id="18228-103">The Windows Communication Foundation (WCF) samples can be built using the Visual Studio IDE or using the **msbuild** command from the command line.</span></span> <span data-ttu-id="18228-104">本主题介绍这两个过程。</span><span class="sxs-lookup"><span data-stu-id="18228-104">Both procedures are described in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="18228-105">在生成或运行任何 WCF 示例之前，请确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="18228-105">Before building or running any of the WCF samples, ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

## <a name="to-build-the-sample-using-a-command-prompt"></a><span data-ttu-id="18228-106">使用命令提示生成示例</span><span class="sxs-lookup"><span data-stu-id="18228-106">To build the sample using a command prompt</span></span>

1. <span data-ttu-id="18228-107">打开 Visual Studio 开发人员命令提示，并导航到安装示例的目录位置下语言特定的子目录。</span><span class="sxs-lookup"><span data-stu-id="18228-107">Open Developer Command Prompt for Visual Studio and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="18228-108">`msbuild`在命令行中键入。</span><span class="sxs-lookup"><span data-stu-id="18228-108">Type `msbuild` at the command line.</span></span> <span data-ttu-id="18228-109">将为*client\bin*生成客户端程序文件，并将服务程序文件构建到*service\bin*中。</span><span class="sxs-lookup"><span data-stu-id="18228-109">The client program files are built to *client\bin* and the service program files are built to *service\bin*.</span></span> <span data-ttu-id="18228-110">如果服务由 Internet Information Services （IIS）承载，服务程序文件也会复制到*servicemodelsamples*目录及其*\bin*子目录中。</span><span class="sxs-lookup"><span data-stu-id="18228-110">If the service is hosted by Internet Information Services (IIS), the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="18228-111">必须在 *%systemdrive%\inetpub\wwwroot*上设置 acl，才能向运行的帐户授予 "修改" 权限。</span><span class="sxs-lookup"><span data-stu-id="18228-111">You must set the ACLs on *%systemdrive%\inetpub\wwwroot* to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="18228-112">否则，某些后期生成事件将失败。</span><span class="sxs-lookup"><span data-stu-id="18228-112">Otherwise some post build events fail.</span></span> <span data-ttu-id="18228-113">或者，您可以将 ACL 保留原样，而以管理员身份运行 SDK 命令提示。</span><span class="sxs-lookup"><span data-stu-id="18228-113">Alternatively, you can leave the ACLs as they are and run the SDK command prompt as administrator.</span></span>

## <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="18228-114">使用 Visual Studio 生成示例</span><span class="sxs-lookup"><span data-stu-id="18228-114">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="18228-115">在 Visual Studio 的 "**文件**" 菜单中，选择 "**打开**  >  **项目/解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="18228-115">From the **File** menu in Visual Studio, select **Open** > **Project/Solution**.</span></span> <span data-ttu-id="18228-116">导航到安装示例的目录下特定于语言的子目录，然后双击 .sln 文件图标，在 Visual Studio 中打开该解决方案。</span><span class="sxs-lookup"><span data-stu-id="18228-116">Navigate to the language-specific subdirectory under the directory in which you installed the sample, and double-click the .sln file icon to open the solution in Visual Studio.</span></span>

1. <span data-ttu-id="18228-117">在 "**生成**" 菜单中，选择 "**重新生成解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="18228-117">From the **Build** menu, select **Rebuild Solution**.</span></span>

   <span data-ttu-id="18228-118">客户端程序文件在 client\bin 中生成，服务程序文件在 service\bin 中生成。</span><span class="sxs-lookup"><span data-stu-id="18228-118">The client program files are built to client\bin and the service program files are built to service\bin.</span></span> <span data-ttu-id="18228-119">如果服务在 IIS 中承载，则服务程序文件也会复制到*servicemodelsamples*目录及其*\bin*子目录中。</span><span class="sxs-lookup"><span data-stu-id="18228-119">If the service is hosted in IIS, the service program files are also copied to the *servicemodelsamples* directory and its *\bin* subdirectory.</span></span>

> [!NOTE]
> <span data-ttu-id="18228-120">您必须在 %systemdrive%\inetpub\wwwroot 上设置 ACL，以便为您运行的帐户授予修改权限。</span><span class="sxs-lookup"><span data-stu-id="18228-120">You must set the ACLs on %systemdrive%\inetpub\wwwroot to grant modify permissions to the account under which you are running.</span></span> <span data-ttu-id="18228-121">否则，某些后期生成事件将失败。</span><span class="sxs-lookup"><span data-stu-id="18228-121">Otherwise some post build events fail.</span></span> <span data-ttu-id="18228-122">或者，您可以将 ACL 保留原样，而以管理员身份运行 SDK 命令提示或 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="18228-122">Alternatively, you can leave the ACLs as they are and run the SDK command prompt or Visual Studio as administrator.</span></span> <span data-ttu-id="18228-123">某些 Visual Studio 操作（例如，为 ASP.Net 工作进程附加调试器）也需要管理特权。</span><span class="sxs-lookup"><span data-stu-id="18228-123">Some Visual Studio actions (such as attaching a debugger to the ASP.Net worker process) also require administrative privileges.</span></span>

## <a name="setup-batch-files-and-scripts"></a><span data-ttu-id="18228-124">设置批处理文件和脚本</span><span class="sxs-lookup"><span data-stu-id="18228-124">Setup Batch Files and Scripts</span></span>
 <span data-ttu-id="18228-125">Setup.exe 和 notepad.exe 批处理文件和脚本应从 Visual Studio 开发人员命令提示中运行。</span><span class="sxs-lookup"><span data-stu-id="18228-125">Setup.exe and Cleanup.exe batch files and scripts should be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="18228-126">有几个设置和清理文件将执行需要具有管理特权的任务，应使用管理特权来启动它们。</span><span class="sxs-lookup"><span data-stu-id="18228-126">Several set up and clean up files perform tasks that require administrative privileges and should be launched with administrator privileges.</span></span>

## <a name="important-security-information-about-metadata-endpoints"></a><span data-ttu-id="18228-127">有关元数据终结点的重要安全信息</span><span class="sxs-lookup"><span data-stu-id="18228-127">Important Security Information about Metadata Endpoints</span></span>
 <span data-ttu-id="18228-128">为了避免无意中泄漏可能敏感的服务元数据，Windows Communication Foundation （WCF）服务的默认配置将禁用元数据发布。</span><span class="sxs-lookup"><span data-stu-id="18228-128">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="18228-129">默认情况下此行为是安全的，但也意味着你无法使用元数据导入工具（例如 Svcutil.exe）生成调用服务所需的客户端代码，除非在配置中显式启用服务的元数据发布行为。</span><span class="sxs-lookup"><span data-stu-id="18228-129">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="18228-130">为了使示例体验更简单，几乎所有示例都公开一个不安全的元数据发布终结点。</span><span class="sxs-lookup"><span data-stu-id="18228-130">To make experimenting with the samples easier, almost all samples expose an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="18228-131">此类终结点或许可以供未通过身份验证的匿名使用者使用，因此在部署此类终结点之前，必须谨慎以确保适合公开透露服务元数据。</span><span class="sxs-lookup"><span data-stu-id="18228-131">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="18228-132">有关发布服务元数据的详细信息，请参阅[元数据发布行为](metadata-publishing-behavior.md)示例。</span><span class="sxs-lookup"><span data-stu-id="18228-132">For more information about publishing service metadata, see the [Metadata Publishing Behavior](metadata-publishing-behavior.md) sample.</span></span> <span data-ttu-id="18228-133">有关保护元数据终结点的示例，请参阅[自定义安全元数据终结点](custom-secure-metadata-endpoint.md)示例。</span><span class="sxs-lookup"><span data-stu-id="18228-133">See the [Custom Secure Metadata Endpoint](custom-secure-metadata-endpoint.md) sample for a sample securing a metadata endpoint.</span></span>

## <a name="exception-handling"></a><span data-ttu-id="18228-134">异常处理</span><span class="sxs-lookup"><span data-stu-id="18228-134">Exception Handling</span></span>
 <span data-ttu-id="18228-135">一般来说，这些示例不包括异常处理，以使代码集中处理示例的主题。</span><span class="sxs-lookup"><span data-stu-id="18228-135">Generally speaking these samples do not include exception handling to keep the code focused on the subject of the sample.</span></span> <span data-ttu-id="18228-136">有关异常处理的详细信息，请参阅[预期异常](expected-exceptions.md)示例。</span><span class="sxs-lookup"><span data-stu-id="18228-136">For more information about exception handling, see the [Expected Exceptions](expected-exceptions.md) sample.</span></span>

## <a name="regenerating-clients-and-configuration-with-svcutil"></a><span data-ttu-id="18228-137">使用 Svcutil 重新生成客户端和配置</span><span class="sxs-lookup"><span data-stu-id="18228-137">Regenerating Clients and Configuration with Svcutil</span></span>
 <span data-ttu-id="18228-138">您可以使用 "配置[元数据实用工具（svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md) " 为大多数示例重新生成客户端代码和配置。</span><span class="sxs-lookup"><span data-stu-id="18228-138">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to regenerate client code and configuration for most of the samples.</span></span> <span data-ttu-id="18228-139">某些示例需要手动编辑的配置。</span><span class="sxs-lookup"><span data-stu-id="18228-139">Some samples require manually edited configuration.</span></span> <span data-ttu-id="18228-140">例如，如果您使用 Svcutil.exe 为某个使用客户端证书凭据的示例重新生成配置，必须手动指定之前配置的凭据。</span><span class="sxs-lookup"><span data-stu-id="18228-140">For example, if you use Svcutil.exe to regenerate the configuration for a sample that uses client certificate credentials, you must manually specify the credentials previously configured.</span></span> <span data-ttu-id="18228-141">某些示例使用特定的 Svcutil.exe 选项来影响生成的代码，这些选项在具体的示例主题中进行指定。</span><span class="sxs-lookup"><span data-stu-id="18228-141">Some samples use specific Svcutil.exe options to affect the generated code, these options are specified in the specific sample topics.</span></span>

### <a name="to-regenerate-the-client-and-configuration-files"></a><span data-ttu-id="18228-142">重新生成客户端和配置文件</span><span class="sxs-lookup"><span data-stu-id="18228-142">To regenerate the client and configuration files</span></span>

1. <span data-ttu-id="18228-143">打开 SDK 命令提示，然后定位到安装示例的目录位置下的语言特定的子目录。</span><span class="sxs-lookup"><span data-stu-id="18228-143">Open an SDK command prompt and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="18228-144">如果服务是 Web 承载的类型，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="18228-144">If the service is a Web-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="18228-145">如果服务是自承载类型，请键入以下命令。</span><span class="sxs-lookup"><span data-stu-id="18228-145">If the service is a self-hosted type the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     <span data-ttu-id="18228-146">替换 `http://localhost:8000/ServiceModelSamples/service.svc/mex` 为自承载服务的 mex 终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="18228-146">Replace `http://localhost:8000/ServiceModelSamples/service.svc/mex` with the address of the self-hosted service's mex endpoint.</span></span>

     <span data-ttu-id="18228-147">若要在 Visual Basic 类型中生成客户端，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="18228-147">To generate the client in a Visual Basic type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     <span data-ttu-id="18228-148">如果服务是自承载类型，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="18228-148">If the service is a self-hosted type, use the following command.</span></span>

    ```console
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > <span data-ttu-id="18228-149">若要跳过客户端配置的生成，请添加 **/noConfig**选项。</span><span class="sxs-lookup"><span data-stu-id="18228-149">To skip the generation of client configuration add the **/noConfig** option.</span></span>

## <a name="see-also"></a><span data-ttu-id="18228-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18228-150">See also</span></span>

- [<span data-ttu-id="18228-151">运行 Windows Communication Foundation 示例</span><span class="sxs-lookup"><span data-stu-id="18228-151">Running the Windows Communication Foundation Samples</span></span>](running-the-samples.md)
- [<span data-ttu-id="18228-152">ServiceModel 元数据实用工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="18228-152">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
