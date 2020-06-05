---
title: Of 子句
ms.date: 07/20/2015
f1_keywords:
- Of
- vb.Of
- vb.of
helpviewer_keywords:
- Of keyword [Visual Basic]
- arguments [Visual Basic], data types
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
ms.openlocfilehash: 8497f46453d586fb94e1f7c82c81c6b923dd6f60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404416"
---
# <a name="of-clause-visual-basic"></a><span data-ttu-id="1ee0b-102">Of 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ee0b-102">Of Clause (Visual Basic)</span></span>
<span data-ttu-id="1ee0b-103">引入一个 `Of` 子句，该子句标识*泛型*类、结构、接口、委托或过程中的*类型参数*。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-103">Introduces an `Of` clause, which identifies a *type parameter* on a *generic* class, structure, interface, delegate, or procedure.</span></span> <span data-ttu-id="1ee0b-104">有关泛型类型的信息，请参阅[Visual Basic 中的泛型类型](../../programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-104">For information on generic types, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>  
  
## <a name="using-the-of-keyword"></a><span data-ttu-id="1ee0b-105">使用关键字 of</span><span class="sxs-lookup"><span data-stu-id="1ee0b-105">Using the Of Keyword</span></span>  
 <span data-ttu-id="1ee0b-106">下面的代码示例使用 `Of` 关键字定义带有两个类型参数的类的轮廓。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-106">The following code example uses the `Of` keyword to define the outline of a class that takes two type parameters.</span></span> <span data-ttu-id="1ee0b-107">它*constrains* `keyType` 通过接口约束参数 <xref:System.IComparable> ，这意味着使用的代码必须提供实现的类型参数 <xref:System.IComparable> 。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-107">It *constrains* the `keyType` parameter by the <xref:System.IComparable> interface, which means the consuming code must supply a type argument that implements <xref:System.IComparable>.</span></span> <span data-ttu-id="1ee0b-108">这是必需的，以便 `add` 过程可以调用 <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-108">This is necessary so that the `add` procedure can call the <xref:System.IComparable.CompareTo%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1ee0b-109">有关约束的详细信息，请参阅 [Type List](type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-109">For more information on constraints, see [Type List](type-list.md).</span></span>  
  
```vb  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 <span data-ttu-id="1ee0b-110">如果你完成了前面的类定义，则可以构造其中的各种 `dictionary` 类。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-110">If you complete the preceding class definition, you can construct a variety of `dictionary` classes from it.</span></span> <span data-ttu-id="1ee0b-111">提供给的类型， `entryType` 并 `keyType` 确定类包含的项的类型以及它与每个项关联的键的类型。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-111">The types you supply to `entryType` and `keyType` determine what type of entry the class holds and what type of key it associates with each entry.</span></span> <span data-ttu-id="1ee0b-112">由于约束的原因，您必须提供 `keyType` 实现的类型 <xref:System.IComparable> 。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-112">Because of the constraint, you must supply to `keyType` a type that implements <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="1ee0b-113">下面的代码示例创建一个对象，该对象保存 `String` 项并将 `Integer` 键与每个项关联。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-113">The following code example creates an object that holds `String` entries and associates an `Integer` key with each one.</span></span> <span data-ttu-id="1ee0b-114">`Integer`实现 <xref:System.IComparable> 并因此满足上的约束 `keyType` 。</span><span class="sxs-lookup"><span data-stu-id="1ee0b-114">`Integer` implements <xref:System.IComparable> and therefore satisfies the constraint on `keyType`.</span></span>  
  
```vb  
Dim d As New dictionary(Of String, Integer)  
```  
  
 <span data-ttu-id="1ee0b-115">`Of` 关键字可用于以下上下文中：</span><span class="sxs-lookup"><span data-stu-id="1ee0b-115">The `Of` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1ee0b-116">Class 语句</span><span class="sxs-lookup"><span data-stu-id="1ee0b-116">Class Statement</span></span>](class-statement.md)  
  
 [<span data-ttu-id="1ee0b-117">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="1ee0b-117">Delegate Statement</span></span>](delegate-statement.md)  
  
 [<span data-ttu-id="1ee0b-118">Function 语句</span><span class="sxs-lookup"><span data-stu-id="1ee0b-118">Function Statement</span></span>](function-statement.md)  
  
 [<span data-ttu-id="1ee0b-119">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="1ee0b-119">Interface Statement</span></span>](interface-statement.md)  
  
 [<span data-ttu-id="1ee0b-120">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="1ee0b-120">Structure Statement</span></span>](structure-statement.md)  
  
 [<span data-ttu-id="1ee0b-121">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="1ee0b-121">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ee0b-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ee0b-122">See also</span></span>

- <xref:System.IComparable>
- [<span data-ttu-id="1ee0b-123">Type List</span><span class="sxs-lookup"><span data-stu-id="1ee0b-123">Type List</span></span>](type-list.md)
- [<span data-ttu-id="1ee0b-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ee0b-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="1ee0b-125">在</span><span class="sxs-lookup"><span data-stu-id="1ee0b-125">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="1ee0b-126">弄</span><span class="sxs-lookup"><span data-stu-id="1ee0b-126">Out</span></span>](../modifiers/out-generic-modifier.md)
