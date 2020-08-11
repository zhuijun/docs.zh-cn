---
title: 容器和 Docker 简介
description: 简要了解使用 Docker 所带来的主要优势。
ms.date: 04/15/2020
ms.openlocfilehash: 79b4752ef4d2f0aa6199414aea5cf4ef357c86d3
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915921"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="f4028-103">容器和 Docker 简介</span><span class="sxs-lookup"><span data-stu-id="f4028-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="f4028-104">*容器化是软件开发的一种方法，通过它可将应用程序或服务、其依赖项及其配置（抽象化为部署清单文件）一起打包为容器映像。然后，可将容器化应用程序作为单元进行测试，并将其作为容器映像实例部署到主机操作系统 (OS)。*</span><span class="sxs-lookup"><span data-stu-id="f4028-104">*Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image. You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system (OS).*</span></span>

<span data-ttu-id="f4028-105">就像船只、火车或卡车运输集装箱而不论其内部的货物一样，软件容器充当软件部署的标准单元，其中可以包含不同的代码和依赖项。</span><span class="sxs-lookup"><span data-stu-id="f4028-105">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software deployment that can contain different code and dependencies.</span></span> <span data-ttu-id="f4028-106">按照这种方式容器化软件，开发人员和 IT 专业人员只需进行极少修改或不修改，即可将其部署到不同的环境。</span><span class="sxs-lookup"><span data-stu-id="f4028-106">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="f4028-107">容器还会在共享 OS 上将应用程序彼此隔离开。</span><span class="sxs-lookup"><span data-stu-id="f4028-107">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="f4028-108">容器化应用程序在容器主机上运行，而容器主机在 OS（Linux 或 Windows）上运行。</span><span class="sxs-lookup"><span data-stu-id="f4028-108">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="f4028-109">因此，容器的占用比虚拟机 (VM) 映像小得多。</span><span class="sxs-lookup"><span data-stu-id="f4028-109">Containers therefore have a much smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="f4028-110">每个容器都可运行整个 Web 应用或服务，如图 1-1 所示。</span><span class="sxs-lookup"><span data-stu-id="f4028-110">Each container can run a whole web application or a service, as shown in Figure 1-1.</span></span> <span data-ttu-id="f4028-111">在本例中，Docker 主机是容器主机，App1、App2、Svc1 和 Svc2 是容器化的应用程序或服务。</span><span class="sxs-lookup"><span data-stu-id="f4028-111">In this example, Docker host is a container host, and App1, App2, Svc1, and Svc2 are containerized applications or services.</span></span>

![显示 VM 或服务器中运行的四个容器的关系图。](./media/introduction-to-containers-and-docker/multiple-containers-single-host.png)

<span data-ttu-id="f4028-113">**图 1-1**。</span><span class="sxs-lookup"><span data-stu-id="f4028-113">**Figure 1-1**.</span></span> <span data-ttu-id="f4028-114">在一个容器主机上运行多个容器</span><span class="sxs-lookup"><span data-stu-id="f4028-114">Multiple containers running on a container host</span></span>

<span data-ttu-id="f4028-115">可从容器化获得的另一个优势是可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="f4028-115">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="f4028-116">通过为短期任务创建新容器，可以快速扩大。</span><span class="sxs-lookup"><span data-stu-id="f4028-116">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="f4028-117">从应用程序的角度来看，实例化映像（创建容器）类似于实例化 服务或 Web 应用等进程。</span><span class="sxs-lookup"><span data-stu-id="f4028-117">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="f4028-118">但出于可靠性考虑，在多个主机服务器上运行同一映像的多个实例时，通常要使每个容器（映像实例）在不同容错域中的不同主机服务器或 VM 中运行。</span><span class="sxs-lookup"><span data-stu-id="f4028-118">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="f4028-119">总而言之，容器在整个应用程序生命周期工作流中提供了隔离性、可移植性、灵活性、可伸缩性和可控性等诸多优点。</span><span class="sxs-lookup"><span data-stu-id="f4028-119">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application lifecycle workflow.</span></span> <span data-ttu-id="f4028-120">最重要的优点是可在开发和运营之间实现环境隔离。</span><span class="sxs-lookup"><span data-stu-id="f4028-120">The most important benefit is the environment isolation provided between Dev and Ops.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f4028-121">[上一页](index.md)
>[下一页](what-is-docker.md)</span><span class="sxs-lookup"><span data-stu-id="f4028-121">[Previous](index.md)
[Next](what-is-docker.md)</span></span>
