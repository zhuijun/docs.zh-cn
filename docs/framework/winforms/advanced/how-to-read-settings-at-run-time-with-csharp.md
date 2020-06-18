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
# <a name="how-to-read-settings-at-run-time-with-c"></a>如何：在运行时读取设置 C\#

可以通过“属性”对象在运行时读取应用程序范围和用户范围的设置。 Properties 对象通过在其上定义的项目的默认命名空间中的 "Properties" 属性公开项目的所有默认设置。  
  
## <a name="to-read-settings-at-run-time-with-c"></a>在运行时通过 C 读取设置\#
  
请通过 Properties.Settings.Default 成员访问相应的设置。 下面的示例演示如何将名为 `myColor` 的设置分配给 BackColor 属性。 这要求你在之前已创建包含名为 `myColor` 的设置（其类型为 `System.Drawing.Color`）的设置文件。 有关创建设置文件的信息，请参阅[如何：在设计时创建新设置](how-to-create-a-new-setting-at-design-time.md)。  
  
```csharp
this.BackColor = Properties.Settings.Default.myColor;  
```  
  
## <a name="see-also"></a>另请参阅

- [使用应用程序设置和用户设置](using-application-settings-and-user-settings.md)
- [如何：在运行时编写用户设置 (C#)](how-to-write-user-settings-at-run-time-with-csharp.md)
- [应用程序设置概述](application-settings-overview.md)
