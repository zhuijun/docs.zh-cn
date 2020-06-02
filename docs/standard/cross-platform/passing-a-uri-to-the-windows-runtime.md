---
title: 向 Windows 运行时传递 URI
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
ms.openlocfilehash: 7152fb02abf430c0d0e27b82550e4006e3958e93
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288883"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>向 Windows 运行时传递 URI
Windows 运行时方法只接受绝对 URI。 如果将相对 URI 传递到 Windows 运行时方法，则 <xref:System.ArgumentException> 会引发异常。 原因如下：在 .NET Framework 代码中使用 Windows 运行时时， <xref:Windows.Foundation.Uri?displayProperty=nameWithType> 类 <xref:System.Uri?displayProperty=nameWithType> 在 Intellisense 中显示为。 <xref:System.Uri?displayProperty=nameWithType>类允许相对 uri，但类却 <xref:Windows.Foundation.Uri?displayProperty=nameWithType> 不允许。 对于在 Windows 运行时组件中公开的方法也是如此。 如果组件公开接收 URI 的方法，则代码中的签名包含 <xref:System.Uri?displayProperty=nameWithType>。 但是，对于组件的用户，签名包括 <xref:Windows.Foundation.Uri?displayProperty=nameWithType> 。 传递给组件的 URI 必须是绝对 URI。  
  
本主题演示了如何检测绝对 URI 以及如何在引用应用包中的资源时创建一个。  
  
## <a name="detecting-and-using-an-absolute-uri"></a>检测和使用绝对 URI  
使用 <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> 属性可确保在将 URI 传递给 Windows 运行时之前，该 URI 是绝对的。 使用此属性比捕获和处理 <xref:System.ArgumentException> 异常更为有效。  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>将绝对 URI 用于应用包中的资源  
如果想要为应用包包含的资源指定 URI，可以使用 `ms-appx` 或 `ms-appx-web` 方案来创建绝对 URI。  
  
下面的示例演示如何 <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> <xref:Windows.UI.Xaml.Controls.WebView> 使用 XAML 和代码将控件的属性和 <xref:Windows.UI.Xaml.Controls.Image.Source%2A> 控件的属性设置 <xref:Windows.UI.Xaml.Controls.Image> 为包含在名为页的文件夹中的资源。  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
有关这些方案的详细信息，请参阅 Windows 开发人员中心中的 [URI 方案](/windows/uwp/app-resources/uri-schemes)。  
  
## <a name="see-also"></a>另请参阅

- [.NET Framework 对 Windows 应用商店应用程序和 Windows 运行时的支持情况](support-for-windows-store-apps-and-windows-runtime.md)
