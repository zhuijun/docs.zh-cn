---
title: 防火墙说明
description: 了解如何在防火墙中为 WCF 示例启用端口或程序。 根据你的要求和安全环境使用这些过程之一。
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: de55d067960b8f2096c129f6feaf037219e06a96
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246136"
---
# <a name="firewall-instructions"></a><span data-ttu-id="1953d-104">防火墙说明</span><span class="sxs-lookup"><span data-stu-id="1953d-104">Firewall instructions</span></span>

<span data-ttu-id="1953d-105">你必须在防火墙中启用多个端口或程序，以便 Windows Communication Foundation （WCF）示例可以正常工作。</span><span class="sxs-lookup"><span data-stu-id="1953d-105">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="1953d-106">其中许多示例使用范围 8000-8003 中的端口和端口 9000 进行通信。</span><span class="sxs-lookup"><span data-stu-id="1953d-106">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="1953d-107">防火墙默认情况下会打开，阻止对这些端口进行访问。</span><span class="sxs-lookup"><span data-stu-id="1953d-107">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="1953d-108">若要针对这些示例启用防火墙，请完成以下过程之一，具体情况取决于您的需求和安全环境：</span><span class="sxs-lookup"><span data-stu-id="1953d-108">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>

- <span data-ttu-id="1953d-109">选项 1：在运行时以交互方式启用示例。</span><span class="sxs-lookup"><span data-stu-id="1953d-109">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="1953d-110">不预先更改防火墙配置，并继续开始生成和运行示例的过程。</span><span class="sxs-lookup"><span data-stu-id="1953d-110">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="1953d-111">运行示例时，将显示 " **Windows 安全警报**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="1953d-111">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="1953d-112">然后，可以通过交互方式将所讨论的示例程序添加到取消阻止列表。</span><span class="sxs-lookup"><span data-stu-id="1953d-112">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="1953d-113">对于此过程，您可能必须随后重新启动示例。</span><span class="sxs-lookup"><span data-stu-id="1953d-113">With this procedure, you may have to then restart the sample.</span></span>

- <span data-ttu-id="1953d-114">选项 2：预先启用示例程序。</span><span class="sxs-lookup"><span data-stu-id="1953d-114">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="1953d-115">启动**Windows 防火墙控制面板**小程序，并启用计划运行的示例程序。</span><span class="sxs-lookup"><span data-stu-id="1953d-115">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="1953d-116">您必须首先生成这些程序，以生成它们的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="1953d-116">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="1953d-117">可以在以下过程中找到更详细的说明。</span><span class="sxs-lookup"><span data-stu-id="1953d-117">You can find more detailed instructions in the following procedure.</span></span>

- <span data-ttu-id="1953d-118">选项 3：预先启用端口范围。</span><span class="sxs-lookup"><span data-stu-id="1953d-118">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="1953d-119">启动**Windows 防火墙控制面板**小程序，并启用示例使用的端口80、443、8000-8003 和9000。</span><span class="sxs-lookup"><span data-stu-id="1953d-119">Start the **Windows Firewall Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="1953d-120">可以在以下过程中找到更详细的说明。</span><span class="sxs-lookup"><span data-stu-id="1953d-120">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="1953d-121">相对于其他选项而言，此选项的安全性较差，因为它允许任何程序（而不仅仅是示例）使用这些端口。</span><span class="sxs-lookup"><span data-stu-id="1953d-121">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>

<span data-ttu-id="1953d-122">如果不确定要使用哪个过程，请选择第一个选项。</span><span class="sxs-lookup"><span data-stu-id="1953d-122">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="1953d-123">如果运行其他供应商提供的防火墙，您可能需要进行类似的更改。</span><span class="sxs-lookup"><span data-stu-id="1953d-123">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1953d-124">更改防火墙配置会对安全产生影响。</span><span class="sxs-lookup"><span data-stu-id="1953d-124">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="1953d-125">建议您记录所做的更改，并在使用完示例后移除这些更改。</span><span class="sxs-lookup"><span data-stu-id="1953d-125">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>

## <a name="enable-samples-programs-in-advance"></a><span data-ttu-id="1953d-126">预先启用示例程序</span><span class="sxs-lookup"><span data-stu-id="1953d-126">Enable samples programs in advance</span></span>

1. <span data-ttu-id="1953d-127">生成示例。</span><span class="sxs-lookup"><span data-stu-id="1953d-127">Build the sample.</span></span>

2. <span data-ttu-id="1953d-128">选择 "**启动**  >  **运行**"，然后输入 `firewall.cpl` 。</span><span class="sxs-lookup"><span data-stu-id="1953d-128">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="1953d-129">这将打开 " **Windows 防火墙控制面板**" 小程序。</span><span class="sxs-lookup"><span data-stu-id="1953d-129">This opens the **Windows Firewall Control Panel** applet.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1953d-130">必须具有更改防火墙设置的权限，才能运行需要能够通过 Windows 防火墙进行通信的示例。</span><span class="sxs-lookup"><span data-stu-id="1953d-130">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="1953d-131">如果某些防火墙设置不可用，并且您的计算机连接到域，则系统管理员可以通过组策略控制这些设置。</span><span class="sxs-lookup"><span data-stu-id="1953d-131">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>

