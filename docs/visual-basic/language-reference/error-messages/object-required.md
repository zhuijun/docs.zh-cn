---
title: 需要对象
ms.date: 07/20/2015
f1_keywords:
- vbrID424
ms.assetid: afdc660b-81a5-4c92-ac7e-9c3a3105fc16
ms.openlocfilehash: 4e0544ad7d570c31fc4308534b9b5c18b8b431b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409305"
---
# <a name="object-required-visual-basic"></a><span data-ttu-id="753fc-102">需要对象 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="753fc-102">Object required (Visual Basic)</span></span>
<span data-ttu-id="753fc-103">对属性和方法的引用通常需要显式对象限定符。</span><span class="sxs-lookup"><span data-stu-id="753fc-103">References to properties and methods often require an explicit object qualifier.</span></span> <span data-ttu-id="753fc-104">这就是这种情况。</span><span class="sxs-lookup"><span data-stu-id="753fc-104">This is such a case.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="753fc-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="753fc-105">To correct this error</span></span>  
  
1. <span data-ttu-id="753fc-106">检查对对象属性或方法的引用是否具有有效的对象限定符。</span><span class="sxs-lookup"><span data-stu-id="753fc-106">Check that references to an object property or method have valid object qualifier.</span></span> <span data-ttu-id="753fc-107">如果未提供对象限定符，请指定它。</span><span class="sxs-lookup"><span data-stu-id="753fc-107">Specify an object qualifier if you didn't provide one.</span></span>  
  
2. <span data-ttu-id="753fc-108">检查对象限定符的拼写，并确保对象在您引用它的程序部分中可见。</span><span class="sxs-lookup"><span data-stu-id="753fc-108">Check the spelling of the object qualifier and make sure the object is visible in the part of the program in which you are referencing it.</span></span>  
  
3. <span data-ttu-id="753fc-109">如果向宿主应用程序的 "**文件打开**" 命令提供路径，请检查其中的参数是否正确。</span><span class="sxs-lookup"><span data-stu-id="753fc-109">If a path is supplied to a host application's **File Open** command, check that the arguments in it are correct.</span></span>  
  
4. <span data-ttu-id="753fc-110">检查对象的文档，并确保操作有效。</span><span class="sxs-lookup"><span data-stu-id="753fc-110">Check the object's documentation and make sure the action is valid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753fc-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="753fc-111">See also</span></span>

- [<span data-ttu-id="753fc-112">错误类型</span><span class="sxs-lookup"><span data-stu-id="753fc-112">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
