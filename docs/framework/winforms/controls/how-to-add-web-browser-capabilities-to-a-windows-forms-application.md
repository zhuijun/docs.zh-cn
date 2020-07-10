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
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="118a3-103">如何将 web 浏览器功能添加到 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="118a3-103">How to add web browser capabilities to a Windows Forms application</span></span>

<span data-ttu-id="118a3-104">使用 <xref:System.Windows.Forms.WebBrowser> 控件，可将 Web 浏览器功能添加到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="118a3-104">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="118a3-105">默认情况下，该控件的工作方式类似于 Web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="118a3-105">The control works like a Web browser by default.</span></span> <span data-ttu-id="118a3-106">通过设置 <xref:System.Windows.Forms.WebBrowser.Url%2A> 属性加载初始 URL 后，可以通过单击超链接或通过使用键盘快捷方式在导航历史记录中后移或前移，从而进行导航。</span><span class="sxs-lookup"><span data-stu-id="118a3-106">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="118a3-107">默认情况下，可以通过右键单击快捷菜单来访问其他浏览器功能。</span><span class="sxs-lookup"><span data-stu-id="118a3-107">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="118a3-108">还可通过将新文档置于控件上来打开它们。</span><span class="sxs-lookup"><span data-stu-id="118a3-108">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="118a3-109"><xref:System.Windows.Forms.WebBrowser> 控件还具有几个属性、方法和事件，可将它们可用于实现与 Internet Explorer 中类似的用户界面功能。</span><span class="sxs-lookup"><span data-stu-id="118a3-109">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>

<span data-ttu-id="118a3-110">下面的代码示例实现地址栏、典型的浏览器按钮、“文件”\*\*\*\* 菜单、状态栏以及显示当前页标题的标题栏。</span><span class="sxs-lookup"><span data-stu-id="118a3-110">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>

## <a name="example"></a><span data-ttu-id="118a3-111">示例</span><span class="sxs-lookup"><span data-stu-id="118a3-111">Example</span></span>

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a><span data-ttu-id="118a3-112">编译代码</span><span class="sxs-lookup"><span data-stu-id="118a3-112">Compile the code</span></span>

<span data-ttu-id="118a3-113">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="118a3-113">This example requires:</span></span>

- <span data-ttu-id="118a3-114">对 `System``System.Drawing` 和 `System.Windows.Forms` 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="118a3-114">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="118a3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="118a3-115">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="118a3-116">WebBrowser 控件</span><span class="sxs-lookup"><span data-stu-id="118a3-116">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
