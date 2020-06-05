---
title: 编码不能设置为 Nothing。
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 41565d1aa3b69f6ad92d4bbf2b2f2170014aef87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394474"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="193d9-102">编码不能设置为 Nothing。</span><span class="sxs-lookup"><span data-stu-id="193d9-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="193d9-103">尝试读取或写入文件失败，因为已将参数 `encoding` 设置为 `Nothing` ，但需要有效值。</span><span class="sxs-lookup"><span data-stu-id="193d9-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="193d9-104"><xref:System.Text.Encoding> 用于确定写入文件时使用何种编码。</span><span class="sxs-lookup"><span data-stu-id="193d9-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="193d9-105">默认为 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="193d9-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="193d9-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="193d9-106">To correct this error</span></span>  
  
- <span data-ttu-id="193d9-107">为 `encoding` 参数提供有效值。</span><span class="sxs-lookup"><span data-stu-id="193d9-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193d9-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="193d9-108">See also</span></span>

- [<span data-ttu-id="193d9-109">文件编码</span><span class="sxs-lookup"><span data-stu-id="193d9-109">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="193d9-110">从文件读取</span><span class="sxs-lookup"><span data-stu-id="193d9-110">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="193d9-111">写入文件</span><span class="sxs-lookup"><span data-stu-id="193d9-111">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="193d9-112">文件 System.io.file.readalltext</span><span class="sxs-lookup"><span data-stu-id="193d9-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="193d9-113">文件 Microsoft.visualbasic.fileio.filesystem.writealltext</span><span class="sxs-lookup"><span data-stu-id="193d9-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
