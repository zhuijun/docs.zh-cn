---
title: Visual Studio 开发人员命令提示
description: 了解如何使用 Visual Studio 的开发人员命令提示。开发人员命令提示使你可以更轻松地使用 .NET 工具。 它将自动设置特定的环境变量。
ms.date: 01/05/2020
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
ms.openlocfilehash: 92416820f47cb778dfcc916b8626df4aa328814c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167172"
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="6916b-104">Visual Studio 开发人员命令提示</span><span class="sxs-lookup"><span data-stu-id="6916b-104">Developer Command Prompt for Visual Studio</span></span>

<span data-ttu-id="6916b-105">Visual Studio 的开发人员命令提示使你可以更轻松地使用 .NET Framework 工具。</span><span class="sxs-lookup"><span data-stu-id="6916b-105">Developer Command Prompt for Visual Studio enables you to use .NET Framework tools more easily.</span></span> <span data-ttu-id="6916b-106">它是一个自动设置特定环境变量的命令提示符。</span><span class="sxs-lookup"><span data-stu-id="6916b-106">It's a command prompt that automatically sets specific environment variables.</span></span> <span data-ttu-id="6916b-107">打开开发人员命令提示后，可以为 [.NET Framework](index.md) 工具（如 `ildasm` 或 `clrver`）输入命令。</span><span class="sxs-lookup"><span data-stu-id="6916b-107">After opening Developer Command Prompt, you can enter the commands for [.NET Framework tools](index.md) such as `ildasm` or `clrver`.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6916b-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="6916b-108">Prerequisites</span></span>

