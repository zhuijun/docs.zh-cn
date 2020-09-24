---
title: 基础结构即代码
description: 将基础结构用作代码 (IaC) 与云本机应用程序
ms.date: 05/13/2020
ms.openlocfilehash: d130705e19e0d3d7a9e15c73f4758a22ee8ecd43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163734"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="b148a-103">基础结构即代码</span><span class="sxs-lookup"><span data-stu-id="b148a-103">Infrastructure as code</span></span>

<span data-ttu-id="b148a-104">云本机系统采用微服务、容器和新式系统设计来实现速度和灵活性。</span><span class="sxs-lookup"><span data-stu-id="b148a-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="b148a-105">它们提供自动化的生成和发布阶段，以确保代码的一致性和质量。</span><span class="sxs-lookup"><span data-stu-id="b148a-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="b148a-106">但这只是其中的一部分。</span><span class="sxs-lookup"><span data-stu-id="b148a-106">But, that's only part of the story.</span></span> <span data-ttu-id="b148a-107">如何预配这些系统运行时所用的云环境？</span><span class="sxs-lookup"><span data-stu-id="b148a-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="b148a-108">新式云-本机应用程序采用广泛接受的 [基础结构代码](/azure/devops/learn/what-is-infrastructure-as-code)，即，或 `IaC` 。</span><span class="sxs-lookup"><span data-stu-id="b148a-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="b148a-109">借助 IaC，你可以自动完成平台设置。</span><span class="sxs-lookup"><span data-stu-id="b148a-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="b148a-110">实质上是将软件工程实践（例如测试和版本控制）应用于 DevOps 做法。</span><span class="sxs-lookup"><span data-stu-id="b148a-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="b148a-111">你的基础结构和部署是自动、一致且可重复的。</span><span class="sxs-lookup"><span data-stu-id="b148a-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="b148a-112">就像连续交付自动执行传统的手动部署模型一样，基础结构即代码 (IaC 的) 在不断演变应用程序环境的管理方式。</span><span class="sxs-lookup"><span data-stu-id="b148a-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="b148a-113">Azure 资源管理器 (ARM) 、Terraform 和 Azure 命令行接口等工具 (CLI) 使你能够以声明方式对所需的云基础结构编写脚本。</span><span class="sxs-lookup"><span data-stu-id="b148a-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="b148a-114">Azure 资源管理器模板</span><span class="sxs-lookup"><span data-stu-id="b148a-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="b148a-115">ARM 代表 [Azure 资源管理器](/azure/azure-resource-manager/management/overview)。</span><span class="sxs-lookup"><span data-stu-id="b148a-115">ARM stands for [Azure Resource Manager](/azure/azure-resource-manager/management/overview).</span></span> <span data-ttu-id="b148a-116">它是 Azure 中内置的 API 预配引擎，作为 API 服务公开。</span><span class="sxs-lookup"><span data-stu-id="b148a-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="b148a-117">ARM 使你可以通过单个协调的操作来部署、更新、删除和管理 Azure 资源组中包含的资源。</span><span class="sxs-lookup"><span data-stu-id="b148a-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="b148a-118">为引擎提供基于 JSON 的模板，该模板指定所需资源及其配置。</span><span class="sxs-lookup"><span data-stu-id="b148a-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="b148a-119">ARM 会按正确的顺序与依赖关系自动协调部署。</span><span class="sxs-lookup"><span data-stu-id="b148a-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="b148a-120">引擎可确保幂等性。</span><span class="sxs-lookup"><span data-stu-id="b148a-120">The engine ensures idempotency.</span></span> <span data-ttu-id="b148a-121">如果已存在具有相同配置的所需资源，则将忽略设置。</span><span class="sxs-lookup"><span data-stu-id="b148a-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="b148a-122">Azure 资源管理器模板是一种基于 JSON 的语言，用于定义 Azure 中的各种资源。</span><span class="sxs-lookup"><span data-stu-id="b148a-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="b148a-123">基本架构如图10-14 所示。</span><span class="sxs-lookup"><span data-stu-id="b148a-123">The basic schema looks something like Figure 10-14.</span></span>

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

<span data-ttu-id="b148a-124">**图 10-14** -资源管理器模板的架构</span><span class="sxs-lookup"><span data-stu-id="b148a-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="b148a-125">在此模板中，可能会在资源部分中定义一个存储容器，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b148a-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

