---
title: 适用于 WCF 开发人员的 Docker gRPC
description: 为 ASP.NET Core gRPC 应用程序创建 Docker 映像
ms.date: 09/02/2019
ms.openlocfilehash: 379750edfa1a9fc282e43ffa83e5695425f31a26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152710"
---
# <a name="create-docker-images"></a><span data-ttu-id="84eea-103">创建 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="84eea-103">Create Docker images</span></span>

<span data-ttu-id="84eea-104">本部分介绍如何创建用于 ASP.NET Core gRPC 应用程序的 Docker 映像，并准备在 Docker、Kubernetes 或其他容器环境中运行。</span><span class="sxs-lookup"><span data-stu-id="84eea-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="84eea-105">在 GitHub 上的 [dotnet/gRPC/](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) 存储库中提供了使用的示例应用程序，其中包含 ASP.NET Core MVC web 应用和 gRPC 服务。</span><span class="sxs-lookup"><span data-stu-id="84eea-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="84eea-106">用于 ASP.NET Core 应用程序的 Microsoft 基础映像</span><span class="sxs-lookup"><span data-stu-id="84eea-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="84eea-107">Microsoft 提供了一系列用于构建和运行 .NET Core 应用程序的基本映像。</span><span class="sxs-lookup"><span data-stu-id="84eea-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="84eea-108">若要创建 ASP.NET Core 3.0 映像，请使用两个基本映像：</span><span class="sxs-lookup"><span data-stu-id="84eea-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="84eea-109">用于生成和发布应用程序的 SDK 映像。</span><span class="sxs-lookup"><span data-stu-id="84eea-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="84eea-110">用于部署的运行时映像。</span><span class="sxs-lookup"><span data-stu-id="84eea-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="84eea-111">映像</span><span class="sxs-lookup"><span data-stu-id="84eea-111">Image</span></span> | <span data-ttu-id="84eea-112">描述</span><span class="sxs-lookup"><span data-stu-id="84eea-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="84eea-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="84eea-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="84eea-114">用于生成应用程序 `docker build` 。</span><span class="sxs-lookup"><span data-stu-id="84eea-114">For building applications with `docker build`.</span></span> <span data-ttu-id="84eea-115">不能在生产中使用。</span><span class="sxs-lookup"><span data-stu-id="84eea-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="84eea-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="84eea-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="84eea-117">包含运行时和 ASP.NET Core 依赖项。</span><span class="sxs-lookup"><span data-stu-id="84eea-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="84eea-118">用于生产。</span><span class="sxs-lookup"><span data-stu-id="84eea-118">For production.</span></span> |

<span data-ttu-id="84eea-119">对于每个映像，都有四个基于不同 Linux 分发的变量，由标记来区分。</span><span class="sxs-lookup"><span data-stu-id="84eea-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="84eea-120">图像标记 (s) </span><span class="sxs-lookup"><span data-stu-id="84eea-120">Image tag(s)</span></span> | <span data-ttu-id="84eea-121">Linux</span><span class="sxs-lookup"><span data-stu-id="84eea-121">Linux</span></span> | <span data-ttu-id="84eea-122">说明</span><span class="sxs-lookup"><span data-stu-id="84eea-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="84eea-123">3.0-buster、3。0</span><span class="sxs-lookup"><span data-stu-id="84eea-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="84eea-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="84eea-124">Debian 10</span></span> | <span data-ttu-id="84eea-125">如果未指定操作系统变体，则为默认映像。</span><span class="sxs-lookup"><span data-stu-id="84eea-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="84eea-126">3.0-alpine</span><span class="sxs-lookup"><span data-stu-id="84eea-126">3.0-alpine</span></span> | <span data-ttu-id="84eea-127">Alpine 3。9</span><span class="sxs-lookup"><span data-stu-id="84eea-127">Alpine 3.9</span></span> | <span data-ttu-id="84eea-128">Alpine 基本映像比 Debian 或 Ubuntu 映像小得多。</span><span class="sxs-lookup"><span data-stu-id="84eea-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="84eea-129">3.0-disco</span><span class="sxs-lookup"><span data-stu-id="84eea-129">3.0-disco</span></span> | <span data-ttu-id="84eea-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="84eea-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="84eea-131">3.0-bionic</span><span class="sxs-lookup"><span data-stu-id="84eea-131">3.0-bionic</span></span> | <span data-ttu-id="84eea-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="84eea-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="84eea-133">对于 Debian 和 Ubuntu 映像，Alpine 基本映像约 100 MB，比较 200 MB。</span><span class="sxs-lookup"><span data-stu-id="84eea-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="84eea-134">某些软件包或库可能在 Alpine 的包管理中不可用。</span><span class="sxs-lookup"><span data-stu-id="84eea-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="84eea-135">如果你不确定要使用哪个映像，则应选择默认 Debian。</span><span class="sxs-lookup"><span data-stu-id="84eea-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84eea-136">请确保为生成和运行时使用相同的 Linux 变体。</span><span class="sxs-lookup"><span data-stu-id="84eea-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="84eea-137">在一个变体上构建和发布的应用程序可能无法在另一个上运行。</span><span class="sxs-lookup"><span data-stu-id="84eea-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="84eea-138">创建 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="84eea-138">Create a Docker image</span></span>

