---
title: 如何：使用 WebBrowser 控件导航到 URL
description: 了解如何使用 Windows 窗体 WebBrowser. 导航控件导航到特定的 URL。 还了解如何确定何时加载新文档。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325575"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>如何：使用 WebBrowser 控件导航到 URL
下面的代码示例演示如何将控件导航 <xref:System.Windows.Forms.WebBrowser> 到特定的 URL。

 若要确定新文档完全加载的时间，请处理 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> 事件。 有关此事件的演示，请参阅[如何：使用 WebBrowser 控件进行打印](how-to-print-with-a-webbrowser-control.md)。

## <a name="example"></a>示例

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a>编译代码
 此示例需要：

- 名为 `webBrowser1` 的 <xref:System.Windows.Forms.WebBrowser> 控件。

- 对 `System` 和 `System.Windows.Forms` 程序集的引用。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser 控件](webbrowser-control-windows-forms.md)
- [如何：使用 WebBrowser 控件打印](how-to-print-with-a-webbrowser-control.md)
