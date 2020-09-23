---
title: 代码中的特殊字符
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 60f815f0d30fa785f4a2166db5a041d3851aa954
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097821"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="876c5-102">代码中的特殊字符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="876c5-102">Special Characters in Code (Visual Basic)</span></span>

<span data-ttu-id="876c5-103">有时，您必须在代码中使用特殊字符，即不是字母或数字的字符。</span><span class="sxs-lookup"><span data-stu-id="876c5-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="876c5-104">Visual Basic 字符集中的标点和特殊字符具有多种用途，从组织程序文本到定义编译器或已编译程序所执行的任务。</span><span class="sxs-lookup"><span data-stu-id="876c5-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="876c5-105">它们不指定要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="876c5-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="876c5-106">括号</span><span class="sxs-lookup"><span data-stu-id="876c5-106">Parentheses</span></span>  

 <span data-ttu-id="876c5-107">定义过程（如或）时，请使用括号 `Sub` `Function` 。</span><span class="sxs-lookup"><span data-stu-id="876c5-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="876c5-108">必须将所有过程参数列表括在括号中。</span><span class="sxs-lookup"><span data-stu-id="876c5-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="876c5-109">还可以使用括号将变量或参数置于逻辑组中，特别是在复杂表达式中覆盖运算符优先级的默认顺序。</span><span class="sxs-lookup"><span data-stu-id="876c5-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="876c5-110">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="876c5-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="876c5-111">执行前面的代码后，的值 `d` 为8.225，值为 `e` 3。</span><span class="sxs-lookup"><span data-stu-id="876c5-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="876c5-112">的计算 `d` 使用的默认优先级为 " `/` over" `+` ，等效于 `d = b + (c / a)` 。</span><span class="sxs-lookup"><span data-stu-id="876c5-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="876c5-113">计算中的括号用于 `e` 重写默认优先级。</span><span class="sxs-lookup"><span data-stu-id="876c5-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="876c5-114">分隔器</span><span class="sxs-lookup"><span data-stu-id="876c5-114">Separators</span></span>  

 <span data-ttu-id="876c5-115">分隔符可执行其名称建议：它们分隔代码段。</span><span class="sxs-lookup"><span data-stu-id="876c5-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="876c5-116">在 Visual Basic 中，分隔符为冒号 (`:`) 。</span><span class="sxs-lookup"><span data-stu-id="876c5-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="876c5-117">如果要在单个行而不是单独的行中包含多个语句，请使用分隔符。</span><span class="sxs-lookup"><span data-stu-id="876c5-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="876c5-118">这样可以节省空间，并可提高代码的可读性。</span><span class="sxs-lookup"><span data-stu-id="876c5-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="876c5-119">下面的示例显示了以冒号分隔的三个语句。</span><span class="sxs-lookup"><span data-stu-id="876c5-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="876c5-120">有关详细信息，请参阅 [如何：在代码中中断和组合语句](how-to-break-and-combine-statements-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="876c5-120">For more information, see [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="876c5-121">冒号 (`:`) 字符还用于标识语句标签。</span><span class="sxs-lookup"><span data-stu-id="876c5-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="876c5-122">有关详细信息，请参阅 [如何：标签语句](how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="876c5-122">For more information, see [How to: Label Statements](how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="876c5-123">串联</span><span class="sxs-lookup"><span data-stu-id="876c5-123">Concatenation</span></span>  

 <span data-ttu-id="876c5-124">使用 `&` 运算符进行 *串联*，或将字符串链接在一起。</span><span class="sxs-lookup"><span data-stu-id="876c5-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="876c5-125">不要将其与运算符混淆 `+` ，后者将数值相加。</span><span class="sxs-lookup"><span data-stu-id="876c5-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="876c5-126">如果在 `+` 操作数值时使用运算符进行连接，则可以获得不正确的结果。</span><span class="sxs-lookup"><span data-stu-id="876c5-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="876c5-127">下面的示例演示这一操作。</span><span class="sxs-lookup"><span data-stu-id="876c5-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="876c5-128">执行前面的代码后，的值 `resultA` 为21.01，值为 `resultB` "10.0111"。</span><span class="sxs-lookup"><span data-stu-id="876c5-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="876c5-129">成员访问运算符</span><span class="sxs-lookup"><span data-stu-id="876c5-129">Member Access Operators</span></span>  

 <span data-ttu-id="876c5-130">若要访问类型的成员，请使用点 (`.`) 或感叹号 (`!` 类型名称和成员名称之间的) 运算符。</span><span class="sxs-lookup"><span data-stu-id="876c5-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="876c5-131"> ( ) 运算符</span><span class="sxs-lookup"><span data-stu-id="876c5-131">Dot (.) Operator</span></span>  

 <span data-ttu-id="876c5-132">`.`在类、结构、接口或枚举上使用运算符作为成员访问运算符。</span><span class="sxs-lookup"><span data-stu-id="876c5-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="876c5-133">成员可以是字段、属性、事件或方法。</span><span class="sxs-lookup"><span data-stu-id="876c5-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="876c5-134">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="876c5-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="876c5-135">感叹号 (！ ) 运算符</span><span class="sxs-lookup"><span data-stu-id="876c5-135">Exclamation Point (!) Operator</span></span>  

 <span data-ttu-id="876c5-136">`!`仅在类或接口上将运算符用作字典访问运算符。</span><span class="sxs-lookup"><span data-stu-id="876c5-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="876c5-137">类或接口必须具有接受单个参数的默认属性 `String` 。</span><span class="sxs-lookup"><span data-stu-id="876c5-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="876c5-138">紧跟在运算符后面的标识符 `!` 将成为作为字符串传递到默认属性的参数值。</span><span class="sxs-lookup"><span data-stu-id="876c5-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="876c5-139">下面的示例演示这一操作。</span><span class="sxs-lookup"><span data-stu-id="876c5-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="876c5-140">所有的三个输出行 `MsgBox` 都显示值 `32856` 。</span><span class="sxs-lookup"><span data-stu-id="876c5-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="876c5-141">第一行使用对属性的传统访问 `index` ，第二行使用 `index` 作为类的默认属性的事实 `hasDefault` ，第三行使用对类的字典访问。</span><span class="sxs-lookup"><span data-stu-id="876c5-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="876c5-142">请注意，运算符的第二个操作数 `!` 必须是一个有效的 Visual Basic 标识符，不能用双引号引起来 (`" "`) 。</span><span class="sxs-lookup"><span data-stu-id="876c5-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="876c5-143">换句话说，您不能使用字符串文本或字符串变量。</span><span class="sxs-lookup"><span data-stu-id="876c5-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="876c5-144">对于调用的最后一行，以下更改将 `MsgBox` 生成错误，因为 `"X"` 是括起来的字符串文字。</span><span class="sxs-lookup"><span data-stu-id="876c5-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="876c5-145">对默认集合的引用必须是显式的。</span><span class="sxs-lookup"><span data-stu-id="876c5-145">References to default collections must be explicit.</span></span> <span data-ttu-id="876c5-146">特别是，不能 `!` 对后期绑定变量使用运算符。</span><span class="sxs-lookup"><span data-stu-id="876c5-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="876c5-147">该 `!` 字符还用作 `Single` 类型字符。</span><span class="sxs-lookup"><span data-stu-id="876c5-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876c5-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="876c5-148">See also</span></span>

- [<span data-ttu-id="876c5-149">程序结构和代码约定</span><span class="sxs-lookup"><span data-stu-id="876c5-149">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="876c5-150">类型字符</span><span class="sxs-lookup"><span data-stu-id="876c5-150">Type Characters</span></span>](../language-features/data-types/type-characters.md)
