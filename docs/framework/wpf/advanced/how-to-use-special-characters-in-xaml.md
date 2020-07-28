---
title: 如何：在 XAML 中使用特殊字符
description: 了解使用 Visual Studio 中的 Unicode UTF-8 文件格式对特殊字符进行编码的语法，以便在 Windows Presentation Foundation 中的 XAML 文件中使用。
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: ac2388fd96aa26ddd99408ac9f847ce517958568
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168363"
---
# <a name="how-to-use-special-characters-in-xaml"></a>如何：在 XAML 中使用特殊字符
在 Visual Studio 中创建的标记文件将自动保存为 Unicode UTF-8 文件格式，这意味着，最特殊的字符（如重音符号）已正确编码。 但是，有一组常用特殊字符的处理方式不同。 这些特殊字符遵循用于编码的万维网联合会（W3C） XML 标准。  
  
 下表显示这组特殊字符的编码语法：  
  
|字符|语法|说明|  
|---------------|------------|-----------------|  
|<|`&lt;`|小于符号。|  
|>|`&gt;`|大于符号。|  
|&|`&amp;`|& 符号。|  
|"|`&quot;`|双引号。|  
  
> [!NOTE]
> 如果使用文本编辑器（如 Windows 记事本）创建标记文件，则必须将该文件保存为 Unicode UTF-8 文件格式，以便保留所有编码的特殊字符。  
  
 以下示例演示创建标记时如何在文本中使用特殊字符。  
  
## <a name="example"></a>示例  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