<span data-ttu-id="84eea-139">Docker 映像由 *Dockerfile*定义。</span><span class="sxs-lookup"><span data-stu-id="84eea-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="84eea-140">这是一个文本文件，其中包含生成应用程序所需的所有命令，并安装生成或运行该应用程序所需的任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="84eea-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="84eea-141">下面的示例演示 ASP.NET Core 3.0 应用程序的最简单的 Dockerfile：</span><span class="sxs-lookup"><span data-stu-id="84eea-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

<span data-ttu-id="84eea-142">Dockerfile 包含两个部分：第一个部分使用 `sdk` 基本映像来生成和发布应用程序; 第二个部分从基中创建运行时映像 `aspnet` 。</span><span class="sxs-lookup"><span data-stu-id="84eea-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="84eea-143">这是因为，在运行 `sdk` 时，图像大约为 900 mb，对于运行时映像约 200 mb，其大部分内容是不必要的。</span><span class="sxs-lookup"><span data-stu-id="84eea-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="84eea-144">生成步骤</span><span class="sxs-lookup"><span data-stu-id="84eea-144">The build steps</span></span>

| <span data-ttu-id="84eea-145">步骤</span><span class="sxs-lookup"><span data-stu-id="84eea-145">Step</span></span> | <span data-ttu-id="84eea-146">说明</span><span class="sxs-lookup"><span data-stu-id="84eea-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="84eea-147">声明基映像并分配 `builder` 别名。</span><span class="sxs-lookup"><span data-stu-id="84eea-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="84eea-148">创建 `/src` 目录并将其设置为当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="84eea-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="84eea-149">将主机上当前目录下的所有内容复制到映像上的当前目录。</span><span class="sxs-lookup"><span data-stu-id="84eea-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="84eea-150">还原 (ASP.NET Core 3.0 framework 的所有外部包都已随 SDK) 预先安装。</span><span class="sxs-lookup"><span data-stu-id="84eea-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="84eea-151">生成并发布发布版本。</span><span class="sxs-lookup"><span data-stu-id="84eea-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="84eea-152">请注意， `--runtime` 标志不是必需的。</span><span class="sxs-lookup"><span data-stu-id="84eea-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="84eea-153">运行时映像步骤</span><span class="sxs-lookup"><span data-stu-id="84eea-153">The runtime image steps</span></span>

| <span data-ttu-id="84eea-154">步骤</span><span class="sxs-lookup"><span data-stu-id="84eea-154">Step</span></span> | <span data-ttu-id="84eea-155">说明</span><span class="sxs-lookup"><span data-stu-id="84eea-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="84eea-156">声明新的基本映像。</span><span class="sxs-lookup"><span data-stu-id="84eea-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="84eea-157">创建 `/app` 目录并将其设置为当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="84eea-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="84eea-158">使用第一行中的别名从上一个映像复制已发布的应用程序 `builder` `FROM` 。</span><span class="sxs-lookup"><span data-stu-id="84eea-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="84eea-159">设置要在容器启动时运行的命令。</span><span class="sxs-lookup"><span data-stu-id="84eea-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="84eea-160">`dotnet`运行时映像中的命令只能运行 DLL 文件。</span><span class="sxs-lookup"><span data-stu-id="84eea-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="84eea-161">Docker 中的 HTTPS</span><span class="sxs-lookup"><span data-stu-id="84eea-161">HTTPS in Docker</span></span>

<span data-ttu-id="84eea-162">用于 Docker 的 Microsoft 基本映像将 `ASPNETCORE_URLS` 环境变量设置为 `http://+:80` ，这意味着在该端口上运行的 Kestrel 不带 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="84eea-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="84eea-163">如果对自定义证书使用 HTTPS (如) [自承载 gRPC 应用程序](self-hosted.md) 中所述），则应覆盖此项。</span><span class="sxs-lookup"><span data-stu-id="84eea-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="84eea-164">在 Dockerfile 的运行时映像创建部分设置环境变量。</span><span class="sxs-lookup"><span data-stu-id="84eea-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="84eea-165">.Dockerignore 文件</span><span class="sxs-lookup"><span data-stu-id="84eea-165">The .dockerignore file</span></span>

