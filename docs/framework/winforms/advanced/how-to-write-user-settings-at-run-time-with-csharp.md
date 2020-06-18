---
title: 如何：在运行时编写用户设置 (C#)
description: '了解如何在运行时使用 c # 编写设置，方法是通过调用 Save 方法在应用程序会话之间保留对设置的更改。'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: 6154ff1b92d6c2d4c788299e59eb8f73e6b69c4b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904320"
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="a8f64-103">如何：在运行时编写用户设置和 C\#</span><span class="sxs-lookup"><span data-stu-id="a8f64-103">How To: Write User Settings at Run Time with C\#</span></span>

<span data-ttu-id="a8f64-104">应用程序范围的设置是只读的，只能在设计时更改，或通过在应用程序会话之间更改 .config 文件进行更改。</span><span class="sxs-lookup"><span data-stu-id="a8f64-104">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="a8f64-105">但用户范围的设置可以在运行时写入，就像更改任何属性值一样。</span><span class="sxs-lookup"><span data-stu-id="a8f64-105">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="a8f64-106">新值在应用程序会话的持续时间内始终存在。</span><span class="sxs-lookup"><span data-stu-id="a8f64-106">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="a8f64-107">可以通过调用 Save 方法在应用程序会话之间保留对设置的更改。</span><span class="sxs-lookup"><span data-stu-id="a8f64-107">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
## <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="a8f64-108">如何：在运行时写入和保存用户设置（C）\#</span><span class="sxs-lookup"><span data-stu-id="a8f64-108">How To: Write and Persist User Settings at Run Time with C\#</span></span>
  
1. <span data-ttu-id="a8f64-109">访问设置并向其分配新值，如本示例中所示：</span><span class="sxs-lookup"><span data-stu-id="a8f64-109">Access the setting and assign it a new value as shown in this example:</span></span>  
  
   ```csharp
   Properties.Settings.Default.myColor = Color.AliceBlue;  
   ```  
  
2. <span data-ttu-id="a8f64-110">如果想要到在应用程序会话之间保留对设置的更改，请调用 Save 方法，如本示例中所示：</span><span class="sxs-lookup"><span data-stu-id="a8f64-110">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```csharp
    Properties.Settings.Default.Save();  
    ```  
  
<span data-ttu-id="a8f64-111">用户设置保存在用户的本地应用程序数据文件夹（隐藏）中子文件夹下的文件内。</span><span class="sxs-lookup"><span data-stu-id="a8f64-111">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f64-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8f64-112">See also</span></span>

- [<span data-ttu-id="a8f64-113">使用应用程序设置和用户设置</span><span class="sxs-lookup"><span data-stu-id="a8f64-113">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="a8f64-114">如何：在运行时读取设置 (C#)</span><span class="sxs-lookup"><span data-stu-id="a8f64-114">How To: Read Settings at Run Time With C#</span></span>](how-to-read-settings-at-run-time-with-csharp.md)
- [<span data-ttu-id="a8f64-115">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="a8f64-115">Application Settings Overview</span></span>](application-settings-overview.md)
