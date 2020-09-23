---
title: 参数 BasePath 必须是一个文件夹的路径
ms.date: 07/20/2015
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
ms.openlocfilehash: 3c8d17db7cc03490ff437c91814db967612942a0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079745"
---
# <a name="argument-basepath-must-be-a-path-to-a-folder"></a><span data-ttu-id="82f8c-102">参数 BasePath 必须是一个文件夹的路径</span><span class="sxs-lookup"><span data-stu-id="82f8c-102">Argument BasePath must be a path to a folder</span></span>

<span data-ttu-id="82f8c-103">参数 `BasePath` 必须包含文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="82f8c-103">The argument `BasePath` must consist of a path to a folder.</span></span> <span data-ttu-id="82f8c-104">你可能会错误地解析字符串，并提供一个未被识别为有效路径的值。</span><span class="sxs-lookup"><span data-stu-id="82f8c-104">You may be parsing a string incorrectly and supplying a value that is not recognized as a valid path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="82f8c-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="82f8c-105">To correct this error</span></span>  
  
- <span data-ttu-id="82f8c-106">检查为 `BasePath` 提供的值，确保它是一个文件夹的有效路径。</span><span class="sxs-lookup"><span data-stu-id="82f8c-106">Check the value you are supplying for `BasePath` to make sure it is a valid path to a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f8c-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="82f8c-107">See also</span></span>

- <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>
- <xref:System.Resources.ResXResourceWriter.BasePath%2A>
- <xref:System.Resources.ResXResourceReader.BasePath%2A>
- [<span data-ttu-id="82f8c-108">如何：分析文件路径</span><span class="sxs-lookup"><span data-stu-id="82f8c-108">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
