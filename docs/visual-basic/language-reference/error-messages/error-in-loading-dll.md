---
title: 加载 DLL 时出错
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409617"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="083b9-102">加载 DLL 时出错 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="083b9-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="083b9-103">动态链接库（DLL）是语句的子句中指定的库 `Lib` `Declare` 。</span><span class="sxs-lookup"><span data-stu-id="083b9-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="083b9-104">此错误的可能原因包括：</span><span class="sxs-lookup"><span data-stu-id="083b9-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="083b9-105">该文件不是 DLL 可执行文件。</span><span class="sxs-lookup"><span data-stu-id="083b9-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="083b9-106">该文件不是 Microsoft Windows DLL。</span><span class="sxs-lookup"><span data-stu-id="083b9-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="083b9-107">DLL 引用了不存在的另一个 DLL。</span><span class="sxs-lookup"><span data-stu-id="083b9-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="083b9-108">DLL 或被引用的 DLL 不在路径中指定的目录中。</span><span class="sxs-lookup"><span data-stu-id="083b9-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="083b9-109">更正此错误</span><span class="sxs-lookup"><span data-stu-id="083b9-109">To correct this error</span></span>  
  
- <span data-ttu-id="083b9-110">如果该文件是源文本文件而不是 DLL 可执行文件，则必须对其进行编译并将其链接到 DLL 可执行文件形式。</span><span class="sxs-lookup"><span data-stu-id="083b9-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="083b9-111">如果文件不是 Microsoft Windows DLL，请获取 Microsoft Windows 等效项。</span><span class="sxs-lookup"><span data-stu-id="083b9-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="083b9-112">如果 DLL 引用了不存在的另一个 DLL，则获取被引用的 DLL 并使其可用。</span><span class="sxs-lookup"><span data-stu-id="083b9-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="083b9-113">如果 DLL 或被引用的 DLL 不在路径所指定的目录中，则将 DLL 移到引用的目录。</span><span class="sxs-lookup"><span data-stu-id="083b9-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083b9-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="083b9-114">See also</span></span>

- [<span data-ttu-id="083b9-115">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="083b9-115">Declare Statement</span></span>](../statements/declare-statement.md)
