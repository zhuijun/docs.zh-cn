---
title: 控件
description: 了解如何添加和定位 Windows 窗体控件。 你还可以在设计器中操作控件并编写代码，以便在运行时动态添加控件。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls
- controls [Windows Forms]
- Windows Forms controls, about Windows Forms controls
ms.assetid: f050de8f-4ebd-4042-94b8-edf9a1dbd52a
ms.openlocfilehash: 9ca4a2a1205663ae0ff4537a58cc1991a15da5d8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324041"
---
# <a name="windows-forms-controls"></a><span data-ttu-id="3aa2c-104">Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="3aa2c-104">Windows Forms controls</span></span>

<span data-ttu-id="3aa2c-105">设计和修改 Windows 窗体应用程序的用户界面时，需要添加、对齐和定位控件。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-105">As you design and modify the user interface of your Windows Forms applications, you will need to add, align, and position controls.</span></span> <span data-ttu-id="3aa2c-106">控件是窗体对象内包含的对象。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-106">Controls are objects that are contained within form objects.</span></span> <span data-ttu-id="3aa2c-107">每种类型的控件都有自己的一组属性、方法和事件，使其适用于特定用途。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-107">Each type of control has its own set of properties, methods, and events that make it suitable for a particular purpose.</span></span> <span data-ttu-id="3aa2c-108">可以在设计器中控制控件，并将代码编写为在运行时动态添加控件。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-108">You can manipulate controls in the designer and write code to add controls dynamically at run time.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3aa2c-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="3aa2c-109">In this section</span></span>

<span data-ttu-id="3aa2c-110">[将控件置于 Windows 窗体](putting-controls-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3aa2c-110">[Putting Controls on Windows Forms](putting-controls-on-windows-forms.md)</span></span>\
<span data-ttu-id="3aa2c-111">收录了有关将控件置于窗体上的链接。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-111">Provides links related to putting controls on forms.</span></span>

<span data-ttu-id="3aa2c-112">[排列 Windows 窗体上的控件](how-to-align-multiple-controls-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3aa2c-112">[Arranging Controls on Windows Forms](how-to-align-multiple-controls-on-windows-forms.md)</span></span>\
<span data-ttu-id="3aa2c-113">与在窗体上排列控件相关的文章。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-113">Articles related to arranging controls on forms.</span></span>

<span data-ttu-id="3aa2c-114">[为单个 Windows 窗体控件标记并提供其快捷方式](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)</span><span class="sxs-lookup"><span data-stu-id="3aa2c-114">[Labeling Individual Windows Forms Controls and Providing Shortcuts to Them](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)</span></span>\
<span data-ttu-id="3aa2c-115">介绍了如何使用键盘快捷键、控件文本标签和修改键。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-115">Describes the uses of keyboard shortcuts, text labels on controls, and modifier keys.</span></span>

<span data-ttu-id="3aa2c-116">[要在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="3aa2c-116">[Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md)</span></span>\
<span data-ttu-id="3aa2c-117">列出了 Windows 窗体支持的控件以及每个控件可以完成的基本操作。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-117">Lists the controls that work with Windows Forms, and basic things you can accomplish with each control.</span></span>

<span data-ttu-id="3aa2c-118">[利用 .NET Framework 开发自定义 Windows 窗体控件](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="3aa2c-118">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="3aa2c-119">介绍了背景信息和示例，有助于用户开发自定义 Windows 窗体控件。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-119">Provides background information and samples to help users develop custom Windows Forms controls.</span></span>

<span data-ttu-id="3aa2c-120">[在设计时开发 Windows 窗体控件](developing-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="3aa2c-120">[Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="3aa2c-121">介绍了通过设计和继承创建自定义控件的技巧。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-121">Describes techniques for creating custom controls through design and inheritance.</span></span>

## <a name="related-sections"></a><span data-ttu-id="3aa2c-122">相关章节</span><span class="sxs-lookup"><span data-stu-id="3aa2c-122">Related sections</span></span>

<span data-ttu-id="3aa2c-123">[客户端应用程序](../../develop-client-apps.md)</span><span class="sxs-lookup"><span data-stu-id="3aa2c-123">[Client Applications](../../develop-client-apps.md)</span></span>\
<span data-ttu-id="3aa2c-124">概述了如何开发基于 Windows 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3aa2c-124">Provides an overview of developing Windows-based applications.</span></span>
