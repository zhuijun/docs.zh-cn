---
title: 多文档界面 (MDI) 应用程序
description: 了解 Windows 窗体多文档界面 (MDI) 应用程序如何使您能够同时显示多个文档，每个文档都显示在其自己的窗口中。
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 0912a989ac1710d72c9db1cceb0e695f0ca85dee
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174648"
---
# <a name="multiple-document-interface-mdi-applications"></a><span data-ttu-id="75398-103">多文档界面 (MDI) 应用程序</span><span class="sxs-lookup"><span data-stu-id="75398-103">Multiple-Document Interface (MDI) Applications</span></span>
<span data-ttu-id="75398-104">多文档界面 (MDI) 应用程序使您能够同时显示多个文档，每个文档都显示在其自己的窗口中。</span><span class="sxs-lookup"><span data-stu-id="75398-104">Multiple-document interface (MDI) applications enable you to display multiple documents at the same time, with each document displayed in its own window.</span></span> <span data-ttu-id="75398-105">MDI 应用程序通常具有一个带有子菜单的 "窗口" 菜单项，用于在窗口或文档之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="75398-105">MDI applications often have a Window menu item with submenus for switching between windows or documents.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75398-106">Windows 窗体中 (SDI) windows 的 MDI 窗体和单文档界面之间存在某些行为差异。</span><span class="sxs-lookup"><span data-stu-id="75398-106">There are some behavior differences between MDI forms and single-document interface (SDI) windows in Windows Forms.</span></span> <span data-ttu-id="75398-107">`Opacity`属性不影响 MDI 子窗体的外观。</span><span class="sxs-lookup"><span data-stu-id="75398-107">The `Opacity` property does not affect the appearance of MDI child forms.</span></span> <span data-ttu-id="75398-108">此外，此 <xref:System.Windows.Forms.Form.CenterToParent%2A> 方法不会影响 MDI 子窗体的行为。</span><span class="sxs-lookup"><span data-stu-id="75398-108">Additionally, the <xref:System.Windows.Forms.Form.CenterToParent%2A> method does not affect the behavior of MDI child forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75398-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="75398-109">In This Section</span></span>  
 [<span data-ttu-id="75398-110">如何：创建 MDI 父窗体</span><span class="sxs-lookup"><span data-stu-id="75398-110">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)  
 <span data-ttu-id="75398-111">提供有关为 MDI 应用程序中的多个文档创建容器的说明。</span><span class="sxs-lookup"><span data-stu-id="75398-111">Gives directions for creating the container for the multiple documents within an MDI application.</span></span>  
  
 [<span data-ttu-id="75398-112">如何：创建 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="75398-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)  
 <span data-ttu-id="75398-113">提供有关创建在 MDI 父窗体中运行的一个或多个窗口的说明。</span><span class="sxs-lookup"><span data-stu-id="75398-113">Gives directions for creating one or more windows that operate within an MDI parent form.</span></span>  
  
 [<span data-ttu-id="75398-114">如何：确定活动的 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="75398-114">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)  
 <span data-ttu-id="75398-115">提供有关验证 (的子窗口并将其内容发送到剪贴板) 的说明。</span><span class="sxs-lookup"><span data-stu-id="75398-115">Gives directions for verifying the child window that has focus (and sending its contents to the Clipboard).</span></span>  
  
 [<span data-ttu-id="75398-116">如何：将数据发送到活动的 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="75398-116">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)  
 <span data-ttu-id="75398-117">提供将信息传输到活动子窗口的说明。</span><span class="sxs-lookup"><span data-stu-id="75398-117">Gives directions for transporting information to the active child window.</span></span>  
  
 [<span data-ttu-id="75398-118">如何：排列 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="75398-118">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)  
 <span data-ttu-id="75398-119">提供平铺、层叠或排列 MDI 应用程序的子窗口的说明。</span><span class="sxs-lookup"><span data-stu-id="75398-119">Gives directions for tiling, cascading, or arranging the child windows of an MDI application.</span></span>
