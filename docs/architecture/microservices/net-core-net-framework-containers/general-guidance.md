---
title: 通用指南
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 通用指南
ms.date: 09/11/2018
ms.openlocfilehash: e3bb4b8cf3e371c31d783fe4cfafeac282fb72b8
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144560"
---
# <a name="general-guidance"></a><span data-ttu-id="23b25-103">通用指南</span><span class="sxs-lookup"><span data-stu-id="23b25-103">General guidance</span></span>

<span data-ttu-id="23b25-104">本部分提供有关何时选择 .NET Core 或 .NET Framework 的总结。</span><span class="sxs-lookup"><span data-stu-id="23b25-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="23b25-105">后面各部分将提供对上述选择的详细介绍。</span><span class="sxs-lookup"><span data-stu-id="23b25-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="23b25-106">将 .NET Core 与 Linux 或 Windows 容器结合使用并用于容器化 Docker 服务器应用程序的适用情况：</span><span class="sxs-lookup"><span data-stu-id="23b25-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="23b25-107">用户有跨平台需求。</span><span class="sxs-lookup"><span data-stu-id="23b25-107">You have cross-platform needs.</span></span> <span data-ttu-id="23b25-108">例如，想同时使用 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="23b25-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="23b25-109">应用程序体系结构基于微服务。</span><span class="sxs-lookup"><span data-stu-id="23b25-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="23b25-110">需快速启动容器且每个容器内存占用较小，以实现更好的密度，或每个硬件单位中的容器较多，以降低成本。</span><span class="sxs-lookup"><span data-stu-id="23b25-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="23b25-111">简单地说，在创建新的容器化 .NET 应用程序时，应考虑将 .NET Core 作为默认选择。</span><span class="sxs-lookup"><span data-stu-id="23b25-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="23b25-112">它具有许多好处，并最匹配容器的基本原理和运行方式。</span><span class="sxs-lookup"><span data-stu-id="23b25-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="23b25-113">使用 .NET Core 的另一个好处是可在同一台计算机中并行运行 .NET 版本的应用程序。</span><span class="sxs-lookup"><span data-stu-id="23b25-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="23b25-114">这一优势对于不使用容器的服务器或虚拟机而言更为重要，因为容器会隔离应用所需的 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="23b25-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="23b25-115">（只要它们与基础操作系统兼容。）</span><span class="sxs-lookup"><span data-stu-id="23b25-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="23b25-116">在以下情况下，应将 .NET Framework 用于容器化 Docker 服务器应用程序：</span><span class="sxs-lookup"><span data-stu-id="23b25-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="23b25-117">应用程序当前使用 .NET Framework 并在 Windows 上具有强依赖关系。</span><span class="sxs-lookup"><span data-stu-id="23b25-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="23b25-118">需要使用 .NET Core 不支持的 Windows API。</span><span class="sxs-lookup"><span data-stu-id="23b25-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="23b25-119">用户需要使用不可用于 .NET Core 的第三方 .NET 库或 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="23b25-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="23b25-120">在 Docker 上使用.NET Framework 可通过最大限度地减少部署问题来提升部署体验。</span><span class="sxs-lookup"><span data-stu-id="23b25-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="23b25-121">此[“提升和移动”方案](https://aka.ms/liftandshiftwithcontainersebook)对于针对最初使用传统 .NET Framework（如 ASP.NET WebForms、MVC Web 应用或 WCF (Windows Communication Foundation) 服务）开发的旧应用程序实施容器化而言很重要。</span><span class="sxs-lookup"><span data-stu-id="23b25-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="23b25-122">其他资源</span><span class="sxs-lookup"><span data-stu-id="23b25-122">Additional resources</span></span>

- <span data-ttu-id="23b25-123">电子书：**Modernize existing .NET Framework applications with Azure and Windows Containers**（使用 Azure 和 Windows 容器更新现有 .NET Framework 应用程序）</span><span class="sxs-lookup"><span data-stu-id="23b25-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    <https://aka.ms/liftandshiftwithcontainersebook>

- <span data-ttu-id="23b25-124">**示例应用：Modernization of legacy ASP.NET web apps by using Windows Containers**（使用 Windows 容器更新旧的 ASP.NET Web 应用）</span><span class="sxs-lookup"><span data-stu-id="23b25-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
><span data-ttu-id="23b25-125">[上一页](index.md)
>[下一页](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="23b25-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
