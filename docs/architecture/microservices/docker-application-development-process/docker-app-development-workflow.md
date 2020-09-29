---
title: Docker 应用开发工作流
description: 了解用于开发基于 Docker 的应用程序的工作流的详细信息。 分步深入了解有关优化 Dockerfile 的详细信息，最后了解使用 Visual Studio 时使用的简化工作流。
ms.date: 01/30/2020
ms.openlocfilehash: 04b59a6c30b4fb8f34fe1d0e5cd5328ac77ecb4e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172549"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="88df8-104">Docker 应用开发工作流</span><span class="sxs-lookup"><span data-stu-id="88df8-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="88df8-105">应用程序开发生命周期从你的计算机开始，你作为开发人员在该计算机上使用首选语言对应用程序进行编码和本地测试。</span><span class="sxs-lookup"><span data-stu-id="88df8-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="88df8-106">使用此工作流，无论选择哪种语言、框架和平台，你都可以开发和测试 Docker 容器，但均在本地执行操作。</span><span class="sxs-lookup"><span data-stu-id="88df8-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="88df8-107">每个容器（Docker 映像的实例）都包含以下组成部分：</span><span class="sxs-lookup"><span data-stu-id="88df8-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="88df8-108">操作系统选择（例如，Linux 发行版、Windows Nano Server 或 Windows Server Core）。</span><span class="sxs-lookup"><span data-stu-id="88df8-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="88df8-109">开发过程中添加的文件（例如源代码和应用程序二进制文件）。</span><span class="sxs-lookup"><span data-stu-id="88df8-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="88df8-110">配置信息（例如环境设置和依赖项）。</span><span class="sxs-lookup"><span data-stu-id="88df8-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="88df8-111">开发基于 Docker 容器的应用程序的工作流</span><span class="sxs-lookup"><span data-stu-id="88df8-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="88df8-112">本节介绍基于 Docker 容器的应用程序的内部循环开发工作流  。</span><span class="sxs-lookup"><span data-stu-id="88df8-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="88df8-113">内部循环工作流是指不考虑更广泛的 DevOps 工作流（最多可以包括生产部署），只关注在开发人员的计算机上进行的开发工作。</span><span class="sxs-lookup"><span data-stu-id="88df8-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="88df8-114">其中不包括设置环境的初始步骤，因为这些步骤只需进行一次。</span><span class="sxs-lookup"><span data-stu-id="88df8-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="88df8-115">应用程序由开发人员自己的服务和附加库（依赖项）组成。</span><span class="sxs-lookup"><span data-stu-id="88df8-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="88df8-116">以下是生成 Docker 应用程序时常用的基本步骤，如图 5-1 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="显示创建容器化应用程序所用的 7 个步骤的示意图。":::
<span data-ttu-id="88df8-118">Docker 应用的开发流程：1 - 编写应用代码，2 - 编写 Dockerfile/s，3 - 创建在 Dockerfile/s 上定义的映像，4 -（可选）在 docker-compose.yml 文件中编写服务，5 - 运行容器或 docker-compose 应用，6 - 测试应用或微服务，7 - 推送到存储库并重复操作。</span><span class="sxs-lookup"><span data-stu-id="88df8-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="88df8-119">**图 5-1**。</span><span class="sxs-lookup"><span data-stu-id="88df8-119">**Figure 5-1.**</span></span> <span data-ttu-id="88df8-120">开发 Docker 容器化应用的分步工作流</span><span class="sxs-lookup"><span data-stu-id="88df8-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="88df8-121">本部分详细介绍了整个流程，并着重通过 Visual Studio 环境解释了每个主要步骤。</span><span class="sxs-lookup"><span data-stu-id="88df8-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="88df8-122">使用编辑器/CLI 开发方法（例如，Visual Studio Code 和 macOS 或 Windows 上的 Docker CLI）时，需了解每个步骤，通常需要比使用 Visual Studio 了解得更详细。</span><span class="sxs-lookup"><span data-stu-id="88df8-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="88df8-123">有关在 CLI 环境中进行开发的详细信息，请参阅电子书[Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/)（容器化 Docker 应用程序生命周期与 Microsoft 平台和工具）。</span><span class="sxs-lookup"><span data-stu-id="88df8-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="88df8-124">使用 Visual Studio 2019 时，许多步骤都无需开发人员执行，可显著提高工作效率。</span><span class="sxs-lookup"><span data-stu-id="88df8-124">When you're using Visual Studio 2019, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="88df8-125">使用 Visual Studio 2019 开发多容器应用程序时更是如此。</span><span class="sxs-lookup"><span data-stu-id="88df8-125">This is especially true when you're using Visual Studio 2019 and targeting multi-container applications.</span></span> <span data-ttu-id="88df8-126">例如，只需单击一下，Visual Studio 就会将 `Dockerfile` 和 `docker-compose.yml` 文件添加到含有应用程序配置的项目。</span><span class="sxs-lookup"><span data-stu-id="88df8-126">For instance, with just one mouse click, Visual Studio adds the `Dockerfile` and `docker-compose.yml` file to your projects with the configuration for your application.</span></span> <span data-ttu-id="88df8-127">在 Visual Studio 中运行应用程序时，系统会生成 Docker 映像并在 Docker 中直接运行多容器应用程序；开发人员甚至还能同时调试多个容器。</span><span class="sxs-lookup"><span data-stu-id="88df8-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="88df8-128">这些功能可大大提高开发速度。</span><span class="sxs-lookup"><span data-stu-id="88df8-128">These features will boost your development speed.</span></span>

<span data-ttu-id="88df8-129">但即使 Visual Studio 可以自动执行这些步骤，这也并不意味着开发人员不需要了解 Docker 的工作原理。</span><span class="sxs-lookup"><span data-stu-id="88df8-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="88df8-130">因此，下面的指南详细介绍了每个步骤。</span><span class="sxs-lookup"><span data-stu-id="88df8-130">Therefore, the following guidance details every step.</span></span>

