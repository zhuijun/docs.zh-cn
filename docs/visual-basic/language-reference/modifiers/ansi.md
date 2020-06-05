---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 67792e52c21555bef46548e9ab0a6ebd32061071
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373195"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="5318c-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5318c-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="5318c-103">指定 Visual Basic 应将所有字符串封送到美国国家标准学会（ANSI）值，而不考虑所声明的外部过程的名称。</span><span class="sxs-lookup"><span data-stu-id="5318c-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="5318c-104">调用在项目外部定义的过程时，Visual Basic 编译器无法访问正确调用过程所需的信息。</span><span class="sxs-lookup"><span data-stu-id="5318c-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="5318c-105">此信息包括过程的位置、标识方法、调用序列和返回类型，以及它使用的字符串字符集。</span><span class="sxs-lookup"><span data-stu-id="5318c-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="5318c-106">[Declare 语句](../statements/declare-statement.md)创建对外部过程的引用并提供此必要信息。</span><span class="sxs-lookup"><span data-stu-id="5318c-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="5318c-107">`charsetmodifier`语句中的部分 `Declare` 提供在调用外部过程期间封送处理字符串的字符集信息。</span><span class="sxs-lookup"><span data-stu-id="5318c-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="5318c-108">它还会影响 Visual Basic 搜索外部文件的外部过程名称的方式。</span><span class="sxs-lookup"><span data-stu-id="5318c-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="5318c-109">`Ansi`修饰符指定 Visual Basic 应将所有字符串封送为 ANSI 值，并在搜索过程中查找该过程而不修改其名称。</span><span class="sxs-lookup"><span data-stu-id="5318c-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="5318c-110">如果未指定字符集修饰符， `Ansi` 则默认为。</span><span class="sxs-lookup"><span data-stu-id="5318c-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5318c-111">备注</span><span class="sxs-lookup"><span data-stu-id="5318c-111">Remarks</span></span>  
 <span data-ttu-id="5318c-112">`Ansi`可以在此上下文中使用修饰符：</span><span class="sxs-lookup"><span data-stu-id="5318c-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="5318c-113">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="5318c-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="5318c-114">智能设备开发人员说明</span><span class="sxs-lookup"><span data-stu-id="5318c-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="5318c-115">不支持此关键字。</span><span class="sxs-lookup"><span data-stu-id="5318c-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5318c-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5318c-116">See also</span></span>

- [<span data-ttu-id="5318c-117">自动</span><span class="sxs-lookup"><span data-stu-id="5318c-117">Auto</span></span>](auto.md)
- [<span data-ttu-id="5318c-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="5318c-118">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="5318c-119">关键字</span><span class="sxs-lookup"><span data-stu-id="5318c-119">Keywords</span></span>](../keywords/index.md)
