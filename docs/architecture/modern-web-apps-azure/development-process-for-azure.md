---
title: Azure 的开发过程
description: 使用 ASP.NET Core 和 Azure 构建新式 Web 应用程序 | Azure 的开发过程
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 8907c63f8dcd57ec22c3c196cbb1db52d91a3b5f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169032"
---
# <a name="development-process-for-azure"></a><span data-ttu-id="a22ee-103">Azure 的开发过程</span><span class="sxs-lookup"><span data-stu-id="a22ee-103">Development process for Azure</span></span>

> <span data-ttu-id="a22ee-104">“凭借云，个体和小型企业可轻松无忧地立即建立企业级服务。” </span><span class="sxs-lookup"><span data-stu-id="a22ee-104">_"With the cloud, individuals and small businesses can snap their fingers and instantly set up enterprise-class services."_</span></span>  
> <span data-ttu-id="a22ee-105">\- Roy Stephan </span><span class="sxs-lookup"><span data-stu-id="a22ee-105">_- Roy Stephan_</span></span>

## <a name="vision"></a><span data-ttu-id="a22ee-106">愿景</span><span class="sxs-lookup"><span data-stu-id="a22ee-106">Vision</span></span>

> <span data-ttu-id="a22ee-107">使用 Visual Studio、dotnet CLI、Visual Studio Code 或所选用的编辑器，按照自己喜欢的方式开发出设计优良的 ASP .NET Core 应用程序。 </span><span class="sxs-lookup"><span data-stu-id="a22ee-107">*Develop well-designed ASP .NET Core applications the way you like, using Visual Studio or the dotnet CLI and Visual Studio Code or your editor of choice.*</span></span>

## <a name="development-environment-for-aspnet-core-apps"></a><span data-ttu-id="a22ee-108">ASP.NET Core 应用的开发环境</span><span class="sxs-lookup"><span data-stu-id="a22ee-108">Development environment for ASP.NET Core apps</span></span>

### <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="a22ee-109">开发工具选择：IDE 或编辑器</span><span class="sxs-lookup"><span data-stu-id="a22ee-109">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="a22ee-110">无论你更青睐内容丰富、功能强大的 IDE 还是灵活轻量的编辑器，Microsoft 都可为你提供用于开发 ASP.NET Core 应用程序的工具。</span><span class="sxs-lookup"><span data-stu-id="a22ee-110">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when developing ASP.NET Core applications.</span></span>

<span data-ttu-id="a22ee-111">**Visual Studio 2019。**</span><span class="sxs-lookup"><span data-stu-id="a22ee-111">**Visual Studio 2019.**</span></span> <span data-ttu-id="a22ee-112">Visual Studio 2019 是用于开发适用于 ASP.NET Core 的应用程序的同类最佳 IDE。</span><span class="sxs-lookup"><span data-stu-id="a22ee-112">Visual Studio 2019 is the best-in-class IDE for developing applications for ASP.NET Core.</span></span> <span data-ttu-id="a22ee-113">它提供了多种可提高开发人员生产率的功能。</span><span class="sxs-lookup"><span data-stu-id="a22ee-113">It offers a host of features that increase developer productivity.</span></span> <span data-ttu-id="a22ee-114">可以使用它来开发应用程序，然后分析其性能和其他特征。</span><span class="sxs-lookup"><span data-stu-id="a22ee-114">You can use it to develop the application, then analyze its performance and other characteristics.</span></span> <span data-ttu-id="a22ee-115">借助集成的调试程序，你可以暂停代码执行，并在运行时在代码中来回切换。</span><span class="sxs-lookup"><span data-stu-id="a22ee-115">The integrated debugger lets you pause code execution and step back and forth through code on the fly as it's running.</span></span> <span data-ttu-id="a22ee-116">借助内置的测试运行程序，你可以组织测试及其结果，甚至可以在编写代码时执行实时单元测试。</span><span class="sxs-lookup"><span data-stu-id="a22ee-116">The built-in test runner lets you organize your tests and their results and can even perform live unit testing while you're coding.</span></span> <span data-ttu-id="a22ee-117">使用 Live Share，可以与其他开发人员进行实时协作，并通过网络无缝共享代码会话。</span><span class="sxs-lookup"><span data-stu-id="a22ee-117">Using Live Share, you can collaborate in real time with other developers, sharing your code session seamlessly over the network.</span></span> <span data-ttu-id="a22ee-118">准备就绪后，Visual Studio 包括了将应用程序发布到 Azure 所需的所有内容或任何可托管它的位置。</span><span class="sxs-lookup"><span data-stu-id="a22ee-118">And when you're ready, Visual Studio includes everything you need to publish your application to Azure or wherever you might host it.</span></span>