<span data-ttu-id="b148a-126">**图 10-15** -资源管理器模板中定义的存储帐户的示例</span><span class="sxs-lookup"><span data-stu-id="b148a-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="b148a-127">可以使用动态环境和配置信息对 ARM 模板进行参数化。</span><span class="sxs-lookup"><span data-stu-id="b148a-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="b148a-128">这样一来，就可以重复使用它来定义不同的环境，例如开发、QA 或生产环境。</span><span class="sxs-lookup"><span data-stu-id="b148a-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="b148a-129">通常，模板会在单个 Azure 资源组中创建所有资源。</span><span class="sxs-lookup"><span data-stu-id="b148a-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="b148a-130">如果需要，可以在单个资源管理器模板中定义多个资源组。</span><span class="sxs-lookup"><span data-stu-id="b148a-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="b148a-131">可以通过删除资源组本身来删除环境中的所有资源。</span><span class="sxs-lookup"><span data-stu-id="b148a-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="b148a-132">成本分析还可以在资源组级别运行，从而可以快速评估每个环境的成本。</span><span class="sxs-lookup"><span data-stu-id="b148a-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="b148a-133">GitHub 上的 [Azure 快速入门模板](https://github.com/Azure/azure-quickstart-templates) 项目中提供了许多示例或 ARM 模板。</span><span class="sxs-lookup"><span data-stu-id="b148a-133">There are many examples or ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="b148a-134">它们可以帮助加速创建新模板或修改现有模板。</span><span class="sxs-lookup"><span data-stu-id="b148a-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="b148a-135">可以通过多种方式运行资源管理器模板。</span><span class="sxs-lookup"><span data-stu-id="b148a-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="b148a-136">最简单的方法是将它们粘贴到 Azure 门户中。</span><span class="sxs-lookup"><span data-stu-id="b148a-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="b148a-137">对于实验部署，这种方法很简单。</span><span class="sxs-lookup"><span data-stu-id="b148a-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="b148a-138">它们还可以作为 Azure DevOps 中的生成或发布过程的一部分运行。</span><span class="sxs-lookup"><span data-stu-id="b148a-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="b148a-139">有一些任务将利用连接到 Azure 运行模板。</span><span class="sxs-lookup"><span data-stu-id="b148a-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="b148a-140">对资源管理器模板的更改以增量方式应用，这意味着，若要添加新资源，只需将其添加到模板。</span><span class="sxs-lookup"><span data-stu-id="b148a-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="b148a-141">工具将协调当前资源与模板中定义的差异之间的差异。</span><span class="sxs-lookup"><span data-stu-id="b148a-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="b148a-142">然后，将创建或更改资源，使其与模板中定义的内容相匹配。</span><span class="sxs-lookup"><span data-stu-id="b148a-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="b148a-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="b148a-143">Terraform</span></span>

