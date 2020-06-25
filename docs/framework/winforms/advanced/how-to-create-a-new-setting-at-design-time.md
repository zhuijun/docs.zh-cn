---
title: 如何：在设计时创建新设置
description: 了解如何在设计时使用 Visual Studio 中的 "设置设计器" 创建新的 Windows 窗体设置。
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325840"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="c8368-103">如何：在设计时创建新设置</span><span class="sxs-lookup"><span data-stu-id="c8368-103">How To: Create a new setting at design time</span></span>

<span data-ttu-id="c8368-104">您可以使用 Visual Studio 中的 "设置设计器" 在设计时创建新设置。</span><span class="sxs-lookup"><span data-stu-id="c8368-104">You can create a new setting at design time by using the Settings designer in Visual Studio.</span></span> <span data-ttu-id="c8368-105">"设置设计器" 是一种网格样式的界面，它允许您创建新设置并指定这些设置的属性。</span><span class="sxs-lookup"><span data-stu-id="c8368-105">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="c8368-106">您必须指定新设置的名称、值、类型和作用域。</span><span class="sxs-lookup"><span data-stu-id="c8368-106">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="c8368-107">创建设置后，可在代码中对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="c8368-107">Once a setting is created, it is accessible in code.</span></span>

## <a name="create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="c8368-108">在设计时使用 C 创建新设置\#</span><span class="sxs-lookup"><span data-stu-id="c8368-108">Create a new setting at design time in C\#</span></span>

1. <span data-ttu-id="c8368-109">打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="c8368-109">Open Visual Studio.</span></span>

2. <span data-ttu-id="c8368-110">在**解决方案资源管理器**中，展开项目的 "**属性**" 节点。</span><span class="sxs-lookup"><span data-stu-id="c8368-110">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>

3. <span data-ttu-id="c8368-111">双击要在其中添加新设置的 "设置" 文件。</span><span class="sxs-lookup"><span data-stu-id="c8368-111">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="c8368-112">此文件的默认名称为 "设置"。</span><span class="sxs-lookup"><span data-stu-id="c8368-112">The default name for this file is Settings.settings.</span></span>

4. <span data-ttu-id="c8368-113">在设置设计器中，设置设置的**名称**、**值**、**类型**和**作用域**。</span><span class="sxs-lookup"><span data-stu-id="c8368-113">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="c8368-114">每一行都表示一个设置。</span><span class="sxs-lookup"><span data-stu-id="c8368-114">Each row represents a single setting.</span></span>

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="c8368-115">在设计时在 Visual Basic 中创建新设置</span><span class="sxs-lookup"><span data-stu-id="c8368-115">Create a new setting at design time in Visual Basic</span></span>

1. <span data-ttu-id="c8368-116">打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="c8368-116">Open Visual Studio.</span></span>

2. <span data-ttu-id="c8368-117">在**解决方案资源管理器**中，右键单击项目节点，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="c8368-117">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>

3. <span data-ttu-id="c8368-118">在 "**属性**" 页中，选择 "**设置**" 选项卡。</span><span class="sxs-lookup"><span data-stu-id="c8368-118">In the **Properties** page, select the **Settings** tab.</span></span>

4. <span data-ttu-id="c8368-119">在设置设计器中，设置设置的**名称**、**值**、**类型**和**作用域**。</span><span class="sxs-lookup"><span data-stu-id="c8368-119">In the Settings designer, set the **Name**, **Value**, **Type**, and **Scope** for your setting.</span></span> <span data-ttu-id="c8368-120">每一行都表示一个设置。</span><span class="sxs-lookup"><span data-stu-id="c8368-120">Each row represents a single setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8368-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8368-121">See also</span></span>

- [<span data-ttu-id="c8368-122">使用应用程序设置和用户设置</span><span class="sxs-lookup"><span data-stu-id="c8368-122">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="c8368-123">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="c8368-123">Application Settings Overview</span></span>](application-settings-overview.md)
- [<span data-ttu-id="c8368-124">如何：在设计时更改现有设置的值</span><span class="sxs-lookup"><span data-stu-id="c8368-124">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