![步骤 1 的映像。](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="88df8-132">步骤 1。</span><span class="sxs-lookup"><span data-stu-id="88df8-132">Step 1.</span></span> <span data-ttu-id="88df8-133">开始编码并创建初始应用程序或服务基线</span><span class="sxs-lookup"><span data-stu-id="88df8-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="88df8-134">开发 Docker 应用程序的方式与开发不带 Docker 的应用程序的方式类似。</span><span class="sxs-lookup"><span data-stu-id="88df8-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="88df8-135">二者的区别在于，开发 Docker 应用程序时，是在本地环境中部署和测试在 Docker 容器中运行的应用程序或服务（由 Docker 设置的 Linux VM，或者如果使用 Windows 容器，则直接是 Windows）。</span><span class="sxs-lookup"><span data-stu-id="88df8-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="88df8-136">使用 Visual Studio 设置本地环境</span><span class="sxs-lookup"><span data-stu-id="88df8-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="88df8-137">首先，请务必按以下说明所述安装适用于 Windows 的 [Docker 社区版 (CE)](https://docs.docker.com/docker-for-windows/)：</span><span class="sxs-lookup"><span data-stu-id="88df8-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="88df8-138">适用于 Windows 的 Docker CE 入门</span><span class="sxs-lookup"><span data-stu-id="88df8-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="88df8-139">此外，需要安装了“.NET Core 跨平台开发”工作负载的 Visual Studio 2019 版本 16.4 或更高版本，如图 5-2 所示  。</span><span class="sxs-lookup"><span data-stu-id="88df8-139">In addition, you need Visual Studio 2019 version 16.4 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![“.NET Core 跨平台”开发选择的屏幕截图。](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="88df8-141">**图 5-2**。</span><span class="sxs-lookup"><span data-stu-id="88df8-141">**Figure 5-2**.</span></span> <span data-ttu-id="88df8-142">在 Visual Studio 2019 设置过程中，选择“.NET Core 跨平台开发”工作负载 </span><span class="sxs-lookup"><span data-stu-id="88df8-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2019 setup</span></span>

<span data-ttu-id="88df8-143">即使尚未在应用程序中启用 Docker，开发人员也可以开始在普通 .NET 中编写应用程序（如果打算使用容器，则通常在 .NET Core 中进行），并在 Docker 中进行部署和测试。</span><span class="sxs-lookup"><span data-stu-id="88df8-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="88df8-144">但建议尽快开始使用 Docker，因为这才是真实环境，并且能快速发现存在的问题。</span><span class="sxs-lookup"><span data-stu-id="88df8-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="88df8-145">推荐这样做是因为通过 Visual Studio 可轻松使用 Docker，开发人员能够快速明白，在 Visual Studio 中能调试多容器应用程序就是一个很好的示例。</span><span class="sxs-lookup"><span data-stu-id="88df8-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88df8-146">其他资源</span><span class="sxs-lookup"><span data-stu-id="88df8-146">Additional resources</span></span>

- <span data-ttu-id="88df8-147">适用于 Windows 的 Docker CE 入门   </span><span class="sxs-lookup"><span data-stu-id="88df8-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="88df8-148">**Visual Studio 2019** </span><span class="sxs-lookup"><span data-stu-id="88df8-148">**Visual Studio 2019** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![步骤 2 的映像。](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="88df8-150">步骤 2。</span><span class="sxs-lookup"><span data-stu-id="88df8-150">Step 2.</span></span> <span data-ttu-id="88df8-151">创建与现有 .NET 基础映像相关的 Dockerfile</span><span class="sxs-lookup"><span data-stu-id="88df8-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="88df8-152">要生成自定义映像，需为每个自定义映像提供一个 Dockerfile；无论是从 Visual Studio 自动部署，还是使用 Docker CLI（docker run 和 docker-compose 命令）手动部署，也需为每个要部署的容器提供一个 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="88df8-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="88df8-153">如果应用程序只包含一个自定义服务，则只需要一个 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="88df8-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="88df8-154">如果应用程序包含多个服务（如在微服务体系结构中），则每个服务都需要一个 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="88df8-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="88df8-155">将 Dockerfile 放在应用程序或服务的根文件夹中。</span><span class="sxs-lookup"><span data-stu-id="88df8-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="88df8-156">Dockerfile 包含多个命令，可指示 Docker 如何在容器中设置和运行应用程序或服务。</span><span class="sxs-lookup"><span data-stu-id="88df8-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="88df8-157">开发人员可在代码中手动创建 Dockerfile，并将其与 .NET 依赖项一起添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="88df8-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="88df8-158">借助 Visual Studio 及其 Docker 工具，只需单击几次鼠标即可完成此任务。</span><span class="sxs-lookup"><span data-stu-id="88df8-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="88df8-159">在 Visual Studio 2019 中新建项目时，可看到一个名为“启用 Docker 支持”的选项，如图 5-3 所示  。</span><span class="sxs-lookup"><span data-stu-id="88df8-159">When you create a new project in Visual Studio 2019, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![显示“启用 Docker 支持”复选框的屏幕截图。](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="88df8-161">**图 5-3**。</span><span class="sxs-lookup"><span data-stu-id="88df8-161">**Figure 5-3**.</span></span> <span data-ttu-id="88df8-162">在 Visual Studio 2019 中创建新的 ASP.NET Core 项目时，启用 Docker 支持</span><span class="sxs-lookup"><span data-stu-id="88df8-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2019</span></span>

<span data-ttu-id="88df8-163">也可以如图 5-4 所示，右键单击“解决方案资源管理器”中的项目，并选择“添加” > “Docker 支持...”，从而在现有 ASP.NET Core Web 应用项目中启用 Docker 支持    。</span><span class="sxs-lookup"><span data-stu-id="88df8-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support...**, as shown in Figure 5-4.</span></span>

![显示“添加”菜单中“Docker 支持”选项的屏幕截图。](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="88df8-165">**图 5-4**。</span><span class="sxs-lookup"><span data-stu-id="88df8-165">**Figure 5-4**.</span></span> <span data-ttu-id="88df8-166">在现有 Visual Studio 2019 项目中启用 Docker 支持</span><span class="sxs-lookup"><span data-stu-id="88df8-166">Enabling Docker support in an existing Visual Studio 2019 project</span></span>

<span data-ttu-id="88df8-167">此操作可将 Dockerfile 添加到具有所需配置的项目，并且仅可用于 ASP.NET Core 项目  。</span><span class="sxs-lookup"><span data-stu-id="88df8-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="88df8-168">与其类似，Visual Studio 也可以为具有“添加 > 容器业务流程协调程序支持...”选项的整个解决方案添加 `docker-compose.yml` 文件  。在步骤 4 中，我们将更详细地探讨此选项。</span><span class="sxs-lookup"><span data-stu-id="88df8-168">In a similar fashion, Visual Studio can also add a `docker-compose.yml` file for the whole solution with the option **Add > Container Orchestrator Support...**. In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="88df8-169">使用现有的官方 .NET Docker 映像</span><span class="sxs-lookup"><span data-stu-id="88df8-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="88df8-170">开发人员通常以基础映像（从 [Docker 中心](https://hub.docker.com/)注册表等官方存储库中获取）为基础生成容器的自定义映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="88df8-171">确切地说，在 Visual Studio 中启用 Docker 支持后就可以执行此操作。</span><span class="sxs-lookup"><span data-stu-id="88df8-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="88df8-172">Dockerfile 将使用现有的 `dotnet/core/aspnet` 映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-172">Your Dockerfile will use an existing `dotnet/core/aspnet` image.</span></span>

<span data-ttu-id="88df8-173">之前我们介绍了根据开发人员选择的框架和操作系统可使用的 Docker 映像和存储库。</span><span class="sxs-lookup"><span data-stu-id="88df8-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="88df8-174">例如，如果想使用 ASP.NET Core（Linux 或 Windows），则使用的映像是 `mcr.microsoft.com/dotnet/core/aspnet:3.1`。</span><span class="sxs-lookup"><span data-stu-id="88df8-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="88df8-175">因此，只需指定用于容器的基础 Docker 映像即可。</span><span class="sxs-lookup"><span data-stu-id="88df8-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="88df8-176">为此，将 `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` 添加到 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="88df8-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` to your Dockerfile.</span></span> <span data-ttu-id="88df8-177">Visual Studio 会自动执行此操作，但若要更新版本，则需更新此值。</span><span class="sxs-lookup"><span data-stu-id="88df8-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="88df8-178">使用从 Docker 中心获取的带版本号的官方 .NET 映像存储库可确保能在所有计算机（包括用于开发、测试和生产的计算机）上使用相同的语言功能。</span><span class="sxs-lookup"><span data-stu-id="88df8-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="88df8-179">以下示例显示了 ASP.NET Core 容器的示例 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="88df8-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="88df8-180">在此情况下，该映像以官方 ASP.NET Core Docker 映像的版本 3.1（适用于 Linux 和 Windows 的多体系结构）为基础。</span><span class="sxs-lookup"><span data-stu-id="88df8-180">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="88df8-181">这是 `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` 设置。</span><span class="sxs-lookup"><span data-stu-id="88df8-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="88df8-182">（有关此基础映像的详细信息，请参阅 [.NET Core Docker 映像页](https://hub.docker.com/_/microsoft-dotnet-core/)页面。）在 Dockerfile 中，还需指示 Docker 侦听要在运行时使用的 TCP 端口（示例中由 EXPOSE 设置配置的 TPC 端口为 80）。</span><span class="sxs-lookup"><span data-stu-id="88df8-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="88df8-183">可在 Dockerfile 中指定其他配置设置，具体取决于使用的语言和框架。</span><span class="sxs-lookup"><span data-stu-id="88df8-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="88df8-184">例如，带有 `["dotnet", "MySingleContainerWebApp.dll"]` 的 ENTRYPOINT 行可指示 Docker 运行 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="88df8-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="88df8-185">如果使用 SDK 和 .NET Core CLI (dotnet CLI) 来生成和运行 .NET 应用程序，则此设置会有所不同。</span><span class="sxs-lookup"><span data-stu-id="88df8-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="88df8-186">底部的 ENTRYPOINT 行和其他设置会有所不同，具体取决于为应用程序选择的语言和平台。</span><span class="sxs-lookup"><span data-stu-id="88df8-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88df8-187">其他资源</span><span class="sxs-lookup"><span data-stu-id="88df8-187">Additional resources</span></span>

- <span data-ttu-id="88df8-188">为 .NET Core 应用程序生成 Docker 映像   </span><span class="sxs-lookup"><span data-stu-id="88df8-188">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="88df8-189">**生成开发人员自己的映像**。</span><span class="sxs-lookup"><span data-stu-id="88df8-189">**Build your own image**.</span></span> <span data-ttu-id="88df8-190">请查看官方 Docker 文档。</span><span class="sxs-lookup"><span data-stu-id="88df8-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="88df8-191">保持 .NET 容器映像的最新状态   </span><span class="sxs-lookup"><span data-stu-id="88df8-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="88df8-192">将 .NET 与 Docker 一起使用 - DockerCon 2018 更新   </span><span class="sxs-lookup"><span data-stu-id="88df8-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="88df8-193">使用多体系结构映像存储库</span><span class="sxs-lookup"><span data-stu-id="88df8-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="88df8-194">单个存储库中可包含平台变量，如 Linux 映像和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="88df8-195">借助此功能，Microsoft （基础映像创建者）等供应商可创建涵盖多个平台（即 Linux 和 Windows）的单个存储库。</span><span class="sxs-lookup"><span data-stu-id="88df8-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="88df8-196">例如，Docker 中心注册表中提供的 [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) 存储库可使用相同的存储库名称为 Linux 和 Windows Nano Server 提供支持。</span><span class="sxs-lookup"><span data-stu-id="88df8-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="88df8-197">如果指定了标签，请明确指定一个平台，如下所示：</span><span class="sxs-lookup"><span data-stu-id="88df8-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  <span data-ttu-id="88df8-198">目标：Linux 上的 .NET Core 3.1 仅运行时</span><span class="sxs-lookup"><span data-stu-id="88df8-198">Targets: .NET Core 3.1 runtime-only on Linux</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  <span data-ttu-id="88df8-199">目标：Windows Nano Server 上的 .NET Core 3.1 仅运行时</span><span class="sxs-lookup"><span data-stu-id="88df8-199">Targets: .NET Core 3.1 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="88df8-200">但如果指定相同的映像名称，即使使用的标记相同，多体系结构映像（如 `aspnet` 映像）也将使用 Linux 或 Windows 版本，具体取决于部署的 Docker 主机操作系统，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="88df8-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnet` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  <span data-ttu-id="88df8-201">多体系结构：Linux 或 Windows Nano Server 上的 .NET Core 3.1 仅运行时，具体取决于 Docker 主机操作系统</span><span class="sxs-lookup"><span data-stu-id="88df8-201">Multi-arch: .NET Core 3.1 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="88df8-202">这样一来，从 Windows 主机拉取映像时，也会拉取 Windows 变体，并且从 Linux 主机拉取同一映像名称时，也会拉取 Linux 变体。</span><span class="sxs-lookup"><span data-stu-id="88df8-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="88df8-203">Dockerfile 中的多阶段生成</span><span class="sxs-lookup"><span data-stu-id="88df8-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="88df8-204">Dockerfile 类似于批处理脚本。</span><span class="sxs-lookup"><span data-stu-id="88df8-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="88df8-205">类似于在必须从命令行设置计算机时你会执行的操作。</span><span class="sxs-lookup"><span data-stu-id="88df8-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="88df8-206">从设置初始上下文的基本映像开始，就像位于主机操作系统上的启动文件系统。</span><span class="sxs-lookup"><span data-stu-id="88df8-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="88df8-207">它不是操作系统，但是可以将其视为近似于容器内的操作系统。</span><span class="sxs-lookup"><span data-stu-id="88df8-207">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="88df8-208">执行每个命令行都会在文件系统上创建新的层，其中包含对上一个层的更改，这样一来，合并时可以生成相应的文件系统。</span><span class="sxs-lookup"><span data-stu-id="88df8-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="88df8-209">由于每个新的层都位于上一层之上，并且随着每个命令的执行，生成的图像大小也会增加，因此如果必须添加生成和发布应用程序所需的 SDK，那么映像可能会变得非常大。</span><span class="sxs-lookup"><span data-stu-id="88df8-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="88df8-210">在此情况下，多阶段生成（从 Docker 17.05 及更高版本开始）可以发挥奇妙的作用。</span><span class="sxs-lookup"><span data-stu-id="88df8-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="88df8-211">核心理念如下：可以将 Dockerfile 执行过程分为几个阶段，其中一个阶段为初始映像，后续阶段是一个或多个命令，最后阶段确定最终的映像大小。</span><span class="sxs-lookup"><span data-stu-id="88df8-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="88df8-212">简言之，可以使用多阶段生成将创建拆分为不同的“阶段”，然后只采用中间阶段的相关目录来组建最终的映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="88df8-213">使用此功能的一般策略为：</span><span class="sxs-lookup"><span data-stu-id="88df8-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="88df8-214">将基础 SDK 映像（无论大小）用于生成应用程序并将其发布到文件夹所需的一切内容，然后</span><span class="sxs-lookup"><span data-stu-id="88df8-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="88df8-215">使用基础、仅运行时的小型映像，并从上一阶段复制发布文件夹，以生成小的最终映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="88df8-216">了解多阶段的最好方法可能是逐行仔细浏览 Dockerfile，因此让我们开始浏览初始 Dockerfile（由 Visual Studio 向项目中添加 Docker 支持时所创建，我们稍后将对其进行一些优化）。</span><span class="sxs-lookup"><span data-stu-id="88df8-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="88df8-217">初始 Dockerfile 可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="88df8-217">The initial Dockerfile might look something like this:</span></span>

```dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks …
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="88df8-218">以下为每一行的详细信息：</span><span class="sxs-lookup"><span data-stu-id="88df8-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="88df8-219">**第 1 行：** 使用“小型”仅运行时基础映像开始一个阶段，将其称为“基础”，以供参考  。</span><span class="sxs-lookup"><span data-stu-id="88df8-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="88df8-220">**第 2 行：** 在映像中创建 /app 目录  。</span><span class="sxs-lookup"><span data-stu-id="88df8-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="88df8-221">**第 3 行：** 公开端口 80  。</span><span class="sxs-lookup"><span data-stu-id="88df8-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="88df8-222">**第 5 行：** 使用“大型”映像开始用于生成/发布的新阶段。</span><span class="sxs-lookup"><span data-stu-id="88df8-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="88df8-223">将其称为“生成”  ，以供参考。</span><span class="sxs-lookup"><span data-stu-id="88df8-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="88df8-224">**第 6 行：** 在映像中创建目录 /src  。</span><span class="sxs-lookup"><span data-stu-id="88df8-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="88df8-225">**第 7 行：** 在第 16 行，复制引用的 .csproj 项目文件，以便之后能够还原包  。</span><span class="sxs-lookup"><span data-stu-id="88df8-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="88df8-226">**第 17 行：** 还原 Catalog.API 项目和引用项目的包  。</span><span class="sxs-lookup"><span data-stu-id="88df8-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="88df8-227">**第 18 行：** 将解决方案的所有目录树（.dockerignore 文件中包含的文件/目录除外）复制到映像中的 /src 目录    。</span><span class="sxs-lookup"><span data-stu-id="88df8-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="88df8-228">**第 19 行：** 将当前文件夹更改为 Catalog.API 项目  。</span><span class="sxs-lookup"><span data-stu-id="88df8-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="88df8-229">**第 20 行：** 生成项目（和其他项目依赖项）并输出到映像中的 /app 目录  。</span><span class="sxs-lookup"><span data-stu-id="88df8-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="88df8-230">**第 22 行：** 开始一个从“生成”继续的新阶段。</span><span class="sxs-lookup"><span data-stu-id="88df8-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="88df8-231">将它称为“发布”  以进行引用。</span><span class="sxs-lookup"><span data-stu-id="88df8-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="88df8-232">**第 23 行：** 发布项目（和依赖项）并输出到映像中的 /app 目录  。</span><span class="sxs-lookup"><span data-stu-id="88df8-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="88df8-233">**第 25 行：** 开始一个从“基础”继续的新阶段，并将其称为“最终”   。</span><span class="sxs-lookup"><span data-stu-id="88df8-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="88df8-234">**第 26 行：** 将当前目录更改为 /app  。</span><span class="sxs-lookup"><span data-stu-id="88df8-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="88df8-235">**第 27 行：** 将 /app 目录从阶段“发布”复制到当前目录   。</span><span class="sxs-lookup"><span data-stu-id="88df8-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="88df8-236">**第 28 行：** 定义启动容器时要运行的命令。</span><span class="sxs-lookup"><span data-stu-id="88df8-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="88df8-237">现在让我们探索一些用于提高整个流程性能（以 eShopOnContainer 为例，这意味着在 Linux 容器中构建完整的解决方案需要大约 22 分钟或更长时间）的优化。</span><span class="sxs-lookup"><span data-stu-id="88df8-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="88df8-238">你将利用 Docker 的层缓存功能，该功能非常简单：如果基础映像和命令与之前执行的相同，那么它可以直接使用生成的层，而不需要执行命令，从而节省一些时间。</span><span class="sxs-lookup"><span data-stu-id="88df8-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="88df8-239">因此，让我们重点关注“生成”阶段，第 5-6 行基本相同，但是第 7-17 行与 eShopOnContainer 中每个服务不同，因此它们必须每次都执行命令，但是如果将第 7-16 行更改为： </span><span class="sxs-lookup"><span data-stu-id="88df8-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```dockerfile
COPY . .
```

<span data-ttu-id="88df8-240">然后，对于每项服务都相同，它会复制整个解决方案并创建一个更大的层，但是：</span><span class="sxs-lookup"><span data-stu-id="88df8-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="88df8-241">仅在第一次时（以及如果文件发生更改，则在重新构建时）执行复制进程，而且复制进程会使用所有其他服务的缓存，并且</span><span class="sxs-lookup"><span data-stu-id="88df8-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="88df8-242">由于较大的映像发生在中间阶段，因此不会影响最终的映像大小。</span><span class="sxs-lookup"><span data-stu-id="88df8-242">Since the larger image occurs in an intermediate stage, it doesn't affect the final image size.</span></span>

<span data-ttu-id="88df8-243">下一个重要的优化涉及在第 17 行中执行的 `restore` 命令，其对于 eShopOnContainers 的每项服务也是不同的。</span><span class="sxs-lookup"><span data-stu-id="88df8-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="88df8-244">如果把该行更改为：</span><span class="sxs-lookup"><span data-stu-id="88df8-244">If you change that line to just:</span></span>

```dockerfile
RUN dotnet restore
```

<span data-ttu-id="88df8-245">它将还原整个解决方案的包，但它只还原一次，而不是当前策略中的 15 次。</span><span class="sxs-lookup"><span data-stu-id="88df8-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="88df8-246">然而，`dotnet restore` 仅当文件夹中有单个项目或解决方案文件时才会运行，因此实现这一点有点复杂，解决此问题且无需涉及太多细节的方法是：</span><span class="sxs-lookup"><span data-stu-id="88df8-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="88df8-247">将以下命令行添加到 .dockerignore： </span><span class="sxs-lookup"><span data-stu-id="88df8-247">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="88df8-248">`*.sln`，以忽略主文件夹树中的所有解决方案文件</span><span class="sxs-lookup"><span data-stu-id="88df8-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="88df8-249">`!eShopOnContainers-ServicesAndWebApps.sln`，以仅添加此解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="88df8-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="88df8-250">将 `/ignoreprojectextensions:.dcproj` 参数添加到 `dotnet restore`，因此它也忽略 docker-compose 项目，且仅还原 eShopOnContainers-ServicesAndWebApps 解决方案的包。</span><span class="sxs-lookup"><span data-stu-id="88df8-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="88df8-251">在最后的优化中，第 20 行是多余的，因为第 23 行也生成应用程序，并且实质上它在第 20 行之后运行，所以这又是一个耗时的命令。</span><span class="sxs-lookup"><span data-stu-id="88df8-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="88df8-252">生成的文件为：</span><span class="sxs-lookup"><span data-stu-id="88df8-252">The resulting file is then:</span></span>

```dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -o /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="88df8-253">从头开始创建基础映像</span><span class="sxs-lookup"><span data-stu-id="88df8-253">Creating your base image from scratch</span></span>

<span data-ttu-id="88df8-254">开发人员可以从头开始创建自己的 Docker 基础映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="88df8-255">不推荐刚开始使用 Docker 的开发人员使用此方案，但如果想为自己的基础映像设置特定位，则可采用此方案。</span><span class="sxs-lookup"><span data-stu-id="88df8-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88df8-256">其他资源</span><span class="sxs-lookup"><span data-stu-id="88df8-256">Additional resources</span></span>

- <span data-ttu-id="88df8-257">**多体系结构 .NET Core 映像**。</span><span class="sxs-lookup"><span data-stu-id="88df8-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="88df8-258">**创建基础映像**。</span><span class="sxs-lookup"><span data-stu-id="88df8-258">**Create a base image**.</span></span> <span data-ttu-id="88df8-259">请查看官方 Docker 文档。</span><span class="sxs-lookup"><span data-stu-id="88df8-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![步骤 3 的映像。](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="88df8-261">步骤 3。</span><span class="sxs-lookup"><span data-stu-id="88df8-261">Step 3.</span></span> <span data-ttu-id="88df8-262">创建自定义 Docker 映像并将应用程序或服务嵌入其中</span><span class="sxs-lookup"><span data-stu-id="88df8-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="88df8-263">需为应用程序中的每项服务创建一个相关映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="88df8-264">如果应用程序由单个服务或 Web 应用程序组成，则只需创建一个映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="88df8-265">请注意，Visual Studio 中会自动生成 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="88df8-266">以下步骤仅适用于编辑器/CLI 工作流，下文清楚解释了各步骤的工作原理。</span><span class="sxs-lookup"><span data-stu-id="88df8-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="88df8-267">你作为开发人员在推送完整功能或更改源代码管理系统（例如 GitHub）前，需要在本地进行开发和测试。</span><span class="sxs-lookup"><span data-stu-id="88df8-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="88df8-268">这意味着开发人员需要创建 Docker 映像并向本地 Docker 主机（Windows 或 Linux VM）部署容器，并运行、测试和调试这些本地容器。</span><span class="sxs-lookup"><span data-stu-id="88df8-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="88df8-269">若要使用 Docker CLI 和 Dockerfile 在本地环境中创建自定义映像，可使用 docker build 命令，如图 5-5 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![显示 docker 生成命令的控制台输出的屏幕截图。](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="88df8-271">**图 5-5**。</span><span class="sxs-lookup"><span data-stu-id="88df8-271">**Figure 5-5**.</span></span> <span data-ttu-id="88df8-272">创建自定义 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="88df8-272">Creating a custom Docker image</span></span>

<span data-ttu-id="88df8-273">（可选），可先运行 `dotnet publish`，生成包含所需 .NET 库和二进制文件的可部署文件夹，然后使用 `docker build` 命令，而不是直接从项目文件夹运行 docker build。</span><span class="sxs-lookup"><span data-stu-id="88df8-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="88df8-274">这将创建名为 `cesardl/netcore-webapi-microservice-docker:first` 的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="88df8-275">此处的 :first 是表示特定版本的标记。</span><span class="sxs-lookup"><span data-stu-id="88df8-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="88df8-276">为组合 Docker 应用程序创建自定义映像时，可为每个映像重复执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="88df8-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="88df8-277">应用程序由多个容器组成时（即多容器应用程序），还可使用 `docker-compose up --build` 命令，借助相关 docker-compose.yml 文件中公开的元数据，只需一个命令即可生成所有相关映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="88df8-278">使用 docker images 命令可查找本地存储库中的现有映像，如图 5-6 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![命令 docker 映像的控制台输出，其中显示现有映像。](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="88df8-280">**如 5-6**。</span><span class="sxs-lookup"><span data-stu-id="88df8-280">**Figure 5-6.**</span></span> <span data-ttu-id="88df8-281">使用 docker images 命令查看现有映像</span><span class="sxs-lookup"><span data-stu-id="88df8-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="88df8-282">使用 Visual Studio 创建 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="88df8-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="88df8-283">使用 Visual Studio 创建具有 Docker 支持的项目时，不会显示创建映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="88df8-284">而是在按下 F5（或 Ctrl-F5）运行已 docker 化的应用程序或服务时创建映像   。</span><span class="sxs-lookup"><span data-stu-id="88df8-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="88df8-285">Visual Studio 会自动执行此操作，开发人员不会看到该过程，但务必要了解其原理。</span><span class="sxs-lookup"><span data-stu-id="88df8-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![可选步骤 4 的映像。](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="88df8-287">步骤 4。</span><span class="sxs-lookup"><span data-stu-id="88df8-287">Step 4.</span></span> <span data-ttu-id="88df8-288">生成多容器 Docker 应用程序时，在 docker-compose.yml 中定义服务</span><span class="sxs-lookup"><span data-stu-id="88df8-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="88df8-289">借助 [docker-compose.yml](https://docs.docker.com/compose/compose-file/) 文件，开发人员可定义一组相关服务，通过部署命令将其部署为组合应用程序。</span><span class="sxs-lookup"><span data-stu-id="88df8-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="88df8-290">它还配置其依赖项关系和运行时配置。</span><span class="sxs-lookup"><span data-stu-id="88df8-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="88df8-291">若要使用 docker-compose.yml 文件，则需在主解决方案文件夹或根解决方案文件夹中创建该文件，其内容与以下示例中的内容类似：</span><span class="sxs-lookup"><span data-stu-id="88df8-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mcr.microsoft.com/mssql/server:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="88df8-292">此 docker-compose.yml 文件是简化合并版。</span><span class="sxs-lookup"><span data-stu-id="88df8-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="88df8-293">其中包含始终需要的每个容器的静态配置数据（如自定义映像的名称），以及视部署环境而定的配置信息（如连接字符串）。</span><span class="sxs-lookup"><span data-stu-id="88df8-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="88df8-294">后面的章节将介绍如何将 docker-compose.yml 配置拆分为多个 docker-compose 文件，并根据环境和执行类型（调试或发布）覆盖值。</span><span class="sxs-lookup"><span data-stu-id="88df8-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="88df8-295">docker-compose.yml 示例文件中定义了四项服务：`webmvc` 服务（一个 Web 应用程序）、两个微服务（`ordering-api` 和 `basket-api`）和一个数据源容器（作为容器运行的基于 SQL Server for Linux 的 `sqldata`）。</span><span class="sxs-lookup"><span data-stu-id="88df8-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering-api` and `basket-api`), and one data source container, `sqldata`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="88df8-296">每项服务都将部署为一个容器，因此每项服务都需要一个 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="88df8-297">docker-compose.yml 文件不仅指定正在使用的容器，还指定如何单独配置各容器。</span><span class="sxs-lookup"><span data-stu-id="88df8-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="88df8-298">例如，.yml 文件中的 `webmvc` 容器定义：</span><span class="sxs-lookup"><span data-stu-id="88df8-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="88df8-299">使用预生成的 `eshop/web:latest` 映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="88df8-300">但也可以借助基于 docker-compose 文件中 build: 部分的其他配置，在执行 docker-compose 的过程中配置要生成的映像。</span><span class="sxs-lookup"><span data-stu-id="88df8-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="88df8-301">初始化两个环境变量（CatalogUrl 和 OrderingUrl）。</span><span class="sxs-lookup"><span data-stu-id="88df8-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="88df8-302">将容器上的公开端口 80 转接到主机上的外部端口 80。</span><span class="sxs-lookup"><span data-stu-id="88df8-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="88df8-303">通过 depends_on 设置将 Web 应用链接到目录和排序服务。</span><span class="sxs-lookup"><span data-stu-id="88df8-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="88df8-304">此操作会让该服务处于等待状态，直到启用这些服务。</span><span class="sxs-lookup"><span data-stu-id="88df8-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="88df8-305">稍后介绍如何实现微服务和多容器应用时，我们会再次回顾 docker-compose.yml 文件。</span><span class="sxs-lookup"><span data-stu-id="88df8-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a><span data-ttu-id="88df8-306">在 Visual Studio 2019 中使用 docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="88df8-306">Working with docker-compose.yml in Visual Studio 2019</span></span>

<span data-ttu-id="88df8-307">除了向项目添加 Dockerfile，如前所述，Visual Studio 2017（从版本 15.8 开始）还可以向解决方案添加对 Docker Compose 的业务流程协调程序支持。</span><span class="sxs-lookup"><span data-stu-id="88df8-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="88df8-308">添加容器业务流程协调程序支持（如图 5-7 所示）时，Visual Studio 将首次为项目创建 Dockerfile，并在解决方案中使用几个全局 `docker-compose*.yml` 文件创建新的（服务部分）项目，然后将项目添加到这些文件。</span><span class="sxs-lookup"><span data-stu-id="88df8-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="88df8-309">随后可打开 docker-compose.yml 文件并对其进行更新，增加新的功能。</span><span class="sxs-lookup"><span data-stu-id="88df8-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="88df8-310">必须为要添加到 docker-compose.yml 文件的每个项目重复执行此操作。</span><span class="sxs-lookup"><span data-stu-id="88df8-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="88df8-311">在撰写此文时，Visual Studio 支持 Docker Compose 和 Kubernetes/Helm 业务流程协调程序   。</span><span class="sxs-lookup"><span data-stu-id="88df8-311">At the time of this writing, Visual Studio supports **Docker Compose** and **Kubernetes/Helm** orchestrators.</span></span>

![显示项目上下文菜单中的“容器业务流程协调程序支持”选项的屏幕截图。](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="88df8-313">**图 5-7**。</span><span class="sxs-lookup"><span data-stu-id="88df8-313">**Figure 5-7**.</span></span> <span data-ttu-id="88df8-314">右键单击 ASP.NET Core 项目，在 Visual Studio 2019 中添加对 Docker 的支持</span><span class="sxs-lookup"><span data-stu-id="88df8-314">Adding Docker support in Visual Studio 2019 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="88df8-315">在 Visual Studio 中添加业务流程协调程序支持后，解决方案资源管理器中会出现一个新节点（位于 `docker-compose.dcproj` 项目文件中），其中包含添加的 docker-compose.yml 文件，如图 5-8 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![解决方案资源管理器中 docker-compose 节点的屏幕截图。](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="88df8-317">**图 5-8**。</span><span class="sxs-lookup"><span data-stu-id="88df8-317">**Figure 5-8**.</span></span> <span data-ttu-id="88df8-318">在 Visual Studio 2019 解决方案资源管理器中添加的 docker-compose 树节点 </span><span class="sxs-lookup"><span data-stu-id="88df8-318">The **docker-compose** tree node added in Visual Studio 2019 Solution Explorer</span></span>

<span data-ttu-id="88df8-319">可使用 `docker-compose up` 命令，通过单个 docker-compose.yml 文件部署多容器应用程序。</span><span class="sxs-lookup"><span data-stu-id="88df8-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="88df8-320">但 Visual Studio 按组添加，因此开发人员可根据环境（开发或生产）和执行类型（发布或调试）来覆盖值。</span><span class="sxs-lookup"><span data-stu-id="88df8-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="88df8-321">稍后将介绍此功能。</span><span class="sxs-lookup"><span data-stu-id="88df8-321">This capability will be explained in later sections.</span></span>

![步骤 5 的映像。](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="88df8-323">步骤 5。</span><span class="sxs-lookup"><span data-stu-id="88df8-323">Step 5.</span></span> <span data-ttu-id="88df8-324">生成并运行 Docker 应用程序</span><span class="sxs-lookup"><span data-stu-id="88df8-324">Build and run your Docker application</span></span>

<span data-ttu-id="88df8-325">如果应用程序只有一个容器，则可通过将其部署到 Docker 主机（虚拟机或物理服务器）来运行该程序。</span><span class="sxs-lookup"><span data-stu-id="88df8-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="88df8-326">但如果应用程序包含多项服务，则可使用单个 CLI 命令 (`docker-compose up)`) 或使用 Visual Studio（会在其中使用该命令）将其部署为组合应用程序。</span><span class="sxs-lookup"><span data-stu-id="88df8-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (`docker-compose up)`, or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="88df8-327">接下来介绍这两种不同的选项。</span><span class="sxs-lookup"><span data-stu-id="88df8-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="88df8-328">选项 A：运行单容器应用程序</span><span class="sxs-lookup"><span data-stu-id="88df8-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="88df8-329">使用 Docker CLI</span><span class="sxs-lookup"><span data-stu-id="88df8-329">Using Docker CLI</span></span>

<span data-ttu-id="88df8-330">可使用 `docker run` 命令运行 Docker 容器，如图 5-9 所示：</span><span class="sxs-lookup"><span data-stu-id="88df8-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="88df8-331">上面的命令将在每次运行时从指定的映像创建新的容器实例。</span><span class="sxs-lookup"><span data-stu-id="88df8-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="88df8-332">可以使用 `--name` 参数为容器指定名称，然后使用 `docker start {name}`（或者使用容器 ID 或自动名称）运行现有的容器实例。</span><span class="sxs-lookup"><span data-stu-id="88df8-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![使用 docker run 命令运行 Docker 容器的屏幕截图。](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="88df8-334">**图 5-9**。</span><span class="sxs-lookup"><span data-stu-id="88df8-334">**Figure 5-9**.</span></span> <span data-ttu-id="88df8-335">使用 docker run 命令运行 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="88df8-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="88df8-336">此时，该命令将容器的内部端口 5000 绑定到主机的端口 80。</span><span class="sxs-lookup"><span data-stu-id="88df8-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="88df8-337">这意味着主机在侦听端口 80，并将其转接到容器上的端口 5000。</span><span class="sxs-lookup"><span data-stu-id="88df8-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="88df8-338">显示的哈希为容器 ID，如果不使用 `--name` 选项，还会为它分配随机可读的名称。</span><span class="sxs-lookup"><span data-stu-id="88df8-338">The hash shown is the container ID and it's also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="88df8-339">使用 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88df8-339">Using Visual Studio</span></span>

<span data-ttu-id="88df8-340">如果尚未添加容器业务流程协调程序支持，也可按下 Ctrl-F5 在 Visual Studio 中运行单容器应用，还可使用 F5 在容器中调试应用程序   。</span><span class="sxs-lookup"><span data-stu-id="88df8-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="88df8-341">使用 docker run 在本地运行容器。</span><span class="sxs-lookup"><span data-stu-id="88df8-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="88df8-342">选项 B：运行多容器应用程序</span><span class="sxs-lookup"><span data-stu-id="88df8-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="88df8-343">在大多数企业方案中，Docker 应用程序由多项服务组成，这意味着需要运行多容器应用程序，如图 5-10 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![具有多个 Docker 容器的 VM](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="88df8-345">**图 5-10**。</span><span class="sxs-lookup"><span data-stu-id="88df8-345">**Figure 5-10**.</span></span> <span data-ttu-id="88df8-346">部署了 Docker 容器的 VM</span><span class="sxs-lookup"><span data-stu-id="88df8-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="88df8-347">使用 Docker CLI</span><span class="sxs-lookup"><span data-stu-id="88df8-347">Using Docker CLI</span></span>

<span data-ttu-id="88df8-348">若要使用 Docker CLI 运行多容器应用程序，请使用 `docker-compose up` 命令。</span><span class="sxs-lookup"><span data-stu-id="88df8-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="88df8-349">此命令使用解决方案级别的 docker-compose.yml 文件来部署多容器应用程序  。</span><span class="sxs-lookup"><span data-stu-id="88df8-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="88df8-350">图 5-11 显示了从主解决方案目录（包含 docker-compose.yml 文件）运行命令的结果。</span><span class="sxs-lookup"><span data-stu-id="88df8-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![运行 docker-compose up 命令时的屏幕视图](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="88df8-352">**图 5-11**。</span><span class="sxs-lookup"><span data-stu-id="88df8-352">**Figure 5-11**.</span></span> <span data-ttu-id="88df8-353">运行 docker-compose up 命令时的示例结果</span><span class="sxs-lookup"><span data-stu-id="88df8-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="88df8-354">运行 docker-compose up 命令后，应用程序及其相关容器将部署到 Docker 主机中，如图 5-10 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="88df8-355">使用 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="88df8-355">Using Visual Studio</span></span>

<span data-ttu-id="88df8-356">使用 Visual Studio 2019 运行多容器应用程序十分简单。</span><span class="sxs-lookup"><span data-stu-id="88df8-356">Running a multi-container application using Visual Studio 2019 can't get any simpler.</span></span> <span data-ttu-id="88df8-357">按 Ctrl-F5 可运行，按 F5 可调试，按照惯例，将 docker-compose 项目设置为启动项目    。</span><span class="sxs-lookup"><span data-stu-id="88df8-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="88df8-358">Visual Studio 处理所有需要的设置，所以你可以按照惯例创建断点，并使用已附加的调试程序调试最终在“远程服务器”中运行的独立进程，就是这样。</span><span class="sxs-lookup"><span data-stu-id="88df8-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", with the debugger already attached, just like that.</span></span>

<span data-ttu-id="88df8-359">如前所述，每次向解决方案中的项目添加对 Docker 的支持时，都会在全局（解决方案级别）docker-compose.yml 文件中配置该项目，因此开发人员可以同时运行或调试整个解决方案。</span><span class="sxs-lookup"><span data-stu-id="88df8-359">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="88df8-360">Visual Studio 将为每个启用了 Docker 解决方案支持的项目启动一个容器，并代为执行所有内部步骤（发布 dotnet、生成 Docker 等）。</span><span class="sxs-lookup"><span data-stu-id="88df8-360">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="88df8-361">如果想大致看看所有步骤，请查看文件：</span><span class="sxs-lookup"><span data-stu-id="88df8-361">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="88df8-362">此处的重点是，在 Visual Studio 2019 中，按下 F5 键可执行另一项 Docker 命令，如图 5-12 所示  。</span><span class="sxs-lookup"><span data-stu-id="88df8-362">The important point here is that, as shown in Figure 5-12, in Visual Studio 2019 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="88df8-363">此选项允许开发人员在解决方案级别运行 docker-compose.yml 文件中定义的所有容器，从而运行或调试多容器应用程序。</span><span class="sxs-lookup"><span data-stu-id="88df8-363">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="88df8-364">可调试多容器解决方案就意味着，开发人员可设置多个断点，每个端点都位于不同的项目（容器）中，这样从 Visual Studio 进行调试时，会在不同项目中定义的断点处停止，并在不同容器上运行。</span><span class="sxs-lookup"><span data-stu-id="88df8-364">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![调试工具栏运行 docker-compose 项目的屏幕截图。](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="88df8-366">**图 5-12**。</span><span class="sxs-lookup"><span data-stu-id="88df8-366">**Figure 5-12**.</span></span> <span data-ttu-id="88df8-367">在 Visual Studio 2019 中运行多容器应用</span><span class="sxs-lookup"><span data-stu-id="88df8-367">Running multi-container apps in Visual Studio 2019</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88df8-368">其他资源</span><span class="sxs-lookup"><span data-stu-id="88df8-368">Additional resources</span></span>

- <span data-ttu-id="88df8-369">将 ASP.NET 容器部署到远程 Docker 主机   </span><span class="sxs-lookup"><span data-stu-id="88df8-369">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/visualstudio/containers/hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="88df8-370">有关使用业务流程协调程序进行测试和部署的注意事项</span><span class="sxs-lookup"><span data-stu-id="88df8-370">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="88df8-371">使用 docker-compose up 和 docker run 命令（或在 Visual Studio 中运行和调试容器）足以在开发环境中测试容器。</span><span class="sxs-lookup"><span data-stu-id="88df8-371">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="88df8-372">但不应该将这种方法用于生产部署，在生产部署中应该以业务流程协调程序（例如 [Kubernetes](https://kubernetes.io/) 或 [Service Fabric](https://azure.microsoft.com/services/service-fabric/)）为目标。</span><span class="sxs-lookup"><span data-stu-id="88df8-372">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="88df8-373">如果正在使用 Kubernetes，那么必须使用 [pod](https://kubernetes.io/docs/concepts/workloads/pods/pod/) 来组织容器和[服务](https://kubernetes.io/docs/concepts/services-networking/service/)，使其互联。</span><span class="sxs-lookup"><span data-stu-id="88df8-373">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="88df8-374">还可以使用[部署](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)来组织 pod 的创建和修改。</span><span class="sxs-lookup"><span data-stu-id="88df8-374">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![步骤 6 的映像。](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="88df8-376">步骤 6。</span><span class="sxs-lookup"><span data-stu-id="88df8-376">Step 6.</span></span> <span data-ttu-id="88df8-377">使用本地 Docker 主机测试 Docker 应用程序</span><span class="sxs-lookup"><span data-stu-id="88df8-377">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="88df8-378">这一步骤会因应用程序的用途而有所不同。</span><span class="sxs-lookup"><span data-stu-id="88df8-378">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="88df8-379">对于部署为单个容器或服务的简单 .NET Core Web 应用程序而言，在 Docker 主机上打开浏览器并导航到该站点即可访问该服务，如图 5-13 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-379">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="88df8-380">（如果 Dockerfile 中的配置将容器映射到除主机上的 80 端口以外的任何端口，请在 URL 中包含该主机端口。）</span><span class="sxs-lookup"><span data-stu-id="88df8-380">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![来自 localhost/API/values 的响应的屏幕截图。](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="88df8-382">**图 5-13**。</span><span class="sxs-lookup"><span data-stu-id="88df8-382">**Figure 5-13**.</span></span> <span data-ttu-id="88df8-383">使用 localhost 在本地测试 Docker 应用程序的示例</span><span class="sxs-lookup"><span data-stu-id="88df8-383">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="88df8-384">如果 localhost 未指向 Docker 主机 IP（默认情况下，使用 Docker CE 时应指向主机 IP），若要导航到服务，请使用计算机网卡的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="88df8-384">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="88df8-385">请注意，在此处讨论的特定容器示例中，浏览器中的此 URL 使用的是端口 80。</span><span class="sxs-lookup"><span data-stu-id="88df8-385">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="88df8-386">但该请求会在内部被重定向到端口 5000，因为 docker run 命令之前进行了此部署，如上一步中所述。</span><span class="sxs-lookup"><span data-stu-id="88df8-386">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="88df8-387">还可从终端使用 curl 测试应用程序，如图 5-14 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-387">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="88df8-388">对于 Windows 上安装的 Docker，除计算机的实际 IP 地址以外，默认的 Docker 主机 IP 始终为 10.0.75.1。</span><span class="sxs-lookup"><span data-stu-id="88df8-388">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![通过 curl 获取 http://10.0.75.1/API/values 的控制台输出。](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="88df8-390">**图 5-14**。</span><span class="sxs-lookup"><span data-stu-id="88df8-390">**Figure 5-14**.</span></span> <span data-ttu-id="88df8-391">使用 curl 在本地测试 Docker 应用程序的示例</span><span class="sxs-lookup"><span data-stu-id="88df8-391">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a><span data-ttu-id="88df8-392">使用 Visual Studio 2019 测试和调试容器</span><span class="sxs-lookup"><span data-stu-id="88df8-392">Testing and debugging containers with Visual Studio 2019</span></span>

<span data-ttu-id="88df8-393">使用 Visual Studio 2019 运行和调试容器时，调试 .NET 应用程序的方式与运行不带容器的应用程序的方式类似。</span><span class="sxs-lookup"><span data-stu-id="88df8-393">When running and debugging the containers with Visual Studio 2019, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="88df8-394">不使用 Visual Studio 进行测试和调试</span><span class="sxs-lookup"><span data-stu-id="88df8-394">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="88df8-395">如果使用编辑器/CLI 方法进行开发，调试容器会更加困难，可能要通过生成跟踪来进行调试。</span><span class="sxs-lookup"><span data-stu-id="88df8-395">If you're developing using the editor/CLI approach, debugging containers is more difficult and you'll probably want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88df8-396">其他资源</span><span class="sxs-lookup"><span data-stu-id="88df8-396">Additional resources</span></span>

- <span data-ttu-id="88df8-397">在本地 Docker 容器中调试应用   </span><span class="sxs-lookup"><span data-stu-id="88df8-397">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="88df8-398">**Steve Lasker。Build, Debug, Deploy ASP.NET Core Apps with Docker**（使用 Docker 生成、调试、部署 ASP.NET Core 应用）。</span><span class="sxs-lookup"><span data-stu-id="88df8-398">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="88df8-399">视频。</span><span class="sxs-lookup"><span data-stu-id="88df8-399">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="88df8-400">使用 Visual Studio 可简化开发容器的工作流</span><span class="sxs-lookup"><span data-stu-id="88df8-400">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="88df8-401">实际上，使用 Visual Studio 进行开发的工作流比使用编辑器/CLI 方法的工作流简单得多。</span><span class="sxs-lookup"><span data-stu-id="88df8-401">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="88df8-402">Visual Studio 隐藏或简化了 Docker 需要执行的与 Dockerfile 和 docker-compose.yml 文件相关的大部分步骤，如图 5-15 所示。</span><span class="sxs-lookup"><span data-stu-id="88df8-402">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="显示了创建应用所用的五个简化步骤的关系图。":::
<span data-ttu-id="88df8-404">Docker 应用的开发流程：1 - 编写应用代码，2 - 编写 Dockerfile/s，3 - 创建在 Dockerfile/s 上定义的映像，4 -（可选）在 docker-compose.yml 文件中编写服务，5 - 运行容器或 docker-compose 应用，6 - 测试应用或微服务，7 - 推送到存储库并重复操作。</span><span class="sxs-lookup"><span data-stu-id="88df8-404">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="88df8-405">**图 5-15**。</span><span class="sxs-lookup"><span data-stu-id="88df8-405">**Figure 5-15**.</span></span> <span data-ttu-id="88df8-406">使用 Visual Studio 可简化开发工作流</span><span class="sxs-lookup"><span data-stu-id="88df8-406">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="88df8-407">此外，只需执行一次第 2 步（向项目添加对 Docker 的支持）。</span><span class="sxs-lookup"><span data-stu-id="88df8-407">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="88df8-408">因此，该工作流与使用 .NET 进行任何其他开发时的普通开发任务的工作流类似。</span><span class="sxs-lookup"><span data-stu-id="88df8-408">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="88df8-409">开发人员需要了解其背后的工作原理（映像生成过程，使用的基础映像，容器的部署等），有时还需要编辑 Dockerfile 或 docker-compose.yml 文件以自定义行为。</span><span class="sxs-lookup"><span data-stu-id="88df8-409">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="88df8-410">但 Visual Studio 大大简化了大部分工作，提高了工作效率。</span><span class="sxs-lookup"><span data-stu-id="88df8-410">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88df8-411">其他资源</span><span class="sxs-lookup"><span data-stu-id="88df8-411">Additional resources</span></span>

- <span data-ttu-id="88df8-412">**使用 Visual Studio (2017) 进行 Steve Lasker .NET Docker 开发** </span><span class="sxs-lookup"><span data-stu-id="88df8-412">**Steve Lasker. .NET Docker Development with Visual Studio (2017)** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="88df8-413">在 DockerFile 中使用 PowerShell 命令来设置 Windows 容器</span><span class="sxs-lookup"><span data-stu-id="88df8-413">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="88df8-414">[Windows 容器](/virtualization/windowscontainers/about/index)允许开发人员将现有 Windows 应用程序转换为 Docker 映像，并使用与 Docker 生态系统其余部分相同的工具进行部署。</span><span class="sxs-lookup"><span data-stu-id="88df8-414">[Windows Containers](/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="88df8-415">若要使用 Windows 容器，请在 Dockerfile 中运行 PowerShell 命令，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="88df8-415">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="88df8-416">本示例中使用的是 Windows Server Core 基础映像（FROM 设置），并使用 PowerShell 命令（RUN 设置）来安装 IIS。</span><span class="sxs-lookup"><span data-stu-id="88df8-416">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="88df8-417">同样，也可使用 PowerShell 命令来设置其他组件，如 ASP.NET 4.x、.NET 4.6 或任何其他 Windows 软件。</span><span class="sxs-lookup"><span data-stu-id="88df8-417">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="88df8-418">例如，Dockerfile 中的以下命令可设置 ASP.NET 4.5：</span><span class="sxs-lookup"><span data-stu-id="88df8-418">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="88df8-419">其他资源</span><span class="sxs-lookup"><span data-stu-id="88df8-419">Additional resources</span></span>

- <span data-ttu-id="88df8-420">**aspnet-docker/Dockerfile。**</span><span class="sxs-lookup"><span data-stu-id="88df8-420">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="88df8-421">在 dockerfiles 中运行以包含 Windows 功能的 Powershell 命令示例。</span><span class="sxs-lookup"><span data-stu-id="88df8-421">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="88df8-422">[上一页](index.md)
>[下一页](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="88df8-422">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
