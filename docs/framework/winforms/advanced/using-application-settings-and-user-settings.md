---
title: 使用应用程序设置和用户设置
ms.date: 03/30/2017
description: 了解如何使用应用程序设置和用户设置来创建和访问在应用程序执行会话之间保持的值。
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
ms.openlocfilehash: a30fd354986265eca002fce57bccf5b3bb2adc15
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903163"
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="47b05-103">使用应用程序设置和用户设置</span><span class="sxs-lookup"><span data-stu-id="47b05-103">Using Application Settings and User Settings</span></span>
<span data-ttu-id="47b05-104">从 .NET Framework 2.0 开始，你可以创建和访问在应用程序执行会话之间保持的值。</span><span class="sxs-lookup"><span data-stu-id="47b05-104">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="47b05-105">这些值称为 "*设置*"。</span><span class="sxs-lookup"><span data-stu-id="47b05-105">These values are called *settings*.</span></span> <span data-ttu-id="47b05-106">设置可以表示用户首选项，或应用程序需要使用的重要信息。</span><span class="sxs-lookup"><span data-stu-id="47b05-106">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="47b05-107">例如，可以创建一系列设置，用于存储应用程序的配色方案的用户首选项。</span><span class="sxs-lookup"><span data-stu-id="47b05-107">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="47b05-108">或者，可以存储用于指定应用程序所使用的数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="47b05-108">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="47b05-109">设置允许您将对应用程序而言至关重要的信息持久保存在代码之外，并创建用于存储各个用户的首选项的配置文件。</span><span class="sxs-lookup"><span data-stu-id="47b05-109">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="47b05-110">本节中的主题介绍如何在设计时和运行时使用设置。</span><span class="sxs-lookup"><span data-stu-id="47b05-110">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47b05-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="47b05-111">In This Section</span></span>  
 [<span data-ttu-id="47b05-112">如何：在设计时创建新设置</span><span class="sxs-lookup"><span data-stu-id="47b05-112">How To: Create a New Setting at Design Time</span></span>](how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="47b05-113">介绍如何使用 Visual Studio 为应用程序创建新设置。</span><span class="sxs-lookup"><span data-stu-id="47b05-113">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="47b05-114">如何：在设计时更改现有设置的值</span><span class="sxs-lookup"><span data-stu-id="47b05-114">How To: Change the Value of an Existing Setting at Design Time</span></span>](how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="47b05-115">介绍如何使用 Visual Studio 更改现有设置的值。</span><span class="sxs-lookup"><span data-stu-id="47b05-115">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="47b05-116">如何：在应用程序会话间更改设置的值</span><span class="sxs-lookup"><span data-stu-id="47b05-116">How To: Change the Value of a Setting Between Application Sessions</span></span>](how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="47b05-117">详细介绍如何在应用程序会话之间更改已编译的应用程序中设置的值。</span><span class="sxs-lookup"><span data-stu-id="47b05-117">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="47b05-118">如何：在运行时读取设置 (C#)</span><span class="sxs-lookup"><span data-stu-id="47b05-118">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="47b05-119">介绍如何使用代码通过 c # 读取设置。</span><span class="sxs-lookup"><span data-stu-id="47b05-119">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="47b05-120">如何：在运行时编写用户设置 (C#)</span><span class="sxs-lookup"><span data-stu-id="47b05-120">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="47b05-121">说明如何使用 c # 编写和保存用户设置的值。</span><span class="sxs-lookup"><span data-stu-id="47b05-121">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="47b05-122">如何：向应用程序添加多组设置 (C#)</span><span class="sxs-lookup"><span data-stu-id="47b05-122">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="47b05-123">详细说明如何使用 c # 将多个设置集添加到应用程序。</span><span class="sxs-lookup"><span data-stu-id="47b05-123">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b05-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47b05-124">See also</span></span>

- [<span data-ttu-id="47b05-125">Windows 窗体的应用程序设置</span><span class="sxs-lookup"><span data-stu-id="47b05-125">Application Settings for Windows Forms</span></span>](application-settings-for-windows-forms.md)
