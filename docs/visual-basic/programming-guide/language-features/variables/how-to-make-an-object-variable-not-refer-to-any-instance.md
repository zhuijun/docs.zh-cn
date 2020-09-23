---
title: 如何：使对象变量不引用任何实例
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 61bb06401ebd1e479c9256a80a12d87240831063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080247"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="8b45d-102">如何：使对象变量不引用任何实例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b45d-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>

<span data-ttu-id="8b45d-103">您可以通过将对象变量设置为 " [无](../../../language-reference/nothing.md)" 来解除对象变量与任何对象实例的关联。</span><span class="sxs-lookup"><span data-stu-id="8b45d-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="8b45d-104">断开对象变量与任何对象实例的关联</span><span class="sxs-lookup"><span data-stu-id="8b45d-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="8b45d-105">`Nothing`在赋值语句中将变量设置为。</span><span class="sxs-lookup"><span data-stu-id="8b45d-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="8b45d-106">可靠编程</span><span class="sxs-lookup"><span data-stu-id="8b45d-106">Robust Programming</span></span>  

 <span data-ttu-id="8b45d-107">如果你的代码尝试访问已设置为的对象变量的成员 `Nothing` ，则 <xref:System.NullReferenceException> 会发生。</span><span class="sxs-lookup"><span data-stu-id="8b45d-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="8b45d-108">如果将一个对象变量设置为 `Nothing` "频繁"，或者如果可能该变量未初始化，则最好将成员访问包含在 `Try...Catch...Finally` 块中。</span><span class="sxs-lookup"><span data-stu-id="8b45d-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8b45d-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="8b45d-109">.NET Framework Security</span></span>  

 <span data-ttu-id="8b45d-110">如果对包含机密数据或敏感数据的对象使用对象变量，则可以将变量设置为，以便在 `Nothing` 不主动处理其中一个对象时使用。</span><span class="sxs-lookup"><span data-stu-id="8b45d-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="8b45d-111">这减少了恶意代码访问数据的可能性。</span><span class="sxs-lookup"><span data-stu-id="8b45d-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b45d-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="8b45d-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="8b45d-113">对象变量</span><span class="sxs-lookup"><span data-stu-id="8b45d-113">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="8b45d-114">对象变量赋值</span><span class="sxs-lookup"><span data-stu-id="8b45d-114">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="8b45d-115">没</span><span class="sxs-lookup"><span data-stu-id="8b45d-115">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="8b45d-116">尝试 .。。Catch .。。Finally 语句</span><span class="sxs-lookup"><span data-stu-id="8b45d-116">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