- [<span data-ttu-id="6916b-109">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="6916b-109">Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

## <a name="search-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="6916b-110">在计算机中搜索命令提示符</span><span class="sxs-lookup"><span data-stu-id="6916b-110">Search for the command prompt on your machine</span></span>

<span data-ttu-id="6916b-111">你可能会有多个命令提示符，具体取决于你安装的 Visual Studio 的版本及其他任何 SDK 和工作负载。</span><span class="sxs-lookup"><span data-stu-id="6916b-111">You may have multiple command prompts, depending on the version of Visual Studio and any additional SDKs and workloads you've installed.</span></span> <span data-ttu-id="6916b-112">如果以下步骤不起作用，可以尝试[在计算机中手动查找文件](#manually-locate-the-files-on-your-machine)或[从 Visual Studio 内部启动命令提示符](#start-the-command-prompt-from-inside-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="6916b-112">If the following steps don't work, you can try to [manually locate the files on your machine](#manually-locate-the-files-on-your-machine) or [start the command prompt from inside Visual Studio](#start-the-command-prompt-from-inside-visual-studio).</span></span>

### <a name="windows-10"></a><span data-ttu-id="6916b-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="6916b-113">Windows 10</span></span>

1. <span data-ttu-id="6916b-114">选择“开始”![键盘上的 Windows 徽标键。](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span><span class="sxs-lookup"><span data-stu-id="6916b-114">Select **Start** ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="6916b-115">并滚动到字母“V”。</span><span class="sxs-lookup"><span data-stu-id="6916b-115">and scroll to the letter **V**.</span></span>

1. <span data-ttu-id="6916b-116">展开“Visual Studio 2019”文件夹。</span><span class="sxs-lookup"><span data-stu-id="6916b-116">Expand the **Visual Studio 2019** folder.</span></span>

1. <span data-ttu-id="6916b-117">选择“VS 2019 开发人员命令提示”（或者你想使用的命令提示符）。</span><span class="sxs-lookup"><span data-stu-id="6916b-117">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

   <span data-ttu-id="6916b-118">或者，你可以首先在任务栏的搜索框中键入命令提示符的名称，然后在结果列表开始显示搜索匹配项时选择所需的结果。</span><span class="sxs-lookup"><span data-stu-id="6916b-118">Alternatively, you can start typing the name of the command prompt in the search box on the taskbar, and choose the result you want as the result list starts to display the search matches.</span></span>

   ![在 Windows 10 上显示搜索行为的动画 gif](./media/developer-command-prompt-for-vs/windows10-search.gif)

### <a name="windows-81"></a><span data-ttu-id="6916b-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="6916b-120">Windows 8.1</span></span>

1. <span data-ttu-id="6916b-121">按 Windows 徽标键![键盘上的 Windows 徽标键](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)，转到“开始”屏幕。</span><span class="sxs-lookup"><span data-stu-id="6916b-121">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo key on the keyboard.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png)</span></span> <span data-ttu-id="6916b-122">例如，在键盘上。</span><span class="sxs-lookup"><span data-stu-id="6916b-122">on your keyboard for example.</span></span>

1. <span data-ttu-id="6916b-123">在“开始”屏幕上，按 Ctrl+Tab 打开“应用程序”列表，然后按 V。然后显示一个列表，其中包含所有已安装的 Visual Studio 命令提示。</span><span class="sxs-lookup"><span data-stu-id="6916b-123">On the **Start** screen, press **Ctrl**+**Tab** to open the **Apps** list, and then press **V**. This brings up a list that includes all installed Visual Studio command prompts.</span></span>

1. <span data-ttu-id="6916b-124">选择“VS 2019 开发人员命令提示”（或者你想使用的命令提示符）。</span><span class="sxs-lookup"><span data-stu-id="6916b-124">Choose **Developer Command Prompt for VS 2019** (or the command prompt you want to use).</span></span>

### <a name="windows-7"></a><span data-ttu-id="6916b-125">Windows 7</span><span class="sxs-lookup"><span data-stu-id="6916b-125">Windows 7</span></span>

1. <span data-ttu-id="6916b-126">选择“开始”，然后展开“所有程序”。</span><span class="sxs-lookup"><span data-stu-id="6916b-126">Choose **Start** and then expand **All Programs**.</span></span>

1. <span data-ttu-id="6916b-127">选择“Visual Studio 2019” > “Visual Studio Tools” > “VS 2019 开发人员命令提示”，或者你想使用的命令提示。</span><span class="sxs-lookup"><span data-stu-id="6916b-127">Choose **Visual Studio 2019** > **Visual Studio Tools** > **Developer Command Prompt for VS 2019**, or the command prompt you want to use.</span></span>

   ![突出显示命令提示符的 Windows 7“开始”菜单](./media/developer-command-prompt-for-vs/windows7-menu.png)

<span data-ttu-id="6916b-129">如果安装了其他 SDK，例如 [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 或[之前的版本](https://developer.microsoft.com/windows/downloads/sdk-archive)，则可能看到其他命令提示符。</span><span class="sxs-lookup"><span data-stu-id="6916b-129">If you have other SDKs installed, such as the [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) or [previous versions](https://developer.microsoft.com/windows/downloads/sdk-archive), you may see additional command prompts.</span></span> <span data-ttu-id="6916b-130">查看单个工具的文档，以确定应使用哪个版本的命令提示。</span><span class="sxs-lookup"><span data-stu-id="6916b-130">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>

## <a name="manually-locate-the-files-on-your-machine"></a><span data-ttu-id="6916b-131">在计算机中手动查找文件</span><span class="sxs-lookup"><span data-stu-id="6916b-131">Manually locate the files on your machine</span></span>

<span data-ttu-id="6916b-132">已安装的命令提示符的快捷方式通常放在 Visual Studio 的“开始菜单”文件夹中，例如 %ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools。</span><span class="sxs-lookup"><span data-stu-id="6916b-132">Usually, the shortcuts for the command prompts you have installed are placed at the **Start Menu** folder for Visual Studio, such as in *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.</span></span> <span data-ttu-id="6916b-133">但是如果出于某种原因，搜索命令提示未产生预期的效果，你可以尝试在计算机中手动查找快捷方式。</span><span class="sxs-lookup"><span data-stu-id="6916b-133">But if, for some reason, searching for the command prompt doesn't produce the expected results, you can try to manually locate the shortcut on your machine.</span></span> <span data-ttu-id="6916b-134">请尝试搜索命令提示符文件的名称，例如 VsDevCmd.bat，或者转到“工具”文件夹，例如 %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools（该路径根据你的 Visual Studio 版本和安装位置而变化）。</span><span class="sxs-lookup"><span data-stu-id="6916b-134">Try searching for the name of the command prompt file, such as *VsDevCmd.bat*, or go to the Tools folder, such as *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools* (path changes according to your Visual Studio version, edition, and installation location).</span></span>

## <a name="start-the-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="6916b-135">从 Visual Studio 内部启动命令提示符</span><span class="sxs-lookup"><span data-stu-id="6916b-135">Start the command prompt from inside Visual Studio</span></span>

<span data-ttu-id="6916b-136">为便于访问，你可以将开发人员命令提示或其他任何命令提示符添加到 Visual Studio 中的“工具”菜单中。</span><span class="sxs-lookup"><span data-stu-id="6916b-136">For easier access, you can add Developer Command Prompt, or any other command prompt, to the Tools menu in Visual Studio.</span></span> <span data-ttu-id="6916b-137">要使该工具可用，请将其添加到外部工具列表中。</span><span class="sxs-lookup"><span data-stu-id="6916b-137">To make the tool available, add it to the external tools list.</span></span> <span data-ttu-id="6916b-138">步骤如下：</span><span class="sxs-lookup"><span data-stu-id="6916b-138">Here are the steps:</span></span>

1. <span data-ttu-id="6916b-139">打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="6916b-139">Open Visual Studio.</span></span>

1. <span data-ttu-id="6916b-140">在“启动”窗口中，选择“继续但无需代码”。</span><span class="sxs-lookup"><span data-stu-id="6916b-140">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="6916b-141">在菜单栏上，依次选择“工具” > “外部工具”。</span><span class="sxs-lookup"><span data-stu-id="6916b-141">On the menu bar, choose **Tools** > **External Tools**.</span></span>

1. <span data-ttu-id="6916b-142">在“外部工具”对话框中，选择“添加”按钮。</span><span class="sxs-lookup"><span data-stu-id="6916b-142">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="6916b-143">随即出现一个新项。</span><span class="sxs-lookup"><span data-stu-id="6916b-143">A new entry appears.</span></span>

1. <span data-ttu-id="6916b-144">为新菜单项输入“标题”，例如 `Command Prompt`。</span><span class="sxs-lookup"><span data-stu-id="6916b-144">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>

1. <span data-ttu-id="6916b-145">在“命令”字段中，指定要启动的文件，例如 `%comspec%` 或 `C:\Windows\System32\cmd.exe`。</span><span class="sxs-lookup"><span data-stu-id="6916b-145">In the **Command** field, specify the file you want to launch, such as `%comspec%` or `C:\Windows\System32\cmd.exe`.</span></span>

1. <span data-ttu-id="6916b-146">在“参数”字段中，指定可在其中找到要使用的特定命令提示的位置，例如 `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`。</span><span class="sxs-lookup"><span data-stu-id="6916b-146">In the **Arguments** field, specify where to find the specific command prompt you want to use, such as `/k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"`.</span></span> <span data-ttu-id="6916b-147">此命令将启动随 Visual Studio 2019 Community 一起安装的开发人员命令提示。</span><span class="sxs-lookup"><span data-stu-id="6916b-147">This command launches the Developer Command Prompt that's installed with Visual Studio 2019 Community.</span></span> <span data-ttu-id="6916b-148">根据 Visual Studio 版本和安装位置更改此值。</span><span class="sxs-lookup"><span data-stu-id="6916b-148">Change this value according to your Visual Studio version, edition, and installation location.</span></span>

1. <span data-ttu-id="6916b-149">在“初始目录”字段中，指定将在其中启动命令提示符的目录。</span><span class="sxs-lookup"><span data-stu-id="6916b-149">In the **Initial directory** field, specify the directory in which the command prompt will start.</span></span> <span data-ttu-id="6916b-150">通过选择字段旁边的箭头选择值（如“项目目录”）。</span><span class="sxs-lookup"><span data-stu-id="6916b-150">Choose a value such as **Project Directory** by selecting the arrow next to the field.</span></span>

1. <span data-ttu-id="6916b-151">选择“确定”  按钮。</span><span class="sxs-lookup"><span data-stu-id="6916b-151">Choose the **OK** button.</span></span>

   ![已填写字段值的“外部工具”对话框。](./media/developer-command-prompt-for-vs/add-external-tool.png)

   <span data-ttu-id="6916b-153">系统添加了新菜单项，并且你可以从“工具”菜单访问命令提示符。</span><span class="sxs-lookup"><span data-stu-id="6916b-153">The new menu item is added, and you can access the command prompt from the Tools menu.</span></span>

   ![Visual Studio 中的命令提示符菜单项](./media/developer-command-prompt-for-vs/command-prompt-vs-menu.png)

## <a name="see-also"></a><span data-ttu-id="6916b-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="6916b-155">See also</span></span>

- [<span data-ttu-id="6916b-156">.NET Framework 工具</span><span class="sxs-lookup"><span data-stu-id="6916b-156">.NET Framework Tools</span></span>](index.md)
- [<span data-ttu-id="6916b-157">管理外部工具</span><span class="sxs-lookup"><span data-stu-id="6916b-157">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
- [<span data-ttu-id="6916b-158">通过命令行使用 Microsoft C++ 工具集</span><span class="sxs-lookup"><span data-stu-id="6916b-158">Use the Microsoft C++ toolset from the command line</span></span>](/cpp/build/building-on-the-command-line)
