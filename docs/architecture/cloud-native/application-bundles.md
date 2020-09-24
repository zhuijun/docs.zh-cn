---
title: 云本机应用程序捆绑包
description: 构建适用于 Azure 的云本机 .NET 应用 |云本机应用程序捆绑包
ms.date: 05/13/2020
ms.openlocfilehash: 7f1fcd448f3299a31043bf269717f7b777329c62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158118"
---
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="76054-103">云本机应用程序捆绑包</span><span class="sxs-lookup"><span data-stu-id="76054-103">Cloud Native Application Bundles</span></span>

<span data-ttu-id="76054-104">云本机应用程序的一个关键属性是，它们利用云的功能加快开发速度。</span><span class="sxs-lookup"><span data-stu-id="76054-104">A key property of cloud-native applications is that they leverage the capabilities of the cloud to speed up development.</span></span> <span data-ttu-id="76054-105">此设计通常意味着完整应用程序使用不同种类的技术。</span><span class="sxs-lookup"><span data-stu-id="76054-105">This design often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="76054-106">应用程序可以在 Docker 容器中提供，某些服务可能使用 Azure Functions，而其他部分则可能会直接在具有硬件 GPU 加速功能的大型金属服务器上运行的虚拟机上运行。</span><span class="sxs-lookup"><span data-stu-id="76054-106">Applications may be shipped in Docker containers, some services may use Azure Functions, while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="76054-107">没有两个云本机应用程序是相同的，因此很难提供单一机制来传送它们。</span><span class="sxs-lookup"><span data-stu-id="76054-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="76054-108">Docker 容器可以在 Kubernetes 上使用 Helm 图表进行部署。</span><span class="sxs-lookup"><span data-stu-id="76054-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="76054-109">可以使用 Terraform 模板分配 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="76054-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="76054-110">最后，可以使用 Terraform 分配虚拟机，但使用 Ansible 构建虚拟机。</span><span class="sxs-lookup"><span data-stu-id="76054-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="76054-111">这是一种全面的技术，没有办法将它们一起打包到合理的包中。</span><span class="sxs-lookup"><span data-stu-id="76054-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="76054-112">到现在为止。</span><span class="sxs-lookup"><span data-stu-id="76054-112">Until now.</span></span>

<span data-ttu-id="76054-113">云本机应用程序捆绑 (CNABs) 通过许多相投公司（如 Microsoft、Docker 和 HashiCorp）进行联合工作，以开发用于打包分布式应用程序的规范。</span><span class="sxs-lookup"><span data-stu-id="76054-113">Cloud Native Application Bundles (CNABs) are a joint effort by a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="76054-114">这项工作已于2018年12月公布，因此，为了向更大的社区公开工作，仍有一些工作要做。</span><span class="sxs-lookup"><span data-stu-id="76054-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="76054-115">不过，已经有一个 [开放规范](https://github.com/deislabs/cnab-spec) 和一个称为 [Duffle](https://duffle.sh/)的引用实现。</span><span class="sxs-lookup"><span data-stu-id="76054-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="76054-116">此工具是在中转和 Microsoft 之间的共同努力。</span><span class="sxs-lookup"><span data-stu-id="76054-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="76054-117">CNABs 可以包含不同种类的安装技术。</span><span class="sxs-lookup"><span data-stu-id="76054-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="76054-118">这就允许 Helm 图、Terraform 模板和 Ansible 行动手册共存于同一包中。</span><span class="sxs-lookup"><span data-stu-id="76054-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="76054-119">构建后，这些包将是独立的，并且是可移植的;可以通过 USB 驾驶杆进行安装。</span><span class="sxs-lookup"><span data-stu-id="76054-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="76054-120">对包进行加密签名，以确保它们来自声明的参与方。</span><span class="sxs-lookup"><span data-stu-id="76054-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="76054-121">CNAB 的核心是一个名为的文件 `bundle.json` 。</span><span class="sxs-lookup"><span data-stu-id="76054-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="76054-122">此文件定义绑定的内容，这些内容为 Terraform 或 images 或其他任何内容。</span><span class="sxs-lookup"><span data-stu-id="76054-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="76054-123">图11-9 定义调用某些 Terraform 的 CNAB。</span><span class="sxs-lookup"><span data-stu-id="76054-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="76054-124">但请注意，它实际上定义了用于调用 Terraform 的调用映像。</span><span class="sxs-lookup"><span data-stu-id="76054-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="76054-125">打包时，位于 *cnab* 目录中的 docker 文件内置于 docker 映像中，该映像将包含在包中。</span><span class="sxs-lookup"><span data-stu-id="76054-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="76054-126">将 Terraform 安装在捆绑中的 Docker 容器内意味着用户无需在其计算机上安装 Terraform 即可运行绑定。</span><span class="sxs-lookup"><span data-stu-id="76054-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

<span data-ttu-id="76054-127">**图 10-18** -示例 Terraform 文件</span><span class="sxs-lookup"><span data-stu-id="76054-127">**Figure 10-18** - An example Terraform file</span></span>

<span data-ttu-id="76054-128">`bundle.json`还定义了一组可向下传递到 Terraform 的参数。</span><span class="sxs-lookup"><span data-stu-id="76054-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="76054-129">捆绑的参数化允许在各种不同的环境中进行安装。</span><span class="sxs-lookup"><span data-stu-id="76054-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="76054-130">CNAB 格式也是灵活的，使其可用于任何云。</span><span class="sxs-lookup"><span data-stu-id="76054-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="76054-131">甚至可以针对本地解决方案（例如 [OpenStack](https://www.openstack.org/)）使用它。</span><span class="sxs-lookup"><span data-stu-id="76054-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="76054-132">DevOps 决策</span><span class="sxs-lookup"><span data-stu-id="76054-132">DevOps Decisions</span></span>

<span data-ttu-id="76054-133">在 DevOps 空间中，有很多有用的工具，这些工具还提供了有关如何成功的更好的书籍和文章。</span><span class="sxs-lookup"><span data-stu-id="76054-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="76054-134">DevOps 旅程入门的最喜爱的书籍是 [Phoenix 项目](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/)，该项目遵循从 Noop 到 DevOps 的虚构公司的转换。</span><span class="sxs-lookup"><span data-stu-id="76054-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="76054-135">特别是在部署复杂的云本机应用程序时，DevOps 不再是 "更好的"。</span><span class="sxs-lookup"><span data-stu-id="76054-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="76054-136">这是一种要求，在任何项目开始时，应计划并为其分配资源。</span><span class="sxs-lookup"><span data-stu-id="76054-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

## <a name="references"></a><span data-ttu-id="76054-137">参考</span><span class="sxs-lookup"><span data-stu-id="76054-137">References</span></span>

- [<span data-ttu-id="76054-138">Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="76054-138">Azure DevOps</span></span>](https://azure.microsoft.com/services/devops/)
- [<span data-ttu-id="76054-139">Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="76054-139">Azure Resource Manager</span></span>](/azure/azure-resource-manager/management/overview)
- [<span data-ttu-id="76054-140">Terraform</span><span class="sxs-lookup"><span data-stu-id="76054-140">Terraform</span></span>](https://www.terraform.io/)
- [<span data-ttu-id="76054-141">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="76054-141">Azure CLI</span></span>](/cli/azure/)

>[!div class="step-by-step"]
><span data-ttu-id="76054-142">[上一页](infrastructure-as-code.md)
>[下一页](summary.md)</span><span class="sxs-lookup"><span data-stu-id="76054-142">[Previous](infrastructure-as-code.md)
[Next](summary.md)</span></span>
