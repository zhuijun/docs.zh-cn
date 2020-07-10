---
title: 将 web 浏览器功能添加到应用
description: 了解如何使用 WebBrowser 控件将 web 浏览器功能添加到 Windows 窗体应用程序。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: a5a33961ac8301bda86bb5f34e65ac159308987f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174544"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>如何将 web 浏览器功能添加到 Windows 窗体应用程序

使用 <xref:System.Windows.Forms.WebBrowser> 控件，可将 Web 浏览器功能添加到应用程序中。 默认情况下，该控件的工作方式类似于 Web 浏览器。 通过设置 <xref:System.Windows.Forms.WebBrowser.Url%2A> 属性加载初始 URL 后，可以通过单击超链接或通过使用键盘快捷方式在导航历史记录中后移或前移，从而进行导航。 默认情况下，可以通过右键单击快捷菜单来访问其他浏览器功能。 还可通过将新文档置于控件上来打开它们。 <xref:System.Windows.Forms.WebBrowser> 控件还具有几个属性、方法和事件，可将它们可用于实现与 Internet Explorer 中类似的用户界面功能。

下面的代码示例实现地址栏、典型的浏览器按钮、“文件”**** 菜单、状态栏以及显示当前页标题的标题栏。

## <a name="example"></a>示例

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a>编译代码

此示例需要：

- 对 `System``System.Drawing` 和 `System.Windows.Forms` 程序集的引用。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.WebBrowser>
- [WebBrowser 控件](webbrowser-control-windows-forms.md)
