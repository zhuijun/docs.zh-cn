---
title: 如何添加初始屏幕
description: 了解如何向 Windows Presentation Foundation （WPF）应用程序添加启动窗口或初始屏幕。
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617955"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="13296-103">如何：将初始屏幕添加到 WPF 应用程序</span><span class="sxs-lookup"><span data-stu-id="13296-103">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="13296-104">本主题演示如何将启动窗口或*初始屏幕*添加到 WINDOWS PRESENTATION FOUNDATION （WPF）应用程序。</span><span class="sxs-lookup"><span data-stu-id="13296-104">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="13296-105">将现有图像添加为初始屏幕</span><span class="sxs-lookup"><span data-stu-id="13296-105">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="13296-106">创建或查找要用于初始屏幕的映像。</span><span class="sxs-lookup"><span data-stu-id="13296-106">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="13296-107">可以使用 Windows 映像组件（WIC）支持的任何图像格式。</span><span class="sxs-lookup"><span data-stu-id="13296-107">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="13296-108">例如，可以使用 BMP、GIF、JPEG、PNG 或 TIFF 格式。</span><span class="sxs-lookup"><span data-stu-id="13296-108">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="13296-109">将图像文件添加到 WPF 应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="13296-109">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="13296-110">在**解决方案资源管理器**中，选择图像。</span><span class="sxs-lookup"><span data-stu-id="13296-110">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="13296-111">在属性窗口中，单击 "**生成操作**" 属性的下拉箭头。</span><span class="sxs-lookup"><span data-stu-id="13296-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="13296-112">从下拉列表中选择 " **SplashScreen** "。</span><span class="sxs-lookup"><span data-stu-id="13296-112">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="13296-113">按**F5**生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="13296-113">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="13296-114">初始屏幕图像显示在屏幕的中心，然后在主应用程序窗口出现时淡化。</span><span class="sxs-lookup"><span data-stu-id="13296-114">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="13296-115">从生成中排除初始屏幕</span><span class="sxs-lookup"><span data-stu-id="13296-115">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="13296-116">在**解决方案资源管理器**中，选择初始屏幕图像。</span><span class="sxs-lookup"><span data-stu-id="13296-116">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="13296-117">在 "**属性**" 窗口中，将 "**生成操作**" 设置为 "**无**"。</span><span class="sxs-lookup"><span data-stu-id="13296-117">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="13296-118">从应用程序中删除初始屏幕</span><span class="sxs-lookup"><span data-stu-id="13296-118">To remove the splash screen from an application</span></span>

<span data-ttu-id="13296-119">在**解决方案资源管理器**中，删除初始屏幕图像。</span><span class="sxs-lookup"><span data-stu-id="13296-119">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="13296-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="13296-120">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="13296-121">[如何向项目中添加现有项](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="13296-121">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
