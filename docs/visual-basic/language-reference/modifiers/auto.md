---
title: 自动
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 799a7320b701384dc5f4b4b46fef8544f6b15b02
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875509"
---
# <a name="auto-visual-basic"></a><span data-ttu-id="506ed-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="506ed-102">Auto (Visual Basic)</span></span>

<span data-ttu-id="506ed-103">指定 Visual Basic 应根据正在声明的外部过程的外部名称按 .NET Framework 规则封送字符串。</span><span class="sxs-lookup"><span data-stu-id="506ed-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="506ed-104">调用在项目外部定义的过程时，Visual Basic 编译器不能访问正确调用过程所必须具有的信息。</span><span class="sxs-lookup"><span data-stu-id="506ed-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="506ed-105">此信息包括过程的位置、标识方法、调用序列和返回类型，以及它使用的字符串字符集。</span><span class="sxs-lookup"><span data-stu-id="506ed-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="506ed-106">[Declare 语句](../statements/declare-statement.md)创建对外部过程的引用并提供此必要信息。</span><span class="sxs-lookup"><span data-stu-id="506ed-106">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="506ed-107">`charsetmodifier`语句中的部分 `Declare` 提供在调用外部过程期间封送处理字符串的字符集信息。</span><span class="sxs-lookup"><span data-stu-id="506ed-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="506ed-108">它还会影响 Visual Basic 搜索外部文件的外部过程名称的方式。</span><span class="sxs-lookup"><span data-stu-id="506ed-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="506ed-109">`Auto`修饰符指定 Visual Basic 应根据 .NET Framework 规则封送字符串，并且应确定运行时平台的基本字符集，并可能在初始搜索失败时修改外部过程名称。</span><span class="sxs-lookup"><span data-stu-id="506ed-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="506ed-110">有关详细信息，请参阅 [Declare 语句](../statements/declare-statement.md)中的 "字符集"。</span><span class="sxs-lookup"><span data-stu-id="506ed-110">For more information, see "Character Sets" in [Declare Statement](../statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="506ed-111">如果未指定字符集修饰符， `Ansi` 则默认为。</span><span class="sxs-lookup"><span data-stu-id="506ed-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="506ed-112">备注</span><span class="sxs-lookup"><span data-stu-id="506ed-112">Remarks</span></span>  

 <span data-ttu-id="506ed-113">`Auto`可以在此上下文中使用修饰符：</span><span class="sxs-lookup"><span data-stu-id="506ed-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="506ed-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="506ed-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="506ed-115">智能设备开发人员说明</span><span class="sxs-lookup"><span data-stu-id="506ed-115">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="506ed-116">不支持此关键字。</span><span class="sxs-lookup"><span data-stu-id="506ed-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506ed-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="506ed-117">See also</span></span>

- [<span data-ttu-id="506ed-118">适应</span><span class="sxs-lookup"><span data-stu-id="506ed-118">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="506ed-119">Unicode</span><span class="sxs-lookup"><span data-stu-id="506ed-119">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="506ed-120">关键字</span><span class="sxs-lookup"><span data-stu-id="506ed-120">Keywords</span></span>](../keywords/index.md)
