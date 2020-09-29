---
title: 什么是 Docker？
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 什么是 Docker？
ms.date: 08/31/2018
ms.openlocfilehash: 7d4b419f46f32fa4acdeb1ac7d5e0c2b2c199fc5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172399"
---
# <a name="what-is-docker"></a><span data-ttu-id="4845e-103">什么是 Docker？</span><span class="sxs-lookup"><span data-stu-id="4845e-103">What is Docker?</span></span>

<span data-ttu-id="4845e-104">[Docker](https://www.docker.com/) 是一种[开源项目](https://github.com/docker/docker)，用于将应用程序自动部署为可在云或本地运行的便携式独立容器。</span><span class="sxs-lookup"><span data-stu-id="4845e-104">[Docker](https://www.docker.com/) is an [open-source project](https://github.com/docker/docker) for automating the deployment of applications as portable, self-sufficient containers that can run on the cloud or on-premises.</span></span> <span data-ttu-id="4845e-105">Docker 也是一家[公司](https://www.docker.com/)，它与云、Linux 和 Windows 供应商（包括 Microsoft）协作，致力于推广和发展这项技术。</span><span class="sxs-lookup"><span data-stu-id="4845e-105">Docker is also a [company](https://www.docker.com/) that promotes and evolves this technology, working in collaboration with cloud, Linux, and Windows vendors, including Microsoft.</span></span>

![显示 Docker 容器可运行位置的关系图。](./media/docker-defined/docker-containers-run-anywhere.png)

<span data-ttu-id="4845e-107">**图 2-2**。</span><span class="sxs-lookup"><span data-stu-id="4845e-107">**Figure 2-2**.</span></span> <span data-ttu-id="4845e-108">Docker 在混合云的所有层部署容器。</span><span class="sxs-lookup"><span data-stu-id="4845e-108">Docker deploys containers at all layers of the hybrid cloud.</span></span>

<span data-ttu-id="4845e-109">Docker 容器可以在任意位置运行：在客户数据中心本地、在外部服务提供商或在 Azure 云中。</span><span class="sxs-lookup"><span data-stu-id="4845e-109">Docker containers can run anywhere, on-premises in the customer datacenter, in an external service provider or in the cloud, on Azure.</span></span> <span data-ttu-id="4845e-110">Docker 映像容器可以在 Linux 和 Windows 上本机运行。</span><span class="sxs-lookup"><span data-stu-id="4845e-110">Docker image containers can run natively on Linux and Windows.</span></span> <span data-ttu-id="4845e-111">但是，Windows 映像仅能在 Windows 主机上运行，Linux 映像可以在 Linux 主机和 Windows 主机上运行（到目前为止，使用 Hyper-V Linux VM），其中主机是指服务器或 VM。</span><span class="sxs-lookup"><span data-stu-id="4845e-111">However, Windows images can run only on Windows hosts and Linux images can run on Linux hosts and Windows hosts (using a Hyper-V Linux VM, so far), where host means a server or a VM.</span></span>

<span data-ttu-id="4845e-112">开发人员可以在 Windows、Linux 或 macOS 上使用开发环境。</span><span class="sxs-lookup"><span data-stu-id="4845e-112">Developers can use development environments on Windows, Linux, or macOS.</span></span> <span data-ttu-id="4845e-113">在开发计算机上，开发人员运行部署了 Docker 映像（包括应用及其依赖项）的 Docker 主机。</span><span class="sxs-lookup"><span data-stu-id="4845e-113">On the development computer, the developer runs a Docker host where Docker images are deployed, including the app and its dependencies.</span></span> <span data-ttu-id="4845e-114">在 Linux 或 macOS 上进行开发的开发人员使用基于 Linux 的 Docker 主机，并且他们可以仅为 Linux 容器创建映像。</span><span class="sxs-lookup"><span data-stu-id="4845e-114">Developers who work on Linux or on macOS use a Docker host that is Linux based, and they can create images only for Linux containers.</span></span> <span data-ttu-id="4845e-115">（在 macOS 上进行开发的开发人员可以从 macOS 中编辑代码或运行 Docker CLI，但截至撰写本文时，容器不在 macOS 上直接运行。）在 Windows 上进行开发的开发人员可以为 Linux 或 Windows 容器创建映像。</span><span class="sxs-lookup"><span data-stu-id="4845e-115">(Developers working on macOS can edit code or run the Docker CLI from macOS, but as of the time of this writing, containers don't run directly on macOS.) Developers who work on Windows can create images for either Linux or Windows Containers.</span></span>

<span data-ttu-id="4845e-116">为了在开发环境中承载容器，并提供其他开发人员工具，Docker 为 Windows 或 macOS 提供了 [Docker 社区版 (CE)](https://www.docker.com/community-edition)。</span><span class="sxs-lookup"><span data-stu-id="4845e-116">To host containers in development environments and provide additional developer tools, Docker ships [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows or for macOS.</span></span> <span data-ttu-id="4845e-117">这些产品安装了承载容器所需的 VM（Docker 主机）。</span><span class="sxs-lookup"><span data-stu-id="4845e-117">These products install the necessary VM (the Docker host) to host the containers.</span></span> <span data-ttu-id="4845e-118">Docker 还提供 [Docker 企业版 (EE)](https://www.docker.com/enterprise-edition)，该版本专为企业开发而设计，供生成、交付和在生产中运行大型业务关键型应用程序的 IT 团队使用。</span><span class="sxs-lookup"><span data-stu-id="4845e-118">Docker also makes available [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), which is designed for enterprise development and is used by IT teams who build, ship, and run large business-critical applications in production.</span></span>

<span data-ttu-id="4845e-119">若要运行 [Windows 容器](/virtualization/windowscontainers/about/)，有两种类型的运行时可供使用：</span><span class="sxs-lookup"><span data-stu-id="4845e-119">To run [Windows Containers](/virtualization/windowscontainers/about/), there are two types of runtimes:</span></span>

- <span data-ttu-id="4845e-120">Windows Server 容器通过进程和命名空间隔离技术提供应用程序隔离。</span><span class="sxs-lookup"><span data-stu-id="4845e-120">Windows Server Containers provide application isolation through process and namespace isolation technology.</span></span> <span data-ttu-id="4845e-121">Windows Server 容器与容器主机和主机上运行的所有容器共享内核。</span><span class="sxs-lookup"><span data-stu-id="4845e-121">A Windows Server Container shares a kernel with the container host and with all containers running on the host.</span></span>

- <span data-ttu-id="4845e-122">Hyper-V 容器通过在高度优化的虚拟机中运行各容器来扩展 Windows Server 容器提供的隔离。</span><span class="sxs-lookup"><span data-stu-id="4845e-122">Hyper-V Containers expand on the isolation provided by Windows Server Containers by running each container in a highly optimized virtual machine.</span></span> <span data-ttu-id="4845e-123">在此配置中，容器主机的内核不与 Hyper-V 容器共享，以提供更好的隔离。</span><span class="sxs-lookup"><span data-stu-id="4845e-123">In this configuration, the kernel of the container host isn't shared with the Hyper-V Containers, providing better isolation.</span></span>

<span data-ttu-id="4845e-124">这些容器的映像的创建和运行方式均相同。</span><span class="sxs-lookup"><span data-stu-id="4845e-124">The images for these containers are created the same way and function the same.</span></span> <span data-ttu-id="4845e-125">区别在于，在运行 Hyper-V 容器的映像中创建容器的方式需要使用其他参数。</span><span class="sxs-lookup"><span data-stu-id="4845e-125">The difference is in how the container is created from the image running a Hyper-V Container requires an extra parameter.</span></span> <span data-ttu-id="4845e-126">有关详细信息，请参阅 [Hyper-V 容器](/virtualization/windowscontainers/manage-containers/hyperv-container)。</span><span class="sxs-lookup"><span data-stu-id="4845e-126">For details, see [Hyper-V Containers](/virtualization/windowscontainers/manage-containers/hyperv-container).</span></span>

## <a name="comparing-docker-containers-with-virtual-machines"></a><span data-ttu-id="4845e-127">比较 Docker 容器和虚拟机</span><span class="sxs-lookup"><span data-stu-id="4845e-127">Comparing Docker containers with virtual machines</span></span>

<span data-ttu-id="4845e-128">图 2-3 显示了 VM 和 Docker 容器之间的比较。</span><span class="sxs-lookup"><span data-stu-id="4845e-128">Figure 2-3 shows a comparison between VMs and Docker containers.</span></span>

| <span data-ttu-id="4845e-129">虚拟机</span><span class="sxs-lookup"><span data-stu-id="4845e-129">Virtual Machines</span></span> | <span data-ttu-id="4845e-130">Docker 容器</span><span class="sxs-lookup"><span data-stu-id="4845e-130">Docker Containers</span></span> |
| -----------------| ------------------|
|![显示传统 VM 的硬件/软件堆栈的关系图。](./media/docker-defined/virtual-machine-hardware-software.png)|![显示 Docker 容器的硬件/软件堆栈的关系图。](./media/docker-defined/docker-container-hardware-software.png)|
|<span data-ttu-id="4845e-133">虚拟机包括应用程序、必需的库或二进制文件以及完整的来宾操作系统。</span><span class="sxs-lookup"><span data-stu-id="4845e-133">Virtual machines include the application, the required libraries or binaries, and a full guest operating system.</span></span> <span data-ttu-id="4845e-134">与比容器化相比，完全虚拟化需要更多资源。</span><span class="sxs-lookup"><span data-stu-id="4845e-134">Full virtualization requires more resources than containerization.</span></span> | <span data-ttu-id="4845e-135">容器包括应用程序及其所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="4845e-135">Containers include the application and all its dependencies.</span></span> <span data-ttu-id="4845e-136">但是，它们与其他容器共享 OS 内核，在主机操作系统上的用户空间中作为独立进程运行。</span><span class="sxs-lookup"><span data-stu-id="4845e-136">However, they share the OS kernel with other containers, running as isolated processes in user space on the host operating system.</span></span> <span data-ttu-id="4845e-137">（Hyper-V 容器例外，其中的每个容器都在各容器特定虚拟机内部运行。）</span><span class="sxs-lookup"><span data-stu-id="4845e-137">(Except in Hyper-V containers, where each container runs inside of a special virtual machine per container.)</span></span> |

<span data-ttu-id="4845e-138">**图 2-3**。</span><span class="sxs-lookup"><span data-stu-id="4845e-138">**Figure 2-3**.</span></span> <span data-ttu-id="4845e-139">比较传统虚拟机与 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="4845e-139">Comparison of traditional virtual machines to Docker containers</span></span>

<span data-ttu-id="4845e-140">对于 VM，在主机服务器中有三个基本层，从底部向上依次为：基础结构、主机操作系统和虚拟机监控程序，在所有这些层的顶部，每个 VM 都有其自己的 OS 和所有必需的库。</span><span class="sxs-lookup"><span data-stu-id="4845e-140">For VMs, there are three base layers in the host server, from the bottom-up: infrastructure, Host Operating System and a Hypervisor and on top of all that each VM has its own OS and all necessary libraries.</span></span> <span data-ttu-id="4845e-141">对于 Docker，主机服务器仅有基础结构和 OS，在其顶部是容器引擎，它将容器隔离，但共享基础 OS 服务。</span><span class="sxs-lookup"><span data-stu-id="4845e-141">For Docker, the host server only has the infrastructure and the OS and on top of that, the container engine, that keeps container isolated but sharing the base OS services.</span></span>

<span data-ttu-id="4845e-142">由于容器所需的资源要少得多（例如，它们不需要一个完整的 OS），所以它们易于部署且可快速启动。</span><span class="sxs-lookup"><span data-stu-id="4845e-142">Because containers require far fewer resources (for example, they don't need a full OS), they're easy to deploy and they start fast.</span></span> <span data-ttu-id="4845e-143">这使你能够具有更高的密度，也就是说，这允许你在同一硬件单元上运行更多服务，从而降低了成本。</span><span class="sxs-lookup"><span data-stu-id="4845e-143">This allows you to have higher density, meaning that it allows you to run more services on the same hardware unit, thereby reducing costs.</span></span>

<span data-ttu-id="4845e-144">在同一内核上运行的副作用是，你获得的隔离比 VM 要少。</span><span class="sxs-lookup"><span data-stu-id="4845e-144">As a side effect of running on the same kernel, you get less isolation than VMs.</span></span>

<span data-ttu-id="4845e-145">映像的主要目标是使环境（依赖项）在不同的部署中保持不变。</span><span class="sxs-lookup"><span data-stu-id="4845e-145">The main goal of an image is that it makes the environment (dependencies) the same across different deployments.</span></span> <span data-ttu-id="4845e-146">也就是说，可以在计算机上调试它，然后将其部署到保证具有相同环境的另一台计算机上。</span><span class="sxs-lookup"><span data-stu-id="4845e-146">This means that you can debug it on your machine and then deploy it to another machine with the same environment guaranteed.</span></span>

<span data-ttu-id="4845e-147">借助容器映像，可打包应用或服务并采用可靠且可重现的方式对其进行部署。</span><span class="sxs-lookup"><span data-stu-id="4845e-147">A container image is a way to package an app or service and deploy it in a reliable and reproducible way.</span></span> <span data-ttu-id="4845e-148">可以说 Docker 不只是一种技术，还是一种原理和过程。</span><span class="sxs-lookup"><span data-stu-id="4845e-148">You could say that Docker isn't only a technology but also a philosophy and a process.</span></span>

<span data-ttu-id="4845e-149">在使用 Docker 时，你不会听到开发人员说：“为什么它能在我的计算机上使用却不能用在生产中？”</span><span class="sxs-lookup"><span data-stu-id="4845e-149">When using Docker, you won't hear developers say, "It works on my machine, why not in production?"</span></span> <span data-ttu-id="4845e-150">他们只需说“它在 Docker 上运行”，因为打包的 Docker 应用程序可在任何支持的 Docker 环境上执行，而且它在所有部署目标（例如，开发、QA、暂存和生产）上都按预期运行。</span><span class="sxs-lookup"><span data-stu-id="4845e-150">They can simply say, "It runs on Docker", because the packaged Docker application can be executed on any supported Docker environment, and it runs the way it was intended to on all deployment targets (such as Dev, QA, staging, and production).</span></span>

## <a name="a-simple-analogy"></a><span data-ttu-id="4845e-151">一个简单的类比</span><span class="sxs-lookup"><span data-stu-id="4845e-151">A simple analogy</span></span>

<span data-ttu-id="4845e-152">也许一个简单的类比有助于掌握 Docker 的核心概念。</span><span class="sxs-lookup"><span data-stu-id="4845e-152">Perhaps a simple analogy can help getting the grasp of the core concept of Docker.</span></span>

<span data-ttu-id="4845e-153">让我们回到 20 世纪 50 年代。</span><span class="sxs-lookup"><span data-stu-id="4845e-153">Let's go back in time to the 1950s for a moment.</span></span> <span data-ttu-id="4845e-154">那时，还没有处理器这个词，而复印机无处不在（某种程度上）。</span><span class="sxs-lookup"><span data-stu-id="4845e-154">There were no word processors, and the photocopiers were used everywhere (kind of).</span></span>

<span data-ttu-id="4845e-155">假设你负责按要求快速发出成批的信件、将这些信件邮寄给客户、使用纸张和信封以物理方式寄送到每个客户的地址（那时还没有电子邮件）。</span><span class="sxs-lookup"><span data-stu-id="4845e-155">Imagine you're responsible for quickly issuing batches of letters as required, to mail them to customers, using real paper and envelopes, to be delivered physically to each customer's address (there was no email back then).</span></span>

<span data-ttu-id="4845e-156">在某个时候，你意识到，这些信件只是由一大组段落组合而成的，根据信件的用途对其进行所需的选取和排列，因此，你设计了一个系统，以快速发送这些信件，希望能大幅提高效率。</span><span class="sxs-lookup"><span data-stu-id="4845e-156">At some point, you realize the letters are just a composition of a large set of paragraphs, which are picked and arranged as needed, according to the purpose of the letter, so you devise a system to issue letters quickly, expecting to get a hefty raise.</span></span>

<span data-ttu-id="4845e-157">这个系统很简单：</span><span class="sxs-lookup"><span data-stu-id="4845e-157">The system is simple:</span></span>

1. <span data-ttu-id="4845e-158">先从一副透明薄片开始，每个薄片包含一个段落。</span><span class="sxs-lookup"><span data-stu-id="4845e-158">You begin with a deck of transparent sheets containing one paragraph each.</span></span>

2. <span data-ttu-id="4845e-159">若要发送一组信件，你选择包含所需段落的薄片，然后堆栈并对齐它们，使其外观一致且易于阅读。</span><span class="sxs-lookup"><span data-stu-id="4845e-159">To issue a set of letters, you pick the sheets with the paragraphs you need, then you stack and align them so they look and read fine.</span></span>

3. <span data-ttu-id="4845e-160">最后，你将其置于复印机中并按开始，以生成所需的多个信件。</span><span class="sxs-lookup"><span data-stu-id="4845e-160">Finally, you place the set in the photocopier and press start to produce as many letters as required.</span></span>

<span data-ttu-id="4845e-161">简而言之，这就是 Docker 的核心理念。</span><span class="sxs-lookup"><span data-stu-id="4845e-161">So, simplifying, that's the core idea of Docker.</span></span>

<span data-ttu-id="4845e-162">在 Docker 中，每层都是在执行命令（例如，安装程序）后在文件系统所发生的一组更改。</span><span class="sxs-lookup"><span data-stu-id="4845e-162">In Docker, each layer is the resulting set of changes that happen to the filesystem after executing a command, such as, installing a program.</span></span>

<span data-ttu-id="4845e-163">因此，当你在复制层后“查看”文件系统时，你将看到所有文件，包括在安装程序时的层。</span><span class="sxs-lookup"><span data-stu-id="4845e-163">So, when you "look" at the filesystem after the layer has been copied, you see all the files, included the layer when the program was installed.</span></span>

<span data-ttu-id="4845e-164">你可以将映像视为要在“计算机”中安装的辅助只读硬盘，其中操作系统已经安装。</span><span class="sxs-lookup"><span data-stu-id="4845e-164">You can think of an image as an auxiliary read-only hard disk ready to be installed in a "computer" where the operating system is already installed.</span></span>

<span data-ttu-id="4845e-165">同样，你可以将容器视为已安装映像硬盘的“计算机”。</span><span class="sxs-lookup"><span data-stu-id="4845e-165">Similarly, you can think of a container as the "computer" with the image hard disk installed.</span></span> <span data-ttu-id="4845e-166">与计算机一样，可以打开或关闭容器电源。</span><span class="sxs-lookup"><span data-stu-id="4845e-166">The container, just like a computer, can be powered on or off.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4845e-167">[上一页](index.md)
>[下一页](docker-terminology.md)</span><span class="sxs-lookup"><span data-stu-id="4845e-167">[Previous](index.md)
[Next](docker-terminology.md)</span></span>
