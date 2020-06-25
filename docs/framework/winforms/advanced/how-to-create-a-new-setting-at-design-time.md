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
# <a name="how-to-create-a-new-setting-at-design-time"></a>如何：在设计时创建新设置

您可以使用 Visual Studio 中的 "设置设计器" 在设计时创建新设置。 "设置设计器" 是一种网格样式的界面，它允许您创建新设置并指定这些设置的属性。 您必须指定新设置的名称、值、类型和作用域。 创建设置后，可在代码中对其进行访问。

## <a name="create-a-new-setting-at-design-time-in-c"></a>在设计时使用 C 创建新设置\#

1. 打开 Visual Studio。

2. 在**解决方案资源管理器**中，展开项目的 "**属性**" 节点。

3. 双击要在其中添加新设置的 "设置" 文件。 此文件的默认名称为 "设置"。

4. 在设置设计器中，设置设置的**名称**、**值**、**类型**和**作用域**。 每一行都表示一个设置。

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a>在设计时在 Visual Basic 中创建新设置

1. 打开 Visual Studio。

2. 在**解决方案资源管理器**中，右键单击项目节点，然后选择 "**属性**"。

3. 在 "**属性**" 页中，选择 "**设置**" 选项卡。

4. 在设置设计器中，设置设置的**名称**、**值**、**类型**和**作用域**。 每一行都表示一个设置。

## <a name="see-also"></a>另请参阅

- [使用应用程序设置和用户设置](using-application-settings-and-user-settings.md)
- [应用程序设置概述](application-settings-overview.md)
- [如何：在设计时更改现有设置的值](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
