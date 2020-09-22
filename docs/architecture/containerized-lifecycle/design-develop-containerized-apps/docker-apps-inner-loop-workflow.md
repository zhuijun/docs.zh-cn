---
title: Docker 应用的内部循环开发工作流
description: 了解 Docker 应用程序的“内部循环”开发工作流。
ms.date: 08/06/2020
ms.openlocfilehash: 071e16afede91f4cfd6cbe8662fa68814ffdcdd7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539757"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="f6856-103">Docker 应用的内部循环开发工作流</span><span class="sxs-lookup"><span data-stu-id="f6856-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="f6856-104">在触发跨整个 DevOps 周期的外部循环工作流之前，这一切都从每个开发人员的计算机开始，使用其首选语言或平台对应用本身进行编码，并在本地进行测试（图 4-21）。</span><span class="sxs-lookup"><span data-stu-id="f6856-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="f6856-105">但在所有情况下，无论选择何种语言、框架或平台，都有一个重要的共同点。</span><span class="sxs-lookup"><span data-stu-id="f6856-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="f6856-106">在此特定的工作流中，你始终在本地而不在其他环境中开发和测试 Docker 容器。</span><span class="sxs-lookup"><span data-stu-id="f6856-106">In this specific workflow, you're always developing and testing Docker containers in no other environments, but locally.</span></span>