<span data-ttu-id="84eea-166">与 `.gitignore` 从源代码管理中排除某些文件和目录的文件非常相似， `.dockerignore` 文件可用于在生成过程中排除文件和目录被复制到映像。</span><span class="sxs-lookup"><span data-stu-id="84eea-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="84eea-167">这不仅会节省时间复制，还可以避免在将 `obj` 目录从 PC 复制到映像时出现的一些错误。</span><span class="sxs-lookup"><span data-stu-id="84eea-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="84eea-168">你至少应在文件中添加和的 `bin` 条目 `obj` `.dockerignore` 。</span><span class="sxs-lookup"><span data-stu-id="84eea-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="84eea-169">生成映像</span><span class="sxs-lookup"><span data-stu-id="84eea-169">Build the image</span></span>

<span data-ttu-id="84eea-170">对于具有单个应用程序的解决方案，因此，如果是单个 Dockerfile，则最简单的方法是将 Dockerfile 放在基目录中。</span><span class="sxs-lookup"><span data-stu-id="84eea-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="84eea-171">换句话说，将其放在文件所在的目录中 `.sln` 。</span><span class="sxs-lookup"><span data-stu-id="84eea-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="84eea-172">在这种情况下，若要生成映像，请在包含 Dockerfile 的目录中使用以下 `docker build` 命令。</span><span class="sxs-lookup"><span data-stu-id="84eea-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="84eea-173">令困惑命名 `--tag` 标志 (可以缩短为 `-t`) 指定图像的整个名称，包括实际标记（如果指定）。</span><span class="sxs-lookup"><span data-stu-id="84eea-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="84eea-174">`.`结束时指定将在其中运行生成的上下文; `COPY` Dockerfile 中命令的当前工作目录。</span><span class="sxs-lookup"><span data-stu-id="84eea-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="84eea-175">如果一个解决方案中有多个应用程序，则可以将每个应用程序的 Dockerfile 保存在其自己的文件夹中的 `.csproj` 文件旁边。</span><span class="sxs-lookup"><span data-stu-id="84eea-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="84eea-176">你仍应该 `docker build` 从基本目录运行命令，以确保将解决方案和所有项目都复制到映像中。</span><span class="sxs-lookup"><span data-stu-id="84eea-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="84eea-177">可以通过使用 `--file` (或) 标志，在当前目录下指定 Dockerfile `-f` 。</span><span class="sxs-lookup"><span data-stu-id="84eea-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="84eea-178">在计算机上的容器中运行映像</span><span class="sxs-lookup"><span data-stu-id="84eea-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="84eea-179">若要在本地 Docker 实例中运行映像，请使用 `docker run` 命令。</span><span class="sxs-lookup"><span data-stu-id="84eea-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="84eea-180">`-ti`标志将当前终端连接到容器的终端，并在交互模式下运行。</span><span class="sxs-lookup"><span data-stu-id="84eea-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="84eea-181">`-p 5000:80`发布 (将容器上的端口 80) 链接到 localhost 网络接口上的端口5000。</span><span class="sxs-lookup"><span data-stu-id="84eea-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="84eea-182">将映像推送到注册表</span><span class="sxs-lookup"><span data-stu-id="84eea-182">Push the image to a registry</span></span>

<span data-ttu-id="84eea-183">验证映像工作后，将其推送到 Docker 注册表，使其在其他系统上可用。</span><span class="sxs-lookup"><span data-stu-id="84eea-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="84eea-184">内部网络将需要预配 Docker 注册表。</span><span class="sxs-lookup"><span data-stu-id="84eea-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="84eea-185">这可以像运行 [docker 的 `registry` 映像](https://docs.docker.com/registry/deploying/) 一样简单， (Docker 注册表在 docker 容器中运行) ，但可以使用各种更全面的解决方案。</span><span class="sxs-lookup"><span data-stu-id="84eea-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="84eea-186">对于外部共享和云使用，有多种可用的托管注册表，如 [Azure 容器注册表](/azure/container-registry/) 或 [Docker Hub](https://docs.docker.com/docker-hub/repos/)。</span><span class="sxs-lookup"><span data-stu-id="84eea-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="84eea-187">若要推送到 Docker Hub，请将映像名称作为你的用户或组织名称作为前缀。</span><span class="sxs-lookup"><span data-stu-id="84eea-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="84eea-188">若要推送到专用注册表，请使用注册表主机名和组织名称作为映像名称的前缀。</span><span class="sxs-lookup"><span data-stu-id="84eea-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="84eea-189">映像位于注册表中后，可以将其部署到各个 Docker 主机或容器业务流程引擎（如 Kubernetes）。</span><span class="sxs-lookup"><span data-stu-id="84eea-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="84eea-190">[上一页](self-hosted.md)
>[下一页](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="84eea-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
