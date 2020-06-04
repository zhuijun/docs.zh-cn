---
title: 如何：确定两个对象是否相关
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 30e88a21e737aa57513745899577381ed34151a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410459"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="8ef29-102">如何：确定两个对象是否相关 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ef29-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="8ef29-103">您可以比较两个对象，以确定从中创建它们的类之间的关系（如果有）。</span><span class="sxs-lookup"><span data-stu-id="8ef29-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="8ef29-104"><xref:System.Type.IsInstanceOfType%2A> <xref:System.Type?displayProperty=nameWithType> `True` 如果指定的类从当前类继承，或者当前类型是指定的类所支持的接口，则类的方法将返回。</span><span class="sxs-lookup"><span data-stu-id="8ef29-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="8ef29-105">确定一个对象是否继承自另一个对象的类或接口</span><span class="sxs-lookup"><span data-stu-id="8ef29-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="8ef29-106">在您认为可能是基类型的对象上调用 <xref:System.Object.GetType%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8ef29-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="8ef29-107">在 <xref:System.Type?displayProperty=nameWithType> 返回的对象上 <xref:System.Object.GetType%2A> 调用 <xref:System.Type.IsInstanceOfType%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8ef29-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="8ef29-108">在的参数列表中 <xref:System.Type.IsInstanceOfType%2A> ，指定你认为可能是派生类型的对象。</span><span class="sxs-lookup"><span data-stu-id="8ef29-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="8ef29-109"><xref:System.Type.IsInstanceOfType%2A>`True`如果其参数类型继承自对象类型，则返回 <xref:System.Type?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="8ef29-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="8ef29-110">示例</span><span class="sxs-lookup"><span data-stu-id="8ef29-110">Example</span></span>
 <span data-ttu-id="8ef29-111">下面的示例确定一个对象是否表示一个派生自另一个对象的类的类。</span><span class="sxs-lookup"><span data-stu-id="8ef29-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

<span data-ttu-id="8ef29-112">请注意调用中的两个对象变量的意外位置 <xref:System.Type.IsInstanceOfType%2A> 。</span><span class="sxs-lookup"><span data-stu-id="8ef29-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="8ef29-113">假定的基类型用于生成 <xref:System.Type?displayProperty=nameWithType> 类，假设派生类型作为参数传递给 <xref:System.Type.IsInstanceOfType%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8ef29-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ef29-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ef29-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="8ef29-115">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="8ef29-115">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="8ef29-116">对象变量</span><span class="sxs-lookup"><span data-stu-id="8ef29-116">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="8ef29-117">对象变量值</span><span class="sxs-lookup"><span data-stu-id="8ef29-117">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="8ef29-118">如何：确定两个对象是否相同</span><span class="sxs-lookup"><span data-stu-id="8ef29-118">How to: Determine Whether Two Objects Are Identical</span></span>](how-to-determine-whether-two-objects-are-identical.md)
