---
title: '#If...Then...#Else 指令'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410005"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="5520f-102">#If...Then...#Else 指令</span><span class="sxs-lookup"><span data-stu-id="5520f-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="5520f-103">有条件地编译选定的 Visual Basic 代码块。</span><span class="sxs-lookup"><span data-stu-id="5520f-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="5520f-104">语法</span><span class="sxs-lookup"><span data-stu-id="5520f-104">Syntax</span></span>

```vb
#If expression Then
   statements
[ #ElseIf expression Then
   [ statements ]
...
#ElseIf expression Then
   [ statements ] ]
[ #Else
   [ statements ] ]
#End If
```

## <a name="parts"></a><span data-ttu-id="5520f-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="5520f-105">Parts</span></span>

`expression`  
<span data-ttu-id="5520f-106">对于和语句是必需的 `#If` `#ElseIf` ，在其他位置为可选。</span><span class="sxs-lookup"><span data-stu-id="5520f-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="5520f-107">任何表达式（仅由一个或多个条件编译器常量、文本和运算符组成），其计算结果为 `True` 或 `False` 。</span><span class="sxs-lookup"><span data-stu-id="5520f-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="5520f-108">`#If`语句块必需，在其他位置为可选。</span><span class="sxs-lookup"><span data-stu-id="5520f-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="5520f-109">如果关联的表达式的计算结果为，则 Visual Basic 编译的程序行或编译器指令 `True` 。</span><span class="sxs-lookup"><span data-stu-id="5520f-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="5520f-110">终止 `#If` 语句块。</span><span class="sxs-lookup"><span data-stu-id="5520f-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="5520f-111">备注</span><span class="sxs-lookup"><span data-stu-id="5520f-111">Remarks</span></span>

<span data-ttu-id="5520f-112">在表面上，指令的行为将与语句的行为 `#If...Then...#Else` 相同 `If...Then...Else` 。</span><span class="sxs-lookup"><span data-stu-id="5520f-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="5520f-113">但是， `#If...Then...#Else` 指令将计算编译器编译的内容，而 `If...Then...Else` 语句则计算运行时的条件。</span><span class="sxs-lookup"><span data-stu-id="5520f-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="5520f-114">条件编译通常用于针对不同平台编译相同的程序。</span><span class="sxs-lookup"><span data-stu-id="5520f-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="5520f-115">它还用于阻止调试代码出现在可执行文件中。</span><span class="sxs-lookup"><span data-stu-id="5520f-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="5520f-116">在条件编译期间排除的代码在最终可执行文件中被完全省略，因此它不会对大小或性能产生任何影响。</span><span class="sxs-lookup"><span data-stu-id="5520f-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="5520f-117">不管任何计算结果如何，都将使用计算所有表达式 `Option Compare Binary` 。</span><span class="sxs-lookup"><span data-stu-id="5520f-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="5520f-118">`Option Compare`语句不影响和语句中的 `#If` 表达式 `#ElseIf` 。</span><span class="sxs-lookup"><span data-stu-id="5520f-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="5520f-119">不 `#If` 存在、、 `#Else` `#ElseIf` 和指令的单行形式 `#End If` 。</span><span class="sxs-lookup"><span data-stu-id="5520f-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="5520f-120">任何其他代码都不能与任何指令出现在同一行上。</span><span class="sxs-lookup"><span data-stu-id="5520f-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="5520f-121">条件编译块内的语句必须是完整的逻辑语句。</span><span class="sxs-lookup"><span data-stu-id="5520f-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="5520f-122">例如，你无法有条件地仅编译函数的属性，但你可以有条件地声明函数及其属性：</span><span class="sxs-lookup"><span data-stu-id="5520f-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="5520f-123">示例</span><span class="sxs-lookup"><span data-stu-id="5520f-123">Example</span></span>

<span data-ttu-id="5520f-124">此示例使用 `#If...Then...#Else` 构造来确定是否编译某些语句。</span><span class="sxs-lookup"><span data-stu-id="5520f-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="5520f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5520f-125">See also</span></span>

- [<span data-ttu-id="5520f-126">#Const 指令</span><span class="sxs-lookup"><span data-stu-id="5520f-126">#Const Directive</span></span>](const-directive.md)
- [<span data-ttu-id="5520f-127">If...Then...Else 语句</span><span class="sxs-lookup"><span data-stu-id="5520f-127">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="5520f-128">条件编译</span><span class="sxs-lookup"><span data-stu-id="5520f-128">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