![显示内部循环开发环境概念的示意图。](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="f6856-108">图 4-21  。</span><span class="sxs-lookup"><span data-stu-id="f6856-108">**Figure 4-21**.</span></span> <span data-ttu-id="f6856-109">内部循环开发上下文</span><span class="sxs-lookup"><span data-stu-id="f6856-109">Inner-loop development context</span></span>

<span data-ttu-id="f6856-110">Docker 映像的容器或实例将包含以下组件：</span><span class="sxs-lookup"><span data-stu-id="f6856-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="f6856-111">操作系统选择（例如，Linux 发行版、Windows）</span><span class="sxs-lookup"><span data-stu-id="f6856-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="f6856-112">开发人员添加的文件（例如，应用二进制文件）</span><span class="sxs-lookup"><span data-stu-id="f6856-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="f6856-113">配置（例如，环境设置和依赖项）</span><span class="sxs-lookup"><span data-stu-id="f6856-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="f6856-114">有关 Docker 运行的进程的说明</span><span class="sxs-lookup"><span data-stu-id="f6856-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="f6856-115">可以设置利用 Docker 作为进程的内部循环开发工作流（在下一节中介绍）。</span><span class="sxs-lookup"><span data-stu-id="f6856-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="f6856-116">请考虑不包括设置环境的初始步骤，因为只需要执行一次操作。</span><span class="sxs-lookup"><span data-stu-id="f6856-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="f6856-117">使用 Visual Studio Code 和 Docker CLI 在 Docker 容器中构建单个应用</span><span class="sxs-lookup"><span data-stu-id="f6856-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="f6856-118">应用由开发人员自己的服务和其他库（依赖项）组成。</span><span class="sxs-lookup"><span data-stu-id="f6856-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="f6856-119">图 4-22 显示了构建 Docker 应用时通常需要执行的基本步骤，每个步骤后跟详细说明。</span><span class="sxs-lookup"><span data-stu-id="f6856-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![显示创建容器化应用程序所用的七个步骤的示意图。](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="f6856-121">**图 4-22**。</span><span class="sxs-lookup"><span data-stu-id="f6856-121">**Figure 4-22**.</span></span> <span data-ttu-id="f6856-122">使用 Docker CLI 实现 Docker 容器化应用程序生命周期的高级工作流</span><span class="sxs-lookup"><span data-stu-id="f6856-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="f6856-123">步骤 1：在 Visual Studio Code 中开始编码并创建初始应用/服务基线</span><span class="sxs-lookup"><span data-stu-id="f6856-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="f6856-124">开发应用程序的方式与开发不带 Docker 的应用程序的方式类似。</span><span class="sxs-lookup"><span data-stu-id="f6856-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="f6856-125">二者的区别在于，在开发过程中，将部署和测试在本地环境中放置的 Docker 容器（如 Linux VM 或 Windows）中运行的应用程序或服务。</span><span class="sxs-lookup"><span data-stu-id="f6856-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="f6856-126">**设置本地环境**</span><span class="sxs-lookup"><span data-stu-id="f6856-126">**Setting up your local environment**</span></span>

<span data-ttu-id="f6856-127">使用最新版本的用于 Mac 和 Windows 的 Docker Desktop，开发 Docker 应用程序容易得多，并且设置非常简单。</span><span class="sxs-lookup"><span data-stu-id="f6856-127">With the latest versions of Docker Desktop for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="f6856-128">如需设置用于 Windows 的 Docker Desktop 的说明，请转到 <https://docs.docker.com/docker-for-windows/>。</span><span class="sxs-lookup"><span data-stu-id="f6856-128">For instructions on setting up Docker Desktop for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
> <span data-ttu-id="f6856-129">如需设置用于 Mac 的 Docker Desktop 的说明，请转到 <https://docs.docker.com/docker-for-mac/>。</span><span class="sxs-lookup"><span data-stu-id="f6856-129">For instructions on setting up Docker Desktop for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="f6856-130">此外，还需要代码编辑器，以便在使用 Docker CLI 时实际开发应用程序。</span><span class="sxs-lookup"><span data-stu-id="f6856-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="f6856-131">Microsoft 提供 Visual Studio Code，它是 Windows、Linux 和 macOS 支持的轻量级代码编辑器，并为 IntelliSense 提供[多种语言的支持](https://code.visualstudio.com/docs/languages/overview)（JavaScript、.NET、Go、Java、Ruby、Python 和大多数现代语言）、[调试](https://code.visualstudio.com/Docs/editor/debugging)、[与 Git 集成](https://code.visualstudio.com/Docs/editor/versioncontrol)和[扩展插件支持](https://code.visualstudio.com/docs/extensions/overview)。</span><span class="sxs-lookup"><span data-stu-id="f6856-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="f6856-132">此编辑器是 macOS 和 Linux 开发人员的绝佳选择。</span><span class="sxs-lookup"><span data-stu-id="f6856-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="f6856-133">在 Windows 中，你还可以使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f6856-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="f6856-134">如需了解用于 Windows、Linux 或 macOS 的 Visual Studio Code 的安装说明，请转到 <https://code.visualstudio.com/docs/setup/setup-overview/>。</span><span class="sxs-lookup"><span data-stu-id="f6856-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="f6856-135">如需设置用于 Mac 的 Docker 的说明，请转到 <https://docs.docker.com/docker-for-mac/>。</span><span class="sxs-lookup"><span data-stu-id="f6856-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="f6856-136">可以使用 Docker CLI 并使用任何代码编辑器编写代码，但使用带 Docker 扩展的 Visual Studio Code 可以轻松编写工作区中的 `Dockerfile` 和 `docker-compose.yml` 文件。</span><span class="sxs-lookup"><span data-stu-id="f6856-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="f6856-137">还可以使用下面的 Docker CLI 从 Visual Studio Code IDE 运行任务和脚本，以执行 Docker 命令。</span><span class="sxs-lookup"><span data-stu-id="f6856-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="f6856-138">VS Code 的 Docker 扩展提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="f6856-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="f6856-139">自动执行 `Dockerfile` 和 `docker-compose.yml` 文件生成</span><span class="sxs-lookup"><span data-stu-id="f6856-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="f6856-140">`docker-compose.yml` 和 `Dockerfile` 文件的语法突出显示和悬停提示</span><span class="sxs-lookup"><span data-stu-id="f6856-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="f6856-141">`Dockerfile` 和 `docker-compose.yml` 文件的 IntelliSense（完成）</span><span class="sxs-lookup"><span data-stu-id="f6856-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="f6856-142">`Dockerfile` 文件的 Linting（错误和警告）</span><span class="sxs-lookup"><span data-stu-id="f6856-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="f6856-143">最常用的 Docker 命令的命令面板 (F1) 集成</span><span class="sxs-lookup"><span data-stu-id="f6856-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="f6856-144">用于管理映像和容器的 Explorer 集成</span><span class="sxs-lookup"><span data-stu-id="f6856-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="f6856-145">将映像从 DockerHub 和 Azure 容器注册表部署到 Azure 应用服务</span><span class="sxs-lookup"><span data-stu-id="f6856-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="f6856-146">要安装 Docker 扩展，请按 Ctrl+Shift+P，键入 `ext install`，然后运行安装扩展命令以打开市场扩展列表。</span><span class="sxs-lookup"><span data-stu-id="f6856-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="f6856-147">接下来，键入“docker”，对结果进行筛选，然后选择 Docker 支持扩展，如下图 4-23 所示  。</span><span class="sxs-lookup"><span data-stu-id="f6856-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![VS Code 的 Docker 扩展视图。](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="f6856-149">图 4-23  。</span><span class="sxs-lookup"><span data-stu-id="f6856-149">**Figure 4-23**.</span></span> <span data-ttu-id="f6856-150">在 Visual Studio Code 中安装 Docker 扩展</span><span class="sxs-lookup"><span data-stu-id="f6856-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="f6856-151">步骤 2：创建与现有映像相关的 DockerFile（普通 OS 或 .NET Core、Node.js 和 Ruby 等开发环境）</span><span class="sxs-lookup"><span data-stu-id="f6856-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="f6856-152">需要为每个自定义映像构建 `DockerFile`，并且每个容器都需要部署。</span><span class="sxs-lookup"><span data-stu-id="f6856-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="f6856-153">如果应用由单个自定义服务组成，则需要一个 `DockerFile`。</span><span class="sxs-lookup"><span data-stu-id="f6856-153">If your app is made up of single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="f6856-154">但是，如果应用由多个服务组成（如微服务体系结构中所示），则每个服务需要一个 `Dockerfile`。</span><span class="sxs-lookup"><span data-stu-id="f6856-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="f6856-155">`DockerFile` 通常放在应用或服务的根文件夹中且包含所需命令，以便 Docker 知道如何设置和运行该应用或服务。</span><span class="sxs-lookup"><span data-stu-id="f6856-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="f6856-156">可以创建 `DockerFile` 并将其与代码（node.js、.NET Core 等）一起添加到项目中。或者，如果你是初次接触环境，请查看以下提示。</span><span class="sxs-lookup"><span data-stu-id="f6856-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="f6856-157">在使用与 Docker 容器相关的 `Dockerfile` 和 `docker-compose.yml` 文件时，可以使用 Docker 扩展来提供指导。</span><span class="sxs-lookup"><span data-stu-id="f6856-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="f6856-158">最终，可能无需使用此工具，即可编写这些类型的文件，但使用 Docker 扩展是一个很好的起点，可以加快学习曲线。</span><span class="sxs-lookup"><span data-stu-id="f6856-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="f6856-159">在图 4-24 中，你可以看到使用适用于 VS Code 的 Docker 扩展将 Docker 文件添加到项目的步骤：</span><span class="sxs-lookup"><span data-stu-id="f6856-159">In Figure 4-24, you can see the steps to add the docker files to a project by using the Docker Extension for VS Code:</span></span>

1. <span data-ttu-id="f6856-160">打开命令面板，键入“docker”，然后选择“将 Docker 文件添加到工作区” 。</span><span class="sxs-lookup"><span data-stu-id="f6856-160">Open the command palette, type "**docker**" and select "**Add Docker Files to Workspace**".</span></span>
2. <span data-ttu-id="f6856-161">选择应用程序平台 (ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="f6856-161">Select Application Platform (ASP.NET Core)</span></span>
3. <span data-ttu-id="f6856-162">选择操作系统 (Linux)</span><span class="sxs-lookup"><span data-stu-id="f6856-162">Select Operating System (Linux)</span></span>
4. <span data-ttu-id="f6856-163">包括可选的 Docker Compose 文件</span><span class="sxs-lookup"><span data-stu-id="f6856-163">Include optional Docker Compose files</span></span>
5. <span data-ttu-id="f6856-164">输入要发布的端口（80、443）</span><span class="sxs-lookup"><span data-stu-id="f6856-164">Enter ports to publish (80, 443)</span></span>
6. <span data-ttu-id="f6856-165">选择项目</span><span class="sxs-lookup"><span data-stu-id="f6856-165">Select the project</span></span>

![添加具有 docker 扩展名的 docker 文件的步骤](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="f6856-167">图 4-24  。</span><span class="sxs-lookup"><span data-stu-id="f6856-167">**Figure 4-24**.</span></span> <span data-ttu-id="f6856-168">使用“将 Docker 文件添加到工作区”命令添加 Docker 文件</span><span class="sxs-lookup"><span data-stu-id="f6856-168">Docker files added using the **Add Docker files to Workspace** command</span></span>

<span data-ttu-id="f6856-169">添加 DockerFile 时，可以指定要使用的 Docker 映像（如使用 `FROM mcr.microsoft.com/dotnet/core/aspnet`）。</span><span class="sxs-lookup"><span data-stu-id="f6856-169">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="f6856-170">通常会在 [Docker Hub 存储库](https://hub.docker.com/)中的任何官方存储库（如 [.NET Core 的映像](https://hub.docker.com/_/microsoft-dotnet-core/)或 [Node.js](https://hub.docker.com/_/node/) 的映像）中获得的基础映像上构建自定义映像。</span><span class="sxs-lookup"><span data-stu-id="f6856-170">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

> [!TIP]
> <span data-ttu-id="f6856-171">你必须对应用程序中的每个项目重复此过程。</span><span class="sxs-lookup"><span data-stu-id="f6856-171">You'll have to repeat this procedure for every project in your application.</span></span> <span data-ttu-id="f6856-172">但是，扩展名将要求在第一次之后覆盖生成的 docker-compose 文件。</span><span class="sxs-lookup"><span data-stu-id="f6856-172">However, the extension will ask to overwrite the generated docker-compose file after the first time.</span></span> <span data-ttu-id="f6856-173">你应该回答不覆盖该文件，因此扩展名会创建单独的 docker-compose 文件，然后你可以在运行 docker-compose 之前手动合并这些文件。</span><span class="sxs-lookup"><span data-stu-id="f6856-173">You should reply to not overwrite it, so the extension creates separate docker-compose files, that you can then merge by hand, prior to running docker-compose.</span></span>

<span data-ttu-id="f6856-174">**_使用现有的官方 Docker 映像_**</span><span class="sxs-lookup"><span data-stu-id="f6856-174">**_Use an existing official Docker image_**</span></span>

<span data-ttu-id="f6856-175">使用带版本号的语言堆栈的官方存储库，可确保在所有计算机（包括开发、测试和生产）上都可以使用相同的语言功能。</span><span class="sxs-lookup"><span data-stu-id="f6856-175">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="f6856-176">以下示例显示 .NET Core 容器的示例 DockerFile：</span><span class="sxs-lookup"><span data-stu-id="f6856-176">The following is a sample DockerFile for a .NET Core container:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

<span data-ttu-id="f6856-177">在本例中，该映像以官方 ASP.NET Core Docker 映像的版本 3.1（适用于 Linux 和 Windows 的多体系结构）为基础，依据此行 `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`。</span><span class="sxs-lookup"><span data-stu-id="f6856-177">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="f6856-178">（有关此主题的详细信息，请参阅 [ASP.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)页和 [.NET Core Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core/)页。）</span><span class="sxs-lookup"><span data-stu-id="f6856-178">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="f6856-179">在 DockerFile 中，还可以指示 Docker 侦听将在运行时使用的 TCP 端口（如端口 80 或 443）。</span><span class="sxs-lookup"><span data-stu-id="f6856-179">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80 or 443).</span></span>

<span data-ttu-id="f6856-180">可在 Dockerfile 中指定其他配置设置，具体取决于使用的语言和框架。</span><span class="sxs-lookup"><span data-stu-id="f6856-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="f6856-181">例如，带有 `["dotnet", "WebMvcApplication.dll"]` 的 `ENTRYPOINT` 行指示 Docker 运行 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="f6856-181">For instance, the `ENTRYPOINT` line with `["dotnet", "WebMvcApplication.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="f6856-182">如果使用 SDK 和 .NET Core CLI (`dotnet CLI`) 来生成和运行 .NET 应用程序，则此设置会有所不同。</span><span class="sxs-lookup"><span data-stu-id="f6856-182">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="f6856-183">此处关键在于 ENTRYPOINT 行和其他设置根据为应用程序选择的语言和平台而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f6856-183">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="f6856-184">有关为 .NET Core 应用程序生成 Docker 映像的详细信息，请转到 <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>。</span><span class="sxs-lookup"><span data-stu-id="f6856-184">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="f6856-185">如需了解有关构建自己的映像的详细信息，请转到 <https://docs.docker.com/engine/tutorials/dockerimages/>。</span><span class="sxs-lookup"><span data-stu-id="f6856-185">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="f6856-186">使用多体系结构映像存储库 </span><span class="sxs-lookup"><span data-stu-id="f6856-186">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="f6856-187">存储库中的单个映像名称可包含平台变量，如 Linux 映像和 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="f6856-187">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="f6856-188">借助此功能，Microsoft（基础映像创建者）等供应商可创建涵盖多个平台（即 Linux 和 Windows）的单个存储库。</span><span class="sxs-lookup"><span data-stu-id="f6856-188">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="f6856-189">例如，Docker Hub 注册表中提供的 [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) 存储库使用相同的映像名称为 Linux 和 Windows Nano Server 提供支持。</span><span class="sxs-lookup"><span data-stu-id="f6856-189">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="f6856-190">从 Windows 主机拉取 [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) 映像时，也会拉取 Windows 变体，并且从 Linux 主机拉取同一映像名称时，也会拉取 Linux 变体。</span><span class="sxs-lookup"><span data-stu-id="f6856-190">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="f6856-191">**_从头开始创建基础映像_**</span><span class="sxs-lookup"><span data-stu-id="f6856-191">**_Create your base image from scratch_**</span></span>

<span data-ttu-id="f6856-192">可以从头开始创建自己的 Docker 基础映像，如 Docker 中的[文章](https://docs.docker.com/engine/userguide/eng-image/baseimages/)中所述。</span><span class="sxs-lookup"><span data-stu-id="f6856-192">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="f6856-193">如果刚开始使用 Docker，此方案可能不是最佳方案，但如果想为自己的基础映像设置特定位，则可采用此方案。</span><span class="sxs-lookup"><span data-stu-id="f6856-193">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="f6856-194">步骤 3：创建将服务嵌入其中的自定义 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="f6856-194">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="f6856-195">需要为构成应用的每个自定义服务创建相关映像。</span><span class="sxs-lookup"><span data-stu-id="f6856-195">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="f6856-196">如果应用由单个服务或 Web 应用组成，则只需创建单个映像即可。</span><span class="sxs-lookup"><span data-stu-id="f6856-196">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="f6856-197">考虑“外部循环 DevOps 工作流”时，只要将源代码推送到 Git 存储库（持续集成），就会通过自动构建过程创建映像，因此将在全局环境中从源代码创建映像。</span><span class="sxs-lookup"><span data-stu-id="f6856-197">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="f6856-198">但在考虑采用外部循环路由之前，需要确保 Docker 应用程序实际上正常工作，这样它们就不会将可能无法正常工作的代码推送到 Git 等源代码管理系统。</span><span class="sxs-lookup"><span data-stu-id="f6856-198">But before you consider going to that outer-loop route, you need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="f6856-199">因此，每个开发人员首先需要执行整个内部循环过程，才能在本地进行测试并继续开发，直到他们想要推送完整的功能或更改为源代码管理系统。</span><span class="sxs-lookup"><span data-stu-id="f6856-199">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="f6856-200">若要在本地环境中使用 DockerFile 创建映像，你可以使用 docker 生成命令，如图 4-25 所示，因为它已标记映像并使用简单的命令为应用程序中的所有服务生成映像。</span><span class="sxs-lookup"><span data-stu-id="f6856-200">To create an image in your local environment and using the DockerFile, you can use the docker build command, as shown in Figure 4-25, because it already tags the image for you and builds the images for all services in the application with a simple command.</span></span>

![显示 docker-compose 生成命令的控制台输出的屏幕截图。](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="f6856-202">图 4-25  。</span><span class="sxs-lookup"><span data-stu-id="f6856-202">**Figure 4-25**.</span></span> <span data-ttu-id="f6856-203">运行 docker build</span><span class="sxs-lookup"><span data-stu-id="f6856-203">Running docker build</span></span>

<span data-ttu-id="f6856-204">可以先使用运行 `dotnet publish` 命令生成一个包含所需 .NET 库的可部署文件夹，然后运行 `docker build`，而不是直接从项目文件夹运行 `docker build`（可选）。</span><span class="sxs-lookup"><span data-stu-id="f6856-204">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="f6856-205">此示例创建名为 `explore-docker-vscode/webapi:latest` 的 Docker 映像（`:latest` 是标记，类似于特定版本）。</span><span class="sxs-lookup"><span data-stu-id="f6856-205">This example creates a Docker image with the name `explore-docker-vscode/webapi:latest` (`:latest` is a tag, like a specific version).</span></span> <span data-ttu-id="f6856-206">可为需要为具有多个容器的组合 Docker 应用程序创建的每个自定义映像执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="f6856-206">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span> <span data-ttu-id="f6856-207">但是，我们将在下一节中看到使用 `docker-compose` 进行此操作更为简单。</span><span class="sxs-lookup"><span data-stu-id="f6856-207">However, we'll see in the next section that it's easier to do this using `docker-compose`.</span></span>

<span data-ttu-id="f6856-208">使用 `docker images` 命令可查找本地存储库（开发计算机）中的现有映像，如图 4-26 所示。</span><span class="sxs-lookup"><span data-stu-id="f6856-208">You can find the existing images in your local repository (your development machine) by using the `docker images` command, as illustrated in Figure 4-26.</span></span>

![命令 docker 映像的控制台输出，其中显示现有映像。](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="f6856-210">**图 4-26**。</span><span class="sxs-lookup"><span data-stu-id="f6856-210">**Figure 4-26**.</span></span> <span data-ttu-id="f6856-211">使用 docker 映像查看现有映像</span><span class="sxs-lookup"><span data-stu-id="f6856-211">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="f6856-212">步骤 4：在构建具有多服务的组合 Docker 应用时，在 docker-compose.yml 中定义服务</span><span class="sxs-lookup"><span data-stu-id="f6856-212">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="f6856-213">借助 `docker-compose.yml` 文件，可以使用下一步中介绍的部署命令定义要部署为组合应用程序的一组相关服务。</span><span class="sxs-lookup"><span data-stu-id="f6856-213">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="f6856-214">在主解决方案文件夹或根解决方案文件夹中创建该文件；该文件的内容应与此 `docker-compose.yml` 文件中显示的内容类似：</span><span class="sxs-lookup"><span data-stu-id="f6856-214">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

<span data-ttu-id="f6856-215">在此特定情况下，此文件定义三个服务：Web API 服务（自定义的服务）、Web 应用程序和 Redis 服务（常用缓存服务）。</span><span class="sxs-lookup"><span data-stu-id="f6856-215">In this particular case, this file defines three services: the web API service (your custom service), a web application, and the Redis service (a popular cache service).</span></span> <span data-ttu-id="f6856-216">每项服务都将作为容器部署，因此需要为每个服务使用具体的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="f6856-216">Each service will be deployed as a container, so you need to use a concrete Docker image for each.</span></span> <span data-ttu-id="f6856-217">对于此特定应用程序：</span><span class="sxs-lookup"><span data-stu-id="f6856-217">For this particular application:</span></span>

- <span data-ttu-id="f6856-218">Web API 服务是从 `src/WebApi/Dockerfile` 目录中的 DockerFile 生成的。</span><span class="sxs-lookup"><span data-stu-id="f6856-218">The web API service is built from the DockerFile in the `src/WebApi/Dockerfile` directory.</span></span>

- <span data-ttu-id="f6856-219">主机端口 51080 将转发到 `webapi` 容器上已公开的端口 80。</span><span class="sxs-lookup"><span data-stu-id="f6856-219">The host port 51080 is forwarded to the exposed port 80 on the `webapi` container.</span></span>

- <span data-ttu-id="f6856-220">Web API 服务依赖于 Redis 服务</span><span class="sxs-lookup"><span data-stu-id="f6856-220">The web API service depends on the Redis service</span></span>

- <span data-ttu-id="f6856-221">Web 应用程序使用内部地址 `http://webapi` 访问 Web API 服务。</span><span class="sxs-lookup"><span data-stu-id="f6856-221">The web application accesses the web API service using the internal address: `http://webapi`.</span></span>

- <span data-ttu-id="f6856-222">Redis 服务使用从 Docker Hub 注册表中拉取的[最新公共 redis 映像](https://hub.docker.com/_/redis/)。</span><span class="sxs-lookup"><span data-stu-id="f6856-222">The Redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="f6856-223">[Redis](https://redis.io/) 是服务器端应用程序的常用缓存系统。</span><span class="sxs-lookup"><span data-stu-id="f6856-223">[Redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="f6856-224">步骤 5：生成 Docker 应用并运行该应用</span><span class="sxs-lookup"><span data-stu-id="f6856-224">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="f6856-225">如果应用只有一个容器，只需将其部署到 Docker 主机（VM 或物理服务器），即可运行该应用。</span><span class="sxs-lookup"><span data-stu-id="f6856-225">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="f6856-226">但是，如果应用由多个服务组成，则需要进行编写  。</span><span class="sxs-lookup"><span data-stu-id="f6856-226">However, if your app is made up of multiple services, you need to _compose it_, too.</span></span> <span data-ttu-id="f6856-227">接下来查看不同的选项。</span><span class="sxs-lookup"><span data-stu-id="f6856-227">Let's see the different options.</span></span>

<span data-ttu-id="f6856-228">**_选项 A：运行单个容器或服务_**</span><span class="sxs-lookup"><span data-stu-id="f6856-228">**_Option A: Run a single container or service_**</span></span>

<span data-ttu-id="f6856-229">使用 docker 运行命令，即可运行 Docker 映像，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f6856-229">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 50080:80 explore-docker-vscode/webapp:latest
```

<span data-ttu-id="f6856-230">对于此特定部署，我们会将发送到主机上端口 50080 的请求重定向到内部端口 80。</span><span class="sxs-lookup"><span data-stu-id="f6856-230">For this particular deployment, we'll be redirecting requests sent to port 50080 on the host to the internal port 80.</span></span>

<span data-ttu-id="f6856-231">**_选项 B：编写和运行多容器应用程序_**</span><span class="sxs-lookup"><span data-stu-id="f6856-231">**_Option B: Compose and run a multiple-container application_**</span></span>

<span data-ttu-id="f6856-232">在大多数企业场景中，Docker 应用程序将由多个服务组成。</span><span class="sxs-lookup"><span data-stu-id="f6856-232">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="f6856-233">对于这些情况，你可以运行 `docker-compose up` 命令（图 4-27），该命令将使用吧之前创建的 docker-compose.yml 文件。</span><span class="sxs-lookup"><span data-stu-id="f6856-233">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you created previously.</span></span> <span data-ttu-id="f6856-234">运行此命令将构建所有自定义映像，并使用其所有相关容器部署组合式应用程序。</span><span class="sxs-lookup"><span data-stu-id="f6856-234">Running this command builds all custom images and deploys the composed application with all of its related containers.</span></span>

![来自 docker-compose up 命令的控制台输出。](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="f6856-236">**图 4-27**。</span><span class="sxs-lookup"><span data-stu-id="f6856-236">**Figure 4-27**.</span></span> <span data-ttu-id="f6856-237">运行“docker-compose up”命令的结果</span><span class="sxs-lookup"><span data-stu-id="f6856-237">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="f6856-238">运行 `docker-compose up` 后，（如图 4-28 所示）在 VM 表示形式中将应用程序及其相关容器部署到 Docker 主机中。</span><span class="sxs-lookup"><span data-stu-id="f6856-238">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![运行多容器应用程序的 VM。](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="f6856-240">**图 4-28**。</span><span class="sxs-lookup"><span data-stu-id="f6856-240">**Figure 4-28**.</span></span> <span data-ttu-id="f6856-241">部署了 Docker 容器的 VM</span><span class="sxs-lookup"><span data-stu-id="f6856-241">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="f6856-242">步骤 6：在本地（在本地 CD VM 中）测试 Docker 应用程序</span><span class="sxs-lookup"><span data-stu-id="f6856-242">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="f6856-243">这一步骤会因应用的用途而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f6856-243">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="f6856-244">在部署为单个容器或服务的简单 .NET Core Web API“Hello World”中，只需提供 DockerFile 中指定的 TCP 端口，即可访问该服务。</span><span class="sxs-lookup"><span data-stu-id="f6856-244">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="f6856-245">在 Docker 主机上，打开浏览器并导航到该站点，应看到应用/服务正在运行（如图 4-29 所示）。</span><span class="sxs-lookup"><span data-stu-id="f6856-245">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![来自 localhost/API/值的响应的浏览器视图。](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="f6856-247">**图 4-29**。</span><span class="sxs-lookup"><span data-stu-id="f6856-247">**Figure 4-29**.</span></span> <span data-ttu-id="f6856-248">使用浏览器在本地测试 Docker 应用程序</span><span class="sxs-lookup"><span data-stu-id="f6856-248">Testing your Docker application locally by using the browser</span></span>

<span data-ttu-id="f6856-249">请注意，它将使用端口 50080，但在内部它被重定向到端口 80，因为这是使用 `docker compose` 部署它的方式，如前所述。</span><span class="sxs-lookup"><span data-stu-id="f6856-249">Note that it's using port 50080, but internally it's being redirected to port 80, because that's how it was deployed with `docker compose`, as explained earlier.</span></span>

<span data-ttu-id="f6856-250">可以通过浏览器使用来自终端的 CURL 对此进行测试，如图 4-30 所示。</span><span class="sxs-lookup"><span data-stu-id="f6856-250">You can test this by using the browser using CURL from the terminal, as depicted in Figure 4-30.</span></span>

![从 http://localhost:51080/WeatherForecast 获取的 Curl 结果](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="f6856-252">**图 4-30**。</span><span class="sxs-lookup"><span data-stu-id="f6856-252">**Figure 4-30**.</span></span> <span data-ttu-id="f6856-253">使用 CURL 在本地测试 Docker 应用程序</span><span class="sxs-lookup"><span data-stu-id="f6856-253">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="f6856-254">**调试在 Docker 上运行的容器**</span><span class="sxs-lookup"><span data-stu-id="f6856-254">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="f6856-255">如果使用的是 Node.js 和 .NET Core 容器等其他平台，则 Visual Studio Code 支持调试 Docker。</span><span class="sxs-lookup"><span data-stu-id="f6856-255">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="f6856-256">使用 Visual Studio for Windows or Visual Studio for Mac 时，还可以在 Docker 中调试 .NET Core 或 .NET Framework 容器，如下一节所述。</span><span class="sxs-lookup"><span data-stu-id="f6856-256">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="f6856-257">如需了解有关调试 Node.js Docker 容器的详细信息，请参阅 <https://blog.docker.com/2016/07/live-debugging-docker/> 和 <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>。</span><span class="sxs-lookup"><span data-stu-id="f6856-257">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="f6856-258">[上一页](docker-apps-development-environment.md)
> [下一页](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="f6856-258">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
