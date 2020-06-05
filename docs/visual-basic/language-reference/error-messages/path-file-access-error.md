---
title: 路径/文件访问错误
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: dfe96cd6eaa673438849fe8f799d46fa2617bfdd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387252"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="a57e1-102">路径/文件访问错误</span><span class="sxs-lookup"><span data-stu-id="a57e1-102">Path/File access error</span></span>
<span data-ttu-id="a57e1-103">在文件访问或磁盘访问操作期间，操作系统无法在路径和文件名之间建立连接。</span><span class="sxs-lookup"><span data-stu-id="a57e1-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a57e1-104">更正此错误</span><span class="sxs-lookup"><span data-stu-id="a57e1-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a57e1-105">请确保文件规范格式正确。</span><span class="sxs-lookup"><span data-stu-id="a57e1-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="a57e1-106">文件名可以包含完全限定的（绝对）或相对路径。</span><span class="sxs-lookup"><span data-stu-id="a57e1-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="a57e1-107">完全限定的路径以驱动器名称开头（如果路径位于另一个驱动器上），并列出从根到文件的显式路径。</span><span class="sxs-lookup"><span data-stu-id="a57e1-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="a57e1-108">未完全限定的任何路径都是相对于当前驱动器和目录的路径。</span><span class="sxs-lookup"><span data-stu-id="a57e1-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="a57e1-109">请确保未尝试保存将替换现有只读文件的文件。</span><span class="sxs-lookup"><span data-stu-id="a57e1-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="a57e1-110">如果是这种情况，请更改目标文件的只读属性，或使用不同的文件名保存该文件。</span><span class="sxs-lookup"><span data-stu-id="a57e1-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="a57e1-111">请确保未尝试按顺序或模式打开只读文件 `Output` `Append` 。</span><span class="sxs-lookup"><span data-stu-id="a57e1-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="a57e1-112">如果是这种情况，请在模式下打开该文件 `Input` 或更改该文件的只读属性。</span><span class="sxs-lookup"><span data-stu-id="a57e1-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="a57e1-113">请确保未尝试在数据库或文档中更改 Visual Basic 项目。</span><span class="sxs-lookup"><span data-stu-id="a57e1-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a57e1-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a57e1-114">See also</span></span>

- [<span data-ttu-id="a57e1-115">错误类型</span><span class="sxs-lookup"><span data-stu-id="a57e1-115">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
