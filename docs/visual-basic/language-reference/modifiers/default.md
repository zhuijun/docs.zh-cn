---
title: 默认
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: bc213c3b5564d1833136df8f5b8dab1c6b012296
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875487"
---
# <a name="default-visual-basic"></a><span data-ttu-id="8e2c9-102">Default (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e2c9-102">Default (Visual Basic)</span></span>

<span data-ttu-id="8e2c9-103">将属性标识为其类、结构或接口的默认属性。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e2c9-104">备注</span><span class="sxs-lookup"><span data-stu-id="8e2c9-104">Remarks</span></span>  

 <span data-ttu-id="8e2c9-105">类、结构或接口最多可以将其一个属性指定为 *默认属性*，前提是该属性至少采用一个参数。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="8e2c9-106">如果代码在未指定成员的情况下对类或结构进行引用，则 Visual Basic 解析对默认属性的引用。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="8e2c9-107">默认属性可能会减少源代码中的字符，但会使代码更难以阅读。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="8e2c9-108">如果调用代码不熟悉你的类或结构，则当它对类或结构名称进行引用时，该引用是否访问类或结构本身，或者默认属性，则不能确定这一点。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="8e2c9-109">这可能会导致编译器错误或细微的运行时逻辑错误。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="8e2c9-110">通过始终使用 [Option Strict 语句](../statements/option-strict-statement.md) 将编译器类型检查设置为，可以在一定程度上减少默认属性错误的几率 `On` 。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="8e2c9-111">如果打算在代码中使用预定义的类或结构，则必须确定它是否具有默认属性，如果是，则必须确定其名称。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="8e2c9-112">由于这些缺点，你应考虑不要定义默认属性。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="8e2c9-113">为实现代码可读性，还应考虑始终显式引用所有属性，甚至是默认属性。</span><span class="sxs-lookup"><span data-stu-id="8e2c9-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="8e2c9-114">`Default`可以在此上下文中使用修饰符：</span><span class="sxs-lookup"><span data-stu-id="8e2c9-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="8e2c9-115">Property Statement</span><span class="sxs-lookup"><span data-stu-id="8e2c9-115">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8e2c9-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e2c9-116">See also</span></span>

- [<span data-ttu-id="8e2c9-117">如何：在 Visual Basic 中声明和调用默认属性</span><span class="sxs-lookup"><span data-stu-id="8e2c9-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="8e2c9-118">关键字</span><span class="sxs-lookup"><span data-stu-id="8e2c9-118">Keywords</span></span>](../keywords/index.md)
