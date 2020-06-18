---
title: 如何：在运行时读取设置 (C#)
description: 了解如何通过 Properties 对象在运行时读取应用程序范围的设置和用户范围的设置。
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
ms.openlocfilehash: d784544e018bb693c501e35ea36fcae1946ef5eb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903346"
---
# <a name="how-to-read-settings-at-run-time-with-c"></a><span data-ttu-id="ee45a-103">如何：在运行时读取设置 C\#</span><span class="sxs-lookup"><span data-stu-id="ee45a-103">How To: Read Settings at Run Time With C\#</span></span>

<span data-ttu-id="ee45a-104">可以通过“属性”对象在运行时读取应用程序范围和用户范围的设置。</span><span class="sxs-lookup"><span data-stu-id="ee45a-104">You can read both Application-scoped and User-scoped settings at run time via the Properties object.</span></span> <span data-ttu-id="ee45a-105">Properties 对象通过在其上定义的项目的默认命名空间中的 "Properties" 属性公开项目的所有默认设置。</span><span class="sxs-lookup"><span data-stu-id="ee45a-105">The Properties object exposes all of the default settings for the project via the Properties.Settings.Default member in the default namespace of the project they are defined in.</span></span>  
  
## <a name="to-read-settings-at-run-time-with-c"></a><span data-ttu-id="ee45a-106">在运行时通过 C 读取设置\#</span><span class="sxs-lookup"><span data-stu-id="ee45a-106">To Read Settings at Run Time with C\#</span></span>
  
<span data-ttu-id="ee45a-107">请通过 Properties.Settings.Default 成员访问相应的设置。</span><span class="sxs-lookup"><span data-stu-id="ee45a-107">Access the appropriate setting via the Properties.Settings.Default member.</span></span> <span data-ttu-id="ee45a-108">下面的示例演示如何将名为 `myColor` 的设置分配给 BackColor 属性。</span><span class="sxs-lookup"><span data-stu-id="ee45a-108">The following example shows how to assign a setting named `myColor` to a BackColor property.</span></span> <span data-ttu-id="ee45a-109">这要求你在之前已创建包含名为 `myColor` 的设置（其类型为 `System.Drawing.Color`）的设置文件。</span><span class="sxs-lookup"><span data-stu-id="ee45a-109">It requires you to have previously created a Settings file containing a setting named `myColor` of type `System.Drawing.Color`.</span></span> <span data-ttu-id="ee45a-110">有关创建设置文件的信息，请参阅[如何：在设计时创建新设置](how-to-create-a-new-setting-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="ee45a-110">For information about creating a Settings file, see [How To: Create a New Setting at Design Time](how-to-create-a-new-setting-at-design-time.md).</span></span>  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee45a-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee45a-111">See also</span></span>

- [<span data-ttu-id="ee45a-112">使用应用程序设置和用户设置</span><span class="sxs-lookup"><span data-stu-id="ee45a-112">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="ee45a-113">如何：在运行时编写用户设置 (C#)</span><span class="sxs-lookup"><span data-stu-id="ee45a-113">How To: Write User Settings at Run Time with C#</span></span>](how-to-write-user-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="ee45a-114">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="ee45a-114">Application Settings Overview</span></span>](application-settings-overview.md)
