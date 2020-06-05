---
title: 二元“If”表达式中的第一个操作数必须是可以为 null 的类型或引用类型
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: ca16c6604ee071668a5c65d7e9052b233e2313c7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403013"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="5510e-102">二元“If”表达式中的第一个操作数必须是可以为 null 的类型或引用类型</span><span class="sxs-lookup"><span data-stu-id="5510e-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="5510e-103">`If`表达式可以采用两个或三个参数。</span><span class="sxs-lookup"><span data-stu-id="5510e-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="5510e-104">当只发送两个参数时，第一个参数必须是引用类型或可以为 null 的值类型。</span><span class="sxs-lookup"><span data-stu-id="5510e-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="5510e-105">如果第一个参数的计算结果不是 `Nothing` ，则返回其值。</span><span class="sxs-lookup"><span data-stu-id="5510e-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="5510e-106">如果第一个参数的计算结果为 `Nothing` ，则计算并返回第二个参数。</span><span class="sxs-lookup"><span data-stu-id="5510e-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="5510e-107">例如，下面的代码包含两个 `If` 表达式，一个具有三个参数，一个具有两个参数。</span><span class="sxs-lookup"><span data-stu-id="5510e-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="5510e-108">表达式计算并返回相同的值。</span><span class="sxs-lookup"><span data-stu-id="5510e-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="5510e-109">以下表达式将导致此错误：</span><span class="sxs-lookup"><span data-stu-id="5510e-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="5510e-110">**错误 ID：** BC33107</span><span class="sxs-lookup"><span data-stu-id="5510e-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5510e-111">更正此错误</span><span class="sxs-lookup"><span data-stu-id="5510e-111">To correct this error</span></span>  
  
- <span data-ttu-id="5510e-112">如果无法更改代码，使第一个参数是可以为 null 的值类型或引用类型，请考虑将转换为三参数 `If` 表达式或 `If...Then...Else` 语句。</span><span class="sxs-lookup"><span data-stu-id="5510e-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="5510e-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5510e-113">See also</span></span>

- [<span data-ttu-id="5510e-114">If 运算符</span><span class="sxs-lookup"><span data-stu-id="5510e-114">If Operator</span></span>](../operators/if-operator.md)
- [<span data-ttu-id="5510e-115">If...Then...Else 语句</span><span class="sxs-lookup"><span data-stu-id="5510e-115">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="5510e-116">可以为 null 的值类型</span><span class="sxs-lookup"><span data-stu-id="5510e-116">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
