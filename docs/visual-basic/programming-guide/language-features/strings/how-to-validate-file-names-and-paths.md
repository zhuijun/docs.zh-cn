---
title: 如何：验证文件名和路径
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: b722222ea8b8088a6b326eef27147c08f8419272
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072647"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="64c70-102">如何：在 Visual Basic 中验证文件名和路径</span><span class="sxs-lookup"><span data-stu-id="64c70-102">How to: Validate File Names and Paths in Visual Basic</span></span>

<span data-ttu-id="64c70-103">此示例返回一个 `Boolean` 值，该值指示字符串是否表示文件名或路径。</span><span class="sxs-lookup"><span data-stu-id="64c70-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="64c70-104">验证检查名称是否包含文件系统不允许使用的字符。</span><span class="sxs-lookup"><span data-stu-id="64c70-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64c70-105">示例</span><span class="sxs-lookup"><span data-stu-id="64c70-105">Example</span></span>  

 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="64c70-106">此示例不检查名称是否错误地放置了冒号或没有名称的目录，或者名称长度是否超过了系统定义的最大长度。</span><span class="sxs-lookup"><span data-stu-id="64c70-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="64c70-107">它也不会检查应用程序是否有权访问具有指定名称的文件系统资源。</span><span class="sxs-lookup"><span data-stu-id="64c70-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64c70-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="64c70-108">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="64c70-109">验证字符串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64c70-109">Validating Strings in Visual Basic</span></span>](validating-strings.md)
