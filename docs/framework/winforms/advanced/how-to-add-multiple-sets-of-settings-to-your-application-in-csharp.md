---
title: 如何：向应用程序添加多组设置 (C#)
description: '了解如何使用 Visual Studio 将多组 Windows 窗体设置添加到 c # 中的应用程序。'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173440"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="647af-103">如何：在 C 中向应用程序添加多个设置集\#</span><span class="sxs-lookup"><span data-stu-id="647af-103">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="647af-104">在某些情况下，你可能希望在应用程序中包含多组设置。</span><span class="sxs-lookup"><span data-stu-id="647af-104">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="647af-105">例如，如果你正在开发一个应用程序，其中一组特定的设置需要频繁更改，则可能会将它们全部隔开到一个文件中，以便可以将该文件替换为批发，而不影响其他设置。</span><span class="sxs-lookup"><span data-stu-id="647af-105">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="647af-106">Visual Studio 允许你向项目添加多个设置集。</span><span class="sxs-lookup"><span data-stu-id="647af-106">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="647af-107">可以通过对象访问其他设置集 `Properties.Settings` 。</span><span class="sxs-lookup"><span data-stu-id="647af-107">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="647af-108">添加一组其他设置</span><span class="sxs-lookup"><span data-stu-id="647af-108">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="647af-109">在 Visual Studio 的 "**项目**" 菜单中，选择 "**添加新项**"。</span><span class="sxs-lookup"><span data-stu-id="647af-109">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="647af-110">此时将打开“添加新项”对话框。</span><span class="sxs-lookup"><span data-stu-id="647af-110">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="647af-111">在 "**添加新项**" 对话框中，选择 "**设置文件**"，输入文件的名称，然后单击 "**添加**" 以将新的设置文件添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="647af-111">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="647af-112">在**解决方案资源管理器**中，将新的设置文件拖到**Properties**文件夹中。</span><span class="sxs-lookup"><span data-stu-id="647af-112">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="647af-113">这允许您的新设置在代码中可用。</span><span class="sxs-lookup"><span data-stu-id="647af-113">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="647af-114">像添加任何其他设置文件一样，在此文件中添加和使用设置。</span><span class="sxs-lookup"><span data-stu-id="647af-114">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="647af-115">可以通过对象访问这组设置 `Properties.Settings` 。</span><span class="sxs-lookup"><span data-stu-id="647af-115">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="647af-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="647af-116">See also</span></span>

- [<span data-ttu-id="647af-117">使用应用程序设置和用户设置</span><span class="sxs-lookup"><span data-stu-id="647af-117">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="647af-118">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="647af-118">Application Settings Overview</span></span>](application-settings-overview.md)
