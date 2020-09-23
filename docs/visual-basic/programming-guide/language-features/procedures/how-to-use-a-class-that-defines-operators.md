---
title: 如何：使用定义运算符的类
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 083916a420bf4ad182536363ea46448f6b4c1da5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071347"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="8a866-102">如何：使用定义运算符的类 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a866-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>

<span data-ttu-id="8a866-103">如果你使用的是定义其自己的运算符的类或结构，则可以从 Visual Basic 访问这些运算符。</span><span class="sxs-lookup"><span data-stu-id="8a866-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="8a866-104">在类或结构上定义运算符也称为 *重载* 运算符。</span><span class="sxs-lookup"><span data-stu-id="8a866-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a866-105">示例</span><span class="sxs-lookup"><span data-stu-id="8a866-105">Example</span></span>  

 <span data-ttu-id="8a866-106">下面的示例访问 SQL 结构，该结构 <xref:System.Data.SqlTypes.SqlString> 定义了在 sql 字符串和 Visual Basic 字符串之间的两个方向 ([CType 函数](../../../language-reference/functions/ctype-function.md)) 的转换运算符。</span><span class="sxs-lookup"><span data-stu-id="8a866-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="8a866-107">使用 `CType(` *sql 字符串表达式*，将 `String)` sql 字符串转换为 Visual Basic 字符串，将 `CType(` *Visual Basic 字符串表达式*转换为 <xref:System.Data.SqlTypes.SqlString> `)` 其他方向。</span><span class="sxs-lookup"><span data-stu-id="8a866-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="8a866-108"><xref:System.Data.SqlTypes.SqlString>结构定义一个转换运算符， ([CType 函数](../../../language-reference/functions/ctype-function.md)) 从 `String` 到 <xref:System.Data.SqlTypes.SqlString> ，另一个从 <xref:System.Data.SqlTypes.SqlString> 到 `String` 。</span><span class="sxs-lookup"><span data-stu-id="8a866-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="8a866-109">赋值的语句 `title` `jobTitle` 使用第一个运算符，而 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函数调用使用第二个运算符。</span><span class="sxs-lookup"><span data-stu-id="8a866-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="8a866-110">编译代码</span><span class="sxs-lookup"><span data-stu-id="8a866-110">Compile the code</span></span>  

 <span data-ttu-id="8a866-111">请确保所用的类或结构定义要使用的运算符。</span><span class="sxs-lookup"><span data-stu-id="8a866-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="8a866-112">不要假设类或结构已定义每个可用于重载的运算符。</span><span class="sxs-lookup"><span data-stu-id="8a866-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="8a866-113">有关可用运算符的列表，请参阅 [Operator 语句](../../../language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8a866-113">For a list of available operators, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="8a866-114">`Imports`在此示例中，将 SQL 字符串的相应语句包含在源文件开头 (<xref:System.Data.SqlTypes>) 。</span><span class="sxs-lookup"><span data-stu-id="8a866-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="8a866-115">你的项目必须引用 System.web 和 System.XML。</span><span class="sxs-lookup"><span data-stu-id="8a866-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a866-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="8a866-116">See also</span></span>

- [<span data-ttu-id="8a866-117">运算符过程</span><span class="sxs-lookup"><span data-stu-id="8a866-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="8a866-118">如何：定义运算符</span><span class="sxs-lookup"><span data-stu-id="8a866-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="8a866-119">如何：定义转换运算符</span><span class="sxs-lookup"><span data-stu-id="8a866-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="8a866-120">如何：调用运算符过程</span><span class="sxs-lookup"><span data-stu-id="8a866-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="8a866-121">Widening</span><span class="sxs-lookup"><span data-stu-id="8a866-121">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="8a866-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="8a866-122">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="8a866-123">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="8a866-123">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="8a866-124">如何：声明结构</span><span class="sxs-lookup"><span data-stu-id="8a866-124">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="8a866-125">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="8a866-125">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="8a866-126">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="8a866-126">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