<span data-ttu-id="b148a-144">通常将云本机应用程序构建为 `cloud agnostic` 。</span><span class="sxs-lookup"><span data-stu-id="b148a-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="b148a-145">因此，应用程序并不与特定的云供应商紧密耦合，可以部署到任何公有云。</span><span class="sxs-lookup"><span data-stu-id="b148a-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="b148a-146">[Terraform](https://www.terraform.io/) 是可在所有主要云扮演者之间预配云本机应用程序的商业模板工具： Azure、GOOGLE CLOUD PLATFORM、AWS 和 AliCloud。</span><span class="sxs-lookup"><span data-stu-id="b148a-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="b148a-147">它使用的简要 YAML 略有不同，而不是使用 JSON 作为模板定义语言。</span><span class="sxs-lookup"><span data-stu-id="b148a-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="b148a-148">图10-16 中显示了一个示例 Terraform 文件，该文件与先前资源管理器模板 (图 10-15) 所示：</span><span class="sxs-lookup"><span data-stu-id="b148a-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

<span data-ttu-id="b148a-149">**图 10-16** -资源管理器模板的示例</span><span class="sxs-lookup"><span data-stu-id="b148a-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="b148a-150">Terraform 还为问题模板提供直观的错误消息。</span><span class="sxs-lookup"><span data-stu-id="b148a-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="b148a-151">还有一个便于验证的任务，该任务可在生成阶段用于提前捕获模板错误。</span><span class="sxs-lookup"><span data-stu-id="b148a-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="b148a-152">与资源管理器模板一样，可以使用命令行工具来部署 Terraform 模板。</span><span class="sxs-lookup"><span data-stu-id="b148a-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="b148a-153">Azure Pipelines 中还提供了社区创建的任务，可以验证和应用 Terraform 模板。</span><span class="sxs-lookup"><span data-stu-id="b148a-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="b148a-154">有时，Terraform 和 ARM 模板会输出有意义的值，例如新创建的数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="b148a-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="b148a-155">此信息可以在生成管道中捕获并在后续任务中使用。</span><span class="sxs-lookup"><span data-stu-id="b148a-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="b148a-156">Azure CLI 脚本和任务</span><span class="sxs-lookup"><span data-stu-id="b148a-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="b148a-157">最后，你可以利用 [Azure CLI](/cli/azure/) 以声明方式为你的云基础结构编写脚本。</span><span class="sxs-lookup"><span data-stu-id="b148a-157">Finally, you can leverage [Azure CLI](/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="b148a-158">可以创建、找到并共享 Azure CLI 脚本来预配和配置几乎任何 Azure 资源。</span><span class="sxs-lookup"><span data-stu-id="b148a-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="b148a-159">CLI 易于在学习曲线上使用。</span><span class="sxs-lookup"><span data-stu-id="b148a-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="b148a-160">脚本在 PowerShell 或 Bash 内执行。</span><span class="sxs-lookup"><span data-stu-id="b148a-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="b148a-161">它们也很简单地进行调试，尤其是在与 ARM 模板比较时。</span><span class="sxs-lookup"><span data-stu-id="b148a-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="b148a-162">当你需要关闭和重新部署基础结构时，Azure CLI 脚本非常有效。</span><span class="sxs-lookup"><span data-stu-id="b148a-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="b148a-163">更新现有环境可能比较棘手。</span><span class="sxs-lookup"><span data-stu-id="b148a-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="b148a-164">许多 CLI 命令不是幂等的。</span><span class="sxs-lookup"><span data-stu-id="b148a-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="b148a-165">这意味着，它们将在每次运行时重新创建资源，即使资源已存在也是如此。</span><span class="sxs-lookup"><span data-stu-id="b148a-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="b148a-166">始终可以添加代码，以便在创建资源前检查是否存在每个资源。</span><span class="sxs-lookup"><span data-stu-id="b148a-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="b148a-167">但这样做会使您的脚本变得臃肿且难以管理。</span><span class="sxs-lookup"><span data-stu-id="b148a-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="b148a-168">这些脚本也可以嵌入在 Azure DevOps 管道中 `Azure CLI tasks` 。</span><span class="sxs-lookup"><span data-stu-id="b148a-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="b148a-169">执行管道将调用脚本。</span><span class="sxs-lookup"><span data-stu-id="b148a-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="b148a-170">图10-17 显示了一个 YAML 代码段，其中列出了 Azure CLI 的版本和订阅的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b148a-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="b148a-171">请注意内联脚本中包含 Azure CLI 命令的方式。</span><span class="sxs-lookup"><span data-stu-id="b148a-171">Note how Azure CLI commands are included in an inline script.</span></span>

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

<span data-ttu-id="b148a-172">**图 10-17** -Azure CLI 脚本</span><span class="sxs-lookup"><span data-stu-id="b148a-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="b148a-173">在本文中， [什么是基础结构即代码](/azure/devops/learn/what-is-infrastructure-as-code)，Author Sam Guckenheimer 介绍了 "实现 IaC 的团队如何快速、大规模地交付稳定环境。</span><span class="sxs-lookup"><span data-stu-id="b148a-173">In the article, [What is Infrastructure as Code](/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="b148a-174">团队避免手动配置环境，并通过代码来表示环境所需的状态，从而强制实现一致性。</span><span class="sxs-lookup"><span data-stu-id="b148a-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="b148a-175">使用 IaC 的基础结构部署是可重复的，并防止配置偏移或缺少依赖项导致的运行时问题。</span><span class="sxs-lookup"><span data-stu-id="b148a-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="b148a-176">DevOps 团队可以结合使用一组统一的做法和工具，迅速、可靠、大规模地提供应用程序及其支持基础结构。</span><span class="sxs-lookup"><span data-stu-id="b148a-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b148a-177">[上一页](feature-flags.md)
>[下一页](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="b148a-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
