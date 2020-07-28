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
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="3cec0-103">如何：在 XAML 中使用特殊字符</span><span class="sxs-lookup"><span data-stu-id="3cec0-103">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="3cec0-104">在 Visual Studio 中创建的标记文件将自动保存为 Unicode UTF-8 文件格式，这意味着，最特殊的字符（如重音符号）已正确编码。</span><span class="sxs-lookup"><span data-stu-id="3cec0-104">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="3cec0-105">但是，有一组常用特殊字符的处理方式不同。</span><span class="sxs-lookup"><span data-stu-id="3cec0-105">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="3cec0-106">这些特殊字符遵循用于编码的万维网联合会（W3C） XML 标准。</span><span class="sxs-lookup"><span data-stu-id="3cec0-106">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="3cec0-107">下表显示这组特殊字符的编码语法：</span><span class="sxs-lookup"><span data-stu-id="3cec0-107">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="3cec0-108">字符</span><span class="sxs-lookup"><span data-stu-id="3cec0-108">Character</span></span>|<span data-ttu-id="3cec0-109">语法</span><span class="sxs-lookup"><span data-stu-id="3cec0-109">Syntax</span></span>|<span data-ttu-id="3cec0-110">说明</span><span class="sxs-lookup"><span data-stu-id="3cec0-110">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="3cec0-111">小于符号。</span><span class="sxs-lookup"><span data-stu-id="3cec0-111">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="3cec0-112">大于符号。</span><span class="sxs-lookup"><span data-stu-id="3cec0-112">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="3cec0-113">& 符号。</span><span class="sxs-lookup"><span data-stu-id="3cec0-113">Ampersand symbol.</span></span>|  
|<span data-ttu-id="3cec0-114">"</span><span class="sxs-lookup"><span data-stu-id="3cec0-114">"</span></span>|`&quot;`|<span data-ttu-id="3cec0-115">双引号。</span><span class="sxs-lookup"><span data-stu-id="3cec0-115">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3cec0-116">如果使用文本编辑器（如 Windows 记事本）创建标记文件，则必须将该文件保存为 Unicode UTF-8 文件格式，以便保留所有编码的特殊字符。</span><span class="sxs-lookup"><span data-stu-id="3cec0-116">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="3cec0-117">以下示例演示创建标记时如何在文本中使用特殊字符。</span><span class="sxs-lookup"><span data-stu-id="3cec0-117">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cec0-118">示例</span><span class="sxs-lookup"><span data-stu-id="3cec0-118">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
