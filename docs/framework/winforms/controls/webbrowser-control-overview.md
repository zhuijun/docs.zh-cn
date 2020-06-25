---
title: WebBrowser 控件概述
description: 了解如何使用 WebBrowser 控件在单个应用程序中将 Web 控件与 Windows 窗体控件无缝组合。
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 6a0548bb0f5905d8f848ab13fb82d32b50caa891
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325740"
---
# <a name="webbrowser-control-overview"></a>WebBrowser 控件概述
<xref:System.Windows.Forms.WebBrowser>控件为 WebBrowser ActiveX 控件提供托管包装。 托管包装使你可以在 Windows 窗体客户端应用程序中显示网页。 您可以使用该 <xref:System.Windows.Forms.WebBrowser> 控件在您的应用程序中复制 Internet Explorer Web 浏览功能，也可以禁用默认的 Internet explorer 功能，并将该控件用作简单的 HTML 文档查看器。 你还可以使用控件将基于 DHTML 的用户界面元素添加到窗体中，并隐藏控件中承载的这一事实 <xref:System.Windows.Forms.WebBrowser> 。 此方法使你能够在单个应用程序中将 Web 控件与 Windows 窗体控件无缝组合。  
  
## <a name="frequently-used-properties-methods-and-events"></a>常用的属性、方法和事件  
 <xref:System.Windows.Forms.WebBrowser>控件具有多个可用于实现 Internet Explorer 中的控件的属性、方法和事件。 例如，你可以使用 `Navigate` 方法来实现地址栏，使用 `GoBack` 、、 `GoForward` `Stop` 和 `Refresh` 方法来实现工具栏上的导航按钮。 可以处理事件， `Navigated` 以便用属性的值 `Url` 和标题栏的属性值来更新地址栏 `DocumentTitle` 。  
  
 如果要在应用程序中生成自己的页面内容，可以设置 `DocumentText` 属性。 如果熟悉 HTML 文档对象模型（DOM），还可以通过属性操作当前网页的内容 `Document` 。 利用此属性，你可以在内存中存储和修改文档，而无需在文件之间导航。  
  
 `Document`属性还允许您从客户端应用程序代码调用网页脚本代码中实现的方法。 若要从脚本代码访问客户端应用程序代码，请设置 `ObjectForScripting` 属性。 您指定的对象可以由您的脚本代码作为对象进行访问 `window.external` 。  
  
|名称|说明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> 属性|获取一个对象，该对象提供对当前网页的 HTML 文档对象模型（DOM）的托管访问。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件|网页完成加载时发生。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> 属性|获取或设置当前网页的 HTML 内容。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> 属性|获取当前网页的标题。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> 方法|导航至历史记录中的上一页。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> 方法|导航至历史记录中的下一页。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> 方法|导航到指定的 URL。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> 事件|导航开始之前发生，使操作可以取消。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> 属性|获取或设置一个对象，该对象可用于与您的应用程序进行通信。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> 方法|打印当前网页。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> 方法|重新加载当前网页。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> 方法|暂停当前导航并停止动态页面元素，如声音和动画。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> 属性|获取或设置当前网页的 URL。 设置此属性会将控件导航到新的 URL。|  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [如何：使用 WebBrowser 控件导航到 URL](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [如何：使用 WebBrowser 控件打印](how-to-print-with-a-webbrowser-control.md)
- [如何：向 Windows 窗体应用程序添加 Web 浏览器功能](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [如何：在 Windows 窗体应用程序中创建 HTML 文档查看器](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [如何：在 DHTML 代码和客户端应用程序代码之间实现双向通信](implement-two-way-com-between-dhtml-and-client.md)
- [WebBrowser 安全](webbrowser-security.md)
