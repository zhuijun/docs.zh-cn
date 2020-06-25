---
title: 如何：使用设计器加载图片
description: 了解如何在设计时使用 Windows 窗体 PictureBox 控件在窗体上加载和显示图片。
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325591"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="b3306-103">如何：使用设计器加载图片（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="b3306-103">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="b3306-104">使用 Windows 窗体 <xref:System.Windows.Forms.PictureBox> 控件，可以通过将属性设置为有效的图片在设计时在窗体上加载和显示图片 <xref:System.Windows.Forms.PictureBox.Image%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b3306-104">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="b3306-105">下表显示了可接受的文件类型。</span><span class="sxs-lookup"><span data-stu-id="b3306-105">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="b3306-106">类型</span><span class="sxs-lookup"><span data-stu-id="b3306-106">Type</span></span>|<span data-ttu-id="b3306-107">文件扩展名</span><span class="sxs-lookup"><span data-stu-id="b3306-107">File name extension</span></span>|
|---|---|
|<span data-ttu-id="b3306-108">Bitmap</span><span class="sxs-lookup"><span data-stu-id="b3306-108">Bitmap</span></span>|<span data-ttu-id="b3306-109">.bmp</span><span class="sxs-lookup"><span data-stu-id="b3306-109">.bmp</span></span>|
|<span data-ttu-id="b3306-110">图标</span><span class="sxs-lookup"><span data-stu-id="b3306-110">Icon</span></span>|<span data-ttu-id="b3306-111">.ico</span><span class="sxs-lookup"><span data-stu-id="b3306-111">.ico</span></span>|
|<span data-ttu-id="b3306-112">GIF</span><span class="sxs-lookup"><span data-stu-id="b3306-112">GIF</span></span>|<span data-ttu-id="b3306-113">.gif</span><span class="sxs-lookup"><span data-stu-id="b3306-113">.gif</span></span>|
|<span data-ttu-id="b3306-114"> 图元文件</span><span class="sxs-lookup"><span data-stu-id="b3306-114">Metafile</span></span>|<span data-ttu-id="b3306-115">.wmf</span><span class="sxs-lookup"><span data-stu-id="b3306-115">.wmf</span></span>|
|<span data-ttu-id="b3306-116">JPEG</span><span class="sxs-lookup"><span data-stu-id="b3306-116">JPEG</span></span>|<span data-ttu-id="b3306-117">.jpg</span><span class="sxs-lookup"><span data-stu-id="b3306-117">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="b3306-118">在设计时显示图片</span><span class="sxs-lookup"><span data-stu-id="b3306-118">To display a picture at design time</span></span>

1. <span data-ttu-id="b3306-119"><xref:System.Windows.Forms.PictureBox>在窗体上绘制控件。</span><span class="sxs-lookup"><span data-stu-id="b3306-119">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="b3306-120">在 "**属性**" 窗口中，选择 <xref:System.Windows.Forms.PictureBox.Image%2A> 属性，然后选择省略号按钮以显示 "**打开**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="b3306-120">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="b3306-121">如果你要查找特定的文件类型（例如 .gif 文件），请在 "**文件类型**" 框中选择它。</span><span class="sxs-lookup"><span data-stu-id="b3306-121">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="b3306-122">选择要显示的文件。</span><span class="sxs-lookup"><span data-stu-id="b3306-122">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="b3306-123">在设计时清除图片</span><span class="sxs-lookup"><span data-stu-id="b3306-123">To clear the picture at design time</span></span>

1. <span data-ttu-id="b3306-124">在 "**属性**" 窗口中，选择 <xref:System.Windows.Forms.PictureBox.Image%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="b3306-124">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="b3306-125">右键单击图像对象名称左侧显示的小缩略图图像，然后选择 "**重置**"。</span><span class="sxs-lookup"><span data-stu-id="b3306-125">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3306-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3306-126">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="b3306-127">PictureBox 控件概述</span><span class="sxs-lookup"><span data-stu-id="b3306-127">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="b3306-128">如何：在运行时修改图片的大小或位置</span><span class="sxs-lookup"><span data-stu-id="b3306-128">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="b3306-129">如何：在运行时设置图片</span><span class="sxs-lookup"><span data-stu-id="b3306-129">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="b3306-130">PictureBox 控件</span><span class="sxs-lookup"><span data-stu-id="b3306-130">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