3. <span data-ttu-id="1953d-132">完成以下特定于操作的步骤之一，允许程序通过 Windows 防火墙：</span><span class="sxs-lookup"><span data-stu-id="1953d-132">Complete one of the following operating-specific steps to allow a program through the Windows Firewall:</span></span>

    - <span data-ttu-id="1953d-133">在 Windows 7 或 Windows Server 2008 R2 上，单击 "**允许程序或功能通过 Windows 防火墙**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-133">On Windows 7 or Windows Server 2008 R2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="1953d-134">单击 "**更改设置**" "  >  **允许其他程序**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-134">Click **Change Settings** > **Allow Another Program**.</span></span>

    - <span data-ttu-id="1953d-135">在 Windows Vista 或 Windows Server 2008 上，单击 "**允许程序通过 Windows 防火墙**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-135">On Windows Vista or Windows Server 2008, click **Allow a program through Windows Firewall**.</span></span>

4. <span data-ttu-id="1953d-136">在 "**例外**" 选项卡上，单击 "**添加程序**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-136">On the **Exceptions** tab, click **Add Program**.</span></span>

5. <span data-ttu-id="1953d-137">单击 "**浏览**" 按钮，然后选择你计划运行的示例的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="1953d-137">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>

6. <span data-ttu-id="1953d-138">重复步骤4和步骤5，直到您添加了您计划运行的所有示例的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="1953d-138">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>

7. <span data-ttu-id="1953d-139">单击 **"确定"** 以关闭防火墙小程序。</span><span class="sxs-lookup"><span data-stu-id="1953d-139">Click **OK** to close the firewall applet.</span></span>

## <a name="enable-a-port-range-in-advance"></a><span data-ttu-id="1953d-140">预先启用端口范围</span><span class="sxs-lookup"><span data-stu-id="1953d-140">Enable a port range in advance</span></span>

1. <span data-ttu-id="1953d-141">选择 "**启动**  >  **运行**"，然后输入 `firewall.cpl` 。</span><span class="sxs-lookup"><span data-stu-id="1953d-141">Choose **Start** > **Run**, and enter `firewall.cpl`.</span></span> <span data-ttu-id="1953d-142">这将打开 " **Windows 防火墙控制面板**" 小程序。</span><span class="sxs-lookup"><span data-stu-id="1953d-142">This opens the **Windows Firewall Control Panel** applet.</span></span>

2. <span data-ttu-id="1953d-143">在 Windows 7 或 Windows Server 2008 R2 上，按以下步骤操作。</span><span class="sxs-lookup"><span data-stu-id="1953d-143">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>

    1. <span data-ttu-id="1953d-144">单击 "Windows 防火墙" 窗口左栏中的 "**高级设置**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-144">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>

    2. <span data-ttu-id="1953d-145">单击左栏中的 "**入站规则**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-145">Click **Inbound Rules** in the left column.</span></span>

    3. <span data-ttu-id="1953d-146">单击右侧列中的 "**新建规则**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-146">Click **New Rules** in the right column.</span></span>

    4. <span data-ttu-id="1953d-147">选择**端口**，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-147">Select **Port** and click **next**.</span></span>

    5. <span data-ttu-id="1953d-148">选择 " **TCP** "，然后 `8000, 8001, 8002, 8003, 9000, 80, 443` 在 "**特定本地端口**" 字段中输入。</span><span class="sxs-lookup"><span data-stu-id="1953d-148">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>

    6. <span data-ttu-id="1953d-149">单击“下一步”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1953d-149">Click **Next**.</span></span>

    7. <span data-ttu-id="1953d-150">选择 **"允许连接**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-150">Select **Allow the connection**, and click **Next** .</span></span>

    8. <span data-ttu-id="1953d-151">选择 "**域**和**专用**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-151">Select **Domain** and **Private**, and click **Next**.</span></span>

    9. <span data-ttu-id="1953d-152">为此规则命名 `WCF-WF 4.0 Samples` ，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-152">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>

    10. <span data-ttu-id="1953d-153">单击 "**出站规则**"，然后重复步骤 c 到 h。</span><span class="sxs-lookup"><span data-stu-id="1953d-153">Click **Outbound Rules** and repeat steps c to h.</span></span>

3. <span data-ttu-id="1953d-154">在 Windows Vista 或 Windows Server 2008 上，请执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="1953d-154">On Windows Vista or Windows Server 2008, follow these steps.</span></span>

    1. <span data-ttu-id="1953d-155">单击“允许程序通过 Windows 防火墙”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1953d-155">Click **Allow a program through Windows Firewall**.</span></span>

    2. <span data-ttu-id="1953d-156">在 "**例外**" 选项卡上，单击 "**添加端口**"。</span><span class="sxs-lookup"><span data-stu-id="1953d-156">On the **Exceptions** tab, click **Add Port**.</span></span>

    3. <span data-ttu-id="1953d-157">输入名称，输入8000作为端口号，然后选择 " **TCP** " 选项。</span><span class="sxs-lookup"><span data-stu-id="1953d-157">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>

    4. <span data-ttu-id="1953d-158">单击 "**更改作用域**" 按钮，选择 "仅**我的网络**（子网）" 选项，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="1953d-158">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>

    5. <span data-ttu-id="1953d-159">为端口 8001、8002、8003、9000、80 和 443 重复步骤 b 到 d。</span><span class="sxs-lookup"><span data-stu-id="1953d-159">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>

4. <span data-ttu-id="1953d-160">单击 **"确定"** 以关闭防火墙小程序。</span><span class="sxs-lookup"><span data-stu-id="1953d-160">Click **OK** to close the firewall applet.</span></span>

> [!NOTE]
> <span data-ttu-id="1953d-161">使用完示例后，请移除任何防火墙例外。</span><span class="sxs-lookup"><span data-stu-id="1953d-161">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="1953d-162">为此，请打开**Windows 防火墙控制面板**小程序，并删除前面的过程添加的任何程序或端口项。</span><span class="sxs-lookup"><span data-stu-id="1953d-162">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
