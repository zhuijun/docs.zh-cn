---
title: 表达式是一个值，因此不能作为赋值目标
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 9e4dbaf2f2800454c673cd58ddec4cf0f6e5c6b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409502"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="3aab9-102">表达式是一个值，因此不能作为赋值目标</span><span class="sxs-lookup"><span data-stu-id="3aab9-102">Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="3aab9-103">语句尝试向表达式赋值。</span><span class="sxs-lookup"><span data-stu-id="3aab9-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="3aab9-104">可以在运行时将值仅分配给可写的变量、属性或数组元素。</span><span class="sxs-lookup"><span data-stu-id="3aab9-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="3aab9-105">下面的示例说明了如何发生此错误。</span><span class="sxs-lookup"><span data-stu-id="3aab9-105">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="3aab9-106">类似的示例可能适用于属性和数组元素。</span><span class="sxs-lookup"><span data-stu-id="3aab9-106">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="3aab9-107">**间接访问。**</span><span class="sxs-lookup"><span data-stu-id="3aab9-107">**Indirect Access.**</span></span> <span data-ttu-id="3aab9-108">通过值类型间接访问还会生成此错误。</span><span class="sxs-lookup"><span data-stu-id="3aab9-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="3aab9-109">请看下面的代码示例，它尝试通过将值通过间接访问来设置的值 <xref:System.Drawing.Point> <xref:System.Windows.Forms.Control.Location%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3aab9-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="3aab9-110">前面的示例的最后一条语句失败，因为它只为 <xref:System.Drawing.Point> 属性返回的结构创建临时分配 <xref:System.Windows.Forms.Control.Location%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3aab9-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="3aab9-111">结构是一种值类型，并且在运行语句后不会保留临时结构。</span><span class="sxs-lookup"><span data-stu-id="3aab9-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="3aab9-112">此问题的解决方法是：声明和使用的变量 <xref:System.Windows.Forms.Control.Location%2A> ，这会为结构创建更永久的分配 <xref:System.Drawing.Point> 。</span><span class="sxs-lookup"><span data-stu-id="3aab9-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="3aab9-113">下面的示例演示可以替换前面示例的最后一条语句的代码。</span><span class="sxs-lookup"><span data-stu-id="3aab9-113">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="3aab9-114">**错误 ID：** BC30068</span><span class="sxs-lookup"><span data-stu-id="3aab9-114">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3aab9-115">更正此错误</span><span class="sxs-lookup"><span data-stu-id="3aab9-115">To correct this error</span></span>

- <span data-ttu-id="3aab9-116">如果语句将值分配给表达式，请将表达式替换为单个可写的变量、属性或数组元素。</span><span class="sxs-lookup"><span data-stu-id="3aab9-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="3aab9-117">如果语句通过值类型（通常是结构）进行间接访问，则创建一个变量来保存值类型。</span><span class="sxs-lookup"><span data-stu-id="3aab9-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="3aab9-118">将适当的结构（或其他值类型）分配给该变量。</span><span class="sxs-lookup"><span data-stu-id="3aab9-118">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="3aab9-119">使用变量访问属性，为其赋值。</span><span class="sxs-lookup"><span data-stu-id="3aab9-119">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="3aab9-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3aab9-120">See also</span></span>

- [<span data-ttu-id="3aab9-121">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="3aab9-121">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="3aab9-122">语句</span><span class="sxs-lookup"><span data-stu-id="3aab9-122">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="3aab9-123">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="3aab9-123">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
