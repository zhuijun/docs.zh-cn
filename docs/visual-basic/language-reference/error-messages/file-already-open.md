---
title: 文件已打开
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874175"
---
# <a name="file-already-open"></a><span data-ttu-id="c9670-102">文件已打开</span><span class="sxs-lookup"><span data-stu-id="c9670-102">File already open</span></span>

<span data-ttu-id="c9670-103">有时，必须先关闭文件，然后才能 `FileOpen` 进行其他或其他操作。</span><span class="sxs-lookup"><span data-stu-id="c9670-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="c9670-104">此错误的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="c9670-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="c9670-105">`FileOpen`为已打开的文件执行了顺序输出模式操作</span><span class="sxs-lookup"><span data-stu-id="c9670-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
- <span data-ttu-id="c9670-106">语句引用打开的文件。</span><span class="sxs-lookup"><span data-stu-id="c9670-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c9670-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="c9670-107">To correct this error</span></span>  
  
1. <span data-ttu-id="c9670-108">在执行语句前关闭文件。</span><span class="sxs-lookup"><span data-stu-id="c9670-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9670-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9670-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
