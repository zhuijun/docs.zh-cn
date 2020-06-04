---
title: 确定对象类型
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 3b1c4ad0ab4fd8d2897aff6ad9097cdc81272455
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410639"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="4ce1b-102">确定对象类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ce1b-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="4ce1b-103">泛型对象变量（即声明为的变量 `Object` ）可以包含任何类中的对象。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="4ce1b-104">使用类型的变量时 `Object` ，可能需要根据对象的类执行不同的操作; 例如，某些对象可能不支持特定的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="4ce1b-105">Visual Basic 提供了两种方法来确定存储在对象变量中的对象类型： `TypeName` 函数和 `TypeOf...Is` 运算符。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="4ce1b-106">TypeName 和 TypeOf .。。未</span><span class="sxs-lookup"><span data-stu-id="4ce1b-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="4ce1b-107">`TypeName`如果需要存储或显示对象的类名，则函数返回一个字符串，是最佳选择，如以下代码片段所示：</span><span class="sxs-lookup"><span data-stu-id="4ce1b-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="4ce1b-108">`TypeOf...Is`运算符是测试对象类型的最佳选择，因为它比使用等效的字符串比较快得多 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="4ce1b-109">以下代码片段 `TypeOf...Is` 在语句中使用 `If...Then...Else` ：</span><span class="sxs-lookup"><span data-stu-id="4ce1b-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="4ce1b-110">此处有一则注意事项。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-110">A word of caution is due here.</span></span> <span data-ttu-id="4ce1b-111">`TypeOf...Is` `True` 如果对象是特定类型的，或派生自特定类型，则运算符返回。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="4ce1b-112">几乎对 Visual Basic 所做的一切都涉及对象，这些对象包括通常不会视为对象的某些元素，如字符串和整数。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="4ce1b-113">这些对象派生自，并从继承方法 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="4ce1b-114">当向传递 `Integer` 并使用计算时 `Object` ， `TypeOf...Is` 运算符将返回 `True` 。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="4ce1b-115">下面的示例报告参数 `InParam` 既是 `Object` 又是 `Integer` ：</span><span class="sxs-lookup"><span data-stu-id="4ce1b-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="4ce1b-116">下面的示例使用 `TypeOf...Is` 和 `TypeName` 来确定参数中传递给它的对象的类型 `Ctrl` 。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="4ce1b-117">此 `TestObject` 过程调用 `ShowType` 了三种不同类型的控件。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="4ce1b-118">运行示例</span><span class="sxs-lookup"><span data-stu-id="4ce1b-118">To run the example</span></span>  
  
1. <span data-ttu-id="4ce1b-119">创建新的 Windows 应用程序项目，并向 <xref:System.Windows.Forms.Button> 窗体添加控件、 <xref:System.Windows.Forms.CheckBox> 控件和 <xref:System.Windows.Forms.RadioButton> 控件。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="4ce1b-120">在窗体上的按钮中，调用 `TestObject` 过程。</span><span class="sxs-lookup"><span data-stu-id="4ce1b-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="4ce1b-121">将以下代码添加到你的窗体：</span><span class="sxs-lookup"><span data-stu-id="4ce1b-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="4ce1b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ce1b-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="4ce1b-123">使用字符串名调用属性或方法</span><span class="sxs-lookup"><span data-stu-id="4ce1b-123">Calling a Property or Method Using a String Name</span></span>](calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="4ce1b-124">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="4ce1b-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="4ce1b-125">If...Then...Else 语句</span><span class="sxs-lookup"><span data-stu-id="4ce1b-125">If...Then...Else Statement</span></span>](../../../language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="4ce1b-126">String 数据类型</span><span class="sxs-lookup"><span data-stu-id="4ce1b-126">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="4ce1b-127">Integer 数据类型</span><span class="sxs-lookup"><span data-stu-id="4ce1b-127">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)
