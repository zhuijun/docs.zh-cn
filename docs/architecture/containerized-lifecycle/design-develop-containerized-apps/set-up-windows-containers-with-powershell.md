---
title: 使用 DockerFile 中的 Windows PowerShell 命令来设置 Windows 容器（基于 Docker 标准）
description: 了解在 Windows 容器中使用 Docker 时如何使用 PowerShell
ms.date: 08/06/2020
ms.openlocfilehash: be30fd4092f51acd4972c05b3c3ccc936aebd884
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539783"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="a0cb1-103">使用 DockerFile 中的 Windows PowerShell 命令来设置 Windows 容器（基于 Docker 标准）</span><span class="sxs-lookup"><span data-stu-id="a0cb1-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="a0cb1-104">使用 [Windows 容器](/virtualization/windowscontainers/about/index)可将现有 Windows 应用程序转换为 Docker 映像，并使用与 Docker 生态系统其余部分相同的工具进行部署。</span><span class="sxs-lookup"><span data-stu-id="a0cb1-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="a0cb1-105">要使用 Windows 容器，只需在 DockerFile 中编写 Windows PowerShell 命令，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a0cb1-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="a0cb1-106">在此示例中，我们将使用 Windows PowerShell 来安装 Windows Server Core 基础映像以及 IIS。</span><span class="sxs-lookup"><span data-stu-id="a0cb1-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="a0cb1-107">同样，也可使用 Windows PowerShell 命令来设置其他组件，如传统的 ASP.NET 4.x、.NET 4.6 或任何其他 Windows 软件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0cb1-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="a0cb1-108">[上一页](visual-studio-tools-for-docker.md)
>[下一页](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="a0cb1-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
