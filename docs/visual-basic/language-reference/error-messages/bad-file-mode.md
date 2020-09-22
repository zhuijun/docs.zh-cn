---
title: 错误的文件模式
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 99b84902ddf032f2ecb6e26400e200bea862dfdf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875145"
---
# <a name="bad-file-mode"></a><span data-ttu-id="f85f2-102">错误的文件模式</span><span class="sxs-lookup"><span data-stu-id="f85f2-102">Bad file mode</span></span>

<span data-ttu-id="f85f2-103">用于操作文件内容的语句必须适合于打开该文件的模式。</span><span class="sxs-lookup"><span data-stu-id="f85f2-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="f85f2-104">可能的原因包括：</span><span class="sxs-lookup"><span data-stu-id="f85f2-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="f85f2-105">`FilePutObject`或 `FileGetObject` 语句指定顺序文件。</span><span class="sxs-lookup"><span data-stu-id="f85f2-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="f85f2-106">`Print`语句指定了一个打开的文件，该文件用于访问模式，而不是 `Output` 或 `Append` 。</span><span class="sxs-lookup"><span data-stu-id="f85f2-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="f85f2-107">`Input`语句指定为访问模式打开的文件，而不是`Input`</span><span class="sxs-lookup"><span data-stu-id="f85f2-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="f85f2-108">尝试写入只读文件。</span><span class="sxs-lookup"><span data-stu-id="f85f2-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f85f2-109">更正此错误</span><span class="sxs-lookup"><span data-stu-id="f85f2-109">To correct this error</span></span>  
  
- <span data-ttu-id="f85f2-110">请确保 `FilePutObject` 和 `FileGetObject` 仅引用打开的 `Random` 或访问的文件 `Binary` 。</span><span class="sxs-lookup"><span data-stu-id="f85f2-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="f85f2-111">请确保 `Print` 为 `Output` 或访问模式指定打开的文件 `Append` 。</span><span class="sxs-lookup"><span data-stu-id="f85f2-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="f85f2-112">否则，请使用不同的语句将数据放置在文件中，或在适当的模式下重新打开文件。</span><span class="sxs-lookup"><span data-stu-id="f85f2-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="f85f2-113">请确保 `Input` 指定一个打开的文件 `Input` 。</span><span class="sxs-lookup"><span data-stu-id="f85f2-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="f85f2-114">否则，请使用不同的语句将数据放置在文件中，或在适当的模式下重新打开文件。</span><span class="sxs-lookup"><span data-stu-id="f85f2-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="f85f2-115">如果要写入只读文件，请更改该文件的读/写状态，或不要尝试写入该文件。</span><span class="sxs-lookup"><span data-stu-id="f85f2-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="f85f2-116">使用 `My.Computer.FileSystem` 对象中的可用功能。</span><span class="sxs-lookup"><span data-stu-id="f85f2-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85f2-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f85f2-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="f85f2-118">疑难解答：读取和写入文本文件</span><span class="sxs-lookup"><span data-stu-id="f85f2-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
