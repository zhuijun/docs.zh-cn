---
title: 为事件日志指定了无效名称
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 70b1de2a3776a9c68260cc431b65e754d7247a0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412918"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="bd1bd-102">为事件日志指定了无效名称</span><span class="sxs-lookup"><span data-stu-id="bd1bd-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="bd1bd-103">为事件日志指定了无效名称。</span><span class="sxs-lookup"><span data-stu-id="bd1bd-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="bd1bd-104">通常名称中存在无效字符、文件名太长或空白文件名会导致此结果。</span><span class="sxs-lookup"><span data-stu-id="bd1bd-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd1bd-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="bd1bd-105">To correct this error</span></span>  
  
- <span data-ttu-id="bd1bd-106">如果指定的名称多于 8 个字符，请确保与其他事件日志名称之间不存在冲突。</span><span class="sxs-lookup"><span data-stu-id="bd1bd-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="bd1bd-107">当确定名称是否唯一时，将仅计算前八个字符。</span><span class="sxs-lookup"><span data-stu-id="bd1bd-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="bd1bd-108">如果提供路径，请确保它被正确解析。</span><span class="sxs-lookup"><span data-stu-id="bd1bd-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="bd1bd-109">检查此名称中是否不存在任何无效字符。</span><span class="sxs-lookup"><span data-stu-id="bd1bd-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="bd1bd-110">不能在文件名中使用的字符包括 `<`、 `>`、 `:`、 `"`、 `/`、 `\`和 `|`。</span><span class="sxs-lookup"><span data-stu-id="bd1bd-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1bd-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bd1bd-111">See also</span></span>

- [<span data-ttu-id="bd1bd-112">如何：分析文件路径</span><span class="sxs-lookup"><span data-stu-id="bd1bd-112">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="bd1bd-113">如何：重命名文件</span><span class="sxs-lookup"><span data-stu-id="bd1bd-113">How to: Rename a File</span></span>](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