[<span data-ttu-id="a22ee-119">下载 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="a22ee-119">Download Visual Studio 2019</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

<span data-ttu-id="a22ee-120">**Visual Studio Code 和 dotnet CLI**（适用于 Mac、Linux 和 Windows 的跨平台工具）。</span><span class="sxs-lookup"><span data-stu-id="a22ee-120">**Visual Studio Code and dotnet CLI** (Cross-Platform Tools for Mac, Linux and Windows).</span></span> <span data-ttu-id="a22ee-121">如果更青睐支持任何开发语言的轻量级跨平台编辑器，可以使用 Microsoft Visual Studio Code 和 the dotnet CLI。</span><span class="sxs-lookup"><span data-stu-id="a22ee-121">If you prefer a lightweight and cross-platform editor supporting any development language, you can use Microsoft Visual Studio Code and the dotnet CLI.</span></span> <span data-ttu-id="a22ee-122">这些产品提供简单但可靠的体验，可以简化开发人员工作流。</span><span class="sxs-lookup"><span data-stu-id="a22ee-122">These products provide a simple yet robust experience that streamlines the developer workflow.</span></span> <span data-ttu-id="a22ee-123">此外，Visual Studio Code 支持适用于 C\# 和 Web 开发的扩展，在该编辑器内提供智能感知和快捷任务。</span><span class="sxs-lookup"><span data-stu-id="a22ee-123">Additionally, Visual Studio Code supports extensions for C\# and web development, providing intellisense and shortcut-tasks within the editor.</span></span>

[<span data-ttu-id="a22ee-124">下载 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a22ee-124">Download the .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

[<span data-ttu-id="a22ee-125">下载 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a22ee-125">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a><span data-ttu-id="a22ee-126">Azure 托管型 ASP.NET Core 应用的开发工作流</span><span class="sxs-lookup"><span data-stu-id="a22ee-126">Development workflow for Azure-hosted ASP.NET Core apps</span></span>

<span data-ttu-id="a22ee-127">应用程序开发生命周期始于每位开发人员的计算机，开发人员使用其首选语言对应用进行编码和本地测试。</span><span class="sxs-lookup"><span data-stu-id="a22ee-127">The application development lifecycle starts from each developer's machine, coding the app using their preferred language and testing it locally.</span></span> <span data-ttu-id="a22ee-128">开发人员可选择其青睐的源代码管理系统，并可使用生成服务器或基于内置 Azure 功能配置持续集成 (CI) 和/或持续交付/部署 (CD)。</span><span class="sxs-lookup"><span data-stu-id="a22ee-128">Developers may choose their preferred source control system and can configure Continuous Integration (CI) and/or Continuous Delivery/Deployment (CD) using a build server or based on built-in Azure features.</span></span>

<span data-ttu-id="a22ee-129">若要开始使用 CI/CD 开发 ASP.NET Core 应用程序，可使用 Azure DevOps Services 或组织自身的 Team Foundation Server (TFS)。</span><span class="sxs-lookup"><span data-stu-id="a22ee-129">To get started with developing an ASP.NET Core application using CI/CD, you can use Azure DevOps Services or your organization's own Team Foundation Server (TFS).</span></span>

### <a name="initial-setup"></a><span data-ttu-id="a22ee-130">初始设置</span><span class="sxs-lookup"><span data-stu-id="a22ee-130">Initial setup</span></span>

<span data-ttu-id="a22ee-131">若要为应用创建发布管道，需要具备源代码管理中的应用程序代码。</span><span class="sxs-lookup"><span data-stu-id="a22ee-131">To create a release pipeline for your app, you need to have your application code in source control.</span></span> <span data-ttu-id="a22ee-132">设置一个本地存储库，并将其连接到团队项目中的远程存储库。</span><span class="sxs-lookup"><span data-stu-id="a22ee-132">Set up a local repository and connect it to a remote repository in a team project.</span></span> <span data-ttu-id="a22ee-133">请按照以下说明执行操作：</span><span class="sxs-lookup"><span data-stu-id="a22ee-133">Follow these instructions:</span></span>

- <span data-ttu-id="a22ee-134">[使用 Git 和 Visual Studio 分享代码](/azure/devops/git/share-your-code-in-git-vs)或</span><span class="sxs-lookup"><span data-stu-id="a22ee-134">[Share your code with Git and Visual Studio](/azure/devops/git/share-your-code-in-git-vs) or</span></span>

- [<span data-ttu-id="a22ee-135">使用 TFVC 和 Visual Studio 分享代码</span><span class="sxs-lookup"><span data-stu-id="a22ee-135">Share your code with TFVC and Visual Studio</span></span>](/azure/devops/tfvc/share-your-code-in-tfvc-vs)

<span data-ttu-id="a22ee-136">创建要在其中部署应用程序的 Azure 应用服务。</span><span class="sxs-lookup"><span data-stu-id="a22ee-136">Create an Azure App Service where you'll deploy your application.</span></span> <span data-ttu-id="a22ee-137">转至 Azure 门户上的“应用服务”选项卡，创建一个 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="a22ee-137">Create a Web App by going to the App Services blade on the Azure portal.</span></span> <span data-ttu-id="a22ee-138">单击“+添加”，选择 Web 应用模板，单击“创建”并提供名称或其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="a22ee-138">Click +Add, select the Web App template, click Create, and provide a name and other details.</span></span> <span data-ttu-id="a22ee-139">该 Web 应用可通过 {name}.azurewebsites.net 进行访问。</span><span class="sxs-lookup"><span data-stu-id="a22ee-139">The web app will be accessible from {name}.azurewebsites.net.</span></span>

![AzureWebApp](./media/image10-2.png)

<span data-ttu-id="a22ee-141">**图 10-1.**</span><span class="sxs-lookup"><span data-stu-id="a22ee-141">**Figure 10-1.**</span></span> <span data-ttu-id="a22ee-142">在 Azure 门户中创建新的 Azure 应用服务 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="a22ee-142">Creating a new Azure App Service Web App in the Azure Portal.</span></span>

<span data-ttu-id="a22ee-143">无论新代码何时提交至项目的源代码管理存储库，CI 生成过程均会执行自动生成。</span><span class="sxs-lookup"><span data-stu-id="a22ee-143">Your CI build process will perform an automated build whenever new code is committed to the project's source control repository.</span></span> <span data-ttu-id="a22ee-144">由此你可获得即时反馈，知悉代码已生成（且理想情况下可通过自动测试），并且或许可进行部署。</span><span class="sxs-lookup"><span data-stu-id="a22ee-144">This gives you immediate feedback that the code builds (and, ideally, passes automated tests) and can potentially be deployed.</span></span> <span data-ttu-id="a22ee-145">此 CI 生成将生成一个 Web 部署包项目，并将其发布，以供 CD 进程使用。</span><span class="sxs-lookup"><span data-stu-id="a22ee-145">This CI build will produce a web deploy package artifact and publish it for consumption by your CD process.</span></span>

[<span data-ttu-id="a22ee-146">定义 CI 生成过程</span><span class="sxs-lookup"><span data-stu-id="a22ee-146">Define your CI build process</span></span>](/azure/devops/pipelines/ecosystems/dotnet-core)

<span data-ttu-id="a22ee-147">请务必启用持续集成，从而使得无论何时团队成员提交新代码，系统均可将生成排队。</span><span class="sxs-lookup"><span data-stu-id="a22ee-147">Be sure to enable continuous integration so the system will queue a build whenever someone on your team commits new code.</span></span> <span data-ttu-id="a22ee-148">测试该生成，并验证其是否生成 Web 部署包作为其中一个项目。</span><span class="sxs-lookup"><span data-stu-id="a22ee-148">Test the build and verify that it is producing a web deploy package as one of its artifacts.</span></span>

<span data-ttu-id="a22ee-149">生成成功后，CD 过程会将 CI 生成结果部署到 Azure Web 应用。</span><span class="sxs-lookup"><span data-stu-id="a22ee-149">When a build succeeds, your CD process will deploy the results of your CI build to your Azure web app.</span></span> <span data-ttu-id="a22ee-150">如需对其配置，请创建并配置一个 Release（它将部署到 Azure 应用服务）。 </span><span class="sxs-lookup"><span data-stu-id="a22ee-150">To configure this, you create and configure a *Release*, which will deploy to your Azure App Service.</span></span>

[<span data-ttu-id="a22ee-151">部署 Azure web 应用</span><span class="sxs-lookup"><span data-stu-id="a22ee-151">Deploy an Azure web app</span></span>](/azure/devops/pipelines/targets/webapp)

<span data-ttu-id="a22ee-152">配置 CI/CD 管道后，即可更新 Web 应用，并将更新提交至源代码管理以进行部署。</span><span class="sxs-lookup"><span data-stu-id="a22ee-152">Once your CI/CD pipeline is configured, you can simply make updates to your web app and commit them to source control to have them deployed.</span></span>

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a><span data-ttu-id="a22ee-153">开发 Azure 托管型 ASP.NET Core 应用程序的工作流</span><span class="sxs-lookup"><span data-stu-id="a22ee-153">Workflow for developing Azure-hosted ASP.NET Core applications</span></span>

<span data-ttu-id="a22ee-154">配置 Azure 帐户和 CI/CD 过程后，即可轻松开发 Azure 托管的 ASP.NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="a22ee-154">Once you have configured your Azure account and your CI/CD process, developing Azure-hosted ASP.NET Core applications is simple.</span></span> <span data-ttu-id="a22ee-155">生成 ASP.NET Core 应用并将其托管在 Azure 应用服务作为 Web 应用时，通常会采用以下基本步骤，如图 10-2 所示。</span><span class="sxs-lookup"><span data-stu-id="a22ee-155">The following are the basic steps you usually take when building an ASP.NET Core app, hosted in Azure App Service as a Web App, as illustrated in Figure 10-2.</span></span>

![EndToEndDevDeployWorkflow](./media/image10-3.png)

<span data-ttu-id="a22ee-157">**图 10-2.**</span><span class="sxs-lookup"><span data-stu-id="a22ee-157">**Figure 10-2.**</span></span> <span data-ttu-id="a22ee-158">构建 ASP.NET Core 应用以及将应用于托管于 Azure 的分步工作流</span><span class="sxs-lookup"><span data-stu-id="a22ee-158">Step-by-step workflow for building ASP.NET Core apps and hosting them in Azure</span></span>

#### <a name="step-1-local-dev-environment-inner-loop"></a><span data-ttu-id="a22ee-159">步骤 1。</span><span class="sxs-lookup"><span data-stu-id="a22ee-159">Step 1.</span></span> <span data-ttu-id="a22ee-160">本地开发环境内循环</span><span class="sxs-lookup"><span data-stu-id="a22ee-160">Local dev environment inner loop</span></span>

<span data-ttu-id="a22ee-161">开发要部署到 Azure 的 ASP.NET Core 应用程序与开发其他程序并无不同。</span><span class="sxs-lookup"><span data-stu-id="a22ee-161">Developing your ASP.NET Core application for deployment to Azure is no different from developing your application otherwise.</span></span> <span data-ttu-id="a22ee-162">使用惯用的本地开发环境，无论是 Visual Studio 2017、dotnet CLI、Visual Studio Code 还是个人首选的编辑器。</span><span class="sxs-lookup"><span data-stu-id="a22ee-162">Use the local development environment you're comfortable with, whether that's Visual Studio 2017 or the dotnet CLI and Visual Studio Code or your preferred editor.</span></span> <span data-ttu-id="a22ee-163">在准备将更改推送到共享源代码存储库前，可以编写代码、运行并调试更改、运行自动测试以及本地提交到源代码管理。</span><span class="sxs-lookup"><span data-stu-id="a22ee-163">You can write code, run and debug your changes, run automated tests, and make local commits to source control until you're ready to push your changes to your shared source control repository.</span></span>

#### <a name="step-2-application-code-repository"></a><span data-ttu-id="a22ee-164">步骤 2。</span><span class="sxs-lookup"><span data-stu-id="a22ee-164">Step 2.</span></span> <span data-ttu-id="a22ee-165">应用程序代码存储库</span><span class="sxs-lookup"><span data-stu-id="a22ee-165">Application code repository</span></span>

<span data-ttu-id="a22ee-166">无论何时准备与团队共享代码，均应将更改从本地源存储库中推送到团队共享源存储库。</span><span class="sxs-lookup"><span data-stu-id="a22ee-166">Whenever you're ready to share your code with your team, you should push your changes from your local source repository to your team's shared source repository.</span></span> <span data-ttu-id="a22ee-167">如果一直在自定义分支中工作，此步骤通常涉及将代码合并到共享分支中（或许通过[拉取请求](/azure/devops/git/pull-requests)方式）。</span><span class="sxs-lookup"><span data-stu-id="a22ee-167">If you've been working in a custom branch, this step usually involves merging your code into a shared branch (perhaps by means of a [pull request](/azure/devops/git/pull-requests)).</span></span>

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a><span data-ttu-id="a22ee-168">步骤 3。</span><span class="sxs-lookup"><span data-stu-id="a22ee-168">Step 3.</span></span> <span data-ttu-id="a22ee-169">生成服务器：持续集成。</span><span class="sxs-lookup"><span data-stu-id="a22ee-169">Build Server: Continuous integration.</span></span> <span data-ttu-id="a22ee-170">生成、测试、打包</span><span class="sxs-lookup"><span data-stu-id="a22ee-170">build, test, package</span></span>

<span data-ttu-id="a22ee-171">向共享应用程序代码存储库进行新的提交时，生成服务器上会触发新的生成。</span><span class="sxs-lookup"><span data-stu-id="a22ee-171">A new build is triggered on the build server whenever a new commit is made to the shared application code repository.</span></span> <span data-ttu-id="a22ee-172">作为 CI 过程的一部分，该生成应充分编译应用程序，并运行自动测试以确定一切正常。</span><span class="sxs-lookup"><span data-stu-id="a22ee-172">As part of the CI process, this build should fully compile the application and run automated tests to confirm everything is working as expected.</span></span> <span data-ttu-id="a22ee-173">CI 过程的最终结果应是已可部署的打包版 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="a22ee-173">The end result of the CI process should be a packaged version of the web app, ready for deployment.</span></span>

#### <a name="step-4-build-server-continuous-delivery"></a><span data-ttu-id="a22ee-174">步骤 4。</span><span class="sxs-lookup"><span data-stu-id="a22ee-174">Step 4.</span></span> <span data-ttu-id="a22ee-175">生成服务器：持续交付</span><span class="sxs-lookup"><span data-stu-id="a22ee-175">Build Server: Continuous delivery</span></span>

<span data-ttu-id="a22ee-176">生成成功后，CD 过程将选取产生的生成项目。</span><span class="sxs-lookup"><span data-stu-id="a22ee-176">Once a build has succeeded, the CD process will pick up the build artifacts produced.</span></span> <span data-ttu-id="a22ee-177">其中包括一个 Web 部署包。</span><span class="sxs-lookup"><span data-stu-id="a22ee-177">This will include a web deploy package.</span></span> <span data-ttu-id="a22ee-178">生成服务器将此包部署到 Azure 应用服务，使用新创建的服务替换任何现有服务。</span><span class="sxs-lookup"><span data-stu-id="a22ee-178">The build server will deploy this package to Azure App Service, replacing any existing service with the newly created one.</span></span> <span data-ttu-id="a22ee-179">通常该步骤面向过渡环境，但是部分应用程序通过 CD 过程直接部署到生产。</span><span class="sxs-lookup"><span data-stu-id="a22ee-179">Typically this step targets a staging environment, but some applications deploy directly to production through a CD process.</span></span>

#### <a name="step-5-azure-app-service-web-app"></a><span data-ttu-id="a22ee-180">步骤 5。</span><span class="sxs-lookup"><span data-stu-id="a22ee-180">Step 5.</span></span> <span data-ttu-id="a22ee-181">Azure 应用服务 Web 应用</span><span class="sxs-lookup"><span data-stu-id="a22ee-181">Azure App Service Web App</span></span>

<span data-ttu-id="a22ee-182">部署后，ASP.NET Core 应用程序在 Azure 应用服务 Web 应用的上下文运行。</span><span class="sxs-lookup"><span data-stu-id="a22ee-182">Once deployed, the ASP.NET Core application runs within the context of an Azure App Service Web App.</span></span> <span data-ttu-id="a22ee-183">可使用 Azure 门户监视以及进一步配置该 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="a22ee-183">This Web App can be monitored and further configured using the Azure Portal.</span></span>

#### <a name="step-6-production-monitoring-and-diagnostics"></a><span data-ttu-id="a22ee-184">步骤 6。</span><span class="sxs-lookup"><span data-stu-id="a22ee-184">Step 6.</span></span> <span data-ttu-id="a22ee-185">生产监视和诊断</span><span class="sxs-lookup"><span data-stu-id="a22ee-185">Production monitoring and diagnostics</span></span>

<span data-ttu-id="a22ee-186">该 Web 应用运行时，可监视该应用程序的运行状况，并收集诊断和用户行为数据。</span><span class="sxs-lookup"><span data-stu-id="a22ee-186">While the Web App is running, you can monitor the health of the application and collect diagnostics and user behavior data.</span></span> <span data-ttu-id="a22ee-187">Application Insights 包含于 Visual Studio 中，为 ASP.NET 应用提供自动检测。</span><span class="sxs-lookup"><span data-stu-id="a22ee-187">Application Insights is included in Visual Studio, and offers automatic instrumentation for ASP.NET apps.</span></span> <span data-ttu-id="a22ee-188">它可提供有关使用情况、异常、请求、性能和日志的信息。</span><span class="sxs-lookup"><span data-stu-id="a22ee-188">It can provide you with information on usage, exceptions, requests, performance, and logs.</span></span>

## <a name="references"></a><span data-ttu-id="a22ee-189">参考资料</span><span class="sxs-lookup"><span data-stu-id="a22ee-189">References</span></span>

<span data-ttu-id="a22ee-190">**构建 ASP.NET Core 应用并将其部署到 Azure**</span><span class="sxs-lookup"><span data-stu-id="a22ee-190">**Build and Deploy Your ASP.NET Core App to Azure**</span></span>  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
><span data-ttu-id="a22ee-191">[上一页](test-asp-net-core-mvc-apps.md)
>[下一页](azure-hosting-recommendations-for-asp-net-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a22ee-191">[Previous](test-asp-net-core-mvc-apps.md)
[Next](azure-hosting-recommendations-for-asp-net-web-apps.md)</span></span>
